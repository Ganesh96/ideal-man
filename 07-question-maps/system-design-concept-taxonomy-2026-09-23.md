# System Design Concept Taxonomy — 2026-09-23

Source: submitted “98 System Design Concepts” list. Every source number and label is retained below for traceability; the groups show learning dependencies, not a ranking or a mandate to use each component.

Companion material:
- [Current architecture overlay](../01-syllabus/software-architecture-hard-parts-overlay.md)
- [Scaling technique taxonomy](./scaling-technique-taxonomy-2026-09-23.md) (a separate 98-item list; the two lists overlap but are not identical)
- [Source intake and claim triage](../09-source-inbox/2026-09-23-netflix-dotnet-system-design-source-batch.md)

## A. Workload, APIs, and request boundaries

#1 Scalability · #2 Availability · #3 Reliability · #4 Latency · #5 Throughput · #6 Capacity · #7 Client-Server · #10 Load Balancing · #13 CDN · #14 DNS · #15 API Design · #16 REST · #17 GraphQL · #18 gRPC · #19 Authentication · #20 Authorization · #21 Rate Limiting · #45 Service Discovery · #46 API Gateway · #77 BFF

Start with the workload, invariants, SLOs, and trust boundaries. Scalability is growth capacity; performance includes latency/throughput under a stated load; capacity is a limit under specific assumptions. REST, GraphQL, and gRPC have different contract, query, transport, and tooling trade-offs; they can coexist. “Internal API” describes an audience/boundary, not an architecture that must use microservices. Authentication establishes identity; authorization decides permitted actions. Gateways, DNS, load balancers, service discovery, and BFFs sit at different levels of routing and client shaping.

## B. Data modeling, databases, and consistency

#8 Database · #9 SQL vs NoSQL · #22 Fault Tolerance · #23 High Availability · #24 CAP Theorem · #25 Consistency Models · #26 Replication · #27 Partitioning · #28 Sharding · #29 Indexing · #30 Denormalization · #31 ACID · #32 BASE

Learning order: access pattern and invariants → schema/key choice → query plan/index → transaction/isolation → scaling/distribution → derived/search/analytics structures.

- SQL and NoSQL are families, not single products; compare transaction needs, query model, schema evolution, access paths, scaling, operations, and failure semantics.
- Partitioning divides data; sharding commonly distributes partitions across nodes. Replication copies data. Their purposes and consequences differ.
- Indexes trade write work and storage for specific read paths. Choose them using predicates, ordering, joins, cardinality, plans, and measured workload; selectivity alone is insufficient.
- CAP concerns behavior during a network partition; it is not a general three-way menu to “pick two.” Name the required client-visible consistency and availability behavior.
- Replication lag, conflict resolution, quorum, consensus, leases/fencing, and failover connect but are not interchangeable.
- “BASE” is a broad heuristic often contrasted with ACID; it is not a precise transaction contract.

## C. Architecture, messaging, and failure control

#33 Microservices · #34 Monolith · #35 Event-Driven · #36 Message Queue · #37 Pub/Sub · #38 Sync vs Async · #39 Idempotency · #40 Backpressure · #41 Circuit Breaker · #42 Bulkhead · #43 Retry Logic · #44 Timeout · #47 Load Shedding · #48 Autoscaling · #49 Blue-Green · #50 Canary Release · #51 Feature Flags · #73 CQRS · #74 Event Sourcing · #75 Service Mesh · #76 Sidecar · #78 Strangler Pattern

- A modular monolith is a valid evolution path; services add network, data-ownership, deployment, and operational boundaries.
- Queue, pub/sub, and stream/log differ in delivery, replay, fan-out, ordering, retention, and consumer model. Event sourcing stores domain events as a source of truth; a queue transports work/messages.
- Retries need bounded attempts, backoff/jitter, retryable-error classification, deadlines, and idempotency. Unbounded retries amplify failure.
- Circuit breakers, bulkheads, backpressure, load shedding, and timeouts contain different failure modes; they do not make an overloaded dependency healthy.
- Autoscaling has reaction delay and may intensify pressure on constrained dependencies.
- Release strategies reduce rollout risk but require health signals, rollback behavior, and data/schema compatibility.
- CQRS separates command and query models where their requirements justify the coordination and consistency cost.

## D. Caching, search, and storage/query performance

