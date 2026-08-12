# Software Architecture: The Hard Parts — Progress

Updated: 2026-08-11
Mode: heavy learning
Current block: Block 0 — Architect Decision Model
Current chapter: Chapter 1 — What Happens When There Are No “Best Practices”?

## Current Learning Point

The active concepts are:

- hard architecture problems have no universal best answer;
- optimize for the least-worst combination of trade-offs;
- architecture concerns are the structural choices that are expensive to change later;
- `why` precedes `how` in architecture reasoning;
- operational versus analytical data;
- ADRs document context, decision, and consequences;
- fitness functions turn important architecture characteristics into objective, repeatable checks;
- architecture governance should favor feedback and automation over static diagrams alone.

## Status

| Block | Chapters | Status | Evidence |
|---|---|---|---|
| 0 Architect Decision Model | 1 | In progress | Initial source map loaded; retrieval/transfer not yet tested |
| 1 Coupling and Modularity | 2–3 | Not started | — |
| 2 Decomposition Mechanics | 4–5 | Not started | — |
| 3 Data Decomposition | 6 | Not started | — |
| 4 Service Granularity | 7 | Not started | — |
| 5 Reuse | 8 | Not started | — |
| 6 Data Ownership/Access | 9–10 | Not started | — |
| 7 Workflows/Sagas | 11–12 | Not started | — |
| 8 Contracts | 13 | Not started | — |
| 9 Analytical Data | 14 | Not started | — |
| 10 Trade-Off Analysis | 15 | Not started | — |

## Mastery Evidence

Do not mark a concept stable until the user can do at least two of:

- define it without notes;
- distinguish it from a nearby concept;
- explain the mechanism/cause-effect chain;
- identify when it becomes a bad choice;
- solve a scenario where one constraint changes;
- connect it to an operational failure mode;
- express the decision in ADR form;
- define a measurable fitness function where applicable.

## Immediate Next Step

Finish Chapter 1 as a decision-making toolkit before Chapter 2:

1. least-worst trade-offs;
2. architecture vs design;
3. architecture characteristics and objective measurement;
4. ADR;
5. fitness functions;
6. Sysops Squad baseline problem;
7. short retrieval drill.
