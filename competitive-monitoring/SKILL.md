---
name: competitive-monitoring
description: Tracks competitor organic performance over time for a Mechanism portfolio company — identifying when competitors are gaining ground, what content or links are driving their growth, and what the team should do about it. Use this skill whenever someone asks about competitor tracking, competitor performance, what competitors are doing in search, whether a competitor is growing organically, or how a PortCo stacks up against competitors. Also trigger when someone says things like "keep an eye on [competitor]", "what's [competitor] doing in search", "has [competitor] been building links", "did [competitor] publish anything new", or "are we losing ground to [competitor]". Always use this skill rather than giving ad hoc competitor assessments.
compatibility: "Requires Ahrefs MCP (for domain metrics, organic keyword tracking, and backlink data) and web_search (for new content discovery and SERP checks). Requires PortCo knowledge file for benchmark competitor list and money keywords."
---

# Competitive Monitoring

This skill tracks what benchmark competitors are doing in organic search — their traffic trends, new content, link building activity, and ranking movements — and translates that into specific actions for the Mechanism team.

Competitive monitoring is not research for its own sake. Every output should answer: **so what do we do about it?**

---

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the PortCo being monitored
- **PortCo knowledge file** — for benchmark competitor list and money keywords
- **Monitoring period** — monthly is standard; specify if different (e.g., "last 30 days", "Q1 vs Q4")
- **Focus area** (optional) — content, links, rankings, or all three

---

## What We're Watching For

Competitive monitoring has three layers. Each answers a different question.

**Layer 1 — Traffic & Rankings**
*Are competitors growing faster than us? Are they taking positions we care about?*

Check organic traffic trends, keyword count growth, and position changes on the PortCo's money keywords. If a competitor's traffic is accelerating, something is working for them — find out what.

**Layer 2 — Content Activity**
*Are competitors publishing new content that targets our keywords or audience?*

New content from a well-established competitor that targets money keywords is a threat — not necessarily an immediate one, but worth tracking. New content on informational terms we haven't covered yet is a gap signal.

**Layer 3 — Link Building Activity**
*Are competitors getting new links we should be getting too?*

New referring domains to a competitor's domain or specific pages is the clearest signal that someone is actively building links. If a site linked to a competitor and hasn't linked to us, that's a target.

---

## Workflow

### Step 1: Pull the Benchmark Competitor List

From the PortCo knowledge file, extract:
- Benchmark competitors (direct brands)
- Money keywords (to check ranking shifts on specific SERPs)

If the knowledge file is incomplete, use Ahrefs organic competitors as a fallback.

---

### Step 2: Track Traffic and Keyword Growth

For each benchmark competitor, pull:

```
Ahrefs: site-explorer-metrics-history
target: [competitor domain]
```

Compare current period vs. prior period. Flag:
- Any competitor showing >10% traffic growth month-over-month
- Any competitor whose keyword count is growing significantly
- Any competitor whose DR is increasing (active link building signal)

For money keywords specifically, check current positions for both the PortCo and each competitor:

```
Ahrefs: keywords-explorer-overview
keywords: [money keyword list]
```

Flag any money keyword where a competitor moved up 3+ positions or broke into the top 10.

---

### Step 3: Identify New Competitor Content

For each benchmark competitor, check for new content published in the monitoring period:

```
web_search: site:[competitor domain] [money keyword category]
```

Also check:
```
Ahrefs: site-explorer-top-pages
target: [competitor domain]
```

Look for pages that are new or have significantly increased traffic. Ask: does this page target a keyword we care about? Does it fill a gap we haven't covered?

---

### Step 4: Track New Referring Domains

For each benchmark competitor, pull new referring domains over the period:

```
Ahrefs: site-explorer-referring-domains
target: [competitor domain]
```

Filter for new domains only (first seen in the monitoring period). For each new referring domain:
- Check if it also links to our PortCo (if not, it's a target)
- Check if it ranks for our money keywords (SERPdom value)
- Note the content context (what article/page did the link go to?)

---

### Step 5: Synthesize and Prioritize Actions

Not everything a competitor does requires a response. Prioritize:

**Act immediately:**
- Competitor moved into top 5 for a money keyword you're targeting
- Competitor got a link from a site that ranks P1–5 for a money keyword (they're building SERPdom presence you don't have)
- Competitor published a definitive piece on a topic you haven't covered that's getting traction

**Watch and respond next cycle:**
- Competitor traffic growing consistently but slowly
- New competitor content targeting informational keywords (not money keywords)
- Competitor building DR/links broadly but not specifically on SERPdom targets

**Note but don't act:**
- Minor ranking fluctuations (±1–2 positions is noise)
- New competitor content on topics not relevant to your money keywords
- Competitor link activity on low-relevance sites

---

## Output Format

---

**Competitive Monitoring — [Brand Name]**
*Period: [Month/date range]*

**Competitive Landscape Summary:**
[2–3 sentences. Who's moving? What's the dominant story this period? Is the PortCo gaining or losing ground relative to competitors?]

**Competitor Snapshots:**

| Competitor | Organic Traffic | Traffic Change | DR | Keyword Count | Notable Activity |
|------------|----------------|----------------|----|---------------|-----------------|
| [name] | [X] | [+/-X%] | [X] | [X] | [1 sentence] |
| ... | | | | | |

**Money Keyword Rankings:**

| Keyword | PortCo Position | [Competitor 1] | [Competitor 2] | Change This Period |
|---------|----------------|----------------|----------------|-------------------|
| [keyword] | P[X] | P[X] | P[X] | [who moved where] |
| ... | | | | |

**Competitor Content Worth Noting:**
[List new competitor content that's relevant — what it covers, what keyword it targets, how much traction it's getting. Skip anything irrelevant.]

**New Referring Domains to Benchmark Competitors:**
[List sites that linked to a competitor but not to the PortCo — with DR, relevance, and whether it has SERPdom value. These are outreach targets.]

**Recommended Actions:**
1. [Specific, immediate action — who does it, what is it]
2. [Specific action]
3. [Watch item for next cycle, if relevant]

---

## Judgment Guidelines

- **Most competitor activity doesn't require an immediate response.** The goal is to catch the signals that matter — a competitor breaking into the top 5 on a money keyword, or landing a link from a site that ranks for our keywords. Not every ranking fluctuation is signal.
- **New referring domains to competitors are the highest-value output of this skill.** Every site that linked to a competitor and not to us is a warm outreach target — they've already demonstrated interest in the category.
- **Traffic growth without keyword growth usually means branded.** If a competitor's traffic is up but keyword count is flat, they may be running a brand campaign, not winning in organic. Don't overreact.
- **Content gaps should feed directly into the content strategy.** If a competitor published something you haven't, note it — but run it through the Content Strategy skill before deciding to respond.
- **Always frame actions for the team, not the PortCo.** The competitive monitoring report is internal — it's the basis for your work plan, not something you send to the PortCo.
- **Month-over-month is noisy. Track direction over 3+ months.** A single good or bad month isn't a trend. Flag the direction but be measured about urgency unless the signal is strong.

---

## Example Trigger Phrases

- "Run competitive monitoring for PrimePutt"
- "What are Hey Sunday's competitors doing in search?"
- "Has [competitor] been building links recently?"
- "Are we losing ground to [competitor] on [keyword]?"
- "What new content have our competitors published this month?"
- "Who's been linking to [competitor] that isn't linking to us?"
- "Track competitor activity for [brand] for [month]"
