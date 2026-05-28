# Value hypothesis evaluation

A template for pressure-testing a value hypothesis *before you build anything*. The point is intellectual honesty: is the idea conceptually sound, is it targeting real desperation, is the MVP truly minimal, does the business model make sense, is there an inflection point, is the leap of faith explicit?

Use this when you have a value hypothesis written down (or being argued internally) and you want to stress-test the *structure* of the bet, not the founder or the execution. The goal is not to be right. It is to be wrong as quickly and cheaply as possible, in a way that teaches you where to pivot.

Built on the value-hypothesis discipline in [`../decision-making/value-hypothesis.md`](../decision-making/value-hypothesis.md) and the posture in [`../decision-making/finding-pmf.md`](../decision-making/finding-pmf.md). Synthesized from Rachleff, Ries, Blank, Moore, Christensen, Fitzpatrick, and Duke (*Thinking in Bets*).

---

## How to use

1. Write the value hypothesis on one line: *"For [specific desperate who], we will build [specific what] grounded in [specific insight], monetized via [specific how]."*
2. Write the leap of faith on its own line: *"The one belief that, if false, kills the business is [the leap]."*
3. Walk through every question below. If a question can't be answered, that is the hole.
4. After the walk-through, name the **three load-bearing weaknesses** (the questions where the hypothesis is weakest). Those are what to sharpen before designing the MVP.
5. Re-run after each pivot. The hypothesis evolves; the questions don't.

A worked example using a job-search-tool scenario follows the question set.

---

## Questions for the *what*

The product and the insight underneath it.

1. **Is there a unique insight?** Something you know or believe that the market does not yet agree with. If the insight is consensus, you are pursuing right-and-consensus and the expected return is small.
2. **What is the inflection point?** What technology, behavior, or regulatory change just made this newly possible? If "nothing changed," the insight is suspect.
3. **What is the leap of faith?** *One* assumption, on its own line. Not two or three. Multiple leap-of-faith assumptions complicate testing and dilute focus.
4. **Is the leap of faith non-consensus?** If everyone agrees immediately, the bet is probably incremental. Non-consensus does not mean right; it means there is room for asymmetric return if it is right.
5. **Is the MVP the absolute smallest feature set that tests the leap of faith?** Not just "minimal." *Most* minimal. If the MVP has multiple primary benefits, it is too complex. One primary benefit. One core use case. One clear test.
6. **Is there more than one primary benefit?** If yes, red flag. Hedging on benefits is the most common founder mistake. Pick one. The benefits you cut can come back post-PMF.
7. **Is the MVP enough to delight?** Sounds contradictory. It is not. The feature set must be minimal *and* sufficient to make an early adopter say "this is exactly what I needed." Minimum *and* sellable.
8. **Is it feasible to build?** A strong insight often makes others say "you can't build that" while you know you can. Worth naming.
9. **Can you get to market fast? Do you need partners to ship the MVP?** Sooner you ship, sooner you learn. Pre-existing services (LLM APIs, payment infra, hosted databases) buy speed.
10. **Can it be copied easily?** Worth noting, but matters less than initial insight. **First to PMF wins, not first to market.**

## Questions for the *who*

The desperate target audience.

