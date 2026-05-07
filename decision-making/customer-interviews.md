# Customer interviews

The single most common way PMs collect false positives. A bad interview doesn't just fail to teach you — it convinces you you're right when you aren't. This file is about how to actually run one.

Distilled from Rob Fitzpatrick's *The Mom Test* and the customer-development tradition (Steve Blank, Andy Rachleff). The principles are tactical: when you sit down with a user, what do you ask, what do you ignore, and how do you know whether you learned anything.

---

## The core failure mode

> "I talked to 50 people. Everyone said they loved it. Then we shipped, and nobody bought."

This is the canonical interview failure. It happens because most interviews are designed — without anyone meaning to — to make the customer say nice things about the team's idea. Once you ask "would you use a product that does X?", you've already corrupted the data: people are wildly optimistic about hypothetical futures, especially when they want to be polite.

The fix is not "ask better hypotheticals." The fix is to stop talking about your idea at all, and instead extract concrete facts about the customer's life as it already exists.

---

## The three rules

From *The Mom Test*. They are called this because if you follow them, even your mom can't lie to you about your business.

1. **Talk about their life, not your idea.** Their problems, workflows, frustrations, and what they currently use. Your idea is irrelevant data here.
2. **Ask about specific events in the past, not opinions about the future.** "When was the last time X happened?" beats "Would you ever do X?" every time.
3. **Talk less, listen more.** If you find yourself pitching, you've already lost the data.

Rule of thumb from Fitzpatrick: customer conversations are bad by default. Your job is to fix them.

---

## The three types of bad data

Most interviews are not silent failures — they generate plausible-sounding noise. Three flavors to recognize and neutralize:

### 1. Compliments

> "That's really cool, I love it."
> "I'd definitely buy that."
> "Sounds amazing — let me know when it launches."

These feel like signal. They are not. They're either polite filler or a stalling tactic to end the meeting. *VCs are wrong more often than right; if a professional's opinion is worthless, what's a random person's worth?*

**How to handle:** Apologize for slipping into pitch mode and immediately deflect back to their world. *"Sorry, I got excited — can I ask how you're handling this today?"* If you find yourself saying "the meeting went really well" back at the office, you probably collected compliments instead of facts.

### 2. Fluff (generics, hypotheticals, future-tense)

> "I usually..."
> "I would definitely..."
> "I might consider..."

People describe themselves as who they want to be, not who they are. Fluff feels concrete because the words are confident, but the content is imaginary.

**How to handle:** Anchor every fluffy claim to a specific past event. *"When was the last time that happened? Can you walk me through it?"* The most dangerous fluff sentence in the world is **"I would definitely buy that."** It sounds like money in the bank. It isn't.

### 3. Ideas (theirs)

When customers start designing your product for you ("you should add X, you should integrate with Y"), it feels validating. It usually isn't. They own the problem; you own the solution. Their feature requests are useful only insofar as they reveal an underlying *motivation*.

**How to handle:** When a customer suggests a feature, dig for the why. *"What would that let you do that you can't do now?"* The motivation is the data; the feature is noise.

---

## Good questions vs. bad questions

A pocket reference. The bad questions invite lies even from people who like you. The good ones force concrete answers.

| Bad question (fluff-inducing) | Good question (anchored in past behavior) |
|---|---|
| "Do you think it's a good idea?" | "How are you dealing with this today?" |
| "Would you buy a product that did X?" | "When's the last time you ran into this problem? Walk me through it." |
| "How much would you pay for X?" | "How much does the problem cost you today (time, money, headcount)?" |
| "What would your dream product do?" | "Why do you bother solving this at all? What's the goal?" |
| "Would you switch if it were better?" | "What have you already tried? Why didn't it work?" |
| "Could you see yourself using this?" | "What are the implications of this problem if you don't solve it?" |

Questions that earn their keep regardless of context:

- **"Talk me through the last time that happened."** Forces story-mode, surfaces the workflow.
- **"What else have you tried?"** If they haven't searched for solutions, they don't actually care.
- **"Where does the money come from?"** B2B essential — surfaces the real budget owner.
- **"Who else should I talk to?"** End every conversation with this. Warm intros snowball.
- **"Is there anything else I should have asked?"** A crutch you'll graduate from, but priceless early.

---

## The premature-zoom trap

A common interview mistake: zooming into a hypothesized problem before confirming it's actually a problem.

> Bad: *"Hi Rob, what are your top problems with marketing your blog?"*
> (Now Rob will helpfully invent some marketing problems, even though his blog isn't a business and marketing isn't a real pain.)
>
> Good: *"Hi Rob, what are the top problems with your blog?"*
> (Rob says he barely posts anymore, and Google Reader is dying. Now you know whether marketing is even on the list.)

Start broad. Don't zoom in until the customer themselves raises the problem you care about. If they don't raise it, that itself is the answer.

Rule of thumb: *Start broad and don't zoom in until you've found a strong signal — both with your whole business and with every conversation.*

---

## Look at the elephant

Most product ideas have **multiple failure points**, not just one. PMs naturally spend time on the most interesting failure point and quietly avoid the scariest one.

Two examples:
- **Teachers in poor schools have a real, urgent overload problem.** But the schools have no budget. The interesting question (do they need help?) is yes; the fatal question (can they pay?) is no.
- **Bar owners would love more weeknight foot traffic and would pay for it.** But this only works if you can build a consumer-side audience first. The customer-side risk is solved; the product-side risk is fatal.

Before any interview round, ask: *what are the 2–3 things that would each separately kill this idea?* Then make sure each interview tests at least one of them. If you only ever interview the customer who wants the thing — and never test the budget-holder, the integrator, or the distribution channel — your data has a hole the size of the elephant.

