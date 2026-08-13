# Agentic product design

[`ai-integration.md`](ai-integration.md) is written for AI *features*: the model produces one output — a label, a range, a ranked list, a suggestion — and the user decides what to do with it. Its central rule is that the model should be invisible, because the user cares about the recommendation, not the mechanism.

That rule holds right up to the moment the product stops suggesting and starts **acting**. An agent takes a sequence of steps on the user's behalf, chooses its own path between them, and produces side effects in the world: an email sent, a record updated, a file changed, a booking made. Once the product acts, the invisibility rule inverts. The user now needs to see what was done, by whom, and be able to undo it.

This file is the design discipline for that class of product. Read [`ai-integration.md`](ai-integration.md) first; this one assumes it.

The frame: with a feature you design the screens. With an agent you design the **constraints the agent operates inside**, because you cannot enumerate the paths in advance.

---

## The deterministic-design assumption breaks

The default PM/design workflow assumes a finite set of states: one click goes to one screen, and the spec enumerates them. Every artifact in the standard toolkit — the user flow, the wireframe set, the acceptance criteria — encodes that assumption.

An agent decides how to get from one step to the next, often across a sequence nobody drew. Rachel Been, SVP of Design at Expedia, states the constraint plainly: *"You cannot do deterministic design"* — you can't design all the screens in advance.

The design object changes accordingly:

| Feature design | Agentic design |
|---|---|
| Enumerate the screens | Enumerate the constraints that hold across any path |
| Acceptance criteria per flow | Behavioral rules the system obeys regardless of flow |
| QA the happy path plus known errors | Eval the distribution of outcomes; assume unseen paths |
| Spec says what the product does | Spec says what the product will never do, and who approves the rest |

This is the practical reason agentic PRDs go stale on contact with the build: they were written as flow specs for a system that doesn't have flows.

**Evaluation question:** does this spec enumerate screens, or does it enumerate the rules that hold no matter which path the agent takes? If it's screens, it will be wrong within a sprint.

---

## Design the constraint system, not the outputs

If you can't specify the paths, specify the system that keeps every path coherent. Two moves do most of the work.

**Shared componentry across agents.** Expedia's design team has close to a dozen specialized agents in development — one comparing pricing and amenities, one planning activities, a general Q&A tool — all built on the same underlying design system rather than scripted individually. As Rachel puts it: *"They're all different skills, all different agents, but they're using a lot of the same componentry."* The shared system is what keeps the experience cohesive for the end user even as outputs vary.

**An explicit rule set the agents are held to.** At Accor, VP of Product Design Thomas Vidal's team runs agents that check hotel rates, book rooms, and update reservations across 40 hotel brands in 100 countries. To keep that many agents behaving consistently, they wrote a framework they call *golden rules*, covering things like customer insight (guests want to be known, but not watched) and brand basics (each hotel line, entry-level or luxury, has a distinct personality). *"Our goal isn't to design everything AI can do, but to create the conditions and rules for the system to behave consistently and on brand."*

The PM deliverable here is the rule set, and it is a genuine artifact — not a values statement. A usable golden rule is falsifiable: you can look at an agent output and say whether it complied. *"Be helpful"* is not a rule. *"Never reference a guest's past stay unless the guest raised it first"* is.

**Evaluation question:** if two teams shipped two agents against this spec, would the outputs feel like the same product? What's the written artifact that makes that true?

---

## Decide who the agent is before what it does

For a feature, personality is a copy exercise done at the end. For an agent — something with a persistent presence that talks back — it's an upstream product decision that constrains everything downstream.

Superhuman hit this while building Go, an assistant that orchestrates a team of agents to write in a user's voice, surface context, and handle repetitive tasks. Before settling what Go would do, VP of Design Collin Whitehead's team spent weeks on who Go would be — where it should sit between "wispy and serious" and "cutesy," Clippy-adjacent. They landed on a mascot of two simple shapes and built motion into the UI as a deliberate signal of intelligence: *"When humans see something moving, our brains immediately attribute intelligence, or even intentional agency, to that object."* The agent moves when it's thinking, writing, or listening.

The transferable point is not "add a mascot." It's that an agent's persona sets the user's expectation of its competence and its authority, and an expectation set too high is a trust liability when the agent is wrong. Decide it deliberately, early, and write it into the same rule set as the behavioral constraints.

**Evaluation question:** what does this agent's persona imply about how much the user should trust it — and does that match how good it actually is?

---

## The invisibility rule inverts: attribute every action

[`ai-integration.md`](ai-integration.md) Rule 4 says lead with the outcome, not the model. That holds while the AI is producing a suggestion the user chooses to accept. It stops holding the moment the agent changes shared state, because the user is now accountable for work they didn't personally do.

Sheta Chatterjee, Head of UX for Cloud AI at Google, frames the stakes on Gemini Enterprise — a workplace assistant that searches across an organization's data and lets teams run multiple agents on top of it: *"It's terrifying, because if you've handed something off to an agent, there's this black box. What if I'm performing a financial analysis and something really goes wrong?"*

