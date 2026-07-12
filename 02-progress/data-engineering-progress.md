# Data Engineering Progress Tracker

## Track

Azure Databricks + Microsoft Fabric interview preparation.

## Current mode

Heavy learning mode.

## Current execution block

Block 0 — Data state and correctness.

This maps primarily to Batch 1, while introducing prerequisites for Batch 10 and Batch 11.

Canonical execution order and channel rules: `01-syllabus/data-engineering-execution-plan.md`.

## Current focus

1. operational versus analytical data;
2. events versus snapshots;
3. business keys, surrogate keys, and grain;
4. timestamp semantics;
5. duplicate and late-arrival semantics;
6. full and incremental loads;
7. idempotency and replay;
8. reconciliation and quarantine;
9. Bronze, Silver, and Gold guarantees;
10. first PySpark and Delta implementation.

## Progress table

| Batch | Topic | Status | Confidence | Notes |
|---|---|---:|---:|---|
| 1 | Data platform mental model | In progress | Low | Current focus includes state, grain, correctness, OLTP/OLAP, lake/warehouse/lakehouse. |
| 2 | Spark and PySpark foundations | Not started | Low | Driver/executors/partitions/lazy evaluation/shuffle. |
| 3 | PySpark optimization | Not started | Low | Partitioning, skew, joins, file sizing, Spark UI. |
| 4 | Delta Lake | Not started | Low | Transaction log, ACID, schema evolution, time travel. |
| 5 | Databricks environment | Not started | Low | Notebooks, jobs, clusters, Git, secrets, monitoring. |
| 6 | Microsoft Fabric fundamentals | Not started | Low | OneLake, lakehouse, warehouse, pipelines, dataflows. |
| 7 | Fabric Lakehouse design | Not started | Low | Tables/files, SQL endpoint, medallion layers. |
| 8 | Dataflows Gen2 | Not started | Low | Power Query, low-code transformations, destinations. |
| 9 | Data Pipelines | Not started | Low | Activities, triggers, dependencies, retries. |
| 10 | Warehouse modeling | Not started | Low | Facts, dimensions, grain, star schema, SCD. |
| 11 | Lakehouse architecture patterns | Not started | Low | Medallion, CDC, quality, idempotency, reprocessing. |
| 12 | Interview synthesis | Not started | Low | Scenario answers and stakeholder communication. |

## Evidence rule

Change status or confidence only when there is evidence:

- explanation without notes;
- correct implementation;
- diagnosis using metrics;
- defended decision under a scenario;
- successful delayed retest.

Course completion alone is exposure, not mastery.

## External-resource status vocabulary

- Completed carefully
- Speed-ran
- Partially completed
- Skipped
- Did not understand

## Retest principles

When a mistake is made:

1. Record the wrong assumption.
2. Record the corrected model.
3. Add a retest question in a different form.
4. Re-test after delay.
