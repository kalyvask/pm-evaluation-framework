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

## When user-demand ranking is wrong

Most prioritization frameworks above (RICE, MoSCoW, Opportunity Scoring) assume the right answer is the one users ask for loudest. Often it is. Sometimes it isn't. When brand, moat, vision, or team capacity disagree with user-demand ranking, the team needs a meta-check to sequence the override considerations. This section is that check.

The Streamlit case (a public PM example, post-launch): the team had five user-requested features, all reasonable, none cheap (state, components, deployment, customization, caching). User-vote count alone would have produced one ranking. The team's actual sequencing was different in three of the five cases, because user-demand was the wrong signal for those features.

The decision logic is a **sequence**, not a multi-axis tradeoff. Ask the questions in order; the first one that has a clear answer wins.

### Step 1: Diagnose the bleed

Which stage of the user journey is hurting most right now? Not all stages at once. Pick one.

| Bleeding stage | What overrides demand | What it looks like in practice |
|---|---|---|
| Onboarding (signups not converting) | Brand defense; first-impression risk | First page promises something the product can't deliver |
| Activation (signups not reaching aha) | Speed and reliability of the first complete experience | First app feels slow, broken, or confusing |
| Retention (active users dropping out) | Stickiness, switching costs, session depth | Users try it once, never return |
| Growth (no virality or ecosystem) | Network effects, integration depth, distribution control | Users love it but can't or won't get others to use it |

The bleeding stage decides which override axis dominates this quarter.

### Step 2: Map each candidate feature to an axis

For each feature in contention, ask: *which axis does this feature defend or build?*

The Streamlit mapping was:

- Caching defended *activation* (slow first app meant activation bleed; the team was about to break the "we are fast" brand promise)
- Deployment built *growth and distribution control* (owning the viral loop instead of depending on partner hosts)
- State defended *retention* (deeper sessions, returning to in-progress work)
- Components built *ecosystem moat* (long-term integration lock-in)
- Customization expanded *enterprise revenue moat*, but conflicted with the founding vision

If two features defend the same axis, the higher-impact one wins. If they defend different axes, the one defending the **currently bleeding** stage wins.

### Step 3: Apply three cross-cutting filters

These three override the stage-mapping when they apply:

1. **Reversibility.** If shipping wrong is hard to undo (open source, public API, brand-defining commitment), raise the bar. Streamlit held customization for years because shipping bad customization would have polluted the "5 lines = beautiful app" identity, and they couldn't walk it back without breaking trust with the existing user base. Reversibility raised the bar high enough that customization waited for explicit enterprise-contract pressure.

2. **Capacity match.** Match feature to who can build it. Founder-bottlenecked features get sequenced; delegable features can start in parallel. Streamlit started components because a passionate engineer wanted to build them and it was delegable. State, caching, and customization were founder-bottlenecked.

3. **Hack-vs-polished parallelism.** Can a rough version ship now to power users while the polished version waits? Streamlit shipped a State hack at month one; the full version came later. This buys time on the polished version without losing the power-user segment. See `frameworks/02-defining-the-mvp.md` § "Hack track vs. polished track for developer products" for the full pattern.

### Step 4: Sequence with parallelism

The output of this pass is not *one* feature. It's four things simultaneously:

- **One for what's bleeding now** (brand or activation defense). Streamlit picked caching here.
- **One that's compounding but slow** (moat or ecosystem build). Streamlit started deployment and components in parallel.
- **One that's hackable to buy time** (parallel quick-win for the loud-but-deferrable segment). Streamlit shipped State hacked.
- **Defer the rest with explicit named reasons.** Streamlit explicitly held customization on vision grounds and communicated that internally.

The common mistake is treating prioritization as "which one of these five do we do" instead of "which one defends what's bleeding, which one compounds in the background, which one ships as a hack, and which one is the explicit not-yet."

A useful sanity test: can the team articulate, in one sentence each, the reason for the top-priority bet *and* the reason for the deferred item? If the deferred item has no explicit reason ("we just didn't get to it"), the prioritization didn't run.

---

## Decision checklist

Before locking in a quarterly roadmap:

1. Does every top-5 item connect to the strategy in one sentence?
2. Have we explicitly named what's *not* in scope?
3. Are kill criteria defined for each major bet?
4. Have we sanity-checked the framework's output against qualitative judgment?
5. Is there a strategic-capacity carve-out, separate from the scored backlog?

If two of these are missing, the prioritization layer is broken regardless of how the deck reads.
