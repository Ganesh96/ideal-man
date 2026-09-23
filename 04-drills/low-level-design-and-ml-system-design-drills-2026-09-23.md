# Low-Level Design and ML System Design Drills

Use with the [LLD syllabus](../07-question-maps/low-level-design-syllabus-and-cases-2026-09-23.md), [ML case-study map](../07-question-maps/real-world-ml-system-case-studies-2026-09-23.md), and [source batch](../09-source-inbox/2026-09-23-lld-interview-guides-ml-case-studies.md).

## Low-Level Design

1. **LRU cache:** Define the public API, capacity behavior, eviction invariant, data structures, complexity, and thread-safety contract. Test update-on-hit and capacity-one edge cases.
2. **Notification service:** Model channels, user preferences, templates, and delivery attempts. Add provider failure, retry, idempotency, opt-out, and asynchronous workflow without turning every noun into a class.
3. **Tic-Tac-Toe:** Model board, moves, players, game state, and win detection. Protect invariants against invalid/repeated moves; discuss larger boards and alternate win rules.
4. **ATM:** Walk cash withdrawal end-to-end. Identify authorization and dispense boundaries, cash inventory, cancellation, device failure, and the point where financial side effects become irreversible.
5. **BookMyShow:** Hold a seat while checkout is in progress. Resolve two customers selecting the same seat, hold expiry, payment timeout, duplicate callbacks, and reconciliation.
6. **Pattern test:** A notification system adds a new channel. Compare conditional branches, Strategy, and plugin-style registration. Explain when the extra abstraction is justified.
7. **SOLID test:** A class validates a CSV, writes a database row, sends email, and formats an error report. Refactor responsibilities only enough to isolate change and enable useful tests.
8. **UML test:** Draw a sequence diagram for a booking with a timed hold, payment, confirmation, and expiry race. Mark asynchronous callbacks and idempotency keys.

For each, state assumptions, model responsibilities/invariants, implement or pseudocode one vertical slice, add tests, compare a simpler alternative, and explain concurrency/failure behavior. A hypothetical design is not evidence of past work.

## ML/System Design

1. **Fraud scoring:** Define authorization-time feature availability, latency budget, false-positive/false-negative costs, model fallback, delayed labels, and monitoring.
2. **Recommendation:** A ranking change improves clicks but hurts completed purchases. Diagnose objective mismatch, position bias, experiment slices, and guardrail metrics.
3. **Incident assistant:** Separate retrieval quality, context assembly, LLM output, and operator workflow failures. Design grounding evaluation and a safe human approval boundary.
4. **Payment routing:** Optimize authorization success, fees, latency, or some combination? Define hard constraints, fallback routing, duplicate charging protection, and how to evaluate changes.
5. **Airport demand forecasting:** Specify horizon, geographic granularity, prediction uncertainty, downstream action, peak-event evaluation, and fallback when the model is unavailable.
6. **Human-reviewed generation:** Design a workflow where generated copy requires approval before publication. Measure reviewer effort, edit rate, policy violations, and time saved.
7. **Model choice:** Given two models, compare slice-level quality, p95 latency, cost, context limit, privacy, and operational controls. Set ship criteria before selecting.
8. **RAG vs fine-tuning:** Compare freshness, knowledge changes, answer grounding, examples, privacy, training/evaluation cost, and behavior change. State when neither is warranted.
9. **Evaluation drift:** Offline quality is stable but user outcomes decline after launch. Identify distribution shift, logging/label defects, UX changes, and delayed outcomes; propose rollback triggers.
10. **Capacity spike:** A system serves 10x inference traffic. Calculate token/request demand, concurrency, queue budget, admission control, caching eligibility, model tiering, and graceful fallback.

## Answer review rubric

Score each answer from 0–2 on: requirements, correctness/invariants, trade-offs, failure handling, measurement/testing, and clear communication. A 0 means missing or unsupported, 1 means partial, 2 means concrete and justified. Re-answer any section scoring below 2 without looking at notes.
