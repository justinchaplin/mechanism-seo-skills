# Mechanism SEO Skills Library

This is the Mechanism Organic Team's Claude Code skill library. When someone asks you to run an SEO task, use the skills listed below. Reference the skill file directly using the @ syntax.

## Available Skills

### Content
- `non-branded-keyword-research` — Build a prioritized keyword list for a PortCo from scratch
- `serp-analysis` — Analyze the live SERP for a keyword
- `seo-entry-plan` — Turn keyword research into a concrete page-level execution plan
- `content-strategy` — Full content strategy with topic clusters and calendar
- `page-optimizer` — Audit an existing page against a target keyword and the live SERP

### Link Building
- `seo-competitor-link-gap` — Pull Ahrefs Link Intersect data into a prioritized outreach list
- `link-building-strategy` — Determine the right link building tactic mix for a PortCo
- `outreach-direction` — Build outreach messaging and angle recommendations

### Technical SEO
- `site-health-audit` — Full technical audit covering crawlability, indexability, on-page signals
- `branded-serp-audit` — Analyze how a PortCo appears on its own branded SERP
- `aeo-geo-audit` — Assess how a PortCo appears in AI-generated search answers

### Monitoring & Analytics
- `gsc-performance-monitoring` — Weekly/monthly GSC review
- `performance-monitoring-dashboard` — Cross-platform performance snapshot
- `competitive-monitoring` — Track competitor ranking movements and new content
- `monthly-reporting` — CEO-ready monthly SEO update
- `review-reputation-monitoring` — Audit brand reputation across review platforms, Reddit, and AI

### TPV
- `tpv-content-strategy` — Content and SEO strategy for a TPV property
- `tpv-comparison-pages` — Build comparison and roundup content for TPV properties

### Setup
- `portco-knowledge-setup` — Build a PortCo knowledge file before running any other skill

## How to Run a Skill

Reference the skill file and describe the task in plain language:

```
@~/.claude/skills/mechanism-seo-skills/mechanism-seo-skills/seo-entry-plan/SKILL.md

Run the SEO entry plan for Live It Up — targeting "electrolyte powder"
```

```
@~/.claude/skills/mechanism-seo-skills/mechanism-seo-skills/competitive-monitoring/SKILL.md

Run competitive monitoring for Live It Up
```

## PortCo Knowledge Files

Always load the PortCo knowledge file before running any skill. Knowledge files live at:
`~/.claude/skills/contexts/[portco]-knowledge.md`

Reference it alongside the skill:
```
@~/.claude/skills/mechanism-seo-skills/mechanism-seo-skills/monthly-reporting/SKILL.md
@~/.claude/skills/contexts/liveitup-knowledge.md

Run monthly SEO reporting for Live It Up — March 2026
```

If no knowledge file exists yet, run the `portco-knowledge-setup` skill first.
