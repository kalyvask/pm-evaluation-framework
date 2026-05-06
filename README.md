# PM Evaluation Framework

A working library of frameworks, templates, rubrics, and Claude skills for product managers — across the full lifecycle, from framing a problem to launching, measuring, and reviewing the result.

The material is organized around one question: **what does a good PM actually do at each stage of the work, and how do we know?**

It pulls together decision frameworks, PRD and launch templates, evaluation rubrics, and Claude skills that hold up under exec-review pressure on hard product decisions: when to kill a feature, how to read user research that contradicts your strategy, what "MVP" really means, what readiness actually means before a launch, and which metrics tell you whether the strategy is working vs. whether the product is being used.

---

## How to use this repo

| If you want to... | Start here |
|---|---|
| Pick the right framework for the decision in front of you | [`frameworks/00-overview.md`](frameworks/00-overview.md) |
| Sharpen how you frame a problem before jumping to solutions | [`decision-making/problem-framing.md`](decision-making/problem-framing.md) |
| Think clearly about reversibility before committing | [`decision-making/risk-and-reversibility.md`](decision-making/risk-and-reversibility.md) |
| Decide between user research methods (personas vs. JTBD vs. Kano) | [`decision-making/research-methods.md`](decision-making/research-methods.md) |
| Prioritize a backlog | [`decision-making/prioritization.md`](decision-making/prioritization.md) |
| Define what to measure | [`decision-making/metrics.md`](decision-making/metrics.md) |
| Work better with engineering | [`cross-functional/engineering-partnership.md`](cross-functional/engineering-partnership.md) |
| Run a launch where some failure is expected | [`cross-functional/failure-management.md`](cross-functional/failure-management.md) |
| Understand how AI is changing the PM role | [`ai-and-pm.md`](ai-and-pm.md) |
| See recurring product-decision patterns (anonymized) | [`case-patterns/`](case-patterns/) |
| Evaluate a PM's reasoning on a case | [`rubrics/pm-evaluation-rubric.md`](rubrics/pm-evaluation-rubric.md) |
| Evaluate a strategy memo before it goes up the chain | [`rubrics/strategy-memo-rubric.md`](rubrics/strategy-memo-rubric.md) |
| Show up well in a product / exec review | [`rubrics/product-review-rubric.md`](rubrics/product-review-rubric.md) |
| Use a PRD / decision-memo / postmortem template | [`templates/`](templates/) |

---

## Claude skills

The repo ships with seven [Claude Code skills](https://docs.claude.com/en/docs/claude-code/skills) under `.claude/skills/`. They use the frameworks in this repo as their substrate, and they're organized by where you are in the product lifecycle.

| Stage | Skill | Use when |
|---|---|---|
| **Frame** | [`pm-framework-selector`](.claude/skills/pm-framework-selector/SKILL.md) | You have a decision in front of you and don't know which framework to reach for |
| **Frame / decide** | [`pm-decision-coach`](.claude/skills/pm-decision-coach/SKILL.md) | You want to be walked through a decision: framing → research → prioritization → risk |
| **Build** | [`pm-prd-drafter`](.claude/skills/pm-prd-drafter/SKILL.md) | You're starting a PRD, have a draft to critique, or are stuck on problem / success / scope |
| **Launch** | [`pm-launch-reviewer`](.claude/skills/pm-launch-reviewer/SKILL.md) | You have a launch coming up and want a gate-by-gate pre-flight against a real readiness bar |
| **Measure** | [`pm-metrics-critic`](.claude/skills/pm-metrics-critic/SKILL.md) | You're locking success criteria, debating a North Star, or staring at a dashboard that "looks fine" |
| **Review** | [`pm-evaluator`](.claude/skills/pm-evaluator/SKILL.md) | You want a strategy memo, PRD, or analysis graded against the five-criterion rubric before it goes up |
| **Practice** | [`pm-case-discussion`](.claude/skills/pm-case-discussion/SKILL.md) | You want a cold-call case discussion that pushes back and surfaces what you missed |

To use them locally, drop the repo in a directory Claude Code can see — the skills will appear automatically. New skills follow the format in [`SKILL.md.tmpl`](SKILL.md.tmpl).

---

## Configure for your own use

The frameworks, templates, and rubrics are meant to be reused as-is. The case patterns in [`case-patterns/`](case-patterns/) are deliberately anonymized so you can map them onto your own situations.

To make the repo yours:

1. Fork it. Edit [`LICENSE`](LICENSE) to your name, and update this README to reflect your perspective.
2. Add your own anonymized cases to [`case-patterns/`](case-patterns/) using the existing files as a structural template (Setup → What worked → Lessons → When to recognize this pattern).
3. Tune the [`rubrics/`](rubrics/) to your team's bar — the five-criterion rubric is a starting point, not a fixed standard.
4. Extend the Claude skills under `.claude/skills/` by copying [`SKILL.md.tmpl`](SKILL.md.tmpl) and pointing the new skill at your additions.
5. Keep `.env`, local notes, and unredacted case material out of the repo — they're already gitignored.

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
