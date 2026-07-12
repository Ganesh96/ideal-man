# Data Engineering Execution Plan

## Purpose

This file operationalizes `data-engineering-databricks-fabric-syllabus.md`.

The syllabus is the coverage index. This file defines dependency order, learning depth, channel selection, evidence of mastery, and current execution priority.

## Learner baseline

- experienced backend developer;
- comfortable with coding, APIs, databases, cloud, and common distributed-system terms;
- revisiting fundamentals through a data-engineering lens;
- target: Senior Data Engineer interview readiness for Azure Databricks and Microsoft Fabric.

Do not spend substantial time reteaching general programming unless an observed gap blocks progress.

## North-star capability

Build, explain, verify, operate, diagnose, and economically justify a trustworthy analytical data platform.

Senior-level answers must cover four layers:

1. implementation;
2. execution mechanism;
3. correctness evidence;
4. production operation and tradeoffs.

## High-impact core

Master these before broadening:

1. data semantics, grain, keys, events, snapshots, and contracts;
2. incremental and idempotent processing;
3. Spark execution, joins, shuffle, skew, and query plans;
4. Delta Lake transactions, `MERGE`, schema evolution, retention, and recovery;
5. medallion architecture and dimensional modeling;
6. orchestration, observability, backfills, reliability, capacity, and cost.

These topics form the deep vertical of the T-shaped plan.

## Persistent case study

Use one evolving order-analytics platform instead of unrelated tutorials:

```text
Operational sources
  -> ingestion
  -> Bronze Delta evidence
  -> PySpark validation and conformance
  -> Silver business state
  -> Delta MERGE and SCD processing
  -> Gold star schema
  -> Power BI
```

Inject progressively harder conditions:

- duplicate deliveries;
- out-of-order updates;
- invalid records;
- schema drift;
- source deletes;
- partial failure;
- replay and backfill;
- skewed joins;
- small files;
- freshness and cost constraints.

## Dependency-ordered learning blocks

### Block 0 — Data state and correctness

Learn:

- OLTP versus OLAP;
- event log versus current-state snapshot;
- business key, surrogate key, and table grain;
- event time, source update time, extraction time, and ingestion time;
- duplicate and late-arrival semantics;
- completeness, uniqueness, validity, consistency, timeliness, reproducibility, and idempotency;
- Bronze, Silver, and Gold guarantees;
- source-to-target reconciliation.

Evidence:

- define the grain of every table;
- resolve duplicate and late order updates;
- write reconciliation queries;
- explain what a correct rerun means.

### Block 1 — Distributed execution with Spark

Learn:

- driver, executors, jobs, stages, tasks, and partitions;
- lazy evaluation;
- narrow and wide transformations;
- shuffle boundaries;
- join strategies;
- skew, memory pressure, and spill;
- query plans and Spark UI;
- Adaptive Query Execution.

Evidence:

- predict where a shuffle occurs;
- inspect a physical plan;
- identify whether a slowdown is caused by skew, shuffle, I/O, CPU, or memory;
- compare broadcast and sort-merge joins using metrics.

### Block 2 — Reliable Delta pipelines

Learn:

- Parquet files versus Delta tables;
- transaction log and atomic commits;
- optimistic concurrency;
- schema enforcement and controlled evolution;
- `MERGE`, updates, inserts, and deletes;
- table history and time travel;
- retention and `VACUUM`;
- compaction, partitioning, and clustering concepts.

Evidence:

- build an idempotent incremental load;
- replay the same input without changing business state;
- recover from an incorrect write;
- explain the limits of Delta guarantees across systems.

### Block 3 — Lakehouse and analytical modeling

Learn:

- lake, warehouse, and lakehouse tradeoffs;
- medallion responsibilities;
- facts, dimensions, and grain;
- natural and surrogate keys;
- SCD Type 1 and Type 2;
- star versus snowflake;
- semantic-model readiness and Power BI serving.

Evidence:

- design `fact_order_line`, `dim_customer`, `dim_product`, and `dim_date`;
- defend grain and history choices;
- reconcile Gold measures to Silver state;
- place transformations in the correct layer.

### Block 4 — Databricks and Fabric productionization

Learn:

- exploratory notebook versus production job;
- thin notebook entry points and reusable Python modules;
- parameters, configuration, secrets, libraries, and Git;
- Databricks jobs/workflows and monitoring;
- Fabric Lakehouse, OneLake, Warehouse, SQL analytics endpoint;
- Dataflows Gen2 and Power Query;
- Fabric Pipelines, dependencies, retries, parameters, and failure paths;
- Power BI integration.

Evidence:

- convert a notebook into repeatable production execution;
- orchestrate notebook and Dataflow activities;
- inject failure and rerun only the safe recovery unit;
- explain when to choose notebook, Dataflow, Pipeline, Lakehouse, or Warehouse.

### Block 5 — Senior architecture and economics

Learn:

