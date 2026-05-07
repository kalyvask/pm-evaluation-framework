# Value hypothesis

Before you measure PMF, you need a hypothesis about *why* PMF would happen. Most teams skip this. They have a product, they have users, they have metrics — and no explicit statement of what they're betting on. So when growth stalls, they don't know which assumption broke.

This file is about writing the bet down before you make it. Distilled from Andy Rachleff (Wealthfront, Benchmark), Eric Ries (*The Lean Startup*), Steve Blank (*Four Steps to the Epiphany*), Geoffrey Moore (*Crossing the Chasm*), and Clay Christensen on disruption.

---

## What a value hypothesis is

Andy Rachleff's framing: every value hypothesis decomposes into three pieces.

> **What** — the specific product, grounded in a non-consensus insight (usually a technology inflection).
> **Who** — the customer who is *desperate* for it, not just interested.
> **How** — the business model: how you charge, how you distribute, how you make money in a way that enhances product value.

You should be able to write your value hypothesis on one line. *"For [specific desperate who], we will build [specific what] based on [specific insight], monetized via [specific how]."*

If any of the four blanks is generic ("for SMBs," "via subscription"), the hypothesis isn't ready to test. Sharpen it before you run the experiment.

---

## The "what": insight before product

Most product books tell you to start with a market and find a problem. Rachleff's argument — and the empirical record of successful tech companies — is that this produces "right and consensus" outcomes: low returns, because anyone can do it.

The asymmetric returns come from **right and non-consensus**. That means starting from a specific insight — typically a technology inflection that just made something newly possible — and then searching for the market that's desperate for what the insight enables.

Examples:
- *"LLMs can now write production code from natural language"* → search for the market that's desperate for this (it took a few years to find).
- *"Smartphones plus GPS make on-demand car dispatch possible"* → Uber found the market.
- *"Software can manage investments without human advisors at near-zero marginal cost"* → Wealthfront's insight; the desperate market turned out to be young engineers, not high-net-worth individuals.

Rule of thumb: *change creates opportunity.* Without an inflection, "good enough" usually wins, and your "10× better" product can't displace the incumbent. Andy Rachleff's stronger version: *in tech, it's almost impossible to win from behind through better execution.*

The thing to be skeptical of: a "what" with no inflection underneath it. *"We're building a better project management tool"* is a feature, not a hypothesis. *"We're building project management on top of [thing that just became possible]"* is a hypothesis.

---

## The "who": desperation, not need

The most counterintuitive part of the framework. Many products solve real problems for real users — and still fail because the users aren't *desperate*.

Need ≠ desperation. Desperation looks like:
- Customers reach across the table to grab the product from your hands
- They pay before the product is finished
- They've already cobbled together a manual workaround (spreadsheets, scripts, hiring an intern, sticky notes)
- They get visibly emotional about the problem — *"this is the worst part of my job"* not *"yeah, that'd be nice"*

Steve Blank's term for the desperate buyer is **earlyvangelist**. They have the problem, know they have the problem, have budget to solve it, and have already tried to solve it. (See `decision-making/customer-interviews.md`.)

### Geoffrey Moore's adoption curve

Picking the right "who" means picking the right segment of the curve:

| Segment | Buying behavior | Use them for? |
|---|---|---|
| **Innovators** | Buy for the joy of trying new things | Skip — they don't influence others |
| **Early adopters (visionaries)** | Want breakthroughs, don't need references, satisfied by proof of concept | **Your first market.** This is where PMF is found. |
| **Early majority (pragmatists)** | Want productivity, demand references, need a "whole product" | Cross to here *after* PMF, not before |
| **Late majority (conservatives)** | Buy only when it's the standard | Years later |
| **Laggards** | Never buy | Ignore |

The chasm sits between early adopters and pragmatists. Most failed products tried to skip the early-adopter beachhead and sell directly to the pragmatic majority — who don't buy unproven things. Don't.

### The bowling-pin strategy

You want the biggest possible market eventually. You don't get there by aiming at it directly.

Pick a **lead pin** — a narrow segment that is:
1. Desperate (not just interested)
2. Adjacent to other markets you could expand into later
3. Small enough that you can dominate it with a focused MVP

Win the lead pin. Adjacent markets reveal themselves through customer requests — not through your strategic deck. Each new pin requires going back to early adopters and rebuilding the whole product for them.

Rule of thumb from Rachleff: *your initial market doesn't have to be the most desperate, but it must be desperate. Need is irrelevant.*

A useful test: can you name your lead pin in fewer than 15 words, including the segmenting axes (vertical, role, company size, geography, life situation, JTBD)? If the answer is *"SMBs in North America,"* you haven't picked a lead pin. You've picked a TAM slide.

---

