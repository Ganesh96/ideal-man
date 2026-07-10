# Data Engineering Drills: Databricks + Fabric

## Batch 1 — Data platform mental model

1. Explain OLTP vs OLAP using an e-commerce system.
2. Explain why raw application databases should not be used directly for BI dashboards.
3. Compare data lake, data warehouse, and lakehouse.
4. Explain ETL vs ELT and when each is appropriate.
5. Explain Bronze, Silver, and Gold using a sales analytics example.

## Batch 2 — Spark and PySpark foundations

1. What is the difference between a Spark driver and executor?
2. What is a partition?
3. Why is Spark lazy?
4. What is a narrow transformation?
5. What is a wide transformation?
6. Why is shuffle expensive?
7. What happens when you call collect on a large DataFrame?

## Batch 3 — PySpark optimization

1. A Spark job is slow after a join. What do you inspect first?
2. How do you handle data skew?
3. When should you use a broadcast join?
4. Why do many tiny files hurt performance?
5. What is predicate pushdown?
6. What is column pruning?
7. Why are Python UDFs often slower than built-in functions?

## Batch 4 — Delta Lake

1. Why is Delta Lake more than Parquet?
2. How does the Delta transaction log enable ACID behavior?
3. What is time travel used for?
4. What is schema enforcement?
5. What is schema evolution?
6. What is MERGE used for?
7. What is the danger of VACUUM with time travel?

## Batch 5 — Databricks environment

1. Difference between notebook development and production job execution.
2. Job cluster vs all-purpose cluster.
3. How do you parameterize a notebook job?
4. How do you manage secrets?
5. How do you monitor a failed workflow?

## Batch 6 — Microsoft Fabric fundamentals

1. What is OneLake?
2. What is a Fabric Lakehouse?
3. What is the difference between Fabric Lakehouse and Fabric Warehouse?
4. What is a SQL analytics endpoint?
5. When would you use notebooks, Dataflows Gen2, or Pipelines?

## Batch 7 — Architecture scenarios

1. Design ERP to Power BI sales reporting pipeline.
2. Design incremental ingestion with schema drift.
3. Design medallion architecture for clickstream data.
4. Design daily batch processing with retry and alerting.
5. Explain lakehouse architecture to a non-technical stakeholder.
