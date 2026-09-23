# Real-World ML System Design Case Studies

Source table transcribed from the image and destinations recorded in [the source intake](../09-source-inbox/2026-09-23-lld-interview-guides-ml-case-studies.md). The linked company/engineering write-ups are primary or organization-published sources where available. They vary in depth; this map is a reading and interview-practice guide, not a reconstruction of confidential production systems.

## Case map

| Company | Problem class | What to investigate in the source |
| --- | --- | --- |
| Stripe Radar | Fraud classification/risk scoring | Label delay and quality, false-positive cost, decision latency, human review, feedback loops, model + rules interactions |
| Walmart Complete the Look | Recommendation / complementarity | Candidate generation vs ranking, catalog and image/text features, business objective, cold start, experiment design |
| Uber airport demand and ETR | Forecasting / operational decisions | Forecast horizon, spatial-temporal features, uncertainty, downstream staffing/positioning decisions, forecast evaluation |
| Pinterest advertiser churn | Churn prediction / retention action | Churn definition and horizon, intervention vs prediction, class imbalance, calibration, uplift and business metric |
| Stitch Fix expert-in-the-loop GenAI | Generative content with human oversight | Human review boundary, brand constraints, quality evaluation, workflow integration, failure and escalation |
| Swiggy item recommendation | Personalized recommendation | Intent signals, ranking objective, context and freshness, exploration, online/offline metric gap |
| Microsoft cloud incident management | LLM-assisted incident diagnosis | Retrieval/context assembly, grounding, evaluation, operator control, data privacy, latency and confidence |
| Foodpanda menu ranking | Ranking / choice optimization | Session/context features, objectives and constraints, position bias, experimentation, feedback |
| Zillow Neural Zestimate | Property valuation regression | Sparse/heterogeneous features, uncertainty, data freshness, error by geography/property, human interpretation |
| Airbnb home attributes | Preference estimation / ranking | Explicit vs implicit interest, cold start, aggregate signals, personalization, exposure bias |
| GitHub Copilot LLMs | Code generation / completion | Context construction, latency and token budget, model evaluation, safety/privacy, editor UX and user feedback |
| DoorDash Dasher wait times | Operational prediction/optimization | Outcome definition, dispatch coupling, intervention effects, segment metrics, guardrails and rollout |
| LinkedIn payment routing (partial row) | Payment routing / ML decision | Source title is cut off; canonical source and exact row attribution remain unverified |

## A reusable ML system design answer frame

1. **Product objective:** Who benefits, what action changes, and which business metric should move? State guardrails and costs of errors.
2. **Decision point:** Is this prediction, ranking, retrieval, generation, forecasting, or optimization? Identify whether ML is needed at all.
3. **Data contract:** Features available at decision time, labels and delay, privacy/retention constraints, leakage risks, freshness, missingness and skew.
4. **Baseline:** Rules, heuristic, existing model, or human workflow. Establish a measurable baseline before adding complexity.
5. **Model choice:** Compare quality on representative slices, latency, cost, context needs, update cadence, interpretability, safety and operational support. Explain RAG vs fine-tuning conditionally when relevant.
6. **Serving architecture:** Online/offline path, feature retrieval, model endpoint, timeouts, caching, fallback, admission control, batching and async work. Identify the critical latency budget.
7. **Evaluation:** Offline metrics aligned to objective; temporal and segment holdouts; human evaluation when needed; online experiment with guardrails. Avoid relying on “looks good.”
8. **Operations:** Versioning, rollout, drift and data-quality monitoring, model/feature lineage, tracing, incident rollback, retraining and feedback loops.
9. **Abuse and safety:** Authorization, prompt injection (for retrieval/agents), sensitive data handling, harmful output controls, human approval for consequential actions.
10. **Trade-offs:** State alternatives rejected and what new requirement would change the decision.

## Practice prompts

- Design a fraud decision service. Which signals are available before authorization, and how do you bound decision latency without approving suspicious traffic blindly?
- A recommendation model improves clicks but lowers completed orders. Which objective, guardrails and experiment slices do you inspect?
- An incident assistant produces plausible but ungrounded fixes. How do you separate retrieval, context selection, model, and workflow failures?
- Compare RAG, fine-tuning, a smaller task model, and deterministic search for a frequently changing policy assistant.
- A forecast is accurate on average but systematically poor during airport events. What slices, uncertainty estimates, and operational fallback do you add?
- A generative tool costs 4x more for a small quality gain. What minimum quality threshold, latency/cost budget and routing policy justify the expense?
- Define the event, label, and evaluation plan for advertiser churn when retention actions themselves affect the outcome.
- Explain how a shadow model can be validated without letting it issue real payment or dispatch decisions.

## Evidence discipline

Do not invent exact model families, feature sets, scale, latency, or deployment topology where the linked article does not state them. Distinguish source facts, your inference, and a hypothetical architecture proposal in interview answers.
