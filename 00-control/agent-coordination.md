# Agent Coordination Protocol

This repository is an external memory and coordination layer for ChatGPT/LLM agents helping the user prepare for interviews.

Primary user goal: prepare across multiple interview tracks with high-depth, iterative learning and retesting.

Current active tracks:

- .NET backend / C# / ASP.NET Core / Azure architecture
- Data engineering interview: Azure Databricks, PySpark, Delta Lake, Microsoft Fabric, Lakehouse, Dataflows Gen2, Pipelines, Power BI, data warehouse/lakehouse architecture
- General HLD: distributed systems, networking, scaling, storage, case studies
- General LLD: OOP, SOLID, design patterns, class modeling, interview case studies
- Future/parallel tracks may include frontend, databases, LeetCode, AWS, data engineering tools, system design, and architecture.

## Repository Use

Treat this repo as LLM-oriented memory, not human-facing documentation.

Optimize for:

- compact state recovery
- progress tracking
- mistake-driven retesting
- durable interview phrasing
- cross-track concept reuse
- low-friction continuation by another conversation/agent

Do not optimize for beautiful notes.

## Required Agent Behavior

Before major updates:

1. Inspect existing files relevant to the track.
2. Avoid duplicating syllabus files unless the existing structure is clearly insufficient.
3. Preserve previous mistakes, progress markers, and retest queues.
4. If changing hierarchy, update this file and `00-control/agent-update-log.md`.
5. If adding a new learning track, create or update:
   - `01-syllabus/<track>.md`
   - `02-progress/<track>-progress.md`
   - `04-drills/<track>-drills.md`
   - optionally `03-mistakes/<track>-mistakes.md` if mistakes become numerous.

After each substantial learning session:

- update progress
- add mistakes if user showed incorrect assumptions
- add weak concepts to retest queue
- add concise concept entries only when reusable across tracks
- add a session snapshot if the session changed direction or introduced a major track

## Concurrent Write Safety

Assume another conversation may update the repository at any time.

Before updating an existing file:

1. fetch its latest content and SHA immediately before the write;
2. inspect recent commits affecting the same track;
3. preserve valid work from other agents;
4. make the smallest coherent change;
5. use the fetched SHA for optimistic concurrency.

Additional rules:

- prefer new dated files in `06-sessions/` for append-only history;
- avoid turning one shared file into a high-frequency write hotspot;
- never force-update a branch or overwrite unknown changes;
- if a write fails because the file changed or already exists, re-read and merge semantically;
- use lowercase kebab-case and track prefixes for new files;
- do not silently delete, rename, or move files.

## File Roles

- `00-control/` — coordination rules for agents and learning protocol
- `01-syllabus/` — track-level syllabus and learning order
- `02-progress/` — current state and confidence/progress markers
- `03-mistakes/` — wrong assumptions, corrected models, and retest prompts
- `04-drills/` — theory/interview/coding-template/system-design drills
- `05-concepts/` — reusable concept ledger across tracks
- `06-sessions/` — dated session summaries

## Update Granularity

Prefer compact, structured updates.

Good update:

```md
## 2026-07-10 — Data Engineering Track Added
- Added Azure Databricks + Fabric interview track.
- Current focus: lakehouse mental model, medallion architecture, Delta Lake fundamentals.
- Retest later: OLTP vs OLAP, lake vs warehouse vs lakehouse, Bronze/Silver/Gold.
```

Bad update:

- long transcript
- verbose motivational notes
- uncategorized summaries
- duplicate concept explanations copied into many files

## Mistake Capture Format

Use this structure:

```md
## <Date> — <Mistake Name>

Track: <track>
Context: <where the mistake appeared>
Wrong assumption: <what user believed or implied>
Why plausible: <why the mistake makes sense>
Missing concept: <concept gap>
Corrected model: <short correction>
Retest prompt: <ask the same idea differently later>
Status: open | retested | stable
```

## Retesting Rule

If the user gets a concept wrong, do not only explain it once.

Add it to a retest queue and test later using a different surface form:

- definition question
- scenario question
- tradeoff question
- failure-mode question
- interview-answer question

## Current Teaching Preference

User prefers:

- heavy learning mode first
- direct teaching over constant questioning
- no code unless explicitly requested
- theory, mental models, interview phrasing, tradeoffs, scenarios
- concise but deep explanations
- avoiding meta commentary in normal teaching responses

## Current Data Engineering Interview Focus

Job asks for:

- Azure Databricks hands-on experience
- PySpark distributed processing and optimization
- Delta Lake ACID, time travel, schema evolution
- Databricks notebooks and productionization
- Microsoft Fabric Lakehouses, Dataflows Gen2, Pipelines
- data warehouse architecture: dimensional modeling, star/snowflake schemas
- lakehouse architecture: medallion Bronze/Silver/Gold
- Power BI modeling, DAX, report development as good-to-have

Default training path for this track:

1. Data platform mental model: OLTP, OLAP, lake, warehouse, lakehouse
2. Medallion architecture: Bronze/Silver/Gold
3. Delta Lake fundamentals
4. PySpark distributed processing
5. Databricks notebooks, jobs, clusters, productionization
6. Fabric Lakehouse, Dataflows Gen2, Pipelines
7. Dimensional modeling: facts, dimensions, star/snowflake
8. Pipeline orchestration, monitoring, quality, governance
9. Scenario designs and mock interviews

## Coordination Contract

Any future LLM/agent should first read:

1. `00-control/learning-protocol.md`
2. `00-control/agent-coordination.md`
3. relevant `01-syllabus/*`
4. relevant `02-progress/*`
5. `03-mistakes/retest-queue.md`
6. `05-concepts/concept-ledger.md`

Then continue from the active track rather than restarting from scratch.
