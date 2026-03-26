---
name: portco-knowledge-setup
description: Builds a complete PortCo knowledge file for a Mechanism portfolio company. This file is required before running any other skill — it is the source of truth Claude uses to understand who the brand is, what it sells, where it stands competitively, and what the SEO mandate is. Use this skill when onboarding a new PortCo, when a knowledge file doesn't exist yet, or when an existing knowledge file needs a full refresh. Trigger when someone says "set up knowledge file for [brand]", "onboard [brand]", "create context file for [brand]", or "we need to get [brand] set up in Claude".
compatibility: "Requires Ahrefs MCP for domain metrics, referring domains, organic keywords, and traffic data. Requires web_search and browser tools for product research, pricing, and competitor identification. PortCo contact or OE input required for analytics setup, reporting cadence, and open issues."
---

# PortCo Knowledge File Setup

This skill builds the knowledge file that powers every other skill in the Mechanism SEO library. Without it, Claude is working blind — it doesn't know what the brand sells, what keywords matter, who the competitors are, or what the current SEO situation looks like.

A complete knowledge file takes 30–60 minutes to build properly. Most of that time is pulling Ahrefs data and researching the product line. The output is a markdown file saved to `~/.claude/skills/contexts/[portco-name]-knowledge.md`.

**Before starting, confirm you have:**
- Brand name and root domain
- Access to Ahrefs (MCP or UI)
- Access to the brand's website
- OE or PortCo contact available for analytics and reporting questions

---

## Step 1: Company Overview

Navigate to the brand's website and pull the following. Use browser tools — most DTC brand sites are JS-rendered.

