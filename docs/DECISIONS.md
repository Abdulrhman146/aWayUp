# DECISIONS.md — Mutabiq

Architecture and product decision records. Append-only: never edit an accepted
ADR's decision; write a new one that supersedes it.

## Index
| ID | Title | Date | Status |
|---|---|---|---|
| ADR-001 | First project: Mutabiq, a grounded F&B compliance assistant | 2026-10-30 | Accepted |
| ADR-002 | Defer customer validation and the paying-customer target | 2026-10-30 | Accepted |

---

## ADR-000 — Template
- **Date:** YYYY-MM-DD
- **Status:** Proposed | Accepted | Superseded by ADR-XXX | Deprecated
- **Context:** What problem forced this decision now? Include the constraint or
  the measured failure (metric + value), not just "we needed X".
- **Decision:** What we chose, in one or two sentences.
- **Alternatives considered:** Each option, and why it lost. "Didn't think of
  any" is not allowed.
- **Evidence:** What the decision is based on: eval results, benchmark,
  test on N real documents, cost calculation. Link to the run or commit.
- **Consequences:** What gets easier, what gets harder, what risk we accept.
- **Revisit when:** The concrete signal that would reopen this decision.

---

## ADR-001 — First project: Mutabiq, a grounded F&B compliance assistant
- **Date:** 2026-10-30
- **Status:** Accepted
- **Context:** I need a first project that exercises retrieval, grounding and
  evaluation before any agent work, uses public data, has outputs that can be
  checked objectively, and could be sold. Saudi F&B operators deal with SFDA and
  municipal rules spread across Arabic/English PDFs, and violations carry fines
  and closure.
- **Decision:** Build Mutabiq: an API that answers F&B compliance questions,
  cites the article/clause behind every claim, and abstains when the corpus
  does not cover the question. Arabic-first corpus, English questions supported.
  Corpus limited to freely published SFDA and municipal documents.
- **Alternatives considered:**
  - Saudi Labor Law Q&A for SME HR — clean data, but crowded and no edge.
  - Shippy ops assistant (WhatsApp orders, ETAs) — private data, hard to evaluate
    objectively, pulls toward agents. Candidate for a later project.
- **Evidence:** Regulations and penalty tables are publicly published by SFDA;
  every gold answer can map to a specific clause, so eval is objective.
- **Consequences:** Must handle Arabic PDF extraction and legal-text chunking
  well. Paid GSO standards are excluded, so some questions must be refused.
  Regulations change, so the corpus needs versioning.
- **Revisit when:** Corpus extraction quality makes clause-level citation
  impossible, or freely available documents can't cover common questions.

---

## ADR-002 — Defer customer validation and the paying-customer target
- **Date:** 2026-10-30
- **Status:** Accepted
- **Context:** Shippy's client base is too small to source operator interviews,
  and I want the full build-to-production cycle in 3–4 weeks.
- **Decision:** Skip operator interviews. Drop the "2 paying restaurants" target.
  Still build the Moyasar subscription flow end-to-end.
- **Alternatives considered:**
  - Interview 8+ operators first — better questions, but adds ~1 week and
    depends on contacts I don't have yet.
- **Evidence:** None on demand. This is a time/scope decision, not a
  product-evidence one.
- **Consequences:** Gold-set questions are self-written, so they risk mirroring
  the regulations' wording. Mitigations: write the gold set before any
  retrieval code; ≥30% colloquial/vague questions; every design note states
  who is hurt when a component is wrong. Willingness to pay stays unproven.
- **Revisit when:** The product is deployed (Phase 3 done), or 3+ real operator
  questions become available — then compare them against the gold set.