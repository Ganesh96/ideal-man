# Walmart R-2606196 — Staff Software Engineer Interview Syllabus

## Target
Walmart Global Tech — Staff, Software Engineer (R-2606196), Change Engineering.

The role is a hands-on Staff position at the intersection of software engineering, distributed systems, cloud/platform engineering, enterprise integration, production operations, and AI/ML. Preparation must therefore combine:
1. coding/problem solving,
2. system design,
3. architecture and trade-off reasoning,
4. production reliability/observability,
5. enterprise integration/change-engineering concepts,
6. AI/ML/LLM production systems,
7. project deep dives,
8. Staff-level leadership and behavioral judgment.

The resume is not merely background material. Every claim is an interview surface and must become something that can be explained, diagrammed, defended, stress-tested, and connected to alternatives.

---

## Study method for every resume claim

For every bullet, be able to answer:

### Mechanism
- What was the architecture before and after?
- What components existed?
- Where was state stored?
- What happened synchronously vs asynchronously?
- What exact algorithm/pattern/data structure/tool was used?
- How did data move through the system?

### Why
- What problem existed?
- What requirement or production symptom forced the change?
- Why this option over alternatives?
- What trade-off was accepted?

### Correctness
- What invariants had to remain true?
- What failure windows existed?
- How were duplicates, retries, partial failures, ordering, consistency, schema changes, and concurrency handled?
- What tests or validation proved the change worked?

### Scale/performance
- QPS/events/sec/jobs/day/data/day/users.
- Read/write ratio.
- latency p50/p95/p99 where meaningful.
- storage and growth.
- capacity/bottleneck analysis.
- what would fail at 10x?

### Operations
- logs, metrics, traces, dashboards, alerts.
- SLI/SLO.
- retry/backoff/circuit breaker/timeouts.
- rollout/rollback.
- incident diagnosis and recovery.

### Staff lens
- Who else was affected?
- What decision needed alignment?
- What standard/reusable pattern emerged?
- What risks did you identify before implementation?
- How did you influence peers/stakeholders?
- What would you redesign now?

---

# Track 1 — Distributed Systems and Service Architecture

## Resume anchors
- clear service boundaries
- asynchronous processing
- durable job state
- idempotent retries
- Kafka consumers
- event-driven workflows
- retry-safe event handling
- partial downstream failure
- versioned REST contracts
- long-running asynchronous workers

## Learn deeply
- sync vs async communication
- queues vs pub/sub vs logs
- Kafka partitions, consumer groups, ordering, offsets
- at-most-once / at-least-once / effectively-once
- idempotency and idempotency keys
- transactional outbox/inbox
- retries, exponential backoff, jitter
- poison messages and DLQs
- backpressure
- circuit breakers and bulkheads
- workflow state machines
- sagas and compensating actions
- orchestration vs choreography
- service boundaries, cohesion, coupling, architecture quanta
- API and event contract evolution
- distributed transactions and eventual consistency

## Proof questions
- Why did asynchronous processing help?
- What new failure modes did it introduce?
- What happens if a consumer commits state but crashes before acknowledgement?
- What happens if messages arrive twice or out of order?
- When is eventual consistency unacceptable?
- How would you migrate from a shared database to service-owned data?
- How would you prove service independence rather than merely drawing separate boxes?

---

# Track 2 — APIs, Contracts, Enterprise Integration

## Resume anchors
- Java/Spring Boot APIs
- REST/OpenAPI
- versioned REST contracts
- API-contract checks in CI
- integration endpoints
- authorization context
- MCP-style tools
- external payer/payment/integration systems

## Walmart alignment
The role explicitly emphasizes REST APIs, event-driven systems, webhooks, asynchronous workflows, system-to-system integration, data consistency, lineage, traceability, and reusable integration patterns.

