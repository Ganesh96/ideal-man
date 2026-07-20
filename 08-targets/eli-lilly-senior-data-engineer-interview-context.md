# Eli Lilly Senior Azure Databricks & Microsoft Fabric Data Engineer Target

## Authority

Canonical job description supplied by the user on 2026-07-20.

Use this file as the end-goal filter for teaching, practical labs, technical drills, mock interviews, and resume-story preparation. Do not infer progress from coverage or course completion.

## Role Outcome

The candidate must appear capable of owning an enterprise Azure data platform from requirements and architecture through implementation, optimization, testing, deployment, governance, production support, and stakeholder communication.

This is not merely a Spark coding role. The evaluation surface combines:

1. distributed data processing depth;
2. lakehouse and warehouse architecture;
3. Databricks and Fabric platform judgment;
4. production engineering and operations;
5. SQL and data modeling;
6. governance, security, and regulated-environment awareness;
7. communication and end-to-end ownership.

## Canonical Requirements

### Mandatory

- Strong hands-on Azure Databricks.
- PySpark, Spark SQL, Delta Lake, and Databricks Notebooks.
- Microsoft Fabric: Lakehouses, Dataflows Gen2, Data Pipelines, and OneLake.
- Data Warehouse and Lakehouse architecture.
- Strong SQL and data modeling.
- Enterprise-scale cloud platform delivery from design through production.
- Data ingestion, transformation, validation, and performance tuning.
- Structured and semi-structured data.
- Collaboration with business stakeholders, architects, BI developers, and cross-functional teams.
- Solution design, code review, testing, deployment, and production support.
- Security, governance, documentation, Git, and CI/CD discipline.
- Independent problem solving and clear stakeholder communication.

### Experience Bar

- Job asks for 8–15 years overall IT experience.
- At least 4+ years in Azure Data Engineering.
- Evidence must be concrete: architecture, scale, implementation decisions, failure diagnosis, tradeoffs, metrics, and operational ownership.

### Good to Have

- Power BI: data modeling, DAX, Power Query, and report development.
- Azure Data Factory and ADLS Gen2.
- Azure DevOps, Git, and CI/CD.
- Azure Synapse Analytics.
- Unity Catalog and Microsoft Purview.
- Agile/Scrum delivery.
- Microsoft Azure or Fabric certifications.

### Domain Advantage

- Manufacturing, pharmaceuticals, healthcare, life sciences, or supply chain.
- Regulated environments, especially GxP/FDA.
- Training must include auditability, lineage, validation evidence, access control, controlled change, reproducibility, retention, and separation of duties without pretending domain experience that was not actually held.

## Interview Probability Map

### Tier 1 — Must Defend Deeply

- Spark execution: driver, executors, partitions, stages, tasks, lazy evaluation, narrow/wide transformations, shuffle.
- PySpark performance: partition sizing, skew, broadcast/sort-merge joins, AQE, predicate pushdown, column pruning, caching, small files, Spark UI and explain plans.
- Delta Lake correctness: transaction log, ACID on object storage, optimistic concurrency, MERGE, schema enforcement/evolution, time travel, retention, VACUUM, compaction, clustering.
- End-to-end ingestion: batch, watermark, CDC, events, APIs, files; idempotency, replay, deduplication, late data, schema drift, reconciliation, quarantine.
- Production Databricks: notebooks versus jobs, cluster choice, parameters, secrets, Git, deployment, monitoring, retries, backfills, Unity Catalog.
- Architecture: lake versus warehouse versus lakehouse, medallion guarantees, compute/storage separation, enterprise scalability.

### Tier 2 — Strong Working Depth

- Fabric: OneLake, workspaces/capacity, Lakehouse versus Warehouse, shortcuts, SQL analytics endpoint, Dataflows Gen2, Data Pipelines, notebooks, semantic models.
- Dimensional modeling: business process, grain, facts, dimensions, surrogate keys, SCD, star/snowflake, late-arriving dimensions, Power BI readiness.
- SQL: joins, windows, aggregation, deduplication, incremental logic, execution plans, indexing concepts, correctness under duplicates and nulls.
- Production engineering: testing pyramid for data, CI/CD promotion, environment configuration, observability, SLAs/SLOs, incident diagnosis, rollback/reprocessing.
- Security/governance: RBAC, least privilege, secrets, catalog permissions, lineage, PII controls, retention, audit trails, Purview/Unity Catalog roles.

### Tier 3 — Differentiators

- Power BI storage modes, semantic-model design, DAX and Power Query boundaries.
- ADF/Synapse comparison and migration/coexistence decisions.
- Cost/capacity reasoning across Databricks and Fabric.
- GxP/FDA-oriented validation, traceability, reproducibility, controlled deployment, and audit evidence.
- Manufacturing/pharma/supply-chain scenario fluency.

## Tool-Boundary Questions to Expect

The interviewer may test whether the candidate knows which service owns which responsibility:

- Fabric/ADF Copy Activity: managed movement and orchestration.
- Auto Loader: incremental discovery of cloud files.
- Spark/PySpark: distributed transformation and computation.
- Delta Lake: transactional table format and state management.
- Kafka/Event Hubs: durable streaming transport and decoupling.
- Fabric Dataflows Gen2: Power Query-based low-code ingestion/transformation.
- Fabric Data Pipelines: orchestration and activity dependencies.
- OneLake/ADLS: storage and namespace.
- Lakehouse/Warehouse: analytical storage and serving choices.
- Power BI: semantic model and consumption, not raw-ingestion correctness.

Answers must cover use case, mechanism, prerequisites, state/checkpoint, delivery semantics, replay, failure modes, tradeoffs, security, and monitoring.

## Submitted Resume Alignment

Resume claims to defend:

- 6+ years building production data platforms, analytical pipelines, ML-ready datasets, and transaction-sensitive workflows.
- Skills listed: Azure Databricks, PySpark, Delta Lake, Microsoft Fabric, Lakehouse architecture, data warehousing, ETL/ELT, Azure/AWS, Kafka, Power BI, DAX, semantic models.
- University of Florida: analytical platform for research simulations; 10GB+ time-series sensor data/day; PostgreSQL/TimescaleDB; raw-to-curated stages; ingestion guards; schema versioning; validation; checkpointed loads; duplicate/schema-drift isolation; partitioning, indexes, caching, and observability.
- Maxil: feature-generation pipelines; 200K+ embeddings/day; Kafka-style clickstream ingestion; PostgreSQL/pgvector/Redis/MongoDB; versioned contracts; reconciliation and instrumentation.
- BestRx: pharmacy claims/billing workflows; 50K+ daily transactions; auditability; asynchronous validation/reconciliation; SQL audit and exception detection; structured logging; correlation IDs; operational dashboards; retry-safe workflows.
- Autoreview: document feature extraction; Python preprocessing; embeddings; vector search; PostGIS/geospatial features; secure document storage and processed metadata.
- Infosys: Oracle/MS SQL to Azure SQL migration analysis; SQL validation, stored procedures, views, tuning; Power BI/SSRS work; compliance checks; Azure storage lifecycle/replication/RBAC.

Never fabricate implementation details. Convert transferable experience into explicit analogies and clearly distinguish direct experience from conceptual or lab-based knowledge.

## Principal Risk

The role requests 8–15 years overall and 4+ years of Azure Data Engineering, while the submitted resume reportedly claims 6+ years overall. Tool keywords alone will not close this gap.

The defense must emphasize:

- complexity and ownership rather than inflated tenure;
- concrete production incidents and design decisions;
- measurable scale, latency, reliability, and business impact;
- credible transfer from database/backend/distributed systems work;
- honest boundaries around direct Databricks/Fabric experience.

## Training Rule

When a lesson intersects this target, include:

INTERVIEW TRAINING
- likely question;
- job requirement tested;
- resume claim or experience it maps to;
- strong answer structure;
- weak answer to avoid;
- technical follow-up probes;
- practical evidence still needed.

## Practical-Evidence Standard

A topic is not interview-ready until the user can:

1. explain the problem and mechanism without notes;
2. implement or trace the core workflow;
3. diagnose at least one realistic failure using evidence;
4. defend a design against an alternative;
5. explain security, governance, testing, deployment, and operations;
6. retell it as a concise senior-level interview answer.

## Current Sequence

Continue from the current doubt map and progress tracker. Do not restart the syllabus.

1. Data state and correctness: grain, time, keys, duplicates, late data, idempotency, replay.
2. Source-to-lake ingestion: batch, watermark, CDC, API, files, Kafka/Event Hubs.
3. Spark/PySpark execution and performance.
4. Delta Lake correctness and maintenance.
5. Production Databricks.
6. Fabric OneLake/Lakehouse/Dataflows/Pipelines.
7. Warehouse modeling, SQL, and Power BI serving.
8. CI/CD, testing, observability, security, governance, and production support.
9. Pharma/GxP scenario overlay.
10. Architecture drills and resume-based mock interviews.

## Resume Story Template

For each claim, prepare:

- business problem and regulated/domain context;
- source systems, data shape, and contracts;
- scale, volume, latency, and SLA;
- architecture and alternatives rejected;
- ingestion and transformation design;
- state, grain, keys, and data model;
- correctness and quality controls;
- failure, evidence, root cause, and fix;
- performance/cost tradeoff;
- security, lineage, validation, and auditability;
- tests, CI/CD, deployment, rollback, and reprocessing;
- monitoring and production ownership;
- stakeholder disagreement or requirement ambiguity;
- measured result;
- honest direct-experience boundary.

## Agent Coordination

Read before continuing:

- `00-control/learning-protocol.md`
- `00-control/agent-coordination.md`
- `01-syllabus/data-engineering-databricks-fabric-syllabus.md`
- `01-syllabus/data-engineering-execution-plan.md`
- `02-progress/data-engineering-progress.md`
- `07-question-maps/data-engineering-doubt-map-2026-07-12.md`
- `08-targets/eli-lilly-senior-data-engineer-interview-context.md`

Do not change progress/confidence based only on this job description. Record progress only from demonstrated evidence.
