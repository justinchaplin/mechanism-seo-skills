---
name: serp-analysis
description: >
  Analyzes the full first-page SERP for any keyword and produces actionable intelligence on what's winning and how to crack in. Use this skill whenever someone wants to understand a SERP before going after it — trigger phrases include "what's ranking for X", "analyze this SERP", "what's on page one for X", "what type of content is winning for X", "how do I crack into this SERP", "what does page one look like for X", "is there an AI Overview for X", "what format is winning on this SERP", or any request that combines a keyword with intent to understand the competitive landscape before executing. Always run this skill before the SEO Entry Plan when SERP context is needed. Works with or without a PortCo context — can be run as pure research or as a first step in an entry plan.
compatibility: "Requires Ahrefs MCP (serp-overview). Pairs with SEO Entry Plan skill as the upstream research step."
---

# SERP Analysis

This skill takes a target keyword and produces a complete first-page SERP breakdown — what's ranking, what formats are winning, what SERP features exist, and what it would take to crack in. It answers: **what does page one look like for this keyword, and what does winning here require?**

The output is a strategic read of the SERP that gives a team member everything they need to decide whether and how to pursue a keyword — before writing a single word or building a single link.

---

## Inputs Required

- **Target keyword** — the SERP to analyze (e.g., "best AG1 alternative", "mosquito repellent", "laundry detergent sheets")
- **PortCo domain** (optional) — if provided, flag where the PortCo currently ranks and what the gap looks like
- **Country** — default US unless specified

---

## Workflow

### Step 1 — Pull SERP Data via Ahrefs

Call `serp-overview` for the target keyword:
- Target: the keyword as entered
- Country: US (or as specified)
- Pull: position, URL, domain, DR, referring domains, page type, traffic estimate

If `serp-overview` is unavailable, note this and proceed with web search to manually identify P1–10 results, flagging that DR/RD data will be estimated.

---

### Step 2 — Classify Search Intent

Before mapping the SERP, identify the dominant intent — this determines what vehicle and content format to recommend at the end.

| Intent | SERP Signals | What the User Wants | Winning Format |
|--------|-------------|---------------------|----------------|
| Informational | Wikipedia, knowledge panels, "what is" queries | Learn something | Guide, explainer, tutorial |
| Commercial | Reviews, comparisons, "best X" queries | Compare options | Comparison, listicle, review |
| Transactional | Product pages, shopping results, "buy X" | Purchase something | Product page, PDP |
| Navigational | Brand homepage, login pages | Find a specific site | Homepage, brand page |

Note the confidence level — what % of P1–10 results support the classification. Flag mixed intent explicitly (e.g., commercial + informational), as it means multiple content formats can coexist on the SERP and opens up more vehicle options.

---

### Step 3 — Map the SERP Landscape

For each P1–10 result, classify:

**Page Type**
- Product/PDP — a brand selling directly
- Category/Collection — a brand's collection or category page
- Editorial/Review — a media site, blog, or review aggregator ranking a list or review
- Comparison — "X vs Y" or "X alternative" style content
- Forum/UGC — Reddit, Quora, community threads
- Aggregator — Amazon, Walmart, retailer listing pages
- Informational — how-to, educational, definition content

**Domain Type**
- Direct brand (e.g., ag1.com, primeputt.com)
- Third-party editorial (e.g., healthline.com, mygolfspy.com)
- Retail aggregator (e.g., amazon.com, walmart.com)
- UGC platform (e.g., reddit.com, quora.com)

**Authority Signal** — DR and referring domains per result

---

### Step 4 — Identify SERP Features

Flag every SERP feature present:

| Feature | Present? | Notes |
|---------|----------|-------|
| AI Overview (AIO) | ✅/❌ | What does it say? What sources does it cite? |
| People Also Ask | ✅/❌ | List the PAA questions |
| Shopping/Product Snippets | ✅/❌ | What products are listed? Price range? |
| Featured Snippet | ✅/❌ | What format (paragraph, list, table)? Which URL owns it? |
| Image Pack | ✅/❌ | — |
| Video Carousel | ✅/❌ | — |
| Local Pack | ✅/❌ | — |
| Knowledge Panel | ✅/❌ | — |

**AI Overview is the most important feature to flag.** If an AIO is present:
- What question is it answering?
- What sources is it citing (domains, not just URLs)?
- Is the PortCo cited or absent?
- What format is the AIO (list, paragraph, comparison table)?
- Does the AIO likely reduce click-through to organic results?

---

### Step 5 — Analyze What’s Winning

Identify the dominant patterns across P1–10:

**Content Format**
- What type of content owns the top 3 positions? (product pages, editorial lists, comparisons, forums)
- Is there a clear format winner, or is the SERP mixed?
- What's the average estimated content length for editorial results? (flag thin vs. comprehensive)

**Authority Bar**
- What's the DR range of P1–3 results?
- What's the referring domain range of P1–3 results?
- Is the SERP dominated by high-DR editorial sites (DR 60+), or is it winnable by a brand with moderate authority?

**Brand vs. Editorial Mix**
- How many of P1–10 are brand/product pages vs. editorial/third-party?
- This determines the vehicle — if P1–5 is all editorial, a product page alone won't win here

**Commercial Intent Signals**
- Are shopping snippets present? (signals high transactional intent)
- Are product pages ranking? (signals Google surfaces commercial content for this query)
- Is the PAA box informational or commercial?

**Content Gaps**
- What topics or angles are missing across P1–10? (e.g., no comparison of X vs Y, no content addressing a specific use case)
- Which competitors are thin on depth or specificity?
- Is there a format gap? (e.g., everyone has a listicle but no comprehensive guide, or no video when PAA questions are how-to)
- These gaps inform what a new entrant needs to do differently to earn a position, not just match what’s there

**Word Count Benchmark**
- Estimate content length for P1–3 editorial results (thin = <800 words, mid = 800–2,000, comprehensive = 2,000+)
- Target: competitor average + ~20% for a new entrant — enough to signal depth without padding

---

### Step 6 — Flag the Opportunity & Barriers

**Opportunity Assessment**
- Is there a clear gap in the top 10 that the PortCo could fill?
- Is the PortCo's page type (product vs. editorial) represented in the top 10?
- Are any P1–10 results weak on authority relative to their position? (potential displacement targets)
- Does an AI Overview dominate the top of page, potentially cannibalizing organic clicks?

**Barriers to Entry**
- DR bar to compete (e.g., "P1–3 requires DR 50+ with 30+ RDs")
- Format mismatch (e.g., "SERP is entirely editorial — a product page alone won't rank here")
- AIO displacement (e.g., "AI Overview answers this query directly — organic CTR may be significantly reduced")
- Brand dominance (e.g., "The brand itself owns P1 and P2 — this SERP is already locked")

---

### Step 7 — Produce the SERP Snapshot Output

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
