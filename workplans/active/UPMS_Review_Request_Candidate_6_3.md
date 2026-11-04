# UPMS Review Request (D1 Formulation 1.3, Candidate 6.3)

3 November 2026 · prepared by Claude (AI, Opus 5.5) for the product owner (Sam) · not yet sent · supersedes the unsent `UPMS_Review_Request_Candidate_6_2.md`

**Please independently review the D1 formulation candidate 1.3, and the core of UPMS architecture manual candidate 6.3 with its anonymous-review annex. Decide PASS or NO-PASS for Gate 0 entry.** The reviewer must be **outside the Claude family**. Every text here was written by Claude. Its only reviews so far are:
- Codex's review of the proposal (NO-PASS);
- a same-family review of candidate 6.1 (Claude Opus 5.5, NO-PASS);
- a same-family check of the candidate 5 reconciliation;
- a same-family review of candidate 6.2 (Claude Fable 5.1, NO-PASS).

Candidate 6.3 repairs what the 6.2 review found. Those repairs have not been reviewed by anyone. If Codex reviews, say that it is the same reviewer family as the proposal review.

## 1. Review package

**Under review:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_3.md` | `4c0c81d1e62b9dbcf09c874e6ef41f626458c60c6d716e7dfba0793fa7a69d77` | Proposed D1 parent; changes from 1.2 in its Appendix E |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3.md` | `e6c02b0a60eead112b2a0ef78b07ff849e0006c71df25e60aeefa24686590a44` | Proposed D3 core: Gate 0 to Slice 2 and every cross-cutting contract |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Anonymous_Review.md` | `e5becbd510ec3205a5b241062c3bdca03a2dcbf90d6f803365f994fef51738cb` | §7.8, §11.5 and their tests |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_3_Change_History.md` | `c2a7ded8dd9198a92989c81ca8216718b7a3af8ff2875bf48cce60c40775e571` | Change map and the author's dispositions: A.8 for Codex, A.10 for 6.1 → 6.2, A.11 for the reconciliation check, A.12 for the history moved out of the core, A.13 for 6.2 → 6.3. Read as claims to test |
| `workplans/active/UPMS_Candidate_6_2_Same_Family_Review.md` | `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9` | Same-family review of 6.2: S62-1 to S62-3, F62-01 to F62-18 |
| `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Owner decisions D-63 to D-70 |
| `workplans/active/UPMS_Candidate_6_1_Same_Family_Review.md` | `f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592` | Same-family review of 6.1: SC-R1 to SC-R3, R-01 to R-20 |
| `workplans/active/UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Owner decisions D-37 to D-46; D-47 to D-56 are in the core's §18.2 |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex review of the proposal: SC-TE01 to SC-TE05, TE-R01 to TE-R20 |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction and owner decisions D-20 to D-36 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2.md` | `0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc` | Predecessor, for diffing only |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md` | `219a81bbfa061cf5914df1c144246416ce1b28ea15a6f5985c1a4151ecd01ed2` | Predecessor, for diffing only |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base (D-23), for context only |

**Not under review now** (D-56):
- the checking annex, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` (SHA-256 `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51`), reviewed before Gate 3;
- the Slice 4 annex, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` (SHA-256 `f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7`), reviewed before Gate 4;
- the mathematics annex, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Mathematics.md` (SHA-256 `a2d59886c3d762f74c69eb5379228accbb986259c99055d4d84e40e4d0b424aa`), with its D1 parent `UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md` (SHA-256 `b50638641a506ae29861cec10fc76a647d6ed961d7345cff27dc0783168047a9`) and decisions D-57 to D-62, reviewed separately. Its hooks H1 to H7 are now in the core and **are** under review as core text.

The SCIRE sources are in the SCIRE repository (`SCIRE_Conceptual_Proposal_v0.4.md` `1816425…`, `SCIRE_v0.4_Re-Review.md` `2d5fb01…`), if needed.

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **The 6.3 repairs, against the 6.2 review's trajectories** (core §18.3, C63-1 to C63-12):
   - withdrawal of a target leaves objections live (D1 F-3b; core §5.11, §6.10, §12.2);
   - the anonymous annex's split into published and operational records, and the sealed per-pseudonym area outside scope permissions (annex §7.8);
   - the total route-status table, "premises not established", compatibility and cross-scope premises (D1 §6.1; core §9.9);
   - same-assessor supersession and no anonymous judgments (D1 Definition 2.8, F-8);
   - the recovery log with dissent, its off-site copy and the restore record (§12.4);
   - the derived late-objection delta and the hand-over of pending decisions (§6.9).
2. **Interactions of the new rules**, which no reviewer has seen: for example, can "target withdrawn, not re-examined" objections accumulate without bound on question pages; can a rebind to a restatement be abused; does the off-site log copy change failure behavior (§13)?
3. **The absorbed mathematics hooks** (core §5, §5.1, §5.3 to §5.5, §4.3; D1 Definition 2.7, §6.1): do they change any existing meaning, and is D-70's rule on discharged hypotheses sound?
4. **Each Codex finding and each same-family finding against the operative text,** not against change history A.8, A.10 or A.13.
5. **Sealed identities:** can anything a reader, proposer, overseer, administrator, processor, front end or log sees still depend on one?
6. **The front-end boundary** (§4.4, §6.9): does the core decide anything that is SCIRE's?
7. **Deletion and restore** (§12): does anything resurrect, vanish silently or keep payload?
8. **The owner decisions D-37 to D-70:** raise a Serious Challenge with a trajectory where one causes a material failure.
9. **Simplicity:** the core is about 37,800 words with its appendices (6.2: about 40,300 by the same count). The Gate 0 package (D1, core and anonymous annex) is about 51,400 words, almost unchanged, because the repairs added about as much as the moves removed. Name what can go.

## 3. Requested output

Write a review record. List any Serious Challenge first. Then give findings by earliest owning domain (D1 formulation, D3 core or annex, the proposal, or the SCIRE front end), each with a counterexample trajectory, a consequence and a bounded repair. Include:
- PASS or NO-PASS for the D1 text, and for the core with its annex;
- the status of each Codex finding and each same-family finding;
- the owner decisions you think the texts still need.

State your model family and the parts you did not read.

## 4. Owner actions before sending

- Choose the reviewer (outside the Claude family) and send this package by its hashes.
