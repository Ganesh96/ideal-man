# Software Architecture: The Hard Parts — Learning Overlay

Purpose: extend the book with interview/system-design depth, LinkedIn technical posts, and DDIA connections without replacing the book's chapter order.

## Current spine
1. Ch 1 — trade-off analysis, ADRs, fitness functions, architecture vs design
2. Ch 2 — coupling, architecture quanta, static/dynamic coupling
3. Ch 3 — modularity drivers
4. Ch 4-7 — decomposition, data decomposition, service granularity
5. Ch 8-13 — reuse, ownership, distributed transactions, data access, workflows, sagas, contracts
6. Ch 14 — analytical data
7. Ch 15 — custom trade-off analysis

## External-post overlay topics

### Reliable event delivery: Outbox + Inbox
Map to: Ch 9 distributed transactions; Ch 11 workflows; Ch 12 sagas; Ch 13 contracts.
DDIA links: transactions, message delivery semantics, logs/streams, idempotent consumers, derived data.

Concepts to master:
- dual-write problem
- transactional outbox
- dispatch/relay process
- message broker
- at-least-once delivery
- acknowledgement and redelivery
- consumer crash window
- idempotency
- inbox / processed-message table
- atomic consumer transaction
- stable message/event IDs
- duplicate suppression
- ordering and partition keys
- retry policy and poison messages
- exactly-once vs effectively-once behavior
- retention/cleanup of outbox/inbox records
- observability: lag, retry count, duplicate count, failed dispatches
- trade-off: stronger reliability vs storage/operational complexity

Decision questions:
- Does the business update and event publication need atomic intent?
- Can transport redeliver? Assume yes unless contract proves otherwise.
- Is the consumer side effect naturally idempotent?
- Can inbox record and business mutation share one local transaction?
- What is the deduplication key and retention horizon?
- Are ordering guarantees required per aggregate/key?

Interview surfaces:
- Why does publishing after DB commit still fail?
- Why does outbox not prevent duplicate consumer effects?
- How do you make payment/email/inventory consumers retry-safe?
- Is 'exactly once' a broker property or an end-to-end system property?
- Where are the remaining failure windows?
- How do you operate/backfill/replay safely?

---

## Scaling and Architecture Series — 23-topic system-design overlay

Source currently provides topic titles/links only. Treat the titles as syllabus coverage; do not attribute detailed claims to the posts until their contents are shared.

### A. Requirements, capacity, and scaling fundamentals
1. Back-of-the-Envelope Estimation
2. Horizontal vs Vertical Scaling
3. Load Balancing
4. Fault Tolerance

Book map: Ch 1 trade-offs/fitness functions; Ch 3 scalability, availability, fault tolerance; Ch 15 contextual trade-off analysis.
DDIA links: reliability, scalability, load distribution, failure assumptions.

Master:
- QPS/read-write ratio, concurrency, bandwidth, storage growth, latency percentiles
- vertical vs horizontal scale and their ceilings/costs
- load-balancing algorithms, health checks, connection/state implications
- redundancy, failure domains, graceful degradation, RTO/RPO, failover
- capacity headroom and credible growth rather than hypothetical scale

### B. Edge, traffic, and request-routing layer
5. CDN
6. Rate Limiting
7. API Gateway
8. Service Discovery

Book map: Ch 2 dynamic coupling; Ch 3 performance/availability/scalability; Ch 7 service granularity; Ch 13 contracts; Ch 15 trade-offs.
DDIA links: network boundaries, locality, distributed failure, routing.

Master:
- CDN cache hierarchy, origin protection, TTL/invalidation, static vs dynamic content
- token bucket/leaky bucket/fixed/sliding-window rate limiting; local vs distributed counters
- gateway responsibilities: routing, auth, throttling, aggregation, protocol translation; gateway coupling risk
- client-side vs server-side discovery, registry health, DNS/service-mesh approaches

### C. Caching and latency engineering
9. Caching
10. Cache Invalidation
11. Idempotency, Data Latency & Finale

Book map: Ch 3 performance/scalability; Ch 10 replicated caching/data access; Ch 15 trade-offs.
DDIA links: derived data, materialized views, consistency, replication lag.

Master:
- cache-aside/read-through/write-through/write-behind patterns
- TTL, eviction, working set, hit rate, cold cache, stampede/thundering herd
- invalidation/update strategies and consistency windows
- latency budget across network/service/storage layers
- idempotency keys and safe retries
- freshness versus performance trade-offs