## Learn deeply
- resource-oriented API design
- HTTP semantics and idempotency
- pagination/filtering/versioning
- strict vs tolerant contracts
- OpenAPI/JSON Schema/protobuf concepts
- backward/forward compatibility
- schema evolution
- consumer-driven contract testing
- API gateway responsibilities
- webhooks and retry/security models
- correlation/causation IDs
- canonical model vs point-to-point transformations
- anti-corruption layer / adapters
- ServiceNow/ITSM concepts: change request, approval, scheduling, validation, verification
- enterprise topology/configuration/policy/incident integration
- data lineage and auditability

## Case study
Apigee transformation migration:
- classify edge-policy vs business transformation
- decide ownership
- contract parity tests
- downstream observability
- migration/rollback

---

# Track 3 — Reliability, Observability, and Operational Excellence

## Resume anchors
- production failure modes
- correlation IDs
- audit events
- production RCA
- retry exhaustion
- rollback
- partial service failure
- 99.99% availability claim
- sub-second views / p95 reduction

## Walmart alignment
The role explicitly asks for SLO/SLI design, observability, alerting, bottleneck analysis, proactive telemetry-driven improvement, failure handling, recovery, rollback, graceful degradation, and operational readiness.

## Learn deeply
- availability/reliability/durability distinctions
- SLI, SLO, SLA
- error budgets
- RED and USE signals
- logs vs metrics vs traces
- distributed tracing
- correlation IDs
- cardinality and telemetry cost
- alert design and alert fatigue
- health/readiness/liveness
- timeout budgets
- graceful degradation
- load shedding
- fault isolation
- recovery and rollback
- RTO/RPO
- chaos/failure-injection thinking
- postmortems and RCA
- capacity headroom

## Proof questions
- What does 99.99% availability mean numerically?
- Which failure domains were isolated?
- What telemetry would distinguish application failure from dependency failure?
- What happens if logging/telemetry backend itself is unavailable?
- What metric proves a latency optimization did not damage correctness?

---

# Track 4 — Data Systems, Databases, Caching, and Scale

## Resume anchors
- PostgreSQL/TimescaleDB
- SQL Server/Oracle/MongoDB/Redis/DynamoDB/Neo4j/PostGIS/pgvector
- time-based partitions
- composite indexes
- cached projections
- read/write workload separation
- query tuning
- HNSW/index tuning
- 42s -> 4.5s query improvement
- p95 1.4s -> 320ms
- 10GB+ daily data

## Learn deeply
- indexes: B-tree, composite, covering, selectivity, write cost
- query plans
- partitioning and sharding
- replication
- leader/follower basics
- read replicas
- consistency and replication lag
- transaction isolation
- optimistic/pessimistic concurrency
- cache-aside/read-through/write-through/write-behind
- cache invalidation
- TTL
- stampede/thundering herd
- hot keys
- relational vs document vs key-value vs graph vs time-series
- vector indexes and approximate nearest neighbor trade-offs
- HNSW concepts
- source of truth vs derived projections
- OLTP vs analytical workloads
- capacity/storage estimates

## Proof questions
- Why was a given index chosen?
- What is the write amplification?
- Why TimescaleDB vs plain PostgreSQL?
- What happens when cached data is stale?
- Why Redis candidate cache vs querying pgvector directly?
- What does 10x data volume change?

---

# Track 5 — Performance and Capacity Engineering

## Resume anchors
- sub-second analytical views
- 10K+ events/sec
- 200K+ embeddings/day
- 50K+ transactions/day
- 50K+ daily users
- p95 1.4s -> 320ms
- 5s -> 500ms
- 42s -> 4.5s

## Learn deeply
- back-of-the-envelope estimation
- throughput vs latency
- Little's Law intuition
- p50/p95/p99
- queueing effects
- CPU/memory/network/I/O bottlenecks
- connection pools
- batch size
- concurrency
- horizontal vs vertical scaling
- load balancing
- saturation
- critical-path analysis
- profiling
- performance test design
- capacity planning

## Requirement
For every metric on the resume, know:
- baseline
- bottleneck
- intervention
- measurement method
- before/after
- trade-off
- remaining limit

---

# Track 6 — AI/ML/LLM Production Systems

