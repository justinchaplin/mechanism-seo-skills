---
name: content-strategy
description: Determines what content a Mechanism portfolio company should create, why, and in what order — informed by competitor analysis, keyword research, and business impact. Also provides the E-E-A-T quality framework used to evaluate and brief content once the strategy is set. Use this skill whenever someone asks about content strategy, what content to create, what pages to build, content planning, content roadmap, or how to prioritize content for a PortCo. Also trigger when someone asks to audit content quality, check E-E-A-T signals, evaluate thin content, or assess whether existing content is up to standard. Trigger when someone says things like "what should [brand] be writing about", "what content do we need for [brand]", "build a content plan for [brand]", "what pages should we create", "is this content good enough to rank", or "does this page have strong E-E-A-T". Always use this skill rather than giving generic content advice.
compatibility: "Requires Ahrefs MCP (for competitor content analysis, keyword data, and traffic estimates) and web_search (for SERP and category research). Requires PortCo knowledge file for business context and money keywords."
---

# Content Strategy

This skill has two parts that work together:

**Part 1 — Content Strategy:** Determines what content to create, why, and in what order. The output is a prioritized content roadmap with rationale.

**Part 2 — E-E-A-T Quality Framework:** The standard all content must meet. Used when briefing new content, auditing existing content, or evaluating whether a page is performing to its potential.

---

## How Mechanism Thinks About Content

Every piece of content must serve the business. Traffic that doesn't connect to a customer decision, a ranking goal, or a link building opportunity is not worth creating. An article about "cool things to do in a small bathroom" for a laundry brand might get impressions — it does nothing for the business.

**Content and links are symbiotic.** The best content earns links because it's genuinely useful to people in the category. When developing content strategy, always ask: would someone in this space want to reference or share this? If yes, it's a link building asset too.

**Competitor content is the fastest path to a roadmap.** If competitors are ranking for a keyword with a specific type of page, that's signal — not just that the keyword is worth targeting, but that the content format works for that SERP.

**E-E-A-T is the quality bar.** Google's quality rater guidelines are built around Experience, Expertise, Authoritativeness, and Trustworthiness. Generic AI-generated content that says nothing new will not rank and will not earn links. Content needs a genuine point of view. The Helpful Content System was merged into Google's core ranking algorithm in March 2024 — helpfulness signals are now weighted continuously, not through separate updates.

---

## The Four Content Types

Every content recommendation maps to one of four types. Each has a different job:

**1. Money Pages**
Pages designed to rank for high-intent, non-branded money keywords and convert. The most important pages on the site. Must be optimized for both search and conversion.
*PrimePutt example: PDP targeting "best putting mat"*

**2. Supporting Content**
Articles, guides, and pages that build topical authority around money keywords. Help money pages rank by establishing the site as a category expert. May not convert directly but create the authority scaffolding that makes money pages rank.
*PrimePutt example: "Are indoor putting mats worth it?" — intercepts a real buyer question, builds topical authority*

**3. Linkable Assets**
Original data, studies, tools, or perspectives designed to earn editorial links. High-effort, high-reward. Not every PortCo needs this at early stages — only recommend when the PortCo has original data, a unique perspective, and the category has publications that cover it.
*PrimePutt example: "My handicap dropped by 5 after these 10+ putting drills" — original, specific, shareable*

**4. Informational Content**
Educational content that addresses questions buyers ask before or during the purchase process. Only worth creating if it intercepts a real buyer at a real decision point — not a pure traffic play.
*PrimePutt examples: "Why is PrimePutt so expensive?" / "PrimePutt vs BirdieBall" — high intent, brand-aware, close to a buying decision*

---

# PART 1: CONTENT STRATEGY WORKFLOW

## Inputs Required

- **Brand name** and **domain**
- **Product category** — what the brand sells and who buys it
- **Money keywords** — from the Non-Branded Keyword Strategy skill if already run; otherwise derive here
- **Existing content** — any pages already published (optional but useful)
- **CVR / AOV** — to map content traffic potential to business impact

---

### Step 1: Map Existing Content

If the PortCo already has content, pull their top pages from Ahrefs:

```
Ahrefs: site-explorer-top-pages
target: [brand domain]
country: us
```

Assess:
- Which pages are already getting organic traffic?
- Which money keyword pages exist but aren't ranking?
- Are there obvious gaps vs. what competitors have?
- Are any existing pages worth optimizing rather than creating new ones?

**Fix before you build.** If a money page exists but isn't ranking, optimize it before creating new content. New content competes with existing pages for crawl budget and internal links.

---

### Step 2: Competitor Content Analysis

For each of the top 3 benchmark competitors, pull their top pages:

```
Ahrefs: site-explorer-top-pages
target: [competitor domain]
country: us
```

For each competitor, identify:
- What are their highest-traffic non-branded pages?
- What content types are working (product pages, roundups, guides, comparisons)?
- What keywords are they ranking for that the PortCo isn't targeting?
- What content format dominates?

