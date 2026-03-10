# Mechanism Organic Team — Claude Skills Library

> A library of Claude-powered SEO workflows built for Mechanism's portfolio companies. Each skill encodes how the Organic Team approaches a specific task — not generic SEO advice, but Mechanism-specific thinking built from operating across multiple PortCos.

---

## Quick Start

New to this? Follow these four steps to go from zero to running your first skill in about 10 minutes.

### What You'll Need

| Requirement | Details |
|-------------|---------|
| Claude Pro account | Required to use skills. $20/month at [claude.ai](https://claude.ai). |
| Claude Code (CLI) | A free command-line tool. Connects Claude to your local skill files. |
| Node.js (version 18+) | Required to run Claude Code. Free download at [nodejs.org](https://nodejs.org). |
| Terminal | Mac: Terminal app (search with Cmd+Space). Windows: Command Prompt or PowerShell. |

---

### Step 1 — Create a Claude Account

1. Go to [claude.ai](https://claude.ai) and sign up with your work email
2. Click your name in the bottom-left corner → **Upgrade to Pro** ($20/month)
3. Confirm it's working: open a new conversation and type anything — Claude should respond

> **Note:** If Mechanism is covering the cost, confirm with Justin before signing up.

---

### Step 2 — Install Node.js and Claude Code

**Install Node.js:**

1. Go to [nodejs.org](https://nodejs.org) and download the **LTS** version (labeled "Recommended for most users")
2. Run the installer — click through with default settings
3. Confirm it worked — open Terminal and run:

```
node --version
```

You should see something like `v20.x.x`.

**Install Claude Code:**

In Terminal, run:

```
npm install -g @anthropic-ai/claude-code
```

Confirm it worked:

```
claude --version
```

**Connect Claude Code to your account:**

```
claude
```

The first time you run this, a browser window opens asking you to log in. Sign in with the Claude account from Step 1. Once authorized, you're connected.

> **Troubleshooting:** If you see `Permission denied` on Mac, prefix the command with `sudo` — e.g. `sudo npm install -g @anthropic-ai/claude-code` — and enter your Mac password when prompted.

---

### Step 3 — Install the Skills

In Terminal, run these commands one at a time, pressing Enter after each:

```
cd ~
mkdir -p .claude/skills
cd .claude/skills
git clone https://github.com/justinchaplin/mechanism-seo-skills.git .
```

> **Note:** The `.` at the end of the last command is important — it downloads files directly into your current folder rather than creating a subfolder.

**Confirm it worked:**

```
ls
```

You should see skill folders listed: `non-branded-keyword-research`, `page-optimizer`, `serp-analysis`, etc. If you see them, you're done.

> **If you see `git: command not found`:** Install Git from [git-scm.com/downloads](https://git-scm.com/downloads), then repeat the `git clone` command.

---

### Step 4 — Run Your First Skill

In any Claude conversation at [claude.ai](https://claude.ai), type `@` followed by the skill name and your inputs:

```
@page-optimizer Audit https://letsliveitup.com/products/electrolytes for the keyword "electrolyte powder"
```

```
@serp-analysis Run a SERP analysis for "greens powder"
```

```
@non-branded-keyword-research PortCo: Live It Up — electrolyte supplement brand targeting daily hydration
```

Claude will load the skill and run the full workflow automatically. You don't need to explain what the skill does — just provide the inputs.

---

### Keeping Skills Up to Date

When skills are updated, Justin will post in Slack. To pull the latest version, run:

```
cd ~/.claude/skills && git pull
```

---

## Skill Library

**19 skills across 4 pillars + TPV.**

---

### Pillar 1 — Content

| Skill | What It Does |
|-------|-------------|
| [`non-branded-keyword-research`](./non-branded-keyword-research/SKILL.md) | Build a prioritized non-branded keyword list for a PortCo from scratch using Ahrefs + SERP analysis. Outputs a ranked target list with vehicle decisions. |
| [`serp-analysis`](./serp-analysis/SKILL.md) | Analyze the live SERP for a keyword — classify intent, map page types, identify what's winning, surface content gaps and opportunity score. |
| [`seo-entry-plan`](./seo-entry-plan/SKILL.md) | Takes keyword research output and produces a concrete, page-level execution brief. The "what to actually do" skill. |
| [`content-strategy`](./content-strategy/SKILL.md) | Develop a full content strategy with topic clusters, content calendar, and E-E-A-T quality standards. |
| [`page-optimizer`](./page-optimizer/SKILL.md) | Audit an existing page against a target keyword and the live SERP. Produces a competitor-informed, prioritized optimization plan with specific copy rewrites. |

---

### Pillar 2 — Link Building

| Skill | What It Does |
|-------|-------------|
| [`seo-competitor-link-gap`](./seo-competitor-link-gap/SKILL.md) | Pull Ahrefs Link Intersect data and produce a prioritized outreach target list. |
| [`link-building-strategy`](./link-building-strategy/SKILL.md) | Determine the right link building tactic mix for a PortCo's stage and category. |
| [`outreach-direction`](./outreach-direction/SKILL.md) | Build outreach messaging and angle recommendations for a specific link building campaign. |

---

### Pillar 3 — Technical SEO

| Skill | What It Does |
|-------|-------------|
| [`site-health-audit`](./site-health-audit/SKILL.md) | Full technical audit covering crawlability, indexability, on-page signals, schema, images, and Core Web Vitals. Three modes: Full, Single Page, Targeted. |
| [`branded-serp-audit`](./branded-serp-audit/SKILL.md) | Analyze how a PortCo brand appears on its own branded SERP. Includes ORM triage. |
| [`aeo-geo-audit`](./aeo-geo-audit/SKILL.md) | Assess how a PortCo appears in AI-generated search answers — ChatGPT, Perplexity, Google AI Overview. |

---

### Pillar 4 — Monitoring & Analytics

| Skill | What It Does |
|-------|-------------|
| [`gsc-performance-monitoring`](./gsc-performance-monitoring/SKILL.md) | Weekly/monthly GSC review. What's gaining, what's losing, what needs action. |
| [`performance-monitoring-dashboard`](./performance-monitoring-dashboard/SKILL.md) | Cross-platform performance snapshot across GA4, GSC, Shopify, and Ahrefs. |
| [`competitive-monitoring`](./competitive-monitoring/SKILL.md) | Track competitor ranking movements, new content, and backlink activity over time. |
| [`monthly-reporting`](./monthly-reporting/SKILL.md) | CEO-ready monthly update. Business impact framing, not vanity metrics. |

---

### TPV Skills

TPV (Third Party Validator) domains are a long-term authority play — a secondary property that builds ranking power alongside the core brand domain. **TPV work is never prioritized over core domain SEO.** These skills apply once a PortCo has an established TPV domain and the core SEO workstream is in a healthy rhythm.

| Skill | What It Does |
|-------|-------------|
| [`tpv-content-strategy`](./tpv-content-strategy/SKILL.md) | Develop a content and SEO strategy for a TPV property targeting a specific money keyword. |
| [`tpv-comparison-pages`](./tpv-comparison-pages/SKILL.md) | Build comparison and roundup content for TPV properties. Covers CTR2 optimization and CTA placement. |

---

## Skill Status

| Status | Count |
|--------|-------|
| ✅ Built | 19 |
| 🔲 Planned | SEO Content Brief, Core Web Vitals Review, Redirect & Migration Audit |

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| `git: command not found` | Install Git from [git-scm.com/downloads](https://git-scm.com/downloads), then re-run the `git clone` command. |
| `node: command not found` | Re-download Node.js LTS from [nodejs.org](https://nodejs.org) and re-run the installer. |
| `claude: command not found` | Re-run: `npm install -g @anthropic-ai/claude-code` |
| `Permission denied` on Mac | Prefix with `sudo` — e.g. `sudo npm install -g @anthropic-ai/claude-code` |
| Skill doesn't seem to run | Make sure you've completed Steps 2 and 3, then restart Claude.ai. Use exact skill names with no spaces: `@page-optimizer` not `@page optimizer`. |
| Skills are out of date | Run `cd ~/.claude/skills && git pull` |

---

## Commands Cheat Sheet

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Verify installs
node --version
claude --version

# Create skills folder and download skills
cd ~
mkdir -p .claude/skills
cd .claude/skills
git clone https://github.com/justinchaplin/mechanism-seo-skills.git .

# Update skills to latest version
cd ~/.claude/skills && git pull

# List installed skills
ls ~/.claude/skills
```

---

## About

Built by Justin Chaplin, Head of Organic Growth at Mechanism.  
Questions? Ping Justin in Slack.  
Last updated: March 2026
