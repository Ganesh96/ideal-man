# System Design, Netflix, and .NET Checklist — Source Intake

Date received: 2026-09-23  
Status: processed into concept taxonomy, supplemental .NET checklist, architecture overlay, and drills.

## Intake rules

- Shortened LinkedIn links are retained as source pointers, not treated as evidence.
- Lists and diagrams are syllabus signals; they are not automatically technically correct or a recommended design.
- Company architecture claims need the linked engineering article or an authoritative technical source before being repeated as company fact.
- The supplied Netflix container piece links to Netflix TechBlog. The article exists as an official Netflix post: [Mount Mayhem at Netflix: Scaling Containers on Modern CPUs](https://netflixtechblog.com/mount-mayhem-at-netflix-scaling-containers-on-modern-cpus-f3b09b68beac), published Nov. 7, 2025. Treat the long text supplied here as a paraphrase; for numbers, causal claims, and implementation details, read the article itself.
- The image of the .NET checklist is legible in the conversation and transcribed below. No local copy was available to attach to the repository.

## Source inventory

### Social-post and reference lists

- “12 System Design Concepts in Plain English”; includes the claim “I’ve worked at Microsoft, Amazon, and Salesforce,” the shortlink [12 patterns](https://dub.sh/12-patterns), and the [Alexandre Zajac LinkedIn profile](https://www.linkedin.com/in/alexandre-zajac/).
- “98 System Design Concepts” list: the terms are preserved and grouped in [the concept taxonomy](../07-question-maps/system-design-concept-taxonomy-2026-09-23.md).
- Netflix system-patterns post: Hystrix/circuit breaker, Chaos Monkey, event sourcing, CQRS, Prana/sidecar, Zuul/edge gateway, eventual consistency, and adaptive-bitrate streaming.
- API-type post: REST, GraphQL, internal APIs, security-first design.
- Staff/Lead/Architect concept map: API gateway, microservices, scaling, replication/sharding, consistent hashing, caching, rate limiting, circuit breaking, REST/gRPC, Kafka/RabbitMQ, OAuth/JWT, saga, idempotency, election, failover, and heartbeats.
- Image-processing interview cheat sheet: requirements and baseline ingest → queue → worker → storage architecture.
- “System Design Metro Map” and system case-study list (15 LinkedIn shortlinks):
  1. YouTube — https://lnkd.in/e7q9F4Sg
  2. Spotify — https://lnkd.in/eGbWVeNW
  3. Reddit — https://lnkd.in/egmm_P7a
  4. Google Search — https://lnkd.in/exsvNqFn
  5. WhatsApp — https://lnkd.in/eU2fswMi
  6. Bluesky — https://lnkd.in/eEhB8V_k
  7. Stock Exchange — https://lnkd.in/eNf2QxVZ
  8. Airbnb — https://lnkd.in/dGVfstQM
  9. LLMs / ChatGPT — https://lnkd.in/eSd6fS7n
  10. URL Shortener — https://lnkd.in/evFTZVQq
  11. Tinder — https://lnkd.in/en65fv-W
  12. Twitter Timeline — https://lnkd.in/eniXMPfU
  13. Uber Payment System — https://lnkd.in/ecVw7jfi
  14. Slack — https://lnkd.in/eATMDjrK
  15. Kafka — https://lnkd.in/eTtVAjTg
- Senior .NET developer post and checklist image. The post claims its checklist is based on LinkedIn job listings; the underlying sample, companies, and date range were not supplied.

### Official and primary references for focused study

- Netflix container article: [Mount Mayhem at Netflix](https://netflixtechblog.com/mount-mayhem-at-netflix-scaling-containers-on-modern-cpus-f3b09b68beac)
- Linux kernel: [VFS documentation](https://docs.kernel.org/filesystems/vfs.html), [mount API](https://docs.kernel.org/filesystems/mount_api.html), and [NUMA documentation](https://www.kernel.org/doc/html/v4.18/vm/numa.html)
- Kubernetes documentation: https://kubernetes.io/
- Netflix historical architecture examples in the supplied post need their original post links (Hystrix, Prana, Zuul, Chaos Monkey, per-title encoding) before detailed company-specific claims are used. The item contains no direct links for those individual claims.

## Image transcription: Senior .NET Developer Checklist

The graphic is titled “The Senior .NET Developer Checklist (2026)” and groups these skills:

- **.NET:** C# (latest features), ASP.NET Core, Minimal APIs, Web APIs/REST, GraphQL, gRPC, SignalR, background services.
- **Cloud:** Azure App Service / Functions / AKS; AWS Lambda / ECS; Terraform / Bicep; cloud-cost optimization.
- **Data:** SQL Server, PostgreSQL, Cosmos DB / MongoDB, Redis, EF Core, Dapper, database migrations.
- **DevOps:** GitHub Actions, Azure DevOps, Docker, Kubernetes / Helm, CI/CD pipelines, feature flags, GitOps.
- **Security:** OAuth 2 / OpenID Connect, JWT validation, RBAC / policy-based authorization, OWASP Top 10, secret management.
- **Messaging:** RabbitMQ, Kafka, Azure Service Bus, event-driven architecture, publish/subscribe.
- **Observability:** OpenTelemetry, structured logging, distributed tracing, Grafana / Prometheus, health checks.
- **Architecture:** microservices, Domain-Driven Design, vertical slices, design patterns, API versioning, system design.
- **Testing:** xUnit, integration tests, Testcontainers, mocking frameworks, load testing.

The image is an unvalidated checklist, not a representative labor-market survey. Use it to identify possible study areas, then select a stack based on actual target role requirements and current experience. See [the .NET checklist map](../07-question-maps/dotnet-senior-developer-checklist-2026-09-23.md).

## Claim triage and corrections to preserve

### Keep as conditional heuristics, not laws

- “System design boils down to 12 concepts,” “all you need,” and career-level pattern ladders are simplifications. The right mechanism follows requirements, load shape, correctness constraints, team capacity, and operational budget.
- “REST for scalability, GraphQL for complex UIs, internal APIs for microservices” is too broad. REST, GraphQL, and gRPC expose different contracts and trade-offs; they can coexist. “Internal API” describes a boundary/audience, not an architecture that must be microservices.
- The image-upload baseline is a useful first sketch. At scale, consider direct uploads to object storage with short-lived signed URLs, content validation, metadata/authorization, asynchronous transforms, retries, idempotency, orphan cleanup, lifecycle policies, and private/public CDN behavior. A queue buffers work but does not create processing capacity.
- “Indexes are worth it on high-selectivity columns” is a starting point only. Choose indexes from predicates, ordering, joins, cardinality, write overhead, storage, and query plans; selectivity alone is insufficient.
- “Replication helps reads / partitioning helps writes” is useful shorthand, not a guarantee: replicas also affect durability/availability and lag; partitioning can improve locality or write distribution but creates routing, rebalancing, and cross-partition costs.
- “Tracing > logging,” “horizontal scaling beats vertical,” and “dead-letter queues are not optional” are not universal rules. Signals are complementary; scaling depends on bottleneck and coordination; poison-message policy must provide detection and recovery but may not require a broker DLQ feature.
- “The cheapest resource is disk, most expensive is time” is rhetorical rather than a portable cost model.

### Netflix-pattern post: claims to verify before reuse

The names are valuable study leads, but much of the prose is historical shorthand and includes absolute language. Do not memorize or repeat these as universal/current Netflix facts without the original technical post and date:

- “Every microservice has a circuit breaker. No exceptions.”
- Chaos Monkey “randomly kills production instances” as an unqualified description of current practice.
- Every play/pause/skip/rating is stored as an immutable event and replayed to rebuild state.
- A simple two-store split of catalog reads and user-activity writes as the definition of Netflix CQRS.
- Prana/Zuul behavior and whether either is the current implementation.
- A blanket claim that three AWS regions always choose availability over consistency.
- “1,200+ different bitrates” for every title. Distinguish encoded representations, per-title/per-shot ladders, device/codec variants, and client adaptation; source this number specifically.

The technical value is in extracting questions: what failure does the pattern address, where does state live, what contract is preserved, how is it measured, and what is the cost of operating it?

### Mount Mayhem article: study method

Use the linked Netflix article as a cross-layer performance case study. Reconstruct the evidence chain from workload to symptom, measurement, suspected mechanism, mitigation, and validation. Treat the user-supplied claims about ~20,000 syscalls, instance-family comparisons, hyperthreading gains, and O(n) to O(1) mount work as article-specific figures that need checking in the original text. Do not generalize a benchmark result into a universal CPU or instance-selection rule. The source itself is more useful than secondary summaries.

## Resume and interview integrity

A supplied post claims first-hand experience at Microsoft, Amazon, and Salesforce. That is the post author’s claimed biography, not the learner’s profile. Never copy it into the user’s resume or interview stories.

For practice, hypothetical projects are fine when clearly labeled as exercises. In a real resume or interview answer, use only work the user actually did; describe scale with evidence, ranges, or explicit uncertainty. Improve technical depth by explaining real decisions, constraints, measurements, alternatives, failures, and personal contribution—not by inventing employers, ownership, metrics, or impact.

## Next processing links

- Organized 98-concept inventory: [system design concept taxonomy](../07-question-maps/system-design-concept-taxonomy-2026-09-23.md)
- Image-derived and .NET supplemental syllabus: [senior .NET checklist map](../07-question-maps/dotnet-senior-developer-checklist-2026-09-23.md)
- Apply the topics with scenario prompts in [architecture drills](../04-drills/software-architecture-hard-parts-drills.md)


### Additional URLs extracted from the supplied Mount Mayhem write-up

These are hyperlinks present in the user's supplied explanatory text. Inclusion records provenance; it does not imply endorsement or source validation.

- Kubernetes — https://kubernetes.io/
- Linux VFS docs — https://docs.kernel.org/filesystems/vfs.html
- Linux NUMA docs — https://www.kernel.org/doc/html/v4.18/vm/numa.html
- NUMA explainer — https://smithanjohn.medium.com/understanding-numa-non-unified-memory-access-4fcb9c493d2c
- Linux mount API docs — https://docs.kernel.org/filesystems/mount_api.html
- Global locks (community wiki) — https://meta.miraheze.org/wiki/Global_locks
- AWS workload-aware computing — https://aws.amazon.com/blogs/hpc/a-scientific-approach-to-workload-aware-computing-on-aws/
- Redis cache-coherence glossary — https://redis.io/glossary/cache-coherence/
- Broadcom hyper-threading guidance — https://techdocs.broadcom.com/de/de/vmware-cis/cloud/vmware-cloud-on-aws/SaaS/performance-best-practices-for-vmc/esxi-and-virtual-machines/esxi-cpu-considerations/hyper-threading.html
- Single-socket server announcement — https://www.engineering.com/supermicro-announces-single-socket-servers-for-data-centers/
- AWS instance type overview — https://www.cloudzero.com/blog/aws-instance-types/
- Kubernetes portability commentary — https://www.cdotrends.com/story/4644/kubernetes-promised-portability-so-why-are-so-many-locking-themselves
- CNCF container runtimes explainer — https://www.cncf.io/blog/2019/07/15/demystifying-containers-part-ii-container-runtimes/
- Pragmatic Engineer / Google newsletter page — https://newsletter.pragmaticengineer.com/p/google
- Meta observability commentary — https://logz.io/blog/going-beyond-infrastructure-observability-meta/
- eBPF — https://ebpf.io/
- Brendan Gregg's perf resources — https://www.brendangregg.com/perf.html
- Datadog flame graph guide — https://www.datadoghq.com/knowledge-center/distributed-tracing/flame-graph/

Secondary explainers and vendor posts can help with orientation. For Linux behavior, validate with kernel documentation and the Netflix article; for a performance claim, prefer the experiment's actual methodology and measurements.
