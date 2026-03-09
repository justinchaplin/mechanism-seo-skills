---
name: aeo-geo-audit
description: Audits how a Mechanism portfolio company appears in AI-generated responses — including ChatGPT, Perplexity, Google AI Overviews, and other LLM-powered surfaces — identifying whether the brand is mentioned, what's being said, what sources are cited, and what competitors are appearing instead. Includes technical accessibility checks (AI crawler access, llms.txt), passage-level citability scoring, platform-specific optimization, and Brand Radar share of voice analysis. Use this skill whenever someone asks about AI search presence, whether a brand shows up in ChatGPT or Perplexity, what AI tools say about a brand or category, how the brand is performing in AEO (Answer Engine Optimization) or GEO (Generative Engine Optimization), or whether AI overviews are affecting organic traffic. Also trigger when someone says "what does ChatGPT say about [brand]", "are we showing up in AI search", "how do we get into AI overviews", "why are our impressions up but clicks down", or "optimize our content for AI search".
compatibility: "Requires web_search (for manual AI Overview checks and Perplexity/ChatGPT spot-checks) and Ahrefs Brand Radar MCP tools (brand-radar-mentions-overview, brand-radar-sov-overview, brand-radar-cited-domains, brand-radar-cited-pages, brand-radar-ai-responses) for structured AI mention data. Requires PortCo knowledge file for brand name, money keywords, and competitor list."
---

# AEO / GEO Audit

This skill audits how a Mechanism portfolio company appears in AI-generated search responses and identifies what to do to improve that presence. It covers technical accessibility (can AI crawlers reach the site?), brand mention share of voice (is the brand appearing vs. competitors?), passage-level citability (is the content structured for AI citation?), and platform-specific optimization.

---

## Why AI Search Presence Matters

AI-referred sessions grew 527% between January and May 2025. Google AI Overviews now reach 1.5 billion users monthly across 200+ countries and appear on 50%+ of all queries. ChatGPT has 900 million weekly active users. Perplexity handles 500 million+ queries per month.

**The critical insight:** Brand mentions correlate 3× more strongly with AI visibility than backlinks (Ahrefs, December 2025 study of 75,000 brands). Correlation by signal type:

| Signal | Correlation with AI Citations |
|--------|------------------------------|
| YouTube mentions | ~0.737 (strongest) |
| Reddit mentions | High |
| Wikipedia presence | High |
| LinkedIn presence | Moderate |
| Domain Rating (backlinks) | ~0.266 (weak) |

**What this means for Mechanism PortCos:** Getting into the editorial layer — roundups, reviews, "best of" content on trusted sites — is the primary lever for AI search presence. This is the same work as link building and outreach. TPV domains that rank in traditional search are more likely to be cited in AI search as well. Brands with little editorial coverage will not appear in AI answers even if their own site is technically strong.

**Platform-specific citation reality:**

| Platform | Key Citation Sources | Optimization Priority |
|----------|---------------------|----------------------|
| Google AI Overviews | 92% from top-10 ranking pages; 47% from below P5 | Traditional SEO + passage optimization |
| ChatGPT | Wikipedia (47.9%), Reddit (11.3%) | Entity presence, authoritative sources |
| Perplexity | Reddit (46.7%), Wikipedia | Community presence, editorial roundups |
| Bing Copilot | Bing index, authoritative sites | Bing SEO alignment |

Only 11% of domains are cited by both ChatGPT and Google AI Overviews for the same query — platform behaviors differ meaningfully.

---

## Inputs Required

- **Brand name** — exact public brand name
- **Domain** — root domain
- **PortCo knowledge file** — for money keywords, competitor list, benchmark context
- **GSC data** (optional) — to check for impressions-up/clicks-flat AI Overview signal
- **Focus** (optional) — brand mentions, category presence, technical audit, or all three

---

## Pre-Check: Technical Accessibility

Before anything else — if AI crawlers can't access the site, no other GEO work matters.

**Check robots.txt at [domain]/robots.txt for these crawlers:**

| Crawler | Owner | Required Action |
|---------|-------|----------------|
| GPTBot | OpenAI (ChatGPT search) | Must allow |
| OAI-SearchBot | OpenAI (search features) | Must allow |
| PerplexityBot | Perplexity | Must allow |
| ClaudeBot | Anthropic | Allow |
| ChatGPT-User | OpenAI (browsing) | Allow |
| Bytespider | ByteDance/TikTok AI | Allow if desired |
| CCBot | Common Crawl (training) | Can block |
| anthropic-ai | Anthropic (training) | Can block |

Flag immediately if GPTBot, OAI-SearchBot, or PerplexityBot are blocked.

