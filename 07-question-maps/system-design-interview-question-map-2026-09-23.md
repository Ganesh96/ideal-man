# System Design Interview Question Map — 2026-09-23

Source: image `284e32df-daaa-414f-b850-22b0b2bbacf3.png`, submitted with the system-design/AI source batch.
Tracks: HLD, software architecture, security, reliability, data systems.
Status: extracted and organized; questions are prompts, not validated solution requirements.

## Study order

Work from requirements and data correctness toward scaling and operations. For each answer, state assumptions, alternatives, failure behavior, measurable signals, and the condition that would change the decision.

### A. Data model, transactions, and correctness

1. What is your approach to multi-tenant data models? *(image #1)*
2. What patterns reduce the risk of deadlocks in transactional systems? *(#2)*
3. How do you choose among computed views, materialized views, and real-time aggregations? *(#3)*
4. How do you design data-retention and archival policies? *(#4)*
5. How do you decide between OLTP and OLAP designs when modeling data? *(#11)*
6. How do you handle database failover while meeting a stated data-loss objective? *(#12; clarify RPO/RTO instead of assuming “no data loss” is free)*
7. How do you reduce write contention at scale? *(#13)*
8. When do you denormalize, and how do you keep duplicated data consistent? *(#14)*
9. How do you make atomic updates when a NoSQL system lacks multi-document transactions? *(#23; name the invariants and consider conditional writes, single-record modeling, idempotency, or sagas)*

### B. Security, identity, and governance

10. How do you design authentication and authorization across distributed systems? *(#5)*
11. How do you secure internal service-to-service communication? *(#6 and #9; merged duplicate)*
12. What is your approach to secret rotation and zero-trust controls? *(#8)*
13. How do you document architecture so operators and future engineers can use it? *(#10; include decisions, data flows, trust boundaries, and operational procedures)*

### C. Availability, scaling, and cost

14. How would you handle a 100x traffic spike? *(#15; first bound the load and identify graceful-degradation choices)*
15. What signals tell you whether the application, storage, or network tier is the bottleneck? *(#16 and #24; merged duplicate)*
16. How do you avoid single points of failure? *(#17; reason about correlated failure and failure domains)*
17. Which approaches reduce shared state between nodes? *(#18; identify what state must remain authoritative)*
18. How do you rate-limit at API, service, and user levels? *(#19; include fairness and distributed-counter trade-offs)*
19. Which patterns make horizontal scaling predictable and cost-efficient? *(#20; include utilization, skew, state, and operational overhead)*
20. How do you run workloads across multiple availability zones? *(#21; distinguish zone redundancy from region-level disaster recovery)*
21. What are the trade-offs between managed and self-hosted cloud services? *(#22; compare operational burden, control, portability, cost, and failure responsibility)*

## Hidden prerequisites / concept links

- Multi-tenancy → tenant isolation, shard/partition key, noisy-neighbor control, per-tenant quotas, authorization boundaries.
- Deadlocks and write contention → transaction scope, lock ordering, isolation levels, optimistic concurrency, hot keys, queueing.
- Computed/materialized/real-time views → freshness SLA, update path, recomputation, incremental aggregation, cache invalidation.
- Retention/archives → legal/product retention needs, restore time, deletion propagation, tiering, encryption/key lifecycle.
- OLTP/OLAP → access patterns, normalization, analytical replicas/ETL, workload isolation.
- Failover → synchronous/asynchronous replication, quorum, acknowledged-write durability, fencing, split brain, RPO/RTO.
- Denormalization and atomic NoSQL operations → source of truth, dual writes, outbox, idempotency, versioning, reconciliation.
- Distributed auth → identity propagation, authorization policy location, least privilege, token lifetime, revocation, auditability.
- Service security and secrets → mTLS/workload identity, key management, rotation overlap, trust boundaries, zero-trust threat model.
- Scaling and bottlenecks → workload model, saturation signals, queue depth, tail latency, backpressure, load shedding.
- Availability zones and managed services → failure domains, shared dependencies, regional recovery, provider responsibility boundaries.

## Answer frame

For every prompt:

1. Clarify users, workload, invariants, latency/freshness, availability, RPO/RTO, security, and cost constraints.
2. Give a simple baseline and name its bottleneck or risk.
3. Compare two plausible options and the coupling or operational cost each adds.
4. Walk through at least one partial failure and recovery path.
5. Name the metrics or test that would falsify the design.
6. State what changed constraint would reverse your choice.

## Retest

Ask the same question later as a failure investigation or changed-constraint scenario. Do not mark an answer stable from reading alone.
