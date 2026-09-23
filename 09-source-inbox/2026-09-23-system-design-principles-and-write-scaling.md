# Source Batch — System Design Principles and Write Scaling

Captured: 2026-09-23
Tracks: system design, distributed data, performance, architecture, code reading
Status: extracted; core heuristics and caveats routed to the principles map, architecture overlay, and drills

## Source items

1. **“35 practical thoughts on system design.”** No author, date, or original URL supplied.
2. **“11 building blocks every engineer should know.”** Recommends load balancer, API gateway, application server, distributed cache, relational DB, NoSQL DB, message queue, object storage, rate limiter, search index, and CDN. It links two Grokking volumes below.
3. **“12 must-read newsletters.”** Resource recommendations below; rankings and “all free” claim were not independently checked.
4. **Codebases to study:** Redis, SQLite, Git, Quake III Arena, Go standard library, Linux kernel. The text also claims approximate source/test line counts, coverage, hardware performance, and readability qualities; most of these are undated, undefined, or subjective, so they are preserved as leads rather than facts.
5. **“One of the most underrated system design topics: scaling writes.”** No author, date, or source URL supplied. The post gives illustrative write-rate thresholds and recommends vertical scaling, partitioning/sharding, and queues for bursts.

## Assessment and corrections

- These are useful prompts, not laws. Apply every heuristic to a specified workload, invariant, latency/availability target, team, and cost budget.
- The “35 thoughts” map distinguishes generally useful principles from absolutes. For example: latency is the critical path (parallel work does not simply sum); selectivity alone does not determine index value; replication/partitioning can serve multiple purposes; event stores and queues solve different problems; observability uses logs, metrics, and traces together; a DLQ is one poison-message policy, not universally mandatory.
- The SQL-vs-NoSQL and write-scaling contrasts are simplified. A data store’s write/read properties depend on its model, engine, indexes, consistency settings, partition key, workload, and operational design. A poor shard key can create hotspots; queues absorb bursts only within storage/age limits and cannot fix sustained overload.
- The “1K/10K/100K writes per second” values and 3–5x burst are examples, not portable capacity thresholds.
- The 11 building blocks are categories, not components every design needs. A single API gateway can simplify policy but also become a critical dependency; “NoSQL” does not guarantee horizontal scaling; object storage and search indexes add separate consistency and lifecycle concerns.
- Study advice to read real code is useful if bounded: choose one question, trace the data/control path, inspect tests and failure handling, and record one design trade-off. A daily 30-minute habit or named project is a suggestion, not an evidence-backed requirement.

## Links extracted

### System-design book recommendations

- Grokking System Design Interview — https://lnkd.in/giwyzfkT
- Grokking System Design Interview, Volume II — https://lnkd.in/gzqcC4gK

### Newsletter recommendations

- The T-Shaped Dev — https://thetshaped.dev/
- System Design One — https://lnkd.in/dHfNRENN
- System Design Classroom — https://lnkd.in/d2NzrKc2
- Craft Better Software — https://lnkd.in/dGKSVZZj
- Engineering Leadership — https://lnkd.in/dykRMpPC
- Level Up Coding — https://lnkd.in/dGZ_XPMA
- Tech World With Milan Newsletter — https://lnkd.in/ddypDdZ2
- Algo Master — https://lnkd.in/dHs5VBcD
- Anton DevTips — https://antondevtips.com/
- Coding Challenges — https://lnkd.in/dtjsjCwJ
- .NET & Software Architecture — https://lnkd.in/dpcMf5CJ
- Hungry Minds — https://lnkd.in/d9uS_36v

## Primary references for claims that can be checked

- Redis describes command execution as mostly single-threaded while noting modern versions use threads for other work: https://redis.io/docs/latest/operate/oss_and_stack/management/optimization/benchmarks/
- SQLite documents its TH3 suite, branch/MC/DC coverage, and the fact that TH3 is proprietary: https://sqlite.org/testing.html
- Git’s object model (blobs, trees, commits, refs) can be studied in its internals documentation: https://git-scm.com/book/en/v2/Git-Internals-Git-Objects

## Routing

- `07-question-maps/system-design-principles-and-building-blocks-2026-09-23.md` — synthesis and conditional interpretation.
- `01-syllabus/software-architecture-hard-parts-overlay.md` — write scaling and component selection.
- `04-drills/software-architecture-hard-parts-drills.md` — scenario-based retrieval.
