# PM Evaluation Framework

A working library of frameworks, templates, rubrics, and Claude skills for product managers. Built around the artifacts that actually go up the chain: strategy memos, PRDs, launch checklists, metrics dashboards, kill / continue decisions. Not for case-interview prep.

The material covers the full lifecycle, from framing a problem and running customer discovery through launch readiness and post-launch metrics. Two design choices distinguish it from a generic PM checklist library.

**Discovery is treated as technique, not philosophy.** The repo includes a Mom-Test customer-interview coach (with the rules behind why "would you use this?" produces fluff and "when's the last time that happened?" produces signal), a Lean-Startup-grounded value-hypothesis stress-tester, and substantive framework docs underneath each. The principles are tactical: what to ask, what to ignore, what counts as evidence.

**Every primary skill chains into an adversarial second pass.** The [`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) skill takes the output of any other skill (or any external AI critique, or your own draft) and re-reviews it under a different lens. Most artifacts that "look fine" do so because the first reviewer applied the comfortable lens. The second pass picks a different one. The point matches a working principle from my chief-of-staff setup: critically evaluate AI output, don't defer to it.

The repo organizes around one question: **what does a good PM actually do at each stage of the work, and how do we know?** The [five evaluation criteria](#the-five-evaluation-criteria) below answer it. Everything else (frameworks, decision-making docs, cross-functional traps, rubrics, templates, skills) feeds those five.

---

## Personalize this for your own use

If you forked or cloned this repo, do these steps in order. Each one is concrete — you should be able to copy-paste and run.

1. **Fork the repo and re-clone your fork.** On GitHub, fork `kalyvask/pm-evaluation-framework`, then `git clone git@github.com:<you>/pm-evaluation-framework.git`. Edit [`LICENSE`](LICENSE) to your name and update the intro of this README to reflect your perspective.

2. **Install the Claude skills so they work in every project, not just this repo.** The ten skills under [`.claude/skills/`](.claude/skills/) auto-load when Claude Code is opened *inside this repo*. To make them available everywhere, copy them into your user-level skills directory:
   ```bash
   mkdir -p ~/.claude/skills
   cp -r .claude/skills/* ~/.claude/skills/
   ```
   Restart Claude Code. Run `/skills` to confirm the ten `pm-*` skills are listed. If you only want a subset, copy individual skill folders.

3. **Add your own artifact templates.** Put new templates in [`templates/`](templates/) alongside [`prd-template.md`](templates/prd-template.md), [`decision-memo.md`](templates/decision-memo.md), [`decision-log.md`](templates/decision-log.md), [`launch-criteria.md`](templates/launch-criteria.md), and [`blameless-postmortem.md`](templates/blameless-postmortem.md). Match the existing voice (imperative, section-headed, no jargon) so the skills can find and reuse them.

4. **Customize rubric weights and criteria for your team's bar.** The three rubrics in [`rubrics/`](rubrics/) — [`pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md), [`strategy-memo-rubric.md`](rubrics/strategy-memo-rubric.md), [`product-review-rubric.md`](rubrics/product-review-rubric.md) — are deliberately editable. Re-weight criteria, add team-specific ones (e.g. "addresses regulated-data path"), or replace the five top-level questions in the [The five evaluation criteria](#the-five-evaluation-criteria) section below. The skills cite these files by path, so they pick up your edits automatically.

5. **Extend or override skills with your own voice and style.** To add a new skill: copy [`SKILL.md.tmpl`](SKILL.md.tmpl) into a new folder under `.claude/skills/<your-skill>/SKILL.md` and fill in the front-matter description (this is what Claude pattern-matches against). To change the voice of an existing skill: edit its `SKILL.md` directly — tighten the prose, add your own anti-patterns, or point it at frameworks you added in steps above.

6. **Keep your private material local — it's already gitignored.** [`.gitignore`](.gitignore) already excludes `drafts/`, `local/`, `private/`, `outputs/`, `.cache/`, `*.draft.md`, `*.local.md`, CVs, PDFs, DOCX, and `.env*`. Use these for unredacted notes, in-flight memo drafts, your CV, and any private artifact you want a skill to reason over without committing it. Sanity-check with `git status` before every commit.

7. **Smoke-test that personalization worked.** From inside Claude Code, ask: *"Use the pm-evaluator skill to grade this draft memo: [paste]"* — confirm the skill triggers and cites your edited rubric. Then ask: *"Use pm-framework-selector for [your situation]"* — confirm the skill routes you to the right framework.

---

## How to use this repo

| If you want to... | Start here |
|---|---|
| Pick the right framework for the decision in front of you | [`frameworks/00-overview.md`](frameworks/00-overview.md) |
| Sharpen how you frame a problem before jumping to solutions | [`decision-making/problem-framing.md`](decision-making/problem-framing.md) |
| Think clearly about reversibility before committing | [`decision-making/risk-and-reversibility.md`](decision-making/risk-and-reversibility.md) |
| Decide between user research methods (personas vs. JTBD vs. Kano) | [`decision-making/research-methods.md`](decision-making/research-methods.md) |
| Run a customer-discovery interview that actually produces signal | [`decision-making/customer-interviews.md`](decision-making/customer-interviews.md) |
| Stress-test the value hypothesis behind a product before committing | [`decision-making/value-hypothesis.md`](decision-making/value-hypothesis.md) |
| Argue defensibility honestly — which moat, with what evidence | [`decision-making/competitive-moat.md`](decision-making/competitive-moat.md) |
| Navigate the user-vs-chooser split in enterprise sales | [`decision-making/user-vs-chooser.md`](decision-making/user-vs-chooser.md) |
| Adversarially re-review an existing critique before acting on it | [`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) skill |
| Prioritize a backlog | [`decision-making/prioritization.md`](decision-making/prioritization.md) |
| Define what to measure | [`decision-making/metrics.md`](decision-making/metrics.md) |
| Review the user-facing design layer of a PRD or feature | [`decision-making/behavioral-design.md`](decision-making/behavioral-design.md) |
| Put AI into a product without bolting on a chatbot | [`decision-making/ai-integration.md`](decision-making/ai-integration.md) |
| Work better with engineering | [`cross-functional/engineering-partnership.md`](cross-functional/engineering-partnership.md) |
| Run a launch where some failure is expected | [`cross-functional/failure-management.md`](cross-functional/failure-management.md) |
| Understand how AI is changing the PM role | [`ai-and-pm.md`](ai-and-pm.md) |
| Evaluate a PM's reasoning on a case | [`rubrics/pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md) |
| Evaluate a strategy memo before it goes up the chain | [`rubrics/strategy-memo-rubric.md`](rubrics/strategy-memo-rubric.md) |
| Show up well in a product / exec review | [`rubrics/product-review-rubric.md`](rubrics/product-review-rubric.md) |
| Use a PRD / decision-memo / decision-log / postmortem template | [`templates/`](templates/) |

---

## Claude skills

The repo ships with ten [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills) under `.claude/skills/`. They use the frameworks in this repo as their substrate, and they're organized by where you are in the product lifecycle.

| Stage | Skill | Use when |
|---|---|---|
| **Frame** | [`pm-framework-selector`](.claude/skills/pm-framework-selector/SKILL.md) | You have a decision in front of you and don't know which framework to reach for |
| **Frame / decide** | [`pm-decision-coach`](.claude/skills/pm-decision-coach/SKILL.md) | You want to be walked through a decision: framing → research → prioritization → risk |
| **Discover** | [`pm-customer-interview-coach`](.claude/skills/pm-customer-interview-coach/SKILL.md) | You're prepping or debriefing customer interviews and want them stress-tested against the Mom Test rules |
| **Discover** | [`pm-value-hypothesis-tester`](.claude/skills/pm-value-hypothesis-tester/SKILL.md) | You're about to launch, fundraise, or scale, and you want the underlying what / who / how bet pressure-tested |
| **Build** | [`pm-prd-drafter`](.claude/skills/pm-prd-drafter/SKILL.md) | You're starting a PRD, have a draft to critique, or are stuck on problem / success / scope |
| **Build / Review** | [`pm-design-critic`](.claude/skills/pm-design-critic/SKILL.md) | You have a PRD or design spec drafted and want the user-facing surface critiqued against behavioral and UX principles (defaults, friction, choice architecture, AI surfaces) |
| **Launch** | [`pm-launch-reviewer`](.claude/skills/pm-launch-reviewer/SKILL.md) | You have a launch coming up and want a gate-by-gate pre-flight against a real readiness bar |
| **Measure** | [`pm-metrics-critic`](.claude/skills/pm-metrics-critic/SKILL.md) | You're locking success criteria, debating a North Star, or staring at a dashboard that "looks fine" |
| **Review** | [`pm-evaluator`](.claude/skills/pm-evaluator/SKILL.md) | You want a strategy memo, PRD, or analysis graded against the five-criterion rubric before it goes up |
| **Challenge** | [`pm-red-team`](.claude/skills/pm-red-team/SKILL.md) | You have an existing critique (from another skill, an external AI, or yourself) and want it adversarially re-reviewed before you act on it |

To use them locally, drop the repo in a directory Claude Code can see — the skills will appear automatically. New skills follow the format in [`SKILL.md.tmpl`](SKILL.md.tmpl).

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