#11 Caching · #12 Cache Invalidation · #59 Full-Text Search · #60 Time Series · #61 Vector DB · #62 Materialized View · #63 Query Optimization · #64 Connection Pooling · #65 Cache Stampede · #66 Cache Warming · #67 CDN Caching · #68 Data Compression · #69 Serialization · #70 Deserialization · #79 LSM Trees · #80 B-Trees · #81 Merkle Trees · #82 Bloom Filter · #83 HyperLogLog

- Cache placement, invalidation, stampede protection, warming, and freshness are part of correctness and operations, not just tuning.
- Materialized views, full-text indexes, and vector indexes are derived structures; define freshness, permission filtering, and rebuild/repair paths.
- B-trees and LSM trees represent different storage/write/read trade-offs. Bloom filters test probable membership, Merkle trees support efficient difference detection, and HyperLogLog estimates cardinality. Know the error, space, and update costs.
- Connection pools are a bounded resource. Pool saturation can dominate API latency even when application CPU is low.
- Serialization and compression trade CPU for network/storage bytes; measure end-to-end effects.

## E. Observability, real-time communication, and data processing

#52 Observability · #53 Logging · #54 Metrics · #55 Tracing · #56 Correlation ID · #57 Monitoring · #58 Alerting · #71 WebSockets · #72 WebRTC · #84 MapReduce · #85 Batch Processing · #86 Stream Processing · #87 ETL · #88 Data Pipeline · #89 Data Lake · #90 Data Warehouse

Logs, metrics, and traces answer related but different questions. Correlation/trace identifiers connect events; alerts should be tied to actionable objectives. WebSockets provide persistent bidirectional application communication; WebRTC targets realtime peer/media/data scenarios with signaling and connectivity concerns.

Batch and stream processing differ in latency, state, replay, late/out-of-order data, and cost. Pipelines need schema evolution, data quality, lineage, retries/backfills, and quarantine or dead-letter policy. Data lakes and warehouses have distinct modeling, governance, and query patterns.

## F. Security and distributed coordination

#91 Secrets Management · #92 RBAC · #93 SSO · #94 Encryption · #95 Checksum · #96 Erasure Coding · #97 Consensus · #98 Leader Election

Security mechanisms address separate layers: secret lifecycle, identity federation, authorization, and data protection. Checksums detect corruption; erasure coding provides storage durability with capacity/compute trade-offs. Consensus coordinates replicated state under failures; leader election selects a coordinator, and safe failover may also require terms, leases, fencing, or quorum rules.

## Cross-concept interview drills

1. **Write API:** authentication/authorization → rate limit/admission → idempotency → durable queue → bounded workers → backpressure → database partition plan → metrics and replay.
2. **Search on mutable records:** primary database → CDC/outbox → search index/materialized view → freshness objective → reconciliation and rebuild.
3. **Reliable multi-service workflow:** local transactions → outbox → message delivery → idempotent consumers → saga/compensation only where the business workflow crosses service owners.
4. **Realtime collaboration:** WebSocket/WebRTC choice → connection routing → presence state → persistence → reconnect and conflict handling.
5. **High-read API:** query plan/index → cache placement/invalidation → replica lag → CDN eligibility → cost and consistency contract.
6. **Failover:** define RPO/RTO and acknowledged-write durability → replication model → leader/fencing behavior → client retry/idempotency → recovery validation.

## Study sequence

Use the sequence to reduce working-memory load; it is not a ranking of interview frequency.

1. State workload, invariants, SLOs, and a simple baseline.
2. Master API contracts, data modeling, transactions, indexes, and query analysis.
3. Add caching, queues, consistency, idempotency, timeouts, and backpressure.
4. Then study partitioning/sharding, replication/consensus, service boundaries, streaming, and multi-component recovery.
5. Finally explore specialized structures, realtime protocols, vector search, and analytics according to the target role.

For each mechanism explain: problem, operation, preconditions, trade-offs, failure mode, observable evidence, when not to use it, and a concrete example. Treat social-post slogans, company case-study numbers, and job-market claims as leads to verify, not as universal facts.


## Additional topics surfaced by later interview-prep lists

These extend the 98-term taxonomy with interview-specific mechanisms and case families. Learn by workload and invariant, not by memorizing every product example.

### Cache policy and data models
- LRU/LFU are eviction policies; choice depends on access distribution and metadata/update cost, not a universally superior policy.
- Write-through, write-back/write-behind, and write-around describe cache/write-path strategies with different freshness, durability, and failure windows. Specify source of truth and recovery.
- Relational, document, key-value, object/blob, search, vector, and analytical stores serve different access patterns. A label alone does not decide a datastore.

