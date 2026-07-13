# Data Engineering Doubt Map — 2026-07-12

## Context

User watched part of Pluralsight Apache Spark 3 Fundamentals and stopped around RDDs. User has many doubts around Spark, PySpark, Lakehouse, Data Warehouse, Fabric, Databricks, CDC, orchestration, streaming, governance, and enterprise architecture.

Primary target: interview for Azure Databricks + Microsoft Fabric / Senior Data Engineer style role.

## Learning mode

Heavy learning mode. Do not switch to mock interview yet.

## Rule

Arrange doubts according to learning path. If a doubt requires prerequisites, teach the prerequisite and then return to the original doubt.

## Ordered doubt clusters

### Cluster A — Data platform mental model
Covers doubts: 0, 1, 2, 4, 14, 15, 16, 22, 23, 24, 33, 34.

Core concepts:
- OLTP vs OLAP
- Data Lake vs Data Warehouse vs Lakehouse
- Bronze zone vs warehouse staging
- Medallion architecture
- orchestration components
- enterprise data platform map
- governance
- replay and raw history
- replication and disaster recovery

### Cluster B — Ingestion patterns
Covers doubts: 1, 5, 6, 7, 9, 26.

Core concepts:
- batch extraction
- scheduled queries
- CDC
- event-driven ingestion
- APIs/webhooks
- Kafka/message queues
- streaming into lakehouse/warehouse
- schema integrity during ingestion

### Cluster C — Spark foundations
Covers doubts: 8, 20, 25, 27, 28, 29, 30, 31.

Core concepts:
- RDDs
- DataFrames / Structured API
- driver/executors
- jobs/stages/tasks
- partitions
- cluster modes
- local/client/cluster mode
- MPP engines vs Spark
- Spark application design

### Cluster D — Transformations and modeling
Covers doubts: 2, 3, 10, 18, 19, 32.

Core concepts:
- cleaning and standardization
- ETL vs ELT
- dbt
- SQL engine vs PySpark
- ML feature engineering
- BI-optimized reporting tables
- dimensional modeling

### Cluster E — Delta Lake, Databricks, Fabric, Snowflake
Covers doubts: 11, 12, 13, 21.

Core concepts:
- Delta Lake transaction log
- ACID/time travel/audit trails
- schema evolution
- Databricks SQL performance
- spot instances
- Snowflake unstructured data
- Fabric Lakehouse/Warehouse/Dataflows/Pipelines

## Recommended response order

1. Start with Cluster A, especially Data Lake vs Warehouse vs Lakehouse grid.
2. Then teach ingestion from OLTP to OLAP.
3. Then return to Spark internals and RDD/DataFrame transition.
4. Then Delta Lake and medallion architecture.
5. Then Fabric/Databricks enterprise architecture.

## Retest later

Ask the user to explain:
- why analytics should not usually run directly on OLTP;
- difference between lake, warehouse, and lakehouse;
- bronze vs staging;
- CDC vs batch extraction;
- where Spark fits;
- why Delta Lake matters;
- why Gold tables are BI-optimized.
