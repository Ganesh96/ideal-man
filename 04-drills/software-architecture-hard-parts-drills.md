# Software Architecture: The Hard Parts — Drills

## Chapter 1 Retrieval Drills

### Basic
1. Why does the book reject the idea of a universal best architecture?
2. What does `least-worst combination of trade-offs` mean?
3. What is the book's practical distinction between architecture and design?
4. Define coupling using the book's simplified definition.
5. What are operational and analytical data?
6. What are the three core sections of the book's ADR format?
7. What is an architecture fitness function?

### Intermediate
1. A team says `the system must be high performance`. Why is this insufficient for a fitness function?
2. Distinguish a domain test from an architecture fitness function.
3. Why can a static architecture diagram fail as a governance mechanism?
4. Why might improving security harm another architecture characteristic?
5. Why does the book argue that data became a harder architecture concern with distributed systems?
6. Give one example of an atomic fitness function and one holistic fitness function.

### Transfer
1. A monolith has cyclic dependencies between billing, customer, and ticket components. What would you measure before deciding to decompose it?
2. A team proposes microservices because they are a `best practice`. Identify the reasoning error and the missing context.
3. Design an ADR skeleton for `use asynchronous notifications instead of synchronous notification calls` without choosing the answer until constraints are stated.
4. Define one measurable fitness function for availability and one for deployability.
5. If an architecture decision has a good outcome, does that prove the decision process was good? Explain.

## System-design question-map drills

Use the grouped prompts in `07-question-maps/system-design-interview-question-map-2026-09-23.md`. Start with one data-correctness, one security, and one scale/reliability scenario. For each, state assumptions, baseline, trade-offs, failure path, and falsifying metric.

1. A multi-tenant service has one very large tenant and frequent cross-tenant reports. Compare shared tables with tenant keys, schema-per-tenant, and database-per-tenant. What changes with isolation, cost, migrations, noisy neighbors, and query patterns?
2. A database failover must lose no acknowledged writes. State the exact durability/RPO requirement, then compare synchronous replication and quorum/leader failover. What latency, availability, and split-brain risks follow?
3. Traffic rises 100x for five minutes. Estimate request shape first. Design load shedding, queue bounds, rate limits, autoscaling, and graceful degradation; explain which controls respond too slowly.
4. A NoSQL workflow must atomically update a profile, audit record, and search index. Which data belongs in one aggregate? Which can be derived asynchronously? Design idempotency, repair, and reconciliation.
5. A service uses materialized aggregates but product now requires sub-second freshness. Compare incremental updates, stream processing, synchronous computation, and cached reads. State what freshness and correction guarantees are feasible.
6. A security review finds a long-lived shared service credential in logs. Explain containment, rotation without downtime, workload identity/mTLS, authorization scope, and audit verification.

## AI application architecture drills

1. A support assistant must answer from frequently changing internal policies with per-user permissions. Compare RAG, fine-tuning, a deterministic search/UI, and a hybrid. Name the retrieval and authorization boundaries.
2. A model change improves average score but doubles p95 latency and cost. What representative slices, quality floors, budgets, and rollout checks determine whether to ship it?
3. Users report fabricated answers. Separate retrieval failure, stale source data, context truncation, model behavior, and product UX. Propose an evaluation and tracing plan.
4. A RAG pipeline retrieves a document containing instructions to reveal secrets. Threat-model retrieval-time prompt injection and cross-tenant leakage; define controls and tests.
5. An agent may create or refund payments through a tool. Define authorization, human approval, idempotency, retry limits, audit, and failure recovery. What must remain outside the model's authority?
6. An interviewer asks `Why RAG instead of fine-tuning?` Answer conditionally: what objective, data freshness, update cadence, privacy, evaluation results, and operational costs make each option fit?
7. What would make you select a smaller or cheaper model over the strongest available one? Define a task-specific evaluation set, minimum quality threshold, latency/cost budget, and fallback.

## Coding and behavioral transfer

