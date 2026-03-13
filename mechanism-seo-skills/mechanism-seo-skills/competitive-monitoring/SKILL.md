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
