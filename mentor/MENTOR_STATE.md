# MENTOR_STATE
Last updated: 2026-10-30

## Project
Name: Mutabiq (مطابق)
Brief (2–3 lines): A compliance assistant for Riyadh F&B operators (1–4 branches). It answers SFDA and municipal regulation questions in Arabic and English, cites the article or clause behind every claim, and refuses when the corpus doesn't cover the question. Monthly subscription via Moyasar.
Headline target: On a frozen held-out gold set of 150 questions (≥40% Arabic, ≥30% colloquial, ≥20 not covered by the corpus): ≥85% correct, ≥95% of cited clauses support the claim, ≥90% correct refusals, p95 < 5 s. Deployed with a working Moyasar subscription, 100% of requests traced, monitoring and alerting live.
Out of scope: Customer validation and sales (deferred, see ADR-002); acting as legal advice or guaranteeing compliance; filing license applications; pharma, cosmetics and import/export; paid GSO/Mwasfah standards; agents; mobile app.

## Timeline (current baseline)
| Phase | Goal | Weeks | Exit criterion | Status |
|---|---|---|---|---|
| 0. Corpus + gold set | Define "correct" before building | 0.5 (→ 2026-11-03) | Manifest ≥25 docs (URL, version, date); gold v0 = 60 questions (≥40% Arabic, ≥30% colloquial, ≥10 not covered by corpus) | Not started |
| 1. Hand-built baseline | Retrieval with citations and refusals plus eval runner, no LangChain | 1 (→ 2026-11-10) | One command reports correctness, citation support, refusal accuracy, p95 latency, cost/query; baseline recorded | Not started |
| 2. Quality with evidence | Fix measured failures | 1 (→ 2026-11-17) | Held-out 150: ≥85% correct, ≥95% citation support, ≥90% correct refusals, p95 < 5 s | Not started |
| 3. Ship & observe | Deploy, billing, production monitoring | 1 (→ 2026-11-24) | Public URL with auth and quotas; Moyasar subscription works end-to-end; 100% of requests traced; dashboards for latency, cost, errors, refusals; error alert; daily eval of sampled production traffic; corpus update without downtime | Not started |

## Current Position
Phase: 0. Corpus + gold set
Milestone: M1 (brief pending; open a new chat)
Milestone deadline: 2026-11-03 (provisional; set in M1 brief)
Last update received: 2026-10-30
Next update due: 2026-10-31
Days late on current milestone: 0
Next expected action from me: Commit this state, record ADR-001 and ADR-002, open the Milestone 1 chat on 2026-10-31.

## Latest Metrics
None yet.

## Tracked Weaknesses
None yet (to be diagnosed from submitted work, not assumed).

## Design-Note Bar
v1 (2026-10-30): 5–15 lines covering the problem, the approach, ≥1 rejected alternative with the reason, the top risk with its mitigation, a success metric with a number and how it is measured, and who gets hurt when this component is wrong.

## Re-baseline Log
2026-10-30: Initial baseline. 5 phases, ~5 weeks, end 2026-12-04.
2026-10-30: Dropped customer validation and the paying-customer target (user decision, Shippy client base too small). Compressed to 4 phases, ~3.5 weeks, end 2026-11-24. Gold set must be ≥30% colloquial; design notes must state who gets hurt when the component is wrong.

## Completed Milestones
Kickoff: 2026-10-30, project confirmed (Mutabiq), 1 day late.