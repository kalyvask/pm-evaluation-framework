# Blameless postmortem template

For projects that didn't deliver — kills, missed launches, missed metrics, escalated incidents. Goal: extract learning, not assign blame.

Length: usually 1–3 pages. Longer postmortems are usually defensive narratives in disguise.

---

## Title

[Short, specific. What happened in one line.]

## TL;DR

One paragraph. What we tried, what happened, the most important thing we learned.

## What we set out to do

The original goal, in plain language. Pre-committed success and failure criteria, if they existed.

If pre-committed criteria didn't exist: note this. It's often a contributing factor.

## What happened

Factual. What we built, when we shipped, what the results were. No interpretation yet.

Include:
- Key dates
- Key metrics, with values
- Key decisions made along the way

## What we learned

The interpretive section. Three questions:

### 1. Was this the right problem?

Did we solve what mattered, or did we drift to an easier adjacent problem?

If the diagnosis was wrong, name it specifically. *"We treated this as a friction problem; it was an incentive problem."*

### 2. What did we learn?

What do we now know that we didn't before?

- Specific surprises
- Specific assumptions that turned out to be wrong
- Specific assumptions that turned out to be right (worth noting — confirms our priors are sometimes correct)

### 3. How could we have learned this sooner?

What signal was available earlier that we missed or under-weighted?

What would we change in our pre-launch process to catch it next time?

## What we won't do again

Specific behaviors to drop, with the reason.

- "We won't validate exclusively with the convenient segment when the strategy depends on a different segment."
- "We won't ship without pre-committed kill criteria."
- "We won't treat stakeholder approval as validation."

Specificity matters. "Be more rigorous" is not a learning.

## What we'll do differently next time

The forward-looking complement.

- Specific changes to our pre-launch process
- Specific changes to how we validate
- Specific changes to how we communicate up

## What we wouldn't change

Often missed. The decisions that, with hindsight, were still the right calls — even if the outcome wasn't what we hoped.

This matters because it preserves the team's confidence in the process. Not every bad outcome is the result of a bad decision.

## Carried-forward team

Where the team goes next. Move them within 2–4 weeks of the postmortem.

- Team member 1 → [new project, role]
- Team member 2 → ...

## Postmortem distribution

Who reads this. Postmortems should be circulated, not buried.

- Leadership review
- Team review
- Cross-functional partners (engineering, design, sales, support)
- Future PMs working on similar problems

---

## What this template avoids

- "Whose fault was it?" — destroys psychological safety, kills the next round of risk-taking
- "Why didn't we ship faster?" — confuses speed with quality of decision
- "Who approved this?" — re-litigation, not learning
- Defensive narratives — most often signaled by paragraph after paragraph of context-setting before any honest assessment of what went wrong

The output of this postmortem is **a written learning, shared**. Not a list of people to blame, not a deck for execs that softens the news.
