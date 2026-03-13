---
name: seo-entry-plan
description: Converts non-branded keyword research output into a concrete SEO execution plan for a Mechanism PortCo. Use this skill whenever someone asks how to start ranking for a keyword, what to do to rank on a SERP, how to enter a category organically, or what the SEO action plan is. Trigger phrases include "how do we rank for X", "what do we need to do to rank", "build me an entry plan for X", "what's the action plan to get to P1", "how do we get on this SERP", "where do we start for [brand] SEO", or any request that combines a brand + a keyword + intent to rank. This skill takes keyword research (ideally from the Non-Branded Keyword Research skill) as input and produces a page-level execution brief that a team member can act on immediately. Always use this skill rather than giving manual advice.
compatibility: "Requires Ahrefs MCP (serp-overview, keywords-explorer-overview). Works with or without prior Non-Branded Keyword Research output — can run keyword research inline if needed."
---

# SEO Entry Plan

This skill takes a target brand, a target keyword or category, and SERP data — and produces a concrete, page-level execution brief. It answers: **what do we actually build or optimize, and what does it take to rank?**

The output is an action plan a team member can execute, not a strategy deck. It specifies the target URL, page type, title tag, content direction, competitive gap, and link building bar — so there's no ambiguity about what to do next.

---

## Inputs Required

- **Brand name** — the PortCo being analyzed
- **Domain** — root domain (e.g., hellopest.com)
- **Target keyword(s)** — the SERP(s) to enter (can come from Non-Branded Keyword Research output or stated directly)
- **PortCo DR** — domain rating (pull from Ahrefs if unknown)
- **Existing pages** — any existing pages targeting these keywords (can be "none")
- **CVR / AOV** (optional) — for revenue upside framing in the output

If keyword research hasn't been run yet, run `keywords-explorer-overview` to confirm volume and difficulty before proceeding. If SERP data isn't available, call `serp-overview` as the first step.

---

## How Mechanism Thinks About SEO Entry

Before running the workflow, understand the philosophy:

**The goal is P1–3 on the core domain.** A new brand with DR < 20 might need foundational work before targeting high-competition terms, but the roadmap should always point toward the core domain owning the money keywords.

**SERPDom is the ideal end state.** The brand should appear in multiple SERP positions — ideally a product page at P1–3 and editorial coverage (earned media) at P1–3 simultaneously. When building the entry plan, identify which positions are realistically acquirable and sequence toward full SERPDom over time.

**The competitive gap is on-page before it's off-page.** If a competitor ranks above the PortCo despite weaker domain authority, the problem is almost certainly on-page (title tag, copy, internal links, schema) — not link equity. Diagnose this before recommending link building.

**New domain vs. established domain changes the sequencing.** A DR < 15 domain needs foundational authority before targeting competitive terms. A DR 40+ domain may just need on-page optimization. The plan should reflect the actual starting point.

---

## Workflow

### Step 1: Confirm the SERP Landscape

Pull `serp-overview` for each target keyword if not already available:

```
Ahrefs: serp-overview
keyword: [target keyword]
country: us
select: position, url, title, domain_rating, page_type, type, traffic, refdomains
top_positions: 10
```

From the results, extract:
- **Target position** — what position are we trying to reach? (Usually P1–3)
- **Current PortCo position** — is the brand already ranking anywhere?
- **SERPDom opportunities** — is the brand featured in any editorial content already ranking? (e.g., "Best [Product]" roundup that includes the brand)
- **Competitive bar at the target position** — DR and refdomains of the page currently holding that position
- **SERP features** — AI overview, shopping units, PAA, organic shopping? Each feature above P1 reduces click capture
- **Page type at target position** — product page (`/Listing/Product`), editorial (`/Article/Product_or_Brand_Review`), UGC (Reddit, forums), or other

Record these clearly — they drive every decision downstream.

---

### Step 2: Diagnose the Gap

Compare the PortCo's current position (if any) to the target position, and the PortCo's domain metrics to the competitor currently holding the target position.

**If the PortCo is already in the SERP but ranking below a weaker competitor:**
→ This is almost certainly an on-page problem. The authority is there — the page isn't optimized.
→ Diagnose: title tag match, keyword coverage in headings and copy, internal links pointing to this page, schema markup.

