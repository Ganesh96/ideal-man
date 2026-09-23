# SE II Interview Answer Templates and Cheat Sheets

Use these as retrieval scaffolds, not scripts to recite. State assumptions; revise when new facts change the answer.

## Coding interview: CLARIFY

- **C — Clarify:** input/output, constraints, edge cases, allowed assumptions.
- **L — Lay out examples:** normal, boundary, duplicate/empty/failure.
- **A — Approach:** baseline first, then optimize around repeated work or an invariant.
- **R — Reason:** explain why the invariant/algorithm is correct.
- **I — Implement:** write executable code and narrate meaningful decisions.
- **F — Falsify/test:** trace examples and adversarial cases; fix issues aloud.
- **Y — Yield complexity:** time/space, limits, follow-up change.

Useful phrases:
- “I’ll confirm the contract and constraints before choosing a data structure.”
- “The simple solution is …; it costs … because …”
- “The repeated work is …, so I can maintain … as an invariant.”
- “Let me trace this input to check the boundary case.”
- “This change preserves the invariant but costs …”

If stuck: reduce to an example → brute force → find repeated work → name needed operations → choose a pattern → test its invariant. In practice, request a hint after a bounded effort. In an interview, state uncertainty and your next experiment.

## System design: SCOPE → SHAPE → STRESS

### Scope
Users/use cases; exclusions; correctness invariants; latency/freshness, availability, retention, security, cost; what “scale” means (users, requests/sec, bytes, concurrency, bursts, regions).

### Shape a baseline
Estimate orders of magnitude and show assumptions; define APIs/data; sketch the smallest viable architecture; trace read/write paths; identify sync vs async work and source of truth; select storage for access patterns and invariants; state first bottleneck.

### Stress and revise
Deep-dive the two highest-risk components; walk partial failure, duplicate request, overload and recovery; add only justified scaling mechanisms; name SLOs/metrics; state operational/security costs and the constraint that would change your choice.

### 45-minute pacing cue
- 0–5: scope and invariants.
- 5–10: load estimate, API/data.
- 10–20: baseline and request flows.
- 20–35: bottleneck and two deep dives.
- 35–42: failures, operations, security/cost.
- 42–45: recap, trade-offs, open questions.

Adapt to the interviewer. Do not sacrifice a correctness invariant to finish a diagram.

## Low-level design: USE → MODEL → COLLABORATE → TEST

1. State use cases and non-goals.
2. Identify entities/value objects and invariants.
3. Assign responsibilities; add interfaces at real change/test boundaries.
4. Walk normal, failure and concurrency flows.
5. Implement one vertical slice.
6. Test domain rules and collaborators.
7. Explain extension points, complexity, lifecycle, and what stayed simple.

## Behavioral: STAR-L + evidence

- **Situation:** concise context and stakes.
- **Task:** your responsibility and success criteria.
- **Actions:** what you did, why, alternatives/dead ends, collaboration and trade-offs.
- **Result:** measured outcome if known; label estimates and attribution.
- **Learning:** what you would repeat/change.

Prepare evidence: sequence, scope, stakeholders, your contribution, alternatives, result source, limitations. Be truthful; do not invent scale or metrics.

## Situational: FRAME

- **F — Frame** goal, stakeholders, constraints and unknowns.
- **R — Risks** to users, correctness, security, reliability and deadlines.
- **A — Alternatives** including safe short-term action and longer-term fix.
- **M — Make and communicate** the decision, ownership, escalation and rollback/guardrail.
- **E — Evaluate** with tests/metrics, update stakeholders, capture learning.

For incidents, protect users/data and establish facts before speculating. For disagreement, identify the shared goal, bring evidence, run a bounded test when useful, decide ownership, and commit.

## Technical fact answer: D-M-E

- **Definition:** one precise sentence.
- **Mechanism:** how it works and what it guarantees.
- **Example/trade-off:** where it helps, cost/failure, and when it is a poor fit.

Example — idempotency: “An operation is idempotent when repeating it has the same intended effect as performing it once. A payment API can persist a client key with the request/result so a retry after timeout returns the original outcome instead of charging again. The key needs a scope, retention window and request binding; this does not make arbitrary side effects exactly-once.”

## Debugging/code review

1. Reproduce; define expected vs observed.
2. Narrow to the smallest failing input/path.
3. Form a testable hypothesis; inspect code, logs/traces and data.
4. Make the smallest safe change and add a regression test.
5. Verify correctness/performance; describe rollback/monitoring.
6. State remaining uncertainty.

## Project/resume answer

Problem → users/constraints → your contribution → choice and alternative → implementation/verification → defensible result → limitation/next step. Separate your action from team output. If you studied rather than shipped it, say “I designed/practiced…” rather than “I built/launched…”

## LeetCode practice loop

1. Pick one topic and learn just enough theory to name its pattern/invariant.
2. Use a few easy warmups, then representative mediums and variants.
3. Attempt → examples → brute force → invariant/pattern → code → test/complexity.
4. If blocked, request a hint before solution. After studying, close it and reconstruct from memory.
5. Retest next day, then a changed variant about a week later. Schedule another review if still weak.
6. Record miss type: recognition, invariant/proof, implementation, edge case, complexity, communication.
7. Use alarms/streaks to start; measure independent recall and transfer, not question count.

See [worked C# examples](./se2-coding-patterns-worked-examples-2026-09-23.md).

## Close any answer with

“Given **[constraint]**, I chose **[design]** because **[reason]**. It improves **[quality]** at the cost of **[cost]**. The main failure risk is **[risk]**; I would detect it using **[signal/test]**. If **[constraint changes]**, I would reconsider **[alternative]**.”
