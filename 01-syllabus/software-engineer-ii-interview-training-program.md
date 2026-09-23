# Software Engineer II Interview Training Program

Updated: 2026-09-23

## Outcome

Prepare for mid-level software engineering interviews across Google, Netflix, Amazon, Tesla, Microsoft, Palo Alto Networks, GEICO, Walmart, and similar employers. Build transferable ability to solve coding problems, implement maintainable software, design reliable systems, debug unfamiliar code, reason through trade-offs, and explain real work clearly.

Company titles are not comparable level definitions. “Software Engineer II,” “SWE III,” and similar titles vary by employer, team, location, and role. This program targets a practical mid-level bar; it cannot promise an offer or infer an exact interview loop. Use job descriptions and recruiter guidance to choose the relevant company overlay.

## Starting assumptions

- Repo focus is .NET/C#. Worked coding examples use C# unless you later select another interview language.
- C# foundations/OOP are marked introduced in the existing syllabus, but need testing before advancing.
- System-design, LLD, AI, behavioral, interview-report, and architecture materials already exist. This program connects them rather than duplicating glossaries.
- No interview date or weekly capacity is set, so progress is competency-gated rather than tied to an invented deadline.

## Mid-level competency target

You should be able to:

1. Turn an ambiguous request into testable requirements and explicit assumptions.
2. Write correct, readable code; explain invariants, complexity, edge cases, and tests.
3. Extend, debug, and review existing code as well as solve from scratch.
4. Model objects and interfaces around responsibilities and invariants without overengineering.
5. Design a service from workload through APIs, data, failure recovery, observability, security, and cost.
6. Compare alternatives and explain what evidence or changed constraint would reverse the choice.
7. Own a scoped project through delivery and operation; describe collaboration and your contribution accurately.
8. Communicate decisions and uncertainty clearly under time pressure.

These are learning outcomes, not claims about a company’s secret rubric.

## Program phases

Each phase uses the same loop: learn a mechanism → retrieve it without notes → solve a fresh problem → explain it → record the miss → retest later.

### Phase 0 — Baseline and communication

Clarify prompts, timebox, state assumptions, narrate decisions, use complexity language, and recover when you find a bug.

**Practice:** one unseen coding prompt, a short design case, one project walkthrough, and one behavioral/situational prompt.

**Gate:** restate the problem, ask high-value questions, describe your next step, and correct an error without going silent.

### Phase 1 — Programming and computer science foundations

C# types and object model; collections; exceptions; generics; delegates/events; LINQ; async/await; tasks/cancellation; concurrency; memory/runtime basics; HTTP; SQL; transactions; indexes; testing; Git; debugging.

**Gate:** explain core mechanisms and trade-offs, implement small examples, and verify behavior with tests. Avoid slogans such as “all value types live on the stack.”

See [.NET syllabus](./dotnet-backend-syllabus.md) and [.NET theory drills](../04-drills/dotnet-theory-drills.md).

### Phase 2 — Data structures and algorithms

Arrays/strings and complexity → hash maps/sets → two pointers/sliding windows → stacks/queues → binary search → linked lists → trees/BSTs → heaps → intervals/sorting → graphs/BFS/DFS/topological sort → recursion/backtracking → dynamic programming → trie/union-find when role-relevant.

For each pattern: identify the problem shape; derive a baseline; state the invariant; explain correctness; implement; test normal, boundary, and adversarial cases; state time/space; solve a changed variant.

**Gate:** solve unseen medium-level problems in a realistic timebox, explain before/during coding, and handle a follow-up. Raw problem count is not the metric.

### Phase 3 — Practical software engineering

Requirements and acceptance criteria; API contracts; validation/errors; persistence/schema evolution; transaction boundaries; concurrency/idempotency; integration tests; code review; unfamiliar-code debugging; performance measurement; deployment/rollback; observability and incidents.

**Practice:** extend a parser/API after requirements change, debug a seeded fault, review a flawed patch, trace a request through code and tests.

**Gate:** safely change an existing design and explain how you verified it.

### Phase 4 — Object-oriented and low-level design

Encapsulation, abstraction, composition/inheritance, SOLID, cohesion/coupling, interfaces, DI, state machines, selected patterns, useful UML, test seams, concurrency.

Cases: LRU cache; notification system; Tic-Tac-Toe; ATM; booking/seat reservation; rate limiter; product-catalog ingestion.

