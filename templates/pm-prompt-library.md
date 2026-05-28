# PM prompt library

A collection of reusable prompts for common PM artifacts. Each prompt is designed to produce a usable first draft you can edit, not a final artifact. The prompts are calibrated to the eight prompt principles in [`../decision-making/ai-craft-for-pms.md`](../decision-making/ai-craft-for-pms.md).

How to use:

1. Pick the prompt that matches the artifact you're working on.
2. Replace the bracketed placeholders with your specifics. The more context you put in those slots, the better the output.
3. Run it through your preferred model. Long-context models with strong structured-output behavior work best for these prompts.
4. Iterate. The first output is a draft. Critique it, ask for revisions, refine.

The placeholders use `[brackets]`. Customize aggressively. The prompts below are starting points, not finished prompts.

---

## Discovery interview prep

Use this before a customer-discovery interview to get a sharp set of opening questions and listen-fors.

```
I'm preparing for a customer-discovery interview with [Name], [Role] at [Company description, including company size, industry, what they do]. They [relevant context about their business situation, what they're trying to accomplish, any specific pain points you've heard].

My goal in this interview is to understand:
1. [Specific aspect of their workflow / decision / pain you want to learn about]
2. [Second aspect]
3. [Third aspect]

Help me prepare:
- 5-7 opening questions calibrated to the Mom Test rules (focus on past behavior, current pain, money already spent, attempts to solve the problem). Avoid leading questions, opinion questions, and hypotheticals about the future.
- For each question, the signal I should listen for, and what would be a "polite no" disguised as positive feedback.
- The one question I shouldn't ask because it would tip my hypothesis and bias the answers.
- An exit question to surface adjacent pains I haven't asked about.
```

The Mom Test rules referenced here live in [`../decision-making/customer-interviews.md`](../decision-making/customer-interviews.md).

---

## Interview transcript synthesis

Run this on a transcript after a discovery interview.

```
I've attached a transcript from my interview with [Name, Role] at [Company]. Context: [why I was talking to them, what hypothesis I was testing].

Analyze this conversation and produce:

## Key insights
Three to five specific insights, each anchored to a verbatim quote from the transcript. No paraphrasing; quote the actual words.

## Signal vs. noise
- What they said that was strong behavioral signal (past actions, money spent, attempts to solve, expressions of frustration about a specific moment)
- What was likely polite filler ("would be useful," "sounds interesting," "I can see how that helps")
- What was a polite no disguised as positive feedback

## Hypothesis check
Did this interview validate or weaken my hypothesis (which was: [your hypothesis])? Be specific about which parts moved and which didn't.

## Adjacent threads
What did they mention that wasn't my main topic but might point to a different problem worth exploring?

## Open questions
What did I not ask that I should have? What should the next interview probe?

For every claim above, cite the part of the transcript it came from. If a claim is an inference rather than a direct quote, mark it [INFER].
```

---

## PRD section-by-section

Don't ask AI for a full PRD in one shot. Section by section produces consistently better output. The first section sets the foundation; later sections build on it. The full PRD template referenced here lives in [`prd-template.md`](prd-template.md).

### Section 1: Overview and ICP

```
Help me draft the "Overview & ICP" section of a PRD.

Context:
- Product: [Name and one-sentence description]
- The problem I'm solving: [Specific user, specific job, specific blocker, specific cost. Avoid generic phrasing like "users want better X."]
- Why now: [What just changed (technology, behavior, regulation) that makes this newly buildable]
- The load-bearing assumption: [The one belief this PRD rests on]

Produce:

## Overview
A 2-3 sentence summary of what this product does and for whom.

## Ideal customer profile (ICP)
Named segment with multiple axes (role, company size, industry, situation, job-to-be-done). The narrower the better. Include the behavioral signature that distinguishes this ICP from adjacent segments.

## Why this ICP first
One paragraph on why this segment is the right beachhead vs. adjacent segments. Mention specifically why they are *desperate* (behavioral evidence), not just *needy*.

Keep each section tight. No filler. If you're not confident about a claim, mark it [INFER] so I know to verify.
```

### Subsequent sections

After the Overview & ICP is locked, run separate prompts for each subsequent section. Don't paste the whole PRD back in; trust the model to remember the earlier sections from the same conversation.

