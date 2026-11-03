# UPMS Review Request (Theory–Evidence Proposal, D1 Formulation 1.1, Candidate 6.1)

3 November 2026 · prepared by Claude (AI, Opus 5.5) for the product owner (Sam) · not yet sent · supersedes the unsent `UPMS_Review_Request_Candidate_6.md`

**Please independently review the D1 formulation candidate 1.1 and UPMS architecture manual candidate 6.1, and decide PASS or NO-PASS for Gate 0 entry.** The reviewer must be **outside the Claude family**. Both texts, their predecessors, the proposal they apply and every earlier UPMS review except one were written by Claude. The exception is Codex's review of the proposal (NO-PASS), which arrived while candidate 6 was being drafted. Candidate 6.1 then followed from the author re-reading that review against candidate 6's body text. If Codex reviews again, say that the re-review is by the same reviewer family as the first.

## 1. Review package

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction and owner decisions D-20 to D-36; already reviewed NO-PASS (below). Defects that remain in it route to it |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex review of the proposal: SC-TE01 to SC-TE05, TE-R01 to TE-R20. Its revisit condition: close a finding only when the operative body text resolves it |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md` | `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | **Under review:** proposed D1 parent; changes from candidate 1 in its Appendix B |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_1.md` | `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a` | **Under review:** proposed D3 architecture; change map in its Appendix A, with A.9 for candidate 6 → 6.1 |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md` | `65b736253c7bcb7e8a0f1d6dafc0251cc59adfb56dfd310cf336ad03766d30fc` | Predecessor of 1.1, for diffing; not itself under review |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6.md` | `1b125d2c73aa8f78ebb28e549ef0a3a9b363b4581e0a0c4f8dadd72a8ca87062` | Predecessor of 6.1, for diffing; not itself under review |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base (D-23); not itself under review |
| SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md` | `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Source of the theory semantics (§§3–7) |
| SCIRE repository, `workplans/active/SCIRE_v0.4_Re-Review.md` | `2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e` | Same-family findings SC-41 to SC-43, V4-04 to V4-20; dispositions in candidate 6.1 Appendix A.5 |

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **Each Codex finding against the operative text,** not against candidate 6.1's Appendix A.8, which is the author's view. The author's own re-check already found that four A.8 entries overstated the repair; assume more may. The judgment-on-judgment contract (§9.10) and the narrow reading of D-36 (§5.11) are the most consequential.
2. **The 6.1 repairs to the anonymous-review back end** (§7.8, D1 F-20a, C61-3 to C61-6): can anything a reader sees still depend on sealed attribution? Try differencing across reviews, across signing, through conflict checks, decline timing, assisting agents, administrator reads of personal scopes and review packages.
3. **The reconciliation of candidate 5 §§11, 12, 13 and 15** with D-24 and D-25, clause by clause in candidate 6.1 Appendix A.3.
4. **The two Serious Challenges the author raised against the proposal** and their repairs (§18.3): SC-61 (deletion marker, §12.3) and SC-62 (sealing everything an anonymous-role session causes, §7.8). Look for any other record class that leaks a sealed identity.
5. **The front-end boundary** (§4.4): does the back end decide anything that is SCIRE's, in particular through the decision integrity checks, the decision-policy owner and `validated` commits of §6.9 (C6-11, C61-2, SC-TE05)?
6. **The standing projection and the one-hop applicable set** (D1 §6, F-6; §9.9): can a material objection be hidden, or a reader be shown a winner?
7. **The person guard** (D1 §7, §9.13) and de-attribution (D1 F-9a, §12.3): is any person-level output or authorship-dependent ranking reachable, and does de-attribution conflict with attribution, deletion or fact-checking?
8. **The author's recommendations** (§18.2, §18.3): advise where you disagree, especially on D-36, operator custody (C6-1), erasure (C6-5) and deferring judgment on judgment.
9. **Retention by importance** (§12.1–§12.2) and **simplicity** (C6-13): candidate 6.1 is larger again; name what can go.

## 3. Requested output

A review record with: any Serious Challenge first, then findings by earliest owning domain (D1 proposal or formulation, D3 candidate 6.1, or SCIRE front end), each with a counterexample trajectory, a consequence and a bounded repair; PASS or NO-PASS for each of the two texts, and the status of each Codex finding; and the owner decisions you think the texts need. Please state your model family and the parts you did not read.

## 4. Owner actions before sending

- Decide, change or leave open each recommendation in candidate 6.1 §18.2 and §18.3.
- Choose the reviewer (outside the Claude family) and send this package by its hashes.
