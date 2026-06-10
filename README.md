# PM Evaluation Framework

A working library of frameworks, templates, rubrics, and Claude skills for product managers. Built around the artifacts that actually go up the chain: strategy memos, PRDs, launch checklists, metrics dashboards, kill / continue decisions. Not for case-interview prep.

The material covers the full lifecycle, from framing a problem and running customer discovery through launch readiness and post-launch metrics. Two design choices distinguish it from a generic PM checklist library.

**Discovery is treated as technique, not philosophy.** The repo includes a Mom-Test customer-interview coach (with the rules behind why "would you use this?" produces fluff and "when's the last time that happened?" produces signal), a Lean-Startup-grounded value-hypothesis stress-tester, and substantive framework docs underneath each. The principles are tactical: what to ask, what to ignore, what counts as evidence.

**Every primary skill chains into an adversarial second pass.** The [`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) skill takes the output of any other skill (or any external AI critique, or your own draft) and re-reviews it under a different lens. Most artifacts that "look fine" do so because the first reviewer applied the comfortable lens. The second pass picks a different one. The point matches a working principle from my chief-of-staff setup: critically evaluate AI output, don't defer to it.

The repo organizes around one question: **what does a good PM actually do at each stage of the work, and how do we know?** The [five evaluation criteria](#the-five-evaluation-criteria) below answer it. Everything else (frameworks, decision-making docs, cross-functional traps, rubrics, templates, skills) feeds those five.

For recent additions, see [`CHANGELOG.md`](CHANGELOG.md).

---

## Personalize this for your own use

If you forked or cloned this repo, do these steps in order. Each one is concrete — you should be able to copy-paste and run.

1. **Fork the repo and re-clone your fork.** On GitHub, fork `kalyvask/pm-evaluation-framework`, then `git clone git@github.com:<you>/pm-evaluation-framework.git`. Edit [`LICENSE`](LICENSE) to your name and update the intro of this README to reflect your perspective.

2. **Install the Claude skills so they work in every project, not just this repo.** The twenty-three skills under [`.claude/skills/`](.claude/skills/) auto-load when Claude Code is opened *inside this repo*. To make them available everywhere, copy them into your user-level skills directory:
   ```bash
   mkdir -p ~/.claude/skills
   cp -r .claude/skills/* ~/.claude/skills/
   ```
   Restart Claude Code. Run `/skills` to confirm the twenty-three `pm-*` skills are listed. If you only want a subset, copy individual skill folders.

3. **Add your own artifact templates.** Put new templates in [`templates/`](templates/) alongside [`prd-template.md`](templates/prd-template.md), [`decision-memo.md`](templates/decision-memo.md), [`decision-log.md`](templates/decision-log.md), [`launch-criteria.md`](templates/launch-criteria.md), and [`blameless-postmortem.md`](templates/blameless-postmortem.md). Match the existing voice (imperative, section-headed, no jargon) so the skills can find and reuse them.

4. **Customize rubric weights and criteria for your team's bar.** The three rubrics in [`rubrics/`](rubrics/) — [`pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md), [`strategy-memo-rubric.md`](rubrics/strategy-memo-rubric.md), [`product-review-rubric.md`](rubrics/product-review-rubric.md) — are deliberately editable. Re-weight criteria, add team-specific ones (e.g. "addresses regulated-data path"), or replace the five top-level questions in the [The five evaluation criteria](#the-five-evaluation-criteria) section below. The skills cite these files by path, so they pick up your edits automatically.

5. **Extend or override skills with your own voice and style.** To add a new skill: copy [`SKILL.md.tmpl`](SKILL.md.tmpl) into a new folder under `.claude/skills/<your-skill>/SKILL.md` and fill in the front-matter description (this is what Claude pattern-matches against). To change the voice of an existing skill: edit its `SKILL.md` directly — tighten the prose, add your own anti-patterns, or point it at frameworks you added in steps above.

6. **Keep your private material local — it's already gitignored.** [`.gitignore`](.gitignore) already excludes `drafts/`, `local/`, `private/`, `outputs/`, `.cache/`, `*.draft.md`, `*.local.md`, CVs, PDFs, DOCX, and `.env*`. Use these for unredacted notes, in-flight memo drafts, your CV, and any private artifact you want a skill to reason over without committing it. Sanity-check with `git status` before every commit.

7. **Smoke-test that personalization worked.** From inside Claude Code, ask: *"Use the pm-evaluator skill to grade this draft memo: [paste]"* — confirm the skill triggers and cites your edited rubric. Then ask: *"Use pm-framework-selector for [your situation]"* — confirm the skill routes you to the right framework.

---

## How to use this repo

Organized by where you are in the product cycle. Pick the section that matches what you're doing right now.

### Frame & Decide

| If you want to... | Start here |
|---|---|
| Pick the right framework for the decision in front of you | [`frameworks/00-overview.md`](frameworks/00-overview.md) |
| Sharpen how you frame a problem before jumping to solutions | [`decision-making/problem-framing.md`](decision-making/problem-framing.md) |
| Reason from first principles without overusing it | [`decision-making/first-principles-thinking.md`](decision-making/first-principles-thinking.md) |
| Think clearly about reversibility before committing | [`decision-making/risk-and-reversibility.md`](decision-making/risk-and-reversibility.md) |

### Discover & Validate

| If you want to... | Start here |
|---|---|
| Decide between user research methods (personas vs. JTBD vs. Kano) | [`decision-making/research-methods.md`](decision-making/research-methods.md) |
| Run a customer-discovery interview that actually produces signal | [`decision-making/customer-interviews.md`](decision-making/customer-interviews.md) |
| Stress-test the value hypothesis behind a product before committing | [`decision-making/value-hypothesis.md`](decision-making/value-hypothesis.md) |
| Find product-market fit on a new product or startup (posture, not just framework) | [`decision-making/finding-pmf.md`](decision-making/finding-pmf.md) |
| Implement an explicit new-product process that maximizes the probability of PMF | [`frameworks/06-product-process-for-pmf.md`](frameworks/06-product-process-for-pmf.md) |
| Argue defensibility honestly — which moat, with what evidence | [`decision-making/competitive-moat.md`](decision-making/competitive-moat.md) |
| Navigate the user-vs-chooser split in enterprise sales | [`decision-making/user-vs-chooser.md`](decision-making/user-vs-chooser.md) |

### Build & Ship

| If you want to... | Start here |
|---|---|
| Use a PRD / decision-memo / decision-log / postmortem template | [`templates/`](templates/) |
| Review the user-facing design layer of a PRD or feature | [`decision-making/behavioral-design.md`](decision-making/behavioral-design.md) |
| Put AI into a product without bolting on a chatbot | [`decision-making/ai-integration.md`](decision-making/ai-integration.md) |
| Sharpen positioning and the value proposition | [`decision-making/positioning-and-value-prop.md`](decision-making/positioning-and-value-prop.md) |

### Measure & Grow

| If you want to... | Start here |
|---|---|
| Prioritize a backlog | [`decision-making/prioritization.md`](decision-making/prioritization.md) |
| Define what to measure | [`decision-making/metrics.md`](decision-making/metrics.md) |
| Identify the aha moment and design the path to it | [`decision-making/activation.md`](decision-making/activation.md) |
| Critique an activation or conversion funnel against the right model | [`decision-making/conversion.md`](decision-making/conversion.md) |

### Cross-functional

| If you want to... | Start here |
|---|---|
| Work better with engineering | [`cross-functional/engineering-partnership.md`](cross-functional/engineering-partnership.md) |
| Align stakeholders before a decision goes up the chain | [`cross-functional/stakeholder-alignment.md`](cross-functional/stakeholder-alignment.md) |
| Run a launch where some failure is expected | [`cross-functional/failure-management.md`](cross-functional/failure-management.md) |

### AI and the PM

| If you want to... | Start here |
|---|---|
| Understand how AI is changing the PM role | [`ai-and-pm.md`](ai-and-pm.md) |
| Use AI well as a working PM (prompt principles, anti-patterns, hallucination handling) | [`decision-making/ai-craft-for-pms.md`](decision-making/ai-craft-for-pms.md) |
| Reusable AI prompts for common PM artifacts (interviews, PRDs, PR/FAQ, competitive monitoring) | [`templates/pm-prompt-library.md`](templates/pm-prompt-library.md) |

### PM craft and career

| If you want to... | Start here |
|---|---|
| Understand what separates a good PM from an average one | [`what-makes-a-good-pm.md`](what-makes-a-good-pm.md) |
| Manage your PM career deliberately (networking, getting into the room, performing in interviews, internal moves) | [`what-makes-a-good-pm.md`](what-makes-a-good-pm.md) § Career craft |

### Rubrics, review, and operate

| If you want to... | Start here |
|---|---|
| Adversarially re-review an existing critique before acting on it | [`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) skill |
| Evaluate a PM's reasoning on a case | [`rubrics/pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md) |
| Evaluate a strategy memo before it goes up the chain | [`rubrics/strategy-memo-rubric.md`](rubrics/strategy-memo-rubric.md) |
| Show up well in a product / exec review | [`rubrics/product-review-rubric.md`](rubrics/product-review-rubric.md) |
| Turn the framework into a daily PM agent partner (morning briefs, meeting prep, weekly review) | [Operate-stage setup](#operate-stage-setup-the-agent-partner-layer) |

---

## Reading paths

Three reading paths depending on where you are. The "How to use this repo" table above is the lookup layer; the paths below are the linear-reading layer.

### If you're finding PMF

The bulk of this repo is calibrated for working PMs at established companies: exec reviews, strategy memos, launch reviews, status updates, dashboards. If you're a founder or an early-stage PM pre-PMF, that calibration is wrong for you. Read these in order instead:

1. **[`decision-making/finding-pmf.md`](decision-making/finding-pmf.md)** — the posture. Why execution doesn't matter pre-PMF, right-and-non-consensus, leap of faith vs. value hypothesis, the canonical distractions list, savor the surprise.
2. **[`frameworks/06-product-process-for-pmf.md`](frameworks/06-product-process-for-pmf.md)** — the spine. The eight-step process from insight to validated PMF, the counterintuitive doctrine, build-to-learn vs build-to-execute, and the financing milestones mapped to PMF stages.
3. **[`decision-making/value-hypothesis.md`](decision-making/value-hypothesis.md)** — the mechanics. What/who/how, validation sequence, MVP types, pivot vs. restart, common failures.
4. **[`decision-making/customer-interviews.md`](decision-making/customer-interviews.md)** — the technique. Mom Test rules for problem-validation interviews.
5. **[`frameworks/03-pre-pmf-validation.md`](frameworks/03-pre-pmf-validation.md)** — the measurement. Sean Ellis, 10 happy users, smile curve, ARC framework, GTM checklist.
6. **[`pm-pmf-coach`](.claude/skills/pm-pmf-coach/SKILL.md) skill** — the operationalization. Walks you through a specific bet end-to-end: leap of faith → value hypothesis → experiment design → interpretation → pivot decision → distractions check.

Most of the rest of this repo (PRD drafting, launch readiness, exec communication) is calibrated for the post-PMF stage. Run the files above first. Most of the post-PMF content is a distraction pre-PMF.

The line between pre-PMF and post-PMF often runs through a single company. A team can have PMF on its core product and be pre-PMF on a new product line being launched alongside. The discipline is different for each. Apply the founder-reading-path above to the pre-PMF line; apply the rest of the repo to the post-PMF line.

### If you're a working PM at a fast-growing company

The default audience for this repo. The most load-bearing files for the daily work:

1. **[`what-makes-a-good-pm.md`](what-makes-a-good-pm.md)** — the posture. What separates a good PM from average, plus the career-craft section for navigating internal moves and the next role.
2. **[`decision-making/problem-framing.md`](decision-making/problem-framing.md)** — sharpen problem statements before any PRD; the most common failure mode of working-PM artifacts.
3. **[`decision-making/prioritization.md`](decision-making/prioritization.md)** — the prioritization frameworks plus the override-axis sequencing for when user-demand ranking is wrong.
4. **[`decision-making/metrics.md`](decision-making/metrics.md)** plus **[`decision-making/activation.md`](decision-making/activation.md)** — what to measure and how to instrument the path to aha, including the day-1 / day-10 / day-30 sticky-moment tension.
5. **[`pm-progress-auditor`](.claude/skills/pm-progress-auditor/SKILL.md) skill** — audit every status update for credibility leaks before sending. Goodwill is a finite budget.
6. **[`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) skill** — adversarial second pass on any high-stakes artifact heading up the chain.

For non-trivial cross-functional moments, also read [`cross-functional/engineering-partnership.md`](cross-functional/engineering-partnership.md), [`cross-functional/stakeholder-alignment.md`](cross-functional/stakeholder-alignment.md), and [`cross-functional/failure-management.md`](cross-functional/failure-management.md).

### If you're prepping for AI PM interviews

The most directly relevant files for AI PM interview preparation:

1. **[`ai-and-pm.md`](ai-and-pm.md)** — how AI is changing what PMs are hired for. Evals replace the PRD; ship-to-learn criteria; PMs read raw feedback themselves.
2. **[`decision-making/ai-integration.md`](decision-making/ai-integration.md)** — designing AI surfaces in products (shape, confidence, override, fallback, model-invisibility).
3. **[`decision-making/ai-craft-for-pms.md`](decision-making/ai-craft-for-pms.md)** — how PMs personally use AI well: prompt principles, anti-patterns, AI/human decision matrix, hallucination handling.
4. **[`decision-making/first-principles-thinking.md`](decision-making/first-principles-thinking.md)** — the working-PM use of first principles, calibrated to prevent over-application. Useful framing when interviewers probe "how would you approach this."
5. **[`decision-making/research-methods.md`](decision-making/research-methods.md)** § "Right-sizing exploration to stakes" — the high-agency answer to research-scope questions in case interviews.
6. **[`what-makes-a-good-pm.md`](what-makes-a-good-pm.md)** § "Career craft" — networking, three interview signals (communication / agency / authentic enthusiasm), company-over-title strategy.

The skills `pm-pmf-coach`, `pm-progress-auditor`, and `pm-red-team` are also worth invoking on mock-interview answers to pressure-test them before the real round.

---

## Claude skills

The repo ships with twenty-three [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills) under `.claude/skills/`. They use the frameworks in this repo as their substrate, and they're organized by where you are in the product lifecycle.

Sixteen of them are **reactive** — invoke when you need critique on a specific artifact or decision. The other seven are **operate-stage** skills that turn the framework into a daily PM partner: morning brief, meeting prep, meeting debrief, weekly review, inbox triage, stakeholder tracker, and the context loader they all chain to. The operate-stage skills read from a `pm-state/` folder you maintain (see below).

| Stage | Skill | Use when |
|---|---|---|
| **Frame** | [`pm-framework-selector`](.claude/skills/pm-framework-selector/SKILL.md) | You have a decision in front of you and don't know which framework to reach for |
| **Frame / decide** | [`pm-decision-coach`](.claude/skills/pm-decision-coach/SKILL.md) | You want to be walked through a decision: framing → research → prioritization → risk |
| **Frame / decide** | [`pm-design-process-router`](.claude/skills/pm-design-process-router/SKILL.md) | You're scoping a feature and need to decide whether it runs through the full Research → PRD → Concept → Detailed → Code pipeline or the Express Lane (verbal sign-off, no Figma). Routes by scope (XS/S/M/L/XL) with moderators for novelty, reversibility, and visibility |
| **Discover** | [`pm-customer-interview-coach`](.claude/skills/pm-customer-interview-coach/SKILL.md) | You're prepping or debriefing customer interviews and want them stress-tested against the Mom Test rules |
| **Discover** | [`pm-value-hypothesis-tester`](.claude/skills/pm-value-hypothesis-tester/SKILL.md) | You're about to launch, fundraise, or scale, and you want the underlying what / who / how bet pressure-tested |
| **Found / Pre-PMF** | [`pm-pmf-coach`](.claude/skills/pm-pmf-coach/SKILL.md) | You're pre-PMF and want to be walked through finding it: surface the leap of faith → build the value hypothesis → design the smallest falsifying experiment → interpret the result → pivot the who, pivot the how, or restart the what → distractions check |
| **Build** | [`pm-prd-drafter`](.claude/skills/pm-prd-drafter/SKILL.md) | You're starting a PRD, have a draft to critique, or are stuck on problem / success / scope |
| **Build / Review** | [`pm-design-critic`](.claude/skills/pm-design-critic/SKILL.md) | You have a PRD or design spec drafted and want the user-facing surface critiqued against behavioral and UX principles (defaults, friction, choice architecture, AI surfaces) |
| **Build / Review** | [`pm-persona-stress-tester`](.claude/skills/pm-persona-stress-tester/SKILL.md) | You have a design or flow and want it walked through step-by-step from a specific persona's point of view — what they see, think, expect, and where they bounce. 10-minute usability audit before scheduling real user research |
| **Launch** | [`pm-launch-reviewer`](.claude/skills/pm-launch-reviewer/SKILL.md) | You have a launch coming up and want a gate-by-gate pre-flight against a real readiness bar |
| **Measure** | [`pm-north-star-selector`](.claude/skills/pm-north-star-selector/SKILL.md) | You're picking *one* North Star and weighing simple behavioral (MAU/DAU) vs. value-delivered vs. revenue. Forces the explainability, lead/lag, gameability comparison most teams skip |
| **Measure** | [`pm-metrics-critic`](.claude/skills/pm-metrics-critic/SKILL.md) | You're locking success criteria, debating a North Star, or staring at a dashboard that "looks fine" |
| **Measure / Grow** | [`pm-funnel-critic`](.claude/skills/pm-funnel-critic/SKILL.md) | You have an activation funnel, conversion funnel, paywall, or trial design and want the funnel-layer logic pressure-tested (binding stage, drop-off driver, model fit) |
| **Review** | [`pm-progress-auditor`](.claude/skills/pm-progress-auditor/SKILL.md) | You're about to send a status update, exec review, board email, or dashboard callout and want every claim pressure-tested for credibility leaks (overstated verbs, cherry-picked windows, vanity-metric-as-validation, "on track" with no threshold) |
| **Review** | [`pm-evaluator`](.claude/skills/pm-evaluator/SKILL.md) | You want a strategy memo, PRD, or analysis graded against the five-criterion rubric before it goes up |
| **Challenge** | [`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) | You have an existing critique (from another skill, an external AI, or yourself) and want it adversarially re-reviewed before you act on it |
| **Operate** | [`pm-context-loader`](.claude/skills/pm-context-loader/SKILL.md) | You're starting a PM workflow and need the agent to load your `pm-state/` (personal style, active projects, stakeholders) before doing anything else. Most operate-stage skills chain to this first. |
| **Operate** | [`pm-morning-brief`](.claude/skills/pm-morning-brief/SKILL.md) | First thing in the morning. Pulls calendar, inbox, project todos, and yesterday's transcripts; surfaces the top 3 today plus slipped commitments. Writes to `pm-state/inbox/` |
| **Operate** | [`pm-meeting-prep`](.claude/skills/pm-meeting-prep/SKILL.md) | Before a meeting that matters. Pulls attendees, prior transcripts, project state, stakeholder context; drafts a one-page brief including the question you don't want asked |
| **Operate** | [`pm-meeting-debrief`](.claude/skills/pm-meeting-debrief/SKILL.md) | Right after a meeting. Extracts commitments and decisions from a Granola transcript, drafts follow-ups, proposes writes to project todos and decisions files |
| **Operate** | [`pm-inbox-triage`](.claude/skills/pm-inbox-triage/SKILL.md) | When the inbox is backed up. Classifies threads, drafts replies for the substantive ones, surfaces stale threads where you're awaiting or being awaited |
| **Operate** | [`pm-weekly-review`](.claude/skills/pm-weekly-review/SKILL.md) | Friday afternoon. What got done, what slipped, what's hanging, what to renegotiate. Catches the patterns the daily brief misses |
| **Operate** | [`pm-stakeholder-tracker`](.claude/skills/pm-stakeholder-tracker/SKILL.md) | Weekly or before any high-stakes push. Who's going cold, who has open commitments hanging, who needs proactive attention |

To use them locally, drop the repo in a directory Claude Code can see — the skills will appear automatically. New skills follow the format in [`SKILL.md.tmpl`](SKILL.md.tmpl).

### Operate-stage setup (the agent partner layer)

The seven operate-stage skills (morning brief, meeting prep, meeting debrief, inbox triage, weekly review, stakeholder tracker, context loader) read from a `pm-state/` folder you maintain. This is what turns the reactive skill set into a daily PM agent partner.

To set up `pm-state/`:

1. Pick a location. Default: `~/pm-state/`. If you want it synced (recommended), use a cloud-synced path like `~/OneDrive/Documents/pm-state/` and point the skills at that path. The operate-stage skills currently reference `C:/Users/alexa/OneDrive/Documents/GSB/pm-state/`; fork the repo and update the path for your install.
2. Scaffold the structure outside this repo. The folder layout is:
   - `you.md` — personal PM context (style, role, active projects, cross-project stakeholders). The agent reads this at the start of every PM session.
   - `INSTRUCTIONS.md` — overview of the folder for the agent and any human reader
   - `stakeholders.md` — global cross-project stakeholder list
   - `decisions-log.md` — cross-project decisions worth remembering
   - `lessons.md` — cross-project lessons learned
   - `inbox/` — where the agent writes daily and weekly briefs (e.g. `2026-05-18-morning-brief.md`)
   - `projects/_template/` — copy this when starting a new project
   - `projects/<name>/` — one folder per active project, containing `status.md`, `decisions.md`, `open-questions.md`, `stakeholders.md`, `todos.md`
3. Fill in `you.md`. This is the single most important file — the agent reads it at the start of every PM session.
4. Populate one or two active projects. Don't try to capture every project on day one; start with the two that matter most this week.
5. (Optional) Schedule the morning brief and weekly review as recurring jobs so they run automatically (e.g., 7:30am weekdays for the morning brief, 4pm Fridays for the weekly review).

The maintenance contract: 5 minutes a day updating `todos.md` and `decisions.md` for the active project, 15 minutes a week refreshing `you.md` and stakeholder lists. If you stop maintaining the state, the agent's outputs go stale and you stop trusting them. The maintenance is what makes the partnership work.

The `pm-state/` folder itself is **not** checked into this repo. It contains personal context, stakeholder names, and decision history that should stay private. Each user maintains their own outside the repo.

### Relationship with chief-of-staff

The seven operate-stage skills run standalone in any Claude Code session that can see a `pm-state/` folder. If you want a full runtime around them, with Gmail and Google Calendar integration, a JSONL work queue with provenance, a permission engine with tier checks, scheduled overnight `/email-triage` and `/calendar-prep` jobs, conformance audits encoded as code, and a typed-link graph over stakeholders and decisions, see [chief-of-staff](https://github.com/kalyvask/chief-of-staff). It is the runtime layer that wires this skill library (and four specialist subagents of its own) into a daily PM loop.

The split: pm-evaluation-framework is the public library you can drop into any repo. chief-of-staff is the personal runtime you install once.

---

## The five evaluation criteria

Every framework in this repo ladders up to five questions that travel with you across any product decision:

1. **Did you identify the right problem before jumping to solutions?**
2. **Did you apply a framework to remove bias and surface stakeholder perspectives?**
3. **Did you account for bundle effects and the full user journey** — including procurement, admin, and downstream teams?
4. **Did you define what success and failure look like upfront?**
5. **Did you prototype or validate before committing real resources?**

The full rubric is in [`rubrics/pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md).

---

## License

MIT. Use it, fork it, ship better products.
