# Interview Practice Protocol — 2026-09-23

Purpose: train recall, reasoning, and explanation instead of collecting memorized solutions. This protocol supports the active [SE II interview program](../01-syllabus/software-engineer-ii-interview-training-program.md).

## Unseen coding problems

1. Restate inputs, outputs, constraints, edge cases, and success criteria.
2. Work small normal, boundary, and empty/failure examples.
3. State a direct baseline and its complexity.
4. Find repeated work or an invariant before choosing a pattern.
5. Pick a data structure based on needed operations (lookup, ordering, range, membership, priority).
6. Explain why the invariant remains true; test duplicates and boundaries.
7. Narrate approach, uncertainty, alternatives, and why a change is justified.
8. After a bounded attempt, consult a hint/solution and explain why it works and where it fails.
9. Close the source, reconstruct the idea later, and solve a changed variant.

Use a timebox matching the target interview. If stuck, use this hint ladder: example → brute force → repeated work/invariant → relevant operation/data structure. Longer struggle is not automatically better practice.

## System design

For each case, state requirements/exclusions, workload/SLOs, invariants, minimal baseline, critical read/write paths, biggest risk, failure/recovery, observability, trade-offs, and the changed constraint that would reverse the choice. Use the flexible format in [the design interview map](../07-question-maps/deployment-strategies-and-system-design-practice-2026-09-23.md). Practice unseen prompts as well as classic products.

## Behavioral and project stories

Use only real events. Prepare situation/task, your actions, alternatives/dead ends, stakeholders, evidence/result, and what you would change. Separate your contribution from the team's work; label estimates as estimates.

## After-action notes

Record problem/date, what you tried before lookup, mistaken assumption, correctness verification, explanation clarity, and one retest date/variant. Watched videos and read solutions do not count as solved problems. A concept is stable when you can reconstruct and transfer it without the source.


## Shared answer tools

Use the [answer templates and cheat sheets](./se2-interview-answer-templates.md), [worked coding patterns](./se2-coding-patterns-worked-examples-2026-09-23.md), [worked URL shortener case](./se2-system-design-worked-case-url-shortener.md), and [behavioral story workbook](./se2-behavioral-story-bank-workbook.md). Record mock evidence in [the SE II readiness tracker](../02-progress/se2-interview-readiness.md).
