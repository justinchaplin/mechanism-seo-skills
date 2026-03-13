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
