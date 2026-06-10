# First-principles thinking

When to use it, when to skip it, and how to combine it with input from people who have already solved the adjacent problem.

First-principles reasoning gets pitched as a universal posture: bold, original, the way great PMs and founders supposedly think. In practice, it's a narrow tool with a specific use case, and overusing it produces slower, worse decisions than borrowing the pattern.

This file is the working-PM reference for using first-principles well: when to reach for it, where to constrain it, what it costs to break an established pattern, and how to weave it with network input.

---

## First-principles has a narrow right use

The default failure mode is to apply first-principles reasoning everywhere. The PM who reaches for it on every decision will re-derive solved problems on company time, ship slower than competitors who borrowed the pattern, and burn credibility with engineering when the obvious-in-hindsight answer turns out to be what everyone else already does.

The narrow right use of first-principles reasoning:

1. **The established pattern is provably broken for your situation.** Not "I don't like the pattern" or "it's inelegant." You can articulate the specific failure mode the pattern produces in your case. If you can't, default to the pattern.
2. **You have a structural advantage no incumbent has.** A different cost structure, distribution channel, data position, or regulatory standing. If your situation is genuinely different, the pattern designed for the standard situation may not apply. If your situation isn't genuinely different, the pattern probably does.
3. **No useful prior art exists.** Genuinely novel categories (new modalities, new substrates, new behavioral shifts) sometimes have no pattern to borrow. Most product decisions don't live here. When they do, first-principles is unavoidable.

In every other regime, the established pattern carries compressed information from thousands of prior attempts. It is your starting point, not a sign of unimaginativeness.

The discipline: before reaching for first-principles, name which of the three regimes you're in. If you can't, you're not in any of them. Use the pattern.

A useful test: can you describe, in one sentence, what's specifically broken about the established pattern *for your situation*? If yes, first-principles is justified. If you find yourself answering "it's just outdated" or "I think we can do better," the bar isn't cleared and the pattern is probably still your best starting point.

---

## Innovate on one or two axes, borrow the rest

Once you've decided to use first-principles reasoning, the next discipline is to bound it. Every product has many axes you could redesign: pricing model, onboarding flow, core interaction pattern, data model, billing cadence, support model, integrations, naming, file formats, keyboard shortcuts.

Pick the one or two axes where your insight is genuinely differentiated. Innovate hard there. On every other axis, borrow the dominant pattern users already know.

Three reasons:

- **Innovation budget is finite.** Each axis you change taxes the user's learning, the team's execution capacity, and your ability to attribute outcomes to specific choices. Five novel axes mean five simultaneous learning curves and five confounded experiments.
- **Conventional choices are a feature, not a failure of imagination.** Users come with established habits. Conventional choices on non-differentiating axes let users spend their attention on the parts that are actually new. Novel choices on every axis force them to re-learn everything before they reach the value.
- **Attribution requires control.** If something works after launch, you need to know which choice drove it. If five axes changed at once, you can't tell. If one or two axes changed, the attribution is clean.

The discipline: before design starts, write down explicitly which axes you are innovating on. Defend them. Then commit to conventional choices on every other axis.

A useful symptom of getting this wrong: the team can't articulate, in one sentence, what's actually different about the product compared to the closest reference point. "We're rethinking everything" is not a differentiation thesis; it's the absence of one.

---

## The hidden cost of throwing out an established pattern

When users have a habit around an existing pattern, breaking that pattern carries costs that don't appear in the design doc.

Four specific costs:

1. **Retraining cost.** Users must consciously relearn what was automatic. Their first sessions are slower. Their error rates spike. Their support requests rise. The product feels broken even when it isn't.
2. **Support cost.** Questions you didn't anticipate. Documentation you didn't write. Edge cases that don't exist in the standard pattern but emerge in your version.
3. **Trust cost.** Users assume you broke something they relied on. Even when the new pattern is better, the assumption is that the change was forced on them by a team that doesn't understand their workflow. Trust takes weeks to rebuild.
4. **Switching-friction cost.** The new pattern must be meaningfully better, not just different, to overcome inertia. Pure novelty rarely wins on its own.

