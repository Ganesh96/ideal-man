# Active Learning Track

Updated: 2026-08-11

Primary active track: `Software Architecture: The Hard Parts`.

Status of previous interview-prep tracks: paused, retained for future reuse; do not delete or overwrite them.

## Current Objective

Use the book as the syllabus for deep software-architecture mastery, with emphasis on:

- trade-off reasoning rather than memorizing patterns;
- coupling, modularity, decomposition, service granularity, data ownership, distributed workflows, sagas, contracts, and analytical data;
- system-design and technical-interview transfer;
- practical decision making under uncertainty;
- explicit preconditions, constraints, failure modes, consequences, and measurable architecture characteristics.

## Teaching Method

Default mode: heavy learning, incremental and fast-paced.

For each concept:

1. real problem being solved;
2. naive/default approach and why it fails;
3. core mechanism;
4. prerequisites and assumptions;
5. architecture characteristics affected;
6. trade-offs and second-order consequences;
7. failure modes and operational pain;
8. when not to use it;
9. practical scenario;
10. interview/system-design transfer;
11. short retrieval test or homework;
12. delayed retest if weak.

Avoid code unless the user explicitly requests it.

## Physical Notebook Protocol

Use a compact two-page mechanism rather than copying prose.

Left page — `Decision Map`:
- Problem
- Forces/constraints
- Options
- Coupling introduced/removed
- Trade-offs
- Decision rule

Right page — `Retrieval & Transfer`:
- 3 key terms from memory
- 1 failure scenario
- 1 compare/contrast question
- 1 system-design application
- 1 prediction: what changes if a constraint changes?

## Cross-Book Reasoning Lenses

Use these only when they clarify a real architecture decision, not as decoration:

- `Thinking in Bets`: decision quality is separate from outcome quality; record uncertainty and assumptions.
- `Algorithms to Live By`: explore/exploit, optimal stopping, caching/scheduling analogies where technically appropriate.
- `Predictably Irrational`: detect status quo, sunk-cost, framing, social-proof, and ownership biases in architecture decisions.
- `The Organized Mind`: externalize state, reduce working-memory load, use checklists and clear information boundaries.
- `How to Read a Book`: inspectional pass → analytical pass → syntopical comparison; ask what problem/claim/evidence/trade-off the author is making.
- `80/20`: prioritize concepts that explain many downstream decisions; do not confuse priority with completeness.
- `Four Thousand Weeks / time-management-for-mortals lens`: accept finite study capacity; deliberately omit low-value detail and finish decision loops.
- `Superintelligence`: useful mainly for second-order effects, control/alignment analogies, incentives, and irreversible decisions; do not force-fit AI concepts.

## Source Handling

Primary source order for this track:

1. uploaded Markdown/HTML for fast text retrieval;
2. uploaded PDF only when diagrams/layout matter;
3. current official/web sources only when the book's implementation detail may be outdated or the user asks for updates.

Always distinguish book-derived claims from later updates or model inference.

## Resume/Interview Link

The current goal is no longer the prior Eli Lilly interview. Architecture concepts should still be translated into system-design/interview reasoning when useful, but do not let interview cramming replace book mastery.
