# Prioritization

How to choose what to build, in what order, with what level of confidence.

---

## The two kinds of prioritization decisions

It's worth separating two questions that often get conflated:

1. **Which problem to solve next?** — strategic. Lives in `frameworks/01-strategy-and-discovery.md`.
2. **Within an agreed problem, which solution / feature to ship next?** — tactical. This file.

Most prioritization disputes are actually disguised strategy disputes. If two engineers and a designer disagree about which feature to ship, sometimes the underlying disagreement is "we don't share the same target user." Re-anchor on the strategy before you score the backlog.

---

## Painkiller vs. vitamin

A useful early filter for any feature.

- **Painkiller** — solves a problem the user actively feels. Without it, they suffer. They will pay to make the pain go away.
- **Vitamin** — nice to have. Improves things on the margin. They might pay; they might not.

Most successful products are painkillers for *some* user. The trap is shipping vitamins to users who are not in pain and expecting them to pay.

In B2B, painkillers are usually:
- Compliance / regulatory pressure
- Cost reduction
- Outage / incident reduction
- Sales/revenue enablement
- Saving time on a frequent, painful task

Vitamins:
- "Better experience" features
- Generic productivity gains
- Innovation/competitive parity

When in doubt: a painkiller has a budget owner who can justify the spend in their own words. A vitamin has a champion who has to translate it into ROI for someone else.

---

## Toothbrush test

Will users use this twice a day, or every five months?

The original framing: a feature that solves a *frequently-encountered* problem will get more compounding usage and word-of-mouth than a feature that solves a *rarely-encountered* one — even if the rare problem is more painful per occurrence.

Use this when ranking features that all sound important. The more frequent ones almost always win on lifecycle value.

Caveat: high-stakes infrequent jobs (tax filing, annual reporting, year-end planning) are toothbrush-test failures by definition, and yet they're huge product categories. The test is most useful for *consumer and prosumer* products where habit formation drives retention. For specialized B2B tasks, frequency is less informative.

---

## Severity × Frequency × Feasibility

When ranking issues or feature requests in interface- or hardware-heavy contexts, score on three axes:

- **Severity** — how bad is the problem when it occurs? (1–5)
- **Frequency** — how often does it occur? (1–5)
- **Feasibility** — how cheaply can we fix it? (1–5)

Multiply. Rank.

This works particularly well for:

- Bug triage in critical-path products
- Hardware interface decisions where some issues are catastrophic but rare and others are minor but constant
- Enterprise feature requests where you have to choose among 30+ legitimate asks

The framework's value is in forcing the team to assess feasibility *separately* from desirability. A high-severity, high-frequency issue that requires rebuilding the data model is not the same as one that needs a 2-day patch.

---

## RICE Scoring

`RICE = (Reach × Impact × Confidence) / Effort`

See `frameworks/05-continuous-prioritization.md` for the full treatment. Two repeated cautions:

1. Don't break ties with false precision (7.4 vs. 7.6 is noise).
2. Confidence is the most-gamed input. Calibrate it against past quarters' deliveries.

---

## WSJF (Weighted Shortest Job First)

`WSJF = Cost of Delay / Job Size`

Particularly useful when the team is debating whether to do *one big strategic bet* or *several small unblocking items*. Often the small unlocks dominate, especially when:

- They unblock other work the team or another team is waiting on
- They reduce future risk (technical debt, security, deprecation)
- The big bet is in a phase where it's not yet ready to compound

The lesson is usually: *ship the small unlocks, in the small unlock window, while the big bet is still maturing.*

---

## MoSCoW (for release scoping)

When defining a release, force every candidate feature into one of:

- **Must-have** — absence breaks the product for the target segment
- **Should-have** — important but the product still works without it
- **Could-have** — desirable, ships if there's time
- **Won't-have** (this release) — explicitly out of scope

The discipline is in *Must-have*. A *must* must be testable: which segment rejects the product without it? If the answer is "everyone would prefer it," it's a *should*, not a *must*.

The *Won't-have* column is the most valuable. It's where scope creep dies.

---

## Opportunity Scoring

Survey users on:
- **Importance** of a job/feature (1–10)
- **Satisfaction** with current solutions (1–10)

`Opportunity = Importance + max(Importance − Satisfaction, 0)`

Highest opportunity = high importance, low satisfaction. Pair with a "what's your current workaround?" follow-up to identify revealed gaps, not just stated wishes.

---

## How to actually run a prioritization session

A failure pattern: the team picks a framework, scores 50 items, ranks them, and ships in order — and six weeks later the highest-RICE item turns out to have been irrelevant to the strategy.

A better flow:

1. **State the strategy in one sentence.** What is the current bet? What is the North Star metric we're trying to move?
2. **Filter brutally.** Drop any candidate that doesn't directly serve the strategy. Be willing to drop 60–80%.
3. **Score what's left.** Use one framework, not three. Pick the right one for the question (RICE for general backlog, WSJF for unlock-heavy, Opportunity Scoring when survey data is available).
4. **Sanity-check the top 5.** Read them out loud. Ask: *if we ship these, will the strategy actually move?* If not, the framework picked wrong; re-state the strategy.
5. **Define kill criteria for each.** What would we see that makes us stop? Ship without kill criteria and you'll keep shipping zombies.

The framework is a forcing function for clarity. It is not a tiebreaker. If two items score the same, the strategic narrative breaks the tie — not the score.

---

## Concentration after signal

Most teams over-spread their bets *after* signal has emerged. They keep funding the things that aren't working "in case they turn around" and under-fund the thing that is working "because it might be a fluke."

The right move is the opposite: **once a bet shows real signal, concentrate aggressively.** The cost of slightly under-funding a winner is large (you give up compounding upside); the cost of slightly over-funding a fluke is small (you find out and stop).

This applies in two common situations:

- **A portfolio of experiments where one starts working.** A team running several parallel bets should expect most to die. When one shows real signal, the question is not "should we keep the others alive?" but "how fast can we shift resources?" Killed teams move to the next bet within 2–4 weeks; the discipline is in moving them.
- **A roadmap where one feature is unexpectedly hot.** When usage data shows one of the shipped features pulling away, the temptation is to keep ratio'ing investment across the rest of the roadmap. The right move is usually to drop a weaker bet and double down on what's actually compounding.

The discipline is hardest when it's politically costly — when the bets being de-funded belong to people who advocated for them. Pre-committed concentration rules ("if any experiment hits X by Y, we move N% of capacity onto it") make the call easier later.

---

## Ranking rare-but-strategic against frequent-but-tactical

Frameworks like RICE systematically under-weight strategic bets, because:

- **Reach** for a strategic bet is small at first
- **Impact** is hard to quantify before you've shipped
- **Confidence** is low because the bet is novel

Don't try to fix this by inflating the inputs. Instead, **carve out a "strategic capacity" budget** — 20–30% of the team's time — that is *not* governed by the prioritization framework. It's governed by the strategic narrative.

That way, RICE governs the everyday work, the strategic narrative governs the bets, and the team isn't forced into a false comparison between them.

---

## Decision checklist

Before locking in a quarterly roadmap:

1. Does every top-5 item connect to the strategy in one sentence?
2. Have we explicitly named what's *not* in scope?
3. Are kill criteria defined for each major bet?
4. Have we sanity-checked the framework's output against qualitative judgment?
5. Is there a strategic-capacity carve-out, separate from the scored backlog?

If two of these are missing, the prioritization layer is broken regardless of how the deck reads.