The answer her team landed on is **clear attribution**: track the changes an agent makes closely enough that errors are easy to recognize and roll back. *"We need to be able to delineate what a human has done and what an agent has done."* The model she points to is Figma's own canvas — multiple people see each other's cursors and what's being edited in real time. The same visibility should exist when the collaborator is an agent.

Three concrete requirements fall out of this:

1. **Every agent-produced change is labeled as agent-produced**, in the surface where the change lives — not in a separate log the user has to go find.
2. **Every change is individually reversible**, at the granularity the agent worked at. "Undo the whole session" is not attribution; it's a blunt instrument that punishes the user for the agent's one bad step.
3. **Concurrent work is visible while it happens**, not summarized afterward, whenever the agent is operating on something the user is also touching.

**Evaluation question:** looking at any object the agent touched, can the user tell which parts were the agent's and reverse exactly those parts?

---

## Calibrate transparency to accountability, not to capability

Attribution tells the user *what was done*. Transparency is the separate question of how much of the agent's *process* to show. The instinct is to show everything, and it's wrong as often as it's right.

The case for showing process: Gemini Enterprise surfaces what the team calls the model's **thinking states** — status updates like *"I accessed these files"* or *"I connected to Google Drive."* *"We need to show what process Gemini is going through when it's trying to help you get work done."* That transparency makes enterprise users feel more in control, and the reason is specific: **they're accountable for the output.** A person who will have to defend the analysis needs to see how it was produced.

The case against: Deidre Kolarick, Managing VP and Head of Design for Bank, Business, and Card at Capital One, has been researching where that line sits. *"How much transparency do we give users about which parts of the experience are being powered by AI, versus how much do we try to just create a seamless experience? This is going to be an ongoing debate. People don't necessarily want to know all the details of what's going on behind the scenes."* Feeling stuck behind an AI agent becomes a negative experience fast. Most of the time her customers want the issue resolved as quickly as possible; whether a human or an agent handles it is a design choice, not something the user needs to see.

Both are right, and the variable that separates them is **who owns the outcome**:

