---
name: branded-serp-audit
description: Audits what appears in Google when someone searches a Mechanism portfolio company's brand name — identifying what the brand owns, what it doesn't, what third parties are saying, and whether anything on the branded SERP is a risk or an opportunity. Use this skill whenever someone asks what shows up for a brand name search, what the branded SERP looks like, whether a brand controls its search results, if there are reputation issues showing up in branded search, or how to improve branded SERP presence. Also trigger when someone says "what does Google show for [brand]", "audit the branded SERP for [brand]", "do we own our branded search", or "something bad is showing up when you Google [brand]". Always use this skill rather than giving ad hoc assessments.
compatibility: "Requires web_search (to manually check branded SERPs and variations) and Ahrefs MCP (for branded keyword data in GSC via site-explorer-organic-keywords). Requires PortCo knowledge file for brand name, domain, and competitor context."
---

# Branded SERP Audit

This skill audits what Google shows when someone searches a Mechanism portfolio company's brand name. It identifies what the brand controls, what third parties are saying, what's missing, and whether anything represents a risk or an opportunity.

Branded SERPs matter for two reasons. First, they're the last impression before purchase — someone who has already heard of the brand and is Googling it is high-intent. Second, the brand doesn't fully control what appears there — third parties, review sites, Reddit threads, and competitor ads can all show up and influence conversion.

---

## Inputs Required

- **Brand name** — exact name as it appears publicly (e.g., "Hey Sunday", "PrimePutt")
- **Domain** — root domain (e.g., heysunday.com)
- **PortCo knowledge file** — for competitor context and brand positioning
- **Any known issues** (optional) — if the team already knows something problematic is showing up, note it before searching

---

## What to Search

Run the following searches and record what appears in the top 10 organic results, ads, knowledge panels, and SERP features for each:

1. **[Brand name]** — exact brand name, no modifiers
2. **[Brand name] reviews** — the most important modifier; what are third parties saying?
3. **[Brand name] vs [top competitor]** — comparison intent; is a competitor running ads here?
4. **[Brand name] discount / coupon** — commercial intent; are affiliate sites capturing these searches?
5. **Is [brand name] legit / worth it / any good** — skeptic intent; what do undecided buyers find?

For each search, note:
- Position 1–10 organic results: domain and content type
- Ad slots: is the brand running its own ads? Are competitors running ads?
- SERP features: knowledge panel, People Also Ask, review stars, shopping results, image pack
- Sentiment signals: are results positive, neutral, or negative?

---

## Step 1: Audit the Core Branded SERP

Search: **[Brand name]**

**What should be there:**
- P1: Brand's own website (homepage or most relevant landing page)
- P2–3: Brand's social profiles (Instagram, TikTok, LinkedIn depending on brand)
- P4–10: Mix of press mentions, editorial reviews, TPV (if mature), retailer listings

**Red flags:**
- Brand's own site is not P1 — rare but happens on very new domains or with exact-match competitor domains
- Negative press, Reddit complaints, or BBB complaints in the top 10
- Competitor sites appearing in top 10 for the brand name
- No knowledge panel for a brand that's been live for 12+ months

**Opportunities:**
- Knowledge panel exists but is incomplete — flag missing description, images, or social links
- Social profiles not ranking — flag which profiles exist and whether they're optimized
- TPV (thelaundryguru.net, tourgrade.golf) could appear here — note if it does

---

## Step 2: Audit the Reviews SERP

Search: **[Brand name] reviews**

This is the most commercially important branded modifier. High-intent buyers who are close to purchasing often run this search.

**What to check:**
- Are reviews predominantly positive, mixed, or negative?
- Which third-party sites are ranking? (Trustpilot, Reddit, YouTube, niche editorial sites)
- Does the brand appear in any "best of" roundups in this SERP?
- Is the TPV appearing here for relevant PortCos?
- Are there any review sites flagging significant product complaints?

**Red flags:**
- Reddit threads with negative sentiment in top 5
- Trustpilot rating below 3.5 stars appearing prominently
- Consumer complaint sites (ConsumerAffairs, BBB with low rating) in top 10
- YouTube reviews with negative framing in titles

**Opportunities:**
- Positive review sites that could be amplified via outreach
- Missing Trustpilot / Google Business profile setup
- Strong editorial reviews that could be promoted

---

## Step 3: Audit the Comparison SERP

Search: **[Brand name] vs [top competitor]**

**What to check:**
- Who owns this SERP — the brand, the competitor, or a third party?
- Is the brand running ads on this query?
- Is the competitor running ads here (bidding on the brand name)?
- What does the editorial content say — does it favor the brand?

**Red flags:**
- Competitor running ads on the brand's comparison query without brand running its own
- Third-party comparison content that favors the competitor
- No brand-owned content targeting this query

**Opportunities:**
- Brand could publish its own comparison page (e.g., "Hey Sunday vs. Earth Breeze") to control the narrative
- If the TPV ranks here, it can function as the brand's editorial voice

