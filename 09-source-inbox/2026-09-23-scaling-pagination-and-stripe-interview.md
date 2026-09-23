# Source Batch — Pagination at Scale, Interview Reports, Scaling Checklist

Captured: 2026-09-23
Tracks: system design, data-intensive APIs, database consistency, backend interviews
Status: extracted; primary technical article reviewed; concepts routed to the scaling taxonomy and pagination case map

## Sources

### Stripe Data Scientist interview report
- User-supplied short link: https://lnkd.in/g2i4fGrR
- The Loop / Interview Query: https://theloop.interviewquery.com/
- A social post reports one candidate’s sequence: hiring-manager screen, technical screen, team matching, case study/readout, and a team loop. It also reports an AI assistant present in each round.
- **Claim type:** single candidate account, not official Stripe policy or a stable process specification.
- **Inference in the post:** the assistant’s presence means Stripe transcribes every round and scores clarity/signal density. No evidence for that inference was supplied or found in the account. Do not repeat it as fact.
- **Practice transfer:** prepare role/team-relevant questions when credible team context is available; ask the recruiter about the actual loop; prepare a few detailed, truthful stories with trade-offs, stakeholders, and alternatives. Do not overfit to one interview report.

### Arcesium PositionService pagination article
- User-supplied short link: https://lnkd.in/gY4HYSYj
- Original engineering article: https://medium.com/arcesium-engineering-blog/positionservice-pagination-at-scale-119b772c5094
- By Ayush Jain and Nirley Gupta; published 2026-04-16.
- The article describes a company-specific finance API that filters and aggregates mutable position records. Its authors report about 2 million API calls/day, a largest client dataset of about 7 billion positions, and about 5 million daily create/update/delete operations for one large client. Treat these as author-reported context, not independently audited benchmarks.
- The design uses cursor-based pagination. For large results, it reads a bounded raw-data chunk from SQL Server, orders by date, aggregates it, streams Parquet to S3, and uses DuckDB to serve later pages from the staged data. The article describes a maximum page size of 100,000 and a nominal 10-million raw-record chunk; `WITH TIES` can exceed that chunk to avoid splitting a date boundary.
- For repeatable multi-page results while data changes, the article describes a uni-temporal model, a request-initiation timestamp propagated across pages, and a stable committed timestamp at or before that request time. Readers filter by the stable timestamp. It also retains SQL Server `NOLOCK`; the correctness argument depends on the writer/versioning model and the exact predicates.
- **Trade-off:** page 1 does the query, aggregation, staging, and upload work when the result exceeds one page; later pages reduce repeated database load. The authors state this is worthwhile because consumers commonly traverse all pages. This is poorly matched to clients that usually abandon after page 1.
- **Reported metric mismatch:** the LinkedIn summary says “sub-second SLOs.” The article’s performance table shows an average of 1.322 seconds for “Paginated Read | S3 | DuckDB” in its 10-million-record, 100,000-page-size test. These may be different measurements, but the article does not make that sub-second claim evident in the table. Do not quote a sub-second result without reconciling the metric and measurement boundary.
- **Evidence limit:** the article is a valuable implementation case study, but company-reported timings do not establish independent reproducibility or a general guarantee. The article’s 10-run table is not a substitute for a production latency distribution, workload profile, or p95/p99 test.

### 98-item scaling checklist
- No author, date, or source URL was supplied.
- The complete set is grouped in `07-question-maps/scaling-technique-taxonomy-2026-09-23.md`.
- **Assessment:** useful vocabulary inventory, not a prioritized plan. It mixes architecture styles, capacity tactics, reliability controls, data structures, protocols, observability, and application features. Some items overlap or are alternatives; none should be selected without identifying a measured bottleneck and requirements.

### Attached image — “System Design Cheat Sheet”
File: `ac571706-e7fd-4d83-96e3-159b7c3abe8e.png`

Image text covers load balancing, caching, database scaling, SQL vs NoSQL, indexing, sharding (image heading appears as “SHARING”), consistency models, replication, CAP, API gateway, rate limiting, queues, microservices, CDN, and monitoring/logging.

#### Corrections and qualifications
- **SQL vs NoSQL:** structured vs unstructured and vertical vs horizontal are not reliable dividing lines. Both relational and non-relational databases can scale vertically or horizontally; distribution depends on engine, data model, and workload.
- **CAP:** partition tolerance is a condition of distributed networks, not a dial one can simply turn off. During a partition, a system must define whether it favors consistency or availability for affected operations; CAP consistency is not every possible meaning of “strong consistency.”
- **Consistency models:** linearizability is one strong model, not a complete synonym for all “strong” consistency. Eventual consistency promises convergence under assumptions, not a bound on staleness or a universal user experience.
- **Replication:** copies can improve read capacity or availability, depending on topology and configuration; replication also introduces lag, stale reads, write/failover complexity, and cost.
- **Sharding:** the image’s “sharing” label appears to mean sharding. Sharding is a form of data partitioning across owners/nodes; it adds routing, skew, resharding, and cross-shard query costs.
- **Load balancing/CDN/queues:** each can reduce a particular bottleneck or failure exposure; none automatically guarantees scalability or fault tolerance.
- **Microservices:** “small” is not the core criterion. Boundaries, independent change/deployment, data ownership, and the distributed-systems cost matter.
- **Monitoring and logging:** useful signals, but a complete observability approach often also needs metrics, traces, correlation, useful cardinality control, and actionable alerting.

## Routing

- `07-question-maps/scaling-technique-taxonomy-2026-09-23.md` — all 98 terms grouped by mechanism with selection cautions.
- `07-question-maps/pagination-at-scale-case-study-2026-09-23.md` — design reconstruction, failure cases, and trade-off prompts.
- `01-syllabus/software-architecture-hard-parts-overlay.md` — pagination and point-in-time export extension.
- `04-drills/software-architecture-hard-parts-drills.md` — retrieval and transfer practice.
