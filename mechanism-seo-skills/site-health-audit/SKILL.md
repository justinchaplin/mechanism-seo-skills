---
name: site-health-audit
description: Checks the technical health of a Mechanism portfolio company's website using Ahrefs Site Audit (set to crawl every 24 hours) and Google Search Console — identifying errors that could suppress rankings, flagging alarming signals that require immediate action, and distinguishing real problems from noise. Use this skill whenever someone asks to check a site's technical health, audit a site, look for crawl errors, check GSC for issues, investigate a traffic drop with no obvious content cause, or review a site before or after a major change. Also trigger when someone says "check the site health for [brand]", "are there any technical issues on [domain]", "something is wrong with [domain]'s rankings", or "run a site audit for [brand]". Always use this skill rather than giving ad hoc technical assessments.
compatibility: "Requires Ahrefs MCP (site-audit-projects and site-audit-issues tools; Site Audit must be configured in Ahrefs for the domain and set to crawl every 24 hours). GSC data is interpreted manually or via GSC screenshots — Claude cannot pull GSC data directly. Requires PortCo knowledge file for domain and site type context."
---

# Site Health Audit

This skill checks a portfolio company's site for technical issues that could suppress organic performance — pulling from Ahrefs Site Audit (daily crawl) and interpreting Google Search Console signals. It separates alarms from noise, explains what each issue means, and tells the team exactly what to do about it.

Technical SEO is not the primary lever for most Mechanism PortCos — content and links are. But a site with critical technical errors can have all the right content and links and still not rank. This skill exists to make sure nothing is silently broken.

---

## Setup Requirements

Before running this skill, confirm:

**Ahrefs Site Audit is configured for the domain and set to crawl every 24 hours.**
- In Ahrefs: Site Audit → [Project] → Settings → Schedule → Daily
- If not configured, flag this to the team — a site without a daily crawl has no early warning system
- The crawl covers all internal pages; external pages and JavaScript-heavy SPAs may require additional configuration

**Google Search Console is verified and accessible for the domain.**
- Access via search.google.com/search-console
- The domain property (not URL prefix) is preferred for complete coverage

---

## Inputs Required

- **Brand name** and **domain** — the PortCo being audited
- **Ahrefs Site Audit project ID** — from the PortCo knowledge file or by finding it in the Ahrefs URL: `https://app.ahrefs.com/site-audit/[project_id]`
- **GSC data** — provided by the person running the audit (screenshots, exports, or manual observation)
- **Context for the audit** — routine weekly check, post-launch check, investigating a traffic drop, pre-launch review, or other

---

## Step 1: Pull Ahrefs Site Audit Data

Pull the current site audit project summary:

```
Ahrefs: site-audit-projects
project_id: [id]
```

This returns:
- `health_score` — proportion of internal URLs with no errors (0–100)
- `urls_with_errors` — count of pages with Error-level issues
- `urls_with_warnings` — count of pages with Warning-level issues
- `urls_with_notices` — count of pages with Notice-level issues
- `total` — total crawled URLs
- `status` — last crawl status (Completed / Error / In_progress / Stopped)
- `date` — last crawl timestamp

Then pull all active issues:

```
Ahrefs: site-audit-issues
project_id: [id]
```

This returns issues with:
- `issue_id` — unique identifier
- `name` — issue name
- `importance` — Error / Warning / Notice
- `category` — Internal pages / Indexability / Links / Redirects / Content / Social tags / Duplicates / Localization / Usability and performance / Images / JavaScript / CSS / Sitemaps / External pages / Other
- `crawled` — number of URLs currently affected
- `change` — difference vs. previous crawl (positive = new issues appearing, negative = resolved)

---

## Step 2: Triage Issues by Severity

Not every issue in the audit requires action. Apply this triage framework:

### 🔴 Alarm — Act Immediately

These issues can directly suppress rankings or remove pages from the index. Investigate same day.

**Indexability issues — always Alarm if `crawled` > 0 on important pages:**
- `Noindex page` — pages with a `noindex` tag or header. If this is on pages that should be ranking, it's a kill switch. Verify intentional vs. accidental.
- `Blocked by robots.txt` — pages blocked from crawling. Any money page or key content here is invisible to Google.
- `Canonical points to different URL` — if a money page canonicals to a different URL, Google may credit the wrong page.
- `Page returns 4XX status code` — broken pages returning 404/410. Important if these are pages that previously ranked or have backlinks.
- `Page returns 5XX status code` — server errors. Any 5XX on important pages means Google can't crawl them.

**Redirect issues — Alarm if widespread:**
- `Redirect chain` — multiple hops before reaching the destination. Bleeds link equity. Alarm if affecting money pages or pages with backlinks.
- `Broken redirect` (redirect to 4XX/5XX) — redirects pointing nowhere. PageRank and links pointing to these are wasted.

