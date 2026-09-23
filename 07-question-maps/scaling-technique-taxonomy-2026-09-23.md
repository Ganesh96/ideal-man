# Scaling Technique Taxonomy — 2026-09-23

Source: unattributed 98-item “If I had to scale a system” checklist submitted in the source batch. Terms are grouped by the main mechanism they affect; the source numbering is preserved for traceability.
Status: extracted and classified, not ranked or treated as recommendations.

## 1. Capacity, compute, and architecture shape
- #1 Horizontal Scaling
- #2 Autoscale
- #4 Orchestration
- #14 Kernel Bypass
- #15 Vertical Scaling
- #16 Microservices
- #20 Capacity Planning
- #28 Async Non-Blocking IO
- #32 Diagonal Scale
- #42 Thread Pool Tuning
- #58 Stateless
- #61 Modularity
- #79 Job Scheduling
- #87 Container

## 2. Ingress, routing, and edge delivery
- #7 gRPC
- #9 Backend for Frontend
- #11 Edge Computing
- #18 Service Mesh
- #25 Edge Authentication
- #33 Consistent Hashing
- #43 Load Balance
- #46 CDN
- #59 GeoDNS
- #81 Edge Image Transformation
- #90 HTTP Keep-Alive
- #92 API Gateway
- #94 Anycast Routing
- #97 Zero-Copy Networking

## 3. Admission, overload control, and failure containment
- #3 Retries
- #5 High Availability
- #10 Priority Queues
- #13 Brownout Mode
- #17 Rate Limit
- #19 Graceful Degradation
- #23 Request Coalescing
- #24 Dead Letter Queues
- #27 Leaky Bucket Smoothing
- #30 Event Driven
- #31 Circuit Breaker
- #34 Hot Standby
- #41 Token Bucket Throttling
- #44 Queueing
- #45 Backpressure
- #47 CAP Tradeoff
- #55 Adaptive Timeouts
- #56 Load Shedding
- #70 Admission Control
- #73 Multi Region
- #75 Bulkhead
- #84 Concurrency Limits
- #86 Timeouts
- #88 Failover
- #93 Worker Pools
- #98 Hedged Requests

## 4. Query, storage, and read-serving optimization
- #6 Lazy Load
- #8 Data Archiving
- #21 Pagination
- #22 Tiered Storage
- #29 Caching
- #35 Database Connection Pooling
- #36 TTL Expiration
- #37 Batch Reads
- #39 Static Site Generation
- #40 Storage Partition Pruning
- #48 Read Replica
- #49 Materialized Views
- #53 Incremental Static Regeneration
- #54 Client-Side Caching
- #57 Sharding
- #63 Query Result Caching
- #67 Server-Side Rendering Cache
- #68 Columnar Storage for Analytics
- #69 In-Memory Data Grids
- #71 Replication
- #72 Indexing
- #76 Compression
- #77 Denormalization
- #80 Regional Read Caches
- #82 Search Offloading
- #83 Memory-Mapped Files
- #85 Partition
- #89 Prefetching
- #91 Read/Write Splitting
- #96 Specialized Datastores

## 5. Data movement, change propagation, and write-path work
- #12 Delta Sync
- #26 Change Data Capture
- #38 Stream Processing
- #50 Log Compaction
- #51 Idempotency Keys
- #52 Micro-Batching
- #62 Write Batching
- #64 Event Sourcing
- #65 Asynchronous Workflows
- #66 Data Locality
- #78 CQRS
- #95 Optimistic UI with Deferred Sync

## 6. Observability
- #60 Monitoring
- #74 Tracing

## How to choose

Do not start with this list. Start with a workload and a bottleneck:

1. State the workload shape: reads/writes, burstiness, request size, hot keys, freshness, and query pattern.
2. Set correctness and service objectives: latency percentiles, availability, durability, consistency, recovery, and cost.
3. Measure where time/resources go: application CPU, DB locks/IO, network, queue age, storage scans, or downstream saturation.
4. Choose the smallest mechanism that addresses the measured constraint; estimate its new coupling and failure modes.
5. Load-test normal, burst, skewed, and partial-failure cases. Record p50/p95/p99, throughput, cost, and correctness.
6. Add capacity, overload, recovery, and observability controls appropriate to the consequences of failure.

A practical escalation might be: query/index/data-model fixes → caching or batching where semantics allow → vertical headroom or replicas → stateless horizontal capacity and autoscaling → queues/backpressure for burst absorption → partitioning/sharding only when measurements justify the coordination cost. It is not a mandatory sequence.

## Category errors to avoid

- Retries, circuit breakers, rate limits, and load shedding mostly shape failure/overload; they do not create backend capacity.
- Autoscaling can react too slowly for sharp spikes and may amplify a failing dependency.
- CAP trade-offs, modularity, monitoring, microservices, and event-driven design are not drop-in “scale switches.”
- Caching, denormalization, asynchronous updates, and optimistic UI change freshness or consistency behavior.
- Hedged requests can reduce tail latency while multiplying load; use only with bounded concurrency and evidence.
- Kernel bypass, zero-copy networking, memory-mapped files, and in-memory grids are specialized optimizations with higher complexity; profile first.
- “Diagonal scaling” is a label, not a precise portable mechanism. Define what changes in the target platform.
- Similar names are not interchangeable: partitioning, sharding, replication, consistent hashing, and service/data ownership solve different problems.
- A technique should have a measurable success criterion and a rollback or failure plan.
