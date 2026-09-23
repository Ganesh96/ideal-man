# Source Intake and Processing Protocol

## Goal

Turn posts, articles, notes, PDFs, and screenshots into a small set of accurate, connected, testable study assets. Do not use this repo as a pile of copied source text.

## Source record

Capture one source per item in `09-source-inbox/README.md` or an attached batch. Keep the original URL and author/date when visible. If there is no URL, record the filename or where it came from.

Minimum metadata:

- source ID and capture date
- original title, author, publication date, and URL (unknown values stay unknown)
- source format: link, text, PDF, screenshot, or image
- likely tracks and interview type
- processing status
- extracted claims, image text/diagram description, and links found inside the material

## Processing sequence

1. **Capture.** Preserve the source pointer and available context. Do not silently discard a source because its post is brief or generalized.
2. **Extract.** Separate the author’s claims, examples, caveats, external hyperlinks, and image content. For images, transcribe legible text and describe diagrams, labels, relationships, and uncertainty. Mark unreadable parts instead of guessing.
3. **Classify.** Route useful material to one or more of:
   - factual/technical concepts;
   - implementation and operations;
   - system design and architecture scenarios;
   - LeetCode / coding patterns;
   - behavioral evidence and stories;
   - situational judgment and decision scenarios.
4. **Assess.** For each nontrivial claim, record whether it is:
   - **source claim** — what the author says;
   - **verified** — checked against a primary/current source where correctness or freshness matters;
   - **inference** — reasoned extension, labeled as such;
   - **open** — unclear, contested, or awaiting verification.
   Preserve dates and link verification sources. Do not present generalizations as universal rules.
5. **Expand.** Identify prerequisites, mechanisms, trade-offs, constraints, failure modes, counterexamples, adjacent concepts, and interview follow-ups. Add only the concepts that improve the syllabus; link to existing notes rather than duplicating them.
6. **Route.** Update the relevant syllabus, concept ledger, drill set, mistake/retest queue, or role target. Keep source-specific provenance with the resulting notes.
7. **Practice.** Convert the material into an active-recall prompt, scenario, coding task, design decision, or behavioral prompt. Use retrieval before rereading; schedule weak items for a different-form retest.
8. **Close.** Mark the source processed only after useful claims have been routed and practice prompts are recorded. A source that adds no learning value can be marked `skip` with a short reason.

## Source note format

Use this compact structure for substantial sources:

```md
# <Source title>

Source: <author, date, URL or filename>
Captured: <YYYY-MM-DD>
Tracks: <one or more>
Status: captured | extracted | verified | expanded | practiced | retest | skip

## Links found
- <URL> — <why it appears relevant or where it points>

## Extracted
- Source claim:
- Example or evidence:
- Image/OCR notes:
- Uncertainty:

## Concept expansion
- Prerequisites:
- Mechanism:
- Trade-offs / limits / failure modes:
- Adjacent concepts:
- Verification or inference notes:

## Routed to
- <repo path> — <what changed or what should be added>

## Retrieval / interview practice
- Recall:
- Scenario or follow-up:
- Retest trigger:
```

For a batch of tiny posts, one dated batch note may hold multiple source records, but each source keeps its own URL and claim provenance.

## Integrity rules

- Keep personal experience separate from learned or hypothetical examples.
- Never invent employers, ownership, outcomes, metrics, traffic, data volumes, team sizes, or production scale for a resume or interview answer.
- Strengthen truthful experience by clarifying the real problem, personal contribution, decisions, implementation details, constraints, evidence, and lessons.
- Label practice scenarios and hypothetical scale estimates as hypothetical. Use them to demonstrate reasoning, not as claims about past work.
- Prefer a concise paraphrase and a source link over reproducing a post or article.
- When a claim depends on current product behavior, standards, or law, verify it against an authoritative current source before treating it as fact.

## Completion test

A source is useful when a future session can recover: what it claims, where that claim came from, what is known versus inferred, which syllabus concepts it changes, and what the learner should be able to answer or do.
