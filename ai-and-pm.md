# AI and the PM role

How AI is changing what PMs do, what they're hired for, and what gets harder vs. easier.

---

## What changes, what doesn't

A useful frame: not all PM work is equally exposed to AI leverage. Some of it gets dramatically easier; some of it doesn't move at all.

| High AI leverage | Limited AI impact |
|---|---|
| PRD drafting and editing | Cross-functional alignment |
| Competitive benchmarking and feature comparison | Stakeholder management and trust building |
| Customer interview synthesis (transcripts → themes) | Strategic decision-making in ambiguity |
| Meeting notes, follow-up extraction | Calibrated conviction with executives |
| Design mockups (text-to-mock, prompt-to-Figma) | Differentiated pricing decisions |
| GTM planning and simulation | High-stakes one-way-door calls |
| Prototype building (PMs shipping working prototypes) | Hiring, firing, and team building |
| Data exploration and pattern recognition | Reading the room |

The pattern: **AI accelerates artifacts.** It does not (yet) replace judgment in ambiguous, high-context, multi-stakeholder situations.

---

## The bar has moved: PMs as builders

Until recently, the standard PM job was: write the PRD, work with design on mocks, hand to engineering, iterate. The PM rarely shipped anything functional themselves.

That's changing. The bar is shifting toward: **can you generate a working prototype for customer validation before engineering investment?**

The PMs who can do this have several advantages:

- **They validate demand cheaper.** A real prototype that users can click through reveals friction that a Figma mock never will.
- **They reduce engineering risk.** Engineering doesn't have to invest 6 weeks to discover the spec was wrong.
- **They build internal credibility faster.** "I have a working prototype" is more persuasive than "I have a spec."
- **They learn faster.** Building forces clarity in a way writing about building does not.

For PMs without engineering backgrounds, the entry point is usually:
- Prompt-driven prototyping tools (v0, Lovable, Cursor, Replit Agent)
- Model APIs for backend functionality
- Component libraries for frontends

You don't need to be a senior engineer. You need to be able to ship something that works for ten users, not 10,000.

---

## What hiring is now selecting for

Three traits that have moved up in the importance ranking:

### 1. Curiosity and continuous AI adoption

The AI tooling landscape changes monthly. PMs who stay current — try every new model, every new prototyping tool, every new evaluation framework — keep their leverage growing. PMs who don't see their leverage decay relative to peers.

This is a hireable trait: in interviews, ask candidates which AI tools they've used in the last month, what they tried that didn't work, and what changed in their workflow as a result. Vague answers are a red flag.

### 2. Communication skills under uncertainty

When AI does the artifacts, the human bottleneck moves to *communication*: explaining the bet to leadership, aligning engineering on a moving target, telling the team what to do when the model behavior is unpredictable.

Hire for clarity in ambiguity, not for fluent presentation skills. The two are different. A candidate who can summarize a 30-minute call into a 3-bullet exec brief — accurately, with the load-bearing points and not the filler — has the right wiring.

### 3. Full-stack building capability

Not "knows how to write production code." But: can build a working prototype, can use the AI tools, can speak credibly with engineers about tradeoffs.

The PM-as-builder profile is becoming the default in many AI-native companies, not the exception.

---

## What gets *more* valuable as execution speed democratizes

Counter-intuitively: **strategic assets that AI can't replicate become more valuable**, not less.

When everyone can ship a prototype quickly, the differentiation moves to the things AI doesn't help with:

- **Brand** — earned trust, recognized name, customer recall
- **Proprietary data** — training data, behavioral data, access nobody else has
- **Custom models** — fine-tuned for your specific domain, your specific use case
- **Regulatory relationships** — licenses, approvals, sector access
- **Distribution** — sales force, retail presence, partner channels
- **Network effects** — the side of the market AI can't bootstrap into existence

PMs in companies with these assets should think hard about how their products *leverage* the assets. PMs in companies without them should think hard about how to acquire or build one.

The pattern: in a world where the cost of building goes down, the value of *owning what's hard to build* goes up.

---

## What gets harder

A few things get *more* difficult, not less, in the AI-PM era:

### 1. Differentiation

When everyone can ship a working AI feature in a week, the surface-level differentiation collapses. You can't out-AI competitors with the same models. The differentiation has to come from somewhere else — data, distribution, brand, integration depth, workflow context.

A common failure: shipping a "with AI!" version of an existing product feature, expecting the AI itself to be differentiating. Within 6 months, three competitors have shipped the same thing.