This tells you what the category rewards before you start creating.

---

### Step 3: Content Gap Analysis

Pull keywords competitors rank for that the PortCo doesn't:

```
Ahrefs: site-explorer-organic-keywords
target: [competitor domain]
country: us
```

Filter for:
- Non-branded keywords
- Commercial or transactional intent
- Volume ≥ 500/month
- Keywords the PortCo has no ranking page for

Cross-reference with the money keyword list from the Non-Branded Keyword Strategy skill if available. Flag high-priority keywords without a dedicated page — these are the most urgent content gaps.

---

### Step 4: SERP Format Analysis

For each priority keyword, search Google and observe what content format ranks:
- Long-form guide (2,000+ words)?
- Short, direct product/category page?
- Comparison or "best of" roundup?
- FAQ or tool?

**Format match is non-negotiable.** Creating a 300-word page for a keyword where P1 is long-form guides is a waste of effort. Match the format — don't fight it.

Also note:
- Does an AI Overview appear? If so, what question is it answering and what sources are cited?
- Are there featured snippets? What format triggers them?
- Google AI Mode (launched May 2025) provides a fully conversational experience with zero organic blue links — citation is the only visibility mechanism for AI Mode queries

---

### Step 5: Categorize and Prioritize

Organize all identified content opportunities into the four content types and sequence them:

**Money Pages — Highest Priority**
Built first. Must target one primary keyword clearly, be optimized for conversion, match the SERP format, and have a link building plan. These pages need links to rank.

**Supporting Content — Medium Priority**
Prioritize based on keyword volume, whether they support a high-priority money page, and whether competitors have this content driving traffic.

**Linkable Assets — Strategic**
Only recommend if the PortCo has original data or a strong brand voice, and the category has publications that cover original research.

**Informational Content — Low Priority Unless High Intent**
Only recommend if the searcher is clearly close to a buying decision and competitors are ranking for it driving meaningful traffic.

---

### Step 6: Build the Content Roadmap

**Phase 1 — Foundation (Month 1–2)**
Money pages for the top 3–5 priority keywords. Fix any existing pages that are clearly underperforming.

**Phase 2 — Authority Building (Month 2–4)**
Supporting content that builds topical authority around Phase 1 money pages. High-intent informational content that intercepts buyers.

**Phase 3 — Amplification (Month 4+)**
Linkable assets, content expansion, optimization of existing pages based on GSC performance data.

---

## Content Strategy Output Format

---

**Content Strategy — [Brand Name]**
*Analyzed: [date]*