## Resume anchors
- Amazon Bedrock
- LangChain
- LangGraph
- MCP-style tools
- semantic retrieval
- embeddings
- pgvector / Redis vector search
- model-assisted research workflows
- deterministic services retaining execution ownership
- authorization boundaries around model output

## Walmart alignment
The role explicitly asks for anomaly detection, classification, recommendation, risk scoring, LLM reasoning, retrieval/grounding/context management, evaluation, explainability, monitoring, guardrails, fallbacks, and continuous improvement.

## Learn deeply
- RAG pipeline
- embeddings and similarity
- retrieval precision/recall
- chunking
- reranking
- metadata filtering
- vector index trade-offs
- prompt/context management
- model vs retrieval failure
- tool calling
- agent state and workflow design
- deterministic vs probabilistic boundaries
- authorization around tools
- prompt injection and retrieval poisoning
- evaluation datasets
- offline vs online evaluation
- hallucination/groundedness
- fallback models/paths
- latency/cost/quality trade-offs
- explainability and traceability
- model/version monitoring
- anomaly detection/classification/risk scoring fundamentals

## Staff-level question
How would you build an AI-assisted change-risk system that uses topology, incident history, configuration data, deployment metadata, and change descriptions while remaining explainable and safe enough for production approval workflows?

---

# Track 7 — Cloud, Containers, CI/CD, and Platform Engineering

## Resume anchors
- AWS ECS/Lambda/S3/RDS/IAM
- Azure
- Docker
- Kubernetes
- GitHub Actions
- build/test gates

## Walmart alignment
The role centers on platform engineering, cloud integration, safe technology change, and reusable platform capabilities.

## Learn deeply
- containers/images/registries
- Kubernetes: pods, deployments, services, config/secrets, probes, autoscaling
- ECS vs Kubernetes conceptual trade-offs
- IAM/least privilege
- CI vs CD
- deployment strategies: rolling, blue-green, canary
- feature flags
- schema compatibility during rollout
- rollback
- infrastructure/config change safety
- secrets
- environment promotion
- test gates
- operational readiness review

---

# Track 8 — Application, API, Cloud, and Supply-Chain Security

Security is part of backend correctness, not a separate specialist topic. The goal is to design services that preserve confidentiality, integrity, availability, authorization boundaries, auditability, and recoverability under realistic misuse and compromise.

## P0 — Backend engineer must know deeply

### Threat modeling and architecture
- threat modeling: assets, actors, entry points, abuse cases, mitigations
- attack surface
- trust boundaries
- least privilege
- defense in depth
- blast radius
- secure defaults and fail-closed vs fail-open decisions
- authentication vs authorization
- authorization at service, resource, and data boundaries
- broken object-level authorization / IDOR
- multi-tenant isolation
- network segmentation and zero-trust principles

### Identity, authentication, and credentials
- OAuth 2.x roles and flows at a conceptual/implementation level
- OpenID Connect and how it differs from OAuth
- access token vs ID token
- session management, cookies, expiry, revocation, rotation
- JWT validation pitfalls: issuer, audience, signature, algorithm, expiry, key rotation, over-trusting claims
- MFA and phishing-resistant authentication
- understand why SMS-based MFA is weaker than authenticator/passkey/security-key approaches: SIM-swap, interception, and phishing exposure
- passkeys/WebAuthn conceptually; backend challenge/origin/credential lifecycle responsibilities
- password storage: salts, adaptive hashing, bcrypt/Argon2; never reversible encryption for passwords
- short-lived credentials
- IAM roles/workload identities vs static access keys
- secrets management; no credentials in code, images, logs, or source control
- credential/key rotation

### API and input security
- validate and constrain untrusted input
- SQL injection
- command injection
- prompt injection when LLM/tool systems are involved
- SSRF
- unsafe deserialization / parser boundary awareness
- rate limiting and abuse controls
- CORS: browser-origin policy, not authentication or authorization
- webhook authentication/signatures and replay protection
- secure file upload boundaries where applicable
- API gateway security responsibilities vs service-owned authorization