**Content issues — Alarm if affecting money pages:**
- `Duplicate page` or `Duplicate title` on money pages — Google may not know which version to rank.

**Health score interpretation:**
- 90–100: Healthy. Investigate any Errors but no alarm.
- 75–89: Warning territory. Review Errors closely.
- Below 75: Alarm. Something meaningful is broken.
- Sudden drop of 10+ points vs. prior crawl: Alarm regardless of absolute score.

---

### 🟡 Warning — Address Within 2 Weeks

These issues reduce efficiency but don't immediately kill rankings. Schedule for the next sprint.

**Content:**
- `Missing meta description` — not a ranking factor but affects CTR in SERPs. Prioritize money pages.
- `Title tag too long` / `Title tag too short` — truncated or missing titles reduce SERP click appeal.
- `Low word count` — thin pages. Not always a problem (product pages are legitimately short) but flag for review.
- `Missing H1` / `Multiple H1 tags` — structural clarity for crawlers.

**Links:**
- `Broken internal links` (returning 4XX) — clean these up. Wasted crawl budget and confusing for users.
- `Orphan pages` — pages with no internal links pointing to them. Crawlers may not find them reliably.

**Images:**
- `Missing alt text` — accessibility and minor crawl signal. Prioritize images on money pages.
- `Broken images` — poor user experience and crawl inefficiency.

**Redirects:**
- `Redirect loop` — circular redirects. Pages in a loop are uncrawlable.
- `3XX redirect to HTTPS` or `HTTP page` — flag if the site should be fully HTTPS.

**Performance:**
- `Slow page` — pages with high load time. Core Web Vitals factor. Flag if widespread (20%+ of pages).

---

### 🔵 Notice — Log and Monitor

These are real but low-priority. Review quarterly or when running a deep audit.

- `Missing Open Graph tags` / `Missing Twitter card tags` — social sharing appearance. Not a ranking factor.
- `Long URL` — minor.
- `Missing canonical tag` — only an issue if there's a real duplicate content risk.
- `Sitemap issues` — flag if the sitemap is missing important pages or includes noindex pages.

---

## Step 3: Check Google Search Console

GSC surfaces signals Ahrefs Site Audit can't see — because it shows Google's actual view of the site, not a crawler's simulation.

### Coverage Report (Index → Pages)

The Coverage report shows which pages Google has indexed, which have errors, and why.

**Variables to check and what they mean:**

| Status | What it means | When to act |
|--------|--------------|-------------|
| **Error: Submitted URL not found (404)** | A URL in your sitemap returns 404 | Alarm — fix or remove from sitemap |
| **Error: Submitted URL blocked by robots.txt** | Sitemap URL is blocked | Alarm — robots.txt is blocking something it shouldn't |
| **Error: Submitted URL has crawl issue** | Google couldn't access the URL | Alarm — investigate server or redirect issues |
| **Error: Server error (5XX)** | Server returned an error | Alarm — server instability or downtime |
| **Warning: Indexed, not submitted in sitemap** | Google found the page but it's not in the sitemap | Monitor — add to sitemap if important |
| **Warning: Page with redirect** | Sitemap URL redirects | Warning — update sitemap to final URLs |
| **Excluded: Noindex** | Page has noindex tag | Alarm if it's a page that should rank |
| **Excluded: Canonicalized** | Page defers to a canonical URL | Normal if intentional; Alarm if on money pages unintentionally |
| **Excluded: Crawled - currently not indexed** | Google crawled but chose not to index | Investigate if this is a money page — may indicate thin/duplicate content |
| **Excluded: Discovered - currently not indexed** | Google found but hasn't crawled yet | Normal for new pages; Alarm if important pages have waited >4 weeks |
| **Excluded: Duplicate without user-selected canonical** | Duplicate content, no canonical | Warning — add canonical tags |

**Alarm thresholds in Coverage:**
- Any Errors on URLs that should be indexed: immediate investigation
- "Crawled - currently not indexed" on money pages: investigate content quality
- Large spike in Excluded pages after a site change: rollback risk

---

### Performance Report (Search Results)

The Performance report shows impressions, clicks, CTR, and average position from Google Search.

**Key variables:**

| Variable | What it is | What a drop means |
|----------|-----------|-------------------|
| **Total clicks** | Actual Google organic clicks | Direct traffic signal — a drop here is real |
| **Total impressions** | Times the site appeared in search results | Drop = rankings lost or pages deindexed |
| **Average CTR** | Clicks ÷ Impressions | Drop without clicks/impressions drop = title/meta issues |
| **Average position** | Mean ranking position across all queries | Rising number = rankings declining |

**Filters to run during a health check:**
- Filter by **Search type: Web** (excludes Image and Video)
- Compare **last 28 days vs. previous 28 days** for trend
- Filter by **page** to isolate drops to specific URLs
- Filter by **query** to see if specific keywords are falling

