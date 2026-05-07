# Competitive moats and defensibility

Most PM artifacts mention "defensibility" once and move on. A real moat conversation forces you to name *which* moat, with *which* evidence, and *which* still-undefended flank a competitor would attack first.

This file is the working-PM reference for that conversation. Useful when writing a strategy memo, defending a roadmap to leadership, or stress-testing a "we'll be the leader because we're better" claim.

---

## What a moat is and isn't

A **moat** is a structural reason a competitor cannot copy your product into commodity. Quality, polish, and clever features are not moats — they're table stakes that any well-funded incumbent will catch up on. Moats are the things that *get harder for a competitor to overcome the longer you run.*

Two common misuses:

- **Aspirational moats.** *"We'll have network effects once we hit critical mass."* Every two-sided product says this. It's not a moat until users are visibly choosing you because the network is bigger; until then it's a hypothesis. Rate it *emerging*, not *strong*.
- **Brand confused with reputation.** A reputation for shipping good product is not a moat. Brand becomes a moat when users default to you without comparing alternatives — and that takes years and visible category leadership.

A useful test: *if a well-resourced competitor launches a 1.5× better version next quarter, how much of our user base do we lose in 12 months?* If the honest answer is "most," the moat isn't real.

---

## The eight moats

| Moat | What it looks like | Common failure mode |
|---|---|---|
| **Habit / behavioral lock-in** | Users have made the product part of their daily flow; switching means rebuilding muscle memory | Confusing high engagement (vitamin) with habit (painkiller in a daily ritual) |
| **Network effects** | The product gets better for each user as more users / counterparties join | Overstating one-sided usage as a network effect; ignoring local network density |
| **Switching costs** | Data lock-in, workflow integration, training investment, social ties | Mistaking *inconvenience* for switching cost; switching cost only counts if it changes user behavior |
| **Proprietary data advantage** | Datasets that compound with use and improve the product (recommendations, models, fraud detection) | Assuming generic public data is proprietary; assuming model quality is data quality |
| **Ecosystem / platform** | Multiple products reinforce each other; integrations make the bundle costlier to leave than any single piece | Calling a product suite an ecosystem before integrations are real |
| **Scale economics** | Unit costs fall structurally as volume grows; competitors can't match price without losing money | Confusing fixed-cost amortization with structural scale advantage |
| **Brand and trust** | Users default to you in a category where trust matters (financial, health, security) | Treating awareness as trust; trust requires demonstrated reliability over time |
| **Regulatory / IP** | Licenses, certifications, patents, or compliance moats that take competitors years to acquire | Patents that don't actually block the workaround; certifications that competitors can also obtain |

Most products have one *real* moat, one or two *emerging*, and several that are *aspirational at best*. Naming the categories honestly is more useful than claiming all eight.

---

## Habit specifically — what makes it real

Habit is the most-claimed and least-tested moat. The bar is high:

- **Daily or near-daily use, anchored to a recurring user trigger** (morning email, end-of-shift report, every commit). Weekly or monthly use is engagement, not habit.
- **Returns reinforced by user investment.** The user has built up something inside the product (data, history, tags, contacts, settings) that they'd lose by switching.
- **Low cognitive cost at the moment of use.** Habits run on autopilot. If users still consciously decide whether to open the product, it's not a habit yet.

The Fogg behavior model framing: habit forms when **motivation × ability × prompt** all line up consistently. Most products fail one of the three — usually ability (too much friction at the moment of use) or prompt (no reliable trigger).

---

## When a moat conversation is premature

Pre-PMF, moat questions are mostly distracting. The first job is to find a desperate audience that buys (`decision-making/value-hypothesis.md`). Worrying about defensibility before you've validated the value hypothesis is a way of avoiding the harder question.

That said, two pre-PMF cases where moats matter:

- **The "right and consensus" check.** If anyone could build what you're building, you don't have a moat *and* you don't have a non-consensus insight. That's the lowest-return position. (See `decision-making/value-hypothesis.md` § "The 'what'.")
- **B2B distribution.** In enterprise, the relationship and the integrations *are* the moat for many years. PMs from consumer backgrounds underweight this. The product can be technically inferior and still win because the buyer already has procurement, security, and integrations sorted.

---

## When a moat conversation matters most

- **Strategy memo to leadership** — claims about defensibility need evidence, not adjectives.
- **Pricing decisions** — products with real moats can hold price; products without one cannot.
- **Build-vs-buy** — buying often makes more sense for table-stakes capabilities and less sense for moat-relevant ones.
- **Acquisition integration** — the moat usually lives in *one* of the acquirer's or acquiree's stacks. Pick the one with the moat; rebuild the rest if needed.
- **Competitive response** — when a credible competitor enters, the defensible flanks tell you where to invest and where to concede.

---

## The ethical check

Engagement and habit-formation tactics can be designed in ways that exploit users (variable rewards, dark patterns, friction asymmetries between getting in and getting out). Building a habit moat by making the product *worse* for users — harder to leave, harder to ignore, harder to pause — is short-term defensibility at the cost of long-term trust.

The clean version of a habit moat: users keep using the product because it's the best way to get a recurring job done. The exploitative version: users keep using it because the team made leaving artificially painful.

Trust is a moat too. Burning it to build engagement is a bad trade.

---

## Decision checklist

Before claiming defensibility in a memo or deck:

1. **Which moat, specifically?** Pick from the eight. Generic "we have a moat" doesn't survive a review.
2. **Where's the evidence?** Behavioral data, retention curves, switching events, integration depth — not adjectives.
3. **Aspirational vs. emerging vs. real?** Be honest. Most teams over-rate.
4. **What's the still-undefended flank?** Every product has one. Naming it is more useful than pretending it doesn't exist.
5. **Would this survive a 1.5× better competitor?** If not, the moat isn't real yet.
6. **Are we building the moat ethically?** Habits built on dark patterns are short-term defensibility for long-term trust loss.

If two of these can't be answered, the strategy doesn't yet rest on a moat. It rests on hope, which is fine to admit and dangerous to disguise.
