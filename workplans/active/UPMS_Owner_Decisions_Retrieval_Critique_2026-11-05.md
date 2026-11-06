# UPMS Owner Decisions on the Codex Critique of the Retrieval Design Note, 5 November 2026 (D-117 to D-120)

5 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**These are owner decisions on direction.** The Codex critique of the retrieval design note (REVISE BEFORE DRAFTING) asked the owner four questions. The author recommended an answer to each and asked: "Accept my recommended answers to Codex's four owner questions?" The owner answered **"Accept all four"** (5 November 2026). The recommendations are quoted below as the author put them; the decision text is the author's wording of them.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Retrieval_Design_Note_Codex_Critique.md` | `aae43b0c104791ea35b622e1ef286a38c200d1ccc9e1a5847ee2a16661eef923` | Codex critique: SC-R01 to SC-R03, R-01 to R-15; its "Questions for the owner" are answered here |
| `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_2026-11-05.md` | `49412e997735253135885fa78bcbbfdf81fb806b89f3a7a06c29073362188abb` | Design note revision 1, critiqued; frozen |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` | Decisions D-101 to D-116, refined here |

## 2. Decisions

| ID | Decision | Recommendation the owner accepted | Codex question |
| --- | --- | --- | --- |
| **D-117** | **The discovery map starts cheap and is qualified.** Procedural discovery (D-116) begins with cheap metadata summaries over the asker's eligible population, with defined counting units and a snapshot identity; facets conditioned on the query are optional and budgeted, and partial, bounded or estimated counts are labeled as such. An "unstructured or unknown" population is always shown. This replaces the author's completion of D-116 that the broad step returns exact counts cheaply | "start with cheap metadata summaries, and offer facets that depend on the query only as a budgeted option, where partial or estimated counts are clearly labelled. I recommend yes." | 1 |
| **D-118** | **Exact checks and semantic judgments are reported separately.** A result reports, as separate facts, that its source is intact and current, that it is eligible, and that it satisfies an exact predicate; whether its interpretation is faithful and whether it supports the answer are fallible assessments, attributed and labeled. Semantic candidates that no exact predicate matched are shown only through an explicitly labeled route. This refines D-102, D-104 and D-110 | "report 'the source and an exact predicate match are verified' separately from fallible semantic verification, and show unverified semantic candidates through an explicitly labelled route. I recommend yes; this is the fix for SC-R01." | 2 |
| **D-119** | **Simple deletion boundaries in the first product.** Content is deduplicated only within an independently deletable unit, accepting extra storage; no key is destroyed while it protects surviving content, which is rewritten first. Wider deduplication waits for measured need. This refines D-113 | "deduplicate only within an independently deletable unit, accepting some extra storage, and rewrite survivors before any key is destroyed. I recommend yes. It keeps deletion honest and simple, and wider deduplication can come later if measurement shows it is worth it." | 3 |
| **D-120** | **The larger-scale workload is deferred to D2.** The D2 draft proposes a representative query workload, concurrency, bulk-import rate and degraded recovery service as defaults for the owner to set; until a profile claiming larger scale is bound, the pilot targets of core 6.17 §14.2 stay in force | "I recommend deferring this. The D2 draft would propose a representative query workload, concurrency, bulk-import rate and degraded recovery service as defaults for you to set. Until then the pilot targets stay in force." | 4 |

## 3. Corrections that need no decision

The critique's other findings are repaired by the author in design note revision 2 (`UPMS_Retrieval_Translation_Economy_Design_Note_R2_2026-11-05.md`, its change map). Two corrections concern the decision record of D-101 to D-116, which is frozen:

- its §3 says core 6.17 has "no scaling design and no fidelity–serving invariant". The second half overstates: core 6.17 already makes canonical records authoritative and indexes, hubs and caches derived and rebuildable (§4.1, §9.5, §9.6, §14.3). The SERIOUS CHALLENGE stands as inadequacy of core 6.17 for D-101, not as a defect of the ratified pilot design within its envelope (critique R-15);
- its §3 says none of the D2 triggers of core §1.4 fires. That is too categorical: a no-false-negative pruning guarantee is an error property consumers rely on, which bears on the trigger "no consumer relying on a guaranteed approximation bound" (critique R-04). D2 opens on both grounds.

## 4. What this record does not decide

It accepts no text and changes no ratified text. D-1 to D-116 stand as recorded, except as refined above. If the decision wording says more than the owner was shown, the quoted recommendation governs.