### 2. Unit economics

AI features are expensive. Compute costs scale with usage. If you ship a feature that everyone uses and you can't charge proportionally, you've built a margin destroyer.

Before shipping any AI feature, model the cost-per-user-per-month at expected usage. Compare to expected revenue lift. Many "exciting" features are unit-economically broken.

### 3. Quality at scale

LLMs hallucinate, behave inconsistently, and degrade in unexpected ways under load or after model upgrades. PMs shipping AI features need to think about evaluation — how do you know the feature is working? — in ways that pre-AI products didn't require.

Specifically:

- **Evals** — automated tests that run before every deploy
- **Production monitoring** — sampling outputs in production for quality drift
- **Human review pipelines** — for high-stakes outputs, a human checks a sample
- **Fallback behavior** — when the model fails, what does the user see?

Most AI products that fail in market do so because of consistency / quality issues at scale, not because of capability gaps.

### 4. Trust and adoption

Users are increasingly skeptical of AI features. Privacy concerns, accuracy concerns, "did the AI make this up?" concerns. The bar for transparency, citations, "show your work" is higher than it was for non-AI features.

This is solvable, but it requires treating trust as a *first-class product property*, not a checkbox. Examples:

- Citation-first interfaces (every AI answer shows sources)
- Transparency in failure modes (the AI says "I'm not sure" rather than guessing)
- User control over AI behavior (toggle off, change model, escalate to human)

---

## What good AI PMs do

A composite of patterns that show up in successful AI-product PMs:

1. **They prototype before they spec.** A working prototype is the spec.
2. **They invest in evals early.** Quality drift kills AI products faster than missing features.
3. **They're explicit about model limitations.** They don't oversell capabilities to leadership or to users.
4. **They model unit economics under load.** Before scale, not after.
5. **They build trust into the UX.** Citations, transparency, control.
6. **They keep humans in the loop where stakes are high.** Even when the model is good, a human review pipeline lowers tail risk.
7. **They stay current on tooling.** They try every new prototyping tool, every new model, every new framework.
8. **They don't confuse "AI feature" with "differentiation."** They understand the AI is a capability; the differentiation has to come from somewhere else.

---

## Evals replace the PRD for model work

For traditional software, the PRD is the artifact engineering builds against. For model work, the center of gravity has shifted. The PRD still exists, mostly as a coordination doc for launch comms, design, and downstream teams. The artifact that actually drives the build is the eval set.

The reasoning: a PRD says *what the feature should do*. An eval set says *whether the model is doing it, on which inputs, with what failure modes*. When the model is the product, the second answer is the load-bearing one.

Practical implications:

- **Spec the evals before the prose.** If you can't describe the eval cases that would falsify the feature, the PRD prose is also vague.
- **The eval set is a living artifact.** It moves as you learn; the PRD usually doesn't.
- **There's no "the PRD is done" without an eval set behind it.**

---

## When to ship before the model is ready

Not every AI capability has to be polished before users see it. The cost of waiting can outweigh the cost of an imperfect first version, especially when the second-loop learning is the point. Five questions for the call:

1. **Is it generally safe?** Not "no failure modes." "No high-severity failure modes the user can't recover from."
2. **Will we learn something by shipping that we can't learn by waiting?** If yes, the slope of improvement after ship is part of the case for shipping.
3. **Is it useful for some users at current quality, even if not for everyone?** Developer surfaces can ship at 20% accuracy if developers will iterate around it. Consumer surfaces usually can't.
4. **Is the form factor going to be broadly applied later?** A novel form factor (computer use, agentic loops, MCP) has option value worth shipping for. A polished version of an existing form factor has less.
5. **Will the next version be materially better because of what users did with this one?**

If three of the five are yes, ship the imperfect thing. If two are clearly no, hold.

Not shipping is also a decision, with its own cost. The default isn't "wait for polish."

---

## Decision checklist

When considering an AI feature:

1. Have I prototyped it? (Not specced. Built.)
2. Do I have an eval suite? Or a plan to build one?
3. What are the unit economics at scale? Specifically — cost per user per month?
4. What's the failure mode when the model is wrong? What does the user see?
5. What's actually *differentiating* about this — the AI itself, or the data / distribution / context around it?
6. Have I budgeted for trust and transparency UX, not just core functionality?

If two of these are unanswered, the AI feature is not yet ready to commit.