**What to look for:**
- Impressions drop but clicks stable → AI Overview may be absorbing clicks without reducing impressions
- Clicks drop but impressions stable → CTR problem (title tags, meta descriptions, or SERP feature cannibalizing)
- Both drop together → rankings lost — investigate Ahrefs position history for those pages
- Specific pages dropping with no content changes → possible algorithmic quality signal or competitor movement

---

### Manual Actions Report (Security & Manual Actions)

Always check this report. A manual action means Google has penalized the site. If there's an active manual action:

**🔴 Alarm — this is the highest-severity possible issue in GSC.**

Types:
- **Unnatural links to your site** — Google has flagged manipulative link building
- **Thin content with little or no added value** — content quality penalty
- **Pure spam** — site flagged as spam
- **User-generated spam** — blog comments or forum posts generating spam signals
- **Hacked content** — site has been compromised

If a manual action is found, escalate to Justin immediately. Do not attempt to resolve without a full investigation.

---

### Core Web Vitals Report (Experience → Core Web Vitals)

Checks real-world performance data from Chrome users.

**Variables:**
- **LCP (Largest Contentful Paint)** — how fast the main content loads. Good: <2.5s. Needs improvement: 2.5–4s. Poor: >4s.
- **INP (Interaction to Next Paint)** — responsiveness to user interactions. Good: <200ms.
- **CLS (Cumulative Layout Shift)** — visual stability. Good: <0.1.

**When to act:** Flag if >20% of pages are in "Poor" status. Core Web Vitals are a confirmed ranking signal, and meaningful underperformance here can suppress rankings on competitive SERPs.

---

## Step 4: Interpret the Full Picture

After pulling Ahrefs issues and reviewing GSC, synthesize:

1. **Is there an active alarm?** Any 🔴 issue requires an action item with a deadline.
2. **Is the health score declining trend?** Even without a current alarm, a health score that has dropped 5+ points over the past 30 days is a signal to investigate.
3. **Do Ahrefs issues and GSC signals corroborate each other?** A 404 in Ahrefs + a "submitted URL not found" in GSC = confirmed problem. A 404 only in Ahrefs may be on a page GSC hasn't crawled.
4. **Is this a site change aftermath?** If the audit is post-launch, post-migration, or post-redesign, pay extra attention to Coverage and redirect chains.

---

## Output Format

---

**Site Health Audit — [Brand Name] ([domain])**
*Audit date: [date] | Last crawl: [Ahrefs crawl date]*

**Health Score: [X]/100** [🔴 / 🟡 / 🟢 based on score]
*[X] total pages crawled | [X] errors | [X] warnings | [X] notices*

---

**🔴 Alarms — Act Immediately**
[List each alarm with: issue name, pages affected, what it means, and what to do]

If none: ✅ No active alarms.

---

**🟡 Warnings — Address Within 2 Weeks**
[List warnings with pages affected and recommended action]

If none: ✅ No active warnings.

---

**GSC Signals**
[Coverage summary — any errors, notable exclusions]
[Performance summary — clicks/impressions trend, notable drops]
[Manual actions — clean or flagged]
[Core Web Vitals — pass/fail summary]

---

**Recommended Actions**
1. [Specific action — owner, deadline]
2. [Specific action]
3. [Monitor item, if relevant]

---

**What's Not a Problem**
[Explicit callout of any issues in the audit that look alarming but are expected/intentional — e.g., noindex on thank-you pages, canonicals on filtered URLs. This prevents the team from wasting time investigating noise.]

---

## Judgment Guidelines

- **Distinguish between important pages and everything else.** A 404 on an old blog post is different from a 404 on a money page with backlinks. Always check whether affected pages are important before escalating.
- **New issues that appeared in the last crawl (high `change` value) are higher priority than persistent issues.** Something that just broke is more urgent than something that's been stable for months.
- **Don't flag notices as warnings.** Notice-level issues are real but low-priority. Treating them as urgent burns credibility with PortCo teams.
- **If the crawl status is not "Completed," the data is unreliable.** Flag this before interpreting any issue counts.
- **Ahrefs crawls differently than Googlebot.** Ahrefs may flag issues that Googlebot doesn't see (and vice versa). GSC is always the ground truth for what Google actually sees.
- **A healthy Ahrefs score with a GSC manual action is still an alarm.** The audit score doesn't account for penalties.
- **After a site migration or redesign, always check redirect chains and coverage together.** These are the two most common post-migration failure modes.

---

## Example Trigger Phrases

- "Run a site health audit for Hey Sunday"
- "Check if there are any technical issues on primeputt.com"
- "Something is wrong with Learner's rankings — nothing changed in content"
- "Check the site audit for Hello Pest after the migration"
- "Are there any GSC errors for [brand]?"
- "What does the Ahrefs site audit show for [domain]?"
- "Weekly site health check for [brand]"
