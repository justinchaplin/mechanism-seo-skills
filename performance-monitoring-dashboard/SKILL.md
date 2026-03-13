---
name: performance-monitoring-dashboard
description: Produces a structured organic performance snapshot for a Mechanism portfolio company by pulling together data from GA4, GSC, Shopify, and Ahrefs. Use this skill whenever someone asks for a monthly performance review, organic performance summary, how organic is performing for the business, or wants a cross-platform view of organic results. Also trigger when someone says things like "how is [brand] performing this month", "give me an organic performance update for [brand]", "run the monthly review for [brand]", or "pull together organic performance for [brand]". This skill goes beyond GSC rankings — it connects traffic to conversions and business impact. Always use this skill rather than giving manual reporting instructions.
compatibility: "Requires at least one of: GA4, Shopify, or GSC access for the PortCo. Ahrefs MCP recommended for ranking and backlink data. Triple Whale can substitute for GA4/Shopify where used."
---

# Performance Monitoring Dashboard Review

This skill produces a monthly organic performance snapshot for a Mechanism PortCo. It connects ranking data (GSC, Ahrefs) to business outcomes (GA4, Shopify) to answer the question PortCo leadership actually cares about: **is organic growing the business?**

This is the monthly review. For weekly ranking checks, use the GSC Performance Monitoring skill instead.

---

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the PortCo being reviewed
- **Review period** — typically current month vs. prior month, or current month vs. same month last year
- **Analytics platform** — GA4, Triple Whale, Shopify, or a combination. Note which is the source of truth for this PortCo.
- **GSC access** — for ranking and click data
- **Ahrefs access** — for DR, referring domains, and ranking movement
- **Money keywords** — the primary keywords this PortCo targets

If the PortCo uses Triple Whale, note that organic channel data may have discrepancies vs. GA4 — flag this in the output if relevant. (Hey Sunday has a known Triple Whale / Organic & Social channel discrepancy — always cross-reference with GA4 for that PortCo.)

---

## How to Read Organic Performance

Before pulling data, understand what we're measuring and why:

**The organic funnel has three layers:**

1. **Visibility** — Are we showing up? (GSC impressions, Ahrefs rankings)
2. **Traffic** — Are people clicking? (GSC clicks, GA4 organic sessions)
3. **Business impact** — Is it converting? (GA4/Shopify organic conversions, revenue)

A healthy organic program shows growth across all three layers. Gaps between layers are signals:
- High impressions, low clicks → CTR problem (title tags, SERP competition)
- High traffic, low conversions → landing page or intent mismatch problem
- Low impressions across the board → authority or indexation problem

**The halo effect complicates attribution — always acknowledge it.** Organic work drives conversions in paid, direct, and referral channels that will never show in organic conversion reports. When presenting results to PortCo leadership, always note that organic attribution understates total organic impact.

---

## Workflow

### Step 1: Visibility Layer — Ahrefs

Pull the current domain state from Ahrefs:

```
Ahrefs: site-explorer-domain-rating
target: [brand domain]
```

```
Ahrefs: site-explorer-backlinks-stats
target: [brand domain]
```

```
Ahrefs: site-explorer-metrics
target: [brand domain]
```

Record:
- Current DR vs. prior month (is authority building?)
- Referring domain count vs. prior month (are links accumulating?)
- Estimated organic traffic from Ahrefs (directional benchmark)
- Top 5 money keyword positions

---

### Step 2: Traffic Layer — GSC

Pull GSC data for the review period (current month vs. prior month or YoY):

Filter non-branded and branded separately.

Record:
- Total non-branded clicks and impressions vs. prior period
- Total branded clicks and impressions vs. prior period
- Average position on money keywords vs. prior period
- Any keywords entering or exiting top 10
- Positions 11–20 with high impressions (opportunity list)

For the halo effect flag: if branded clicks are growing independently of paid brand campaigns, note this as organic-driven brand awareness growth.

---

### Step 3: Business Impact Layer — GA4 / Shopify / Triple Whale

Pull organic channel data from the PortCo's analytics source of truth:

**From GA4:**
- Organic sessions vs. prior period
- Organic conversions (purchases, sign-ups, or primary goal) vs. prior period
- Organic revenue vs. prior period
- Organic conversion rate vs. prior period
- Top organic landing pages by sessions and conversions

