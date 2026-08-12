# Software Architecture: The Hard Parts — Drills

## Chapter 1 Retrieval Drills

### Basic
1. Why does the book reject the idea of a universal best architecture?
2. What does `least-worst combination of trade-offs` mean?
3. What is the book's practical distinction between architecture and design?
4. Define coupling using the book's simplified definition.
5. What are operational and analytical data?
6. What are the three core sections of the book's ADR format?
7. What is an architecture fitness function?

### Intermediate
1. A team says `the system must be high performance`. Why is this insufficient for a fitness function?
2. Distinguish a domain test from an architecture fitness function.
3. Why can a static architecture diagram fail as a governance mechanism?
4. Why might improving security harm another architecture characteristic?
5. Why does the book argue that data became a harder architecture concern with distributed systems?
6. Give one example of an atomic fitness function and one holistic fitness function.

### Transfer
1. A monolith has cyclic dependencies between billing, customer, and ticket components. What would you measure before deciding to decompose it?
2. A team proposes microservices because they are a `best practice`. Identify the reasoning error and the missing context.
3. Design an ADR skeleton for `use asynchronous notifications instead of synchronous notification calls` without choosing the answer until constraints are stated.
4. Define one measurable fitness function for availability and one for deployability.
5. If an architecture decision has a good outcome, does that prove the decision process was good? Explain.

## Retest Variants

For every weak concept, create a later variant across at least two surfaces:

- definition;
- compare/contrast;
- changed constraint;
- failure diagnosis;
- ADR decision;
- fitness-function design.
