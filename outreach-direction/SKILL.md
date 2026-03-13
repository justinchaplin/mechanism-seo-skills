---
name: outreach-direction
description: Identifies the highest-value link building targets for a Mechanism portfolio company and determines the right pitch angle for each — scored across link authority, SERPdom value, and halo effect potential. Use this skill whenever someone asks how to approach link building outreach, what sites to target, how to pitch a specific site, what angle to use for outreach, or how to prioritize link building targets. Also trigger when someone says things like "how do we pitch [site]", "what's our outreach strategy for [brand]", "who should we be reaching out to for [brand]", or "how do we get into [site]'s roundup". Always use this skill rather than giving generic outreach advice.
compatibility: "Requires Ahrefs MCP (for domain metrics and SERP ranking data) and web_search (for SERP research and target site analysis). Requires PortCo knowledge file for pitch angle derivation."
---

# Outreach Direction

This skill identifies the highest-value outreach targets for a Mechanism PortCo and determines the right pitch angle for each. It scores targets across three dimensions — link authority, SERPdom value, and halo effect potential — so the team always knows not just who to reach out to, but why and how.

This skill is about strategy and angle. Email templates are handled separately — this tells you what to say and why, not how to format it.

---

## Inputs Required

Before starting, confirm you have:
- **Brand name** — the PortCo being analyzed
- **Domain** — root domain (e.g., primeputt.com)
- **PortCo knowledge file** — required for pitch angle derivation (what's distinctive, target customer, money keywords)
- **Target site or tactic** (optional) — if a specific site or tactic has been identified, assess that directly. Otherwise run the full target identification workflow.

---

## How Mechanism Thinks About Outreach Targets

Before running the workflow, understand the scoring philosophy:

**Not all links are equal — and not all equal links are equal for the same reason.**

A link from Breaking80 for PrimePutt does three things simultaneously:
1. **Link authority** — adds a high-DR, niche-relevant backlink to the domain
2. **SERPdom value** — Breaking80 ranks P1 for "best putting mat" — being in that article means PrimePutt appears in a P1 result for its money keyword
3. **Halo effect** — Breaking80's readers are serious golfers — PrimePutt's exact target customer. Brand exposure here converts across paid, direct, and referral later.

A scholarship link from a college site does only one thing (weakly): adds a backlink. No SERPdom value. No halo effect. Not worthless — but a completely different category of target.

**The best outreach targets score high on all three dimensions.** The team should always know which dimension they're optimizing for when they reach out.

---

## Step 1: Read the PortCo Knowledge File

Before identifying targets, extract from the PortCo knowledge file:
- **Money keywords** — these drive which SERP positions matter
- **What's distinctive about the product** — this is the pitch hook
- **Target customer** — this defines which sites have halo effect value
- **Benchmark competitors** — their backlink profiles reveal where to outreach

If the knowledge file doesn't exist or is incomplete, flag the missing fields before proceeding.

---

## Step 2: Identify SERP-Ranked Target Sites

For each of the PortCo's top 3 money keywords, search Google and identify every site ranking in the top 10 organic positions that:
- Is an editorial/content site (not a retailer, not Amazon, not the PortCo itself)
- Has published content that includes or could include a product like this PortCo's

These are **SERPdom targets** — sites where a placement simultaneously earns a link and puts the brand in front of customers who are actively searching for the money keyword.

For each SERP target, note:
- Which money keyword they rank for
- Their position (P1–P10)
- What type of content they published (roundup, review, guide)
- Whether the PortCo is already mentioned

---

## Step 3: Pull Competitor Backlinks for Additional Targets

Using Ahrefs, pull referring domains for the top 2–3 benchmark competitors:

```
Ahrefs: site-explorer-referring-domains
target: [competitor domain]
```

Cross-reference with SERP targets from Step 2. Add any high-relevance referring domains not already on the list.

Filter for:
- DR 30+ preferred but relevance over DR always
- Topically relevant to the PortCo's category
- Real content sites — not directories, not PBNs

---

## Step 4: Score and Prioritize Targets

For each target, score across three dimensions on a simple H/M/L scale:

**Link Authority Value**
- H: DR 50+, niche-relevant, editorial content
- M: DR 30–50, relevant, or DR 50+ but less targeted
- L: DR < 30, or high DR but low relevance

**SERPdom Value**
- H: Ranks in top 5 for one of the PortCo's money keywords
- M: Ranks in positions 6–20 for a money keyword, or ranks for supporting keywords
- L: Doesn't rank for any target keywords

**Halo Effect Potential**
- H: Site's audience is the PortCo's exact target customer (e.g., golf sites for PrimePutt, eco/home sites for Hey Sunday)
- M: Site's audience overlaps with but isn't exclusively the target customer
- L: General audience with limited customer overlap

**Priority tiers:**
- 🔴 Tier 1 — H on SERPdom + H on Halo Effect (highest value, pursue first)
- 🟡 Tier 2 — H on at least one dimension, M on others
- 🔵 Tier 3 — Good link authority but low SERPdom/halo value (still worth pursuing, lower urgency)

---

## Step 5: Derive Pitch Angles

For each Tier 1 and Tier 2 target, derive the specific pitch angle using the PortCo knowledge file's "what's distinctive" field and the site's specific content.

**Pitch angle formula:**
*[What the site cares about] + [What makes the PortCo worth featuring] + [Specific ask]*

**Tactic-specific angles:**

**Roundup inclusion (existing article):**
"They already have a 'best [category]' article. Lead with a specific reason the PortCo belongs in it — not 'we'd love to be featured' but 'here's why our product stands out vs. what you've already included.' Offer a sample if physical product."

**Roundup inclusion (upcoming/new article):**
"Pitch the angle of the product story, not the product features. For PrimePutt: 'serious golfers who try it say it's the best they've used — here's why.' Make it easy for the writer to include it without doing extra research."

**Broken link replacement:**
"Lead with solving their problem first. 'I noticed [specific link] on your [specific page] is broken — we have content that would serve as a direct replacement.' Don't mention the link ask until they acknowledge the problem."

**Product review / editorial mention:**
"Make the product available. The strongest pitch is often just getting it in their hands. For physical products: offer to send one at no cost. For digital/service: offer a trial or walkthrough. Let the product do the pitch."

**Resource page inclusion:**
"Connect to their audience's needs specifically. Why does their audience need to know about this PortCo? What problem does it solve for their readers? Lead with the audience benefit, not the product features."

---

## Output Format

---

**Outreach Direction — [Brand Name]**
*Analyzed: [date]*

**SERP Landscape Summary:**
[2–3 sentences on who controls the editorial layer for the PortCo's money keywords — who are the highest-value SERPdom targets and why]

**Prioritized Target List:**

| Site | DR | SERPdom Value | Halo Effect | Link Authority | Tier | Pitch Angle |
|------|----|--------------|-------------|----------------|------|-------------|
| breaking80.com | [DR] | H — P1 "best putting mat" | H — serious golfers | H | 🔴 Tier 1 | Existing roundup inclusion — lead with product quality claim, offer to send a mat |
| ... | | | | | | |

**Tier 1 Deep Dives:**
For each Tier 1 target, a short paragraph:
- What content they have that's relevant
- Exactly what the pitch should lead with
- What the ask is
- What to offer

**What NOT to Pitch:**
[Specific site types or target categories that would be a waste of outreach time for this specific PortCo — with rationale]

**First Outreach Recommendation:**
[One specific target to start with, the exact angle, and why it's the highest-leverage first move]

---

## Judgment Guidelines

- **SERPdom value multiplies link value.** A link from a site that ranks P1 for your money keyword is worth dramatically more than the same DR site that doesn't rank for anything relevant. Always check SERP position before scoring.
- **The pitch angle comes from the product, not the template.** Generic outreach fails because it doesn't give the site owner a reason to care. The "what's distinctive" field in the PortCo knowledge file is the source of every good pitch.
- **Physical products have a natural pitch lever — send them.** For ecommerce PortCos, product seeding is the highest-conversion outreach tactic. Getting the product in a writer's hands removes the friction of convincing them without evidence.
- **Don't lead with the link ask.** The ask is implicit in the outreach type. Lead with the value — why their readers benefit from knowing about this product.
- **Roundup articles are the highest-leverage targets in ecommerce.** A "best [category]" article ranking P1 checks all three boxes: link authority, SERPdom presence, and audience relevance. These are always Tier 1 for physical product PortCos.
- **Flag the halo effect dimension explicitly in the output.** The team needs to understand they're not just building links — they're building brand presence in the places their customers make decisions.

---

## Example Trigger Phrases

- "How do we get PrimePutt into the Breaking80 roundup?"
- "What's our outreach strategy for Hey Sunday?"
- "Who should we be reaching out to for Hello Pest?"
- "How do we pitch [site] for a link?"
- "What's the angle for getting into golf authority sites?"
- "Identify the highest-value outreach targets for [brand]"
- "How do we approach outreach for a new brand entering the [category] market?"