### Transport and data protection
- TLS: what it protects and what it does not
- certificate chain / hostname validation at a practical level
- encryption in transit vs encryption at rest
- key ownership and rotation
- sensitive-data classification
- avoid leaking secrets/PII through logs, traces, exceptions, analytics, or model prompts

### Secure operations
- audit logs: who/what/when/outcome, tamper resistance, access control, retention
- prevention vs detection
- security monitoring and actionable alerts
- incident response fundamentals: detect -> contain -> eradicate -> recover -> learn
- patch management
- backup/restore strategy
- prove backups through restoration tests; a backup that has never been restored is an unverified recovery mechanism
- RTO/RPO and recovery access controls

## P1 — Important supporting knowledge

### Browser-facing security
- XSS: stored/reflected/DOM concepts and backend encoding/content-handling responsibility
- CSRF: when cookie-based authentication creates risk; SameSite/CSRF-token concepts
- security headers, especially Content-Security-Policy
- cookie attributes: Secure, HttpOnly, SameSite
- CORS configuration and preflight behavior

### Software supply chain
- dependency provenance and supply-chain attacks
- lockfiles and dependency pinning
- controlled dependency upgrades
- vulnerability scanning
- SBOM purpose
- signed artifacts/provenance concepts
- CI/CD credential isolation
- branch/review/build gates
- avoid secrets in build logs and artifacts

### Container and workload isolation
- minimal/base-image hygiene
- non-root containers
- image scanning and patching
- read-only filesystems / dropped capabilities where practical
- secrets injected at runtime rather than baked into images
- Kubernetes/service-account/RBAC concepts
- sandboxing and isolation boundaries
- host/container boundary awareness

### Vulnerability and risk triage
- CVE vs CVSS
- CVSS is severity context, not a complete business-risk decision
- exploitability, reachability, asset criticality, exposure, and compensating controls
- remediation prioritization

## P2 — Know conceptually; do not over-invest for backend interview prep
- phishing and social engineering patterns
- detailed WebAuthn cryptography
- PKI internals beyond practical certificate/TLS debugging
- advanced exploit development
- security-operations tooling internals unless the role specifically asks for them

## Security reasoning loop for backend/system design

For every externally reachable component ask:
1. What asset/state am I protecting?
2. Who is the caller and how is identity established?
3. What exactly is the caller authorized to do?
4. Where are the trust boundaries?
5. Which inputs are untrusted?
6. What happens if a credential/token is stolen?
7. What happens if a downstream dependency is malicious or compromised?
8. What is logged, and could logs themselves leak sensitive data?
9. Can abuse exhaust CPU, memory, DB connections, queues, or external-provider quota?
10. What is the smallest blast radius if this service is compromised?
11. How are keys/secrets rotated?
12. How do we detect abuse/compromise?
13. How do we recover and prove recovery works?

## Interview/application cases
- Design secure authentication/authorization for a multi-tenant API.
- A user changes /users/123 to /users/124 and sees someone else's record. Identify the failure and fix the authorization model.
- Design a webhook consumer that is safe under spoofing and replay.
- A service on AWS needs database credentials. Compare static keys/passwords with IAM/workload identity and short-lived credentials.
- A backend fetches user-supplied URLs. Analyze SSRF risk.
- Design a secure file-upload or document-processing pipeline.
- Design rate limiting that protects both users and downstream capacity.
- An API uses JWTs. Explain validation, revocation/expiry trade-offs, key rotation, and why JWT does not eliminate server-side authorization.
- A container image contains a critical CVE. Explain how severity, reachability, exploitability, exposure, and rollback affect the decision.
- Your backups succeed nightly. Explain how you know you can actually recover.

## Cross-links to other tracks
- Track 1: retries/idempotency can become abuse surfaces; event consumers require authorization/trust assumptions.
- Track 2: contracts must define authentication, authorization context, sensitive fields, and webhook integrity.
- Track 3: security detection uses the same logs/metrics/traces but with stronger retention/access/tamper considerations.
- Track 6: prompt injection, tool authorization, data leakage, retrieval poisoning, and deterministic permission boundaries.
- Track 7: IAM, secrets, container hardening, CI/CD supply chain, deployment credentials.
- Track 9/10: change risk, audit evidence, blast radius, rollback, and patching.
- System design: security requirements are first-class non-functional requirements, not a final checklist.