---

## Step 4: Audit the Discount / Coupon SERP

Search: **[Brand name] discount** or **[Brand name] coupon**

**What to check:**
- Which affiliate sites are capturing this traffic?
- Are coupon sites (RetailMeNot, Honey, Groupon) top-ranking?
- Is the brand's own site anywhere in results?

**Context:** Affiliate coupon traffic is typically low-margin but high-intent. It's not necessarily a problem — but if the brand has a strong loyalty program or first-party offer, it may be worth owning this SERP with a dedicated landing page.

---

## Step 5: Audit the Skeptic SERP

Search: **Is [brand name] legit** or **[brand name] worth it**

**What to check:**
- What does a skeptical first-time buyer find?
- Is there Reddit content? What is the sentiment?
- Are there news articles, complaints, or positive editorial reviews?

**Red flags:**
- Reddit threads with high engagement expressing product complaints
- News articles flagging recalls, deceptive practices, or controversies
- No positive content addressing common objections

---

## Step 6: Pull Branded Keyword Data from Ahrefs

Pull organic keyword data filtered to branded terms:

```
Ahrefs: site-explorer-organic-keywords
target: [brand domain]
where: keyword contains [brand name]
```

This shows:
- Which branded terms are driving the most impressions and clicks
- Average position for the core brand name keyword
- Which branded modifiers have the most search volume (reviews, discount, vs. [competitor], etc.)

Cross-reference with GSC branded search data if available — GSC is more accurate for branded click and impression volume.

---

## Output Format

---

**Branded SERP Audit — [Brand Name]**
*Audited: [date]*

**Overall Assessment:** [🟢 Healthy / 🟡 Some issues / 🔴 Needs attention]
[2–3 sentences on the overall branded SERP picture]

---

**Core Branded SERP — "[brand name]"**

| Position | Domain | Content Type | Sentiment | Notes |
|----------|--------|-------------|-----------|-------|
| P1 | heysunday.com | Homepage | — | ✅ Brand owns |
| P2 | instagram.com/heysunday | Social profile | — | ✅ |
| P3 | [domain] | [type] | [+/neutral/-] | [note] |
| ... | | | | |

SERP features present: [Knowledge panel / People Also Ask / Review stars / Shopping / Image pack]
Ads: [Brand running own ad? / Competitor running ads?]

---

**Reviews SERP — "[brand name] reviews"**

| Position | Domain | Rating/Sentiment | Risk/Opportunity |
|----------|--------|-----------------|-----------------|
| P1 | [domain] | [positive/negative/mixed] | [note] |
| ... | | | |

---

**Comparison SERP — "[brand name] vs [competitor]"**
[Who owns it, ad activity, content sentiment — 3–4 sentences]

**Discount/Coupon SERP — "[brand name] discount"**
[Which affiliates rank, whether brand has own presence — 2–3 sentences]

**Skeptic SERP — "is [brand name] legit/worth it"**
[What skeptical buyers find, Reddit sentiment, key risks — 2–3 sentences]

---

**🔴 Risks — Act Now**
[Any negative content, competitor encroachment, or significant brand reputation issues]

**🟡 Opportunities — Address Soon**
[Missing knowledge panel info, unowned comparison queries, positive reviews to amplify]

**🔵 Monitor**
[Items to track over time but not urgent]

---

**Recommended Actions**
1. [Specific action — owner, deadline]
2. [Specific action]
3. [Monitor item]

---

## Judgment Guidelines

- **P1 for the core branded term is non-negotiable.** If the brand's own site isn't ranking P1 for its own name, escalate immediately — something is technically wrong.
- **Reddit is the highest-risk third-party surface.** Reddit threads rank well for branded queries and are high-trust for skeptical buyers. A negative Reddit thread in the top 5 for "[brand] reviews" is a meaningful conversion risk.
- **Competitor ads on branded terms are common and not always worth fighting.** Note them, but don't escalate unless they're dominant or the brand has no own ad running.
- **Knowledge panels are earned, not controlled directly.** If one is missing for a brand that's been live 12+ months with press coverage, it suggests insufficient brand entity signals. Flag for entity building work (Wikipedia, Wikidata, press mentions, structured data on site).
- **Branded SERP health correlates with halo effect strength.** A brand with a clean, positive branded SERP converts more of the traffic that organic and TPV work drives to it. This is worth including in the halo effect framing when reporting.
- **The TPV can appear in branded SERPs and that's fine.** If thelaundryguru.net appears in the P3–P8 range for "Hey Sunday," that's additional real estate for a trusted voice. Don't flag it as a problem.

---

## Example Trigger Phrases

- "Audit the branded SERP for Hey Sunday"
- "What shows up when you Google PrimePutt?"
- "Do we own our branded search for Hello Pest?"
- "Something negative is showing up when you search [brand name]"
- "Check if [competitor] is running ads on our brand terms"
- "What does a new customer find when they Google [brand]?"
- "Run a branded SERP check for [brand] before we launch"
