# UPMS Architecture Manual, Candidate 6.12: Change History (A.22)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.12 and anonymous-review annex 6.6; not architecture, decides nothing. A.1 to A.21 are in the earlier change-history files, all unchanged. This file adds A.22.

### A.22 Candidate 6.11 → candidate 6.12

Candidate 6.11 (`UPMS_Architecture_Manual_Review_Candidate_6_11.md`, SHA-256 `43a234db345dba99d72c58012b0e485864aa5788817120ab4228f03744feedc7`), the anonymous-review annex 6.5 (`UPMS_Architecture_Manual_Review_Candidate_6_5_Annex_Anonymous_Review.md`, SHA-256 `b2567c2fa8580d2873f6b18c039e80ea258c22c503eaa2b5531673aa2a363f55`) and the other annexes are unchanged. The changes answer the Codex cross-check of candidate 6.11 and D1 1.11 (`UPMS_Candidate_6_11_Codex_Cross_Check.md`, SHA-256 `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3`; Codex, the OpenAI family of the 6.4 to 6.8 reviews, NO-PASS) and the Gemini review of the same texts (`UPMS_Candidate_6_11_Independent_Review.md`, SHA-256 `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4`; Gemini 3.8 Flash (High), PASS conditional on D-97), and apply owner decisions D-97 to D-99 (`UPMS_Owner_Decisions_6_11_Review_2026-11-05.md`, SHA-256 `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295`). The D1 parent moves to 1.12 (map N), the anonymous-review annex to 6.6. The three Serious Challenges predate the objection repairs of 6.9 to 6.11; earlier reviews did not expose them.

#### A.22.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C612-1 | SC-CC611-01: D-64 and D1 F-8 said route status changes only through attributed judgments, while an anonymous objection makes a route challenged | D-98 clarifies D-64. D1 P2 and F-8, core §4.4 and annex §7.8 say an anonymous objection marks routes challenged and supplies no assessment; annex T99 reads status before and after the attributed judgment; D1 stress case 32 |
| C612-2 | SC-CC611-02: Definition 5.3 could label a relation an independent test of a claim it does not target | D1 Definition 5.3 requires a target revision the relation binds; T136; D1 stress case 37 |
| C612-3 | SC-CC611-03: an empty set of cited routes made a source-grounded step circular | D-99. D1 §6.1 defines terminal, grounded and rootless bases and circularity as dependence on the conclusion; F-25 points there; core §5.3 and §9.9; TE-07; T135; D1 stress cases 33 to 36 |
| C612-4 | D-97 pending | Decided in amended form; "pending" removed from D1 and the core; §18.2 lists D-97 to D-99 |
| C612-5 | R611-01: T83 named "an unresolved objection" instead of §12.2's liveness predicate | T83 uses §12.2's predicate and includes an objection resolved at `K2` that stays open for `K1` |

**Not taken, or left open:**
- **The cross-check's §7 simplifications** were not taken in this revision.
- **The Gemini review's route-level overstatement and its nonexistent "D1 §0.3"** are corrected in the cross-check, not in the frozen review.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 40,338 to 40,788 words, the anonymous-review annex from 3,246 to 3,286. D1 1.12 is 12,553 words. The Gate 0 package (D1 1.12, core 6.12, anonymous-review annex 6.6) is 56,627 words.

#### A.22.2 Text moved out of candidate 6.11 (D-85; moved verbatim)

#### Candidate 6.11 §1, revision paragraph and annex sentence

**Revision 6.11 and its files.** Revision 6.11 answers the second review of these texts by a Gemini-family model (NO-PASS, Serious Challenges SC610-01 and SC610-02, findings R610-01 and R610-02; repairs C611-1 to C611-4 in change history A.21). Rules marked **pending** apply D-97, which the author proposed under the owner's delegation of the review cycle and the owner has not made (§18.2). The review package (D-56) is:

The checking and Slice 4 annexes of 6.3, the mathematics annex of 6.4 and the anonymous-review annex of 6.5 are unchanged by this revision and remain part of it; where they name "the core", they mean this core. Section numbers are the core's, and each moved section leaves a stub here.

#### Candidate 6.11 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.10 and D1 1.10 (Gemini 3.8 Flash, Gemini family) | `UPMS_Candidate_6_10_Independent_Review.md`, SHA-256 `2645faef1aed615b859decb02074724c0175ebb4bed9fb689eb4141e3b8258fb` | NO-PASS for D1 1.10 and for core 6.10 with anonymous-review annex 6.5; SC610-01, SC610-02, R610-01, R610-02; repaired in this revision (change history A.21). The same family as the 6.9 review |
| Proposed decision D-97 | `UPMS_Proposed_Decisions_6_9_Review_2026-11-05.md`, SHA-256 `4d5b32f04d94950b7cd0536f1874d0873c62623d41e8a201dc559f37159a56b6` | Applied here as **pending** (§18.2) |
| UPMS Architecture Manual, review candidate 6.10 | `UPMS_Architecture_Manual_Review_Candidate_6_10.md`, SHA-256 `4e396576403ba1fe445e59888647d8af01c952c22bc61207f9a1fdedaf549ebd` | Immediate predecessor, unchanged; changes in change history A.21. Earlier predecessors and reviews are listed with their hashes in A.17 to A.21 |

#### Candidate 6.11 §15.1, T83

| T83 | A year of simulated operation with no requests: nothing is deleted. A refuted claim is recommended for archive with its reason; a record cited by a live claim, an unresolved objection, an open question's position, a pinned record and an open task's checkpoint are never recommended and the core refuses to archive them; recency of use alone recommends nothing; an unassessed observation and a null result are not recommended for irrelevance; archive is reversed by another curator; an archived record is retrievable on request and appears in history and standing |

#### Candidate 6.11 §18.1, independent-review row

| Independent review | The author cannot accept this candidate, the D1 formulation or the proposal; same-family review does not count | Reviewer outside the Claude family (for the next round, of another family than Codex, D-96), then the product owner at Gate 0 |

#### Candidate 6.11 §18.2, proposed-decision table

| ID | Proposed decision (pending the owner; `UPMS_Proposed_Decisions_6_9_Review_2026-11-05.md`) | Applied in |
| --- | --- | --- |
| D-97 | A resolution settles an objection for scientific standing only at the target it assessed; its workflow closes everywhere; a dispute applies through the resolution it disputes | D1 Definition 2.5, F-6 to F-8, §6.1, F-28; §5.11, §6.10, §10.5.1; T129, T134 |

#### A.22.3 Text moved out of anonymous-review annex 6.5 (D-85; moved verbatim)

**Status:** part of review candidate 6.5, proposed D3 architecture; not accepted-current. Reviewed with the core at Gate 0 (D-56). Section and test numbers are those of the core, `UPMS_Architecture_Manual_Review_Candidate_6_5.md`, which leaves a stub at each moved section and whose terms, invariants and decisions govern this text. It replaces the 6.3 annex, which stays unchanged (it was carried unchanged into 6.4); the changes are mapped in change history A.15. They apply owner decisions D-79 and D-85 to the independent review of candidate 6.4 (Codex review SC64-02).

An anonymous participant's lead changes a route's status only through an attributed judgment (D1 F-8, D-37).

| T99 | An anonymous objection points to a counterexample to an inference step a finalization relies on; the anonymous-role session tries to submit an inference assessment and is refused (D-64); a participant records an attributed inference assessment that the step is invalid: the route is broken through that judgment, the anonymous objection is shown and is not treated as a veto, and the decision projection shows both |
