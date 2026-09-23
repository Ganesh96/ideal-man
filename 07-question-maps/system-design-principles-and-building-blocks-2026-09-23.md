# System Design Principles and Building Blocks — 2026-09-23

Source: unattributed “35 practical thoughts” and “11 building blocks” posts, submitted 2026-09-23.
Related source record: `09-source-inbox/2026-09-23-system-design-principles-and-write-scaling.md`
Status: synthesized and qualified.

## 35 practical thoughts — organized for retrieval

### Decision quality and change
1. **Every design trades something.** Name the constrained qualities and the affected users; do not turn “speed/cost/simplicity” into a universal triangle.
5. **Design for change.** Prefer reversible choices where uncertainty is high; also identify the cost of deferring a hard decision.
16. **Microservices are often an organizational choice.** Boundaries, ownership, independent delivery, and operational readiness matter more than service count.
17. **Monolith → modular monolith → services is a useful default path, not a law.** Choose from change patterns, boundaries, team constraints, and failure isolation needs.
18. **Choreography vs orchestration is a trade-off.** Choreography reduces a central coordinator but can make flow visibility and change harder; orchestration centralizes process logic and can create coordinator coupling.
19. **Serverless trades control for managed operations and elastic scaling.** Include limits, cold starts, vendor coupling, observability, and cost shape.
31. **Documentation supports operation and change.** Keep system context, data flows, decisions, and runbooks useful and current.
32. **Design reviews test reasoning.** Use diagrams to expose boundaries and flows; evaluate requirements, alternatives, failure modes, and consequences.
33. **PR size is context-dependent.** Small changes ease review and rollback; coherent large changes sometimes preserve context. Optimize for safe comprehension and delivery.
34. **Ask uncomfortable failure and change questions.** Make them specific enough to alter a decision.
35. **Production changes assumptions.** Design for detection, containment, recovery, and revision; no design is failure-proof.

### Performance, capacity, and workload shape
2. **Latency follows the critical path.** Sequential layer delays accumulate; parallel work follows the slowest dependency plus coordination, not a simple sum. Track percentiles, not only averages.
3. **Scalability and performance are distinct but related.** Define the load range and a latency/throughput objective; test both.
4. **Read and write paths often need different treatment.** Make access patterns, data freshness, and consistency explicit.
20. **Queues smooth bursts; they do not erase work.** Bound queue age/depth, define backpressure and overload behavior, and plan for sustained arrival rates above service capacity.
26. **Optimize measured hot paths.** Use profiles and traces before micro-optimizing cold code.
27. **Do not assume the database is the bottleneck.** Measure CPU, lock waits, I/O, network, queueing, and downstream dependencies.
28. **Horizontal vs vertical scaling is workload-specific.** Horizontal capacity adds coordination, partitioning, and network costs; vertical capacity has hardware and availability ceilings.
29. **Measure warm and cold behavior.** Cold-cache effects matter for restarts, failover, rare keys, and burst recovery.
30. **Do not rank disk, time, or other resources universally.** Measure total cost, including engineering and operating time.

### Data, consistency, and reliability
6. **Index value depends on the workload.** Selectivity is one factor alongside query frequency, sort/join patterns, covering, write amplification, memory, and planner behavior.
7. **Replication and partitioning are different mechanisms.** Replication can help reads/availability; partitioning can distribute data/work; either can add write paths or complexity depending on topology.
8. **Uncoordinated dual writes can drift.** Consider an outbox/CDC or another explicit consistency contract; retries and reconciliation still matter.
9. **Event stores and queues are not substitutes.** An event log/store can be durable history or source of truth; a queue/broker distributes work. Some systems use both.
10. **Cache invalidation creates a freshness/complexity trade-off.** State the consistency window and recovery path.
11. **Idempotency makes retries safer, not magically correct.** Define key scope, retention, atomic effect boundary, and duplicate result behavior.
13. **Eventual consistency is acceptable only under a product contract.** Specify stale-read behavior, convergence, conflict handling, and user-visible compensation.
14. **Active-active conflict resolution is partly domain policy.** Infrastructure detects/replicates conflicts; the business defines valid merge or rejection semantics.
15. **Cross-region durability costs latency and money.** State RPO/RTO and sync/async acknowledgement semantics.
23. **Retries need limits, backoff, jitter, budgets, and retry-safe effects.** Otherwise failure load can amplify itself.
24. **Poison-message handling is necessary; a dead-letter queue is one option.** Alternatives include bounded retries, quarantine, rejection, or operator repair.
25. **Operational levers reduce blast radius.** Define owner, guardrails, audit, and rollback for kill switches or feature controls.

