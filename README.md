# Mechanism Organic Skill Library

> A structured library of Claude-powered SEO workflows built for Mechanism's portfolio companies. Each skill encodes how the Organic Team approaches a specific task — not generic SEO advice, but Mechanism-specific thinking built from operating across multiple PortCos.

---

## What This Is

Mechanism's Organic Team runs SEO across a portfolio of startups. Every engagement involves the same core challenges: identifying the right keywords to go after, building authority from zero, monitoring performance, and knowing when to push and when to hold.

This library standardizes how we do that work. Each skill is a Claude workflow that any team member can run to produce a consistent, high-quality output — from keyword research to link building strategy to monthly reporting.

**15 skills. 4 pillars. Built to scale.**

---

## How to Use a Skill

1. Open the skill folder and copy the contents of `SKILL.md`
2. Open a new Claude conversation at [claude.ai](https://claude.ai)
3. Paste the skill content
4. Add the relevant PortCo knowledge file (see `/context/` — coming soon)
5. Run it

Skills are designed so that outputs are CEO-sendable without editing. If something needs to be changed, the skill needs to be updated — not the output.

---

## Skill Library

### Pillar 1 — Content

Skills that govern what content we create, why, and how to brief it.

| Skill | What It Does |
|-------|-------------|
| [`non-branded-keyword-research`](./non-branded-keyword-research/SKILL.md) | Identify and prioritize money keywords using Ahrefs + SERP analysis. Outputs a ranked target list with vehicle decisions. |
| [`seo-entry-plan`](./seo-entry-plan/SKILL.md) | Takes keyword research output → produces a concrete page-level execution brief. The "what to actually do" skill. |
| [`content-strategy`](./content-strategy/SKILL.md) | Determine what content to create and why. Covers money pages, supporting content, and E-E-A-T quality standards. |

### Pillar 2 — Link Building

Skills that govern how we build authority.

| Skill | What It Does |
|-------|-------------|
| [`seo-competitor-link-gap`](./seo-competitor-link-gap/SKILL.md) | Pull Ahrefs Link Intersect data and produce a prioritized outreach target list. |
| [`link-building-strategy`](./link-building-strategy/SKILL.md) | Determine the right link building tactic mix for a PortCo's stage and category. |
| [`outreach-direction`](./outreach-direction/SKILL.md) | Determine the right outreach angle and pitch positioning for a specific link opportunity. |

### Pillar 3 — Technical SEO

Skills that surface site health issues requiring action.

| Skill | What It Does |
|-------|-------------|
| [`site-health-audit`](./site-health-audit/SKILL.md) | Full technical audit covering crawlability, indexability, on-page, schema, images, and Core Web Vitals. Three modes: Full, Single Page, Targeted. |
| [`branded-serp-audit`](./branded-serp-audit/SKILL.md) | Analyze how a PortCo brand appears on its own branded SERP. Includes ORM triage. |
| [`aeo-geo-audit`](./aeo-geo-audit/SKILL.md) | Assess how a PortCo appears in AI-generated search answers (ChatGPT, Perplexity, Google AI Overview). |

### Pillar 4 — Monitoring & Analytics

Skills that track performance and surface what needs attention.

| Skill | What It Does |
|-------|-------------|
| [`gsc-performance-monitoring`](./gsc-performance-monitoring/SKILL.md) | Weekly/monthly GSC review. What's gaining, what's losing, what needs action. |
| [`performance-monitoring-dashboard`](./performance-monitoring-dashboard/SKILL.md) | Cross-platform performance snapshot across GA4, GSC, Shopify, and Ahrefs. |
| [`competitive-monitoring`](./competitive-monitoring/SKILL.md) | Track competitor ranking movements, new content, and backlink activity. |
| [`monthly-reporting`](./monthly-reporting/SKILL.md) | CEO-ready monthly update. Business impact framing, not vanity metrics. |

### TPV Skills

TPV (Third Party Validator) domains are a long-term authority play — a secondary property that builds ranking power alongside the core domain. **TPV work never competes with core domain SEO for priority during launch.** These skills apply once a PortCo has an established TPV domain and the core SEO workstream is in a healthy rhythm.

| Skill | What It Does |
|-------|-------------|
| [`tpv-content-strategy`](./tpv-content-strategy/SKILL.md) | Develop a content and SEO strategy for a TPV property targeting a specific money keyword. |
| [`tpv-comparison-pages`](./tpv-comparison-pages/SKILL.md) | Build comparison and roundup content for TPV properties. Covers CTR2 optimization and CTA placement. |

---

## Skill Status

| Status | Count |
|--------|-------|
| ✅ Built | 15 |
| 🔲 In progress | 2 (SEO Content Brief, Core Web Vitals Review) |

---

## About

Built by Justin Chaplin, Head of Organic Growth at Mechanism.  
Last updated: March 2026
