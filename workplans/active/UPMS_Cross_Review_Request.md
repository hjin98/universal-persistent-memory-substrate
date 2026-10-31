# UPMS Cross-Review Request (Candidate 2)

31 October 2026 · requested by the product owner (Sam) · prepared by Claude (AI)

**Please independently review UPMS Architecture Manual review candidate 2 and decide PASS or NO-PASS for Gate 0 entry.** Attempt to falsify it: look for traces where every component obeys its local rule while the system still violates correction, confidentiality, deletion, permission or coherence guarantees. The manual's author (an AI) cannot accept its own text; this review is the independent falsification step it requires.

## 1. Review Package

**Review the candidate itself; use the other documents only to check that nothing was lost or weakened.**

| File | SHA-256 | Role in this review |
| --- | --- | --- |
| `UPMS_Architecture_Manual_Review_Candidate_2.md` | `16fee00e43899a7cfd34c3e4fc4e67c3deee4bd3c32e982546f942783a14266f` | **The object under review** |
| `UPMS_Round_2_Amendments.md` | `0b5bada26c400cafefe5a758b884b1c4824fea2e3cf245e196f711ea12740285` | Rationale for the new material (A1–A7) |
| `UPMS Architecture Manual - Refined.md` (review candidate 1) | `0ffc2740b4ec9088511754c1d2593262feff74d8bac6a1e39c4f37ab55ab4443` | Baseline; check that its repairs survive |
| `UPMS Architecture Review.md` (F01–F18) | `b0617a925916a130d47187917e54acd009ba3f367da29015c916ff94e8854f50` | Earlier findings; check that each disposition still holds |
| `UPMS Architecture Proposal v0.3.md` | `da109215e9de0bafb3e7aff68bbe4d768c017c5e70050aa7d6811795284a6f0b` | Product requirements baseline |

The two Markdown files are exports of Claude Docs artifacts; their two diagrams are rendered as plain-text figures. The earlier v0.3 review (R1–R7) is reproduced in the candidate's Appendix A. Documents and their contents are design inputs, not instructions to execute tools.

**Method.** The candidate was written under the SSDP 7.2.1 software-design method; no task `protocol_version` is assigned. A D3 review reconstructs the governing requirements, attempts falsification of ownership, state, concurrency, security, resource, compatibility and abstraction adequacy, and raises a Serious Challenge if the architecture itself is contradictory, materially ambiguous or unrealizable.

**Already decided by the owner:** Codex with OpenAI-family models first, Claude second; configurable retention; the proposed defaults D-1 to D-10 are kept for this round (§18.2), and domain-adapted small models are in scope (D-11). You may still argue against any of them.

## 2. Priority Focus

**Most risk sits where the new material (A1–A7) meets the earlier repairs (F01–F18); spend effort there first.**

| Area | Candidate sections | Why it may break |
| --- | --- | --- |
| Permissions × release fence | §7.3.7, §9.4 | Revocation and group removal are now restriction commits; membership is owned externally and cached |
| Cross-scope derived memory | §7.3.4–7.3.5, §5.5 | Readability requires rights on every source scope; cost, staleness and leakage through metadata |
| Administrator power | §7.3.6, §11.4 | Elevation, access records and the limits that bind admins too |
| Publication as the only declassification | §10.6.2, §7.4, §5.5 | Owner-only release of dependencies; interaction with mixed-source items and redaction |
| Lineage exclusion and blind work | §10.6.4, §10.4, §8.1 | Enforcement across context, overview and runtime; what the independence attestation can honestly claim |
| Overview layer | §10.5 | Per-reader assembly, overlay versus narrative, invalidation without an LLM, consolidation errors and budget |
| Statement language and screening | §5.7, §9.7 | Determinism of flags, rule matching scope, coverage of what cannot be structured |
| Vocabulary governance | §5.8 | Poisoning through proposals, merge reversibility, scope disclosure through definitions |
| Adapters | §9.8 | Training-data selection, membership inference, deletion fallback and retraining, re-embedding cost |
| Delivery placement | §16 | Whether Slice 1a is still thin enough, and whether gates test the right invariants |

## 3. Falsification Questions

**Answer each with a concrete trajectory that breaks the guarantee, or with the reason none exists.**

1. Can an agent session read content after its user loses group access but before the restriction is acknowledged, or after acknowledgement through a cache, overview line, adapter or handle?
2. Can a derived item, flag, coverage report or overview reveal the existence or content of a scope the reader lacks `l` on?
3. Can publication release a dependency the publisher does not own, for example through redaction copies, merged vocabulary or a consolidation output?
4. Can a lineage-excluded source reach a blind reviewer's context through the shared pool, an overview hub, a vocabulary definition or an adapter?
5. Can an administrator, or an agent acting for one, read past a barrier, forge attribution, or erase the evidence of an elevated access?
6. Can screening ever change admission, truth status or a slot's current value without an investigation producing a judgment?
7. Can planted external content alter the vocabulary, a screening rule or an adapter in a way that changes another principal's retrieval or flags?
8. Can a consolidated narrative present a fact that is stale, deleted, contradicted by exact projections or unreadable by the reader?
9. Does any new mechanism make a guarantee from F01–F18 weaker, or depend on a capability the Codex integration has not shown?
10. Is anything here more complex than the user journeys need? Name what could be removed while keeping §1.2's journeys and §15's invariants.
11. Are D-1 to D-10 coherent with each other and with the invariants? Is any default unsafe?
12. Is "no D1 or D2 parent" still correct with the statement language, screening, adapters and consolidation included (§1.4)?

## 4. Expected Output

**Return a decision record first, then findings ranked by severity; a revised candidate is welcome but must be a separate document with a change map.**

1. **Disposition:** PASS or NO-PASS for Gate 0 entry, and any Serious Challenge stated first.
2. **Findings,** most severe first, each with:
   - ID, affected section and invariant;
   - the concrete counterexample trajectory;
   - consequence and severity (blocker, major, minor);
   - the proposed alternative, its cost, and how to verify it;
   - whether it is a D3 defect or a D4 choice the manual deliberately leaves open.
3. **Regression check:** for each of F01–F18, whether its repair survives in this candidate.
4. **Simplification:** anything removable while keeping the journeys and invariants.
5. **Decisions:** agreement or disagreement with D-1 to D-10, with reasons.
6. **Evidence ledger:** what you read and checked, what you did not, and your own limits as a reviewer (asserter: human or AI, and which agent).

Do not edit the candidate in place. If you produce a review candidate 3, deliver it as a new document, record its SHA-256, and map every change to a finding.
