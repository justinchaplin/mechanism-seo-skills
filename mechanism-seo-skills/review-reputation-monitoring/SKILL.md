---
name: review-reputation-monitoring
description: Audits the current reputation health of a Mechanism portfolio company across all review surfaces — brand site, third-party platforms, Reddit, and AI — and flags risks, gaps, and opportunities. Use this skill whenever someone asks about reviews, brand reputation, what customers are saying, whether negative feedback is showing up, or whether there are reputation issues to address. Also trigger when someone says things like "what are customers saying about [brand]", "are our reviews healthy", "check reputation for [brand]", "run a reputation check", "is there negative sentiment about [brand]", "what does our review profile look like", or "something bad is showing up in reviews". Always run this skill rather than giving ad hoc reputation assessments. Especially critical for early-stage engagements (feasibility and 0-to-1 phases), post-incident situations, and before major content or link building pushes.
compatibility: "Requires web_search and browser tools (Claude in Chrome) for extracting live review data from JS-rendered platforms. Ahrefs Brand Radar useful but optional for AI visibility data. PortCo knowledge file required for brand name, domain, product line, launch date, and competitor context."
---

# Review & Reputation Monitoring

This skill audits the reputation health of a Mechanism portfolio company — what real buyers find when they go looking for social proof, and whether what they find helps or hurts conversion.

The framing is simple: **if a CEO asked "what is my company's general online reputation?", this skill answers that question.**

Reputation matters for SEO beyond the obvious. Review content influences conversion on every channel. Reddit threads rank in branded SERPs. AI assistants surface review sentiment in zero-click answers. A brand can win on content and links while losing conversions because the reputation layer is weak or actively damaged.

---

## Step 0: Establish Launch Stage Context

Before running any audit, determine which stage the brand is in. This changes what "healthy" looks like and what the right actions are.

Pull the brand's launch date from the PortCo knowledge file and categorize:

**🌱 Early Stage (0–6 months live)**
- Review counts will be low by default — this is expected
- The primary risk is having *zero* reviews, not having *few* reviews
- A seeded review strategy (real customer reviews + supplemental AI-assisted reviews as a temporary bridge) may be in play — note this if known, and assess whether early reviews read naturally and cover the key product benefits buyers care about
- Benchmark against competitors at a similar stage, not against mature brands
- Focus: Is there enough social proof to support conversion? Are the early reviews positive?

**📈 Growth Stage (6–18 months live)**
- Review counts should be accelerating
- Benchmark against direct competitors — are we pacing with or behind them?
- First negative patterns or Reddit threads may be emerging — flag these early
- Focus: Velocity, platform coverage, first signs of brand narrative forming

**🏢 Mature Stage (18+ months live)**
- Reputation profile is largely set — audit is about protecting it
- Velocity gaps against competitors compound over time — flag if widening
- Incident monitoring becomes more important (Reddit, AI surfacing complaints)
- Focus: Consistency, response rate, AI reputation alignment

---

## Step 1: First-Party Reviews (Brand's Own Site)

Navigate to the brand's key product pages using browser tools. Most DTC brands use JS-rendered review widgets (Okendo, Yotpo, Junip) — `web_fetch` will not load these. Use the Chrome browser tool.

For each key product page:

**Extract:**
- Overall star rating and total review count
- Approximate monthly velocity — count reviews with dates in the last 30 days, or estimate from recent date stamps
- Most common themes in the last 20–30 reviews (positive and negative)
- Whether the brand responds to reviews, and how often

**Flag if:**
- Rating is below 4.2 — meaningful conversion drag for DTC
- No reviews in the last 30 days on a live, active product
- Negative reviews cluster around a specific issue (ingredient, shipping, product performance)
- Brand is not responding to negative reviews at all

---

## Step 2: Third-Party Review Platforms

Check the platforms buyers in this category actually use for research. For Mechanism's DTC portfolio:

**Note: Mechanism PortCos are not on Amazon and do not have mobile apps. Do not check those surfaces.**

### Trustpilot

Check: `trustpilot.com/review/[domain]`