- **User stories.** *"Continue the PRD. Now draft the User Stories section based on the ICP above. Format each story as: 'As a [persona], I want to [job] so that [outcome]', plus a 1-2 sentence story of when this would actually happen in their week."*
- **Discovery strategy.** *"Continue. Now draft the Discovery Strategy: which assumptions still need validation, which experiments would falsify them, what success and failure thresholds apply."*
- **Competitive landscape.** *"Continue. Now draft the Competitive Landscape: who else is solving this, what segment of the market they own, where the white space is. Honest, no positioning fluff."*
- **GTM and sales motion.** *"Continue. Now draft the GTM section: pricing, sales motion (PLG / sales-assist / sales-led), distribution channel, and the rep economics question if relevant."*
- **Success metrics and kill criteria.** *"Continue. Now draft the Success Metrics and Kill Criteria section. For each metric: the specific value, the segment cut, the timeline. For the kill criterion: the specific threshold that would make us wind this down."*

Each section gets its own iteration cycle. Critique and revise before moving on.

---

## Press release and FAQ (working-backwards exercise)

The working-backwards exercise: write the press release and FAQ before building the product. Forces the team to articulate what the launch will say *if it succeeds*. If the press release reads as vague or unconvincing, the underlying bet is unclear.

```
Write a Press Release and FAQ for [Product], as if we're launching it 18 months from now and it became the success we hoped for.

Context:
- Product description: [What it does, who it's for, the insight behind it]
- The launch milestone (18 months from now): [What we'd consider "success enough to issue a press release about"]
- The audience for the press release: [tech press, industry trade press, customer-facing]

## PRESS RELEASE

Format like a real press release:
- Headline (one line, specific outcome, no hedging)
- Subheadline (one line, the why-now)
- Dateline + lede paragraph (the 5W: who, what, when, where, why)
- Three quotes (one customer, one company exec, one industry observer). The customer quote should be specific to a real before/after, not generic praise.
- One paragraph on the market context (the problem this is solving and who's been failing to solve it)
- One paragraph on what's next

## FAQ

The five questions a smart skeptic would ask after reading the press release. Each with an honest answer. No marketing speak. If the question reveals a real weakness in the strategy, name it explicitly rather than dressing it up.

If you find yourself writing a press release that sounds generic, or that any competitor could write with their name swapped in, stop and tell me which part of the underlying strategy isn't sharp enough to make a credible press release.
```

The PR/FAQ exercise is most useful *before* building, not after.

---

## Competitive monitoring

A two-prompt setup for staying current on a space without spending 5 hours a week reading.

### Setup prompt (run once, save the output)

```
Create a monitoring strategy for my space.

My space: [Specific market / segment / category, e.g. "B2B AI-driven sales enablement for mid-market"].

I want to track:
1. Competitors: [List 3-5 named competitors]
2. Adjacent players who might enter: [List 2-3 plausible adjacencies]
3. Underlying tech and behavioral shifts that would change the category

For each of the three buckets, give me:
- The top 3-5 specific sources to monitor (newsletters, X / LinkedIn accounts, podcasts, blogs, regulatory filings, conference talks)
- The signal-to-noise expectation for each (e.g., "high signal, weekly" vs. "low signal, scan headlines only")
- The question I should be asking myself when I see new content from each source
```

### Weekly synthesis prompt

```
Here are this week's updates from my monitoring sources [attach or paste the raw content].

Synthesize into:

## What's new
3-5 specific developments, with a one-sentence summary and a source link for each.

## What it means
For each development: does this change how I think about my market? What's the one decision I might revisit because of it? Be honest if the answer is "nothing, this is noise."

## What to watch next week
What's the question I should ask my team or my customers based on this week's signal?

## What I should ignore
Anything that looks important but isn't. Specifically flag press releases dressed up as news, and competitor announcements that won't ship for another six-plus months.

Keep the whole synthesis under 400 words. If a development isn't worth surfacing, drop it.
```

---

## Customizing for your context

The prompts above are starting points. Per the principles in [`../decision-making/ai-craft-for-pms.md`](../decision-making/ai-craft-for-pms.md):

- **Context before request.** The bracketed placeholders are where you add context. Don't skimp.
- **Specify the output structure.** Adjust the structure to match what you actually need. If a section is irrelevant for your use, remove it.
- **Prime the role.** When relevant, prefix with: *"Act as a [specific kind of PM] at a [specific kind of company]."*
- **Iterate.** The first output is a draft. Critique, revise, polish.
- **Specify length.** If you want short, say short. AI defaults to verbose.

The prompts are intentionally opinionated. They reflect how the rest of this repo thinks about PM work: narrow over broad, behavioral over attitudinal, falsifiable success criteria, honest naming of weakness. If they don't match your context, edit them.