**Gate:** state invariants and responsibilities, implement a vertical slice, test it, explain failure/concurrency, and defend the simplest sufficient design.

See [LLD syllabus and cases](../07-question-maps/low-level-design-syllabus-and-cases-2026-09-23.md).

### Phase 5 — System design and distributed systems

Workload/quality attributes → APIs and data models → relational and specialized stores → indexes/query plans → caches/CDNs → load balancing/gateways → queues/events/CDC/outbox → consistency/replication/partitioning/sharding → rate limits/backpressure/resilience → multi-zone/region recovery → security → observability/cost.

Cases: URL shortener; image upload; notification; rate limiter; feed; chat; booking/payment; search; video; leaderboard; ML recommendation/fraud.

**Gate:** in a 45-minute design, clarify scope, estimate dominant load, propose a minimal baseline, trace critical paths, identify bottlenecks/failure recovery, name measurable signals, and defend an alternative.

See [system design taxonomy](../07-question-maps/system-design-concept-taxonomy-2026-09-23.md), [question map](../07-question-maps/system-design-interview-question-map-2026-09-23.md), the [worked URL shortener case](../04-drills/se2-system-design-worked-case-url-shortener.md), and [answer templates](../04-drills/se2-interview-answer-templates.md).

### Phase 6 — Behavioral and situational reasoning

Prepare true examples of ownership, disagreement, failure, ambiguity, learning, delivery, customer impact, and helping another engineer. Use STAR-L: Situation, Task, Actions, Result, Learning. Explain alternatives, stakeholders, your contribution, and evidence.

For hypothetical situations, structure goal/constraints → risks → options → decision/communication → validation/escalation. Do not present an imagined event as personal experience.

**Gate:** tell two or three distinct, truthful stories and handle follow-ups about decisions, evidence, and what you would change. Use the [story-bank workbook](../04-drills/se2-behavioral-story-bank-workbook.md).

### Phase 7 — Mixed practice and company overlays

Rotate DSA, code/debug, LLD, system design, and behavioral practice. Run timed mocks. After each, choose at most three fixable weaknesses.

Company overlays adjust emphasis, not fundamentals. Verify the current role and format through the job description, official material, and recruiter; treat social posts as practice prompts, not policy.

## Study cadence

Use a repeatable five-session cycle, spread over any calendar period:

1. Coding pattern lesson + worked example.
2. Two unseen/retrieval coding problems, including one retest.
3. Fundamentals, debugging, or code review.
4. Spoken system-design or LLD case.
5. Behavioral story + mixed mock + error review.

A 45–75 minute session can use: 5 minutes closed-book recall, 10–15 minutes lesson, 20–35 minutes active problem, 10 minutes explanation/correction, plus a scheduled retest. On low-energy days, use a small retrieval task. A streak is a start cue, not evidence of learning.

For LeetCode, attempt independently first, then use progressively stronger hints. If stuck, learn the missing pattern, close the solution, reconstruct it, and solve a changed variant later. The source’s 30-minute cap is a practice heuristic, not a universal rule.

## Readiness scorecard

Score 0–3 from observed mock evidence:

- 0: cannot start or makes unsupported claims.
- 1: partial, heavily prompted, or correctness unclear.
- 2: independently solid with a minor miss.
- 3: clear, correct, adaptable, handles follow-up.

Rate coding correctness; DSA; code quality/testing/debugging; LLD; system design; fundamentals; communication; behavioral evidence; time management.

Do not claim readiness from an average alone. Coding correctness and design structure must each score 2+ on two separate mocks; behavioral answers must be grounded in real events and retested.

## Evidence and integrity

Keep distinct: **observed work** (what you personally built/measured/decided/operated), **team result** (shared outcome with your attribution), and **hypothetical design** (practice proposal). Never convert a practice estimate into a personal metric. If a metric is unavailable, say what was and was not measured.

## Linked assets

- [Latest database/source intake](../09-source-inbox/2026-09-23-database-resources-and-leetcode-practice.md)
- [Database selection decision map](../07-question-maps/database-selection-decision-map-2026-09-23.md)
- [Interview templates and cheat sheets](../04-drills/se2-interview-answer-templates.md)
- [Worked C# coding patterns](../04-drills/se2-coding-patterns-worked-examples-2026-09-23.md)
- [Company overlay](../08-targets/se2-company-overlay.md)
