# Low-Level Design Syllabus and Case Bank

## Purpose

Build interview-ready object modeling and implementation skills. Treat this as a supplementary syllabus alongside the active .NET sequence in `01-syllabus/dotnet-backend-syllabus.md`; it does not replace the current batch. The intake and original shortlinks are preserved in [the source batch](../09-source-inbox/2026-09-23-lld-interview-guides-ml-case-studies.md).

## Learning sequence

### 1. Object-oriented foundations

- Encapsulation, abstraction, inheritance, polymorphism.
- Prefer composition when it expresses ownership or collaboration more clearly than inheritance.
- Distinguish interface contracts from implementation reuse.
- Model invariants and domain behavior, not just data containers.

**Check:** Given a small domain, identify entities/value objects, invariants, public operations, and likely change points.

### 2. SOLID and code quality

- SRP: one cohesive responsibility, with change reasons as a useful diagnostic.
- OCP: extend behavior through stable seams; avoid speculative extension points.
- LSP: substitutability must preserve promised behavior.
- ISP: small client-specific interfaces.
- DIP: high-level policy depends on abstractions; implementations are supplied at boundaries.
- Cohesion, coupling, information hiding.
- DRY, KISS, YAGNI as contextual heuristics, not rules that override clarity.

**Check:** Name the concrete change or test difficulty an abstraction solves. If none, keep the design simpler.

### 3. Patterns by recurring pressure

Focus first on Strategy, Factory, Adapter, Decorator, Observer/pub-sub, Command, State, and Repository where useful. Study Singleton as a constrained lifecycle/global-state choice, not a default. Recognize patterns without forcing them into the model.

For each pattern, explain: pressure it addresses; simpler alternative; collaboration flow; lifecycle and error behavior; cost; test seam.

### 4. UML and communication

- Class diagrams: responsibilities and relationships.
- Sequence diagrams: interaction order, branching, async boundaries.
- Activity diagrams: workflow and decision branches.
- Object diagrams: one concrete snapshot of object links/state.

Use only as much notation as needed to make assumptions and behavior reviewable. Label ownership, cardinality, and important interfaces.

### 5. Interfaces, dependency injection, and boundaries

- Constructor injection is the ordinary default for required dependencies.
- Setter injection suits optional or replaceable dependencies when object validity is preserved.
- “Interface injection” is a named form, but is uncommon in mainstream .NET; do not present it as equally idiomatic.
- DI container/IoC container composes objects; the application remains responsible for sound boundaries and lifetimes.
- Consider lifetime mismatches, hidden service-locator access, and excessive abstraction.

### 6. Tests and maintainability

- TDD loop: failing behavior test → smallest implementation → refactor.
- Unit test domain rules; integration test persistence, messaging, and external contracts.
- Mocks verify interactions but can couple tests to implementation; use fakes or real collaborators where clearer.
- Test invariants, edge cases, concurrency assumptions, failure and retry behavior.
- Refactor after a behavior-preserving test is in place.

### 7. LLD interview workflow

1. Clarify scope, actors, core use cases, constraints, and explicit non-goals.
2. Identify entities/value objects and invariants.
3. Define interfaces and responsibilities; sketch the main collaboration.
4. Walk a normal flow and at least one failure/concurrency flow.
5. Implement the smallest vertical slice; compile mentally or actually, depending on interview format.
6. Add tests, discuss complexity and extension points.
7. Revisit trade-offs and simplify any speculative design.

## Case bank

Start with one happy path and one changed requirement for each:

- LRU cache: key/value API, capacity, eviction order, O(1) get/put, concurrency policy.
- Tic-Tac-Toe: board invariants, turn taking, win/draw detection, invalid moves, configurable board size.
- Notification system: channels, preferences, templates, retries, idempotency, provider failures, async delivery.
- ATM: authentication/session state, cash inventory, authorization, dispense consistency, cancellation and hardware failure.
- BookMyShow: seat inventory, temporary holds, expiry, payment races, idempotent booking, reconciliation.
- Uber: trip lifecycle, matching boundary, pricing/payment abstractions, concurrent state transitions.

For larger distributed cases such as Uber or booking, separate the LLD domain model from system design infrastructure. Do not imply one class diagram represents the production architecture.

## Portfolio evidence

A portfolio project can include a small running implementation, concise README, class/sequence diagram, invariants, tests, trade-offs, known limitations, and a small load/concurrency discussion. State what was actually implemented and measured; label scale extensions as proposals, not experience.

## Completion standard

For a case, explain and defend:

- object responsibilities and invariants;
- why composition/inheritance and chosen patterns fit;
- how collaborators are injected and tested;
- behavior under invalid input, failure, retry, and concurrency;
- a simpler alternative and the condition that would justify more complexity.