### Observability and operations
12. **Fail fast where the caller can recover; preserve useful context.** Some transient failures need bounded retries rather than immediate failure.
21. **Logs, metrics, and traces answer different questions.** Traces connect requests; logs retain events/context; metrics expose aggregate behavior and alert signals. None outranks all others.
22. **Metrics need ownership and action.** Control cardinality and connect alerts to an SLO, decision, or operator response.

## 11 building blocks — when they fit and what they cost

| Block | Common job | Decision questions |
|---|---|---|
| Load balancer | Distribute requests among healthy instances | Is balancing per request or connection? How are health and draining handled? |
| API gateway | Centralize external routing/policy | Does it simplify clients, or become a bottleneck/critical dependency? |
| Application server | Execute application logic | What is stateless, what is local state, and how does concurrency scale? |
| Distributed cache | Reduce repeated reads/latency | What is the invalidation, staleness, stampede, and outage policy? |
| Relational database | Transactions and relational queries | What are the transaction invariants, indexes, write limits, and recovery objectives? |
| NoSQL database | A family of non-relational data models | Which model/access pattern fits? What consistency and partition-key risks follow? |
| Message queue | Buffer and decouple work | What are ordering, delivery, retry, idempotency, poison-message, and lag semantics? |
| Object storage | Durable, low-cost blob/file storage | How are objects indexed, secured, versioned, expired, and recovered? |
| Rate limiter | Bound demand or enforce quotas | Which identity/key, algorithm, distributed accuracy, and fairness policy are needed? |
| Search index | Low-latency text/filter retrieval | What is the source of truth, indexing lag, reindex path, and consistency contract? |
| CDN | Cache and deliver content near users | Which responses are safe to cache, and how are invalidation and private content handled? |

These are options, not a mandatory architecture checklist. A design may not need all of them.

## Write-heavy system reasoning

Use the write-scaling post as a scenario, not a universal claim that writes are always harder than reads.

1. Measure write arrival rate, burst shape, payload size, transaction/constraint cost, hot keys, lock waits, storage latency, and required acknowledgement/durability.
2. Remove avoidable work first: query/index/data-model corrections, batching, bounded concurrency, and connection management where measurement supports them.
3. Add queueing only if asynchronous acceptance is allowed. Define maximum age, capacity, fairness, backpressure, retries, idempotency, dead-letter/quarantine behavior, and how sustained overload is rejected.
4. Partition or shard only when one write owner is the measured limit. Validate distribution, hotspots, cross-partition transactions, rebalancing, and ordering.
5. Consider vertical capacity, replicas, or a different datastore only against concrete write/read/consistency requirements and migration cost.
6. Autoscaling does not instantly increase database write capacity; dependency limits and warm-up matter.
7. Compare read/write trade-offs on the actual engine and model. Do not use “Cassandra vs traditional DB” as a universal ranking.

## Code-reading exercise

Pick one codebase and one question (event loop, transaction boundary, object model, test philosophy, or failure handling). Spend one focused session to:

1. trace one request or data path from entry point to effect;
2. locate its invariants and tests;
3. inspect one failure/recovery path;
4. write one evidence-backed design decision and one question you cannot yet answer.

Suggested projects from the source: Redis, SQLite, Git, Quake III Arena, Go standard library, Linux kernel. The source’s line counts, coverage metrics, and qualitative comparisons require version/scope-specific verification before repeating them.
