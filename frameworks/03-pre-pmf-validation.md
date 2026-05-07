# Phase 3 — Pre-PMF Validation

**Focus:** Find signal to scale. You've shipped something. Before you pour growth dollars in, you need evidence that users actually want what you built — and that you can sell it.

---

## "10 Happy Users" Rule

Before measuring NPS or retention curves, find ten **non-friend** users who genuinely love the product. Not ten users who tried it. Ten who would be visibly upset if it disappeared.

If you cannot name them, you have a usage problem, not a metrics problem. No amount of funnel optimization fixes a product that ten strangers don't love.

This is also a useful counter to "free adoption ≠ PMF": ten people who took a free trial and never came back are not a signal of anything.

---

## Sean Ellis Test

Ask current users: *"How would you feel if you could no longer use this product?"*

Options: very disappointed / somewhat disappointed / not disappointed / N/A.

Below ~40% "very disappointed" is generally taken as a signal of weak PMF — though the threshold varies by category and segment, so use it as directional, not as a pass/fail. Slice the response by user segment; PMF often exists for a narrower group than you assumed.

The most useful data is in the open-ended follow-up: *"What would you use as a replacement?"* The answers reveal the actual competitive set, which is usually different (and often more dangerous) than the deck slide.

---

## Activation Rate / Time to Value (TTV)

Two paired metrics:

- **Activation rate** — % of new users who reach the *aha* moment in their first session (or first N days, depending on category).
- **Time to value** — median elapsed time from sign-up to that *aha*.

Define *aha* concretely. "Sent first message" is concrete. "Engaged with the product" is not.

Bad activation kills good acquisition. If 60% of sign-ups never hit *aha*, doubling acquisition spend doubles the wasted users, not the active ones. Fix activation before scaling acquisition.

---

## GTM Strategy Checklist

Before claiming PMF, validate the *go-to-market* plan, not just the product:

- **ICP** — who is the ideal customer profile, named specifically? "SMB" is not an ICP; "operations leader at 50–200-person logistics company in North America" is.
- **Sales motion** — PLG, sales-assist, or sales-led? Does the price point support that motion?
- **Distribution** — what channel(s) reach the ICP repeatably? Have you proven any of them work?
- **Pricing** — what value metric, what willingness to pay, what packaging? How much friction does the price create at the point of sale?
- **Sales-rep economics** (in B2B) — does the rep make enough commission per deal to prioritize this product? **Coin-optimized reps will not push a product without commission upside, no matter how good it is.**

In B2B, **distribution is product**. A technically superior product that doesn't get in front of buyers has zero value. If your launch strategy assumes reps will carry the product without an incentive, that is a launch-blocker, not a launch-detail.

---

## Smile Curve

Plot a histogram of user engagement frequency over the last 30 days. The healthy shape is a *smile*: a tall left bar (users who churned), a short middle (occasional users), and a tall right bar (users who use it heavily).

A flat or frowning shape (most users in the middle) usually indicates a product that's *nice to have* — useful enough to keep around, not useful enough to commit to. Flat-shape products typically don't survive contact with a competitive market.

A smile shape is a sign that the product has true believers, even if many users churn. PMF often lives on the right tail.

---

## ARC PMF Framework

Three dimensions:

- **Acquisition** — can you get users efficiently? Are CAC and channel economics defensible?
- **Retention** — do users stay? Cohort curves should flatten, not collapse.
- **Consumption** — once retained, do users use it deeply? More accounts? More seats? More usage per session?

PMF requires evidence on all three. Strong acquisition with collapsing retention is a viral curiosity. Strong retention with no consumption growth is a niche tool. Strong consumption with no acquisition path is a nice-to-have for a small group.

---

## What "PMF" actually means

Three things that are easy to confuse:

- **Free adoption ≠ PMF.** People will try anything that's free. PMF requires evidence that people would *pay*, *renew*, or *switch from an existing solution*.
- **Strong NPS ≠ PMF.** A product can have unusually high NPS and still fail to find a sustainable economic model. NPS measures love, not viability. See `decision-making/value-hypothesis.md` § "The inclusion vs. control tension" for the version of this that shows up in regulated categories.
- **Usage ≠ PMF.** Free trials, internal employee usage, and "I tried it once" all count as usage. PMF requires retained, growing, willing-to-pay usage from your ICP.

The hardest question in this phase is honest: *would users still use this if it cost what it should cost to run?*

---

## When this phase is done

You should be able to answer:

1. Who are the ten happy users? What do they have in common?
2. What's the activation rate, time to value, and Sean Ellis "very disappointed" %?
3. What does the smile curve look like?
4. What's the GTM motion that gets us from here to scale, and have we proven any of its core assumptions?

If you can't answer these with real data — not aspirational projections — you do not have PMF, regardless of how the deck reads.