### Delivery, coordination, and realtime APIs
- At-least-once delivery implies consumer duplicates are possible; exactly-once claims must specify the boundary and external side effects.
- Quorums, distributed locks, leases/fencing, consensus, and leader election have different guarantees and failure assumptions.
- Compare WebSockets, Server-Sent Events, and long polling by directionality, connection lifetime, intermediary support, scale, reconnect behavior, and client needs.
- Fanout-on-write versus fanout-on-read is a workload trade-off for feeds/notifications. Identify celebrity/hot-key skew, write amplification, freshness, and repair/rebuild paths.
- Webhooks are asynchronous outbound API calls: define signing/authentication, retries, idempotent receiver, replay protection, ordering, subscription validation, and delivery visibility.
- Actor-model message isolation does not automatically make a system distributed, durable, or horizontally scalable; locate mailbox state and supervision/recovery boundaries.
- Protocol Buffers and JSON differ in schema/contracts, encoding, compatibility, inspectability, and tooling; compare measured end-to-end costs.

### Production correctness and operations
- Define SLOs as internal objectives and SLAs as externally meaningful agreements where applicable; state measurement windows and error-budget behavior.
- Schema migrations and zero-downtime deployments require old/new code compatibility, phased expand/migrate/contract steps, backfill verification, and rollback boundaries.
- Disaster recovery needs explicit RPO/RTO, region/AZ failure assumptions, restore tests, dependency maps, and cost constraints. Multi-AZ is not a substitute for regional recovery.
- Track blast radius, hot partitions/keys, thundering herd, cold starts, queue age, and capacity headroom as workload/failure variables—not just glossary terms.
- Secure password storage with a purpose-built, salted password-hashing/KDF scheme and current parameter guidance; a fast general-purpose hash is not appropriate. JWT is a signed/encoded claims format by default, not confidential encryption; validate issuer, audience, signature, expiry, and allowed algorithms.

### Case-study bank from the submitted list

Practice each with requirements, rough load/data estimates, APIs, data model, critical paths, bottleneck, failure/recovery, observability, and one reversible trade-off:
- URL shortener / TinyURL; file storage and sync / Dropbox; photo/social feed / Instagram; video upload and playback / YouTube; chat / WhatsApp; rideshare / Uber; ticket inventory / Ticketmaster; food delivery; live streaming; search engine/ranking; payment service; notification service; rate limiter; logging pipeline; real-time leaderboard; news feed.

The shortlink-only list also includes frontend system design. Add client state, caching, network failure, accessibility, performance budgets, API aggregation, and rollout/experiment behavior to the system boundary. Shortlinks are leads; source content remains unreviewed until opened.


## Supplemental source intake: LLD, ML, protocols, and operations

The captured shortlinks and screenshot transcriptions from the next intake batch are recorded in [LLD, interview guides, ML case studies, and architecture checklist](../09-source-inbox/2026-09-23-lld-interview-guides-ml-case-studies.md). The new [LLD map](./low-level-design-syllabus-and-cases-2026-09-23.md) and [ML case-study map](./real-world-ml-system-case-studies-2026-09-23.md) have separate practice paths.

Use this supplemental cluster to connect concepts that are often conflated:

- **Request path and protocol:** DNS, TLS/HTTPS, reverse proxy vs load balancer vs API gateway, REST vs GraphQL vs gRPC, Protobuf vs JSON, webhooks, versioning, WebSockets.
- **Database and delivery:** SQL/NoSQL selection, ACID vs BASE, database types, indexes, connection pools, database caching, CDC, outbox, queues vs pub/sub, idempotency.
- **Coordination and health:** service discovery, heartbeat vs health check, leader election/consensus, consistent hashing, retries, circuit breakers, backpressure and rate limits.
- **Security and operations:** JWT validation, authentication vs authorization, CI/CD, observability, deployment rollouts, health probes, rollback and recovery.
- **Low-level design:** object responsibilities, SOLID, patterns, UML, DI, testability and concurrency; see the separate LLD syllabus for depth.
- **ML-enabled products:** fraud, recommendations, demand forecasts, churn, ranking, generative assistance, payment routing; see the ML case map. Public case write-ups are prompts to inspect, not complete blueprints.

Prefer comparisons tied to a concrete request path or failure scenario over memorizing standalone definitions.
