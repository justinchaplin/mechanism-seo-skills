---
name: seo-competitor-link-gap
description: Runs a full SEO competitor identification and link gap analysis for any brand launch. Use this skill whenever someone mentions finding SEO competitors, running a link gap analysis, identifying link building targets, or kicking off SEO research for a new or existing company. Also trigger when someone says things like "who should we be building links from", "find our link targets", "who are our SEO competitors", or "kick off SEO research for [brand]". This skill uses Ahrefs MCP to execute the analysis directly — the user does not need to open Ahrefs manually. Always use this skill rather than giving manual instructions.
compatibility:
  tools:
    - Ahrefs MCP (required — for Site Explorer, organic competitors, and Link Intersect)
    - web_search (required — for manual SERP research)
---

# SEO Competitor Identification & Link Gap Analysis

This skill identifies SEO competitors for a brand and runs a link gap analysis to surface prioritized domain targets for link building outreach. It is fully executable — Claude runs the analysis using Ahrefs MCP and web search. The user does not open Ahrefs manually.

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the company being analyzed
- **Domain** — the brand's root domain (e.g., hellopest.com)
- **Primary money keywords** — 3–5 high-intent search terms the brand wants to rank for
- **Known competitors** (optional) — any competitors the team already knows about

If any of these are missing, ask before proceeding.

---

## Workflow

### Step 1: SERP Research — Identify Who's Actually Ranking

For each money keyword provided, run a web search and record the top 10 organic results. You are looking for:

- **Direct competitors** — other brands selling the same or similar product
- **Indirect competitors** — review sites, roundups, editorial content, affiliates that rank for the same terms
- **SERP patterns** — note if results are dominated by editorial content, retailers, or brand sites. This shapes link building strategy.

Record every unique domain that appears across the money keyword SERPs. Flag which type each is (direct / indirect / editorial).

**Key judgment call:** Indirect competitors and editorial sites (e.g., "best pest control products" roundups) are often *better* link targets than direct brand competitors — they already link to products in this category.

---

### Step 2: Ahrefs Organic Competitors Pull

Using the Ahrefs MCP, run the organic competitors report for the brand's domain:

```
Ahrefs: site-explorer-organic-competitors
target: [brand domain]
```

Pull the top 10 organic competitors by overlap score. Cross-reference with the SERP research from Step 1. Combine into a single deduplicated competitor list, prioritizing:

1. Domains that appeared in both SERP research AND Ahrefs organic competitors
2. Domains with high topical relevance to the brand's category
3. Remove any that are clearly not useful (major retailers like Amazon, large news sites with no linking patterns relevant to the niche)

**Final competitor list:** Aim for 3–5 strong, relevant competitors to feed into the link intersect.

---

### Step 3: Ahrefs Link Intersect

Using the Ahrefs MCP, run the Link Intersect tool with the top 3–5 competitors vs. the brand's domain:

```
Ahrefs: site-explorer-all-backlinks (run for each competitor)
target: [competitor domain]
```

For each competitor, pull their referring domains. Then identify domains that:
- Link to 2 or more competitors but NOT to the brand
- Have a DR of 30 or above
- Are topically relevant to the brand's category

These are the highest-priority link gap targets — sites already willing to link to brands in this space that haven't linked to this brand yet.

---

### Step 4: Enrich & Prioritize Targets

For each link gap domain identified, add context:

- **DR** (from Ahrefs)
- **Why it's relevant** — what content on their site links to competitors
- **Link type** — resource page, blog post, roundup, directory, editorial mention
- **Outreach angle** — one sentence on how to approach them (e.g., "They have a 'best pest control products' roundup — pitch for inclusion")

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