These are practice surfaces drawn from anecdotal interview reports, not claims about a current company's hiring loop.

- Extend a working parser after a new requirement arrives. Explain how you keep the design open to change without speculative abstractions.
- Integrate a paginated API with rate limits and partial failures. Define retries, checkpointing, deduplication, and output validation.
- Navigate an unfamiliar repository and debug a regression. State how you form hypotheses, narrow the fault, and verify the fix.
- Review a slow or incorrect AI-generated patch. Find the smallest failing test, inspect assumptions, measure performance, and explain what you reject.
- Prepare three truthful STAR stories that collectively cover leadership, conflict, failure, and achievement. For each, separate your contribution from the team's result and be ready to state evidence and limits.

## Retrieval and practice rules

- For each weak answer, record the mistaken assumption and retest in a different form later.
- Do not convert an unverified company-scale anecdote into a design requirement.
- Do not claim hands-on experience from a hypothetical exercise.
- A strong answer explains when the proposed pattern is a poor fit.

## Retest Variants

For every weak concept, create a later variant across at least two surfaces:

- definition;
- compare/contrast;
- changed constraint;
- failure diagnosis;
- ADR decision;
- fitness-function design.


## Pagination and point-in-time export

Use `07-question-maps/pagination-at-scale-case-study-2026-09-23.md`.

1. A client traverses 800 pages while new rows and corrections arrive. Define the snapshot contract and cursor fields so a retry or page-500 request does not silently observe a different dataset.
2. A result exceeds one page. Compare repeated database reads, cursor pagination, and staging an immutable Parquet snapshot to object storage. Include first-page cost, page latency, abandonment, object expiry, authorization, and cleanup.
3. One date contains more rows than the nominal extraction chunk. Explain why `WITH TIES` may help and how it changes upper-bound/capacity assumptions.
4. The team uses `NOLOCK` and a commit watermark. What write-version invariants and predicates must hold before you believe the result excludes uncommitted or missing data?
5. The LinkedIn post says “sub-second,” but the article benchmark reports a 1.322-second mean for one S3/DuckDB paginated-read measurement. What metric boundary and percentile evidence would you ask for before repeating the claim?

## Write-heavy scaling

1. A database sees 5x bursts for 10 minutes and lower traffic overnight. Which facts determine whether to queue writes, shed load, autoscale, or partition?
2. Arrival rate stays above processing capacity for 30 minutes. Calculate backlog growth and time-to-capacity; explain why a queue alone cannot solve it.
3. A user-ID shard key is balanced on average but one tenant produces 40% of writes. Compare tenant isolation, hot-key mitigation, and a compound key; include cross-tenant query cost.
4. A team proposes “add replicas” to fix write throughput. Explain which read/write paths replication may improve and which write bottlenecks remain.
5. Given an index, batch size, and partition change, define before/after correctness tests and p95/p99, throughput, and cost measures.

## Heuristic and building-block evaluation

1. Pick one “rule” such as “horizontal beats vertical” or “replication helps reads, partitioning helps writes.” Name the conditions where it holds, counterexamples, and a changed requirement that reverses it.
2. A design checklist recommends all 11 components. Reduce it to the minimum set that meets a stated product requirement; name the failure mode or operational cost introduced by each chosen component.
3. An interviewer says “Use Cassandra because writes are hard.” Respond by eliciting access patterns, consistency, transaction, partitioning, and operational constraints before selecting a store.
4. Explain why an event store and a message queue are different roles. Show one valid design that uses both and one that needs neither.
5. Trace one request in a production codebase from entry point through data mutation to tests and failure recovery. State only conclusions supported by the code or docs you inspected.

## Interview-report discipline

Prepare a few truthful stories deeply rather than memorizing one anecdotal loop. For each story, identify your contribution, decision alternatives, stakeholder constraints, dead ends, evidence, and result. Confirm the actual target interview stages with the recruiter; do not infer transcription or scoring practices from an AI assistant being present.
