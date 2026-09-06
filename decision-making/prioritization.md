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

## Route requests by band before scoring them

Every framework on this page — RICE, WSJF, Opportunity Scoring, MoSCoW — takes request volume as an input. Raw request volume systematically over-weights the users least interested in the product, because there are more of them and they complain more precisely. Before anything gets scored, sort the requesters into the three bands from `frameworks/03-pre-pmf-validation.md` § "Lovers, likers, and the disinterested" — the users who love it, the ones who kind of like it, and the ones who aren't interested — and route each request into one of four lanes.

The roadmap serves the first two bands. Three of the lanes are ways of doing that; the fourth is the explicit exclusion.

| Lane | Who it serves | What it is | Rough capacity |
|---|---|---|---|
| **Hold the shared core** | Both engaged bands | The features lovers and likers both use heavily. Reliability, speed, and quality on the thing that made anyone stay | Steady and non-negotiable. Chronically under-funded because it doesn't look like a differentiator |
| **Deepen the love** | The lover band | Depth and expansion on the separators — what lovers do that likers don't | The largest discretionary lane. Also the source of the next conversion hypothesis |
| **Pull the middle up** | The liker band | Remove what's holding likers at "kind of like it": the friction on the separator behavior, and the blocked-benefit requests | Second-largest. Highest yield per unit of work, because these users already chose to stay |
| **Not serving** | The disinterested | Explicitly declined, in writing, with the reason | Zero |

Four consequences worth being deliberate about:

- **The shared core is the lane that gets raided.** It has no champion — it isn't new, it isn't a differentiator, and nobody demos it. Letting it degrade loses likers before you ever convert them, and eventually costs you lovers too.
- **The separators are a conversion asset, not just a loyalty asset.** What lovers do and likers don't is the most specific description you have of the gap between the two bands, which makes it the best available hypothesis for moving the middle up. Depth work and conversion work are often the same work viewed from different ends.
- **Weigh the different-benefit request rather than reflexively taking or refusing it.** A liker asking for a faster version of the core workflow is straightforwardly high-yield. A liker asking for an adjacent capability ("could it also do invoicing?") might be a real surprise worth savoring — but a roadmap built mostly from those drifts toward the average of everyone's requests and stops fitting anyone in particular. The test is whether the request keeps the shared core load-bearing or routes around it.
- **"Not serving" has to be written down.** An unstated no is a yes with a delay — it comes back through escalation three weeks later with an exec attached. Give each declined request the same one-sentence named reason that deferred items get in Step 4 below.

Two people advocating the same feature for different bands are having a strategy argument, not a prioritization argument. Sort the bands first or the meeting will not converge.

### Why the disinterested capture the roadmap anyway

The pull toward the middle is structural, not a failure of individual judgment. Each force has a specific counter-move.

| Force | Why it pulls to the middle | Counter-move |
|---|---|---|
| Churn surveys | Sample only the people who left — by construction, the disengaged | Run a "why do you stay" study across both engaged bands at the same cadence |
| Lost-deal reports | Losses get documented and reviewed; wins are silent | Debrief wins with equal rigor. The won-deal reasons are the lover signature |
| Support tickets | Skew toward the confused and the blocked | Weight tickets by band before reading volume as priority |
| Escalation paths | The loudest customer is rarely the most loving one | Ask which band the escalating account is in before committing capacity |
| Exec anecdote | A single disengaged user with organizational power | Answer with the banding, not with a counter-anecdote |
| Growth targets | The unengaged band is the biggest addressable population on paper | Grow by converting likers, who are already halfway there, before chasing users who left |

Note what this table is and isn't arguing. The failure mode is building for people who aren't interested — not building for the middle. The likers are a target; they're simply a target you approach through the shared core and the separators rather than by taking every request at face value.

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

Most prioritization frameworks above (RICE, MoSCoW, Opportunity Scoring) assume the right answer is the one users ask for loudest. Often it is. Sometimes it isn't. When brand, moat, vision, or team capacity disagree with user-demand ranking, the team needs a meta-check to sequence the override axes. This section is that check.

The setup it's built for: the team has three to seven user-requested features, all reasonable, all expensive, more than one can be shipped this quarter. User-vote count would produce one ranking. Strategic axes (brand, moat, vision, capacity, sequence) would produce a different one. The team needs a defensible way to choose.

The decision logic is a **sequence**, not a multi-axis tradeoff. Ask the questions in order; the first one that has a clear answer wins.

### Step 1: Diagnose the bleed

Which stage of the user journey is hurting most right now? Not all stages at once. Pick one.

