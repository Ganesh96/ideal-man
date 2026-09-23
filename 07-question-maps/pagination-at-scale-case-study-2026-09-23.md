# Pagination at Scale — Case Study Map — 2026-09-23

Source: Arcesium Engineering, “PositionService: Pagination at Scale” (2026-04-16): https://medium.com/arcesium-engineering-blog/positionservice-pagination-at-scale-119b772c5094
Related source record: `09-source-inbox/2026-09-23-scaling-pagination-and-stripe-interview.md`
Status: source reviewed; design reconstructed; independent production validation unavailable.

## Problem shape

A finance API serves filtered and aggregated position data from a frequently updated SQL Server dataset. Consumers may traverse every page and need a repeatable point-in-time view across many page requests. The article reports a very large dataset and frequent writes; treat those values as the authors’ environment, not generic sizing guidance.

## Reconstruct the design

1. **Define the contract.** Does a traversal mean a stable snapshot? What filters and grouping are fixed? Does every page need deterministic ordering? What are page-size, retention, authorization, latency, and completeness requirements?
2. **Bound raw extraction.** Query an ordered range from SQL Server. Use the date cursor because date is required and participates in grouping/order. The article uses `WITH TIES` to avoid splitting one date boundary when the nominal raw chunk is reached.
3. **Aggregate and stage.** Aggregate each chunk, stream it as compressed Parquet to S3, and align row groups with the serving page pattern.
4. **Serve subsequent pages.** DuckDB reads the staged Parquet and serves the next page without repeating the heavy database query.
5. **Hold one snapshot across requests.** Propagate a stable request-start time. Resolve the latest committed watermark at or before that time and apply the temporal validity constraints consistently on every page.
6. **Track continuation.** A cursor identifies the query and continuation position/state. Retrying the same cursor should not silently change the logical snapshot.
7. **Expire and recover.** Define object TTL/cleanup, encryption, tenant isolation, cursor expiry, partial upload behavior, and recovery if staged files or cursor state are missing.

## Why it can work

- It moves repeated page scans away from the contended operational database.
- Columnar compressed staging fits aggregate-read workloads when only selected columns are needed.
- A stable temporal boundary can make a long traversal repeatable while writes continue.
- It is optimized around the authors’ observed behavior that clients usually consume the full result.

## Costs and risks to investigate

- Page 1 performs the expensive query/aggregation/stage/upload work; later pages are cheaper. Measure first-page latency and full-export completion separately.
- If clients abandon early, staging a huge result can waste database, network, object-store, and compute resources.
- `WITH TIES` can exceed the nominal chunk by the size of a tied date group; bound or understand the worst hot-date cardinality.
- Date is only a safe cursor when the query contract guarantees date filtering/grouping and boundary handling. Otherwise use a unique stable tie-breaker or composite cursor.
- Cursor state must be scoped to tenant, authorization, query filters, sort order, snapshot watermark, and expiry. Prevent tampering and cross-tenant replay.
- Temporary S3 data needs lifecycle, encryption, access control, cleanup on failure, and cost controls.
- The correctness of `NOLOCK` plus a stable timestamp is specific to their write/versioning protocol. A timestamp predicate alone does not prove freedom from dirty, missing, duplicated, or phantom rows. Validate writer commit ordering, version validity intervals, and all query predicates; compare snapshot isolation/temporal-table alternatives.
- Large page sizes can overload API memory, network, clients, and retries. Benchmark realistic consumers and bound response payload size.
- Separate source-reported claims from measured evidence. The article’s table reports a 1.322-second average for its S3/DuckDB paginated-read benchmark, while the LinkedIn post summarizes “sub-second SLOs.” Confirm the exact operation and percentile before repeating that number.

## Interview prompts

- When is cursor/keyset pagination preferable to offset pagination? What ordering invariant does the cursor require?
- How would you preserve a consistent view while the underlying rows are inserted, updated, and deleted?
- Why stage to object storage instead of query the relational database for every page?
- Why choose Parquet and DuckDB for this workload? Which data shapes would make this a poor choice?
- What does `WITH TIES` protect against, and what is its worst-case cost?
- How do you make retries, concurrent page requests, and client restarts safe?
- How do you measure end-to-end export SLOs separately from per-page latency?
- What changes if users usually read only the first page, need live freshness, or require a hard bound on temporary storage?

## Retrieval check

Without notes, draw the request → SQL Server → aggregation → Parquet/S3 → DuckDB → cursor path. Then identify:
- the snapshot boundary;
- the cursor invariants;
- the expensive first-page work;
- one data-correctness risk;
- one cost-control mechanism;
- a workload change that would make another design preferable.