**Existing Content Assessment:**
[2–3 sentences on what currently exists, what's working, what gaps are most urgent]

**Competitor Content Patterns:**
| Competitor | Top Content Type | Key Ranking Formats | Notable Gaps |
|-----------|-----------------|---------------------|-------------|
| ... | ... | ... | ... |

**Priority Content Gaps:**
| Keyword | Volume | Intent | Content Type | Format | Competitor Example |
|---------|--------|--------|-------------|--------|-------------------|
| ... | | | | | |

**Content Roadmap:**

Phase 1 — Foundation (Month 1–2):
- [Content]: [Target keyword, format, why priority 1]

Phase 2 — Authority Building (Month 2–4):
- [Content]: [Target keyword, how it supports Phase 1]

Phase 3 — Amplification (Month 4+):
- [Content]: [Type, goal, trigger condition]

**Link Building Leverage:**
[Which content pieces are best positioned to earn links — flag for the link building team]

**What NOT to Create:**
[Specific content ideas that would generate traffic but not business value for this PortCo]

**Recommended First Action:**
[One sentence — the single most important content piece to start with and why]

---

# PART 2: E-E-A-T QUALITY FRAMEWORK

Use this framework when briefing new content, auditing existing content, or evaluating whether a page is performing to its potential. Content that doesn't meet this bar won't rank in a competitive SERP regardless of the strategy behind it.

---

## E-E-A-T Dimensions

### Experience — Has a human actually done this?
The most underrated E-E-A-T signal. Google's quality raters are specifically trained to identify whether content reflects first-hand experience.

**Strong signals:**
- Original research, testing, case studies, before/after results
- Personal anecdotes and process documentation with specific details
- Unique data or proprietary insights not found elsewhere
- Photos or videos from direct product use or testing

**Weak signals:**
- Generic descriptions of how a product or process works without evidence of having done it
- Content that could have been written without touching the product
- Summaries of what other sources say without adding original perspective

### Expertise — Does the author know what they're talking about?
**Strong signals:**
- Author byline with relevant credentials or background
- Technical depth appropriate for the audience
- Accurate, well-sourced claims
- Definitions and explanations that demonstrate category fluency

**Weak signals:**
- Anonymous authorship
- Surface-level coverage that doesn't go beyond what any casual reader knows
- Factual errors or unsupported claims

### Authoritativeness — Is this a recognized voice in the category?
**Strong signals:**
- External citations and backlinks from authoritative sources
- Brand mentions across industry publications
- Expert quotes with attribution
- Entity presence: Wikipedia, Wikidata, recognized industry directories

**Weak signals:**
- No external recognition
- No citations to or from other authoritative sources
- No evidence the brand or author is known in the category

### Trustworthiness — Can the reader trust this source?
**Strong signals:**
- Contact information visible
- Privacy policy and terms of service present
- Publication date and last-updated date visible
- Customer testimonials and verifiable reviews
- HTTPS / secure site
- Transparent corrections when errors are found

**Weak signals:**
- No dates on content
- No contact information
- No reviews or social proof
- Unclear ownership or authorship

---

## Content Quality Checklist

Use this when reviewing a page before publishing or when diagnosing why an existing page isn't ranking.

**Structure:**
- [ ] Logical H1 → H2 → H3 heading hierarchy
- [ ] Question-based headings where appropriate (matches query patterns)
- [ ] Short paragraphs (2–4 sentences)
- [ ] Tables for comparative data
- [ ] Lists for multi-item content
- [ ] Table of contents for long-form content

**Keyword signals:**
- [ ] Primary keyword in title, H1, and first 100 words
- [ ] Natural density — present throughout without stuffing
- [ ] Semantic variations present (not just exact-match repetition)

**Content depth:**
- [ ] Covers the topic thoroughly for its type — use SERP format analysis to calibrate length, not arbitrary word count minimums. Word count is not a direct ranking factor. A 500-word page that fully answers the query will outrank a 2,000-word page that doesn't.
- [ ] Direct answer in first 40–60 words for informational queries (also improves AI citation)
- [ ] Original perspective or data point that isn't available elsewhere
- [ ] Accurate, specific claims — not vague generalities

**Author and trust signals:**
- [ ] Author byline with credentials or relevant background
- [ ] Publication date visible
- [ ] Last-updated date if content has been revised (flag content older than 12 months on fast-changing topics for a freshness review)
- [ ] Citations to primary sources where claims are made

**Multimedia:**
- [ ] Relevant images with descriptive alt text
- [ ] Video where appropriate
- [ ] Comparison tables for products or features

**Internal linking:**
- [ ] 3–5 relevant internal links per 1,000 words
- [ ] Descriptive anchor text
- [ ] Links to related money pages and supporting content
- [ ] No orphan pages — every page has at least one internal link pointing to it

**AI content signals:**
Google quality raters now formally assess whether content appears AI-generated. AI-generated content is acceptable when it demonstrates genuine E-E-A-T, provides unique value, and has human oversight and editing. Low-quality AI content markers:
- Generic phrasing with no specificity
- No original insight — says nothing that isn't already everywhere
- Repetitive structure across pages
- No author attribution
- Factual inaccuracies

---

## E-E-A-T Audit Output Format

**E-E-A-T Assessment — [Page URL]**

| Dimension | Score | Key Signals Present | Key Signals Missing |
|-----------|-------|--------------------|--------------------|
| Experience | H/M/L | [what's there] | [what's missing] |
| Expertise | H/M/L | | |
| Authoritativeness | H/M/L | | |
| Trustworthiness | H/M/L | | |

**Content Quality Issues:**
[List specific checklist failures with page-level fixes]

**Top 3 Changes to Make:**
1. [Specific, actionable fix]
2. [Specific, actionable fix]
3. [Specific, actionable fix]

---

## Judgment Guidelines

- **Fix before you build.** Optimizing an existing underperforming money page is almost always faster than creating a new one.
- **Format match is non-negotiable.** Study the SERP format before briefing content. Don't fight what Google is already rewarding.
- **Competitor content is a floor, not a ceiling.** Match what works, then add a genuine point of view. Generic coverage of a topic will never outrank an established competitor.
- **Informational content is a trap without intent alignment.** High-volume informational keywords that don't connect to a buyer decision inflate traffic without driving revenue. Always ask: would this reader buy this product?
- **Content strategy and link strategy must be developed together.** Every money page needs a link building plan. Flag this when recommending Phase 1 content.
- **E-E-A-T is a quality bar, not a checklist to game.** The goal is content that genuinely reflects first-hand knowledge and serves the reader. Ticking boxes without substance doesn't fool quality raters or AI systems.
- **TPV content follows the same rules.** If recommending content for a TPV domain, apply the same framework — money pages first, topical authority second, CTR2 optimization baked in from the start.

---

## Example Trigger Phrases

- "What content should Hey Sunday be creating?"
- "Build a content plan for Hello Pest"
- "What pages does PrimePutt need?"
- "What's our content strategy for [brand]?"
- "What content gaps do we have vs. competitors?"
- "We need more organic traffic for Learner — what do we write?"
- "Is this page good enough to rank?"
- "Audit the E-E-A-T on this Hey Sunday article"
- "Why isn't this page ranking — is it a content quality issue?"
- "Does this content meet our quality bar?"