### D. Database scaling and data distribution
12. Database Scaling
13. Sharding
14. Partitioning
15. Replication
16. Leader Election

Book map: Ch 6 pulling apart operational data; Ch 7 granularity; Ch 9 data ownership; Ch 10 distributed data access; Ch 15 trade-offs.
DDIA links: Part II Distributed Data — replication, partitioning, transactions, consensus/leadership.

Master:
- read replicas, indexes, caching, connection pooling, vertical scaling before distribution
- sharding/partitioning keys: range/hash/directory, cardinality, skew, hotspots, locality
- routing, rebalancing, resharding, scatter-gather, secondary indexes
- leader-follower and multi-leader replication; sync vs async replicas; replication lag
- failover, split brain, quorum concepts, leader election and fencing
- distinguish logical partitioning, physical partitioning, and service/data ownership boundaries

### E. Consistency and distributed correctness
17. CAP Theorem
18. Consistency Models
19. Eventual Consistency
20. Distributed Transactions

Book map: Ch 6 operational data; Ch 9 data ownership/distributed transactions; Ch 10 distributed access; Ch 11 workflows; Ch 12 transactional sagas; Ch 15 trade-offs.
DDIA links: replication guarantees, linearizability, transactions, distributed systems failure, consensus.

Master:
- CAP only under network partition; consistency/availability meaning in CAP
- strong/linearizable, sequential, causal, read-your-writes, monotonic reads, eventual consistency
- staleness and convergence; conflict resolution
- local ACID vs cross-service business transactions
- 2PC basics/limitations, saga/compensation, outbox/inbox, idempotency
- distinguish transport, processing, storage, and business-effect guarantees

### F. Messaging and asynchronous systems
21. Queues

Book map: Ch 2 dynamic coupling; Ch 9 eventual consistency; Ch 11 workflows; Ch 12 sagas; Ch 13 contracts.
DDIA links: logs, streams, message brokers, consumers, delivery semantics.

Master:
- queue vs pub/sub vs append-only log
- producer/broker/consumer, acknowledgement, redelivery
- ordering, partitions, consumer groups, backpressure
- retry queues, dead-letter queues, poison messages
- at-most-once / at-least-once / bounded exactly-once claims
- asynchronous decoupling versus temporal/semantic coupling

### G. Architecture style and service boundaries
22. Microservices
23. Microservices vs Monoliths

Book map: Ch 2 coupling/quanta; Ch 3 modularity; Ch 4-7 decomposition and granularity; Ch 8 reuse; Ch 9-13 costs of putting distributed pieces back together.
DDIA links: service-owned data, distributed transactions, derived data, messaging, operational complexity.

Master:
- modular monolith vs distributed services
- bounded context/domain boundaries, cohesion, independent deployment
- static/dynamic/data/temporal coupling
- service granularity forces: scalability, volatility, fault tolerance, security, transaction/data relationships
- distributed-system tax: network failures, observability, consistency, deployment, versioning, operations
- organizational/team topology implications

## Cross-topic system-design reasoning order
For any case study, evaluate in this order:
1. Functional requirements and invariants
2. Non-functional requirements: scale, latency, availability, consistency, durability, cost
3. Back-of-the-envelope capacity estimates
4. Data model, access patterns, ownership, transaction boundaries
5. Baseline architecture before optimization
6. Traffic distribution: LB/CDN/gateway/discovery
7. Storage scaling: indexes/cache/replicas/partitioning/sharding
8. Async boundaries: queues/events and delivery semantics
9. Consistency and failure behavior
10. Idempotency/retries/timeouts/circuit breaking/backpressure
11. Observability, recovery, security, deployability
12. Explicit trade-offs and conditions that would change the design

## Retrieval prompts to weave into book sessions
- What problem forces this mechanism to exist?
- What architecture characteristic improves?
- What new coupling/failure mode does it introduce?
- Where is state held and who owns it?
- What happens under partial failure?
- How does it behave under retries/duplicates/reordering?
- What changes at 10x read traffic, 10x write traffic, or 10x data size?
- What is the simplest design that meets the stated requirements?
- What metric/fitness function would prove the decision is working?
- What assumption, if changed, would reverse the decision?
