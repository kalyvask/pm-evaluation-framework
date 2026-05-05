# Failure management

How to plan for, talk about, and recover from things going wrong. The asymmetry: avoiding failure is a low ceiling. Recovering well from failure is a high one.

---

## Set expectations for failure *before* the project starts

The most expensive failures are not the ones that happen. They're the ones that happen *after* a team has rationalized a metric drift for so long that no one will publicly admit the project failed.

The antidote is pre-commitment. Before any major project starts, the team writes down:

- **What does success look like?** Specific metric, specific value, specific date.
- **What does failure look like?** Specific metric, specific threshold, specific date.
- **What's the acceptable failure range?** What level of underperformance can we live with as a learning, vs. what level forces us to kill the project?

When the post-launch result lands inside the failure range, the team has a pre-agreed decision rule. The conversation becomes "we hit the bar we set" or "we didn't" — instead of "is this good or bad in some abstract sense?"

This also gives executive cover. *"We agreed in advance that <X% adoption at <Y> weeks would mean we stop. We're at <X−5%>."* That's a much easier conversation than retroactive judgment.

---

## Blameless postmortem

When something goes wrong, the team meets and reviews — without blame.

Three questions structure the conversation:

1. **Was this the right problem?** Did we solve what mattered, or did we drift to an easier adjacent problem?
2. **What did we learn?** Specifically — what do we now know that we didn't before? What was a surprise vs. a thing we should've predicted?
3. **How could we have learned this sooner?** What signal was available earlier that we missed or under-weighted? What would we change in our pre-launch process to catch it next time?

Three questions to *avoid*:

- "Whose fault was it?" — destroys psychological safety
- "Why didn't we ship faster?" — confuses speed with quality of decision
- "Who approved this?" — re-litigation of decisions, not learning

The output of a blameless postmortem is a written learning, shared. Not a list of people to blame, not a defensive narrative for execs.

---

## The "wrong problem" postmortem

A specific failure pattern that deserves its own treatment: *the team built the right thing well, and it didn't matter*.

When this happens, the postmortem question is not "did we build it well?" (yes) — it's "did we identify the right constraint?" (no).

The signals that you're in this category:

- The product addressed pain points users described
- Execution was clean
- Adoption was lower than expected, particularly among the segment the strategy depended on
- After launch, qualitative feedback reveals the *real* blocker was somewhere else

Recovery is harder than from execution failure, because you can't fix it by trying again on the same plan. You have to re-diagnose, which often means revisiting strategic assumptions you'd considered settled.

(See `case-patterns/wrong-bottleneck.md` for the canonical example, anonymized.)

---

## Move failed teams quickly

When a project fails decisively, the worst thing you can do is leave the team to dwell on it. Move them to a new project — visibly, with new framing — within 2–4 weeks.

This works for several reasons:

- **Identity protection.** A team that *had* a failure is different from a team that *is* failing.
- **Learning preservation.** The team's hard-won learnings are most valuable when applied to the next problem, not when the team is still rehashing the last one.
- **Morale.** Engineering and design morale recovers fastest when there's a new ambitious bet to anchor on.

Caveat: don't skip the postmortem. Move the team *after* the postmortem is written, not before. The postmortem is the bridge.

---

## Notify executives early

The worst version of an exec conversation: the executive learns about a problem from a customer, a competitor, a peer, or a board member.

A good PM gets ahead of that with a brief, honest message *as soon as the problem is identifiable* — not when it's fully analyzed.

Structure:

> **Heads up:** here's what we're seeing — [specific signal, specific data]
> **What we don't yet know:** [specific open questions]
> **What we're doing about it:** [specific actions, in flight or planned]
> **When I'll have more:** [specific date, specific update format]

Two things worth noting:

1. **Tell your boss before they hear it from somewhere else.** Even a half-formed update is better than them learning from a customer.
2. **Don't wait for a complete analysis.** A preliminary plan with caveats is more useful than a polished one delivered three days later. Velocity of information beats precision of information for most exec contexts.

This applies in both directions: also tell engineering, design, and sales early when you sense a problem in your own area — before they hear from leadership.

---

## Public ownership, private accountability

When something goes wrong externally, the PM takes the public hit. That means:

- In customer conversations: don't blame engineering ("they couldn't ship in time"), design ("they over-scoped"), or sales ("they oversold"). Take it. *"We over-promised on the timeline. We're working through it."*
- In exec conversations: don't blame the team ("morale's been low"). Take it. *"The strategy I committed to didn't pan out. Here's what I'm changing."*
- In all-hands or written comms: don't soften it with passive voice. *"We mis-diagnosed the constraint."*

Internally, accountability is private but real. The PM holds people to standards in 1:1s, in design reviews, in code review. Tough on the work, generous in public attribution.

The asymmetry is the point. **Trust gets built by absorbing blame the team didn't earn.**

---

## When to perseverate vs. when to kill

The hardest call in failure management. There's no clean answer, but two heuristics help:

### Signs to keep going (perseverate):

- The diagnosis is right; only the execution path is uncertain. Iterating *on the path* is likely to find a working version.
- Pre-committed kill criteria have not been hit. The result is bad but inside the agreed acceptable-failure range.
- Qualitative signal from the strategic segment is positive, even if quantitative signal is weak. Sometimes the metrics are lagging the user behavior.
- The team is energized and proposing concrete next experiments, not relitigating the original decision.

### Signs to kill:

- Pre-committed kill criteria have been hit. Don't move the goalposts.
- The diagnosis turned out to be wrong, and there's no obvious version of the project that solves the right diagnosis.
- The strategic segment is *worse* than neutral — they've actively rejected the product or there's a structural reason they can't adopt (e.g., it imposes a cost on them they cannot accept).
- The team is exhausted and rehashing the original decision rather than proposing experiments.

### When in doubt:

Most teams hold on too long, not too short. **Sunk cost is the dominant bias in PM decisions.** When uncertain, the historical pattern is that killing earlier was the right move.

But "kill earlier" is not the same as "kill at the first bad data point." Real signal needs time to develop. The discipline is in pre-committing kill criteria so the question becomes *"have we hit the bar we set?"* rather than *"do I feel good about this?"*

---

## After a kill: framing matters

If you kill a project, how you frame the kill determines what the team learns and whether they have permission to take risks again.

**Bad framing:**

- "It didn't work." (Implies someone's fault.)
- "We've decided to focus elsewhere." (Vague; reads as "we lost faith.")
- "Resources were needed for higher-priority work." (Implicit ranking; demoralizing.)

**Good framing:**

- "Here's what we hypothesized. Here's what we observed. Here's the specific reason the bet didn't pay off, and here's what we now know that we didn't before. The team's learning carries forward to [next project]."

This treats the kill as the proper endpoint of an experiment, not a punishment. It preserves the team's willingness to take the next risk.

---

## Decision checklist

Before launch:

1. Are success and failure criteria pre-committed?
2. Is there an acceptable failure range, agreed by team and exec?
3. Are kill criteria written down?

When something goes wrong:

1. Have I told my boss before they heard from somewhere else?
2. Am I taking the public hit?
3. Will the postmortem ask "was this the right problem?" — not just "did we ship well?"

After a kill:

1. Has the team been moved to a new bet within 2–4 weeks?
2. Is the kill framed as a completed experiment, not a punishment?
3. Has the learning been written down and shared, not just discussed?

If two of these are missing, the failure management practice is broken — even if the team is still functional.
