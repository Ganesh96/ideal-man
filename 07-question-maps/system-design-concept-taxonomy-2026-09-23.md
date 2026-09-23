# System Design Concept Taxonomy — 2026-09-23

Source: submitted “98 System Design Concepts” list. Original numbering and labels are retained for traceability, but entries are grouped by learning dependency rather than presented as a must-memorize checklist.

Companion material:
- [Current architecture overlay](../01-syllabus/software-architecture-hard-parts-overlay.md)
- [Scaling technique taxonomy](./scaling-technique-taxonomy-2026-09-23.md) (another 98-item list; techniques overlap but are not the same list)
- [Source intake and claim triage](../09-source-inbox/2026-09-23-netflix-dotnet-system-design-source-batch.md)

## A. Workload and system qualities
#1 Scalability · #2 Availability · #3 Reliability · #4 Latency · #5 Throughput · #6 Capacity

Start with the workload, service-level objectives, and failure costs. Scalability is growth capacity; performance includes latency/throughput under a stated load; capacity is a limit under specific assumptions. Availability and reliability overlap but are not synonyms.

## B. Application and API boundaries
#7 Client-Server · #15 API Design · #16 REST · #17 GraphQL · #18 gRPC · #19 Authentication · #20 Authorization · #21 Rate Limiting · #45 Service Discovery · #46 API Gateway · #75 Service Mesh · #76 Sidecar · #77 BFF

Study as a contract and trust-boundary module:
- HTTP semantics, versioning, pagination, errors, timeouts, compatibility, and idempotency.
- REST, GraphQL, and gRPC have different interaction and tooling trade-offs; do not reduce them to “scalable,” “flexible,” or “fast” labels.
- Authentication establishes identity; authorization decides permitted actions. Rate limits apply to a defined identity/resource/budget and need distributed-state and fairness decisions.
- Gateway, BFF, service discovery, service mesh, and sidecar overlap in some deployments but solve distinct routing, client-shaping, identity, policy, and telemetry concerns.

## C. Data model and database mechanics
#8 Database · #9 SQL vs NoSQL · #27 Partitioning · #28 Sharding · #29 Indexing · #30 Denormalization · #31 ACID · #32 BASE · #59 Full-Text Search · #60 Time Series · #61 Vector DB · #62 Materialized View · #63 Query Optimization · #64 Connection Pooling · #67 CDN Caching · #68 Data Compression · #69 Serialization · #70 Deserialization · #79 LSM Trees · #80 B-Trees · #81 Merkle Trees · #82 Bloom Filter · #83 HyperLogLog · #89 Data Lake · #90 Data Warehouse

Learning order: access pattern and invariants → schema/key choice → query plan/index → transaction/isolation → scaling/distribution → derived/search/analytics structures.
- SQL and NoSQL are families, not single products; compare transactions, query model, schema evolution, access paths, scaling, operational burden, and failure semantics.
- Partitioning is data division; sharding commonly means distribution of partitions across nodes. Replication copies data. Their purposes and consequences differ.
- Indexes trade write work/storage for specific read paths. Query plans and actual workload matter more than a simple “high selectivity” rule.
- Materialized views/search indexes/vector indexes are derived structures and require a freshness and repair strategy.
- B-trees, LSM trees, Bloom filters, Merkle trees, and HyperLogLog solve different storage, membership, reconciliation, or approximate-counting problems. Learn what they guarantee and their error/space costs.
- “BASE” is a broad heuristic often contrasted with ACID; it is not an equivalent, precise transaction contract.

## D. Data distribution and consistency
#22 Fault Tolerance · #23 High Availability · #24 CAP Theorem · #25 Consistency Models · #26 Replication · #31 ACID · #32 BASE · #38 Sync vs Async · #39 Idempotency · #73 CQRS · #74 Event Sourcing · #78 Strangler Pattern · #91 Secrets Management · #92 RBAC · #93 SSO · #94 Encryption · #95 Checksum · #96 Erasure Coding · #97 Consensus · #98 Leader Election

