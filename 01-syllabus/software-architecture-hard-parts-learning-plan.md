# Software Architecture: The Hard Parts — Learning Plan

Primary source: Neal Ford, Mark Richards, Pramod Sadalage, Zhamak Dehghani, *Software Architecture: The Hard Parts*.

## Learning Strategy

The book is organized around hard decisions with no universal best answer. Study it as a decision system, not a glossary.

Each chapter is learned in four passes:

- Pass A — Map: vocabulary, problem, forces, options.
- Pass B — Mechanism: coupling/data/workflow mechanics and architecture characteristics.
- Pass C — Decision: trade-offs, constraints, failure modes, fitness functions/ADRs.
- Pass D — Transfer: system-design scenario, interview explanation, changed-constraint variant.

Mastery requires recall and transfer, not recognition while reading.

## Dependency Order

### Block 0 — Architect Decision Model
Chapter 1: no best practices, least-worst trade-offs, architecture vs design, ADRs, fitness functions, operational vs analytical data.

Output: a reusable architecture-decision loop.

### Block 1 — Coupling and Modularity
Chapter 2: architecture quantum, independent deployability, functional cohesion, static/dynamic coupling.
Chapter 3: modularity drivers: maintainability, testability, deployability, scalability, availability/fault tolerance.

Output: identify what is actually coupled and why separation might create value.

### Block 2 — Decomposition Mechanics
Chapter 4: decomposability, afferent/efferent coupling, abstractness, instability, main sequence, component decomposition, tactical forking.
Chapter 5: component-based decomposition patterns.

Output: reason about whether/how to break a monolith apart.

### Block 3 — Data Decomposition and Technology Choice
Chapter 6: data decomposition drivers/integrators, data domains, migration steps, polyglot persistence.

Output: separate code decomposition from data decomposition and understand their tensions.

### Block 4 — Service Granularity
Chapter 7: disintegrators versus integrators; scope, volatility, scalability, fault tolerance, security, extensibility, transactions, workflow, shared code, relationships.

Output: choose service boundaries as a balance of competing forces.

### Block 5 — Reuse and Shared Capabilities
Chapter 8: replication, shared libraries, shared services, sidecars/service mesh, platforms.

Output: evaluate reuse against change risk, performance, coupling, deployment, and ownership.

### Block 6 — Data Ownership and Distributed Transactions
Chapter 9: ownership patterns, transaction boundaries, eventual consistency patterns.
Chapter 10: distributed data access patterns.

Output: make data ownership explicit and avoid hidden distributed monoliths.

### Block 7 — Distributed Workflows and Sagas
Chapter 11: orchestration, choreography, workflow state.
Chapter 12: saga patterns, compensation, eventual consistency, state machines.

Output: design multi-service workflows under partial failure.

### Block 8 — Contracts and Integration Coupling
Chapter 13: strict/loose contracts, stamp coupling, bandwidth, workflow contracts.

Output: reason about interface evolution and semantic coupling.

### Block 9 — Analytical Data
Chapter 14: warehouse, lake, data mesh, data product quantum.

Output: distinguish operational architecture from analytical data architecture.

### Block 10 — General Trade-Off Method
Chapter 15: entangled dimensions, coupling points, qualitative/quantitative analysis, MECE, out-of-context trap, domain cases, bottom line, anti-evangelism.

Output: build independent trade-off analyses for novel architecture problems.

## High-Leverage Concepts

These should receive repeated retrieval practice because they recur throughout the book:

1. coupling as change propagation;
2. cohesion and bounded responsibility;
3. architecture characteristics as forces;
4. architecture quantum;
5. data ownership;
6. transaction boundary;
7. synchronicity versus asynchronicity;
8. orchestration versus choreography;
9. eventual consistency and compensation;
10. contract coupling;
11. service granularity integrators/disintegrators;
12. fitness functions;
13. ADRs;
14. entangled dimensions and least-worst trade-offs.

## Decision Template

For every major architectural choice, fill:

- Problem:
- Context:
- Constraints:
- Architecture characteristics that matter:
- Coupling points:
- Options:
- Preconditions for each option:
- Benefits:
- Costs:
- Failure modes:
- Reversibility / cost of change:
- Evidence/metrics needed:
- Decision rule:
- Fitness function:
- Consequences:

## Reward Loop

A study unit is complete only after one small win:

- explain from memory in under 90 seconds;
- solve a changed-constraint scenario;
- identify a hidden trade-off in an existing design;
- write one ADR from memory;
- predict a failure mode before reading the answer.

Do not reward passive page completion as mastery.
