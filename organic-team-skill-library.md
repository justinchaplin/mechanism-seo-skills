# Mechanism Organic Team — Skill Library

> This document defines the full skill library for the Organic Team. Skills are organized into two dimensions: **by function** (what the skill does) and **by who runs it** (Justin vs. the team). Each skill is an executable Claude workflow that encodes Mechanism-specific thinking — not generic SEO advice.
>
> **Scope:** These skills assume foundational setup is complete (GSC connected, Ahrefs access, site live). For launch setup, see the SEO Launch Playbook.

---

## Skills by Bucket

### 🔵 Bucket 1 — Strategy & Research
*High-judgment work. Requires SEO experience and PortCo context. Primarily Justin, or senior team members with oversight.*

| Skill | What It Does | Status |
|-------|-------------|--------|
| **Non-Branded Keyword Research** | Given a PortCo and category, identify and prioritize money keywords via Ahrefs + SERP analysis. Outputs prioritized target list with vehicle decisions (optimize existing page, create new page, or earned media). Feeds into SEO Entry Plan. | ✅ Built |
| **SEO Entry Plan** | Given keyword research output, produce a page-level execution brief: target URL, title tag, content direction, internal linking, schema, link building bar, SERPDom sequencing. The "what to actually do" skill. | ✅ Built |
| **Content Strategy** | Determine what content to create and why across money pages, supporting content, and informational content. Includes competitor content gap analysis. All content must serve a clear business purpose — not just traffic. | ✅ Built |
| **Link Building Strategy** | Given a PortCo's stage, DA, category, and goals, determine the right tactic mix: scholarship vs. content-focused vs. best list outreach vs. partnership. Output tactic prioritization with rationale. | ✅ Built |
| **Competitor Link Gap Analysis** | Pull Ahrefs Link Intersect data for a PortCo vs. competitors. Produce prioritized outreach target list with DR, relevance, and strategic notes. | ✅ Built |

---

### 🟢 Bucket 2 — Execution & Production
*Repeatable production work. Can be run by trained team members (Mary Ann, Ana Julia, Ana Medina) independently.*

| Skill | What It Does | Status |
|-------|-------------|--------|
| **SEO Content Brief** | Given a target keyword and PortCo context, produce a full content brief: supporting keywords, search intent, recommended structure, internal linking opportunities, E-E-A-T signals, and content-to-conversion flow. | 🔲 To build |
| **Outreach Direction** | Given a target link opportunity and PortCo context, determine the right outreach angle and pitch positioning. Strategic direction — not templates (team has those). | ✅ Built |

---

### 🟡 Bucket 3 — Audits & Technical
*Structured audit work. Can be run by team members; outputs become tickets for web dev. Escalate to Justin if issues require strategic judgment.*

| Skill | What It Does | Status |
|-------|-------------|--------|
| **Site Health Audit** | Structured site audit across crawlability, indexability, Core Web Vitals, schema, images, JS rendering, and AI crawlers. Three modes: Full Audit, Single Page Check, Targeted Check. Output is prioritized issue list with fixes. | ✅ Built |
| **Branded SERP Audit** | Analyze how a brand appears on its own branded SERP. What's ranking, what's missing, what needs to be improved or suppressed. Includes ORM triage. | ✅ Built |
| **AEO / GEO Audit** | Assess how a PortCo appears in AI-generated search answers (ChatGPT, Perplexity, Google AI Overview). Entity clarity, structured data, AI crawler access, E-E-A-T signals. Readiness scorecard + action list. | ✅ Built |
| **Core Web Vitals Review** | Assess LCP, CLS, and INP across key pages. Flag failures, recommend fixes for web dev. | 🔲 To build |

---

### 🟠 Bucket 4 — Monitoring & Reporting
*Recurring operational work. Fully delegatable to team once templates and benchmarks are established.*

