---
name: page-optimizer
description: >
  Audits an existing page's on-page SEO against a target keyword, the live SERP, and specific competitors — then produces a prioritized optimization plan. Use this skill whenever someone wants to improve an existing page's ranking, close the gap on a specific competitor, or understand why a page isn't ranking where it should. Trigger phrases include "why isn't our page ranking for X", "how do we beat [competitor] for X", "audit our page for keyword X", "what's wrong with our PDP for X", "how do we optimize [URL] for [keyword]", "on-page audit for X", "what should we change on this page to rank better", "compare our page to BirdieBall", or any request that combines an existing URL + a keyword + intent to improve. Works for any page type — PDP, category page, editorial/blog, landing page. Always produces a page-type-aware optimization plan, not generic SEO advice.
compatibility: "Requires: URL of the page to audit (user provides or fetchable), target keyword. Optional but preferred: Ahrefs MCP (serp-overview) for SERP data, web_fetch for competitor page analysis. Falls back to web search if Ahrefs unavailable."
---

# Page Optimizer

This skill audits an existing page against a target keyword, the live SERP, and named competitors — and produces a concrete, prioritized optimization plan. It answers: **what specifically needs to change on this page to rank higher for this keyword?**

The output is not a generic SEO checklist. It is a page-type-aware, competitor-informed action plan with specific rewrites, structural changes, and content additions the team can execute immediately.

---

## Inputs Required

- **Target URL** — the page being audited (e.g., primeputt.com/products/golf)
- **Target keyword** — the primary keyword to optimize for (e.g., "indoor putting mat")
- **PortCo domain + DR** — for authority context
- **Primary competitor URL** (optional but high-value) — the page you're trying to beat (e.g., BirdieBall's product page at P1)
- **Additional competitors** (optional) — up to 2 more P1–3 URLs for pattern analysis

If the user doesn't provide competitor URLs, pull them from `serp-overview` for the target keyword and use P1–3.

---

## Page Type Classification

Before auditing, identify the page type — this determines what "good" looks like and what the optimization plan should prioritize.

| Page Type | Primary Goal | Key On-Page Signals |
|-----------|-------------|---------------------|
| **PDP (Product Detail Page)** | Convert + rank transactionally | Title tag, H1, product description, specs, schema, reviews, internal links |
| **Category/Collection Page** | Capture commercial/transactional intent at scale | H1, intro copy, product grid, filters, internal link density |
| **Editorial/Blog Post** | Capture informational or commercial intent | Title, H1/H2 structure, depth, E-E-A-T signals, internal links to money pages |
| **Landing Page** | Capture one intent, convert | Single keyword focus, CTA alignment, proof elements |
| **Comparison Page** | Capture commercial intent for "vs/alternative" queries | Structured comparison, schema, named competitors, verdict |

---

## Workflow

### Step 1 — Fetch the Target Page

⚠️ **Critical:** Most modern ecommerce pages (Shopify, BigCommerce, Webflow, headless CMS) render significant content via JavaScript after page load. `web_fetch` performs a static HTTP GET and will miss this content entirely — including product descriptions, reviews, FAQ sections, ingredient cards, and benefit grids. A thin `web_fetch` result on a live PDP is almost always a JS-rendering limitation, not a content gap.

**PREFERRED — Browser tools (when available):**

Use browser automation to extract signals from the fully rendered DOM:

```
// All headings
document.querySelectorAll('h1,h2,h3,h4').forEach(h => console.log(h.tagName, h.textContent.trim()))

// All schema markup
document.querySelectorAll('script[type="application/ld+json"]').forEach(s => console.log(s.textContent))

// All image alt text
document.querySelectorAll('img').forEach(i => console.log(i.alt || '[empty]', i.src))

// Full page text
document.body.innerText
```

Also use `get_page_text` for full rendered body content and `screenshot` for visual layout context.

Extract:
- Title tag (exact text)
- Meta description (exact text)
- H1 (exact text)
- H2s and H3s (full heading structure)
- First 150 words of body copy
- Product description / main copy block (for PDPs)
- All page sections and their content (value props, ingredients, how-to-use, FAQ, reviews, etc.)
- Internal links present on page (anchor text + destination)
- Schema markup present (product, review, FAQ, breadcrumb, etc.)
- Image alt text for all images — flag if multiple images share identical alt text
- Word/content length estimate

**FALLBACK — `web_fetch` only when browser tools unavailable:**

Use `web_fetch` on the target URL. Then immediately apply this sanity check:

