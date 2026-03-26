# Mechanism Organic Team — Claude Skills Library

A library of Claude-powered SEO workflows built for Mechanism's portfolio companies. Each skill encodes how the Organic Team approaches a specific SEO task — not generic advice, but Mechanism-specific thinking built from operating across multiple PortCos.

This library exists so the team can run high-quality SEO work without needing a dedicated SEO specialist in the room. The skills handle the thinking. You handle the inputs and judgment calls.

---

## What Is This?

Each "skill" is a markdown file that tells Claude exactly how to approach a specific SEO task — what to look at, what to flag, how to structure the output, and what to do with the results. There are 18 skills covering everything from keyword research and content strategy to link building, technical audits, and monthly reporting.

Skills are organized into four pillars:

- **Content** — keyword research, SERP analysis, content planning, page optimization
- **Link Building** — competitor gap analysis, link strategy, outreach direction
- **Technical SEO** — site health, branded SERP audits, AI search presence (AEO/GEO)
- **Monitoring & Analytics** — GSC monitoring, performance dashboards, competitive tracking, monthly reporting, review & reputation monitoring

Plus two **TPV skills** for Mechanism's third-party validator domain strategy.

Browse the full list by clicking into the `mechanism-seo-skills/` folder above.

---

## How to Use These Skills

There are two ways to use these skills. One is significantly more powerful than the other.

---

### Path 1 — Claude Code (Recommended)

**This is the right way to use the library.** Claude Code is a free command-line tool that connects Claude to your local skill files and gives it access to real tools — web browsing, Ahrefs data, file saving, and more. Skills run as designed, outputs save automatically to your machine as Word documents, and you can run complex multi-step workflows without babysitting the process.

If you want to actually use these skills in your day-to-day work, set up Claude Code. It takes about 20–30 minutes once.

#### What You'll Need