Focus on the exact guarantee:
- CAP concerns behavior during a network partition; it is not a general three-way menu to pick two at all times.
- Consistency can mean different properties (linearizability, causal order, read-your-writes, eventual convergence); state the required client-visible behavior.
- Replication lag, conflict resolution, quorum, consensus, leases/fencing, and failover are connected but not interchangeable.
- Event sourcing stores domain events as a source of truth; a queue transports work/messages; a log may serve both roles but the concepts differ.
- Idempotency protects a business operation from duplicate effects under retry; it is not the same as a transport delivery guarantee.

## E. Architecture and communication patterns
#33 Microservices · #34 Monolith · #35 Event-Driven · #36 Message Queue · #37 Pub/Sub · #38 Sync vs Async · #40 Backpressure · #41 Circuit Breaker · #42 Bulkhead · #43 Retry Logic · #44 Timeout · #47 Load Shedding · #48 Autoscaling · #49 Blue-Green · #50 Canary Release · #51 Feature Flags · #71 WebSockets · #72 WebRTC

Learn mechanisms with failure paths:
- A modular monolith is a valid scaling/evolution path; services add network, data ownership, deployment, and operational boundaries.
- Queue, pub/sub, and stream/log differ in delivery, replay, fan-out, ordering, retention, and consumer model.
- Retries need bounded attempts, backoff/jitter, retryable-error classification, deadlines, and idempotency; unbounded retries amplify failure.
- Circuit breakers, bulkheads, backpressure, load shedding, and timeouts contain different failure modes. They do not make an overloaded dependency healthy.
- Autoscaling has reaction delay and can increase pressure on constrained dependencies.
- Release strategies reduce rollout risk but need health signals, rollback behavior, and data/schema compatibility.
- WebSockets provide a persistent bidirectional app channel; WebRTC targets real-time peer/media/data scenarios with signaling and connectivity concerns.

## F. Observability, operations, and performance
#10 Cache Invalidation · #52 Observability · #53 Logging · #54 Metrics · #55 Tracing · #56 Correlation ID · #57 Monitoring · #58 Alerting · #65 Cache Stampede · #66 Cache Warming

Logs, metrics, and traces answer related but different questions. Correlation/trace identifiers connect events; alerts should be tied to actionable service objectives. Cache invalidation, warming, stampede protection, and freshness policies are part of correctness and operations, not just tuning.

## G. Data processing and analytics
#84 MapReduce · #85 Batch Processing · #86 Stream Processing · #87 ETL · #88 Data Pipeline

Compare throughput, freshness, replay, late/out-of-order data, state, exactly-once claims, backfills, and cost. Pipelines need data quality, schema evolution, lineage, retries, and dead-letter or quarantine policy.

## Concept joins worth practicing

1. **Rate-limited write API:** authn/authz → idempotency → admission control → durable queue → bounded workers → backpressure → database partition plan → metrics and replay.
2. **Search over mutable records:** primary DB → CDC/outbox → search index/materialized view → freshness target → reconciliation and rebuild.
3. **Reliable multi-service operation:** local transactions → outbox → message delivery → idempotent consumers → saga/compensation only where business workflow spans service owners.
4. **Realtime collaboration:** WebSocket/WebRTC choice → session/connection routing → presence state → persistence model → reconnect and conflict handling.
5. **High-read API:** query plan/index → cache placement/invalidation → replicas and lag → CDN eligibility → cost and consistency guarantees.

## Study priority and sequence

Use the sequence to reduce working-memory overload; it is not a ranking of interview frequency.

1. State workload, invariants, SLOs, and a simple baseline.
2. Master API contracts, data modeling, transactions, indexes, and query analysis.
3. Add caching, queues, consistency, idempotency, timeouts, and backpressure.
4. Then study partitioning/sharding, replication/consensus, microservices, streaming, and multi-component failure recovery.
5. Finally explore specialized structures (Merkle trees, Bloom filters, HyperLogLog, erasure coding), realtime protocols, vector search, and analytics according to the target role.

For every concept, be able to explain: the problem, mechanism, preconditions, trade-offs, failure mode, observability signal, when not to use it, and a concrete example.
