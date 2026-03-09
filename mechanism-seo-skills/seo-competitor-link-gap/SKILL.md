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

## Output Format

Deliver a prioritized target list in this structure:

---

**SEO Competitor & Link Gap Analysis — [Brand Name]**
*Analyzed: [date]*

**Money Keywords Analyzed:** [list]

**Top SEO Competitors Identified:**
| Domain | Type | Why Relevant |
|--------|------|--------------|
| ... | Direct / Indirect / Editorial | ... |

**SERP Pattern Notes:**
[2–3 sentences on what the SERPs look like — who dominates, what content types rank, what this means for link strategy]

**Prioritized Link Gap Targets:**
| Domain | DR | Link Type | Outreach Angle |
|--------|----|-----------|----------------|
| ... | ... | ... | ... |

**Strategic Notes:**
[2–3 sentences on overall link building approach given what was found — e.g., "This category is dominated by editorial roundups, so outreach should focus on inclusion in 'best of' content rather than resource page links."]

---

## Judgment Guidelines

Apply these principles when interpreting results — they encode how Mechanism approaches link building:

- **Editorial and review sites are high-value targets** in ecommerce categories. They already link to products; getting included is realistic.
- **DR matters but relevance matters more.** A DR 35 niche blog in the exact category beats a DR 70 general lifestyle site.
- **Prioritize domains linking to 2+ competitors.** They have an established pattern of linking to brands in this space. Easiest pitch.
- **Flag if the category is SERP-crowded.** If major retailers and media dominate every keyword, note this — it shapes realistic expectations for what organic can achieve on the brand's own domain vs. a TPV strategy.
- **New domains need foundational links first.** If the brand domain is new (DR < 10), note that the first priority is establishing basic domain credibility (citations, directories, early topical links) before pursuing competitive gap targets.

---

## Example Trigger Phrases

This skill should run when someone says things like:
- "Kick off SEO research for Hello Pest"
- "Find our link building targets for [brand]"
- "Who are the SEO competitors for [brand]?"
- "Run a link gap analysis for [domain]"
- "We're launching [brand] — what does the link landscape look like?"