- batch versus streaming;
- polling, webhooks, CDC, and replay;
- security, governance, lineage, and ownership;
- workload isolation and capacity;
- migration and coexistence strategies;
- operational and cloud cost drivers.

Evidence:

- interpret an existing architecture in semantic, computational, and operational passes;
- estimate scale and freshness requirements;
- identify dominant cost and reliability risks;
- propose measurable changes and state what would falsify the proposal.

## Learning-channel routing

Use the channel that compresses the concept most effectively.

| Need | Primary channel |
|---|---|
| interactive mental model, tradeoffs, case reasoning | conversation |
| visual architecture or guided platform demonstration | Pluralsight |
| compact HLD/LLD concept | Educosys |
| exact and current product behavior | official documentation |
| implementation, diagnosis, and verification | Databricks/Fabric lab |
| production examples and project structure | selected GitHub material |
| durable retrieval | compressed notes and drills |

Do not reproduce a course as a long chat lecture. Do not read documentation linearly.

## External-resource protocol

Assignments should specify:

- exact course/module or document section;
- learning objective;
- what to focus on;
- what to skip;
- expected time box;
- reconstruction question;
- practical follow-up.

Record completion as one of:

- `Completed carefully`;
- `Speed-ran`;
- `Partially completed`;
- `Skipped`;
- `Did not understand`.

Speed-running creates exposure, not mastery.

## Mastery levels

1. `Exposed` — recognizes the term;
2. `Can explain` — explains the mechanism and purpose;
3. `Can implement` — builds a working example;
4. `Can diagnose` — uses evidence to find and repair failures;
5. `Can choose and defend` — selects among alternatives under constraints.

Senior interview preparation prioritizes levels 4 and 5 for the high-impact core.

## Per-topic learning packet

Each deep topic should produce:

1. real problem;
2. naive solution;
3. failure of the naive solution;
4. mechanism;
5. prerequisites and assumptions;
6. implementation;
7. correctness checks;
8. performance and operational metrics;
9. failure recovery;
10. cost drivers;
11. alternatives and decision rule;
12. concise interview explanation;
13. retest questions.

Secondary topics may stop after mechanism, decision rule, and failure mode.

## Architecture-reading framework

### Pass 1 — Semantic

- business outcome;
- consumers;
- source of truth;
- entity/event meaning;
- table grain;
- required correctness and freshness.

### Pass 2 — Computational

- storage layout;
- partitioning;
- processing engine;
- large joins and shuffles;
- state and checkpoints;
- batch or streaming model.

### Pass 3 — Operational and economic

- independent failure units;
- retry and backfill behavior;
- observability and SLOs;
- security and lineage;
- workload ownership;
- capacity contention;
- dominant compute, storage, and maintenance costs.

## Metrics decision framework

Metrics must support a decision or trigger an action.

### Correctness

- source-to-Bronze reconciliation;
- valid plus quarantine reconciliation;
- duplicate business-key count;
- referential-integrity failures;
- aggregate and financial reconciliation;
- schema-contract violation rate.

### Freshness

```text
source lag = ingestion time - source extraction time
transformation lag = publish time - ingestion time
end-to-end freshness = current time - maximum usable event time
```

### Reliability

- SLO attainment;
- retry rate;
- failed partitions;
- mean recovery time;
- stale-dataset count;
- manual-intervention rate.

### Spark performance

- input and output bytes;
- shuffle read/write;
- spill;
- task-duration distribution;
- maximum-to-median task duration;
- records and bytes per partition;
- files read and written;
- failed and retried tasks.

### Cost

Prefer normalized measures:

- compute cost per successful run;
- compute cost per TB processed;
- retry cost divided by total execution cost;
- idle compute divided by total compute;
- storage cost per retained business day;
- cost per Power BI refresh.

## HLD and LLD integration

Use HLD to deepen:

- HTTP/TLS, polling, webhooks, and delivery failure;
- horizontal scaling and partitioning;
- object storage and compute-storage separation;
- ACID and distributed transaction boundaries;
- batch, streaming, and event-driven architecture.

Use LLD to productionize:

- separation of transformation and orchestration;
- Strategy for load modes;
- Adapter for heterogeneous sources;
- Template Method for job lifecycle only when repetition exists;
- state machines for pipeline runs;
- dependency inversion for testability.

Do not spend primary preparation time on generic elevator, chess, or parking-lot implementations.

## Current execution point

Current block: **Block 0 — Data state and correctness**.

Immediate sequence:

1. operational versus analytical data;
2. events versus snapshots;
3. business keys, surrogate keys, and grain;
4. timestamp semantics;
5. duplicates and late arrivals;
6. full and incremental loads;
7. idempotency and replay;
8. reconciliation and quarantine;
9. Bronze/Silver/Gold guarantees;
10. first PySpark and Delta implementation.

Update `02-progress/data-engineering-progress.md` only when evidence changes mastery state. Record observed misconceptions in `03-mistakes/` and create dated summaries in `06-sessions/` after substantial sessions.
