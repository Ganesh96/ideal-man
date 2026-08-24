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
