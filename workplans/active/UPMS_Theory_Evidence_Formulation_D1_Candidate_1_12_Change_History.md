# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.12: Change History (Map N)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of D1 candidate 1.12; not D1 authority, decides nothing. Maps B to M are in the earlier D1 change-history files, all unchanged. This file adds map N and holds the text moved out of candidate 1.11 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_11.md`, SHA-256 `32bb7a7a6b3d0ea93cc0210a0aedbf9725531c3f0b35e7929bc9d17089c2830e`), which stays unchanged.

## N. Change map, candidate 1.11 → candidate 1.12

The changes answer the Codex cross-check of candidate 1.11 and architecture candidate 6.11 (`UPMS_Candidate_6_11_Codex_Cross_Check.md`, SHA-256 `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3`; Codex, the OpenAI family of the 6.4 to 6.8 reviews, NO-PASS) and apply owner decisions D-97 to D-99 (`UPMS_Owner_Decisions_6_11_Review_2026-11-05.md`, SHA-256 `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295`). The Gemini review of the same texts (`UPMS_Candidate_6_11_Independent_Review.md`, SHA-256 `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4`; Gemini 3.8 Flash (High), PASS conditional on D-97) raised no D1 finding; the cross-check overturned its PASS.

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.12; the two 6.11 reviews, the owner decisions and candidate 1.11 added; the rows they replace moved below; no rule is pending any more | D-97 |
| Definition 2.5, §10.3 case 26 | "pending" removed | D-97 |
| P2, F-8 | An anonymous objection marks routes challenged like any objection and supplies no assessment; P2 says which acts change status | SC-CC611-01, D-98 |
| Definition 5.3 | An independent test or confirmation of `κ` requires `κ` to be a target revision the relation binds | SC-CC611-02 |
| F-25, §6.1 | Terminal basis, grounded and rootless bases; a rootless basis establishes nothing; circularity is dependence on the conclusion, never an empty basis; "rootless" leaves the broken row and joins the premise list | SC-CC611-03, D-99 |
| §10.3 | Stress cases 32 to 37 | SC-CC611-01 to SC-CC611-03 |
| §15 item 6 | The pending D-97 item replaced by D-99's open question | D-97, D-99 |
| Appendix A | Anchoring note covers 1.12 | — |

No other text changed. **Word count:** 11,812 → 12,553.

## Text moved out of candidate 1.11 (D-85; moved verbatim)

#### Status line

**Status:** PROPOSED D1 authority. Not reviewed, not accepted, not ratified. It is the D1 parent that UPMS architecture manual candidate 6.11 (`UPMS_Architecture_Manual_Review_Candidate_6_11.md`) concretizes. Neither file is accepted by being in the repository. Rules marked **pending** apply D-97, which the author proposed under the owner's delegation of the review cycle and the owner has not made; every other rule rests on owner decisions.

#### §0.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of D1 candidate 1.10 and architecture candidate 6.10 (Gemini 3.8 Flash, Gemini family) | `workplans/active/UPMS_Candidate_6_10_Independent_Review.md`, SHA-256 `2645faef1aed615b859decb02074724c0175ebb4bed9fb689eb4141e3b8258fb` | NO-PASS; SC610-01, SC610-02, R610-01, R610-02; its D1 findings are answered here. The same family as the 6.9 review |
| Proposed decision D-97 | `workplans/active/UPMS_Proposed_Decisions_6_9_Review_2026-11-05.md`, SHA-256 `4d5b32f04d94950b7cd0536f1874d0873c62623d41e8a201dc559f37159a56b6` | Applied here as **pending** |
| UPMS Theory–Evidence Formulation, D1 candidate 1.10 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_10.md`, SHA-256 `9805746a18c190a0e5f3aa1dd9f62a543d0b3244b92c9c851ed094266e4a98f0` | Immediate predecessor; changes in map M |

#### P2

- **P2 — Status changes only by an attributed act.** Repetition, summarization, persistence, retrieval rank, copying, age or archive placement change no status.

#### F-8, last sentence

**An anonymous participant never submits a judgment** (owner decision D-64; same-family review F62-02): anonymous-role sessions submit objections, critiques, questions and claims that are not about a person, and route status changes only through attributed judgments (Definition 2.8, D-37).

#### §6.1 Well-foundedness, circularity sentences

so it is computed in one pass with no fixed point. **Circularity is judged per derivation** (same-family review R-02): an inference step `S` with conclusion `κ` is **circular** when, for some premise `P` of `S`, every route that `P`'s effective supporting judgments cite reaches `κ` through inference steps. A premise with one cited route that avoids `κ` keeps `S` non-circular, so a third party's converse step cannot break a well-founded route.

#### §15 item 6

6. **Proposed decision D-97** is pending the owner; the rules marked pending fall with it.
