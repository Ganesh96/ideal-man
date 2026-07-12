# Agent Update Log

This file records hierarchical or coordination-level changes made by LLM agents.

Use it to help future conversations understand what changed without scanning every commit.

## 2026-07-10 — Initial learning OS bootstrap

Created initial repository structure for interview preparation:

- `00-control/learning-protocol.md`
- `01-syllabus/dotnet-backend-syllabus.md`
- `02-progress/progress-tracker.md`
- `03-mistakes/mistake-ledger.md`
- `03-mistakes/retest-queue.md`
- `04-drills/dotnet-theory-drills.md`
- `05-concepts/concept-ledger.md`
- `06-sessions/2026-07-10-dotnet-heavy-learning.md`

Purpose: support .NET backend interview preparation with progress tracking, mistake capture, drills, and concept reuse.

## 2026-07-10 — Data engineering track added

Added Azure Databricks + Microsoft Fabric interview track:

- `01-syllabus/data-engineering-databricks-fabric-syllabus.md`
- `02-progress/data-engineering-progress.md`
- `04-drills/data-engineering-databricks-fabric-drills.md`

Focus:

- Azure Databricks
- PySpark
- Delta Lake
- Microsoft Fabric
- Fabric Lakehouse
- Dataflows Gen2
- Data Pipelines
- dimensional modeling
- medallion architecture
- Power BI basics

## 2026-07-10 — Agent coordination protocol added

Added:

- `00-control/agent-coordination.md`

Purpose:

- clarify that the repo is LLM-facing external memory
- define update rules for multiple conversations/agents
- reduce duplicated or conflicting structure
- record user teaching preferences
- require future agents to update logs when making hierarchy-level changes

Key coordination rule:

Future agents should read `00-control/learning-protocol.md`, `00-control/agent-coordination.md`, relevant syllabus/progress files, retest queue, and concept ledger before continuing.

## 2026-07-12 — Data engineering execution architecture added

Added:

- `01-syllabus/data-engineering-execution-plan.md`
- `06-sessions/2026-07-12-data-engineering-learning-architecture-handoff.md`

Updated:

- `02-progress/data-engineering-progress.md`
- `00-control/agent-coordination.md`

Purpose:

- preserve the 12-batch syllabus as the coverage index while adding an authoritative dependency and teaching overlay;
- prioritize the high-impact Senior Data Engineer core: semantics, idempotency, Spark execution, Delta correctness, modeling, and operations;
- route work across conversation, Pluralsight, Educosys, official documentation, labs, and GitHub according to medium fit;
- define evidence-based mastery, metrics, cost reasoning, and architecture-reading passes;
- set the current execution point to Block 0: data state and correctness;
- add optimistic-concurrency rules because multiple conversations may write simultaneously.

Coordination rule:

Do not replace the original data engineering syllabus with the execution plan. Read both, then use the progress file and latest handoff to determine the next action.
