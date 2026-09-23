# Database Selection Decision Map

Use workload and correctness requirements to choose candidate stores. “SQL vs NoSQL” is not a sufficient decision procedure: data shape alone does not determine access patterns, transaction needs, consistency, or operating cost.

## Decision order

1. **Product operation:** What is created/read/updated/deleted? What is authoritative? Which changes must be atomic?
2. **Workload:** Read/write mix, peak and burst, concurrency, object/index size, retention, growth, geography, hot keys/tenants.
3. **Access patterns:** Point lookup, range scan, join, aggregate, full-text, graph traversal, time window, vector similarity, blob fetch. Include sort, pagination, and freshness.
4. **Correctness contract:** Which reads must see which writes? What staleness is allowed, and for how long? What transaction boundary and failover durability are required?
5. **Data model and candidate stores:** Write example queries before choosing products. Model around invariants, relationships, and query shape.
6. **Scale/failure envelope:** Tune/query-plan/index first; measure. Then consider vertical headroom, replicas, partitions/shards, caches, queues, or workload separation. State the bottleneck each handles.
7. **Whole-life cost:** Operations, backup/restore, observability, migrations, security, skills, licensing/cloud spend, lock-in, and incident recovery.
8. **Validate:** Representative data and concurrency; skew/hot keys; p95/p99; cost; failover and restore. Revisit assumptions when workload changes.

## Correct the common simplifications

| Slogan | More accurate model |
|---|---|
| Structured = SQL; JSON = NoSQL | Relational databases can support JSON and indexing. Shape alone does not choose a store. |
| SQL = ACID; NoSQL = eventual | Guarantees depend on the product and operation. Some NoSQL systems provide transactions/strong reads; relational systems also expose different isolation/replication modes. Name the exact client-visible guarantee. |
| Read-heavy = cache; write-heavy = shard | Query/index design, batching, denormalization, partitioning, workload isolation, hardware and caching each address different bottlenecks and add different costs. |
| NoSQL means horizontal scale | Distribution can require access-pattern-specific keys, denormalization and cross-partition coordination. Scale is not free or automatic. |
| Optimize for future growth | Avoid speculative complexity. State the likely next limit, observable trigger, and reversible next step. |
| Polyglot persistence is better | Each store adds sync, security, backup, observability, skills and incident burden. Add only when workload justifies it. |

## Store families: starting hypotheses, not exclusive boxes

| Family | Often useful for | Questions/costs |
|---|---|---|
| Relational row store (PostgreSQL, SQL Server, MySQL) | Transactions, constraints, joins, flexible queries, OLTP | Isolation/locks, query/index design, write coordination, replica lag, scale limit |
| Key-value/wide-column distributed (Redis, DynamoDB, Cassandra) | Key-based access, high concurrency, partitioned workload | Key design/skew, query limits, consistency semantics, indexes, operating model |
| Document (MongoDB, Couchbase) | Hierarchical records commonly read/written together; evolving shapes | Embed/reference choice, duplication, cross-document atomicity, indexing, document growth |
| Search engine (OpenSearch/Elasticsearch, Solr) | Full text, relevance, facets | Usually derived index, not canonical transactional state; freshness, rebuild and reconciliation |
| Columnar OLAP (ClickHouse, BigQuery, Snowflake) | Aggregation over many rows and fewer columns | Ingestion/freshness, update/delete shape, workload isolation, query/cost control |
| Time series (TimescaleDB, InfluxDB) | Timestamped measurements, time windows, retention/downsampling | Cardinality, late data, rollups, retention and correction |
| Graph (Neo4j, Neptune) | Relationship traversal is the central access pattern | Graph shape, transaction needs, distribution/traversal limits |
| Object/blob (S3, Azure Blob, GCS) | Large unstructured files, backups, lake objects | Not a low-latency transactional row store; metadata/index, lifecycle, access and cleanup |
| Vector index/store | Similarity retrieval over embeddings | Approximate recall/latency, filters/isolation, freshness, embedding version/provenance; often paired with source of truth |

## Worked interview problem: online shop

**Prompt:** Design an online shop with checkout, order history, product search, and daily sales analytics.

**Clarify:** Can checkout oversell inventory? How does external payment authorization/commit behave? How fresh must search be? Can analytics lag? Must order history immediately show a new order?

**Defensible baseline:**
- Start with a relational OLTP store for canonical order, inventory-reservation, and payment state because the workflow has explicit invariants and transactional updates. The local transaction does not make an external payment provider atomic.
- Index measured history/inventory queries. Verify query plans and write amplification.
- Use a conditional inventory reservation or hold/expiry model to prevent concurrent oversell. Protect retries with idempotency. Use an outbox or equivalent reliable publication mechanism instead of an unsafe database-plus-queue dual write.
- Serve text search/relevance from a derived search index with a stated freshness goal and rebuild/reconciliation plan.
- Feed analytics through CDC/outbox to an analytical store; dashboard delay is acceptable if product requirements permit it.
- Add cache only to identified hot and safe reads. Cached inventory is not the final purchase authority.
- Measure checkout success/errors, contention, query latency, replica/consumer lag, search freshness, reconciliation and restore/failover.

**Trade-off:** One transactional source simplifies invariants but has capacity and contention limits. Search/analytics stores accelerate specialized workloads but add stale views, backfill, and operational work. Start with one store if it meets requirements; split when evidence justifies it.

This is a practice proposal, not a claim that the learner shipped such a system.

## Interview answer skeleton

“For **[access pattern]**, with **[invariant/freshness]** and **[scale]**, I would start with **[store/model]** because **[mechanism]**. The main risk is **[specific]**. I would measure **[metric/test]** and avoid **[unneeded mechanism]** initially. If **[requirement/threshold changes]**, I would evaluate **[next option]**, accepting **[cost]**.”

## Primary references

- [DynamoDB data modeling foundations](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/data-modeling-foundations.html)
- [DynamoDB transactions](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/transactions.html) and [read consistency](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html)
- [MongoDB data modeling](https://www.mongodb.com/docs/manual/core/data-modeling-introduction/)
- [PostgreSQL JSON types](https://www.postgresql.org/docs/18/datatype-json.html)
- [ClickHouse columnar database](https://github.com/ClickHouse/clickhouse-docs/blob/main/docs/faq/general/columnar-database.md)

Captured source links are in [the intake note](../09-source-inbox/2026-09-23-database-resources-and-leetcode-practice.md).
