# Deployment Strategies and System Design Practice — 2026-09-23

Source: deployment and interview-playbook posts in [the source intake](../09-source-inbox/2026-09-23-system-design-practice-and-rollouts-source-batch.md). Terms below are checked against official Kubernetes, AWS EKS, and Azure AKS documentation.

## Deployment strategies

| Strategy | Mechanism | Useful when | Risks/costs | Checks |
|---|---|---|---|---|
| Recreate | Stop old pods before bringing up new pods | Downtime is acceptable or old/new overlap is unsafe | Planned interruption; failed new version may extend outage | Startup/readiness, rollback time, maintenance window |
| Rolling update | Gradually replace old pods | Compatible stateless workload; simple standard rollout | Capacity dip, mixed versions, bad readiness, slow or unhealthy rollout | maxSurge/maxUnavailable, readiness, draining, error/latency gates, version compatibility |
| Blue-green | Keep old and new environments; switch routing after validation | Isolated validation and fast traffic-reversal path are valuable | Duplicate capacity/cost; routing drift; rollback may not reverse data changes | Traffic switch, schema compatibility, background jobs, rollback test |
| Canary | Route a small measured share to new version, then increase | High-risk release where production evidence matters | Bad split, noisy metrics, delayed impact, shared dependencies | Traffic assignment, guardrails, sample/time window, stop/rollback triggers |
| A/B experiment | Assign cohorts to variants and compare product outcomes | Testing a product or UX hypothesis | Bias, interference, seasonality, multiple comparisons | Randomization/stickiness, hypothesis, primary/guardrail metrics, duration |
| Shadow/mirroring | Copy live requests to candidate; discard candidate response | Validate performance/compatibility using representative input | Extra load/cost, sensitive data, duplicate writes, resource interference | Side-effect isolation, redaction, rate bounds, output comparison |

Kubernetes Deployment objects directly support Recreate and RollingUpdate. The other patterns need surrounding deployments, traffic routing, experiment assignment, or a controller/orchestration layer.

## Important corrections

- Rolling update does not guarantee zero downtime. Readiness, capacity, traffic routing, draining, and old/new compatibility determine user impact.
- Blue-green may make route reversal fast, but does not reverse schema/data mutations, external payments, messages, or irreversible side effects.
- Canary reduces exposure only if traffic is split and monitored against meaningful signals.
- A/B testing is an experimentation method; it can use rollout infrastructure but has distinct statistical/product validity requirements.
- Shadowing avoids serving the candidate response to the user, but the mirrored request still executes. Isolate writes, external calls, sensitive data, and resource impact.
- The post's “very low risk” and “zero user impact” are not inherent guarantees.

## Primary references

- [Kubernetes Deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
- [Kubernetes canary tutorial](https://kubernetes.io/docs/tutorials/stateless-application/canary-deployment/)
- [Amazon EKS: Running highly available applications](https://docs.aws.amazon.com/eks/latest/best-practices/application.html)
- [Azure AKS: Zero-downtime migration](https://learn.microsoft.com/en-us/azure/aks/zero-downtime-migration)
- [Azure Well-Architected: Safe deployments](https://learn.microsoft.com/en-us/azure/well-architected/operational-excellence/safe-deployments)

## Flexible 60-minute design-interview practice

The proposed segments total approximately 50–59 minutes; interviewer follow-ups take precedence.

1. Scope, users, requirements, invariants, workload, SLOs: 5–7 minutes.
2. High-level design and core paths: about 10 minutes.
3. Two or three component deep dives: 15–20 minutes.
4. Bottlenecks and scaling: about 10 minutes.
5. Failures, retries, recovery: 5–7 minutes.
6. Metrics/SLOs and concise close: about 3–5 minutes.

Do not force all sections. Make assumptions visible and adjust to the prompt.

## Practice: rate-limiter LLD

- Define the key (user, tenant, API key, route), quota dimensions, burst behavior, global vs per-instance scope, and failure policy.
- Compare token bucket (allows bounded bursts) and leaky bucket (smooths output); define where state lives and how it expires.
- Choose atomicity under concurrent requests. What happens if the store is slow, unavailable, or partitioned?
- Define rejection response, retry hints, fairness, metrics, and tests.
- Do not claim a strict global limit unless the coordination and consistency cost is addressed.

## Practice: product-catalog ingestion

- Clarify file formats/sizes, schema evolution, validation, duplicate/re-upload semantics, row-level errors, and result visibility.
- Consider direct object upload and asynchronous parsing for large/slow files; define job status and idempotent submission.
- Decide whether imports are atomic or partially accepted. Separate file errors from row errors.
- Prevent duplicate products/stale overwrites with a stated key/version/concurrency policy.
- Design resumability, error reports, retries, authorization, retention, and observability.

## Other practice surfaces

- Extend a parser when requirements change; avoid speculative abstraction.
- Integrate paginated/rate-limited APIs with checkpoints, bounded retries, dedupe, and validation.
- Debug unfamiliar code using a failing test, hypothesis narrowing, and a minimal verified fix.