---

# Track 9 — Change Engineering and Enterprise Operations

This is the domain-specific gap to close because the Walmart team is Change Engineering.

## Learn deeply
- why enterprises formalize technology changes
- standard / normal / emergency changes
- change request lifecycle
- approval routing
- maintenance windows
- dependency/impact analysis
- blast radius
- pre-change validation
- post-change verification
- configuration/topology/dependency graph
- incident/change correlation
- change failure rate
- deployment frequency
- MTTR
- rollback rate
- policy/compliance evidence
- audit trail
- ITSM/ServiceNow fundamentals
- automated risk scoring
- change health signals
- progressive delivery

## System-design target
Design an enterprise Change Intelligence Platform:
- ingest changes/deployments/config/topology/incidents
- construct dependency context
- calculate risk
- route approvals
- schedule changes
- monitor rollout
- verify health
- trigger rollback/escalation
- preserve audit lineage

---

# Track 10 — System Design

## Core designs
1. Distributed rate limiter
2. Notification platform
3. Job scheduler
4. Event ingestion platform
5. Multi-tenant API platform
6. Distributed cache
7. Metrics/alerting platform
8. Workflow orchestrator
9. Search/recommendation platform
10. Enterprise Change Intelligence / risk platform

## Mandatory reasoning order
1. Clarify functional requirements
2. Identify invariants
3. Define SLOs / latency / availability / consistency
4. Estimate scale
5. Define API/event contracts
6. Model data and ownership
7. Draw simplest viable architecture
8. Walk critical request/data paths
9. Identify bottlenecks
10. Test partial failures
11. Handle retries/duplicates/order/concurrency
12. Add security/observability
13. Design rollout/recovery
14. State explicit trade-offs
15. Identify what requirement change would reverse the design

---

# Track 11 — Coding and Problem Solving

The exact Walmart interview sequence is not assumed here; coding remains a core Staff SWE capability.

## Pattern syllabus
- arrays/hash maps
- two pointers/sliding window
- stack/queue
- intervals
- binary search
- linked lists
- trees/BST
- heaps/top-k
- graphs: BFS/DFS/topological sort
- shortest path
- union-find
- recursion/backtracking
- dynamic programming
- prefix sums
- tries where relevant

## Interview discipline
For each problem:
1. restate
2. examples/edge cases
3. brute force
4. identify bottleneck
5. derive optimized approach
6. state invariant
7. prove correctness informally
8. complexity
9. implement
10. test normal/boundary/failure cases

The goal is not memorized solutions; it is controlled reasoning and proof.

---

# Track 12 — Resume Project Deep Dives

## A. University of Florida
Prepare:
- architecture diagram
- API -> job state -> workers -> data stores -> results
- why queue-backed/long-running execution
- checkpoint model
- idempotent retry model
- TimescaleDB partition/index choices
- Redis caching
- Bedrock/LangGraph tool boundary
- schema/data-validation gates
- 10GB/day and sub-second claim measurement
- failure/rollback stories

## B. Maxil
Prepare:
- transactional source of truth vs retrieval projection
- Kafka event flow
- 10K+ events/sec claim
- 200K embeddings/day pipeline
- pgvector/HNSW
- Redis cache
- p95 1.4s -> 320ms
- eventual consistency
- authorization boundary around AI/tool use
- 50K+ daily user release/contract checks

## C. BestRx
Prepare:
- claims/payment state machine
- external payer/payment dependency failure
- idempotency/reconciliation
- Kafka + SQL Server
- 50K+ transactions/day / 500+ pharmacies
- 99.99% availability
- clinical enrichment caching
- 5s -> 500ms
- audit/correlation/rollback
- duplicate/timeouts/retry exhaustion tests

## D. Autoreview.ai
Prepare:
- asynchronous document workflow
- model/inference failure
- raw source vs derived outputs
- vector retrieval
- S3/database ownership
- PostGIS enrichment
- replayability
- 5K sites/day and 10K documents