**Collect:**
- Official brand name and domain
- Product category (what do they actually sell?)
- Target customer (who is the buyer? what's their mindset?)
- What's distinctive about the product (clean label? pricing? formulation?)
- Brand stage — Early (0–6mo), Growth (6–18mo), or Mature (18mo+)
- Approximate customer count if visible (e.g., "300,000+ customers")
- Founding story or key figures (founder name, any credentialed experts like dietitians or doctors — these are link magnets)
- Any notable press or social proof visible on site (Forbes, etc.)

---

## Step 2: Product Line

Navigate to the brand's product pages and collect the full product catalog.

**For each product:**
- Product name and URL slug (e.g., `/products/supergreens`)
- One-line description of what it is
- Price — subscription price and retail price if both exist
- Key ingredients or differentiators
- Any availability flags (out of stock, paused, new launch)

**Note the hero product** — the one with the highest traffic, most links, or most prominent placement. This is the primary SEO focus.

---

## Step 3: Domain Profile

Pull from Ahrefs via MCP. If MCP returns errors, pull manually from Ahrefs Site Explorer and paste the numbers.

**Pull for the root domain:**
- Domain Rating (DR)
- Ahrefs Rank
- Referring Domains (live and all-time)
- Backlinks (live and all-time)
- Organic Keywords (total and in top 3 positions)
- Estimated Organic Traffic (monthly)
- Organic Traffic Value (monthly)
- Paid Keywords and Traffic (if any)

**Traffic by country** — note top 3 countries and % split.

**Branded vs. non-branded split:**
Estimate from Ahrefs keyword data. A brand-heavy split (>70% branded) means non-branded growth is the primary opportunity.

**AI visibility** — if Ahrefs Brand Radar is available, note citation counts across ChatGPT, Perplexity, Gemini, Google AI Overview, Copilot.

---

## Step 4: Money Keywords

Pull the top organic keywords from Ahrefs Site Explorer → Organic Keywords. Filter to keywords with meaningful volume (500+/mo) and positions 1–20.

**Organize into three groups:**

**Primary money keywords** — head terms for the hero product category. These are the keywords the brand most wants to rank for.

**Secondary money keywords** — head terms for secondary product lines or adjacent categories.

**Top branded keywords** — highest-volume branded terms. Document only — don't optimize for these.

For each keyword note: estimated monthly volume, current position, and any notable trend (gaining, losing, stable).

---

## Step 5: Top Organic Pages

Pull from Ahrefs Site Explorer → Top Pages. List the top 10 pages by organic traffic.

**For each page:**
- URL
- Estimated monthly traffic
- Top ranking keyword and position
- Any flags (out of stock, high-value page, etc.)

**Note the content model** — is traffic concentrated on PDPs, blog posts, comparison pages? This shapes the content strategy.

---

## Step 6: Benchmark Competitors

Identify the 4–6 most relevant competitors in the same product category and SERPs.

**Two ways to find them:**
1. Ahrefs Site Explorer → Organic Competitors
2. Search the hero product category in Google and note who's ranking

**For each competitor:** domain, approximate DR, which product category they compete in, and why they're relevant.

If the PortCo has multiple product lines in different categories, note which competitors belong to which category.

---

## Step 7: Content Strategy Summary

Navigate the brand's blog and site structure. Note:
- Site structure — what URL paths exist?
- Content model — what types of content are they publishing?
- What's working — blog posts driving significant non-branded traffic?
- Gaps — obvious keyword clusters with no content?
- TPV status — is there an active TPV domain? If so, what is it and what keyword is it targeting?

---

## Step 8: Analytics & Measurement

Ask the OE or PortCo contact:
- What analytics platform is the source of truth? (GA4 / Shopify / Triple Whale)
- Primary conversion event? (purchase, subscription sign-up)
- CVR, AOV, LTV if known?
- Any known data issues or tracking gaps?

Mark unknown fields as `[Unknown — needs input]` and flag for follow-up.

---

## Step 9: Open Issues & Engagement History

Document anything that affects how SEO work should be approached:
- Active incidents (product pauses, PR issues, algorithm hits)
- Known ranking losses or traffic declines
- SEO work already completed
- Team-flagged priorities

---

## Output

Save the completed knowledge file as:

**Filename:** `[portco]-knowledge.md`
**Example:** `liveitup-knowledge.md`
**Save location:** `~/.claude/skills/contexts/`

Use the following template exactly. Fill in every section. Use `[Unknown — needs input]` for missing data — never leave fields blank.

---

# [Brand Name] — PortCo Knowledge File

> This file is the source of truth for all Organic Team work on [Brand Name]. It must be read before running any skill for this PortCo. It is maintained by the Organic Team and updated as the engagement evolves.
>
> Last updated: [Month Year]

---

## Company Overview

**Brand name:** [Brand Name]
**Domain:** [domain.com]
**Product category:** [What do they sell]
**Target customer:** [Who buys this and why]
**What's distinctive about the product:** [Key differentiators]
**Stage:** [Early / Growth / Mature]
**Engagement status:** Active
**Founding story:** [Founder name and brief background if known]
**Press:** [Notable press mentions]

---

## Product Line

**Hero product:**
- **[Product Name]** (`/products/[slug]`) — [Description]. [Price sub] (sub) / [Price retail] retail.

**Secondary products:**
- **[Product Name]** (`/products/[slug]`) — [Description]. [Price].

---

## Analytics & Measurement

**Source of truth:** [GA4 / Shopify / Triple Whale]
**Primary conversion event:** [New purchases / subscription sign-ups]
**CVR:** [Unknown — needs input]
**AOV:** [Unknown — needs input]
**LTV:** [Unknown — needs input]
**Known data issues:** [None flagged / describe if known]

---

## Current Domain Profile

*Last updated: [Month Year] from Ahrefs Site Explorer*

| Metric | Value | Last Updated |
|--------|-------|-------------|
| Domain Rating (DR) | | |
| Referring Domains (live) | | |
| Organic Keywords | | |
| Estimated Organic Traffic | | |
| Organic Traffic Value | | |

**Traffic by country:** [Top 3 countries and % split]

**Branded vs. non-branded split:**
- Branded: [X keywords → Y traffic]
- Non-branded: [X keywords → Y traffic]

**AI visibility:**
- Google AI Overview: [X citations]
- ChatGPT: [X citations]
- Perplexity: [X citations]
- Gemini: [X citations]

---

## Money Keywords

**Primary ([hero category]):**

| Keyword | Monthly Volume | Current Position | Notes |
|---------|---------------|-----------------|-------|
| | | | |

**Secondary ([secondary category]):**

| Keyword | Monthly Volume | Current Position | Notes |
|---------|---------------|-----------------|-------|
| | | | |

**Top branded keywords:**

| Keyword | Monthly Volume | Current Position |
|---------|---------------|-----------------|
| | | |

---

## Top Organic Pages

*By traffic, [Month Year]*

| URL | Est. Traffic | Top Keyword | Notes |
|-----|-------------|-------------|-------|
| | | | |

---

## Benchmark Competitors

| Domain | DR | Category | Why Selected |
|--------|-----|----------|-------------|
| | | | |

---

## Content Strategy

**Site structure:** [List URL paths]
**Content model:** [What types of content exist]
**What's working:** [High-traffic content patterns]
**Gaps:** [Missing keyword clusters or content types]
**TPV status:** [Active / Not yet active / Opportunity identified]

---

## Link Building

**Current tactic mix:** [Unknown — needs input]
**Active campaigns:** [None / describe if active]
**Key placements secured:** [Notable links earned]

---

## Reporting

**Report recipient:** [Unknown — needs input]
**Reporting cadence:** [Unknown — needs input]
**Key stakeholder context:** [Unknown — needs input]

---

## Open Issues & Notes

- [Date] — [Issue description and SEO implications]

---

## Engagement History

- [Date] — [What was done]