Extract: TrustScore, total review count, review velocity (sort by newest), recurring themes, whether the brand responds.

**Important context on Trustpilot:** Trustpilot's algorithm is partially opaque. Brands cannot directly solicit reviews with incentives, and automated invitation tools require a business account integration. For early-stage brands, Trustpilot pages often have very few reviews because there's no active generation mechanism in place yet — this is normal, not a red flag. The right action if velocity is low: set up the Trustpilot Business free account and enable post-purchase review invitations. Do not chase volume through other means.

**Flag if:**
- TrustScore below 3.5 — this surfaces in branded SERPs and is visible to buyers
- Cluster of recent 1-star reviews in a short window — possible incident or bot attack
- Brand has a Trustpilot page but has never responded to any reviews

### Google Business Profile

Search the brand name and check the knowledge panel for a star rating and review count. Low-stakes for DTC brands without physical retail, but it surfaces in branded SERPs. Note it if it exists.

### YouTube

Search `"[brand name] review"` — note top 3–5 video titles, channel size, publication date, and framing (positive, mixed, negative).

**Flag if:** A video with 10K+ views has a negative title or thumbnail.

---

## Step 3: Reddit & UGC Sentiment

Reddit is the highest-risk third-party surface for DTC brands. Threads rank in Google, persist for years, and are trusted by skeptical buyers precisely because they appear unmoderated.

Run each of the following:

1. `"[brand name]" site:reddit.com` — all indexed threads
2. `"[brand name]" reviews reddit` — what skeptical buyers find in Google
3. Search within `r/[relevant subreddit]` directly (e.g., r/SkincareAddiction, r/Supplements, r/EatCheapAndHealthy depending on category)

For each thread found, note:
- Subreddit and thread title
- Dominant sentiment: ✅ positive / ⚠️ mixed / 🔴 negative
- Number of comments / engagement level
- Date posted
- Whether the brand or a brand-affiliated account responded
- Whether the thread ranks in Google for "[brand name] reviews"

**Flag if:**
- Any negative thread ranks in Google's top 5 for "[brand name] reviews" — this is influencing purchase decisions right now
- A thread with 30+ comments has negative dominant sentiment
- Thread content involves safety, health, or legal concerns — these get pulled into AI answers

---

## Step 4: AI Reputation Check

AI assistants are an increasingly common first stop for buyers who want a quick verdict on a brand. They pull from sources including Reddit, review sites, and press — sometimes surfacing negative content the brand isn't actively monitoring.

For each platform below, prompt: "What do people think of [brand name]?" and "Are there any complaints about [brand name]?"

Check: ChatGPT, Perplexity, Gemini. (Use Ahrefs Brand Radar AI Responses via MCP if available for structured data.)

For each response note:
- Overall framing (positive / neutral / cautious / negative)
- Whether any specific incidents or complaints are surfaced
- Which sources are cited if visible

**Flag if:**
- AI surfaces a specific complaint or incident without positive context to balance it
- AI response is materially more negative than the brand's own review profile
- AI cites Reddit or consumer complaint sites as primary sources

---

## Step 5: Response Strategy Spot Check

A 2-minute check to assess whether the brand is actively managing its reputation or letting it drift.

**Check:**
- What % of reviews under 4 stars have brand responses?
- Do responses address the specific complaint or use a generic template?
- Tone: professional and empathetic, or defensive?

**Benchmark:** Brands in healthy standing respond to 80–100% of negative reviews and at least 20–30% of positive ones. Zero responses on a platform with 20+ reviews is a flag.

**Note:** Drafting 3–4 response templates (5-star, 4-star, 3-star, 1–2 star) takes an hour and immediately improves buyer perception for anyone reading the review thread. Easy win worth flagging to the CEO.

---

## Output Format

---

**Online Reputation Snapshot — [Brand Name]**
*Audited: [date] | Launch stage: [Early / Growth / Mature]*

**Overall Assessment:** [🟢 Healthy / 🟡 Watch / 🔴 Act Now]