| Bleeding stage | What overrides demand | What it looks like in practice |
|---|---|---|
| Onboarding (signups not converting) | Brand defense; first-impression risk | First page promises something the product can't deliver |
| Activation (signups not reaching aha) | Speed and reliability of the first complete experience | First app feels slow, broken, or confusing |
| Retention (active users dropping out) | Stickiness, switching costs, session depth | Users try it once, never return |
| Growth (no virality or ecosystem) | Network effects, integration depth, distribution control | Users love it but can't or won't get others to use it |

The bleeding stage decides which override axis dominates this quarter. If two stages look equally hurt, the one closer to the top of the funnel wins: a broken onboarding silently disqualifies you from the activation problem mattering at all.

### Step 2: Map each candidate feature to an axis

For each feature in contention, answer three diagnostic questions:

1. **Which axis does this feature defend or build?** Brand promise, activation quality, retention/stickiness, ecosystem moat, distribution control, revenue moat, or vision integrity.
2. **What's the user-visible cost if this never ships?** Some features have a load-bearing absence: without them, users churn, the brand suffers, or expansion stops. Other features are merely "nice for the segment that asked."
3. **Is the user-vote count higher or lower than the strategic-axis ranking would suggest?** Disagreements are where this pass earns its keep. Agreement just means RICE was right.

Then apply the tiebreakers:

- If two features defend the same axis, the higher-impact one wins.
- If they defend different axes, the one defending the **currently bleeding** stage wins.
- If the highest user-vote feature defends a non-bleeding axis, it gets deferred regardless of vote count. The team has to be willing to communicate the deferral explicitly.

### Step 3: Apply three cross-cutting filters

These three override the stage-mapping when they apply:

1. **Reversibility.** If shipping wrong is hard to undo (open source, public API, brand-defining commitment, fundamental UX paradigm), raise the bar. A one-way-door feature requires higher confidence before shipping; a two-way-door feature can ship faster and be revised. Open-source maintainers, API platform teams, and any team whose product is the user's deep workflow infrastructure face this constraint hardest. A common failure: shipping the user-requested feature in the wrong form because the team didn't notice it was one-way, then carrying the bad version for years.

2. **Capacity match.** Match feature to who can build it. Founder-bottlenecked or senior-engineer-bottlenecked features get sequenced because there's only so much top capacity. Delegable features (those a passionate or autonomous engineer can pick up without deep core knowledge) can start in parallel with the bottlenecked ones. If you're capacity-constrained on top engineers and you sequence the wrong feature first, the delegable work sits idle while the bottleneck queue stretches.

3. **Hack-vs-polished parallelism.** Can a rough version ship now to power users while the polished version waits? For products with strong power-user contingents (developer tools, infrastructure, technical platforms), this is often the right move. Power users tolerate rough edges, file useful bug reports, and build internal credibility for the feature; the polished version benefits from their feedback. See `frameworks/02-defining-the-mvp.md` § "Hack track vs. polished track for developer products" for the full pattern.

### Step 4: Sequence with parallelism

The output of this pass is not *one* feature. It's four things simultaneously:

- **One for what's bleeding now:** the brand or stage-defense feature. Top priority, highest urgency, gets the best capacity.
- **One that's compounding but slow:** the moat or ecosystem build. Started in parallel, lower urgency, longer payoff. Often delegable.
- **One that's hackable to buy time:** the parallel quick-win for the segment that's loudest. Hack ships now, polished version waits in the queue.
- **The rest, deferred with explicit named reasons.** Each deferred item gets a one-sentence reason ("violates vision X," "waits on team capacity Y," "compounds with feature Z which isn't ready"). No deferral by silence.

The common mistake is treating prioritization as "which one of these features do we do" instead of "which one defends what's bleeding, which one compounds in the background, which one ships as a hack, and which one is the explicit not-yet." A team that runs only one track at a time falls behind on the others by construction.

A useful sanity test: can the team articulate, in one sentence each, the reason for the top-priority bet *and* the reason for the most-deferred item? If the deferred item has no explicit reason ("we just didn't get to it"), the prioritization didn't run.

---

## Decision checklist

Before locking in a quarterly roadmap:

1. Does every top-5 item connect to the strategy in one sentence?
2. Have we explicitly named what's *not* in scope?
3. Are kill criteria defined for each major bet?
4. Have we sanity-checked the framework's output against qualitative judgment?
5. Is there a strategic-capacity carve-out, separate from the scored backlog?
6. Do we know which band each top-5 item serves — the users who love the product, the ones who kind of like it, or the ones who aren't interested? Is anything in the top 5 serving the third, and is anything holding the shared core the first two depend on?

If two of these are missing, the prioritization layer is broken regardless of how the deck reads.
