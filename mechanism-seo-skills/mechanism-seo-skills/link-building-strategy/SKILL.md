---
name: link-building-strategy
description: Determines the right link building tactic mix for a Mechanism portfolio company based on their stage, domain authority, category, and goals. Use this skill whenever someone asks about link building strategy, which link building tactics to use, how to prioritize link building for a PortCo, what kind of links to build, or how to approach link building for a new or existing engagement. Also trigger when someone says things like "what's our link building strategy for [brand]", "should we do scholarship links or content links", "how do we build links for [brand]", or "kick off link building for [brand]". Always use this skill rather than giving generic link building advice.
compatibility: "Requires Ahrefs MCP (for domain rating, backlink profile, and competitor analysis) and web_search (for SERP and category research)."
---

# Link Building Strategy

This skill determines the right link building tactic mix for a Mechanism PortCo. It encodes how Mechanism thinks about link building — not a generic set of tactics, but a judgment-driven decision about what will actually move the needle for a specific company at a specific stage.

The output is a prioritized tactic stack with rationale, recommended starting points, and clear guidance on what not to do.

---

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the PortCo being analyzed
- **Domain** — root domain (e.g., primeputt.com)
- **Product category** — what the brand sells
- **Current DR** — if known; otherwise pull from Ahrefs
- **Stage** — New Launch / Growth / Mature/Stable
- **Known link building history** — any tactics already tried, any wins or failures

If stage or DR are unknown, pull from Ahrefs before proceeding.

---

## How Mechanism Thinks About Link Building

Before running the workflow, understand the philosophy:

**Relevance and real traffic beat DR — every time.** A DR 50 niche site with ranking pages in the category outperforms a DR 80 general site with a random contributor post. Always evaluate whether the linking site is actually talking to our customer.

**Links are brand signals, not just domain authority plumbing.** The future of link value is being mentioned in authoritative, relevant places — the kind of editorial mentions that shape how AI search surfaces a brand. A Golf Digest mention of PrimePutt is not comparable to a scholarship link on a college site, even if the DR looks similar.

**Tactic selection is stage-dependent.** A new domain needs foundational authority before competitive gap targeting. A mature domain needs quality over volume. The tactics that work at launch often don't scale, and the tactics that scale aren't always the right starting point.

