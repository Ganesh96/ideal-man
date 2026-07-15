# Eli Lilly Senior Data Engineer — Referrer Scope Questions

## Purpose
Use a short conversation with Suresh Reddipalle to identify the true interview boundary, likely client priorities, expected depth, and low-value topics to deprioritize.

## Role context
- Client: Eli Lilly
- Role: Senior Data Engineer
- Known must-haves: Azure Databricks, PySpark, Delta Lake, notebooks, Microsoft Fabric Lakehouses, Dataflows Gen2, Data Pipelines, warehouse/lakehouse architecture, design-to-production ownership, stakeholder communication
- Good to have: Power BI, data modeling, DAX, report development
- Expected interview: deep client-side technical interview

## Highest-value questions

1. **What are the top two or three outcomes the client expects this person to own in the first six months?**
   - Narrows the role to migration, greenfield build, pipeline development, platform stabilization, reporting, governance, or production support.

2. **Between Azure Databricks and Microsoft Fabric, which is the primary platform in daily work, and how are the two used together?**
   - Determines whether to weight Databricks internals, Fabric implementation, or integration architecture.

3. **How hands-on is the interview likely to be? Should I expect live PySpark/SQL coding, notebook exercises, architecture design, debugging, or mostly experience-based discussion?**
   - Defines preparation format.

4. **Which Databricks capabilities are actively used: batch, Structured Streaming, Auto Loader, Workflows, Unity Catalog, Databricks SQL, Delta Live Tables, or ML workloads?**
   - Prevents overstudying unused platform features.

5. **Which Fabric capabilities are central: Lakehouse, Warehouse, Dataflows Gen2, Data Pipelines, notebooks, OneLake shortcuts, semantic models, or deployment pipelines?**
   - Clarifies practical Fabric scope.

6. **What kinds of data and workloads are involved: structured enterprise tables, files, APIs, events, clinical/manufacturing data, streaming, or large historical batch processing?**
   - Reveals ingestion, modeling, latency, and governance requirements.

7. **What scale should I be ready to discuss: approximate daily volume, table sizes, event rates, SLA/latency, concurrency, and retention?**
   - Anchors partitioning, cluster sizing, incremental processing, and performance answers.

8. **Is the architecture primarily medallion lakehouse, dimensional warehouse, or a hybrid? Are star schemas and Power BI semantic models part of this role’s ownership?**
   - Separates engineering-heavy lakehouse work from BI-serving responsibilities.

9. **What production problems are most important to the client: skew, long-running jobs, schema drift, duplicate data, late arrivals, failed loads, small files, cost, data quality, or orchestration reliability?**
   - Reveals likely debugging and decision-making questions.

10. **How much emphasis is placed on regulated-data concerns such as lineage, auditability, access control, validation evidence, PII/PHI handling, and reproducibility?**
    - Critical for Eli Lilly context without asking for confidential information.

11. **Is the work mainly building new pipelines, migrating existing workloads, modernizing legacy ETL, or supporting an established platform?**
    - Changes the architecture and interview narrative.

12. **What gaps have previous candidates shown, or what usually differentiates someone who performs well in this client interview?**
    - Highest signal for hidden evaluation criteria.

13. **Which parts of the job description are truly must-prove in the interview, and which are only supporting skills?**
    - Directly reduces low-value study.

14. **Are there areas I can safely deprioritize for this round—for example deep DAX, ML, raw RDD APIs, Kubernetes, or non-Azure tooling?**
    - Explicitly creates a study boundary.

## Follow-up technical boundary questions
Ask only if the conversation allows more detail.

- Does the team use PySpark DataFrames almost exclusively, or are Spark SQL and SQL-first transformations equally common?
- Are incremental pipelines built with CDC, watermark-based loads, MERGE, Auto Loader, or event streaming?
- How are jobs orchestrated: Databricks Workflows, Fabric Pipelines, ADF, or another scheduler?
- What is the source-control and deployment model for notebooks and pipelines?
- How are environments separated across development, testing, validation, and production?
- Which catalog/governance layer is used: Unity Catalog, Microsoft Purview, Fabric governance, or a combination?
- What monitoring stack is used for pipeline SLAs, data quality, cost, and incident triage?
- Are performance questions likely to go into Spark UI, execution plans, shuffle, partitioning, broadcast joins, skew, caching, and file compaction?
- Are Delta Lake topics likely to include concurrency, MERGE, schema evolution, time travel, OPTIMIZE, VACUUM, and change data feed?
- Does the role own Power BI datasets and DAX, or only the curated data models consumed by BI teams?

## Suggested conversation order
1. First-six-month outcomes
2. Databricks vs Fabric weighting
3. Interview format
4. Workload type and scale
5. Architecture pattern
6. Production pain points
7. Governance/regulatory depth
8. High-signal differentiators
9. Safe deprioritization

## Interpretation rules

- **Databricks-heavy** → prioritize Spark execution model, PySpark DataFrames, optimization, Delta Lake, jobs/workflows, debugging.
- **Fabric-heavy** → prioritize OneLake, Lakehouse vs Warehouse, Pipelines, Dataflows Gen2, notebooks, semantic models, deployment/governance.
- **Migration-heavy** → prioritize source assessment, schema mapping, reconciliation, dual runs, cutover, rollback, data validation.
- **Streaming-heavy** → prioritize Kafka/Event Hubs, Structured Streaming, checkpoints, watermarks, late data, idempotency, exactly-once semantics.
- **BI-heavy** → prioritize dimensional modeling, grain, SCD, Power BI model design, Direct Lake/DirectQuery/import tradeoffs, DAX basics.
- **Regulated-data-heavy** → prioritize lineage, audit trails, reproducibility, access controls, validation evidence, retention, change management.
- **Production-support-heavy** → prioritize monitoring, incident triage, retries, backfills, replay, data quality gates, cost and SLA management.

## Avoid
- Asking every tool keyword as a checklist.
- Asking for confidential client architecture details.
- Questions already answered directly by the job description.
- Presenting as though only interview questions matter; frame around role success and client needs.
- Overclaiming current hands-on depth before preparation is complete.