## E. Infosys / Bank of America
Prepare:
- AML case lifecycle
- batch/integration architecture
- query optimization 42s -> 4.5s
- Oracle indexes/query plans
- idempotent feeds
- release/regression process
- enterprise stakeholder coordination
- audit correctness

---

# Track 13 — Staff-Level Leadership and Situational Judgment

## Themes
- technical direction
- influence without authority
- design reviews
- conflicting proposals
- standards/reusable patterns
- mentoring
- cross-team migrations
- technical debt prioritization
- incident leadership
- ambiguity
- disagreement
- trade-off communication
- production ownership
- simplification/modernization

## Story bank to build
Prepare at least one real story for:
1. architecture decision
2. production incident
3. difficult debugging
4. disagreement
5. migration
6. performance optimization
7. reliability improvement
8. mentoring/helping another engineer
9. requirement ambiguity
10. failure/mistake and correction
11. influencing a broader team
12. simplifying an over-complex solution

For every story:
Context -> Stakes -> Constraints -> Options -> Decision -> Your action -> Result -> What changed afterward -> What you learned.

---

# Resource Mapping

Do not study sources linearly merely because they exist.

For every technical book / Pluralsight course / Educosys module provided later, map it into:
- role requirement,
- resume claim,
- system-design concept,
- coding pattern,
- Staff behavior,
- prerequisite,
- priority (P0/P1/P2),
- retrieval drill,
- mock-interview question.

Priority rule:
- P0: directly required by Walmart role + appears on resume
- P1: directly required by role but weaker/no resume evidence
- P2: useful depth or adjacent knowledge

---

# First Evening Study Session

Target: establish the highest-value foundation, not cover many topics.

## Block 1 — 45 min: Role + resume defense map
Read:
- Walmart responsibilities
- resume summary
- UF, Maxil, BestRx bullets

Write one page:
- 5 strongest alignment points
- 5 weakest/gap areas
- 3 strongest project stories

Immediate gap candidates:
- Change Engineering / ITSM / ServiceNow
- enterprise topology/configuration/incident integration
- formal SLI/SLO/error-budget reasoning
- AI evaluation/risk scoring/explainability
- Staff cross-team influence narratives

## Block 2 — 75 min: Distributed-systems foundation
Study/retrieve:
- sync vs async
- queue/log/pub-sub
- retries + idempotency
- outbox/inbox
- eventual consistency
- saga
- timeout/circuit breaker/backpressure

Use BestRx and UF as concrete examples.

Output:
Explain one end-to-end failure:
"DB commit succeeds, publish/ack fails. What happens and how is correctness preserved?"

## Block 3 — 60 min: System design
Prompt:
"Design a reliable workflow orchestration system."

Do only:
- requirements
- scale assumptions
- APIs/events
- data model/state machine
- high-level architecture
- failure paths
- observability

No polishing. The objective is to expose gaps.

## Block 4 — 45 min: Coding
Solve 1 medium problem cold.
Required output:
- brute force
- optimized idea
- invariant
- complexity
- tests

## Block 5 — 30 min: Project deep dive
Take BestRx.
Explain aloud:
- request/data flow
- transaction states
- retries
- idempotency
- reconciliation
- failure handling
- observability
- availability claim
- one alternative design and why not

## Closeout — 15 min
Record:
- 3 concepts that were weak
- 2 resume claims that were hard to defend
- 1 system-design decision you could not justify
These become tomorrow's first review targets.

---

# Readiness Rubric

Score each topic 0-4:
- 0 = unfamiliar
- 1 = recognize terminology
- 2 = can explain mechanism
- 3 = can apply and compare trade-offs
- 4 = can defend under adversarial follow-ups and connect to production evidence

Interview-ready means mostly 3-4 on P0 material.

The Staff bar is not "I know Kafka/Redis/Kubernetes."
It is:
"I can identify when the mechanism is justified, explain how it fails, select among alternatives, prove the critical invariants, operate it in production, and communicate the decision across teams."
