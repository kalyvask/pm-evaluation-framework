# Finding product-market fit

Most of this repo is for working PMs at established companies. This file is for the case where the product is new, the market is unproven, and the question isn't *how do we ship better*. The question is *should we ship at all, to whom, based on what insight, and how would we know it worked.*

The framework is the Lean Startup synthesis. Product-market fit (PMF) as a term was coined by Andy Rachleff (Wealthfront, Benchmark). The methodology draws from Steve Blank (*The Four Steps to the Epiphany*), Eric Ries (*The Lean Startup*), Geoffrey Moore (*Crossing the Chasm*), Clay Christensen (*The Innovator's Solution*), Howard Marks (the right-and-non-consensus framework from his Oaktree memos), Rob Fitzpatrick (*The Mom Test*), Jake Knapp (*Sprint*), and Scott Cook (the "savor the surprise" principle from his work at Intuit).

This file is the **posture**. The mechanics (value hypothesis, MVP types, validation sequence) live in [`value-hypothesis.md`](value-hypothesis.md). The metrics (Sean Ellis, smile curve, ARC) live in [`../frameworks/03-pre-pmf-validation.md`](../frameworks/03-pre-pmf-validation.md). Read this first; the others operationalize it.

---

## The load-bearing claim: execution doesn't matter

The most uncomfortable claim in the methodology, and the one that defines everything else: **for a brand-new tech startup, success or failure can almost always be traced to the quality of its product-market fit, not its execution.**

The empirical basis: 25-year-olds run billion-dollar companies. They are not managing finance teams well. They are not running customer-success orgs well. They are not negotiating large enterprise contracts well. They are not great at operations at scale. They are great at one thing. They found a market that wanted what they built.

The reframe: a great startup management team is not defined by how well it executes. It is defined by how well it **optimizes its potential PMF.**

Two corollaries:

- When a great team meets a lousy market, the market wins. When a lousy team meets a great market, the market wins. The team is the smaller variable.
- Finding PMF is a **discovery** problem, not an **optimization** problem. The two require opposite processes. Discovery rewards hypothesis-experiment-learn cycles. Optimization rewards execution discipline. Pre-PMF, you are running the wrong play if you are optimizing.

If you accept this claim, three things change about how you spend your time. You stop reading execution-focused PM literature. You stop running OKRs. You stop measuring yourself on velocity. You start measuring yourself on rate of learning.

---

## Insight before product: right and non-consensus

The canonical advice (find a market, identify a problem, build a solution) produces what Howard Marks calls *right and consensus* outcomes. Real but small. Anyone can do it; the returns get arbitraged away.

Outsized outcomes require **right and non-consensus.** In tech, that almost always means starting from a specific insight, typically a technology inflection that just made something newly possible, and then searching for the market that's desperate for what the insight enables.

The principle: **change creates opportunity.** Without an inflection (technology, behavior, regulation), good enough wins and your "10x better" product cannot displace the incumbent. Technology inflections are usually more durable than behavioral or regulatory ones because they are harder to reverse.

The skeptical test for any value hypothesis: *what just changed that makes this newly possible?* If the answer is "nothing, we just think users want it," the bet is right-and-consensus. Acceptable, but not outsized. Calibrate ambition accordingly.

---

## Leap of faith vs. value hypothesis

The single most common discipline failure in early-stage PMs: conflating the leap of faith with the value hypothesis.

- **Leap of faith.** The *one underlying belief* that, if false, makes the entire business dead. Airbnb: "people will sleep in a stranger's home." Wealthfront: "people will let software manage their investments." SpaceX: "reusable rockets meaningfully reduce launch costs." AppDynamics: "enterprises will adopt SaaS for application performance monitoring instead of on-premises software."
- **Value hypothesis.** The bet built on top of the leap of faith. The specific what/who/how you are testing this quarter.

The leap of faith is upstream. It rarely changes. The value hypothesis is downstream. It pivots constantly.

The discipline: **write the leap of faith down separately, on its own line, before you write the value hypothesis.** Then design the smallest experiment that would falsify the leap of faith specifically. Most early-stage MVPs try to test four or five assumptions at once and learn nothing, because the team cannot isolate which assumption broke when the experiment fails.

Ries's definition of an MVP captures this: *the minimum functionality required to prove your leap-of-faith assumption.* Steve Blank's complementary definition: *the smallest feature set that gets a customer to pay for it.* Both are right; pick the one that matches the assumption you are testing.

---

## Need is irrelevant. Desperation is everything.

A real need does not produce a customer. Desperation does.

Desperation has a behavioral signature, not an attitudinal one. The four signals:

1. **The customer pays with little proof.** They don't ask for fifty references. They need to see the product work once, and they buy.
2. **They have tried to build it themselves.** They have a spreadsheet, a script, an intern doing the job manually, an internal tool the engineering team hacked together. The single most reliable signal of desperation in enterprise is a janky internal version of what you are selling.
3. **They are actively frustrated.** They mention the pain by name when asked "what's keeping you up at night?" They have a specific story about how this problem screwed up their last quarter.
4. **They want the solution now.** The first question after a demo is *when can I have it?* Not *can we evaluate in Q3?* Not *can you build feature X first?* The verb tense matters.

The behavioral filter: a customer who only buys after you've added two features they requested was not desperate. Adding features does not create desperation. Desperation precedes features.

If your hypothesized audience is needy but not desperate, **change the audience.** Don't add features to make them desperate. They will not become desperate. Pivot the who.

---

## Iterate on the who, not the what

When an experiment fails (most do), the temptation is to change the product. Almost always wrong. The two distinct moves:

- **Pivot.** Change the who, sometimes the how. Hold the what (the underlying insight) constant.
- **Restart.** Change the what. This is starting over with a new insight.

Four reasons to almost never restart:

1. Adding features doesn't create desperation. If the audience wasn't desperate before, features don't change that.
2. If you don't yet know your ideal customer, you don't know which features to build. You'll build a composite product that satisfies no one fully.
3. Changing the what changes too many variables at once. You can't isolate what caused the failure.
4. Changing the what **obsoletes your insight.** Once your insight is gone, you are competing on execution in a known market: the worst place to compete from.

The vocabulary matters. *Pivot* succeeds often. *Restart* almost never succeeds. Famous restarts that worked (Instagram from Burbn, Slack from Glitch) are outliers. Most restarts fail because the team has already burned cash and learning cycles getting to the moment of restart and now has to start over with less of both.

### The exception: savor the surprise

The one explicit exception, from Scott Cook's work at Intuit. When an experiment produces an **unexpected positive signal** (users using the product for something you didn't design it for, a feature you considered minor getting outsized adoption, a segment you didn't target loving it), drop everything and double down on the surprise. Even if it means changing the what.

The principle: the market knows something you don't. Listen to it. Most successful tech companies look in retrospect like they shipped the original plan, but they didn't. They pivoted (sometimes restarted) when surprises appeared and rewrote the founding story later because it sells better.

Practically: a weekly review pass should ask *what surprised us this week?* before *what are we shipping next week?* The surprises are where the value compounds.

---

## Built to learn, not built to execute

The organizational implication of treating PMF as a discovery problem: the pre-PMF startup is structured to learn, not to deliver against a plan.

What this changes in practice:

- **OKRs are wrong before PMF.** OKRs are a planning tool for known systems. Pre-PMF, the system is unknown. Setting a Q3 OKR for "10,000 active users" is a fake target. You have no basis for the number, and hitting it (or missing it) tells you nothing about whether you're learning.
- **Rate of learning is the metric.** *The most important variable in a startup is the rate at which you learn* (Ries). Measure: how many falsifiable experiments did the team run this month, what did each one teach you, what changed in the value hypothesis as a result.
- **Hedging is the enemy.** Picking three lead pins in parallel because you can't decide. Building three features into the MVP "just in case." Running three channels because none of them is working. Hedging burns cycles. Pick one. If wrong, pivot, but pick one again.
- **Concentrate after signal.** When one experiment, one channel, or one segment shows signal, drop the others and concentrate. Most teams over-spread their bets *after* signal emerges, keeping the things that aren't working "in case they turn around." The cost of slightly under-funding a winner is large (give up compounding upside). The cost of slightly over-funding a fluke is small (find out and stop). See [`prioritization.md`](prioritization.md) § "Concentration after signal" for the full pattern.

---

## Distractions to finding PMF

A canonical list of pre-PMF activities that look productive and aren't. Each one is a post-PMF move done too early.

1. **Trying to accelerate growth.** Growth amplifies whatever exists. If the value hypothesis isn't validated, growth amplifies waste, churn, and confusion. Growth-hypothesis work belongs after value-hypothesis validation, not before.
2. **Worrying about competition.** Before PMF, your problem is customer indifference, not competitors. The company with desperate customers learns faster than the company chasing the leader. Compete on rate of learning, not on feature parity.
3. **Involving a corporate partner.** Pre-PMF partnerships consume cycles to negotiate, deliver against, and report on, none of which build PMF. After PMF they can be growth multipliers; before, they are a tax.
4. **Building barriers to entry.** Pre-PMF, you don't have anything to defend yet. Time spent on patents, exclusive contracts, or moat construction is time not spent finding the desperate customer. Moats build naturally as PMF compounds; they cannot be manufactured upfront.
5. **Building brand.** Brand is built through customer love, not through agencies. Pre-PMF, you have no love to amplify. Brand work converts to ROI only after PMF.
6. **Maximizing margins.** Pre-PMF, you should be willing to absorb negative margins to learn. The cost of a unit of learning is the real currency.
7. **Enabling scale.** Scaling infrastructure, scaling the team, scaling the sales motion: all are post-PMF moves. Scaling prematurely is the canonical way pre-PMF startups die. (Steve Blank: "the number-one cause of startup death is premature scaling.")

A useful sanity test: if a meeting on your calendar would matter in the world where you have already found PMF and are growing fast, hold it. If a meeting on your calendar would only matter *if* you found PMF, hold it. If a meeting on your calendar is about something you would do *whether or not* PMF is found, cancel it. Most of the list above is in the third category.

---

## The success pattern

Almost every successful tech company followed this path, but most followed it by accident. The deliberate version:

1. **Recognize an inflection point** (technology, behavior, regulation) that makes something newly possible.
2. **State the leap of faith** explicitly. One sentence. The one belief that must be true.
3. **Build the value hypothesis** (what/who/how) on top, with a specific desperate lead pin (segment).
4. **Run the validation sequence:** problem (Mom Test interviews) → implementation (design sprint) → product (MVP). Each step gates the next.
5. **Iterate on the who** when experiments fail. Hold the what. Pivot, don't restart, unless the insight itself is wrong.
6. **Savor surprises** when they appear. Double down on the unexpected signal.
7. **Measure PMF by behavior**, not by intent. Word of mouth, organic growth, sales yield >1 in B2B. Survey-based metrics (NPS, "would you be disappointed?") are directional only.
8. **Once PMF is confirmed, switch modes.** Value-hypothesis discipline gives way to growth-hypothesis discipline. The organization built to learn rebuilds as the organization built to scale. Different game, different design.

The probability of success is a function of the quality of your insight, the rate at which you learn, and luck. The methodology improves the first two. The third is yours to find.

---

## When this file applies

Use this file when:

- You're pre-PMF and the next thing you need is the posture, not another framework
- You're a working PM at an established company launching a new product (not a feature) that needs PMF discipline rather than execution discipline
- You're advising a founder and want to ground the conversation in the canonical framework

Don't use this file when:

- The product already has confirmed PMF. The post-PMF playbook is different. Use the rest of this repo.
- The work is a feature inside an existing product with known PMF. Use [`value-hypothesis.md`](value-hypothesis.md) for the bet-level discipline and the rest of the repo for execution.
- The work is a pure execution problem (launch readiness, exec communication, sales motion design) on a product that already works. Use the relevant working-PM files.

The hardest line to hold: knowing whether you're pre- or post-PMF on your *current* product. Many companies have PMF on one product line and are pre-PMF on a new line being launched alongside it. The discipline is different for each. Apply this file to the pre-PMF line. Apply the rest of the repo to the post-PMF line.
