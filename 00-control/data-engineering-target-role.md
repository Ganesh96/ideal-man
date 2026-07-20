# Target Role: Senior Azure Databricks & Microsoft Fabric Data Engineer

## Source

Canonical role profile supplied by the user on 2026-07-20. Use this file to keep teaching, drills, projects, and mock interviews aligned with the actual job rather than a generic data-engineering roadmap.

## Role mission

Design, implement, optimize, deploy, and support enterprise-scale Azure data platforms from source ingestion through analytical serving.

The candidate must operate across four layers:

1. architecture and requirements;
2. development and data modeling;
3. production deployment and operations;
4. communication, governance, and stakeholder alignment.

## Mandatory platform stack

- Azure Databricks
- PySpark
- Spark SQL
- Delta Lake
- Databricks Notebooks
- Microsoft Fabric
- Fabric Lakehouses
- Dataflows Gen2
- Fabric Data Pipelines
- OneLake
- SQL
- Data Warehouse and Lakehouse architecture

## Strong supporting stack

- Power BI: data modeling, DAX, Power Query, report development
- Azure Data Factory
- Azure Data Lake Storage Gen2
- Azure DevOps
- Git and CI/CD
- Azure Synapse Analytics
- Unity Catalog
- Microsoft Purview

## Expected senior capabilities

### Architecture

- translate business requirements into scalable technical designs;
- choose between Lakehouse and Warehouse patterns;
- design Bronze/Silver/Gold flows;
- define ingestion, transformation, serving, governance, security, and recovery boundaries;
- justify tool selection, cost, latency, and operational tradeoffs.

### Development

- write production-quality PySpark and Spark SQL;
- build ETL/ELT workflows;
- implement incremental loads, deduplication, validation, MERGE, schema evolution, and dimensional models;
- handle structured and semi-structured data;
- optimize joins, partitions, files, shuffles, and query plans;
- convert notebooks into parameterized, testable, deployable jobs.

### Fabric and Databricks operation

- build and manage Lakehouses, OneLake assets, Dataflows Gen2, and Data Pipelines;
- orchestrate Copy, Notebook, Dataflow, validation, and notification activities;
- monitor runs, diagnose failures, retry safely, backfill, and support production incidents;
- manage environments, Git integration, CI/CD, access control, governance, and documentation.

### Data modeling and serving

- define fact and dimension grains;
- design star and snowflake schemas;
- implement slowly changing dimensions and surrogate keys;
- prepare Gold data and semantic models for Power BI;
- maintain metric correctness and source-to-target reconciliation.

### Collaboration

- work with business stakeholders, solution architects, BI developers, and engineering teams;
- lead or participate in solution design, code review, testing, deployment, and production support;
- explain technical decisions to both technical and non-technical stakeholders.

## Experience signal

The role asks for 8-15 years overall IT experience, 4+ years in Azure data engineering, and proven enterprise-scale platform delivery. Interview preparation must therefore emphasize evidence of ownership and judgment rather than isolated tool definitions.

Each major topic should be answerable at these levels:

1. what problem it solves;
2. how it works;
3. how to implement it;
4. how to verify correctness;
5. how to diagnose and operate it;
6. when not to use it;
7. cost and scalability implications;
8. how it fits an enterprise architecture.

## Likely interview evaluation dimensions

1. PySpark/Spark execution and optimization
2. Delta Lake correctness and lifecycle
3. Databricks notebook-to-production engineering
4. Fabric Lakehouse, OneLake, Dataflows Gen2, and Pipelines
5. SQL and dimensional modeling
6. incremental ingestion, CDC, replay, and idempotency
7. architecture tradeoffs: Lakehouse vs Warehouse, batch vs streaming, Copy vs Spark vs Dataflow
8. observability, testing, deployment, security, governance, and incident recovery
9. enterprise delivery and stakeholder communication
10. regulated-domain awareness where applicable

## Preferred domain context

Use Manufacturing, Pharmaceuticals, Healthcare, Life Sciences, and Supply Chain case studies where useful.

Regulated-environment extensions should include:

- auditability and traceability;
- controlled changes and approvals;
- reproducibility;
- data lineage;
- access control and segregation of duties;
- validation evidence;
- retention and deletion policies;
- production incident documentation.

Do not teach GxP/FDA regulations as legal advice. Teach the engineering implications of operating auditable and controlled data systems.

## Persistent project evidence

The main order-analytics case study should eventually demonstrate:

- Azure SQL or file/API ingestion;
- Copy Activity or another justified ingestion mechanism;
- Bronze/Silver/Gold Lakehouse layers;
- PySpark and Spark SQL transformations;
- Delta MERGE, schema evolution, time travel, and recovery;
- Dataflows Gen2 where low-code transformation is appropriate;
- Fabric Pipelines for dependencies, retries, and monitoring;
- Gold star schema and Power BI-ready serving;
- tests, reconciliation, observability, CI/CD, security, and runbooks;
- one regulated-domain variant such as pharmaceutical supply-chain analytics.

## Priority implication

The job is not a narrow Spark coding role. Training must maintain this balance:

- 40% distributed processing, Delta, SQL, and data modeling;
- 25% Fabric/Databricks implementation and productionization;
- 20% architecture, reliability, observability, governance, and cost;
- 15% communication, domain scenarios, and interview synthesis.

The current execution order remains in `01-syllabus/data-engineering-execution-plan.md`.