[3–4 sentences that directly answer: "What is this company's general online reputation?" — written for a CEO, not an SEO report. Lead with the overall picture, then name the single biggest risk and single biggest opportunity.]

---

**Review Profile**

| Surface | Rating | Count | Monthly Velocity | Status |
|---------|--------|-------|-----------------|--------|
| Brand site (flagship product) | X.X/5 | XXX | ~XX/mo | 🟢/🟡/🔴 |
| Brand site (secondary product) | X.X/5 | XXX | ~XX/mo | 🟢/🟡/🔴 |
| Trustpilot | X.X/5 | XXX | ~XX/mo | 🟢/🟡/🔴 |
| Google | X.X/5 | XXX | — | 🟢/🟡/🔴 |

**What buyers are saying (positive):** [Top 2–3 themes from recent reviews]
**What buyers are saying (negative):** [Top 2–3 themes — or "No significant negative patterns observed" if clean]
**Brand response rate:** [Active / Sporadic / None observed]

---

**Reddit & UGC**

[If no Reddit presence: "No Reddit threads found mentioning [brand]. Normal for early-stage brands — worth monitoring monthly as brand awareness grows."]

[If Reddit threads exist:]
| Thread | Sentiment | Engagement | Ranks in Google? |
|--------|-----------|------------|-----------------|
| [title] | ✅/⚠️/🔴 | XX comments | Yes / No |

---

**AI Reputation**

| Platform | Framing | Incidents Surfaced? |
|----------|---------|-------------------|
| ChatGPT | Positive / Neutral / Cautious / Negative | Yes / No |
| Perplexity | Positive / Neutral / Cautious / Negative | Yes / No |
| Gemini | Positive / Neutral / Cautious / Negative | Yes / No |

[1–2 sentences: is AI reputation aligned with actual review sentiment, or diverging?]

---

**🔴 Act Now**
[Specific risks actively hurting conversion or search — be direct about what's happening and why it matters]

**🟡 Address This Month**
[Gaps that aren't urgent but will compound — platform coverage, response rate, velocity lag]

**🟢 Looking Good**
[What's working — worth noting for CEO context and stakeholder updates]

---

**Recommended Actions**
1. [Specific action — what, who, timeline]
2. [Specific action]
3. [Monitor — re-run cadence]

---

## Judgment Guidelines

- **Read launch stage before reading the numbers.** A brand with 47 reviews at 4.6 stars that's been live 3 months is in great shape. The same numbers at 24 months is a problem. Never evaluate reputation in isolation from brand age.
- **Early-stage seeding is a known strategy.** If it's in play, don't flag it as a risk internally. Assess whether early reviews read naturally and whether the transition to fully organic reviews is on track.
- **Trustpilot is a black box.** The algorithm and weighting aren't fully transparent. Don't promise specific outcomes from Trustpilot work. The right recommendation is always: set up the free business account, enable post-purchase invitations, let it build organically.
- **Reddit is the highest-leverage reputation risk.** A single high-engagement negative thread ranking in Google for "[brand] reviews" is worth escalating above almost everything else in this audit.
- **AI reputation and Google reputation can diverge.** Check both — they require different remediation approaches.
- **The CEO output should be readable in 90 seconds.** The overall assessment paragraph is the most important part. Write it like a trusted advisor giving a frank brief, not like an SEO report.
- **Tie reputation to the halo effect in stakeholder framing.** Weak reviews mean organic traffic converts less efficiently — every point of SEO growth is worth less if the reputation layer is leaking conversion. Frame it this way when reporting to justify reputation work.
- **Post-incident, run this skill before any content or link building work.** No point driving traffic to a brand in the middle of a reputation crisis. The conversation shifts from growth to protection first.

---

## Example Trigger Phrases

- "Run a reputation check for Live It Up"
- "What are customers saying about Hey Sunday?"
- "Check if there's negative sentiment on Reddit about PrimePutt"
- "Is the salmonella situation showing up in customer reviews?"
- "We need a reputation baseline before we start content"
- "How are our reviews looking — anything to flag for the CEO?"
- "What does our review profile look like for Hello Pest?"
- "Run ORM audit on [brand]"
