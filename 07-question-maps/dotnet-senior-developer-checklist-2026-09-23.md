# Senior .NET Developer Checklist Map — 2026-09-23

Source: checklist image supplied in conversation. The source labels itself “based on real LinkedIn job posts (2026),” but provides no sample, role mix, geography, or methodology. Treat this as a menu for gap analysis, not a market census or a mandate to learn every vendor.

This is a supplemental map for the retained .NET interview syllabus. The syllabus remains paused at Batch 1; this file does not mark any topic as learned or change the active learning track.

## Extracted checklist

### .NET and API development
- C# (latest language features)
- ASP.NET Core
- Minimal APIs
- Web APIs / REST
- GraphQL
- gRPC
- SignalR
- Background services

### Cloud and infrastructure
- Azure App Service, Functions, AKS
- AWS Lambda, ECS
- Terraform, Bicep
- Cloud cost optimization

### Data
- SQL Server, PostgreSQL
- Cosmos DB, MongoDB
- Redis
- EF Core, Dapper
- Database migrations

### DevOps and delivery
- GitHub Actions, Azure DevOps
- Docker
- Kubernetes / Helm
- CI/CD pipelines
- Feature flags
- GitOps

### Security
- OAuth 2 / OpenID Connect
- JWT validation
- RBAC / policy-based authorization
- OWASP Top 10
- Secret management

### Messaging
- RabbitMQ, Kafka, Azure Service Bus
- Event-driven architecture
- Publish / subscribe

### Observability
- OpenTelemetry
- Structured logging
- Distributed tracing
- Grafana / Prometheus
- Health checks

### Architecture
- Microservices
- Domain-Driven Design
- Vertical slices
- Design patterns
- API versioning
- System design

### Testing
- xUnit
- Integration tests
- Testcontainers
- Mocking frameworks
- Load testing

## Turn the checklist into a learnable syllabus

### Priority 1 — Backend fundamentals
Build on the current .NET syllabus:
- HTTP request pipeline, middleware, dependency injection, configuration, validation, error handling.
- REST contract design, status/error models, pagination, versioning, authn/authz.
- SQL fundamentals, transaction boundaries, query plans/indexes, EF Core tracking and migrations.
- Async/await, cancellation, thread-pool behavior, connection pooling, and background services.
- Unit plus integration tests; use a real database/container when behavior depends on provider semantics.

### Priority 2 — Production application behavior
- Structured logs, metrics, traces, correlation, health/readiness checks.
- Timeouts, retry bounds, circuit breaking, idempotency, queue acknowledgements, poison messages.
- Secret handling, OAuth/OIDC/JWT validation, authorization policies, least privilege.
- Docker image build and deployment pipeline; environment config and safe schema rollout.
- Measure latency percentiles, throughput, saturation, error rate, queue age, and cost.

### Priority 3 — Architecture and cloud choices
- Modular monolith and domain boundaries before distributed-service extraction.
- Pick one cloud and one IaC tool based on target roles; understand identity, networking, storage, observability, availability, and costs.
- Compare App Service/Functions/AKS or Lambda/ECS for workload shape, scaling, operational control, cold start, cost, and team capacity.
- Select a relational, document, key-value/cache, search, or event-log store from access patterns and consistency requirements.
- Add Kafka/RabbitMQ/managed bus only where durable async communication or replay/fan-out needs justify it.

### Specialization topics — learn when target roles require them
GraphQL, gRPC, SignalR/WebRTC, Kubernetes internals, GitOps, Cosmos DB/MongoDB, Kafka, and advanced DDD should be applied in a small project or interview case, not memorized as checkbox definitions.

## Evidence of competence

For a technology you claim to know, prepare one real example with:
1. requirement and workload;
2. alternatives you considered;
3. implementation boundary and your specific contribution;
4. test or production evidence;
5. operational issue/failure and response;
6. limits of the result and what you would change next.

Do not claim a tool from a checklist as professional experience without having used it. A small, clearly labeled learning project can demonstrate practice, but is not employment experience.

## Interview prompts

1. When would you choose Minimal APIs vs controllers, and what cross-cutting behavior must stay consistent?
2. When does EF Core help, and when would Dapper or hand-written SQL be justified? How would you compare correctness and measured performance?
3. How do you propagate cancellation and deadlines through ASP.NET Core, a queue, and downstream calls?
4. How do you make a background consumer safe under redelivery and process restart?
5. How would you deploy a schema change while old and new application versions overlap?
6. How would you diagnose rising API p99 latency? Which traces, metrics, logs, query plans, and resource signals would narrow the cause?
7. What is the difference between authentication and authorization? Where are token signature, issuer, audience, expiry, and scope/role checked?
8. When should a modular monolith become separate services? State the independent deployment, ownership, scaling, or isolation force that pays for the added network boundary.
9. What does a health check prove, and what should liveness/readiness checks avoid doing?
10. How do you limit cloud cost while preserving the agreed SLO and recovery objective?

## Source links

The input’s job-market summary has no direct job-post citations. Verify the target employer’s current requirements from its actual job postings before using this checklist to prioritize study.