| Requirement | Details |
|-------------|---------|
| Claude Max account | Recommended — you will hit rate limits on Pro quickly. Claude Max is $100/month at [claude.ai](https://claude.ai). Claude Pro ($20/month) works but is the minimum. |
| Node.js (version 18+) | Free at [nodejs.org](https://nodejs.org) |
| Claude Code (CLI) | Free — installed via terminal |
| Git | Free — usually pre-installed on Mac |

#### Setup (One-Time)

**Step 1 — Create a Claude account**

> **Already have a Claude account? Skip to Step 2.**

Go to [claude.ai](https://claude.ai), sign up with your work email, and upgrade to Max (recommended) or Pro. If Mechanism is covering the cost, confirm with your manager first.

**Step 2 — Install Node.js**

Go to [nodejs.org](https://nodejs.org) and download the LTS version. Run the installer with default settings. Confirm it worked:

```bash
node --version
```

You should see something like `v20.x.x`.

**Step 3 — Install Claude Code**

Open Terminal (Mac: Cmd+Space → type "Terminal") and run:

```bash
npm install -g @anthropic-ai/claude-code
```

Confirm it worked:

```bash
claude --version
```

If you see `Permission denied`, prefix with `sudo`:

```bash
sudo npm install -g @anthropic-ai/claude-code
```

**Step 4 — Connect Claude Code to your account**

```bash
claude
```

The first time you run this, a browser window opens asking you to log in. Sign in with your Claude account. Once authorized, you're connected. You can close the browser window and return to Terminal.

**Step 5 — Download the skills**

```bash
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/justinchaplin/mechanism-seo-skills.git .
```

Confirm it worked:

```bash
ls ~/.claude/skills/mechanism-seo-skills/
```

You should see skill folders listed. If you see them, you're done with setup.

> **If you see `git: command not found`:** Install Git from [git-scm.com/downloads](https://git-scm.com/downloads), then re-run the `git clone` command.

---

#### Running a Skill

Open Terminal and start Claude Code:

```bash
claude --dangerously-skip-permissions
```

> **Why `--dangerously-skip-permissions`?** This flag tells Claude Code to run without stopping to ask for confirmation at every step. Without it, Claude will pause and ask you to approve each tool use (web search, file save, etc.), which breaks the automation. The flag is safe to use for these SEO workflows.

Then reference the skill file and describe your task in plain language:

```
@~/.claude/skills/mechanism-seo-skills/mechanism-seo-skills/page-optimizer/SKILL.md

Run the page optimizer for Live It Up — audit the supergreens product page
```

```
@~/.claude/skills/mechanism-seo-skills/mechanism-seo-skills/competitive-monitoring/SKILL.md

Run competitive monitoring for Live It Up
```

```
@~/.claude/skills/mechanism-seo-skills/mechanism-seo-skills/monthly-reporting/SKILL.md

Run monthly SEO reporting for HeySunday — March 2026
```

You don't need to give Claude a long brief — just name the brand and what you want. Claude reads the skill file and knows what to do.

Output saves as a Word document to `~/Documents/mechanism-seo/outputs/`.

---

#### PortCo Knowledge Files

**Knowledge files are required, not optional.** Skills work best — and in many cases only correctly — when Claude knows who it's working for. Each PortCo has a knowledge file with the brand's products, SEO metrics, competitors, and key context that Claude needs to run skills accurately.

Ask whoever manages this library for the knowledge file for your PortCo. Once you have it, save it here:

```bash
mkdir -p ~/.claude/skills/contexts
mv ~/Downloads/liveitup-knowledge.md ~/.claude/skills/contexts/
```

Then just mention the brand name when running a skill — Claude will find the context file automatically.

---

#### Keeping Skills Up to Date

When skills are updated, pull the latest version:

```bash
cd ~/.claude/skills && git pull
```

---

### Path 2 — Claude.ai One-Off (Limited)

If you just need to run a single skill quickly and don't want to set up Claude Code, you can upload a skill file directly into a Claude conversation. **This is a fallback, not the recommended path.** To really unlock this library and use it day-to-day, you need Claude Code.

The one-off path works for text-heavy skills like monthly reporting or content strategy — but it won't work for skills that need live data. Skills that require Ahrefs, web crawling, or file saving will produce incomplete outputs via this path.

**How it works:**

1. Go to [github.com/justinchaplin/mechanism-seo-skills](https://github.com/justinchaplin/mechanism-seo-skills) and navigate to the skill you want
2. Open `SKILL.md`, click the download icon (or copy the raw content)
3. Go to [claude.ai](https://claude.ai) and start a new conversation
4. Upload or paste the SKILL.md content as a reference file
5. Describe what you want: *"Follow this skill to run a content strategy for HeySunday — laundry sheets brand targeting eco-conscious households"*

**Skills that work reasonably well via this path:**
- `monthly-reporting`
- `content-strategy`
- `link-building-strategy`
- `seo-entry-plan`
- `outreach-direction`

**Skills that require Claude Code to work properly:**
- Anything pulling Ahrefs data
- `page-optimizer`, `site-health-audit`, `branded-serp-audit` (need live page crawling)
- `gsc-performance-monitoring`, `performance-monitoring-dashboard` (need live data access)
- `competitive-monitoring`, `aeo-geo-audit`, `review-reputation-monitoring`

---

## About This Library

Built by Justin Chaplin, Head of Organic Growth at Mechanism. These skills encode the SEO approach that worked across the portfolio — they're a starting point, not a finished system. The expectation is that whoever inherits this will build on top of it, update skills as the tools and tactics evolve, and add new ones as new workflows get figured out.

The repo is public. The skills are the methodology. The PortCo knowledge files are private and shared separately.

Questions? Start by reading the SKILL.md file for the skill you want to run — each one explains what it does, what inputs it needs, and what the output looks like.

---

## Commands Cheat Sheet

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Verify installs
node --version
claude --version

# Download skills (first time)
mkdir -p ~/.claude/skills
cd ~/.claude/skills
git clone https://github.com/justinchaplin/mechanism-seo-skills.git .

# Update skills
cd ~/.claude/skills && git pull

# Run Claude Code with skills
claude --dangerously-skip-permissions

# Create outputs folder
mkdir -p ~/Documents/mechanism-seo/outputs
```
