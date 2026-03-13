---
name: gsc-performance-monitoring
description: Runs a structured Google Search Console performance review for a Mechanism portfolio company. Use this skill whenever someone asks about GSC performance, how a site is ranking, what keywords are moving, what's happening in Search Console, or wants a weekly or monthly organic performance check. Also trigger when someone says things like "check GSC for [brand]", "how are our rankings looking", "what's moving in search for [brand]", "run a GSC review", or "what does Search Console show for [brand]". Always use this skill rather than giving manual GSC instructions.
compatibility: "Requires access to Google Search Console data for the PortCo (via GSC export, shared report, or direct access). Ahrefs MCP optional for cross-referencing ranking data."
---

# GSC Performance Monitoring

This skill runs a structured Google Search Console performance review for a Mechanism PortCo. It tells you what's moving, what's stalling, and what needs action — in plain language, not just raw numbers.

GSC is the most direct signal of organic performance available. It shows exactly what Google is serving the site for, at what positions, and how many people are clicking. Run this review weekly at a minimum for active engagements.

---

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the PortCo being reviewed
- **GSC access** — either direct access, a shared report, or a data export
- **Review period** — typically:
  - Last 7 days vs. prior 7 days (weekly check-in)
  - Last 28 days vs. prior 28 days (monthly review)
  - Month vs. same month prior year (year-over-year — best for seasonal categories)
- **Money keywords** — the primary keywords this PortCo is targeting (from the Non-Branded Keyword Strategy skill if available)

---

## What GSC Tells Us (and What It Doesn't)

**GSC measures:**
- Impressions — how many times the site appeared in Google results
- Clicks — how many times someone clicked through
- CTR — clicks ÷ impressions
- Average position — average ranking across all queries the site appeared for

**What to watch:**
- **Clicks and impressions on money keywords** — are we gaining or losing ground on the keywords that matter?
- **Position movement** — are money keyword rankings trending up, flat, or down?
- **CTR on high-impression pages** — if we're getting impressions but not clicks, the title tag or meta description may be the problem
- **New keywords entering the top 20** — early signal that new content or links are starting to work
- **Pages losing impressions** — early warning of ranking drops before they hit traffic

**What GSC doesn't tell us:**
- Whether organic traffic is converting (need GA4 or Shopify for that)
- Why rankings changed (need Ahrefs and manual SERP analysis for that)
- **Organic search presence on non-Google engines** — Bing, DuckDuckGo, and others are invisible in GSC. For most PortCos this is a small share of traffic, but it exists and is untracked.
- **AI Overview presence specifically** — GSC includes impressions from AI Overview appearances in its data, but you cannot break out AI Overview clicks/impressions separately from traditional organic results. This is a significant blind spot as AI Overviews grow. If overall impressions are rising but clicks aren't keeping pace, AI Overviews may be intercepting traffic. Use Ahrefs Brand Radar as a supplementary signal for AI search presence.

---

## Workflow

### Step 1: Set the Time Period and Filter

Open GSC for the PortCo domain. Set the date range:
- **Weekly review:** Last 7 days vs. previous 7 days
- **Monthly review:** Last 28 days vs. previous 28 days
- **Year-over-year:** Specific month vs. same month prior year (e.g. Feb 2026 vs. Feb 2025) — use this when the category is seasonal or when longer-term trend context matters more than recent movement

Apply two separate views:
1. **Non-branded keywords only** — exclude brand name and variations. This is the primary growth signal.
2. **Branded keywords only** — the brand name and variations. Track separately. Branded growth is a signal of halo effect working.

---

### Step 2: Money Keyword Check

Filter for each of the PortCo's primary money keywords. For each one, record:
- Current average position
- Position change vs. prior period
- Impressions
- Clicks
- CTR

Flag any money keyword that has:
- 🔴 Dropped more than 3 positions period-over-period
- 🟡 Been stuck in positions 11–20 for 4+ weeks (just off page one — highest leverage for link building)
- 🟢 Moved into the top 10 for the first time
- 🟢 Improved CTR without a position change (title tag test working)

---

### Step 3: Top Pages Review

Pull the top 10 pages by clicks for the period. For each page, note:
- Is it a money page or supporting content?
- Is it trending up or down vs. prior period?
- Are impressions high but CTR low? (title/meta issue)
- Are clicks dropping despite stable impressions? (SERP composition changed — AI overview may have appeared)

---

### Step 4: New Keyword Opportunities

Filter for keywords ranking in positions 11–20 with at least 100 impressions in the period. These are the highest-leverage near-term ranking opportunities — one page up can mean 2–3x the clicks.

For each, ask:
- Does the PortCo have a page targeting this keyword?
- Is the ranking page the right page for this keyword?
- What would it take to move into the top 10? (usually: better content, more links to that page, or internal linking)

Flag the top 3 opportunities for the team to act on.

---

### Step 5: Drops and Anomalies

Look for:
- Any page that lost 30%+ of clicks vs. prior period
- Any keyword that dropped out of the top 20 entirely
- Any spike or drop in total impressions that doesn't correspond to a known change (new content, algorithm update, site change)

If a drop is significant, cross-reference with:
- Known Google algorithm update dates
- Any site changes made recently (URL changes, content edits, technical issues)
- Ahrefs to check if referring domains to the affected pages changed

---

## Output

Save the report as a Word document (.docx) using python-docx.

**Filename:** `[portco]-[skillname]-[M.DD.YY].docx`
**Example:** `liveitup-aeogeoaudit-3.13.26.docx`
**Save location:** `~/Documents/mechanism-seo/outputs/`

Structure the document in this exact order:

---

**[Skill Name] — [Brand] — [Date]**

**TL;DR**
2–3 sentences. The headline finding and the single most important action.

---

**Summary**
Narrative overview written for a CEO. What was audited, what was found, overall health or status. No bullet points, no data tables. Plain language. 3–5 paragraphs.

---

**Findings**
Full analysis — all data, tables, competitive breakdowns, page-level detail, and supporting evidence. Nothing stripped out. This is the working reference for whoever is executing the work.

---

**Action Items**
Numbered list. Each item states the action and why it matters or what impact it drives.

1. [Action] — [why it matters / expected impact]
2. [Action] — [why it matters / expected impact]
3. [Action] — [why it matters / expected impact]