## The "how": business model as an unfair advantage

The how is not a footnote. The right business model can compound the value of the product; the wrong one can kill it even if the product is good.

Three rough internet business models: **advertising, subscription, transaction fees.** Pick one (or a hybrid) deliberately, not by default.

Two strong heuristics:

1. **If you're not advertising-based, charge from day one.** If a customer won't pay for the MVP, they won't pay for the polished version either. Free MVPs don't validate anything except "people will accept free stuff."

2. **Use a disruptive model when you can.** Clay Christensen's definition of disruption is precise:
   - **Simpler, cheaper, more convenient** (not "better" — that's a sustaining innovation).
   - Either serves *non-consumers* (new-market disruption — Airbnb, Quicken) or *the over-served* (low-end disruption — Dell).
   - Creates an **innovator's dilemma** for the incumbent: it's *uneconomic* for them to compete.
   - Tesla is **not** disruptive by this definition: it's not cheaper, not simpler, and the incumbents could compete if they chose to.

   If you're designing the model from scratch anyway, why not make it disruptive? It's an asymmetric competitive moat.

The thing to watch: founders often pick a business model based on what's familiar (their last company, what investors want to see) instead of what enhances the product. Google's inline ads enhanced search. Facebook's early display ads distracted from the feed. Same revenue model, opposite product effect.

---

## Validation sequence: problem → implementation → product

Andy Rachleff's ordering, refined from Lean Startup:

### 1. Validate the problem (the who)

You're testing whether the segment you picked is actually desperate. Use customer interviews — see `decision-making/customer-interviews.md` for technique.

The questions are about their life, not your idea:
- *Tell me about the last time you encountered this problem.*
- *What's the hardest part?*
- *How are you solving it today?*
- *What's the cost of not solving it?*
- *What budget have you allocated to it?*

If they're not desperate, **pivot the who, not the what.** Adding features doesn't make a customer more desperate. The bowling-pin moves to a different pin.

### 2. Validate the implementation

Once you have a desperate audience, test whether your specific solution is the one they'd hire. The best tool here is a **design sprint** (Knapp): a compressed week of prototyping and customer testing without committing to build.

Critical: **try to sell it, don't ask if they'd buy it.** Asking what customers want is market research and produces fluff. Trying to sell forces a real reaction.

Use the **five whys** when they object — but seek the objection, don't overcome it. The goal is to learn whether the audience is wrong, the implementation is wrong, or the price is wrong, so you can pivot to the right thing. Sales-tactics-style "overcoming objections" defeats the purpose.

### 3. Validate the product

Build the smallest MVP that lets a customer actually use and pay for the product. Eric Ries: *the minimum functionality required to prove the leap-of-faith assumption critical to the business.* Steve Blank: *the smallest feature set that gets a customer to pay.*

Counterintuitive rules from Rachleff:
- **Iterate on the who, not the what.** Adding features rarely creates desperation. Changing the audience often does.
- **It's appropriate to *reduce* scope, not add.** Too many benefits make the MVP harder to sell — buyers who only want one of the benefits will reject the product if there's a benefit they don't need.
- **Don't hedge.** "Hedging is the enemy of entrepreneurs." Pick one lead pin, one MVP, one bet at a time.

### Prototype types — "smallest" is not the same as "shippable"

The smallest test of a leap-of-faith assumption usually isn't a real product. A short menu of disposable validation artifacts, ordered roughly by build cost:

- **Smoke test / fake door.** A landing page or feature button that captures intent. No product behind it. Tests whether anyone wants the thing at all.
- **Painted door.** Looks like a working feature, but on click delivers a "coming soon" or a manual response. Tests intent at a higher fidelity.
- **Concierge MVP.** A human (often the founder) does the work behind the scenes, by hand, for a small number of named users. Tests whether the *outcome* is valuable, before automating delivery.
- **Wizard of Oz.** Looks fully automated to the user. Behind the curtain, humans (or scripts) do the work. Tests the experience of the automated version without paying to build the automation.
- **Single-feature MVP.** A real, working version of the smallest one feature. No supporting product around it.
- **Full thin slice.** End-to-end working product covering one job, narrow segment, narrow scope. Story-mapping language.

Picking the right one is mostly a question of *which leap of faith you're testing.* Testing intent? A smoke test is enough. Testing whether the outcome is worth paying for? A concierge MVP. Testing whether the automated experience is acceptable? Wizard of Oz. Testing whether the full motion (acquisition, activation, retention) holds together? A real thin-slice MVP.

The mistake is to skip straight to the thin-slice MVP for every test. Most early hypotheses can be falsified for a fraction of the cost with a smoke test or concierge round first.

---

## What "PMF achieved" actually means

You've validated the value hypothesis when:

- **Consumer:** exponential organic growth driven by word of mouth, plus retention. Word of mouth is the single most important signal — only delight produces virality.
- **B2B:** sales yield greater than 1, where sales yield = average gross margin per sales rep ÷ fully-loaded cost of fielding that rep. Yield > 1 typically grows quickly to > 2; that inflection point is the proof.

What does **not** prove PMF:
- Survey-based metrics (NPS, "would you be very disappointed?") — useful as directional, but **intent-based, not behavior-based.** People say nice things they don't act on.
- Free adoption — see `frameworks/03-pre-pmf-validation.md`.
- Strong NPS without a viable economic model — measuring user love and confusing it with viability.
- Vanity totals (DAU up, signups up) without segment-level retention.

Rule of thumb: *behavior-based metrics beat intent-based ones every time.* A user who keeps coming back beats a user who said they would.

---

## Pivot vs. restart

When the metrics say PMF isn't there, you change something. Two distinct moves:

- **Pivot** — change the who, the how, or messaging. Keep the insight.
- **Restart** — change the what (the underlying insight). This is starting over.

Restarts are mostly indistinguishable from new companies. They have a much higher probability of success than incremental pivots — but they also burn more time and capital. If you find yourself iterating on the what after every interview round, you don't have a hypothesis; you have a brainstorm.

The right pivot signal comes from the **five whys** during validation: where exactly is the desperation breaking down? That tells you what to change.

---

## Pre-launch checklist

Before pouring growth dollars into a product, you should be able to answer these on one page:

1. **What's the insight?** What just changed (technology, behavior, regulation) that makes this newly possible? Is it right *and* non-consensus?
2. **Who's the lead pin?** Named segment with multiple axes of segmentation. Are they *desperate*, not just *needy*?
3. **What's the business model?** Specifically what you charge, who pays, why the model enhances rather than degrades the product. Why isn't it free?
4. **What's the leap-of-faith assumption?** The one belief that, if false, the whole thing falls apart.
5. **What's the smallest MVP that tests the leap of faith?** Not the smallest product. The smallest test of *the assumption*.
6. **What would falsify the hypothesis?** A specific metric, a specific threshold, a specific timeline. If you can't write the falsifying answer, you're not running an experiment.
7. **What's the kill criterion?** If validation fails, do you pivot the who or restart on the what? Pre-decide.

If you can't answer all seven — especially 4 through 7 — you don't have a value hypothesis. You have an idea you like.

---

## The inclusion vs. control tension

In many regulated and risk-sensitive categories — fintech, healthcare, education, insurance — there's a structural tension worth naming explicitly:

> The users who need the product most are often the hardest to underwrite, qualify, or serve safely. Tightening eligibility reduces risk and makes the unit economics work. It also excludes the strategically necessary segment.

This shows up as a fork between two paths, neither clean:

- **Tighten eligibility.** Loss rates fall, partner banks / regulators / insurers stay happy, the product scales. But the people you originally wanted to help are the ones being filtered out, and the brand promise drifts.
- **Keep eligibility broad.** The brand promise stays intact, the impact story stays real. But losses, complaints, regulatory exposure, or partner pushback eventually constrain growth.

Often there is no single design that solves both. The PM's job in these cases is **not to pretend there's a clean technical fix.** It's to surface the tension explicitly to leadership, with three things on the table: the segment that can be served sustainably, the segment that cannot, and the strategic cost of the choice. Leadership decides; the PM frames.

A useful re-statement when the tension shows up:

> The question is not *"is the product good?"* — it's *"is the product good for the subset of users we can sustainably serve, under what eligibility model, at what price, under what regulatory classification?"*

That re-framing converts a fuzzy "PMF unclear" debate into a specific set of choices, each with a different sustainable-segment definition.

---

## Common value-hypothesis failures

- **Right and consensus.** Solving an obvious problem with an obvious approach. Anyone can do it; nobody wins big.
- **Insight-free product.** No technology or behavioral inflection underneath. The "why now" question doesn't have a real answer.
- **Need confused with desperation.** The audience would benefit, but they're not actively suffering. They won't carry a product across the chasm.
- **Hedging on the who.** Three customer segments in parallel. None get the full attention; none reach desperation; the team can't iterate fast enough on any of them.
- **Iterating on the what.** Adding features instead of changing the audience. Each new feature obsoletes the original insight.
- **Free MVP as validation.** People will accept anything that's free. Free retention proves nothing about willingness to pay.
- **Skipping early adopters.** Selling to the pragmatic majority before crossing the chasm. They want references you don't have.
- **Conflating product risk and market risk.** Customer interviews don't validate product risk. If your idea is mostly product risk (deep tech, consumer media), interviews give you a starting point but you'll have to build to learn the rest.
