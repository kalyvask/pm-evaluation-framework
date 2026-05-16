# User vs. chooser

Most B2B product strategies fail at the same hinge: the user is not the buyer, and the requirements look nothing like each other. The user wants a tool they want to use; the chooser wants a tool they can justify to their CIO. Designing for one and selling to the other is the canonical enterprise-product failure mode.

This file is about what changes as the price point scales, what evidence each tier requires, and the chasm most products fail to cross between them.

---

## The price-point ladder

Three tiers, with very different problems to solve:

- **Under $50K — solve a user-level problem.** The user is the buyer or close enough. Sell on user love. Proof is engagement and word-of-mouth. The case is *"I'm addicted to this thing; it's 10x more fun than the alternative."* You don't have to quantify the 10x; the user feels it.

- **$50K to $1M — solve a VP-level problem.** The user is no longer the buyer. A VP is going to have to walk into a CIO meeting and justify the line item against other budget requests. What gets the VP promoted? What gets them fired? Usually: shipping faster, hitting a delivery commitment, reducing a quantifiable risk. User love is necessary but not sufficient. You also need a story the VP can tell upward.

- **Over $1M — solve a C-suite-level problem.** Now you're competing for budget against other strategic initiatives. The C-suite cares about revenue, margin, risk, and the company-level commitments they made the board last quarter. User love and VP-level efficiency are table stakes. The decisive question is what *company-level* outcome the product moves.

Read the tier against your *actual sale price* and the *actual stakeholder making the call*, not your aspiration. Most teams overestimate which tier they're playing in.

---

## The 10x-fun-to-5x-measurable chasm

The biggest single product trap in enterprise: hitting product-market fit at the user tier on *"10x more fun"*, then trying to scale into the VP and C-suite tiers without translating that into measurable outcomes.

- At the **user tier**, *"I love using this"* is enough.
- At the **VP tier**, *"my team ships features 2x faster since we adopted it"* is the bar.
- At the **C-suite tier**, *"this changed our cost-of-revenue by X percent"* or *"this prevented Y class of incident"* is the bar.

The proof shifts from *feeling* to *quantification*. Products fall into the chasm when they can't make the measurable case. User data looks great (high DAU, high retention) but the team can't tell the CIO what the product is *for* in business terms. Without that translation, the product caps out at user-tier deals.

The discipline: from the start, instrument the product to produce the metric the *next* tier will demand. If you're selling at the user tier today and want to be at the VP tier next year, the *"ships 2x faster"* metric has to be measurable in the product before the VP asks for it, not after.

See also [`decision-making/value-hypothesis.md`](value-hypothesis.md) for stress-testing the leap-of-faith assumption behind your tier claim, and [`decision-making/metrics.md`](metrics.md) for instrumenting the outcome metric.

---

## When user love loses to good-enough plus distribution

The Slack vs. Microsoft Teams pattern, operationalized: when the chooser cares more about cost, integration, IT control, and vendor consolidation than about user experience, *good enough plus bundled distribution beats excellent plus organic adoption*.

This isn't a moral claim. It's the reality of how enterprise software gets bought when the chooser is consolidating vendors. CIOs don't optimize for user delight; they optimize for fewer contracts, fewer integration risks, and fewer vendor relationships to manage.

The strategic test: is the win condition **organic adoption** (you must be excellent and the chooser must listen to users) or **bundled distribution** (you must be good enough and inside an existing channel)? Most strategies treat these as the same condition. They aren't. A strategy that depends on organic adoption against a bundled competitor needs an explicit answer to:

> *What specifically prevents the chooser from defaulting to the bundled option?*

The honest answers usually look like:

- *"Our product is so much better that user revolt forces the chooser's hand."* Rare. Requires both excellence and a chooser who listens to users.
- *"We are not in the bundled stack and the chooser does not have an integrated alternative."* Works until they do.
- *"The chooser is not centralized; departments buy independently."* Works until budgets get consolidated.

If none of those answers hold, the strategy needs to shift toward distribution: get into a channel, get a strategic partner, get bundled, or get acquired. See [`decision-making/competitive-moat.md`](competitive-moat.md) on distribution as moat.

---

## The hybrid path: wedge then wall

The way most successful enterprise products navigate the chasm is the **wedge-to-wall** pattern:

- **Wedge.** Start at the user or VP tier with a focused, opinionated product that users adopt bottom-up. Generates demand signal, social proof, and user-tier revenue.
- **Wall.** Once the wedge is established in a critical mass of accounts, layer on the C-suite-grade requirements (governance, audit, identity, data residency, procurement compliance) so the chooser can sign a wall-to-wall enterprise contract.

The risk in this pattern is mis-timing. Layering on enterprise requirements too early dilutes the user-tier product and slows the wedge. Layering them on too late means the wedge stalls because the chooser can't justify expansion.

The signal for when to start layering: the wedge is hitting the same procurement / security / governance objections in repeated deals. That's the chooser telling you what's blocking wall-to-wall.

---

## Implications by tier

**When working at the user tier:**
- Optimize for user metrics (DAU, retention, NPS, word-of-mouth)
- *Instrument early* for the VP-tier metric the next sale will demand
- Treat your user as a leading indicator of the buyer, not the buyer
- Resist the temptation to add VP-tier features (governance, RBAC, audit) before the wedge is real

**When working at the VP tier:**
- Carry the user data forward but lead the pitch with the measurable VP-level outcome
- Translate user love into specific job outcomes (faster shipping, fewer incidents, lower coordination overhead)
- Build the metrics dashboard the VP can show their CIO without re-pulling the data

**When working at the C-suite tier:**
- Lead with the company-level outcome, not the team-level
- Quantify the alternative (what does the company spend today, in dollars and risk, that this product replaces)
- Solve the procurement, security, and compliance asks *first*; they are deal-killers, not features

---

## Anti-patterns

- **Designing for the user, selling to the chooser, with no translation.** The product is great; the case is mush.
- **Skipping the user tier and going straight to C-suite.** Without bottom-up demand, the sale relies entirely on relationship and budget, which makes it expensive, slow, and dependent on a single executive sponsor.
- **Letting "user love" excuse the absence of measurable outcomes.** User love is real and valuable; it doesn't by itself justify the budget conversation that has to happen eventually.
- **Treating distribution as cheating.** It isn't. Distribution is a real moat — often a bigger one than product quality, especially when the chooser is consolidating.
- **Pricing where you wish the deal would land, not where the chooser is.** A $300K ask without a VP-level proof point will be cut to a user-tier deal at $30K, or rejected. Match the proof to the price.

---

## Diagnostic questions

Before locking a product strategy or a sales motion:

1. **What tier am I actually playing in?** Match the *actual* sale price and stakeholder, not the aspiration.
2. **Who, specifically, is the chooser?** Named role and named reporting line. *"IT"* is not a chooser.
3. **What does the chooser get hired for, fired for, and promoted on?** If you can't answer, you can't pitch.
4. **What's the measurable outcome the next tier will demand?** And is it instrumentable in the product today?
5. **Is my win condition organic adoption or bundled distribution?** And what's the answer to *"what stops the chooser from defaulting to a bundled alternative?"*
6. **If I'm running a wedge-to-wall play, what's the signal that triggers the wall investment?**

If two or more of these are vague, the strategy isn't ready. Sharpen before committing budget or roadmap.