This connects to the **product risk vs. market risk** distinction:
- **Market risk:** do they want it? will they pay? are there enough of them?
- **Product risk:** can you build it? can you grow it? will they keep using it?

Customer interviews resolve market risk well. They resolve product risk poorly. If your idea is mostly product risk (consumer apps, video games, deep-tech), interviews give you a starting point but you have to build to learn the rest.

---

## Pre-plan your three questions

Before any interview round (formal or casual), write down the **three most important things you want to learn** from this type of person. Not five. Not ten. Three.

Forces:
- Discipline against the questions that are comfortable to ask but don't de-risk anything
- Reusability across interviews — you'll get answers 1–2 from one person, 3 from another, fill in the picture across the cohort
- Better serendipity — when you bump into a dream customer at a conference, you can lead with your most important question instead of asking for a coffee

The three questions evolve as you learn. They are different per persona. They should target the things that would most change your decision if you knew the answer.

---

## Keep it casual

The Meeting Anti-Pattern: relegating every customer conversation to a calendar block. This is expensive (4 hours of overhead per 1 hour of meeting) and signals that you're going to pitch them.

Most early-stage learning is faster as a casual chat than a formal meeting. *"How did you get this gig?"* in a hallway at a conference produces better data than a 30-minute Zoom with an agenda. The customer doesn't know they had a "meeting." They had a conversation about their work.

When the conversation has to be a meeting (senior person, scheduled time):
- **Don't position it as an interview** — *"can I ask you a few questions for a survey"* is weak framing
- **Have a real reason for being there** — not "I'm starting a company" but a specific problem you're trying to understand
- **Show interest in their world, not your product** — for the first 80% of the meeting, they shouldn't even know you have an idea

Rule of thumb: *if the meeting feels formal, you're going to get formal answers — which is to say, polite ones.*

---

## Commitment and advancement

After learning, when you're ready to test whether someone is actually a customer (not just a polite person), you push for **advancement** — moving the relationship to the next concrete step.

The currencies of commitment, in increasing strength:

| Currency | Examples |
|---|---|
| **Time** | A scheduled follow-up with goals; sitting through a wireframe review; using a trial themselves |
| **Reputation** | Intro to peers; intro to a decision-maker (boss, spouse, lawyer); public testimonial |
| **Money** | Letter of intent, deposit, pre-order, paid trial, signed contract |

Bad meeting endings (despite feeling good):
- *"That's so cool, I love it."* — pure compliment, zero data
- *"Let me know when it launches."* — polite stall
- *"There are some people I could intro you to when you're ready."* — fuzzy, name-dropping

Good meeting endings:
- *"What are the next steps?"* — they're owning the advancement
- *"When can we start the trial?"* — concrete and time-bound
- *"When can you come back to talk to the rest of the team?"* — opening doors, real signal in B2B
- *"Can I buy the prototype?"* — the rarest, strongest signal

Rule of thumb: *it's not a real lead until you've given them a concrete chance to reject you.* If every meeting ends with vague positivity and no commitment, your pipeline is full of zombie leads.

---

## Earlyvangelists

Steve Blank's term for the rare customer who is genuinely *desperate* for what you're building. In B2B, they:
1. Have the problem
2. Know they have the problem
3. Have a budget to solve it
4. Have already cobbled together a workaround

In consumer, they're the person who'd front you the money on Kickstarter for a duct-tape prototype.

The signal is **emotion**. There's a meaningful gap between *"yeah, that's a problem"* and *"this is the worst part of my job and I'd pay you right now to fix it."* The first is a polite acknowledgment. The second is your earlyvangelist. Andy Rachleff's stronger version: **"if customers don't want to reach across the table to grab the product from your hands, they aren't desperate — and need is not the same as desperation."**

When you find one, do not let them go. They are how PMF starts.

---

## Decision checklist before any interview round

1. **What are the three things I want to learn?** Written down, not in my head.
2. **What are the multiple failure points of this idea?** Am I testing at least one in this round, or only the comfortable one?
3. **Am I planning to mention my idea?** If yes, why? Can I learn what I need without mentioning it?
4. **What's the past-behavior question that anchors each topic?** "When was the last time..." for each.
5. **What would I have to hear to walk away convinced this idea is wrong?** If I can't name the falsifying answer, I'm not running an experiment — I'm collecting evidence for a verdict I've already reached.
6. **Who's my earlyvangelist target?** And does the recruiting plan reach them, or just the convenient cohort?

If you can't answer 5 in particular, the interview round is a ritual, not research.

---

## Common interview anti-patterns

- **Pitching disguised as a question.** *"We're building X — would you use it?"* Replace with *"How do you handle this today?"*
- **Treating compliments as data.** Saying "everyone loves it" back at the office is the warning sign. Get specific or it didn't happen.
- **Asking about pricing in the abstract.** *"What would you pay?"* is fluff. *"What are you paying today for the workaround?"* is real.
- **Stopping at the first plausible problem.** Drill: *why does that matter? what's the implication? what have you tried?* Many "problems" are not painful enough to motivate a purchase.
- **Researching only the convenient segment.** If your strategy depends on enterprise buyers and you only interview prosumers, you're collecting beautiful data about the wrong people. (See `decision-making/research-methods.md`, "the right segment trap.")
- **Ending without a commitment ask.** Even informal chats can end with *"who else should I talk to?"* — that's an advancement currency.
- **Treating one good interview as PMF signal.** PMF is a cohort question. One desperate user is the start; ten are the bar (`frameworks/03-pre-pmf-validation.md`).