| The user is... | Show | Why |
|---|---|---|
| Accountable for the output (they'll present it, sign it, ship it) | Process — sources touched, steps taken, what was skipped | They need to defend it, so they need to check it |
| A customer receiving a service (support, servicing, transactions) | Outcome, plus a visible way out to a human | Process detail is friction between them and resolution |
| Delegating a reversible chore | Outcome, with process available on demand | Nobody reads a log for a task they don't care about |

The failure mode on both sides is the same: transparency chosen by team preference rather than by who carries the consequence.

**Evaluation question:** for each surface, who is accountable for the agent's output? If it's the user, is the process visible by default? If it's the company, is the fastest path to resolution visible instead?

---

## Make failure visible

Mistakes are inevitable. The common approach — set guardrails and hope — treats failure as the exception case, which means it's specced last and designed worst.

Invert it: design the failure states as a matter of course, and hold them to three properties. Failure should be **easy to see, easy to fix, and easy to forgive.**

- **Easy to see.** The user finds out from the product, not from the consequence. If the first signal that the agent got it wrong is a customer replying to a wrong email, the failure design doesn't exist.
- **Easy to fix.** Correction happens where the error is, at the granularity of the error. This is why attribution above is load-bearing: you can't offer a targeted fix for a change you can't isolate.
- **Easy to forgive.** The cost of the mistake is bounded and the user knows it's bounded. A user who believes any given agent action could be catastrophic will supervise every action, which costs more than doing the work themselves.

The PRD test: for each agent action, write the sentence *"When this goes wrong, the user finds out by ___, fixes it by ___, and the worst case is ___."* Any action where you can't complete all three sentences is not ready to ship autonomously.

**Evaluation question:** are failure states specced with the same detail as the happy path, or are they a paragraph at the end that says "handle errors gracefully"?

---

## Treat trust as a feature, with a line in the plan

Trust is make-or-break for agentic products: when a tool acts on the user's behalf, they have to feel comfortable delegating, and once broken it's hard to come back from. Thomas Vidal treats it as deliberate infrastructure: *"You need to integrate trust from the beginning. Trust is not implicit — you really have to think about it."*

That means trust work appears in the plan as scoped, staffed line items, not as a quality everyone hopes emerges. Four mechanisms carry most of the weight.

**1. Let users set their own permissions.** People want to control what their agents can and can't do. At Atlassian, agents inherit the permissions of the account they're working in rather than having a separate set of settings — which means the agent can never reach anything its user couldn't reach, and there's no second permission surface to get out of sync with the first. Inheriting an existing permission model is almost always better than inventing a parallel one.

**2. Separate producing from publishing.** An agent can write and experiment freely; the gate goes at the moment its work reaches someone else. Sheta draws the line plainly: *"There's producing work, and then there's publishing that work. You want to be able to see it before it publishes."* An email hitting an inbox, a document shared with a team, a record other people read — a person approves those. Internal drafting doesn't need a gate; crossing the boundary to another human does.

**3. Route by stakes, not by action type.** At Accor, agents handle functional, low-stakes requests on their own — comparing hotels, checking loyalty points — while higher-stakes moments like customer service escalations go straight to a person. Thomas's formulation: *"The question isn't just 'can AI do it?' but 'should AI do it?'"*

The routing decision is about the emotional and consequential weight of the moment, and the same product surface can hold both. Deidre's example: a lost credit card is a standard request that doesn't need a high-touch, personalized interaction. But *"there are other servicing experiences, like if a family member passes away and you need to manage their estate. You need to engage with our servicing agents to facilitate that — that's a different expectation."* In those moments the user should feel in control, with the option to connect in whatever way feels right to them.

**4. Grant autonomy on a track record.** Autonomy is not a launch setting; it's earned per capability as the agent demonstrates reliability on that capability. Ship the gated version, measure the approval-override rate, and widen the gate where the override rate is near zero. A high override rate is the signal to keep the gate — or to reconsider whether that task should have been delegated at all.

Deidre's prompt to teams is the useful planning exercise: *"Push yourself to identify the high-anxiety experiences you own today, and ask what it would look like to make trust an explicit product requirement."*

**Evaluation question:** which line in this plan is the trust work? If trust isn't scoped and staffed, it isn't a requirement — it's a hope.

---

## Lean on familiar patterns

AI is moving fast enough that users barely build a mental model for one capability before the next arrives. An unfamiliar interface layered on top of an unfamiliar capability compounds the problem: the user is now learning what the thing does *and* how to operate it at the same time.

The design move is to spend novelty where it buys something. Novel capability, familiar container. A user who already understands inboxes, documents, review queues, comment threads, and version history can bring that model to an agent that works inside those objects. The same agent behind a bespoke interaction paradigm has to teach both.

This is also the cheapest source of the trust mechanisms above: existing patterns already carry undo, approval, attribution, and permissions. Reuse the pattern and you inherit the affordances.

**Evaluation question:** what's the novel thing in this design? If both the capability and the interface are novel, cut the interface novelty.

---

## The agentic design checklist

Run this alongside the [AI integration checklist](ai-integration.md#the-ai-integration-checklist) for any product where the AI takes actions rather than making suggestions.

1. **Constraint system:** does the spec enumerate constraints that hold across any path, rather than screens? Is there a written rule set, with rules specific enough to be checkable against an output?
2. **Persona:** is the agent's persona a deliberate decision, and does the competence it implies match the agent's actual reliability?
3. **Attribution:** for every object the agent touched, can the user see which changes were the agent's, and reverse exactly those?
4. **Transparency calibration:** is process visible where the user is accountable for the output, and out of the way where they just want the outcome?
5. **Failure visibility:** for each action — how does the user find out, how do they fix it, and what's the worst case? All three answerable?
6. **Permissions:** does the agent inherit an existing permission model rather than introducing a second one?
7. **Produce vs. publish:** is there a human approval gate at every point where the agent's work reaches someone other than its user?
8. **Stakes routing:** which moments go straight to a human, chosen by emotional and consequential weight rather than by action type?
9. **Autonomy ladder:** what does the agent have to demonstrate, on what metric, to earn a wider gate? Is the override rate instrumented?
10. **Familiar patterns:** is the novelty in the capability rather than the interface?

If items 3, 5, or 7 are weak, the product isn't ready for autonomy regardless of how good the model is. Ship the gated version and widen it on evidence.

---

## When this file applies

Use this file when:

- The product takes multi-step actions on the user's behalf, not just producing outputs the user then acts on
- The AI writes to shared state — documents, records, messages, systems other people read
- You're writing a PRD for an agent and the flow-spec format is fighting you
- Users are refusing to delegate to an agent that passes its evals (the gap is almost always a trust-surface gap, not a model gap)
- You're deciding how much autonomy to grant at launch

Don't use this file when:

- The AI produces a suggestion, estimate, or ranking that the user applies themselves — that's [`ai-integration.md`](ai-integration.md)
- The question is about the general design layer (defaults, friction, choice architecture) — that's [`decision-making/behavioral-design.md`](behavioral-design.md)
- The question is about how the PM personally uses AI — that's [`ai-craft-for-pms.md`](ai-craft-for-pms.md)
- The decision is whether to use AI at all — [`ai-integration.md`](ai-integration.md) § "When AI is the wrong answer" comes first

---

## Sources

Practitioner quotes and examples in this file are drawn from Figma's *Writing the rules of agentic design*, which collects field practice from Rachel Been (SVP of Design, Expedia), Thomas Vidal (VP of Product Design, Accor), Sheta Chatterjee (Head of UX for Cloud AI, Google), Deidre Kolarick (Managing VP and Head of Design for Bank, Business, and Card, Capital One), and Collin Whitehead (VP of Design, Superhuman), plus the Atlassian permission-inheritance pattern. The synthesis into evaluation questions and the checklist is this repo's.
