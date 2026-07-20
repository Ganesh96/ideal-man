# Eli Lilly Senior Data Engineer — 24-Hour Interview Plan

## Goal

Maximize interview readiness for the highest-probability evaluation surface in 24 hours. Do not attempt equal coverage of every tool. Optimize for credible senior-level depth in core architecture, Spark/PySpark, Delta Lake, Databricks productionization, Microsoft Fabric, SQL/data modeling, and resume defense.

## Reality Constraint

Twenty-four hours is insufficient for true mastery. The target is:

- deep command of the highest-probability topics;
- coherent end-to-end architecture reasoning;
- practical vocabulary and failure diagnosis;
- defensible resume stories;
- enough coding readiness to avoid freezing on common PySpark/SQL tasks;
- explicit honesty where direct hands-on depth is limited.

## Interview Weighting

### Tier 1 — 55%

- Spark execution model and PySpark DataFrames;
- joins, partitions, shuffle, skew, caching, query plans;
- Delta Lake transaction log, ACID, MERGE, schema enforcement/evolution, time travel, OPTIMIZE, VACUUM;
- end-to-end ingestion, idempotency, replay, duplicate handling, late data, schema drift;
- lakehouse and medallion architecture.

### Tier 2 — 30%

- Databricks notebooks versus jobs/workflows;
- clusters, parameters, secrets, Git, CI/CD, monitoring, retries, backfills;
- Fabric OneLake, Lakehouse, Warehouse, Dataflows Gen2, Data Pipelines;
- SQL, dimensional modeling, Power BI readiness;
- testing, observability, governance, security.

### Tier 3 — 15%

- Power BI, DAX, Power Query;
- ADF, Synapse, Unity Catalog, Purview;
- GxP/FDA and regulated-platform practices;
- cost and capacity reasoning.

## 24-Hour Schedule

### Hours 0–2 — End-to-End Data Platform Architecture

Master:

- OLTP versus OLAP;
- lake versus warehouse versus lakehouse;
- ingestion → Bronze → Silver → Gold → serving;
- batch, CDC, APIs, files, events;
- orchestration, storage, compute, serving, governance boundaries;
- one pharmaceutical/manufacturing case study.

Deliverable:

- explain one complete platform in five minutes;
- justify each component and name its failure modes.

### Hours 2–5 — Spark/PySpark Core

Master:

- driver, executors, cluster manager;
- partitions, jobs, stages, tasks;
- lazy evaluation;
- narrow versus wide transformations;
- shuffle;
- RDD versus DataFrame;
- logical, optimized, and physical plans;
- join strategies, skew, caching, partition sizing, small files.

Deliverable:

- predict shuffles;
- explain why a job is slow;
- state what Spark UI evidence would confirm the diagnosis.

### Hours 5–8 — Delta Lake

Master:

- Parquet plus transaction log;
- atomic commits and optimistic concurrency;
- schema enforcement versus evolution;
- MERGE and idempotent incremental loads;
- time travel and recovery;
- retention, VACUUM, OPTIMIZE, compaction, partitioning/clustering;
- limits of Delta guarantees across external systems.

Deliverable:

- explain a retry-safe incremental pipeline;
- recover from an incorrect write;
- explain concurrent-write conflicts.

### Hours 8–10 — Databricks Productionization

Master:

- exploratory notebook versus production job;
- thin notebook entry points and reusable modules;
- jobs/workflows, parameters, secrets, libraries, Git;
- job clusters versus interactive clusters;
- retries, checkpoints, backfills, monitoring;
- Unity Catalog and environment separation.

Deliverable:

- turn a notebook prototype into a production design;
- describe deployment and rollback.

### Hours 10–12 — Microsoft Fabric

Master:

- OneLake;
- Lakehouse versus Warehouse;
- SQL analytics endpoint;
- Dataflows Gen2;
- Data Pipelines;
- notebooks;
- shortcuts;
- semantic models and Power BI integration;
- when Fabric orchestrates Databricks and when Fabric performs the transformation itself.

Deliverable:

- choose among Lakehouse, Warehouse, Dataflow, Pipeline, and Notebook for concrete scenarios.

### Hours 12–14 — SQL and Data Modeling

Master:

- grain;
- facts and dimensions;
- star versus snowflake;
- surrogate keys;
- SCD Types 1 and 2;
- late-arriving dimensions;
- deduplication and window functions;
- incremental logic;
- Power BI-ready Gold models.

Deliverable:

- design a fact and dimension model for one pharmaceutical/manufacturing workflow;
- defend the chosen grain and history model.

### Hours 14–16 — Reliability, Testing, Governance, and CI/CD

Master:

- data quality dimensions;
- reconciliation and quarantine;
- idempotency, replay, backfills;
- unit, integration, data-contract, and end-to-end tests;
- SLAs/SLOs, freshness, completeness, failure alerts;
- RBAC, least privilege, secrets, lineage, audit trails;
- Git branching, promotion, environment configuration, rollback;
- GxP/FDA concepts: traceability, validated change, reproducibility, separation of duties.

Deliverable:

- explain one failure and recovery path from source through Power BI.

### Hours 16–18 — Resume Defense

Prepare five stories:

1. UF time-series analytical platform;
2. Maxil event/feature pipeline;
3. BestRx transaction-sensitive reconciliation;
4. Infosys migration/reporting platform;
5. one performance or production incident.

Each story must cover:

- business problem;
- architecture;
- scale and SLA;
- key design decision;
- alternative rejected;
- implementation details;
- failure or bug;
- evidence and diagnosis;
- fix and result;
- testing, deployment, monitoring, governance;
- stakeholder communication;
- honest boundary between direct experience and transferable/lab knowledge.

### Hours 18–20 — Coding Readiness

Without broad algorithm study, rehearse common interview patterns:

- PySpark DataFrame read, select, filter, cast, join, aggregate, window, deduplicate, write;
- Spark SQL equivalent;
- Delta MERGE/incremental load pattern;
- null and duplicate handling;
- partition and write strategy;
- explain-plan interpretation;
- SQL joins, windows, SCD, dedupe, aggregation.

Deliverable:

- write or verbally construct each pattern without searching.

### Hours 20–22 — Architecture and Debugging Drills

Practice:

- design a regulated batch lakehouse;
- design a near-real-time manufacturing pipeline;
- diagnose a slow Spark join;
- diagnose duplicate Delta rows after retries;
- handle schema drift;
- recover from partial pipeline failure;
- choose Databricks versus Fabric transformation;
- choose Lakehouse versus Warehouse;
- reduce compute cost without breaking SLA.

### Hours 22–24 — Compression and Rest

- review compact cheat sheets only;
- rehearse five-minute architecture answer;
- rehearse two-minute resume stories;
- rehearse one-minute definitions;
- stop learning new topics;
- preserve enough sleep to reason clearly.

## Mandatory Interview Answer Shape

For technical questions:

1. define the problem;
2. state requirements and constraints;
3. propose the mechanism;
4. explain data state and correctness;
5. explain performance and scale;
6. explain failure and recovery;
7. explain security/governance;
8. explain alternatives and tradeoffs;
9. state evidence or metrics;
10. conclude with the decision rule.

## Deprioritize

- deep raw RDD implementation beyond concepts;
- advanced ML algorithms;
- generic HLD case studies unrelated to data platforms;
- Kubernetes internals;
- advanced DAX unless specifically signaled;
- obscure Databricks/Fabric features;
- lengthy course completion for its own sake.

## Current Starting Point

Resume from source-to-OLAP ingestion and data correctness, then bridge directly into Spark execution. The learner has watched Spark fundamentals only through the early RDD section and has not completed Structured APIs.

## Next Teaching Sequence

1. enterprise ingestion architecture and component boundaries;
2. batch versus CDC versus streaming;
3. Spark execution model;
4. RDD versus DataFrame and Structured APIs;
5. PySpark performance;
6. Delta Lake;
7. Databricks productionization;
8. Fabric;
9. modeling, governance, and resume drills.
