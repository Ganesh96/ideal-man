# Data Engineering Interview Syllabus: Azure Databricks + Microsoft Fabric

## Target role requirements

Primary focus:

- Azure Databricks
- PySpark
- Delta Lake
- Databricks notebooks and production jobs
- Microsoft Fabric
- Fabric Lakehouses
- Dataflows Gen2
- Fabric Data Pipelines
- Data warehouse architecture
- Lakehouse architecture
- Medallion architecture: Bronze, Silver, Gold
- Stakeholder communication

## Learning rule

Every concept must be learned through this frame:

1. Problem solved
2. Mechanism
3. Preconditions
4. Tradeoffs
5. Failure modes
6. Interview explanation
7. Practical scenario

## Batch order

### Batch 1 — Data platform mental model

Goal: understand why Databricks, Fabric, lakehouse, warehouse, and Power BI exist together.

Topics:

- OLTP vs OLAP
- Data lake vs data warehouse vs lakehouse
- Batch vs streaming
- ETL vs ELT
- Raw vs cleaned vs curated data
- Compute-storage separation
- OneLake, ADLS, Delta tables

### Batch 2 — Spark and PySpark foundations

Goal: understand distributed processing before memorizing APIs.

Topics:

- Driver, executors, cluster manager
- DataFrames, partitions, transformations, actions
- Lazy evaluation
- Narrow vs wide transformations
- Shuffle
- Joins and aggregations
- Caching and persistence
- Spark SQL

### Batch 3 — PySpark optimization

Goal: explain why Spark jobs are slow and how to fix them.

Topics:

- Partition sizing
- Skew
- Broadcast joins
- Predicate pushdown
- Column pruning
- File sizing
- Avoiding collect
- Avoiding Python UDFs when built-ins work
- Adaptive Query Execution
- Reading Spark UI and query plan

### Batch 4 — Delta Lake

Goal: understand why Delta is the table format behind modern lakehouses.

Topics:

- Delta transaction log
- ACID transactions
- Schema enforcement
- Schema evolution
- Time travel
- Table history
- MERGE/upsert
- Vacuum and retention
- Optimize/compaction
- Z-order or clustering concepts

### Batch 5 — Databricks environment

Goal: move from notebook user to production-minded engineer.

Topics:

- Notebooks
- Jobs and workflows
- Task dependencies
- Job clusters vs all-purpose clusters
- Parameters/widgets
- Secrets
- Repos/Git
- Libraries
- Unity Catalog basics
- Access control
- Monitoring and debugging

### Batch 6 — Microsoft Fabric fundamentals

Goal: understand Fabric as an integrated analytics platform.

Topics:

- Workspace
- Capacity
- OneLake
- Lakehouse
- Warehouse
- SQL analytics endpoint
- Notebooks
- Dataflows Gen2
- Data Pipelines
- Semantic models
- Power BI integration

### Batch 7 — Fabric Lakehouse design

Goal: design manageable lakehouse layers.

Topics:

- Tables vs Files
- Delta format
- Shortcuts
- Managed tables
- SQL analytics endpoint limits
- Bronze, Silver, Gold lakehouses
- Data quality and lineage
- Governance

### Batch 8 — Dataflows Gen2

Goal: know when low-code transformation is appropriate.

Topics:

- Power Query
- Connectors
- Applied steps
- Data destinations
- Refresh
- Incremental refresh/change processing concepts
- Monitoring
- When Dataflows are not enough

### Batch 9 — Data Pipelines

Goal: orchestrate workflows, not just write transformations.

Topics:

- Copy activity
- Notebook activity
- Dataflow activity
- Parameters
- Schedules/triggers
- Dependencies
- Failure paths
- Retry
- Monitoring

### Batch 10 — Warehouse modeling

Goal: speak clearly about dimensional modeling.

Topics:

- Facts and dimensions
- Grain
- Star schema
- Snowflake schema
- Slowly changing dimensions
- Surrogate keys
- Measures
- Aggregates
- Semantic model readiness

### Batch 11 — Lakehouse architecture patterns

Goal: design end-to-end analytical pipelines.

Topics:

- Medallion architecture
- Ingestion patterns
- CDC concepts
- Data quality checks
- Idempotency
- Replayability
- Audit columns
- Batch windows
- Reprocessing strategy
- Partitioning strategy

### Batch 12 — Interview synthesis

Goal: answer scenario questions.

Practice scenarios:

- Design sales analytics pipeline from ERP to Power BI
- Design incremental ingestion into Bronze/Silver/Gold
- Optimize slow PySpark join
- Handle schema drift from source system
- Explain Delta time travel and retention
- Compare Databricks vs Fabric
- Explain lakehouse vs warehouse to business stakeholders
