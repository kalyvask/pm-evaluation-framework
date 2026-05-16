# AI integration

Most "AI features" fail not because the model is bad, but because the surface around the model is bolted on. A chatbot at the corner of the screen, a "Powered by AI" banner, a sidebar that asks the user to describe what they want instead of just doing the thing.

This file is the design discipline for putting AI into a product so that it feels like the product got smarter, not so that the product grew a new tab.

The frame: AI is a personalization engine that lives *inside* the existing flow as labels, ranges, suggestions, and pre-fills. The user does not see the model. The user sees the outcome.

---

## The shape question

For any AI feature, the first question is the shape, not the model. Three common shapes:

- **Chatbot.** Conversational front door. User describes what they want; the system responds. Right for open-ended exploration, debugging, or "I don't know what to ask." Wrong for most decision moments — a user at the table choosing a dish does not want a conversation.

- **Inside-flow surfaces.** AI augments the existing UI with labels, ranges, suggestions, pre-filled fields, ranked lists. The user sees the existing product, slightly smarter. Right for almost every decision moment where the user already has a goal in mind.

- **Background.** AI runs invisibly — re-ranking, deduplicating, summarizing, classifying — without surfacing to the user at all. Right when the user wouldn't have a useful opinion on the operation and just wants the result to be better.

Most AI features in mainstream products belong inside the flow or in the background. Chatbots are over-applied because they are easy to ship, not because they are usually the right shape.

**Evaluation question:** for this AI feature, is the chosen shape the one that best serves the user's moment, or the one that's easiest to ship?

---

## The four rules of an AI surface

Any AI surface, whatever its shape, should follow these four rules. Each rule has a corresponding evaluation question.

### Rule 1 — Show confidence when low

An AI output presented as a fact when it's actually an estimate is a lie. The user will discover the lie eventually, and the cost of that discovery is trust, not just the specific output.

When the model is confident, the output can stand alone (no caveats, no asterisks). When the model is uncertain, the surface has to communicate that — through a range (*"850 to 1,150 calories"* not *"1,000 calories"*), through language (*"estimated"*, *"likely"*), or through a fallback (*"using cuisine averages until we learn your patterns"*).

Confidence display does *not* mean putting a percentage on every output. Percentages are noise. The signal is whether the surface reads as a fact or as an estimate.

**Evaluation question:** can a user tell, from the surface alone, when the AI is confident versus when it's guessing?

### Rule 2 — Allow override at the point of decision

The user must be able to disagree with the AI in the moment, at the place where the AI's output is being applied. Not three menus deep. Not on a settings screen. Right where the AI surface lives.

An override that requires the user to navigate away breaks trust. An override that's one tap and visible builds it.

**Evaluation question:** for each AI surface, is the override one tap away, in-context, and visible without scrolling?

### Rule 3 — Fall back gracefully

The model will sometimes be uncertain, fail entirely, or hit a category it doesn't recognize. The design has to specify what happens then. The wrong answer is "block the user." The right answer is usually "category default with a note."

A fallback is not a feature — it's the design floor. If a feature has no fallback design, it has only a happy path, which means it will break for some non-trivial fraction of users in production.

**Evaluation question:** what's the fallback when the model is uncertain or fails? Is it specified, and does it preserve the user's ability to continue the flow?

### Rule 4 — Make the model invisible

The user should see the *outcome*, not the *mechanism*. Phrases like *"our AI thinks..."* or *"based on machine learning..."* are noise. They draw attention to the model, which is the wrong object.

The user cares about the dish recommendation, the calorie estimate, the next-action suggestion. The fact that AI produced it is operationally important and presentationally invisible.

The exception: when the user asks how the system arrived at an output, the explanation should be available. But it lives in the affordance for *how this was generated*, not in the headline copy.

**Evaluation question:** does the AI surface lead with the outcome (the recommendation, the estimate, the suggestion) or with the model? If it leads with the model, rewrite.

---

## AI as personalization, not as chrome

AI features that exist primarily to be visible — to signal that the company is "doing AI" — produce a recognizable failure pattern: the feature ships, generates a marketing moment, and degrades user metrics on the surfaces it touches. This happens when the AI is added as chrome (a sticker on the product) rather than as the personalization engine for an existing decision.

The discipline: AI features should be measurable in the existing user metrics of the surface they touch, not as a separate "AI engagement" KPI. If the AI feature on the recommendation surface doesn't improve the recommendation surface's conversion, retention, or task success, it isn't doing work — regardless of how many users "interact with the AI."

**Evaluation question:** does this AI feature have a measurable effect on the existing user metrics of the surface it touches? Or is it being measured by AI-specific metrics that exist only because the feature exists?

---

## Privacy and trust posture

AI features often need richer data than the rest of the product. Personalization requires history. Estimation requires context. Recommendation requires preferences.

