# Source batch: LLD, company guides, ML case studies, and architecture checklist
Captured: 2026-09-23
Status: extracted; canonical destinations verified only where listed below.

## Intake notes

This batch contains LinkedIn-style resource lists, a low-level design syllabus, and two screenshots. The source text is often promotional or simplified. Treat lists as prompts for study, not as authoritative curricula or claims about hiring loops. Preserve each shortlink as supplied. A shortlink itself may redirect or expire; use a canonical destination only when independently verified.

## Low-level design topics supplied

- OOP fundamentals: abstraction, polymorphism, inheritance (also cover encapsulation and composition).
- SOLID, including single responsibility, open/closed, and dependency inversion.
- Patterns: Singleton, Factory, Strategy, Command; select by use case rather than memorizing lists.
- UML: class, sequence, activity, and object diagrams.
- Object modeling: BookMyShow, Uber, ATM.
- Interfaces, abstraction, loose coupling, plug-and-play design.
- TDD, unit tests, mocks/stubs, test-led refactoring.
- Clean code, code smells, meaningful names, DRY, YAGNI, KISS.
- Dependency injection: constructor, setter, and interface injection; IoC.
- Portfolio work: UML, trade-offs, scalability discussion, test cases, documentation.
- LLD interview cases: LRU cache, notification system, Tic-Tac-Toe.

## Company interview guide shortlinks

Original shortlinks preserved as supplied. Final destinations have not been resolved in this intake.

| Company | Source shortlink |
| --- | --- |
| Google | https://lnkd.in/eTmtDJrZ |
| Meta | https://lnkd.in/e-SPVNfv |
| Amazon | https://lnkd.in/ed9vUHbU |
| Microsoft | https://lnkd.in/eA69HGkF |
| NVIDIA | https://lnkd.in/ex_bQfUn |
| Spotify | https://lnkd.in/eA8gVRtV |
| Uber | https://lnkd.in/equ-Bqfk |
| Pinterest | https://lnkd.in/e4tERBsu |
| Apple | https://lnkd.in/eQwvT2Ad |
| Salesforce | https://lnkd.in/eEwyfHdH |

The list was also found reproduced in LinkedIn posts; that confirms the supplied strings, not that each linked document remains current or official. Prefer the company’s own careers/interview pages when preparing.

## Twenty-five-topic shortlink list

