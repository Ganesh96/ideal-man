# Source batch: database choice, engineering reads, and LeetCode practice

Captured: 2026-09-23
Status: extracted; original URLs preserved. Shortlink destinations are not guessed.

## Database selection framework supplied

The post recommends analyzing data shape/volume/growth, OLTP vs analytics, read/write use cases, horizontal/vertical scaling, consistency, query/index needs, SQL/NoSQL fit, stack compatibility, and future growth.

The post refers to an initial Satish Gupta diagram, but no diagram or explicit database inventory was attached in this batch. No missing systems are attributed to the source. The detailed, qualified decision model is in [Database Selection Decision Map](../07-question-maps/database-selection-decision-map-2026-09-23.md).

## Engineering newsletters and resources

| # | Label | Original URL |
|---:|---|---|
| 1 | System design | https://lnkd.in/ehTrcyak |
| 2 | Actionable tips to write good software | https://lnkd.in/ewTPYGhT |
| 3 | Engineering leadership | https://lnkd.in/ehHM46E2 |
| 4 | Software design & architecture | https://lnkd.in/eAdZAcZi |
| 5 | Test-driven development | https://lnkd.in/ezdTGYKB |
| 6 | Software development tips | https://lnkd.in/e2-fJ-eD |
| 7 | Weekly tech reads | https://lnkd.in/dYsYPA2F |
| 8 | Software design and frontend development | https://thetshaped.dev/ |
| 9 | Engineering career growth strategies | https://lnkd.in/eMVBjiqP |
| 10 | People skills and leadership | https://lnkd.in/eEfdPbiM |
| 11 | Data engineering | https://lnkd.in/eG5hBej6 |
| 12 | DevOps | https://www.tech5ense.com/ |

## Engineering case-study links

Titles and headline figures below are reported in the shared post; article destinations and measurements have not yet been independently verified. Preserve them as leads, not established results.

| # | Title in post | Original URL | Questions to investigate |
|---:|---|---|---|
| 1 | How Grab queries 6.8 billion rows in milliseconds | https://lnkd.in/gH5sFFnh | Data layout, pruning/indexing, latency metric and benchmark boundary |
| 2 | Grab's 20% to 50% cost reductions for most Spark jobs | https://lnkd.in/gZaqfpXN | Baseline, workload sample, cost denominator and correctness guardrails |
| 3 | How Gojek improved memory efficiency and performance by ~50% | https://lnkd.in/gg_iXAMU | Profile evidence, workload, hardware and measurement method |
| 4 | How Gojek reduced app network consumption by 50% | https://lnkd.in/gVeZ5wNF | Payload/transport change, mobile conditions and measurement |
| 5 | Halodoc Data Platform 2.0 (Lakehouse Architecture) | https://lnkd.in/gtyC5GVx | Ingestion, storage layers, governance, batch/stream, operations |
| 6 | Pinterest: 4.5x throughput and 30x cost savings on offline batch ML inference | https://lnkd.in/grTs4etm | Batch design, quality parity, throughput/cost denominator |

## LeetCode advice received and processing

The source recommends topic-based study, a brief theory introduction, 2–3 easy warmups, daily start cues, brute force before optimization, hints before full solutions, a roughly 30-minute stop when stuck, re-coding after reviewing an explanation, and periodic revision.

Refinement:
- Easy warmups lower the entry cost, but move quickly to representative medium problems and changed variants.
- A 30-minute cap is a heuristic; fit the timebox to the target interview and whether useful progress is occurring.
- Use a hint ladder: examples → constraints → pattern clue → partial hint → full explanation. Then close the solution and reconstruct it.
- Retesting and transfer matter more than streaks or problem count.
- Log miss type: pattern recognition, invariant/proof, implementation, edge case, complexity, or communication.

The complete protocol and worked C# problems are in [answer templates](../04-drills/se2-interview-answer-templates.md) and [worked coding examples](../04-drills/se2-coding-patterns-worked-examples-2026-09-23.md).

## Integrity

Verify each article before repeating its title’s numeric claims. Record source date, baseline, workload, metric boundary, comparison and limitations. Distinguish source facts from inference.
