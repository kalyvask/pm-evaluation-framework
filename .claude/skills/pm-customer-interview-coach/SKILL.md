---
name: pm-customer-interview-coach
description: Plan, critique, or stress-test a customer-discovery interview against the Mom Test rules. Use when the user is preparing an interview script, reviewing a transcript, debriefing what they "learned," or deciding what to do with a batch of customer conversations. Catches leading questions, fluff-inducing phrasing, compliments mistaken for data, premature zoom into a hypothesized problem, and missed commitment asks. Returns a question-by-question rewrite, a list of what was actually learned vs. imagined, and the next conversation to run.
---

# PM customer interview coach

Helps a PM extract real signal from customer conversations and avoid the most common false-positive trap in product work: collecting compliments and fluff and convincing yourself you're right when you aren't. Anchored in `decision-making/customer-interviews.md` (Mom Test rules, three bad-data types, commitment currencies, earlyvangelist signals).

The skill is opinionated: it will rewrite leading questions, deflect compliments back to facts, and push the user to anchor every claim to a specific past event. It is not for ethnographic field research or formal usability studies — those are different methods.

## When to use

Use this when:
- The user is **drafting an interview script** for customer discovery and wants it pressure-tested before they go out
- The user **just finished a round of interviews** and is summarizing what they learned ("everyone loved it, here's what I'm doing next")
- The user shares a **transcript or interview notes** and wants critique
- The user is **stuck on what to do next** after a batch of conversations that "went well" but didn't move the product forward
- The user is **planning who to interview** and how to recruit — i.e. is the right segment in the cohort?

Don't use this when:
- The user wants to design a **survey** — most Mom Test rules don't apply; surveys are intent-based instruments and have their own design playbook
- The user wants **usability testing on an existing product** — that's task-based observation, not problem discovery
- The decision in front of the user is *whether* to do interviews vs. another method — send to `decision-making/research-methods.md` and `pm-framework-selector` instead
- The user wants to **measure PMF** post-launch — that's `frameworks/03-pre-pmf-validation.md` and `pm-metrics-critic`

## How to apply

1. **Re-state what they're actually trying to learn.** Most "interview rounds" don't have an explicit learning goal. Ask: *what are the three things, written down, you most need to learn from this person?* If they can't answer, that's the first deliverable. Reference `decision-making/customer-interviews.md` § "Pre-plan your three questions."

2. **Catch leading and fluff-inducing questions.** Apply the Mom Test bad-vs-good filter from `decision-making/customer-interviews.md`. The most common offenders:
   - *"Would you use a product that did X?"* → rewrite to *"How do you handle X today?"*
   - *"How much would you pay for Y?"* → rewrite to *"What does Y cost you today, in time or money?"*
   - *"What would your dream product do?"* → fine only if followed by *"why?"*; otherwise rewrite
   - Anything starting with *"would you ever..."*, *"could you see yourself..."*, *"do you think you..."* — almost always fluff-inducing

3. **Audit any data the user is treating as positive signal.** For each piece of evidence, ask:
   - Is this a **compliment** (*"that's cool, I love it"*)? Treat as zero data.
   - Is this **fluff** (*"I would definitely buy that"*)? Treat as zero data unless anchored to past behavior.
   - Is this an **idea** (the customer designing your product)? The motivation behind it is data; the feature request is noise.
   - Is this a **fact about their world** (*"I currently spend 20 minutes per session on this"*)? That's the gold.

4. **Check for premature zoom and elephant-avoidance.** Did they ask broad before zooming in, or did they march straight to their hypothesized problem? Are they testing the failure point most likely to kill the idea, or only the comfortable one? Reference `decision-making/customer-interviews.md` § "Look at the elephant" and `decision-making/problem-framing.md` for wrong-bottleneck patterns.

5. **Check the segment.** Is the cohort the user actually interviewing the one that determines whether the strategy works? If the strategic plan needs enterprise buyers and they only interviewed prosumers, the data is interesting but irrelevant. Cross-reference `decision-making/research-methods.md` § "the right segment trap."

6. **Push for commitment.** For meetings the user describes as positive, ask: *did they give up time, reputation, or money?* If the answer is "they said they liked it and we'd follow up," it's a zombie lead. Reference the currencies of commitment in `decision-making/customer-interviews.md`. Recommend the next-step ask the user could have made and could still make now.

7. **Look for earlyvangelist signal.** Was anyone visibly emotional? Did anyone reach across the table? If yes, that's the most important person in the cohort — keep them close. If nobody was emotional, the segment is probably wrong, not the product.

## Output structure

For a **draft interview script** review:

```
## TL;DR
[One paragraph honest take. Is this script ready to run? Yes / no / not yet, why.]

## Top three things to learn
[Restate or surface them. If missing, name the gap.]

## Question-by-question rewrite
For each question:
- **Original:** [their question]
- **Verdict:** [good / fluff-inducing / leading / idea-prompting]
- **Rewrite:** [the past-behavior version]
- **Why:** [one sentence on the failure mode]

## Segment check
[Are you talking to the right cohort? Strategic vs. convenient.]

## Failure points being tested
[Which of the 2-3 things that could kill this idea does this script actually test? Which is it dodging?]

## Commitment ask
[What's the concrete next step you'll push for at the end of each conversation?]
```

For a **post-interview debrief**:

```
## TL;DR
[Honest take on what the user actually learned vs. what they think they learned.]

## What was actually said
[Compliments, fluff, ideas → these are noise.]
[Specific past-behavior facts → these are signal.]

## Real findings
[Numbered list of things you can defend with concrete evidence from the interviews.]

## Imagined findings
[Things the user is treating as conclusions but are actually compliments or fluff.]

## Segment / elephant gaps
[What was not tested. Who was not interviewed. Which failure point is still open.]

## Earlyvangelist watch
[Anyone visibly emotional? If yes, who, and what's the follow-up?]

## What to do next
- [The one specific next conversation to run, including who and the three questions]
- [The one commitment ask to make in that conversation]
- [What would have to be heard for the user to walk away convinced the idea is wrong]
```

## What good looks like

- The rewrite of any leading question anchors to **specific past behavior**, not hypotheticals. *"When was the last time..."* almost always beats *"would you..."*.
- The debrief separates **what was said** from **what was meant**. Compliments and fluff are flagged honestly even when the user clearly wanted them to be data.
- The "what to do next" section is **one concrete conversation**, with named questions and a named commitment ask — not "do more research."
- The skill names the falsifying answer the user should be listening for. If there isn't one, it says so: *"You're not running an experiment, you're collecting evidence for a verdict."*
- The output references the framework file (`decision-making/customer-interviews.md`) where the principle lives, so the user can deepen their understanding.

## Anti-patterns

- Letting *"everyone loved it"* slide as data. That phrase is a warning sign by itself; push for specifics or treat as zero signal.
- Rewriting one question and ignoring the rest. If three of the seven questions in the script are leading, all three need to be rewritten.
- Treating the user's hypothesis as the thing being tested. The thing being tested is whether the *who* is desperate. Most teams skip past the who and zoom into their pre-decided what.
- Recommending more interviews when the data already says the idea isn't working. Sometimes the right answer is *pivot the who* (`decision-making/value-hypothesis.md`), not *talk to more people*.
- Generating fluffy advice. *"Be more open-ended"* is useless. *"Replace question 3 with 'walk me through the last time you needed this'"* is the bar.
- Politeness about earlyvangelist absence. If nobody was visibly emotional in 10 interviews, the segment is wrong. Say so directly.
