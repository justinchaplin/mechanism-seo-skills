---
name: non-branded-keyword-strategy
description: Identifies, evaluates, and prioritizes non-branded money keywords for a Mechanism portfolio company. Use this skill whenever someone asks about keyword strategy, what keywords to target, which keywords a PortCo should rank for, keyword research for a new or existing engagement, or how to size the organic opportunity for a brand. Also trigger when someone says things like "what should [brand] rank for", "find our money keywords", "what's the keyword opportunity for [brand]", "which keywords should we go after", or "kick off keyword research for [brand]". This skill uses Ahrefs MCP and SERP analysis to execute the full workflow. Always use this skill rather than giving manual instructions.
compatibility: "Requires Ahrefs MCP (for keyword metrics, competitor analysis, SERP data) and web_search (for manual SERP research and composition analysis)."
---

# Non-Branded Keyword Strategy

This skill identifies, evaluates, and prioritizes non-branded money keywords for a Mechanism PortCo. It encodes how Mechanism thinks about keyword strategy — not just which keywords have volume, but which ones are winnable, worth winning, and map to real revenue upside.

The output is a prioritized keyword target list with strategic rationale, SERP assessments, and a revenue upside estimate for the top opportunities.

---

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the PortCo being analyzed
- **Domain** — root domain (e.g., primeputt.com)
- **Product category** — what the brand sells and who buys it
- **Known competitors** (optional) — any competitors the team already knows
- **CVR / AOV / LTV** (optional but ideal) — needed to map traffic to revenue upside

If CVR/AOV/LTV aren't available, note this in the output and use directional estimates from competitor traffic data.

---

## How Mechanism Thinks About Keywords

Before running the workflow, understand the philosophy:

**We are sizing revenue upside, not just keyword volume.** The goal is to find keywords where: (a) a real customer is searching with intent to buy, (b) we have a realistic path to ranking or appearing, and (c) the traffic, if captured, maps to meaningful revenue.

**The competitor benchmark is the starting point.** Every Mechanism company exists because there's a competitor we're trying to replicate and out-sophisticate. Keyword strategy starts by understanding what's already working for them.

**SERP composition determines whether ranking is worth it.** A keyword with 20k monthly searches but a cluttered SERP (AI overview, product tiles, shopping units, video) may capture fewer clicks at P1 than a cleaner 5k keyword. Evaluate click capture, not just volume.

**The key question is not just "can we rank" — it's "if we rank, does it drive conversions?"** High volume + wrong intent = wasted effort. Example: "ADHD test" is high volume but skews toward people looking for a free quiz, not telehealth services.

---

## Workflow

### Step 1: Competitor Identification

Search Google for 3–5 of the most obvious product-category terms. Observe who's ranking in the top 10 organic positions. Note:
- Direct brand competitors (same product type)
- Editorial/review sites ranking for the category
- Any Mechanism-adjacent domains (TPVs or similar)

Pull the brand's top organic competitors from Ahrefs:
```
Ahrefs: site-explorer-organic-competitors
target: [brand domain]
country: us
```

Cross-reference SERP findings with Ahrefs data. Build a shortlist of 3–5 true competitors — brands most similar to what this PortCo is trying to become. These are your benchmarks.

---

### Step 2: Competitor Keyword Mining

For each benchmark competitor, pull their top organic keywords via Ahrefs:
```
Ahrefs: site-explorer-organic-keywords
target: [competitor domain]
country: us
```

Filter for:
- Non-branded keywords only (exclude competitor brand names)
- Keywords with clear commercial intent (buying, best, review, comparison)
- Volume ≥ 500/month
- Exclude navigational or irrelevant terms

Compile a raw keyword list from across all competitors. This is your universe of possible targets.

---

### Step 3: Keyword Expansion

For the top 10–15 keywords from the competitor mine, expand via Ahrefs to surface related terms:
```
Ahrefs: keywords-explorer-matching-terms
country: us
keywords: [top seed keywords]
```

Also pull search suggestions:
```
Ahrefs: keywords-explorer-search-suggestions
country: us
keywords: [top seed keywords]
```

Look for:
- Higher-intent modifiers ("best [product]", "top [product]", "[product] review")
- Comparison terms ("[brand] vs [brand]")
- Problem-aware terms ("how to [solve problem product solves]")
- Long-tail variants with lower competition but clear buyer intent

---

### Step 4: SERP Evaluation — Winnability & Click Capture

For each candidate keyword, manually search Google and evaluate:

**Winnability signals:**
- What is the DR of domains in the top 5 positions?
- How old and established are the ranking sites?
- How many backlinks do the top-ranking pages have?
- Is the content from authoritative category sources or general sites?

**SERP composition signals (click capture):**
- Is this a clean blue-link SERP or cluttered with product tiles, ads, AI overview, video, shopping units?
- Does the intent match our product? Would someone searching this actually buy what we sell?
- What's the realistic CTR at P1 given the SERP composition?

**Categorize each keyword:**
- 🟢 **Winnable / High click capture** — realistic path to ranking, clean SERP, strong intent
- 🟡 **Winnable / Low click capture** — can rank but messy SERP limits clicks; consider editorial layer instead
- 🔴 **Not winnable near-term** — DR 80+ competitors, .edu-heavy, years of authority required
- ⚪ **Wrong intent** — volume exists but searchers aren't buyers

---

### Step 5: Revenue Upside Mapping

For 🟢 and 🟡 keywords, estimate revenue potential:

If CVR / AOV / LTV are available:
```
Monthly traffic at P1 = [keyword volume] × [estimated CTR at P1 for this SERP type]
Revenue upside = Monthly traffic × CVR × AOV
```

Use these rough CTR benchmarks for P1 (2026 reference ranges — adjust based on actual SERP composition):
- **Clean blue-link SERP, high intent** (e.g. "best putting mat"): ~15–25%
- **Mixed SERP, commercial intent** (some ads, some rich results): ~8–15%
- **Heavy ecommerce SERP** (product tiles, shopping units, AI overview, ads): ~3–7%
- **Branded queries** (user already knows the brand): ~30–40%

Important: These are directional starting points, not fixed rules. CTR is highly dependent on SERP composition, snippet strength, and brand familiarity. Always look at the actual SERP before estimating. A keyword with 3% CTR at P1 but 20k volume may still be worth more than a 25% CTR keyword at 500 volume. Do the math both ways.

If CVR / AOV / LTV are not available, use competitor traffic as a proxy:
```
Competitor monthly traffic for keyword (from Ahrefs) × their estimated CVR for this category
```

Also note CPC as a directional signal of commercial value. High CPC = high commercial intent.

---

### Step 6: TPV vs. Core Domain Decision

For each 🟡 keyword (winnable but low click capture on core domain), evaluate:
- Is there an editorial layer ranking on this SERP? (roundups, "best of" content)
- Could a Mechanism TPV domain credibly compete for the editorial positions?
- Is there an existing Mechanism TPV that could target this keyword?

Flag keywords where **TPV is the better vehicle** rather than going after them on the core domain. This is not a decision to make unilaterally — flag it for strategy discussion.

Note: In an ideal world, money keywords always go to the core domain. TPV is a tactical vehicle for SERPs where direct competition isn't viable near-term.

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