**If the PortCo isn't in the SERP at all:**
→ Check if a relevant page exists on the domain. If yes, it likely has crawlability or relevance issues.
→ If no page exists, the plan starts with page creation.

**If the PortCo DR is significantly lower than competitors at the target position (15+ DR points):**
→ Authority gap is a real factor. Note how many referring domains the target position page has — that's the link building bar.
→ On-page optimization still comes first (authority won't help an under-optimized page), but include a link building requirement in the plan.

**Authority gap benchmark:**
- Target position page has 0–10 RDs → link building likely not the primary lever
- Target position page has 10–50 RDs → achievable link building gap, include in 3–6 month plan
- Target position page has 50+ RDs → significant investment, flag timeline honestly

---

### Step 3: Define the Vehicle and Target URL

Based on the SERP diagnosis, determine what page should rank:

**Option A: Optimize an existing page**
The PortCo has a product or category page that's already in or near the SERP. The plan is to optimize it — not create something new.

**Option B: Create a new product/category page**
No relevant page exists. Build one targeting the keyword cluster.

**Option C: Create supporting content**
The money keyword is best approached via an editorial layer on the core domain (roundup, comparison, category guide). Valid for informational-adjacent terms where a product page alone isn't the right format.

**Option D: Earned media / PR**
The best SERP positions are held by high-DR editorial sites (DR 70+) with extensive backlink profiles. Direct ranking on the core domain isn't viable near-term. The play is getting the brand featured in existing top-ranking editorial content — pitching roundup authors, contributing expert quotes, or running a PR campaign around a product claim. This is a growth/PR lever, not a pure SEO lever — flag it as such and hand off to the appropriate team.

For Options A, B, and C, define:
- **Target URL** — exact URL the optimized or new page should live at (e.g., `hellopest.com/products/mosquito-trap`)
- **Primary keyword** — the single keyword this page should be most optimized for
- **Supporting keywords** — 3–5 closely related terms this page should also rank for (pull from `keywords-explorer-overview` or related SERP data)

---

### Step 4: Write the Page Brief

This is the core output of the skill. For the target URL and keyword, specify:

**Title Tag**
Write the recommended title tag. Follow this formula:
- Lead with the primary keyword
- Include the brand name at the end
- Keep under 60 characters
- Match the style of high-performing competitor title tags on this SERP

Example: `Best Mosquito Trap for Outdoors | HelloPest`

**Meta Description** (optional but include if the SERP shows rich snippets)
One sentence that includes the primary keyword and a benefit-driven hook. Under 155 characters.

**H1**
Usually matches or closely mirrors the title tag. Can be slightly longer.

**Content Direction**
What does this page need to cover to match or beat the current P1–3 content?
- Word count benchmark (pull from SERP winner — note their word count if visible)
- Key sections the page should include based on competing pages and PAA questions
- Buyer intent signals to include (pricing, comparisons, specific use cases)
- E-E-A-T signals relevant to this category (test data, expert credentials, first-hand use)

**Internal Linking**
What pages on the site should link to this target page? (Blog posts, homepage, category nav, related product pages)
This is often the fastest win — internal links pass authority and signal relevance.

**Schema**
What structured data should this page have?
- Product pages: `Product` + `AggregateRating` (if reviews exist)
- Category/roundup pages: `ItemList`
- Blog/editorial: `Article`
- FAQ sections: `FAQPage` (note: Google restricted FAQ rich results — only use if the page serves gov/health content)

---

### Step 5: Set the Link Building Bar

Based on Step 2, state whether link building is required and if so, what the bar is:

**If on-page gap only:**
> Link building is not the primary lever here. Focus on page optimization first. Reassess in 60–90 days once the page is live and indexed.

**If authority gap exists:**
> Target position currently held by [competitor] with [X] referring domains. PortCo page has [Y] referring domains. Gap: [X - Y] referring domains needed.
> Recommended approach: [outreach / digital PR / linkable asset] targeting [link type — category relevant blogs, golf publications, etc.]
> Timeline: [X months to close gap at realistic acquisition pace]

Note: Never recommend link building as Step 1 if the page isn't optimized. Links to a weak page don't move rankings.

---

### Step 6: SERPDom Sequencing

Lay out what the full SERPDom picture looks like for this keyword once the plan is executed — and what the sequencing is to get there:

**Phase 1 (0–90 days):** Page creation or optimization. Internal linking. Schema. Get indexed and establish baseline ranking.

**Phase 2 (90–180 days):** Link building if required. Monitor ranking movement. Update content based on SERP shifts.

**Phase 3 (180+ days):** Earned media push — once the page is ranking P3–8, pitch editorial sites for inclusion in their roundups. This creates the SERPDom stack (brand at P1 via editorial + brand at P2–3 via product page).

Flag if Phase 3 (earned media) is already partially achieved — e.g., if the brand is already featured in a top-ranking roundup, note this as existing SERPDom and build on it.

---

## Output Format

---

**SEO Entry Plan — [Brand Name]**
*Target keyword(s): [keyword(s)]*
*Prepared: [date]*

**SERP Snapshot**
| Position | Page | Type | DR | RDs | Notes |
|---|---|---|---|---|---|
| P1 | [url] | [type] | [DR] | [RDs] | |
| P2 | ... | | | | |
| ... | | | | | |
| Current PortCo position | [url or "not ranking"] | | [DR] | [RDs] | |

**SERPDom Audit**
[Note any positions where the brand already appears through earned media or editorial coverage. This is existing SERPDom to build on.]

**Gap Diagnosis**
[1–2 sentences: is this an on-page gap, an authority gap, or both? What's the primary lever?]

**Vehicle:** [Optimize existing page / Create new page / Earned media]

**Target URL:** `[exact URL]`

---

**Page Brief**

*Title Tag:* `[recommended title tag]`

*Meta Description:* `[recommended meta description]`

*H1:* `[recommended H1]`

*Primary Keyword:* [keyword]
*Supporting Keywords:* [keyword 1], [keyword 2], [keyword 3]

*Content Direction:*
[Bullet points covering: word count target, key sections to include, buyer intent signals, E-E-A-T requirements for this category]

*Internal Linking:*
[Which existing pages should link to this target page, and with what anchor text]

*Schema:*
[What schema types to implement and why]

---

**Link Building Requirement**
[Either "not the primary lever — focus on on-page first" or: specific referring domain gap, recommended link types, and realistic timeline]

---

**SERPDom Sequencing**

- **Phase 1 (0–90 days):** [specific actions]
- **Phase 2 (90–180 days):** [specific actions]
- **Phase 3 (180+ days):** [earned media / SERPDom completion]

**Target state:** [Describe what full SERPDom looks like for this keyword once the plan is complete — e.g., "Product page at P2, brand featured in P1 editorial roundup."]

---

## Judgment Guidelines

These encode how Mechanism evaluates SEO entry — not generic best practices:

- **On-page before off-page.** If a competitor ranks above the PortCo despite weaker domain authority, fix the page before buying links. Links to an under-optimized page don't move rankings.
- **Internal links are free and fast.** They're almost always underused on PortCo sites. Point to the target page from the homepage, blog, and related product pages. This alone can move rankings for low-competition terms.
- **Title tag is the highest-leverage on-page change.** If the primary keyword isn't in the title tag, nothing else matters until it is. Write a specific recommendation — don't say "include the keyword in the title."
- **DR gap < 15 is usually not the real problem.** Most PortCo on-page issues are simpler: wrong keyword in title, thin copy, no internal links. Diagnose on-page first.
- **Earned media > built editorial.** Getting featured in an existing high-DR roundup is faster and more valuable than building new infrastructure. If P1 is held by a DR 70+ editorial site, the play is PR — pitch for inclusion, don't try to outrank them.
- **Be honest about timelines.** A DR 1 domain targeting a KD 20+ keyword is a 12–18 month project minimum. Don't obscure this. State it clearly so the team can make a resource decision.
- **SERPDom is the goal, not just a ranking.** The plan should always point toward the brand appearing in multiple positions — product page + editorial feature. Build toward this even if Phase 3 is 12 months away.

---

## Example Trigger Phrases

- "How do we rank for mosquito repellent traps for HelloPest?"
- "What's the SEO action plan for PrimePutt on 'best putting mat'?"
- "We want to get on page 1 for [keyword] — what do we do?"
- "Build me an entry plan for HeySunday targeting laundry sheets"
- "What does it take to rank for [keyword]?"
- "Where do we start with SEO for [new PortCo]?"
- "We're at P8 for [keyword] — how do we get to P1?"