**Check for llms.txt at [domain]/llms.txt:**
The llms.txt standard provides AI crawlers with structured content guidance. If missing, flag as a Quick Win to implement. Format:
```
# [Brand Name]
> [1-2 sentence brand description]

## Key Pages
- [Page title](url): [Brief description]

## About
- [Key brand fact]
```

**Check server-side rendering:** AI crawlers do NOT execute JavaScript. If the site is a client-side SPA with content rendered via JavaScript, AI crawlers may see blank pages. Flag for engineering review if applicable.

---

## Step 1: Manual AI Spot-Checks

Run the following queries across AI surfaces and record what appears:

**Queries to run:**
1. "What are the best [category]?" — category intent
2. "Is [brand name] good / worth it?" — brand evaluation intent
3. "What's the difference between [brand] and [top competitor]?" — comparison intent
4. "[Brand name]" — direct brand query

**AI surfaces to check:**
- **Google AI Overview** — note if AIO appears, what it says, which sources are cited
- **Perplexity** — perplexity.ai, same queries
- **ChatGPT** — chatgpt.com with web browsing enabled, same queries

For each, record:
- Brand mentioned? (Yes / No / Indirect)
- What's said? (Positive / Neutral / Negative / Factual error)
- Sources cited
- Competitors appearing instead

**GSC signal check:** Impressions rising + clicks flat or declining for a keyword = AI Overview absorbing clicks. Flag which keywords show this pattern. This is a structural shift, not a fixable bug.

---

## Step 2: Pull Ahrefs Brand Radar Data

**Pull brand mentions:**
```
Ahrefs: brand-radar-mentions-overview
brand: [brand name]
competitors: [competitor 1], [competitor 2], [competitor 3]
data_source: chatgpt
select: brand, mentions
```
Repeat for data_source: perplexity

**Pull share of voice:**
```
Ahrefs: brand-radar-sov-overview
brand: [brand name]
competitors: [competitor 1], [competitor 2], [competitor 3]
data_source: chatgpt
select: brand, sov
```

**Pull cited domains:**
```
Ahrefs: brand-radar-cited-domains
brand: [brand name]
data_source: chatgpt
select: domain, brand_mentions, volume
```

**Pull cited pages:**
```
Ahrefs: brand-radar-cited-pages
brand: [brand name]
data_source: chatgpt
select: url, brand_mentions, volume
```

**Pull sample AI responses:**
```
Ahrefs: brand-radar-ai-responses
brand: [brand name]
data_source: chatgpt
select: prompt, response, sources
```

Run all for both chatgpt and perplexity. Brand Radar data is sampled — use for directional signal and competitive benchmarking.

---

## Step 3: Citability Audit

AI models prefer content structured for extraction. Audit key pages against these dimensions:

**Passage structure (highest impact):**
- Optimal passage length: **134–167 words**
- Direct answer in first **40–60 words** of each section
- Self-contained answer blocks — extractable without surrounding context
- Claims attributed to specific sources
- Definitions following "X is..." or "X refers to..." patterns
- Unique data points not found elsewhere

**Structural readability:**
- Clean H1 → H2 → H3 hierarchy
- Question-based headings (matches query patterns)
- Short paragraphs (2–4 sentences)
- Tables for comparative data
- Lists for multi-item content
- FAQ sections with explicit Q&A format

**Authority signals:**
- Author byline with credentials
- Publication and last-updated date
- Citations to primary sources
- Entity presence: Wikipedia, Wikidata, LinkedIn, YouTube

**Multi-modal content:**
Content with multi-modal elements sees 156% higher AI selection rates:
- Relevant images with descriptive alt text
- Comparison tables with real data
- Embedded video content

Audit the brand's money pages and key landing pages. Flag specific pages with low citability and specific fixes needed.

---

## Step 4: Interpret and Diagnose

**Share of voice benchmarks:**
- Fragmented category (5+ competitors): 20%+ is strong
- Concentrated category (2–3 major players): benchmark against direct competitors
- New brands (<12 months old): low share is expected — set realistic expectations

**Cited domains analysis:**
- Domains cited in AI responses but not linking to the brand = highest-priority outreach targets
- Domains linking to the brand but not cited = improve prominence and quality of brand mention on those pages

**Diagnosis by scenario:**

**No presence**
Cause: Insufficient editorial coverage. Brand not in the roundups AI pulls from.
Fix: Outreach to the specific domains AI is already citing in the category. Use the Outreach Direction skill.

**Low or unfavorable position**
Cause: Competitors have stronger editorial coverage on AI-trusted sources.
Fix: Increase quality and quantity of editorial mentions, prioritizing cited domains from Brand Radar.

**Factual errors**
Cause: AI training data is inaccurate, or brand's site doesn't state facts clearly.
Fix: State key facts explicitly on About/FAQ. Request corrections from editorial sites. Flag to PortCo if significant.

