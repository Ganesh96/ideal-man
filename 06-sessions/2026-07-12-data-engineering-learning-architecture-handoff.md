# Handoff: Data Engineering Learning Architecture

## Date

2026-07-12

## Agent scope

Refine the Azure Databricks + Microsoft Fabric interview track for a backend engineer progressing from refreshed fundamentals to Senior Data Engineer judgment.

## Files changed

- `01-syllabus/data-engineering-execution-plan.md` — dependency order, high-impact core, learning-channel routing, mastery evidence, metrics, cost, and current execution point.
- `02-progress/data-engineering-progress.md` — aligned current state to Block 0: data state and correctness.
- `00-control/agent-coordination.md` — added optimistic-concurrency and safe multi-agent write rules.

## Decisions

- Preserve the original 12-batch syllabus as a coverage index.
- Use the execution plan as the authoritative dependency and teaching overlay.
- Treat the learner as an experienced backend developer, not a novice programmer.
- Start with data semantics, grain, event/state modeling, timestamp meaning, correctness, idempotency, and reconciliation before Spark internals.
- Use one evolving order-analytics case study across Databricks, Delta Lake, Fabric, Pipelines, Dataflows Gen2, and Power BI.
- Route concepts to the most efficient medium: conversation for reasoning, Pluralsight for visual/course structure, Educosys for compact HLD/LLD, official docs for product contracts, and labs for implementation/diagnosis.
- Treat course speed-runs as exposure, not mastery.
- Change progress only when supported by explanation, implementation, diagnosis, defended choice, or delayed retest.

## Current state

In progress:

- Block 0 — Data state and correctness.

Immediate topic order:

1. operational versus analytical data;
2. events versus snapshots;
3. business keys, surrogate keys, and table grain;
4. event/update/extraction/ingestion timestamps;
5. duplicates and late arrivals;
6. full versus incremental loads;
7. idempotency and replay;
8. reconciliation and quarantine;
9. Bronze/Silver/Gold guarantees;
10. first PySpark and Delta implementation.

No mastery evidence has been recorded yet. Confidence remains low until tested.

## Next action

Teach the first case study from source semantics before introducing tools:

- define an order source;
- distinguish event history from current state;
- choose business keys and table grains;
- model duplicates, corrections, and late updates;
- define correctness invariants and reconciliation evidence.

Then implement the smallest version in PySpark and Delta.

## Risks / coordination notes

- Another conversation is actively using the repository. Re-fetch files and SHAs before every update.
- Do not replace the original 12-batch syllabus with this execution plan; both have separate contracts.
- Avoid duplicating explanations in syllabus, progress, drills, and concepts.
- Store mistakes only after an observed wrong assumption; do not invent user weaknesses.
- Do not mark a topic complete because a course was watched.