Before discarding a pattern, name the habit it replaces and write down all four costs explicitly. The math usually favors keeping the pattern unless the new one is roughly 2x better on the dimension you care about. "It's cleaner" or "it's more elegant" rarely clears the bar. "It removes a step users hate" often does.

The discipline: pattern-breaking is a transaction with a price tag, not a free creative move. Estimate the price before you make the trade.

A useful diagnostic: if you have to write a "what's changed and why" guide longer than three paragraphs, the change is probably too aggressive. Either the change is wrong, or it should be staged into smaller moves that each carry their own justification.

---

## Combine first-principles with calling people who have solved the adjacent problem

First-principles reasoning and asking your network are not opposites. They are complements with different jobs.

- **First-principles** is for the part of the problem that is genuinely novel to your situation.
- **Your network** is for the part that someone has already solved, usually in a domain one step removed from yours.

The right sequence:

1. **Frame the problem from first-principles.** Identify which sub-problems are actually novel to your case and which are versions of a well-solved problem.
2. **Call three to five people who have shipped something adjacent.** Ask what they tried, what failed, and what they'd do differently. The point is not to copy their answer; it is to learn what's already known.
3. **Borrow their answers on the non-novel sub-problems.** This is the 80-90% of the problem that doesn't deserve original thought.
4. **Spend your first-principles thinking only on the novel sub-problems.** This is the 10-20% where original thought actually pays off.

Two failure modes:

- **Skipping the network step.** You re-derive what a 30-minute call would have given you. This is the most common form of waste in first-principles-heavy PM cultures, and the easiest one to recognize after the fact ("we spent a week on something three people would have answered in an hour").
- **Skipping the first-principles step.** You borrow patterns that don't actually fit your situation because you never identified which sub-problems were genuinely different. This is more common in pattern-heavy big-company cultures, and the harder one to recognize because the borrowed answers feel safe.

The discipline: explicitly partition each decision into "novel, must reason from scratch" and "solved, must find who solved it." Make the partition visible to the team. Spend scarce creative attention only on the first bucket.

A useful default: any time you find yourself thinking about a decision from scratch, ask "who has shipped something adjacent to this?" If the answer is "I don't know" rather than "no one," you have a research task before you have a thinking task.

---

## Decision checklist

Before applying first-principles reasoning to a product decision:

1. **Have I named the regime?** Provably-broken pattern, structural advantage, or no useful prior art. If none of the three, default to the pattern.
2. **Have I bounded the innovation?** Which one or two axes am I actually changing? What am I borrowing as-is?
3. **Have I priced the pattern change?** Four costs (retraining, support, trust, switching-friction) named explicitly.
4. **Have I called the people who would know?** Three to five conversations with people who have shipped something adjacent.
5. **Have I partitioned the decision?** Which sub-problems are genuinely novel; which are solved elsewhere and should be borrowed.

If three of these are weak, the first-principles approach is probably premature. Borrow the pattern, ship, learn, and earn the right to reason from scratch on the next round.

---

## Related

- [`problem-framing.md`](problem-framing.md) — how to write the problem statement that first-principles reasoning then attacks. Get the problem clean before deciding whether to think from scratch.
- [`risk-and-reversibility.md`](risk-and-reversibility.md) — two-way vs. one-way doors. The reversibility of the decision shapes how much first-principles work is justified.
- [`value-hypothesis.md`](value-hypothesis.md) — when the entire bet rests on an inflection point and a leap of faith, first-principles is unavoidable. When it doesn't, borrow the pattern.
- [`finding-pmf.md`](finding-pmf.md) § "Right and non-consensus" — the strategic frame for when first-principles produces asymmetric returns vs. when it doesn't.
- [`ai-craft-for-pms.md`](ai-craft-for-pms.md) — relevant for the partition step: AI is increasingly useful for the "solved sub-problems" research that you would otherwise do via network calls.