| Skill | What It Does | Status |
|-------|-------------|--------|
| **GSC Performance Monitoring** | Structured weekly/monthly GSC review. What keywords are gaining or losing? What pages are under-performing vs. impressions? What needs action? | ✅ Built |
| **Performance Monitoring Dashboard Review** | Cross-platform performance snapshot: GA4, GSC, Shopify, Ahrefs. Traffic on money keywords, brand trends, organic conversions, ranking movement. Flag anything needing attention. | ✅ Built |
| **Competitive Monitoring** | Track ranking and content movements from key competitors. Surface new pages, keyword gains/losses, backlink activity. Flag anything requiring strategic response. | ✅ Built |
| **Monthly Reporting** | Produce a halo-effect-framed monthly update. What did we do, why, what moved, what didn't, what's next. Written for a CEO who cares about business impact, not SEO vanity metrics. | ✅ Built |

---

### 🟣 Bucket 5 — TPV (Long-Term Authority Play)
*TPV domains are a secondary property that gradually builds its own ranking power alongside the core domain. **TPV work should never compete with core domain SEO for priority.** These skills apply once a PortCo has an established TPV domain with meaningful authority and the core domain SEO workstream is in a healthy steady state.*

| Skill | What It Does | Status |
|-------|-------------|--------|
| **TPV Content & SEO Strategy** | Given a TPV domain and target money keyword, develop a content + SEO strategy to intercept the SERP. Covers page structure, target keywords, link building needs, E-E-A-T signals, and CTR2 optimization toward the PortCo. | ✅ Built |
| **TPV Comparison Pages** | Build comparison and roundup content for TPV properties. Best [Category], X vs Y, Alternatives pages. CTR2 persuadability filter, schema, CTA placement, content length targets. | ✅ Built |

---

## Skills by Who Runs It

| Bucket | Primary Runner | Can Delegate To Team? |
|--------|---------------|----------------------|
| 🔵 Strategy & Research | Justin | With oversight |
| 🟢 Execution & Production | Team | Yes — fully |
| 🟡 Audits & Technical | Team | Yes — escalate flagged issues |
| 🟠 Monitoring & Reporting | Team | Yes — fully |
| 🟣 TPV | Justin / Team | With context |

---

## GEO / AEO Readiness
A lens applied across all buckets — not a standalone bucket. Relevant to: link building (AI citations), content E-E-A-T (AI trustworthiness), technical schema (entity clarity), and GSC AI Overview monitoring. The AEO / GEO Audit covers the readiness assessment.

---

## Skill Count

| Bucket | Built | To Build |
|--------|-------|----------|
| 🔵 Strategy & Research | 4 | 0 |
| 🟢 Execution & Production | 1 | 1 |
| 🟡 Audits & Technical | 3 | 1 |
| 🟠 Monitoring & Reporting | 4 | 0 |
| 🟣 TPV | 2 | 0 |
| **Total** | **14** | **2** |

---

## Remaining Build Order
1. **SEO Content Brief** (Bucket 2) — execution-level, needed once content strategy is set
2. **Core Web Vitals Review** (Bucket 3) — recurring but lower frequency than other audits

---

## Skill File Locations

| Skill | File |
|-------|------|
| Non-Branded Keyword Research | `non-branded-keyword-research/non-branded-keyword-research.md` |
| SEO Entry Plan | `seo-entry-plan/seo-entry-plan.md` |
| Content Strategy | `content-strategy/content-strategy.md` |
| Link Building Strategy | `link-building-strategy/link-building-strategy.md` |
| Competitor Link Gap Analysis | `seo-competitor-link-gap/competitor-link-gap-analysis.md` |
| Outreach Direction | `outreach-direction/outreach-direction.md` |
| Site Health Audit | `site-health-audit/site-health-audit.md` |
| Branded SERP Audit | `branded-serp-audit/branded-serp-audit.md` |
| AEO / GEO Audit | `aeo-geo-audit/aeo-geo-audit.md` |
| GSC Performance Monitoring | `gsc-performance-monitoring/gsc-performance-monitoring.md` |
| Performance Monitoring Dashboard | `performance-monitoring-dashboard/performance-monitoring-dashboard.md` |
| Competitive Monitoring | `competitive-monitoring/competitive-monitoring.md` |
| Monthly Reporting | `monthly-reporting/monthly-reporting.md` |
| TPV Content & SEO Strategy | `tpv-content-strategy/tpv-content-strategy.md` |
| TPV Comparison Pages | `tpv-comparison-pages/tpv-comparison-pages.md` |

---

*Last updated: March 2026*
*Owner: Justin, Head of Organic Growth, Mechanism*