> **Completeness check:** Does the returned content seem reasonable for this page type?
> - PDP with 0–1 H2s → likely incomplete fetch
> - PDP with no FAQ, reviews, or benefit sections → likely incomplete fetch
> - Any live page returning fewer than 200 words of body copy → almost certainly JS-rendered
>
> If the result looks thin: state explicitly — *"⚠️ web_fetch returned limited content. This page likely renders content via JavaScript. The content inventory below may be incomplete — verify key sections manually or with browser tools before acting on this audit."*
>
> **NEVER conclude a page has no content based solely on a thin web_fetch result.**

If `web_fetch` is also unavailable, ask the user to paste the page content or describe the page structure.

---

### Step 2 — Pull SERP Data

Call `serp-overview` for the target keyword:
- Note P1–10 positions, domains, DR, RDs
- Identify where the PortCo currently ranks
- Identify the primary competitor(s) to close the gap on
- Flag SERP features: AIO, featured snippet, shopping snippets, PAA

If Ahrefs is unavailable, use web search to identify P1–3 results and note which page types are ranking.

---

### Step 3 — Fetch Competitor Pages

Apply the same browser-first approach from Step 1 to the primary competitor URL (and up to 2 additional P1–3 URLs).

⚠️ **Same JS-rendering caveat applies.** Competitor Shopify/BigCommerce/Webflow pages have the same problem. If you compare a thin `web_fetch` result from the PortCo page against a thin `web_fetch` result from a competitor, you may be comparing two incomplete views — making the gap analysis unreliable. Use browser tools for competitor pages too when available.

Extract the same signals as Step 1:
- Title tag, H1, heading structure
- Copy length and depth
- Schema markup
- Key topics and sections covered
- Internal linking patterns
- Reviews/social proof signals

Build a side-by-side comparison of the PortCo page vs. primary competitor across each signal.

---

### Step 4 — Keyword Alignment Audit

Evaluate how well the target page is optimized for the target keyword across every on-page signal:

**Title Tag**
- Does the target keyword appear in the title tag?
- Is it near the front (first 60 characters)?
- Is the title tag compelling for CTR (includes brand, benefit, or differentiator)?
- Compare to competitor title tag — what are they doing differently?

**Meta Description**
- Does it include the target keyword naturally?
- Is it within 155 characters?
- Does it have a clear CTA or value prop?

**H1**
- Does the H1 contain the target keyword (exact or close variant)?
- Is there only one H1?
- Compare to competitor H1

**Heading Structure (H2s/H3s)**
- Do H2s cover the semantically related subtopics that competitors cover?
- Are there H2s missing that appear in P1–3 competitor structures?
- Flag heading gaps — topics present in competitors but absent from the PortCo page

**Body Copy**
- Does the target keyword appear in the first 100 words?
- What is the keyword density (rough estimate — flag if absent or overused)?
- Are semantically related terms present? (for "indoor putting mat" this might include: practice green, putting stroke, golf training aid, true roll, speed control, distance control)
- What is the content depth vs. competitors? (thin = missing key sections they cover)

**Schema Markup**
- For PDPs: Is Product schema present? Does it include name, description, price, availability, review aggregate?
- For editorial: Is Article or FAQ schema present?
- Flag missing schema that competitors have

**Internal Links**
- Does the page receive internal links from other pages on the site with relevant anchor text?
- Does the page internally link to other relevant pages (supporting content, related products)?
- Flag internal linking gaps vs. competitors

**Image Optimization**
- Are primary images using descriptive, keyword-relevant alt text?
- Flag generic alt text (e.g., "IMG_001.jpg" or empty alt)

---

### Step 5 — Competitor Gap Analysis

Produce a direct comparison table: PortCo page vs. primary competitor, signal by signal.

Then write a narrative gap summary:
- What is the primary competitor doing that the PortCo page is not?
- Is the gap primarily on-page (content, structure, copy) or off-page (authority, links)?
- If the PortCo has comparable or higher DR than the competitor but ranks below them — the problem is almost certainly on-page. Flag this clearly.
- Identify the 2–3 highest-leverage gaps to close first

---

### Step 6 — Semantically Related Keywords

Identify the semantic keyword cluster the page should cover to rank for the target keyword. These are not additional target keywords — they are the supporting terms that signal topical relevance to Google.

Sources for semantic terms:
- PAA questions from the SERP (what is Google surfacing as related questions?)
- H2/H3 topics present in P1–3 competitor pages
- Common modifiers found across P1–3 titles and copy (e.g., "indoor", "practice", "true roll", "speed", "distance")

Present as a flat list of 8–15 terms the page should naturally include in copy, headings, or schema.

---

### Step 7 — Produce the Optimization Plan

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