**From Shopify (if GA4 not primary):**
- Sessions from organic search vs. prior period
- Orders attributed to organic search vs. prior period
- Revenue attributed to organic search vs. prior period

**From Triple Whale (if primary):**
- Organic & Social channel performance vs. prior period
- Note: Triple Whale bundles Organic and Social — cross-reference with GA4 for organic-specific data where possible

Flag any significant discrepancies between platforms — these are worth surfacing to the PortCo.

---

### Step 4: Link Building Activity Summary

Summarize link building activity for the period:
- How many new referring domains were acquired?
- Any notable placements (high-DR, high-relevance editorial mentions)?
- Outreach campaigns active — volume and response rate if available

This connects the invisible work to the visibility layer results.

---

### Step 5: Synthesize and Flag

With all data pulled, synthesize into three buckets:

**What's working:** What grew, what's trending in the right direction, what wins can be communicated to leadership.

**What needs attention:** Rankings dropping, traffic declining, conversion rate shifts, link building gaps.

**What to do next month:** 3 specific actions based on what the data shows.

---

## Output Format

---

**Organic Performance Review — [Brand Name]**
*Period: [current period] vs. [comparison period]*
*Data sources: [list which platforms were used]*

**Executive Summary:**
[3–4 sentences. Is organic growing the business? What's the headline? Written for a CEO, not an SEO.]*

**Visibility:**
| Metric | This Period | Prior Period | Change |
|--------|------------|--------------|--------|
| Domain Rating | ... | ... | ↑/↓ |
| Referring Domains | ... | ... | ↑/↓ |
| GSC Impressions (non-branded) | ... | ... | ↑/↓ % |
| GSC Impressions (branded) | ... | ... | ↑/↓ % |

**Traffic:**
| Metric | This Period | Prior Period | Change |
|--------|------------|--------------|--------|
| GSC Clicks (non-branded) | ... | ... | ↑/↓ % |
| GSC Clicks (branded) | ... | ... | ↑/↓ % |
| Organic Sessions (GA4/Shopify) | ... | ... | ↑/↓ % |
| Avg Position — Money Keywords | ... | ... | ↑/↓ |

**Business Impact:**
| Metric | This Period | Prior Period | Change |
|--------|------------|--------------|--------|
| Organic Conversions | ... | ... | ↑/↓ % |
| Organic Revenue | ... | ... | ↑/↓ % |
| Organic CVR | ... | ... | ↑/↓ |

**Money Keyword Rankings:**
| Keyword | Position | Change | Notes |
|---------|----------|--------|-------|
| ... | ... | ↑/↓ | ... |

**Link Building This Period:**
- New referring domains: [#]
- Notable placements: [list any high-value wins]
- Active campaigns: [summary]

**Halo Effect Note:**
[1–2 sentences acknowledging organic's contribution to non-organic conversions — paid, direct, referral. Include if branded search is growing.]

**What's Working:**
- [bullet]
- [bullet]

**What Needs Attention:**
- [bullet]
- [bullet]

**Actions for Next Month:**
1. [specific action]
2. [specific action]
3. [specific action]

---

## Judgment Guidelines

- **Lead with business impact, not rankings.** The executive summary should answer "is organic growing the business" — not "our average position improved by 0.3." Rankings are context, not the headline.
- **Always acknowledge the halo effect.** Every monthly review should include a sentence about organic's contribution to non-organic conversions. This protects the engagement when attribution looks thin.
- **Branded search growth = halo effect evidence.** If branded clicks in GSC are growing and there's no paid brand campaign driving it, organic and link building work is building awareness. Name this explicitly.
- **Platform discrepancies are worth flagging, not hiding.** If GA4 and Shopify show different organic numbers, note it and use the more conservative number unless there's a clear reason not to.
- **Three actions max.** The output should always end with 3 specific, actionable items — not a wishlist. What will actually move the needle next month?
- **Context matters more than absolute numbers.** A 10% traffic drop after a Google algorithm update is different from a 10% drop with no external cause. Always include context.

---

## Example Trigger Phrases

- "Give me an organic performance update for Hey Sunday for February"
- "How is PrimePutt performing organically this month?"
- "Run the monthly review for Learner"
- "Pull together organic performance for Hello Pest — first 30 days"
- "How is organic performing vs. last year for [brand]?"
- "What's the organic story for [brand] this quarter?"
