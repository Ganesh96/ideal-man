# Eli Lilly Senior Data Engineer — 36-Hour Interview Sprint

## Objective

Reach interview-ready depth across the job's critical path rather than attempt total platform mastery.

Target competencies:
- explain mechanisms clearly;
- design end-to-end architectures;
- write and reason about common PySpark, Spark SQL, SQL, Delta, Fabric pipeline, and Power BI patterns;
- diagnose production failures;
- defend tradeoffs and decisions;
- connect answers to resume stories.

## Priority tiers

### Tier 1 — Must be deep
- Spark execution model and PySpark DataFrames
- Spark SQL
- partitioning, shuffle, joins, skew, caching, execution plans
- Delta Lake transaction log, ACID, MERGE, schema enforcement/evolution, time travel, OPTIMIZE, VACUUM
- Azure Databricks notebooks, clusters, Jobs/Workflows, productionization, monitoring
- Microsoft Fabric Lakehouse, OneLake, Dataflows Gen2, Data Pipelines, notebooks
- lakehouse and data warehouse architecture
- SQL and dimensional modeling
- production reliability: retries, checkpoints, idempotency, backfills, replay, reconciliation, observability

### Tier 2 — Working knowledge
- ADF and ADLS Gen2
- Azure DevOps, Git, CI/CD
- Unity Catalog and Purview
- Synapse positioning
- Power BI semantic models, DAX fundamentals, Power Query, Direct Lake/Import/DirectQuery
- regulated data: lineage, auditability, access control, reproducibility

### Tier 3 — Deprioritize
- deep raw RDD programming
- advanced DAX/report visuals
- Kubernetes internals
- advanced ML algorithms
- unrelated cloud platforms
- deep HDFS internals beyond Spark architecture context

## 36-hour elapsed schedule

### Block 1 — 3 hours
Enterprise data platform architecture
- OLTP vs OLAP
- lake vs warehouse vs lakehouse
- ingestion components
- batch, CDC, APIs, Kafka/Event Hubs
- Bronze/Silver/Gold and warehouse staging

### Block 2 — 5 hours
Spark and PySpark foundations
- driver, executors, cluster manager
- partitions, jobs, stages, tasks
- lazy evaluation, DAG
- transformations vs actions
- RDD vs DataFrame
- narrow vs wide transformations
- Spark SQL and Structured APIs

### Block 3 — 4 hours
PySpark coding and optimization
- reading structured/semi-structured data
- schema handling
- select/filter/withColumn/groupBy/window
- joins and broadcast joins
- deduplication and incremental processing
- repartition/coalesce
- skew, shuffle, caching, explain plans, Spark UI

### Block 4 — 4 hours
Delta Lake
- transaction log and snapshot isolation
- ACID
- MERGE/upsert
- schema enforcement/evolution
- time travel and restore
- OPTIMIZE, file compaction, VACUUM
- concurrency, streaming checkpoints, Change Data Feed

### Sleep and recovery — 7 hours
Do not trade sleep for passive course completion.

### Block 5 — 3 hours
Azure Databricks production
- workspaces, clusters, notebooks
- Jobs/Workflows and parameters
- Auto Loader and Structured Streaming overview
- secrets, Unity Catalog, access control
- Git/Repos, CI/CD, environment promotion
- monitoring, cost, incident handling

### Block 6 — 4 hours
Microsoft Fabric
- OneLake
- Lakehouse vs Warehouse
- Dataflows Gen2
- Data Pipelines
- notebooks and Spark
- SQL analytics endpoint
- semantic models and Direct Lake positioning
- orchestration and deployment concerns

### Block 7 — 2.5 hours
Warehouse modeling and Power BI
- grain
- facts and dimensions
- star vs snowflake
- surrogate keys and SCD
- semantic models
- DAX and Power Query fundamentals
- Import vs DirectQuery vs Direct Lake

### Block 8 — 2 hours
Production architecture and regulated environment
- security and governance
- lineage and audit trails
- data quality and reconciliation
- CI/CD and testing
- GxP/FDA-style validation mindset
- stakeholder communication

### Block 9 — 1.5 hours
Resume defense
Prepare deep stories for:
- UF time-series platform
- Maxil event/feature pipelines
- BestRx transaction-sensitive reconciliation
- Infosys warehouse/Power BI modernization

Each story must include:
- scale and SLA;
- architecture;
- implementation;
- failure/bug;
- diagnosis;
- decision and tradeoff;
- measurable outcome;
- what would be improved now.

## Readiness test

A topic is interview-ready only when the candidate can:
1. define it;
2. explain how it works internally;
3. place it in an enterprise architecture;
4. write or outline the common implementation;
5. name failure modes;
6. diagnose one production issue;
7. compare alternatives;
8. connect it to a resume example.

## Handoff note for other agents

This file is the active short-horizon execution plan for the Eli Lilly Senior Data Engineer interview. Prioritize it over the broader data-engineering syllabus until the interview is complete. Preserve the existing progress, mistake, and retest ledgers. Record only evidence-based confidence changes.