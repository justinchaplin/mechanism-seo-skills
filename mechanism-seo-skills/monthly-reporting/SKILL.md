---
name: monthly-reporting
description: Produces a clear, business-impact-framed monthly organic update for a Mechanism portfolio company — written for a CEO, not an SEO. Use this skill whenever someone asks to write or produce a monthly report, send a monthly update, summarize organic performance for the month, or communicate what the team did and what moved. Also trigger when someone says things like "write the monthly report for [brand]", "draft the monthly update for [brand]", "what do we send to [brand] this month", or "summarize what we did for [brand] in [month]". Always use this skill rather than writing a generic update.
compatibility: "Requires PortCo knowledge file (for conversion event, source of truth, reporting contact, and stakeholder context). Requires performance data from GSC, GA4/Shopify, and Ahrefs for the reporting period."
---

# Monthly Reporting

This skill produces the monthly organic update for a Mechanism PortCo. It is written for a CEO or business owner — not an SEO. It leads with business impact, acknowledges the halo effect, and communicates what was done, what moved, and what's next.

A good monthly report does three things:
1. Builds confidence that the team is working on the right things
2. Connects organic work to business outcomes (even when attribution is incomplete)
3. Sets realistic expectations for what's coming next

A bad monthly report lists activities and rankings without connecting them to anything the PortCo leadership actually cares about.

---

## Inputs Required

Before starting, read the PortCo knowledge file and confirm:
- **Source of truth** — GA4, Shopify, or Triple Whale
- **Primary conversion event** — what counts as a conversion for this PortCo
- **Reporting contact** — who receives this update
- **Stakeholder context** — how SEO-literate is this audience? Are they paid-media focused?
- **Report format** — Slack message, email, or doc
- **Performance data** — run the Performance Monitoring Dashboard skill first if not already done

If the PortCo knowledge file is missing any of these, flag before drafting.

---

## How Mechanism Writes Monthly Reports

**Lead with the business, not the tactics.** The first thing the PortCo contact reads should answer: "is organic contributing to our growth?" Rankings, links, and impressions are supporting evidence — not the headline.

**Always frame the halo effect.** Organic conversions will almost always understate the full impact of the team's work. Every report should include a sentence acknowledging that organic influences paid conversion rates, direct traffic, and branded search — even when it can't be directly attributed.

**Communicate challenges honestly.** If something didn't move, say so and explain why. Hiding bad news erodes trust faster than the bad news itself.

**Three actions forward.** Every report ends with what the team is focused on next month. Not a laundry list — three specific things that connect to the PortCo's goals.

**Match the audience.** A paid-media-focused CEO needs different framing than an SEO-literate one. The PortCo knowledge file's stakeholder context field informs this. When in doubt, write simpler and more business-focused.

---

## Workflow

### Step 1: Pull Performance Data

If the Performance Monitoring Dashboard skill hasn't been run for this period, run it first. The monthly report is a communication layer on top of the data — not a data gathering exercise.

Key numbers needed:
- GSC non-branded clicks and impressions vs. prior period
- GSC branded clicks vs. prior period
- Organic sessions, conversions, and revenue (GA4/Shopify)
- DR and referring domain count vs. prior period
- Money keyword position changes
- New link placements secured this month

---

### Step 2: Identify the Three Headlines

Before writing, identify the three most important things that happened organically this month:

1. **The win** — what moved in a positive direction? A ranking improvement, a strong link placement, organic revenue up, branded search growing?
2. **The work** — what invisible work drove or will drive future results? Outreach volume, content published, campaigns launched?
3. **The honest status** — is the engagement on track? What's the most important thing to communicate about where things stand?

These three things structure the report. Don't write until you know what they are.

---

### Step 3: Draft the Report

**For Slack/short format:**

```
[Brand] Organic Update — [Month]

📈 [One headline win — business-focused]
[2–3 sentences expanding on the win with context]

🔗 [Link building summary]
[What was built, any notable placements, outreach volume]

📊 [Performance snapshot]
[Key numbers — clicks, rankings, conversions — 2–3 stats max]

🔮 [What's next]
[3 specific focus areas for next month]

Note: [Halo effect acknowledgment if relevant — e.g. "Organic influence on paid and direct conversions isn't captured above — branded search is up X% which signals growing brand awareness beyond what organic attribution shows."]
```

**For email/doc format:**

Follow the same structure but expand each section with more context. Include the full performance table from the Performance Monitoring Dashboard output. Add a section on challenges if anything needs to be surfaced.

---

## Output Format

Produce the report in the format specified in the PortCo knowledge file (Slack, email, or doc). Default to Slack format unless specified otherwise.

The report must include:

**Subject/Header:** [Brand] Organic Update — [Month Year]

**Opening headline:** One sentence that answers "is organic moving the needle?" — written for a business owner, not an SEO

**Performance summary:** 3–5 key metrics with context (not just numbers — what they mean)

**What we did:** The most important work completed this month — link placements, content published, campaigns run. Focus on the work that will compound, not task lists.

**What moved:** Rankings, traffic, conversions — what changed and why

**Challenges:** Anything not moving as expected, with honest framing (not buried)

**Halo effect note:** Standard acknowledgment that organic attribution understates total impact — customize based on whether branded search or paid conversion rate data is available to support it

**What's next:** Three specific focus areas for next month

---

## Tone Guidelines

**For paid-media-focused CEOs:**
Lead with revenue and conversion language. Connect every organic metric to dollars where possible. Minimize SEO jargon. The halo effect framing is especially important here — connect organic visibility to paid media performance explicitly.

**For SEO-literate audiences:**
Can go deeper on ranking data and link building strategy. Still lead with business impact but can include more tactical detail.

**For skeptical stakeholders:**
Be especially direct about what moved and what didn't. Don't bury challenges. Over-communicate on the halo effect — this audience needs to understand why organic attribution understates impact.

**Always avoid:**
- Vanity metrics without context ("we got 47 new backlinks!" — so what?)
- Jargon without explanation (DR, CTR, impressions — explain or reframe)
- Activity without outcome ("we sent 200 outreach emails" — what did it result in?)
- Overpromising on timelines

---

## Judgment Guidelines

- **If it was a bad month, say so clearly and explain why.** Algorithm update, thin content, slow link velocity — be specific. Then explain what's being done about it.
- **Branded search growth is an underused proof point.** If branded GSC clicks are up without a paid brand campaign, that's organic-driven brand awareness. Name it explicitly — it connects organic to business outcomes even when conversion attribution is thin.
- **Link placements are worth calling out specifically if they're high-value.** "We secured a mention in a Breaking80 article that ranks P1 for 'best putting mat'" is more meaningful than "we added 3 referring domains."
- **Don't report on what you were supposed to do — report on what you did.** Activity logs belong in internal docs, not client updates.
- **Match the length to the relationship stage.** Early engagements need more context and education. Mature engagements can be more concise — the PortCo already understands the model.

---

## Example Trigger Phrases

- "Write the monthly report for Hey Sunday"
- "Draft the March update for PrimePutt"
- "What do we send to Learner this month?"
- "Summarize what we did for Hello Pest in February"
- "Write up the organic update for [brand]"
- "It's end of month — put together the [brand] report"
