# Source Batch — System Design, AI Engineering, Interview Prep

Captured: 2026-09-23
Tracks: system design, software architecture, backend interviews, AI application engineering, behavioral preparation
Status: extracted; expansion routed to the architecture overlay and question map

## Provenance

Submitted in one message with two images:
- `5829a572-dbf5-4cc7-9150-9cf19202405a.png` — handwritten pre-interview 24-hour ritual.
- `284e32df-daaa-414f-b850-22b0b2bbacf3.png` — 24 software-architecture interview questions.

Original social-post authors, publication dates, and canonical post URLs were not supplied. The `lnkd.in` links below are preserved as submitted; redirect destinations have not been checked. Treat numeric scale claims and interview-loop reports as unverified anecdotes until the original engineering/company source confirms the context.

## Extracted themes and assessment

1. **System design foundations.** A post lists 23 named topics while calling them “25”; preserve the mismatch rather than inventing two missing topics. The titles overlap heavily with the existing system-design overlay. The posts provide titles and links, not enough detail to treat their explanations as evidence.
2. **AI application engineering.** The useful decision topics are model selection, RAG versus fine-tuning, embeddings/retrieval, evaluation, latency, token cost, quality, hallucinations, security, and observability. “Learn fundamentals, justify decisions, measure quality” is a useful learning principle; statements about what interviewers “now” ask are anecdotal and role/time dependent.
3. **Interview preparation resources.** Posts recommend system-design, coding, behavioral, and company engineering-blog resources. Record them as leads, not endorsements or verified quality rankings. The advice to prepare 8–10 STAR stories is a suggestion, not a required count.
4. **Interview-loop reports.** Stripe and Google round descriptions are individual social-media reports, not official or stable hiring specifications. Convert the reported task types into practice: extend existing code, integrate APIs, process data, debug unfamiliar repositories, review AI-generated code, narrate decisions, and discuss real projects. Confirm current format from a recruiter or official source before planning around a specific loop.
5. **Patterns by seniority.** The lists mix architecture styles, design patterns, integration patterns, and infrastructure mechanisms. The “junior/middle/senior” order is not a canonical progression. Learn the problem, forces, costs, preconditions, and failure modes; do not infer that advanced engineers should default to more distributed patterns.
6. **HTTP QUERY.** The post's update is substantially accurate: RFC 10008, *The HTTP QUERY Method*, was published in June 2026 as a Standards Track Proposed Standard. QUERY is defined as safe and idempotent and can carry request content. Its response is cacheable under RFC rules, but cache keys must incorporate the request content and related metadata; QUERY caching is more complex than GET. Standardization does not guarantee uniform deployment support. Primary source: https://www.rfc-editor.org/rfc/rfc10008.html
7. **Numeric architecture claims.** Examples such as 1M RPS, 55M RPS, billions of transactions/swipes, user counts, or extremely high cache-consistency/durability figures need their linked primary articles and definitions before reuse. Ask what workload, time period, consistency/durability meaning, and measurement boundary each number represents.

## Link inventory

### Scaling and Architecture series (23 links supplied; post says 25)

- Load Balancing — https://lnkd.in/gH9rdjCx
- CDN — https://lnkd.in/g83A7-rM
- Caching — https://lnkd.in/gTjxhv2V
- Cache Invalidation — https://lnkd.in/geC955AY
- Rate Limiting — https://lnkd.in/gWqJzCNJ
- API Gateway — https://lnkd.in/gBNKpecH
- CAP Theorem — https://lnkd.in/g4yFYkEi
- Sharding — https://lnkd.in/gFi23iNV
- Replication — https://lnkd.in/gikkrmNp
- Partitioning — https://lnkd.in/gQhJS8ii
- Queues — https://lnkd.in/gPGiuxtu
- Microservices — https://lnkd.in/gZfYV2Qu
- Microservices vs Monoliths — https://lnkd.in/gM-dKE3D
- Fault Tolerance — https://lnkd.in/gdamMmtc
- Database Scaling — https://lnkd.in/ghq4v_gQ
- Service Discovery — https://lnkd.in/gjfbNVBe
- Consistency Models — https://lnkd.in/gGkMENA3
- Eventual Consistency — https://lnkd.in/gdSn54SK
- Distributed Transactions — https://lnkd.in/gTc8pSbH
- Leader Election — https://lnkd.in/g-kwhzSb
- Horizontal vs Vertical Scaling — https://lnkd.in/gW-Vi9Qt
- Back-of-the-Envelope Estimation — https://lnkd.in/gQ6vtM3U
- Idempotency, Data Latency & Finale — https://lnkd.in/gapgNSgh

### Resource recommendations

- TierOnePrep — http://tieroneprep.com/
- ByteByteGo, System Design Primer, Grokking the System Design Interview, NeetCode, LeetCode, and Striver's SDE Sheet were named without direct URLs in the supplied text.

### Company engineering blogs (14 links)

- Stripe Engineering — https://lnkd.in/dEQEbs4D
- Pinterest Engineering — https://lnkd.in/db69r9V3
- Spotify Engineering — https://lnkd.in/djgSjfqu
- Airbnb Tech Blog — https://lnkd.in/dxyxvRd3
- AWS Blog — https://lnkd.in/diH8i8Km
- Meta Engineering — https://lnkd.in/dxEvhNmW
- Google Research — https://lnkd.in/dUNTXB7y
- LinkedIn Engineering — https://lnkd.in/ddFKBz42
- Microsoft Engineering — https://lnkd.in/dsgGCj68
- Netflix Tech Blog — https://lnkd.in/dNhQfbZg
- Shopify Engineering — https://lnkd.in/dSRz4hGx
- Slack Engineering — https://slack.engineering/
- X Engineering — https://lnkd.in/drqsTgwk
- Uber Engineering — https://lnkd.in/dcrRVZaG

