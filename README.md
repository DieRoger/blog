# Code Archaeology of AI Systems

> **Engineering investigations into why AI systems drift from their design 閳?by [Runjie Luo](https://luorj.xyz).**

This repository holds a series of code-level investigations into real AI systems. Each one starts from a reasonable assumption about how a system *should* work, follows the actual code, and reports what the code proves 閳?often contradicting the documentation, the architecture decisions, and sometimes the author's own previous claims.

The investigations are not tutorials. They are **forensic reviews**: for each system, the question is not "what does it do?" but "what did it *actually* do, and why does the record disagree with the design?"

## The Pattern

Every investigation in this series finds the same shape of gap 閳?a feature that exists in one layer and disappears in another:

| # | Claim | Code reality | The gap |
|---|-------|-------------|---------|
| 1 | Evidence-driven citation chain | `document_id="evidence_source"` | Evidence declared, not grounded |
| 2 | Conditional workflow DAG | `Edge.condition` never evaluated | Branching declared, not executed |
| 3 | Hybrid search (BM25 + RRF) | Complete subsystem, zero callers | Retrieval declared, not wired |
| 4 | Three-way human approval | Two buttons, `modifications` never transmitted | MODIFY declared, not real |
| 5 | Append-only audit trail | Three layers, in-memory runtime | Record declared, not durable |
| 6 | Real-time event system | 16 event types, zero subscribers | Delivery declared, not connected |
| 7 | Persisted API writes | POST 201, GET 404 鈥?zero commit() calls | Write declared, not durable |
| 8 | Single vector space | Index 1024d, queries 1536d | Search declared, not coherent |

The recurring sentence: **declared, but not executed.** Each investigation documents how that gap got there 閳?and what it means for building AI systems people can trust.

## The Investigations

- [Part 1 閳?Evidence Without Grounding](docs/investigations/part1-evidence-without-grounding.md)
  *I Thought My AI Was Evidence-Driven. The Code Proved Me Wrong.*

- [Part 2 閳?A DAG That Never Branches](docs/investigations/part2-a-dag-that-never-branches.md)
  *I Expected a next_action Chain. The Engine Had a DAG 閳?and a Condition Nobody Evaluates.*

- [Part 3 閳?The Hybrid Search Nobody Calls](docs/investigations/part3-the-hybrid-search-nobody-calls.md)
  *The README Said BM25. The Code Had Never Heard of It.*

- [Part 4 閳?Three Approval Buttons, Two of Them Real](docs/investigations/part4-three-approval-buttons.md)
  *The Third Approval Button Never Existed: How MODIFY Died on the Way From Design to UI.*

- [Part 5 閳?Three Audit Trails, Zero Truth](docs/investigations/part5-three-audit-trails-zero-truth.md)

- [Part 6 閳?Sixteen Event Types, Zero Subscribers](docs/investigations/part6-sixteen-event-types-zero-subscribers.md)
  *The Real-Time Architecture Nobody Connected.*

- [Part 7 — The API That Said Yes (LuoBlog)](docs/investigations/part7-the-api-that-said-yes.md)
  *The Write Path That Never Committed.*

- [Part 8 — The Index Was 1024, Queries Were 1536 (LuoBlog)](docs/investigations/part8-the-index-was-1024-queries-1536.md)
  *Two Vector Spaces in One System.*
  *The Audit Trail That Dies With Restart: how an AI audit system built persistence everywhere except where it runs.*

## About the Author

**Runjie Luo** 閳?AI Engineer, building reliable AI systems. Undergraduate in Data Science, focused on LLM agents, RAG, and multi-agent orchestration.

- Website: [luorj.xyz](https://luorj.xyz)
- GitHub: [github.com/DieRoger](https://github.com/DieRoger)
- Main AI project: [AuditFlow](https://github.com/DieRoger/auditflow) 閳?an AI-powered intelligent auditing platform

## License

The writing in this repository is 婕?2026 Runjie Luo. All rights reserved.
