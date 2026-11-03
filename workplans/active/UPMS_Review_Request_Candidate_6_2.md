# UPMS Review Request (D1 Formulation 1.2, Candidate 6.2)

3 November 2026 · prepared by Claude (AI, Opus 5.5) for the product owner (Sam) · not yet sent · supersedes the unsent `UPMS_Review_Request_Candidate_6_1.md`

**Please independently review the D1 formulation candidate 1.2, and the core of UPMS architecture manual candidate 6.2 with its anonymous-review annex. Decide PASS or NO-PASS for Gate 0 entry.** The reviewer must be **outside the Claude family**. Every text here was written by Claude. Its only reviews so far are:
- Codex's review of the proposal (NO-PASS);
- a same-family review of candidate 6.1 (NO-PASS);
- a same-family check of the candidate 5 reconciliation.

Candidate 6.2 repairs what the same-family checks found. Those repairs have not been reviewed by anyone. If Codex reviews, say that it is the same reviewer family as the proposal review.

## 1. Review package

**Under review:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md` | `219a81bbfa061cf5914df1c144246416ce1b28ea15a6f5985c1a4151ecd01ed2` | Proposed D1 parent; changes from 1.1 in its Appendix D |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2.md` | `0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc` | Proposed D3 core: Gate 0 to Slice 2 and every cross-cutting contract |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Anonymous_Review.md` | `f7083ddf4ab75ac83a9f8d881e821ba352b7f07c87b6c893f60373b723f1452f` | §7.8, §11.5 and their tests |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_2_Change_History.md` | `a20ecbdd33a3e2e4d858f2cce8b281a8c3cb7edf143597c101db9b9dec2a0b31` | Change map and the author's dispositions: A.8 for Codex, A.10 for 6.1 → 6.2, A.11 for the reconciliation check. Read as claims to test |
| `workplans/active/UPMS_Candidate_6_1_Same_Family_Review.md` | `f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592` | Same-family review of 6.1: SC-R1 to SC-R3, R-01 to R-20 |
| `workplans/active/UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Owner decisions D-37 to D-46; D-47 to D-56 are in the core's §18.2 |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex review of the proposal: SC-TE01 to SC-TE05, TE-R01 to TE-R20 |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction and owner decisions D-20 to D-36 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_1.md` | `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a` | Predecessor, for diffing only |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md` | `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | Predecessor, for diffing only |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base (D-23), for context only |

**Not under review now:** `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Checking.md` (SHA-256 `eb0332c9b75854b814606e840e72d8a4b5b6b0d58aac1aae4b4e4c549eb3323b`). It covers screening, vocabulary, the processing cascade, fact-checking and deferred channel assessment, all Slice 3 or later. Under D-56 it is reviewed before Gate 3. The proposed mathematics annex (`workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Mathematics.md`), with its D1 parent `UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md`, is also not under review. It needs six additive hooks in the core (its §M.0). Please note any way the core as written would conflict with them.

The SCIRE sources are in the SCIRE repository (`SCIRE_Conceptual_Proposal_v0.4.md` `1816425…`, `SCIRE_v0.4_Re-Review.md` `2d5fb01…`), if needed.

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **The repairs of the same-family findings, against their trajectories** (core §18.3, C62-1 to C62-12):
   - objections carried on revision (D1 F-3a);
   - scientific effectiveness (D1 Definition 6.0, core §7.6, §9.9);
   - the anonymous role as a distinct session type (annex §7.8);
   - the late-objection delta and signature completeness (§6.9);
   - the recovery log (§12.4).
2. **Each Codex finding against the operative text,** not against change history A.8.
3. **Sealed identities:** can anything a reader, proposer, overseer, administrator, processor or log sees still depend on one?
4. **The front-end boundary** (§4.4, §6.9): does the core decide anything that is SCIRE's?
5. **Standing** (D1 §6, core §9.9): can a material objection be hidden, a stale or disputed route shown as sound, or a winner shown?
6. **Deletion and restore** (§12): does anything resurrect, vanish silently or keep payload?
7. **The owner decisions D-37 to D-56:** raise a Serious Challenge with a trajectory where one causes a material failure.
8. **Simplicity:** the core is about 40,300 words, against 6.1's 47,500; the split and deferrals removed less than expected. Name what can go.

## 3. Requested output

Write a review record. List any Serious Challenge first. Then give findings by earliest owning domain (D1 formulation, D3 core or annex, the proposal, or the SCIRE front end), each with a counterexample trajectory, a consequence and a bounded repair. Include:
- PASS or NO-PASS for the D1 text, and for the core with its annex;
- the status of each Codex finding and each same-family finding;
- the owner decisions you think the texts still need.

State your model family and the parts you did not read.

## 4. Owner actions before sending

- Choose the reviewer (outside the Claude family) and send this package by its hashes.
