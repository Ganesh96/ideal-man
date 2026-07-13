# Eli Lilly Senior Data Engineer Interview Context

## Purpose

This file is a target-context memory document for LLM agents preparing Ganesan for a deep technical Senior Data Engineer interview.

Use this as the end-goal filter for lessons, drills, corrections, and resume story preparation.

## Job Description Emphasis

Required:

- Proven hands-on Azure Databricks experience.
- PySpark for distributed data processing and optimization.
- Delta Lake: ACID transactions, time travel, schema evolution, MERGE/upsert, table maintenance.
- Databricks notebooks: development and productionization.
- Microsoft Fabric: Lakehouses, Dataflows Gen2, Data Pipelines.
- Data warehouse architecture: dimensional modeling, star/snowflake schemas, BI serving layer.
- Lakehouse architecture: medallion architecture, Bronze/Silver/Gold.
- Large-scale data platform delivery from design to production.
- Strong technical/non-technical stakeholder communication.

Good to have:

- Power BI data modeling, DAX, report development.

## Submitted Resume Alignment

Resume claims to defend:

- 6+ years building production data platforms, analytical pipelines, ML-ready datasets, and transaction-sensitive workflows.
- Skills listed: Azure Databricks, PySpark, Delta Lake, Microsoft Fabric, Lakehouse architecture, data warehousing, ETL/ELT, Azure/AWS, Kafka, Power BI, DAX, semantic models.
- University of Florida: analytical platform for research simulations; 10GB+ time-series sensor data/day; PostgreSQL/TimescaleDB; raw-to-curated pipeline stages; ingestion guards; schema versioning; validation; checkpointed loads; duplicate and schema-drift isolation; time-series partitioning; indexes; caching; observability.
- Maxil: feature-generation pipelines; 200K+ embeddings/day; Kafka-style clickstream ingestion; PostgreSQL/pgvector/Redis/MongoDB; versioned data contracts; graph-backed referral workflows; reconciliation jobs; instrumentation.
- BestRx: transaction-sensitive pharmacy claims/billing workflows; 50K+ daily transactions; auditability; asynchronous validation and reconciliation; SQL-based audit/exception detection; reduced alert latency; structured logging/correlation IDs/operational dashboards; retry-safe workflows.
- Autoreview: document feature extraction; Python preprocessing; embeddings; vector search; PostGIS/geospatial features; secure document storage and processed metadata.
- Infosys: Oracle/MS SQL to Azure SQL migration analysis; SQL validation rules, stored procedures, views, query tuning; 22 Power BI report templates; 96 SSRS report remediation; automated compliance checks; Azure App Service/Blob Storage lifecycle/replication/RBAC.

## Risk Areas

The resume is broad. Interviewers may probe for concrete hands-on depth. Training must convert claims into defensible technical stories.

High-risk areas to strengthen:

- Specific Databricks implementation details: clusters, jobs/workflows, notebook parameterization, Git integration, secrets, Unity Catalog, monitoring, retry, productionization.
- PySpark internals: driver/executors, partitions, jobs/stages/tasks, narrow/wide transformations, shuffles, joins, skew, partitioning, caching, file sizing.
- Delta Lake: transaction log, ACID semantics on object storage, optimistic concurrency, MERGE, schema enforcement/evolution, time travel, VACUUM, OPTIMIZE/ZORDER/liquid clustering if relevant.
- Fabric: Lakehouse vs Warehouse, OneLake, shortcuts, Dataflows Gen2, Pipelines, SQL analytics endpoint, Power BI semantic model, governance.
- Dimensional modeling: grain, facts, dimensions, slowly changing dimensions, star schema, Power BI serving model.
- Production stories: bug/problem, diagnosis, metrics, root cause, fix, tradeoff, monitoring added, stakeholder communication.

## Training Rule

When a lesson intersects resume claims or job requirements, explicitly mark it as:

INTERVIEW TRAINING:
- likely question
- what resume claim it maps to
- strong answer structure
- weak answer to avoid
- possible follow-up probes

## Current Learning Mode

Heavy learning mode, but lessons should be aligned to the Senior Data Engineer interview stack.

Default sequence:

1. Enterprise data platform mental model.
2. OLTP to OLAP ingestion: batch, CDC, API, events, Kafka/Event Hubs.
3. Spark/PySpark fundamentals and internals.
4. Delta Lake production table management.
5. Databricks productionization.
6. Fabric Lakehouse/Dataflows/Pipelines.
7. Warehouse modeling and Power BI serving.
8. Scenario-based architecture drills.
9. Resume-based deep technical stories.

## Resume Story Template

For each project claim, prepare:

- Business problem.
- Source systems and data shape.
- Architecture chosen.
- Ingestion pattern.
- Transformation logic.
- Data model / serving layer.
- Scale/volume/latency.
- Failure encountered.
- Debugging method.
- Fix implemented.
- Tradeoff accepted.
- Monitoring/governance added.
- Stakeholder communication.

## Agent Coordination

Do not restart the syllabus. Continue from current doubt map and data engineering progress tracker.

Read these files first:

- 00-control/learning-protocol.md
- 00-control/agent-coordination.md
- 01-syllabus/data-engineering-databricks-fabric-syllabus.md
- 02-progress/data-engineering-progress.md
- 07-question-maps/data-engineering-doubt-map-2026-07-12.md
- 08-targets/eli-lilly-senior-data-engineer-interview-context.md
