# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.7: Change History (Map I)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of D1 candidate 1.7; not D1 authority, decides nothing. Maps B to G are in `UPMS_Theory_Evidence_Formulation_D1_Change_History.md` and map H in `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_6_Change_History.md`, both unchanged. This file adds map I and holds the §0.1 rows moved out of candidate 1.6 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_6.md`, SHA-256 `4715b231d671becd3bfc92830047122cdd1fd6e923e0c51acc10ea29a30bb7e7`), which stays unchanged.

## I. Change map, candidate 1.6 → candidate 1.7

The changes answer the independent review of candidate 1.6 and architecture candidate 6.6 (`UPMS_Candidate_6_6_Independent_Review.md`, SHA-256 `ac282071dbe79aa61262b70237a5f6e981ddb156a44e652dfb422eb1f0cc39f4`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 and 6.5 reviews) under **proposed** decisions D-90 to D-92 (`UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md`), which the owner has not made. Every change that applies them is marked pending in the text.

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata | Revision 1.7; pending-decision notice; architecture references name candidate 6.7 | — |
| §0.1 | Cut to current parents, the immediate review, the governing decisions and the change histories; earlier predecessors and reviews moved below with their hashes | Review §7 item 1; D-85 |
| Definition 2.5 | Bindings `bind(O)`: first target, carries and rebinds | SC66-02; D-91 (pending) |
| F-3a | Carrying and rebinding add a binding and remove none | SC66-02; D-91 (pending) |
| F-4 | Resolutions and disputes homed among the resolved objection's possible homes, with no tags of their own | SC66-01; D-90 (pending) |
| F-6 | `N(F)` selects objections by any binding in the footprint; projections name the binding | SC66-02; D-91 (pending) |
| F-7a | Readability through the applying binding's tags; the dispute branch covered by F-4's homing | SC66-01, SC66-02; D-90, D-91 (pending) |
| §8.2 | The existence of an objection is not confidential | Review §5 item 3; D-92 (pending) |
| §10.3 | Stress cases 25 and 26 | — |
| §15 | Open challenge 6, the pending decisions | — |
| Appendix A | Anchoring note covers 1.7 and the 1.6 review | — |

No other text changed. **Word count:** 10,885 → 11,032.

## Rows moved out of candidate 1.6 §0.1 (D-85; moved verbatim)

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of D1 candidate 1.5 and architecture candidate 6.5 (Codex, OpenAI GPT family) | `workplans/active/UPMS_Candidate_6_5_Independent_Review.md`, SHA-256 `92ddcda5861711af8cdcdbd43a1b938767ab871cadd7ab6dbfbc8a8c8f2eb515` | NO-PASS; SC65-01, SC65-02, R65-01 to R65-03; its D1 findings (SC65-01, SC65-02, R65-01, and the D1 parts of R65-02 and R65-03) are answered here. The same reviewer and family as the 6.4 review |
| Independent review of D1 candidate 1.4 and architecture candidate 6.4 (Codex, OpenAI GPT-6 family) | `workplans/active/UPMS_Candidate_6_4_Independent_Review.md`, SHA-256 `82941db24d9213921e03b6732d4101d4a58984891bd109d6da53fc4de645d5b6` | NO-PASS; SC64-01 to SC64-03, R64-01 to R64-06; its D1 findings (SC64-01, R64-01 to R64-03, and the D1 parts of SC64-02 and SC64-03) were answered in candidate 1.5 |
| UPMS Theory–Evidence Formulation, D1 candidate 1.5 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_5.md`, SHA-256 `c8876fded8756e93d74bd7885554103e691b84e0f929bd202f0b17b6858ee3b4` | Immediate predecessor; changes in map H |
| UPMS Theory–Evidence Formulation, D1 candidate 1.4 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_4.md`, SHA-256 `5e2b67f97b919d6612db6ed22bd6a3c7456b2be7141e4ef634bb3c2416afbb8f` | Predecessor; changes in the change history, map G |
| UPMS Theory–Evidence Formulation, D1 candidate 1.3 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_3.md`, SHA-256 `4c0c81d1e62b9dbcf09c874e6ef41f626458c60c6d716e7dfba0793fa7a69d77` | Predecessor; changes in the change history, map F |
| UPMS Theory–Evidence Formulation, D1 candidate 1.2 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md`, SHA-256 `219a81bbfa061cf5914df1c144246416ce1b28ea15a6f5985c1a4151ecd01ed2` | Predecessor; changes in the change history, map E |
| UPMS Theory–Evidence Formulation, D1 candidate 1.1 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md`, SHA-256 `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | Predecessor; changes in the change history, map D |
| Same-family review of candidate 1.1 and architecture candidate 6.1 (Claude Opus 5.5, fresh context) | `workplans/active/UPMS_Candidate_6_1_Same_Family_Review.md`, SHA-256 `f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592` | NO-PASS; SC-R1 to SC-R3, R-01 to R-20; same family, so not independent |
| Same-family review of candidate 1.2 and architecture candidate 6.2 (Claude Fable 5.1, fresh context) | `workplans/active/UPMS_Candidate_6_2_Same_Family_Review.md`, SHA-256 `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9` | NO-PASS; S62-1 to S62-3, F62-01 to F62-18; same family, so not independent |
| Same-family review of the mathematics package (Claude Fable 5.1, fresh context) | `workplans/active/UPMS_Mathematics_Package_Same_Family_Review.md`, SHA-256 `ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0` | NO-PASS; SM-1 to SM-4, FM-R01 to FM-R31; its parent-D1 findings (SM-1 to SM-3, FM-R12, FM-R13) are answered here |
| UPMS Theory–Evidence Formulation, D1 candidate 1 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md`, SHA-256 `65b736253c7bcb7e8a0f1d6dafc0251cc59adfb56dfd310cf336ad03766d30fc` | Predecessor; changes in the change history, map B |