**AI Overviews suppressing clicks**
Signal: GSC impressions rising + clicks flat/falling.
Fix: Structural shift — can't be reversed. Increase brand presence within AI Overviews via editorial coverage. Redirect content strategy toward queries where AI Overviews are less dominant.

**Competitors appearing, brand not**
Cause: Competitors have better editorial coverage on AI-trusted sources.
Fix: Identify which sources cite competitors → run link gap → prioritize outreach to those sources.

---

## Output Format

---

**AEO / GEO Audit — [Brand Name]**
*Audited: [date]*

**AI Search Presence Summary:**
[2–3 sentences. Is the brand showing up? Where? What's the headline finding?]

---

**Pre-Check: Technical Accessibility**

| Check | Status | Action Needed? |
|-------|--------|---------------|
| GPTBot | Allowed / Blocked | Yes / No |
| OAI-SearchBot | Allowed / Blocked | Yes / No |
| PerplexityBot | Allowed / Blocked | Yes / No |
| llms.txt | Present / Missing | Yes / No |
| Server-side rendering | Confirmed / At risk | Yes / No |

---

**Manual Spot-Check Results**

| Query | Surface | Brand Mentioned? | What's Said | Competitors Instead | Sources Cited |
|-------|---------|-----------------|------------|-------------------|---------------|
| "best [category]" | Google AIO | Yes / No | [summary] | [brands] | [domains] |
| "best [category]" | Perplexity | Yes / No | [summary] | [brands] | [domains] |
| "best [category]" | ChatGPT | Yes / No | [summary] | [brands] | [domains] |
| "[brand] reviews" | Perplexity | Yes / No | [summary] | — | [domains] |

**GSC Signal:** [Impressions-up/clicks-flat keywords, if any]

---

**Brand Radar — Share of Voice**

| Brand | ChatGPT Mentions | ChatGPT SOV | Perplexity Mentions | Perplexity SOV |
|-------|-----------------|-------------|---------------------|----------------|
| [PortCo] | [X] | [X%] | [X] | [X%] |
| [Competitor 1] | [X] | [X%] | [X] | [X%] |
| [Competitor 2] | [X] | [X%] | [X] | [X%] |

---

**Top Cited Domains**

| Domain | Citation Count | Also Links to Brand? | Outreach Priority |
|--------|---------------|---------------------|------------------|
| [domain] | [X] | Yes / No | High if No |

---

**Citability Issues — Key Pages**
[Pages with low citability scores and specific fixes]

---

**Diagnosis**
[Which scenario(s) apply with evidence]

---

**Recommended Actions**

*Quick Wins:*
1. Allow GPTBot / PerplexityBot in robots.txt (if blocked)
2. Add llms.txt to domain root
3. Rewrite key page openings with direct answer in first 40–60 words
4. Add question-based H2/H3 headings to money pages
5. Add publication and last-updated dates to key pages

*Medium Effort:*
1. Outreach to top cited domains not linking to brand (use Outreach Direction skill)
2. Add author bylines with credentials to key pages
3. Build FAQ sections on money pages with explicit Q&A format
4. Verify server-side rendering for key content

*Higher Effort / Longer Horizon:*
1. Build authentic Reddit presence in category discussions
2. Build Wikipedia entity presence for the brand
3. Create original research or data — unique citability signal
4. YouTube content if brand has strong product demonstration angle

---

## Judgment Guidelines

- **The primary lever is editorial coverage — not technical fixes.** robots.txt and llms.txt are hygiene items. Getting cited requires being in the sources AI trusts. That's outreach work.
- **Don't overreact to low AI share of voice for new brands.** AI training data lags. A brand 6 months old with limited editorial coverage will have low presence by default.
- **Platform behaviors differ.** Google AI Overviews = traditional SEO path. Perplexity and ChatGPT = Reddit and Wikipedia matter disproportionately. Don't treat all AI surfaces identically.
- **AI Overviews absorbing clicks is structural.** Report it honestly. Adaptation, not reversal, is the only path.
- **The cited domains list is the most actionable output.** Every domain AI is already citing in the category is a warm outreach target with proven category relevance.
- **For most Mechanism PortCos, Perplexity and Google AI Overviews are higher priority than ChatGPT** for commercial product queries. Weight outreach and optimization accordingly.
- **Brand Radar data is sampled.** Use it for directional signal and competitive benchmarking, not as a definitive mention count.

---

## Example Trigger Phrases

- "What does ChatGPT say about Hey Sunday?"
- "Are we showing up in AI search for laundry detergent sheets?"
- "Run an AEO/GEO audit for PrimePutt"
- "Why are our impressions up but clicks down for [keyword]?"
- "How do we get Hey Sunday into AI Overviews?"
- "Optimize our content for AI search"
- "Check if AI crawlers can access [domain]"
- "Do we show up in Perplexity for [category] searches?"
- "What are competitors doing in AI search that we're not?"
