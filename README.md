# Code Archaeology of AI Systems

> **Engineering investigations into why AI systems drift from their design — by [Runjie Luo](https://luorj.xyz).**

This repository holds a series of code-level investigations into real AI systems. Each one starts from a reasonable assumption about how a system *should* work, follows the actual code, and reports what the code proves — often contradicting the documentation, the architecture decisions, and sometimes the author's own previous claims.

The investigations are not tutorials. They are **forensic reviews**: for each system, the question is not "what does it do?" but "what did it *actually* do, and why does the record disagree with the design?"

## The Pattern

Every investigation in this series finds the same shape of gap — a feature that exists in one layer and disappears in another:

| # | Claim | Code reality | The gap |
|---|-------|-------------|---------|
| 1 | Evidence-driven citation chain | `document_id="evidence_source"` | Evidence declared, not grounded |
| 2 | Conditional workflow DAG | `Edge.condition` never evaluated | Branching declared, not executed |
| 3 | Hybrid search (BM25 + RRF) | Complete subsystem, zero callers | Retrieval declared, not wired |
| 4 | Three-way human approval | Two buttons, `modifications` never transmitted | MODIFY declared, not real |
| 5 | Append-only audit trail | Three layers, in-memory runtime | Record declared, not durable |

The recurring sentence: **declared, but not executed.** Each investigation documents how that gap got there — and what it means for building AI systems people can trust.

## The Investigations

- [Part 1 — Evidence Without Grounding](docs/investigations/part1-evidence-without-grounding.md)
  *I Thought My AI Was Evidence-Driven. The Code Proved Me Wrong.*

- [Part 2 — A DAG That Never Branches](docs/investigations/part2-a-dag-that-never-branches.md)
  *I Expected a next_action Chain. The Engine Had a DAG — and a Condition Nobody Evaluates.*

- [Part 3 — The Hybrid Search Nobody Calls](docs/investigations/part3-the-hybrid-search-nobody-calls.md)
  *The README Said BM25. The Code Had Never Heard of It.*

- [Part 4 — Three Approval Buttons, Two of Them Real](docs/investigations/part4-three-approval-buttons.md)
  *The Third Approval Button Never Existed: How MODIFY Died on the Way From Design to UI.*

- [Part 5 — Three Audit Trails, Zero Truth](docs/investigations/part5-three-audit-trails-zero-truth.md)
  *The Audit Trail That Dies With Restart: how an AI audit system built persistence everywhere except where it runs.*

## About the Author

**Runjie Luo** — AI Engineer, building reliable AI systems. Undergraduate in Data Science, focused on LLM agents, RAG, and multi-agent orchestration.

- Website: [luorj.xyz](https://luorj.xyz)
- GitHub: [github.com/DieRoger](https://github.com/DieRoger)
- Main AI project: [AuditFlow](https://github.com/DieRoger/auditflow) — an AI-powered intelligent auditing platform

## License

The writing in this repository is © 2026 Runjie Luo. All rights reserved.