### System-design case-study posts (24 links)

- Slack Architecture — https://lnkd.in/eATMDjrK
- Uber nearby drivers, “1 Million RPS” — https://lnkd.in/eeqH9Hjh
- How Lyft Works — https://lnkd.in/eMTEFyja
- Meta cache consistency claim — https://lnkd.in/e88kUZAm
- How Bluesky Works — https://lnkd.in/eEhB8V_k
- Figma/Postgres “4M Users” claim — https://lnkd.in/e7De898X
- How Apple AirTags Work — https://lnkd.in/dizQfm4C
- Stripe idempotent API / double-payment prevention — https://lnkd.in/erMkqwq4
- How Reddit Works — https://lnkd.in/egmm_P7a
- Cloudflare/Postgres “55M RPS” claim — https://lnkd.in/eEQP6Apw
- Tinder “1.6B Swipes/Day” claim — https://lnkd.in/en65fv-W
- How Google Docs Works — https://lnkd.in/ehPNA7Az
- How Twitter Timeline Works — https://lnkd.in/djXiMjnJ
- How WhatsApp Works — https://lnkd.in/eU2fswMi
- How Zoom Works — https://lnkd.in/edidhxZw
- How ChatGPT Works — https://lnkd.in/dwYzJRYG
- How YouTube Works — https://lnkd.in/e7q9F4Sg
- How Airbnb Works — https://lnkd.in/dGVfstQM
- PayPal “1B Transactions/Day with 8 VMs” claim — https://lnkd.in/eqcb7MpP
- Redis use cases — https://lnkd.in/ekJMjMG3
- Netflix microservices lessons — https://lnkd.in/eyVBnWB7
- How Spotify Works — https://lnkd.in/dynAxznF
- Instagram “2.5B Users” claim — https://lnkd.in/ejBKTZPD
- Amazon S3 durability claim — https://lnkd.in/eutGiK35

### Additional system-design examples (30 links)

- Stock exchange — https://lnkd.in/dDaqNNgK
- YouTube — https://lnkd.in/dfQ8-UE8
- Google Docs — https://lnkd.in/dRDzszpB
- Kafka — https://lnkd.in/dJiQjyDx
- URL shortener — https://lnkd.in/dzGQ-Nu6
- WhatsApp — https://lnkd.in/drrVhese
- Airbnb — https://lnkd.in/dj6e5gTy
- Spotify — https://lnkd.in/dynAxznF
- Slack — https://lnkd.in/d78aumwt
- Reddit — https://lnkd.in/dQqrubg3
- Bluesky — https://lnkd.in/dvAChyQn
- Tinder — https://lnkd.in/dxjtUZfH
- Twitter timeline — https://lnkd.in/djXiMjnJ
- Uber nearby drivers — https://lnkd.in/dyR9q6YY
- Amazon S3 — https://lnkd.in/dPXuyAa8
- Apple AirTags — https://lnkd.in/dizQfm4C
- LLMs — https://lnkd.in/dGrSUJmN
- ChatGPT Apps — https://lnkd.in/diDT9mvw
- Uber ETA — https://lnkd.in/dQ9UdBCh
- Meta Serverless — https://lnkd.in/dS6JU9h4
- Live comments — https://lnkd.in/dZ2yUEfd
- Real-time leaderboards — https://lnkd.in/dgdGimQn
- Live presence — https://lnkd.in/dNK8FQYW
- YouTube/MySQL scaling — https://lnkd.in/dyYQUyW7
- Vector databases — https://lnkd.in/dSjbUHt9
- Pastebin — https://lnkd.in/d5VpU2wS
- ChatGPT — https://lnkd.in/dwYzJRYG
- Nginx — https://lnkd.in/dncQQs33
- Lyft — https://lnkd.in/dj3jmFJu
- Google Search — https://lnkd.in/dAMRhXZS

## Image extraction

### Image 1 — Pre-Interview 24-Hour Ritual

**Night before**
- Research (30 min): read the company About page, recent news, and LinkedIn; write three things of genuine interest; reread the job description and match real stories to it.
- Prepare stories (20 min): choose three real experiences covering leadership, failure, conflict, and achievement; structure each as Situation, Task, Action, Result; map stories to question types.
- Logistics: confirm time, format, and interviewer name; test camera/mic/background for virtual interviews; plan clothing for in-person; prioritize sleep.

**Morning of**
- Do not review new problems; review known patterns.
- Read STAR stories aloud.
- Recall three things of interest about the company.
- Eat, hydrate, and move briefly.
- Arrive or log in five minutes early.

**Before starting**
- Reminder: interviewers are evaluating you and want to hire someone; make it easy for them to follow your reasoning.

Interpret as a suggested routine, not a universal or scientifically validated 24-hour protocol. Keep the real-experience and “research company claims from primary sources” constraints.

### Image 2 — Software Architecture Interview Questions

The image contains 24 numbered prompts. The question map groups them by dependency and merges two duplicate pairs: internal service-to-service security (#6/#9) and bottleneck identification (#16/#24). See `07-question-maps/system-design-interview-question-map-2026-09-23.md`.

## Routing

- `01-syllabus/software-architecture-hard-parts-overlay.md` — AI application architecture extension and corrected QUERY note.
- `07-question-maps/system-design-interview-question-map-2026-09-23.md` — OCR questions, deduplication, and study order.
- `04-drills/software-architecture-hard-parts-drills.md` — retrieval and transfer drills.
- Keep detailed explanations for each engineering link in future source-specific notes only when the original article is actually reviewed.
