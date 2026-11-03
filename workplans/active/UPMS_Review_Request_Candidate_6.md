# UPMS Review Request (Theory–Evidence Proposal, D1 Formulation, Candidate 6)

3 November 2026 · prepared by Claude (AI, Opus 5.5) for the product owner (Sam) · not yet sent

**Please independently review the D1 formulation candidate 1 and UPMS architecture manual candidate 6, and decide PASS or NO-PASS for Gate 0 entry.** The reviewer must be **outside the Claude family**. Both texts, the proposal they apply and every earlier UPMS review except one were written by Claude. The exception is Codex's review of the proposal (NO-PASS), which arrived while these texts were being drafted; they fold in bounded repairs for it. If Codex reviews again, say that the re-review is by the same reviewer family as the first.

## 1. Review package

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction and owner decisions D-20 to D-36; already reviewed NO-PASS (below). Defects that remain in it route to it |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex review of the proposal: SC-TE01 to SC-TE05, TE-R01 to TE-R20. Its revisit condition: close a finding only when the operative body text resolves it |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md` | `65b736253c7bcb7e8a0f1d6dafc0251cc59adfb56dfd310cf336ad03766d30fc` | **Under review:** proposed D1 parent (scientific meaning of the records) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6.md` | `1b125d2c73aa8f78ebb28e549ef0a3a9b363b4581e0a0c4f8dadd72a8ca87062` | **Under review:** proposed D3 architecture; change map in its Appendix A |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base (D-23); diff candidate 6 against it. Not itself under review |
| SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md` | `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Source of the theory semantics (§§3–7) |
| SCIRE repository, `workplans/active/SCIRE_v0.4_Re-Review.md` | `2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e` | Same-family findings SC-41 to SC-43, V4-04 to V4-20; dispositions in candidate 6 Appendix A.5 |

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **Each Codex finding against the operative text,** not against candidate 6's Appendix A.8, which is the author's view and was written after the drafts existed (anchoring risk). The judgment-on-judgment contract (§9.10) and the narrow reading of D-36 (§5.11) are the most consequential.
2. **The reconciliation of candidate 5 §§11, 12, 13 and 15** with D-24 (proportionate security) and D-25 (no time-based retention), clause by clause in candidate 6 Appendix A.3. The proposal's author had not read those sections in full.
3. **The two Serious Challenges the author raised against the proposal**, and their provisional repairs (candidate 6 §18.3):
   - **SC-61:** under D-28, `curate` includes deleting others' items, so a curator could delete a critic's objection silently. Repair: a reason and an attributed deletion marker (§12.3).
   - **SC-62:** release records, processing records and an assisting agent's overseer link would unmask an anonymous critic. Repair: everything an anonymous-role session causes is sealed (§7.8).
   Look for any other record class that leaks a sealed identity.
4. **The front-end boundary** (candidate 6 §4.4): does the back end decide anything that is SCIRE's (discussion, facilitation, review process, inquiry policy), in particular through the decision integrity checks and `validated` commits of §6.9 (C6-11, SC-TE05)?
5. **The standing projection and the one-hop applicable set** (D1 §6, F-6; candidate 6 §9.9): can a material objection be hidden, or can a reader be shown a winner?
6. **The person guard** (D1 §7, candidate 6 §9.13): is any person-level output or authorship-dependent ranking still reachable, directly or by aggregation?
7. **Judgment on judgment** (D1 §6.5, candidate 6 §9.10), which the owner left open: advise accept, reject or defer.
8. **Retention by importance** (candidate 6 §12.1–§12.2): can recency or absence of links become time-based retention by another name (C6-2, C6-3), and is the liveness predicate right?
9. **Simplicity** (C6-13): candidate 6 is larger than candidate 5. Name what can go.

## 3. Requested output

A review record with: any Serious Challenge first, then findings by earliest owning domain (D1 proposal or formulation, D3 candidate 6, or SCIRE front end), each with a counterexample trajectory, a consequence and a bounded repair; PASS or NO-PASS for each of the two texts, and the status of each Codex finding; and the owner decisions you think the texts need (candidate 6 §18.2 and §18.3 list the open ones). Please state your model family and the parts you did not read.

## 4. Owner actions before sending

- Read candidate 6 §18.3 and confirm, change or leave open each item for the reviewer.
- Choose the reviewer (outside the Claude family) and send this package by its hashes.