**The don't-do list is as important as the do list:**
- No low-quality links — if it feels 1% spammy, skip it
- No buying links
- No direct link exchanges
- No spray-and-pray outreach — large campaigns are fine and expected, but every target must be relevant to the category. Volume is a tool, not a strategy.
- No scholarship links to irrelevant sites (a putting mat company doesn't need a college scholarship page)

---

## Step 1: Pull Current Domain Profile

Using Ahrefs, get the current state of the domain:

```
Ahrefs: site-explorer-domain-rating
target: [brand domain]
```

Also pull referring domain count and top backlink types:
```
Ahrefs: site-explorer-backlinks-stats
target: [brand domain]
```

Assess:
- What is the current DR?
- How many referring domains does the site have?
- What types of links already exist (editorial, directory, sponsored, etc.)?
- Are there any obvious toxic or spammy links in the profile?

---

## Step 2: Competitor Link Profile Benchmarking

Pull the top 3 competitors' domain ratings and referring domain counts for comparison:

```
Ahrefs: batch-analysis
targets: [competitor domains]
select: [domain_rating, referring_domains, organic_traffic]
```

This tells you:
- How far behind is the PortCo's link profile vs. competitors?
- What DR threshold seems to correlate with ranking in this category?
- Is this primarily a volume gap (need more links) or quality gap (need better links)?

---

## Step 3: Category SERP Link Pattern Assessment

Search Google for the top 2–3 money keywords in the category. For each SERP, look at what types of sites are ranking and linking to the top results:

- Are editorial roundups ("best putting mats of 2025") dominant?
- Are review sites with affiliate links common?
- Are directory or resource pages appearing?
- Are news/media sites covering the category?

This shapes which outreach angles are realistic. A category dominated by editorial roundups means your best path is product inclusion in those roundups — not resource page outreach.

---

## Step 4: Tactic Selection

Based on DR, stage, and category SERP patterns, select the right tactic mix from the menu below. Not every tactic is right for every PortCo.

---

### Tactic Menu

**🟢 Content-Focused Outreach (Best Lists / Roundups)**
*Best for: ecommerce brands, any DR, all stages*

Target editorial sites that publish "best of" roundups in the category. Get the product included in existing articles or pitch for inclusion in upcoming ones. These sites already link to products in the space — it's the most natural outreach angle.

- Why it works: editorial roundup sites have established patterns of linking to products in the category; getting included is realistic and drives real referral traffic
- Effort: medium — requires product samples or strong pitch material
- Timeline: 4–8 weeks per placement
- Signal value: high — these are the mentions that drive halo effect and AI search presence
- Ideal for: PrimePutt (golf roundups), Hey Sunday (laundry/home roundups), Hello Pest (pest control roundups)

---

**🟢 Broken Link Building**
*Best for: any DR, especially effective for informational/resource-heavy categories*

Find pages in the category that link to broken or dead resources. Offer a replacement. Works best when the PortCo has genuinely useful content.

- Why it works: you're solving a problem for the site owner, not just asking for a favor
- Effort: medium — requires prospecting and content to replace the broken resource
- Timeline: 2–4 weeks per placement
- Signal value: medium-high depending on site quality
- Ideal for: Learner (education category has many resource pages that go dead)

---

**🟢 Digital PR / Data-Driven Content**
*Best for: DR 20+, growth and mature stages*

Create original data, studies, or insights that journalists and bloggers want to reference. Requires investment in content creation but earns high-authority editorial links.

- Why it works: gives media a reason to cover the brand beyond product promotion
- Effort: high — requires original research or compelling data
- Timeline: 6–12 weeks per campaign
- Signal value: very high — national/trade media links are the strongest available
- Ideal for: any PortCo with interesting data about their customer base or category

---

**🟡 Scholarship Links**
*Best for: new domains needing foundational DR, not category-relevant*

Create a scholarship page and submit to .edu scholarship directories. Earns high-DR backlinks from universities.

- Why it works: .edu domains have high authority and scholarship directories are well-maintained
- Effort: low-medium — requires a scholarship to actually exist (typically $500–$1k/year)
- Timeline: 4–8 weeks
- Signal value: moderate — helps build domain authority but has zero category relevance or halo effect value
- When to use: only for new domains (DR < 20) that need foundational authority before competitive outreach. Not a primary tactic — a foundation builder.
- When NOT to use: for established domains, or as a primary strategy. A putting mat company ranking for "best putting mat" is not helped by a scholarship link.

---

**🟡 Resource Page Outreach**
*Best for: informational categories, DR 15+*

Find resource pages in the category ("best tools for X", "resources for Y") and pitch for inclusion.

- Why it works: resource pages are built to link out — they want good additions
- Effort: medium — requires prospecting and a clear value proposition for inclusion
- Timeline: 3–6 weeks per placement
- Signal value: medium — depends heavily on the quality of the resource page
- Ideal for: Learner (education resources), Hello Pest (pest prevention resources)

---

**🟡 Partnership-Driven Links**
*Best for: brands with natural partner ecosystems (retailers, complementary products, associations)*

Identify brands, retailers, or organizations the PortCo has natural relationships with and formalize link exchanges or co-marketing that includes links.

- Why it works: existing relationships lower outreach friction
- Effort: low if relationships exist, high if they need to be built
- Timeline: 2–4 weeks per placement
- Signal value: medium — depends on partner domain quality
- Caution: avoid direct link exchanges (I link to you, you link to me). Must be value-driven, not transactional.

---

**🔴 Directory Links**
*Use sparingly — low priority*

Submit to relevant industry directories. Very low effort, very low signal value.

- Only worth doing for: local SEO relevance, niche industry directories with real traffic
- Not worth doing for: general web directories, low-traffic listing sites
- Never use as a primary tactic

---

## Step 5: Build the Tactic Stack

Based on the analysis, produce a prioritized tactic stack specific to this PortCo:

**Tier 1 — Start here (highest impact, most urgent)**
The 1–2 tactics that will move the needle fastest given current DR and stage.

**Tier 2 — Build in parallel (medium-term)**
Tactics to layer in once Tier 1 is running.

**Tier 3 — Later / situational**
Tactics that make sense at a future stage or in specific circumstances.

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