1. **Have you defined a desperate target audience?** Not "people who would benefit." Desperate. Behavioral evidence: they have spent money trying to build the thing themselves, hired consultants, paid for inferior substitutes, reach across the table when you show them the product.
2. **Are they currently served?** If they are, by what? If a good-enough alternative exists, they are unlikely to be truly desperate for yours.
3. **Why are they not currently served?** Most founders skip this. If the problem is real and has existed, why hasn't anyone solved it? The answer should tie to your inflection point.
4. **Are they able to pay?** Different from willing to pay. Students with no income are not a good initial market because they cannot pay. In B2B, the user and the check-writer might be different people; if so, name both.
5. **Will they pay without references, just with a proof of concept?** Tests whether your audience behaves like early adopters. Pragmatists need references; early adopters need only proof of concept. If your target needs references, you are targeting the wrong segment of the curve.
6. **Have they tried to build it themselves?** Strongest single signal of desperation. **Nuance:** if they have *both* tried to build it themselves *and* already have a line-item budget for it, the problem is consensus and a competitor is already on it.
7. **Have you defined the market as narrowly as possible?** Most violated question. There is almost always a way to segment more narrowly. Combine dimensions: job to be done + demographics + function + geography + company stage. The narrower you go, the fewer features you need, the easier it is to dominate, the faster you learn.
8. **Is the market self-referencing?** A market is a group of customers who reference each other. If your segment does not talk to each other and would not trust each other's recommendations, you do not have a market; you have scattered buyers.
9. **Is the audience targetable?** A perfect segment with no list, no community, no channel, no way to find them is academic. You need to be able to identify and contact the people in your segment.
10. **Is there a realistic path to adjacent markets?** You don't need to know what they are or size them. You just need to believe they plausibly exist. Don't calculate TAM for unproven adjacencies; that is a leap of faith requiring data you don't have.
11. **Is the market likely to contain early adopters?** Counter-intuitively, high-margin industries (financial services, pharma, tech) are often the first to adopt new solutions. Low-margin industries that need innovation most tend to be the most resistant.
12. **How easy is it to dominate?** The sooner you dominate, the sooner word of mouth spreads. *Perceived* dominance is enough.

## Questions for the *how*

The business model.

1. **How are you charging?** Should be explicit, not vague.
2. **Does the way you charge reinforce the value you deliver?** Pay-per-use, outcome-based pricing, bundled subscriptions can all reinforce the customer's perception that they are getting a good deal. Distracting fee structures do the opposite.
3. **Does it delight the customer?** Some business models generate delight independent of the product (Amazon Prime, Whoop, in-game purchases). Both product delight and model delight compound.
4. **Is the pricing model as simple as possible?** Just as you want the narrowest audience and the smallest feature set, you want the simplest pricing model. Complicated pricing introduces variables that make tests harder to read.
5. **Could the unit economics plausibly work?** Don't need precision; need coherence. Could you be economic at scale? If there is no visible pathway to positive unit economics, why bother?
6. **Does it create an innovator's dilemma?** Nice-to-have, not required. If you can structure the model so the incumbent's response would damage their existing economics, you have an asymmetric competitive advantage.
7. **Can the product sell itself organically?** At this stage, no growth hypothesis. The product should generate word of mouth through delight. If your model requires a distribution partner or paid acquisition to get any traction at all, that is a complication that slows the rate of learning.
8. **Have you avoided incorporating growth?** A value hypothesis should not include growth strategy. Validate value first. Growth comes after.

## Sanity questions across all three

1. **Is the leap of faith testable?** Can you design an experiment that will tell you whether the leap is right or wrong, fast and cheap? If no, the hypothesis is intellectually interesting but not actionable.
2. **The three most common mistakes** (Rachleff). Run the checklist:
   - **Feature set too large.** Multiple benefits, multiple use cases. *Hedging is the enemy of the entrepreneur.* Commit to one primary benefit.
   - **Market defined too broadly.** "People who want X" is not a targetable audience. If you cannot name and reach the people, you have not narrowed enough.
   - **Need mistaken for desperation.** Many markets need solutions. Few are desperate. If you cannot find behavioral evidence of desperation, you have not found your audience yet.
3. **Have you avoided the trap of starting with the market?** Starting with a market and looking for a problem is right-and-consensus. Starting with an insight and looking for a market is the path to non-consensus returns.
4. **Have you accepted that you will be wrong?** Almost every first hypothesis is wrong. The purpose of the evaluation is not to be right today; it is to identify the cheapest experiment that would tell you you're wrong tomorrow.

---

## Worked example

A value hypothesis evaluation for a hypothetical product. The scenario: an AI-driven job-search assistant that matches a candidate's CV against open roles at frontier AI companies and surfaces the highest-scoring matches daily. Target audience: MBAs targeting AI PM roles.

### The hypothesis

*For job-seeking MBAs targeting AI PM roles at frontier AI companies, we will build an AI-scored daily-matching service that reads a CV and 100+ AI-company ATS feeds and surfaces the 5 best-fit roles each morning, grounded in the insight that LLMs are now cheap and accurate enough to do explainable CV-to-role matching at $0.10/match (vs $5k+ for a search-firm consultant), monetized via a $30/month subscription paid by the candidate.*

