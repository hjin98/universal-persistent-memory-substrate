# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.9: Change History (Map K)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of D1 candidate 1.9; not D1 authority, decides nothing. Maps B to J are in the earlier D1 change-history files, all unchanged. This file adds map K and holds the text moved out of candidate 1.8 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_8.md`, SHA-256 `cbbf2c07b0bfd042952c00a392ad5693f329f39dbd3808445b88571dc30ae1da`), which stays unchanged.

## K. Change map, candidate 1.8 → candidate 1.9

The changes answer the independent review of candidate 1.8 and architecture candidate 6.8 (`UPMS_Candidate_6_8_Independent_Review.md`, SHA-256 `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 to 6.7 reviews) under owner decisions D-92 and D-94 to D-96 (`UPMS_Owner_Decisions_6_8_Review_2026-11-05.md`). D-94, the owner's choice to simplify the objection model, supersedes the author's proposals D-90, D-91 and D-93; no rule now depends on a pending decision.

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.9; the 6.8 review, the D-92 and D-94 to D-96 record and candidate 1.8 added; the proposal rows and the 1.7 rows moved below; "pending" notice removed | D-94 |
| Definition 2.5 | One resolution per objection, recording the target it assessed; bindings renamed target history; the per-binding paragraph replaced by the "resolved by assessment at" label | SC68-01, SC67-03; D-94 |
| F-3, F-3a | Resolution names the target its judgment assessed; resolving at a successor is labeled so | D-94 |
| F-6, F-7, F-7a | Applicability and readability through the target history; travel by `unresolved(O)` | SC68-01, SC68-02; D-94 |
| Definition 5.3 | Missing provenance leaves an independent test or confirmation not established | SC68-03 |
| §8.2 | D-92 decided | D-92 |
| §10.3 | Stress cases 26 and 27 rewritten for D-94; 29 added | — |
| §11 | The "resolved by assessment at" label marked beyond the deliverable | D-94 |
| §15 | Open challenge 6 is now whether the simplified model is enough | D-94 |
| Appendix A | Anchoring note covers 1.9 | — |

No other text changed. **Word count:** 11,352 → 11,397.

## Text moved out of candidate 1.8 (D-85; moved verbatim)

#### §0.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of D1 candidate 1.7 and architecture candidate 6.7 (Codex, OpenAI GPT family) | `workplans/active/UPMS_Candidate_6_7_Independent_Review.md`, SHA-256 `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168` | NO-PASS; SC67-01 to SC67-03, R67-01; its D1 findings are answered here. The same reviewer and family as the 6.4 to 6.6 reviews |
| Proposed decisions D-90 to D-92 | `workplans/active/UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md`, SHA-256 `3a9fd1d4a46f70e115664e8233c6aad4fc07bde86a610a24442bd30ff1ed4236` | Applied here as **pending**; the owner has not made them |
| Proposed decisions D-90 and D-92 amended, D-93 | `workplans/active/UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md`, SHA-256 `3a0741c43d9d71802f99c5cce148bba8ab0c19c33878fc0ce1c87c3640c99d8a` | Applied here as **pending**; amends the 6.6 proposals |
| UPMS Theory–Evidence Formulation, D1 candidate 1.7 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_7.md`, SHA-256 `34bc64c07341ef694875379a110880f614931ba94b51a8f03be8944c065b2052` | Immediate predecessor; changes in map J |

#### Definition 2.5, per-binding paragraph

Where a rule says `O` is unresolved in a projection, it means `unresolved(O, b)` for some binding `b` of `O` in that projection's footprint (F-6). A resolution of `O` at a successor `K2` therefore says nothing about `K1`: a decision that relied on `K1` still shows `O` unresolved there. An author who withdraws `O` at a binding they misapplied leaves that binding in history, labeled so on the decisions that relied on it.
