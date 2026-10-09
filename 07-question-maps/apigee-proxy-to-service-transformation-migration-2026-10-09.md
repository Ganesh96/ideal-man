# Case Study — Moving Transformations from Apigee Proxy to Service

## Scenario
Current:
Client -> Apigee proxy -> transformation/mapping -> backend service -> downstream services

Target:
Client -> Apigee proxy (edge/cross-cutting concerns) -> backend service owns transformation/business mapping -> downstream services

## Core architecture question
Where should transformation logic live?

Classify the transformation before deciding:
- edge/policy transformation: auth headers, routing metadata, protocol mediation, coarse request normalization
- contract adaptation: legacy external schema -> internal canonical/service schema
- business transformation: domain rules, derived fields, enrichment, validation tied to domain semantics
- downstream-specific mapping: service-owned request mapping for a dependency

Default ownership heuristic:
- gateway owns cross-cutting edge policy
- service owns domain/business semantics and downstream-specific mapping
- explicit adapter/BFF/anti-corruption layer may own compatibility logic when boundary complexity justifies it

## Why teams move logic out of a gateway
Potential gains:
- domain logic moves closer to domain owner
- easier unit/integration testing and local debugging
- reduced vendor/gateway lock-in
- clearer service ownership
- simpler gateway and lower policy sprawl
- change/deploy cadence follows service team
- richer language/tooling for transformation

Potential costs:
- service becomes larger/more complex
- multiple services may duplicate edge-normalization logic
- migration can break external contracts
- latency/resource use may move downstream
- observability must cover both gateway and service
- rollback/version compatibility become essential

## Coupling model
Gateway transformation can create:
- contract coupling: proxy schema assumptions
- deployment/change coupling: proxy and service must change together
- vendor coupling: behavior encoded in Apigee-specific policy
- semantic coupling: business rules hidden at edge

Moving transformation does not remove coupling; it relocates it. Verify whether the new owner is the correct bounded/domain owner.

## Data/API contract checklist
Define:
- producer and consumer
- request/response schema
- required vs optional fields
- null/default semantics
- enums and unknown-value behavior
- field meaning/units/time zone/precision
- validation ownership
- error contract
- backward/forward compatibility
- versioning/deprecation policy
- sensitive fields and logging policy
- idempotency/correlation keys where relevant

Useful artifacts:
- OpenAPI / JSON Schema / protobuf schema
- contract tests
- example payloads / golden fixtures
- compatibility rules and deprecation timeline

## Test strategy during migration
1. Unit tests for pure transformation rules in service.
2. Gateway policy tests: routing/auth/header/passthrough behavior.
3. Service contract tests against external/client-facing schema.
4. Downstream contract tests for service -> dependency mapping.
5. End-to-end integration tests across Apigee -> service -> downstream.
6. Golden input/output parity tests comparing old proxy transformation vs new service transformation.
7. Negative/boundary tests: missing fields, unknown enum, malformed data, nulls, oversized payload, timeout, downstream failure.
8. Shadow/dual-run or canary where possible; compare responses/side effects before full cutover.
9. Rollback test and compatibility window.

## Observability
End-to-end request path should propagate:
- correlation/request ID
- distributed trace context
- service/downstream span IDs

Observe three signal families:
- logs: structured events with request/trace correlation; avoid secrets/PII
- metrics: rate, errors, latency, saturation; contract/validation failures
- traces: gateway -> service -> downstream timing and error path

Datadog can correlate logs, metrics, and distributed traces. Equivalent categories may be implemented with OpenTelemetry + another backend.

Questions from downstream logs:
- Did request leave gateway?
- Did service receive expected transformed shape?
- Which downstream was called?
- What payload metadata/version was used?
- Where did latency accumulate?
- Was failure transport, validation, contract, business rule, or dependency?
- Did retries duplicate any side effect?

## Rollout pattern
Current -> target migration:
1. inventory transformation rules
2. classify edge vs domain vs adapter logic
3. write explicit contract and invariants
4. reproduce transformation in service
5. build parity tests
6. deploy service backward-compatible
7. optionally shadow/dual-run and diff outputs
8. move traffic gradually
9. monitor error/latency/contract metrics
10. remove old proxy transformation only after stability window
11. keep rollback path for defined period

## Senior-engineer reasoning
Ask:
- Why are we moving it? Maintainability, ownership, latency, security, cost, testability?
- Is transformation domain logic or edge policy?
- Who owns the contract?
- What clients still depend on old shape?
- Can proxy and service versions be deployed independently?
- What is the blast radius of a schema change?
- What is the rollback mechanism?
- How will we prove semantic parity?
- What happens under partial failure?
- How will logs/traces identify the failing hop?
- Are data/privacy rules preserved after logic moves?

## Book map
Software Architecture: The Hard Parts:
- Ch 1: trade-offs, ADR, fitness functions
- Ch 2: static/dynamic coupling
- Ch 3: modularity, maintainability, testability, deployability
- Ch 7: service scope/granularity and security
- Ch 13: strict/loose contracts, stamp coupling
- Ch 15: trade-off analysis

DDIA:
- Encoding and Evolution: schema compatibility, service/dataflow contracts
- distributed failure/retries where downstream calls are involved

## Interview drill
"You inherit an API where Apigee performs a large request transformation before forwarding to a service. The team wants to move transformation into the service. Walk through how you decide what moves, how you test correctness, how you roll it out without breaking consumers, and how you diagnose failures in production."
