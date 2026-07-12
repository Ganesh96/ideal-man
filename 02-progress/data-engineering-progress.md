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

## Pluralsight priority path

Advisor recommendation accepted as the current course path:

1. Apache Spark 3 Fundamentals — primary technical foundation.
2. Delta Lake Essentials in Databricks — primary lakehouse correctness foundation.
3. Up and Running with Databricks — platform context.
4. Microsoft Fabric: First Look — ecosystem context.
5. Develop a Data Model with Power BI — modeling/reporting context.

Execution rule:

- In the next 24-hour interview window, prioritize Spark fundamentals and Delta Lake.
- Databricks, Fabric, and Power BI courses are skim-for-architecture unless time allows deeper practice.
- Course completion is not mastery; mastery requires explaining, scenario design, and retesting.

## Progress table

| Batch | Topic | Status | Confidence | Notes |
|---|---|---:|---:|---|
| 1 | Data platform mental model | In progress | Low | Current focus includes state, grain, correctness, OLTP/OLAP, lake/warehouse/lakehouse. |
| 2 | Spark and PySpark foundations | In progress | Low | Course path selected: Apache Spark 3 Fundamentals. Focus: driver/executors/partitions/lazy evaluation/shuffle/DataFrames. |
| 3 | PySpark optimization | Not started | Low | Partitioning, skew, joins, file sizing, Spark UI. |
| 4 | Delta Lake | In progress | Low | Course path selected: Delta Lake Essentials in Databricks. Focus: transaction log, ACID, schema evolution, time travel, MERGE. |
| 5 | Databricks environment | Planned | Low | Course path selected: Up and Running with Databricks. Focus: notebooks, jobs, clusters, Git, secrets, monitoring. |
| 6 | Microsoft Fabric fundamentals | Planned | Low | Course path selected: Microsoft Fabric First Look. Focus: OneLake, lakehouse, warehouse, pipelines, dataflows. |
| 7 | Fabric Lakehouse design | Planned | Low | Tables/files, SQL endpoint, medallion layers. |
| 8 | Dataflows Gen2 | Planned | Low | Power Query, low-code transformations, destinations. |
| 9 | Data Pipelines | Planned | Low | Activities, triggers, dependencies, retries. |
| 10 | Warehouse modeling | Planned | Low | Facts, dimensions, grain, star schema, SCD. Course path includes Power BI data modeling. |
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