Original ordering and duplicates are preserved. The input numbered Database types twice (#9 and #18) and skipped #10; the table records both appearances.

| Input number | Topic | Source shortlink |
| --- | --- | --- |
| 1 | JWT | https://lnkd.in/gdF2ce3K |
| 2 | Idempotency | https://lnkd.in/gj5YZCKs |
| 3 | Rate limiting | https://lnkd.in/gFe2knKy |
| 4 | Observability | https://lnkd.in/gdvfWN-Y |
| 5 | Microservices | https://lnkd.in/gWJGQ4TH |
| 6 | CI/CD pipelines | https://lnkd.in/gjYE-XZx |
| 7 | ACID vs BASE | https://lnkd.in/g2Cw_NZX |
| 8 | Change Data Capture (CDC) | https://lnkd.in/giRj-4Sk |
| 9 | Database types | https://lnkd.in/g3qra9q4 |
| 10 (listed as 11) | System design quality attributes | https://lnkd.in/gxmr9SMD |
| 11 (listed as 12) | Health checks vs heartbeats | https://lnkd.in/gurQrfYF |
| 12 (listed as 13) | API gateway vs load balancer vs reverse proxy | https://lnkd.in/gb7RZvQN |
| 13 (listed as 14) | HTTPS | https://lnkd.in/gS-Q9jBn |
| 14 (listed as 15) | Load-balancing algorithms | https://lnkd.in/g3MiDnUc |
| 15 (listed as 16) | Database caching | https://lnkd.in/g3n3b9JE |
| 16 (listed as 17) | CDN | https://lnkd.in/gdB63sSx |
| 17 (listed as 18) | API protocols | https://lnkd.in/gqwB-3Bc |
| 18 | Database types (duplicate) | https://lnkd.in/g3qra9q4 |
| 19 | gRPC | https://lnkd.in/gzmpF_b3 |
| 20 | SQL vs NoSQL | https://lnkd.in/gVvBWQRc |
| 21 | Message queues | https://lnkd.in/g6SEbyJb |
| 22 | Service discovery | https://lnkd.in/gQnHtbRV |
| 23 | Pub/sub | https://lnkd.in/gNWadRiv |
| 24 | Connection pooling | https://lnkd.in/ga3dVMpK |
| 25 | Consistent hashing | https://lnkd.in/gY-hpmZW |

No final redirects were verified for these 25 links in this intake. Retain the shortlinks as provenance; do not infer the target from the label alone.

## Screenshot A: real-world ML systems

Source: attached image `dcd089f2-0e42-447a-b115-08efc68f7f69.png`. Table text extracted from visible rows. The original image supplies titles but not article URLs; canonical official/organization links below were separately located by title. They are reading destinations, not assertions that each article fully documents the production implementation.

| # | Company | Product/problem in image | Visible article title | Canonical reading link |
| --- | --- | --- | --- | --- |
| 1 | Stripe | Prevent fraudulent transactions | How we built it: Stripe Radar | https://stripe.com/blog/how-we-built-it-stripe-radar |
| 2 | Walmart | Recommend complementary items | Personalized ‘Complete the Look’ model | https://medium.com/walmartglobaltech/personalized-complete-the-look-model-ea093aba0b73 |
| 3 | Uber | Forecast demand for airport rides | Demand and ETR Forecasting at Airports | https://www.uber.com/blog/demand-and-etr-forecasting-at-airports/ |
| 4 | Pinterest | Prevent advertiser churn | An ML based approach to proactive advertiser churn prevention | https://medium.com/pinterest-engineering/an-ml-based-approach-to-proactive-advertiser-churn-prevention-3a7c0c335016 |
| 5 | Stitch Fix | Generate ad headlines | A New Era of Creativity: Expert-in-the-loop Generative AI at Stitch Fix | https://multithreaded.stitchfix.com/blog/2023/03/06/expert-in-the-loop-generative-ai-at-stitch-fix/ |
| 6 | Swiggy | Recommend items to order | Building a mind reader at Swiggy using Data Science | https://medium.com/swiggy-bytes/building-a-mind-reader-at-swiggy-using-data-science-5a5c38aa6c17 |
| 7 | Microsoft | Diagnose production incidents with LLM | Large-language models for automatic cloud incident management | https://www.microsoft.com/en-us/research/blog/large-language-models-for-automatic-cloud-incident-management/ |
| 8 | Foodpanda | Optimize menu sorting order | Menu Ranking | https://medium.com/foodpanda-data/menu-ranking-422ad21f381e |
| 9 | Zillow | Estimate home market value | Building the Neural Zestimate | https://www.zillow.com/tech/building-the-neural-zestimate/ |
| 10 | Airbnb | Identify user interests | Prioritizing Home Attributes Based on Guest Interest | https://medium.com/airbnb-engineering/prioritizing-home-attributes-based-on-guest-interest-3c49b827e51a |
| 11 | GitHub | Generate code and code suggestions | Inside GitHub: Working with the LLMs behind GitHub Copilot | https://github.blog/ai-and-ml/github-copilot/inside-github-working-with-the-llms-behind-github-copilot/ |
| 12 | DoorDash | Optimize courier waiting time | Lifecycle of a Successful ML Product: Reducing Dasher Wait Times | https://careersatdoordash.com/blog/lifecycle-of-a-successful-ml-product-reducing-dasher-wait-times/ |
| 13 (partial row) | Not visible | Improve customer experience via ML-driven payment routing | Screenshot shows only a fragment of this title | Canonical destination not verified; search by exact title before citing |

### Study lens for each ML case

Use the full case-study map at `07-question-maps/real-world-ml-system-case-studies-2026-09-23.md`. For each article, distinguish the business objective, prediction/ranking/optimization task, data and labels, offline/online evaluation, serving path and latency budget, fallbacks, human review, feedback loops, monitoring, and privacy/safety constraints. Do not fill gaps in a public write-up with invented implementation details.

## Screenshot B: system design repository map

Source: attached image `1a11b71a-6117-41bc-aa37-33a61ebd2ef9.png`. The image header points to a GitHub repository. Search verified the likely intended source as [ashishps1/awesome-system-design-resources](https://github.com/ashishps1/awesome-system-design-resources). The screenshot text may visually resemble “aships1”; the verified spelling has “ashishps1”.

Visible categories and items:

- Core concepts: scalability; availability; reliability; SPOF; latency vs throughput vs bandwidth; consistent hashing; CAP theorem; failover; fault tolerance.
- Networking: OSI model; IP addresses; DNS; proxy vs reverse proxy; HTTP/HTTPS; TCP vs UDP; load balancing; checksums.
- API fundamentals: APIs; API Gateway; REST vs GraphQL; WebSockets; webhooks; idempotency; rate limiting; API design.
- Database fundamentals: ACID transactions; SQL vs NoSQL (the screenshot cuts off below this).
- Caching: caching 101; caching strategies; cache eviction policies; distributed caching; CDN.
- Async communication: pub/sub; message queues; CDC.
- Distributed systems/microservices: heartbeats; service discovery; consensus algorithms; distributed locking; gossip protocol; circuit breaker; disaster recovery; distributed tracing.
- Architecture patterns: client-server; microservices; serverless; event-driven; peer-to-peer.
- Trade-offs: top 15 trade-offs; vertical vs horizontal scaling; concurrency vs parallelism; long polling vs WebSockets.
- Interview answer framework.
- Visible easy problems: URL shortener/TinyURL; autocomplete/search engine; load balancer; CDN; parking garage; vending machine; distributed key-value store; distributed cache; authentication system; UPI.
- Visible medium problems: WhatsApp; Spotify; Instagram; notification service; distributed job scheduler; Tinder; Facebook; Twitter; Reddit; Netflix; YouTube; Google Search; Amazon-like e-commerce; TikTok; Shopify; Airbnb; rate limiter; distributed queue/Kafka.
- The screenshot is cropped at the bottom; this is not a complete transcription of the live README. Use the canonical repository above for current links and exact lists.

## Related study artifacts

- [LLD syllabus and case bank](../07-question-maps/low-level-design-syllabus-and-cases-2026-09-23.md)
- [ML system design case studies](../07-question-maps/real-world-ml-system-case-studies-2026-09-23.md)
- [Architecture drills](../04-drills/software-architecture-hard-parts-drills.md)

## Source integrity

The shortlinks and screenshot text are preserved independently of canonical reading URLs. A canonical URL is a best-effort verified destination and may move later; if it stops resolving, retain this source note and replace only the canonical field after re-verification. Separate facts reported by an article from interview heuristics and from your own hypothetical design exercises.
