# Concept Ledger

This ledger tracks reusable ideas across backend, frontend, databases, LeetCode, system design, cloud, architecture, and data engineering.

## Concept Entry Template

```md
## <Concept Name>

Definition:
Problem solved:
Mechanism:
Tradeoff:
Failure mode:
Appears in:
Interview phrasing:
Related concepts:
```

## Active Concepts

### Boundary Separation

Definition: Different layers should own different categories of decisions.

Problem solved: Prevents HTTP, business logic, persistence, and infrastructure concerns from mixing.

Mechanism: Controllers own transport, services own use cases, repositories/clients own infrastructure boundaries.

Tradeoff: More structure and indirection.

Failure mode: Fat controllers, duplicated business logic, hard testing.

Appears in: .NET, Web API, architecture, testing, system design.

Interview phrasing: I separate HTTP concerns, business workflow, and persistence so each layer can change and be tested independently.

### Make Invalid States Difficult to Represent

Definition: Design objects so illegal or incomplete states are hard to construct.

Problem solved: Prevents bugs caused by partially initialized or inconsistent objects.

Mechanism: Constructors, private setters, domain methods, validation boundaries.

Tradeoff: Slightly more upfront design.

Failure mode: Public setters everywhere, scattered validation, runtime defects.

Appears in: C#, OOP, domain modeling, DDD, LLD.

Interview phrasing: I prefer constructors and domain methods that preserve invariants instead of allowing any part of the system to mutate state freely.

### Change Boundary

Definition: A place where implementation is likely to vary or fail independently.

Problem solved: Helps decide where abstractions are worth introducing.

Mechanism: Interfaces around databases, external APIs, queues, file systems, time, authentication, and infrastructure services.

Tradeoff: Too many abstractions create ceremony.

Failure mode: Either tight coupling or over-engineered indirection.

Appears in: DI, testing, architecture, cloud, system design.

Interview phrasing: I introduce abstractions at real change boundaries, not around every class by default.