**Leap of faith:** Job-seeking MBAs at top-10 programs will trust and pay for AI-scored matches over the existing pattern of personal Notion sheets, LinkedIn Job Alerts, and recruiter outreach, **at $30/month**, once they have seen one credible daily list.

### What — verdict and questions

**1. Unique insight: yes, partial.** LLM-driven CV-to-job matching at production cost is recent (last 18 months). The insight is *narrow scoring quality at low cost*. Job matching itself is consensus (LinkedIn, Indeed, Wellfound). Differentiation comes from the cost + explainability inflection on a narrow segment, not from being the only one matching CVs to jobs.

**2. Inflection point: clear.** Cost of structured LLM inference fell ~10x in the last 18 months. Multi-step CV-to-role scoring at $0.10/match (50 matches/week = $2/week per user) was uneconomic before. Now it works.

**3. Leap of faith: clean.** One assumption, on its own line. Testable.

**4. Non-consensus: partial.** *Job matching tools exist* is consensus. *MBAs targeting AI PM will pay for AI-scored matches* is non-consensus enough to be interesting (everyone assumes job-seekers won't pay for what they think is free on LinkedIn).

**5. MVP minimality: medium concern.** The candidate MVP includes (a) daily matching, (b) interview prep generation, (c) per-company review docs. That is three primary benefits. **Hedging.** Need to narrow to one. The daily list is the primary; interview prep and company review come post-PMF.

**6. More than one primary benefit: yes.** See above. Cut to one.

**7. MVP enough to delight: probably.** A daily email with five tightly-matched roles, each with a one-paragraph "why this fits" written by the LLM, is delight-shaped. The aha is the first email where two of the five are roles the candidate hadn't found on their own.

**8. Feasibility: high.** LLM APIs + ATS feed connectors + email = a weekend MVP. The technical risk is low; the value risk is whether MBAs will pay for it.

**9. Speed to market: fast.** Days, not months. No partners required for v0.

**10. Easy to copy: yes.** Anyone can wire LLM + ATS scraping. Moat comes from (a) calibration on real successful job searches, (b) niche depth on AI PM roles specifically, (c) being first to the segment. **Copyability is a real concern post-PMF, less of one pre-PMF.**

### Who — verdict and questions

**1. Desperate target audience: behavioral evidence is mixed.** MBAs at top programs targeting AI PM are *interested* and *active* but the desperation signal needs verification. Some evidence: many maintain personal Notion sheets, several pay $5-10k for search-firm consultants, many spend 4-6 hours/week reading job boards manually. The behavioral cost is high; the willingness to pay $30/month for software is unverified.

**2. Currently served: partially.** LinkedIn Jobs is generic and noisy. Wellfound is narrower but not AI-PM-focused. No service today targets *AI PM roles specifically*, scored for fit, delivered daily.

**3. Why not currently served:** (a) The LLM-scoring cost inflection is recent. (b) The AI PM segment is small but growing. (c) Existing job-search tools are advertising-funded by employers, which biases them toward volume over fit.

**4. Able to pay: yes.** MBAs at top programs can absorb $30/month against the expected payoff of a $200k+ first-year salary.

**5. Pay without references: probably yes** at $30/month if the first daily list is credibly good. Higher prices would need references.

**6. Have they tried to build it themselves: yes, repeatedly.** Personal Notion sheets, custom scripts, shared spreadsheets across cohorts. **Strong desperation signal**, but also a sign that the bar for "better than DIY" is real.

**7. Defined as narrowly as possible: not yet.** Current definition: "MBAs targeting AI PM at frontier AI companies." Narrower would be: *Class of 2026 and 2027 MBA students at top-10 programs, currently in a focused AI PM search, with a target list that includes Anthropic, OpenAI, Sierra, Adept, or comparable.* Could go even narrower (one school, one class year). The narrower lead pin is more honest about who the actual early adopter is.

**8. Self-referencing market: yes.** MBA cohorts at top programs are deeply self-referencing through class WhatsApps, AI-PM Slack groups, alumni networks.

**9. Targetable: yes.** Direct outreach via class lists, AI-PM Slack communities, on-campus career events.

**10. Adjacent markets: plausible.** Mid-career PMs at non-AI tech companies wanting to move into AI. Engineers transitioning to PM. Senior individual contributors at FAANG looking at AI startups. Each requires its own beachhead but the technology is reusable.

**11. Early adopters likely: high.** MBAs and AI-curious tech workers are early adopters by definition.

**12. Easy to dominate: yes for the narrow segment.** A cohort of ~50-100 MBAs at one school, one class year, can be dominated by manual outreach plus a few visible "I got my offer through this" testimonials.

### How — verdict and questions

**1. How charging: $30/month subscription, paid by the candidate.** Explicit.

**2. Charging reinforces value: yes.** Monthly subscription matches the daily delivery cadence. Pay-per-match would distort behavior (users would game scoring).

**3. Delights customer: model itself is neutral.** Subscription is normal. Could add a "money-back if you don't get an interview in 60 days" guarantee, which would reinforce value. Worth testing later.

**4. Pricing model as simple as possible: yes.** One tier. No add-ons. No annual discount until post-PMF.

**5. Unit economics: viable.** Cost per user: 50 matches/week × $0.10 = $5/week = $20/month variable cost. Price: $30/month. Gross margin: ~33%. Thin at first. Improves with scale on inference cost. Acceptable for pre-PMF.

**6. Innovator's dilemma: partial.** LinkedIn could build this but would cannibalize their employer-paid job-listing revenue (a high-margin product for them). Indeed similar. The dilemma is real but not strong; both could absorb the cannibalization if they had to.

**7. Sells organically: should.** If a candidate gets an offer through the service, they have a *story* to tell their cohort. The cohort is self-referencing. Word of mouth should compound if the matching quality is real.

**8. Avoided incorporating growth: yes.** No referral mechanics, no paid acquisition, no SEO play. Pure value hypothesis.

### Sanity check

**Testable: yes.** Define the leap of faith as: *Of the first 10 MBAs at one named school in the AI PM search, will at least 5 of them pay $30/month after seeing two daily lists, and will at least 2 of them forward the email to a classmate within two weeks?*

If 5+ pay and 2+ forward, the leap is alive. If only 2-3 pay or zero forward, the leap is falsified and the next move is to apply the five-whys.

**Three common mistakes — applied:**

- **Feature set too large: yes.** Cut interview prep and company review docs. Daily matching only.
- **Market too broadly defined: yes.** Narrow to one school, one class year, one role type for the lead pin. Expand after.
- **Need vs. desperation: medium.** The behavioral evidence is real (Notion sheets, paid consultants) but the willingness to pay $30/month for *software* specifically is unverified. Worth a smaller test (concierge MVP) before committing to product build.

### Three load-bearing weaknesses to sharpen

1. **Cut the MVP from three features to one.** Daily matching only. Interview prep and company review docs are post-PMF features that, if shipped now, dilute the test.
2. **Narrow the lead pin further.** From "MBAs targeting AI PM" to *one school, one class year, one role type*. The current definition is two layers too wide.
3. **Validate willingness to pay $30/month before building.** A landing page + Stripe checkout with a 7-day money-back guarantee, shown to 20 MBAs at the target school, would tell you within a week whether the leap is alive. Behavioral signal beats interview signal.

### Next move

Run a one-week concept test: landing page with the offer ($30/month, daily list of 5 AI PM roles, money-back in 7 days), distributed to one school's Class of 2026 AI-PM cohort (estimated 30-50 people). Conversion >20% paid signups in week one keeps the hypothesis alive. Below 5%, run the five-whys to identify which assumption broke (price, segment, framing, channel, trust).

If the concept test passes, build the MVP for the same cohort. Daily list, manually curated for the first 5-10 users. Concierge approach. Automate after you see whether two of the first five candidates would tell their friends without being asked.

The interview-prep and company-review features wait until at least 10 candidates have used the matching for 30+ days and the word-of-mouth signal is visible.