The trust posture is not a feature; it's the precondition for the AI surface to work at all. If users don't trust that the system will use their data well, they will withhold the data, and the model will be worse.

Three rules that should hold for any AI feature:

1. **Default to the smallest amount of user data the surface can work with.** Expand from there based on the user's opt-in.
2. **Be honest about what data is being used.** Not in a legal disclosure — in the surface itself. *"This recommendation uses your last 10 visits"* is design copy, not a legal line.
3. **Give the user a single, visible control** to turn the AI feature off without losing access to the rest of the product. If the user can't turn it off, they won't trust it.

**Evaluation question:** what's the minimum data this AI feature needs? Is the user explicitly told what's being used? Is there a one-tap off switch?

---

## Hybrid UI for enterprise AI

The four rules above assume the AI is part of the surface. They do not address whether the user should be *forced* to use it.

In enterprise products, the answer is almost always no. Two structural reasons:

**Trust takes time.** Enterprise data is the customer's crown jewels — financial records, customer information, intellectual property, security telemetry. A new AI feature that asks the user to delegate decisions over that data starts with negative trust. The user hasn't yet seen the AI succeed at their specific edge cases; they have no basis to defer to it. Forcing them to use the AI before that trust is built produces resistance, not adoption.

**Not every use case is conversational.** Selecting one item from a known list of fifty is not a chat task. Reading a dashboard is not a chat task. Bulk editing a set of records is not a chat task. The user wants to see the surface, point at the thing they want, and act. A chatbot inserted in front of these flows is added friction, not added intelligence.

The design move is a **hybrid landing**. Give the user explicit control over how AI shows up in the product:

- **AI-first.** Land the user on the AI surface (assistant, chat interface) as the primary entry point. Right for use cases where the user wants to *describe* the outcome rather than navigate to it.
- **Traditional.** Land on the existing dashboard or task surface. AI is available as a sidebar or side-pane, invoked when the user reaches for it. Right for routine, high-frequency tasks where the user already knows what they want.
- **Hybrid.** Both surfaces visible at once. The user moves between them based on the moment. Right when use cases span both modes.

The user picks the landing default in settings. The product remembers and serves that default. Power users who want AI everywhere get it. Cautious users who want to do their job the way they did it yesterday get that too. Trust accumulates as the AI demonstrates value, and the user can shift their default over time.

The corollary: when users push back on an AI surface, the resistance is data. It usually means either the trust gap is bigger than the team thought, or the use case the team picked for AI is one users don't want delegated. Both are worth listening to, not engineering around.

**Evaluation question:** can the user choose how AI shows up on the landing page? Is the choice persistent and respected as the default going forward, or is the AI forced regardless of preference?

---

## When AI is the wrong answer

Not every decision in a product is a candidate for AI. Some moments are better served by a deterministic rule, a curated list, or just a static piece of UI. The cost of AI is non-trivial: latency, failure modes, hallucination risk, debugging difficulty, and the chrome problem above.

Use AI when:

- The user's preference is rich enough to benefit from personalization at scale (a recommendation across thousands of options, a summary across hundreds of inputs)
- The decision is judgment-bearing rather than rules-bearing (a fit score across many features, not a binary eligibility check)
- The cost of being wrong is recoverable in-flow (the user can override, retry, or fall back)

Don't use AI when:

- A deterministic rule produces the same answer with lower latency and full reliability (eligibility, validation, calculation)
- The cost of being wrong is high and not recoverable in-flow (legal, medical, financial commitments)
- The user wants exact, not approximate, output (a tax calculation, a transaction record)

The right test: can the AI surface be replaced by a static rule or curated list and still serve the user? If yes, the static version is probably the right answer until the AI demonstrably outperforms it on the existing user metric.

---

## The AI integration checklist

Run this before any AI surface is finalized:

1. **Shape:** is this a chatbot, inside-flow surface, or background process? Is the shape chosen for the user's moment, or for ease of implementation?
2. **Confidence display:** can the user tell when the AI is confident versus when it's guessing, from the surface alone?
3. **Override:** is the override one tap, in-context, and visible without scrolling?
4. **Fallback:** what happens when the model fails or is uncertain? Is it designed, or does the happy path silently break?
5. **Model invisibility:** does the surface lead with the outcome or with the model?
6. **Measurement:** is this feature measurable in the existing user metrics of the surface it touches, not by AI-specific KPIs?
7. **Data posture:** is the user explicitly told what data is used? Is there a one-tap off switch?
8. **Hybrid landing (enterprise):** can the user choose how AI shows up (AI-first, traditional, hybrid), and is that choice respected as the default going forward?
9. **AI vs. static:** would a deterministic rule or curated list produce the same outcome? If yes, why is the AI version worth the cost?

If two or more answers are weak, the AI surface isn't ready. Cut the AI and ship the static version, or close the gaps before launch.
