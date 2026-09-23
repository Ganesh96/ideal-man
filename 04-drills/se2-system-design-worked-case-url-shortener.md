# Worked System Design Case: URL Shortener

This is a practice design, not an implementation or a claim of prior work. Numbers below are explicit assumptions so the method can be checked; change them if the interviewer provides different requirements.

## 1. Scope

**Functional requirements**
- Create a short link for a destination URL.
- Redirect a short code to the destination.
- Optionally allow owner-selected alias, expiry, disable/delete, and aggregate click analytics.

**Non-functional requirements**
- Redirect availability and low latency matter most.
- Link creation must not silently overwrite an existing code.
- Analytics can lag; redirect correctness cannot.
- Prevent abuse and protect user/privacy data.

**Clarify:** anonymous vs authenticated creation; custom domains; expiration; editability; redirect status (301/302); analytics granularity and retention; abuse/reporting policy.

Assume authenticated create, random short code, optional expiry, HTTP redirect, aggregate analytics with minutes of delay acceptable. No need to promise global active-active writes initially.

## 2. Workload estimate

Assume 10 million new links/month:
- Average create rate ≈ 10M / 30 days ≈ 3.9 creates/sec.
- Assume 10x peak: about 40 creates/sec.
- Assume 100 million redirects/day: average ≈ 1,160 redirects/sec. At 10x peak: ≈ 12,000/sec.
- At ~1 KB per link including an allowance for metadata/indexing, base records are ~10 GB/month before replication, analytics and backups.

The estimate shows redirects are read-heavy under these assumptions. State that traffic ratio and record size must be validated; popular links create skew.

## 3. API and data model

- `POST /v1/links` → destination, expiry, optional alias; return code and URL.
- `GET /{code}` → redirect response.
- `DELETE /v1/links/{code}` or disable endpoint → owner-authorized state transition.
- `GET /v1/links/{code}/stats` → delayed aggregates, if included.

Canonical link record: code (unique key), destination, owner, created time, expiry, status/version. Analytics events are separate appendable records or a stream; do not update a counter synchronously on every redirect unless strict per-click counting is needed.

## 4. Baseline architecture

1. DNS/CDN/WAF routes requests to a stateless redirect service behind a load balancer.
2. Link-creation service validates/authenticates requests and writes the authoritative mapping.
3. Redirect service checks an edge or distributed cache, then the mapping store on a miss.
4. Valid links return redirect; missing, disabled, and expired codes have distinct outcomes.
5. Click events are emitted asynchronously to a queue/stream and aggregated into analytics storage.

Start with a relational database if ownership, expiry, uniqueness, administrative queries and transactions dominate. A unique constraint on code is the final collision guard. At this assumed load, one primary plus read replicas and cache may be enough. A key-value mapping store becomes a candidate if the access pattern and measured scale justify its constraints. Do not choose a distributed store only because “the system may grow.”

## 5. Code generation and collision correctness

Generate a cryptographically secure random base62 code (for example, 8 characters). The theoretical namespace is 62^8 possibilities, but occupied codes and request volume still produce collisions. Attempt insert under a uniqueness constraint; on conflict, generate another code with a bounded retry. Custom aliases use the same uniqueness rule. Avoid predictable sequential IDs when enumeration/privacy matters.

A global counter avoids collision but creates coordination/hotspot and reveals volume. Snowflake-style IDs require time/worker coordination and do not automatically produce short, opaque codes.

## 6. Scale and latency

- Keep redirect handlers stateless and horizontally scalable.
- Cache hot mappings with TTL bounded by expiry and invalidation requirements. Negative caching can protect the store from repeated misses but needs a short TTL to avoid hiding newly created links.
- Use read replicas or partitioning only after measuring database saturation and observing replica freshness needs.
- A viral code can overload one cache key/backend partition. Replicate/cache locally, coalesce concurrent misses, and rate-limit abuse.
- Keep analytics off the critical redirect path; bound and monitor queue depth/lag.

## 7. Failure behavior and correctness

| Failure | Behavior |
|---|---|
| Cache unavailable | Fall back to mapping store with circuit breaker/bulkhead; protect database with admission control. |
| Mapping store unavailable | Serve safe cached mappings if policy permits; otherwise fail clearly. Never redirect to an unknown destination. |
| Duplicate create after client timeout | Use an idempotency key or request fingerprint with defined scope/retention; return the prior result. |
| Analytics queue outage | Redirect continues; buffer within a bound, then drop/sample analytics according to policy and alert. |
| Link expires while cached | Cache TTL cannot outlive expiry; check expiry at read or use expiry-aware cache entries. |
| Malicious destination/abuse | Validate scheme and policy, rate-limit creation, support reports/takedown, audit changes. URL validation alone does not prevent phishing. |

## 8. Security, privacy, operations

Authorize create/edit/stats by owner; protect admin controls. Avoid logging secrets or sensitive query strings by default. Define retention/deletion for mapping and analytics. Observe redirect p50/p95/p99, status/error rates, cache hit rate, store saturation, hot-key distribution, queue lag/drop rate, abuse signals, and restore/failover. Test expiry, failover, restore and duplicate delivery.

## 9. Trade-offs and extension triggers

- **Cache vs freshness:** cached redirects are fast; disabling/editing links may be delayed unless invalidation is reliable.
- **SQL vs key-value:** SQL simplifies relational management and uniqueness/admin queries; key-value fits direct lookup but shifts modeling/query burden.
- **Synchronous vs async analytics:** sync gives immediate counts but increases redirect latency and contention.
- **Regional replication:** add when geography/availability requires it; state whether stale reads or delayed link creation are acceptable.
- **Sharding:** add when measured capacity/working set or write throughput requires it; define key, skew handling and migration first.

## 10. Closing summary

“Under the assumed read-heavy traffic, I would start with a stateless redirect tier, a canonical mapping store with a unique code constraint, and bounded caching. Analytics runs asynchronously because its freshness requirement is weaker than redirect correctness. I would monitor cache effectiveness, store saturation, tail latency and hot keys. I would distribute the store only when measurements cross a defined capacity threshold, accepting additional consistency and operational work.”
