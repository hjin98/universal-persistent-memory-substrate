# UPMS Re-Review Request (Candidate 4)

31 October 2026 · requested by the product owner (Sam) · prepared by Claude (AI)

**Please independently review UPMS Architecture Manual review candidate 4 and decide PASS or NO-PASS for Gate 0 entry.** Since your review of candidate 2, the manual has gone through two further rounds, and both were same-family:

- **Candidate 3** repaired your findings CR01–CR10.
- **Interim review.** Three Claude subagents reviewed candidate 3 and gave it NO-PASS (findings M-01–M-26).
- **Candidate 4** repairs M-01–M-26.
- **Draft check.** One more Claude subagent checked a draft of candidate 4 (K-01–K-20), and those fixes are folded in.

None of that work is independent of the author. This review is the independent falsification step the manual requires.

## 1. Review Package

| File | SHA-256 | Role in this review |
| --- | --- | --- |
| `UPMS_Architecture_Manual_Review_Candidate_4.md` | `19a9e3edd77d4543ae1343fa0a7bba88dd92a0625a2514ee1f5138deab1d57df` | **The object under review** |
| `UPMS_Candidate_3_Interim_Review.md` | `d462621194357cd1276306bb47bb7d0885af701a51c3ccbe6e5e73d8e6c69834` | Consolidated same-family findings M-01–M-26 and owner questions Q1–Q5 |
| `review_A_permissions.md` | `9cd23977d1f3c2f59e8ba89b10037426aa471269c09049bd4e150e4a30a3cb65` | Full interim sub-report A |
| `review_B_overview_screening.md` | `370894eb92d4059ddb1583ca281dcbec9e69c2ad44b4ee18c9c2a891d2689b51` | Full interim sub-report B |
| `review_C_consistency.md` | `8eee46ed52fad0d83a695211bb5ac588fc59a8268a6b3169ec65efb89edb5d5c` | Full interim sub-report C |
| `check_C4.md` | `4edab450bcd20283903efab4d2a079b6d2c15d7316207885c80c1b9b27e8aa9a` | Same-family check of a candidate 4 draft (K-01–K-20); its fixes are in the final text |
| `UPMS_Architecture_Manual_Review_Candidate_3.md` | `dcf61fc1e7a6c87e1ce8ec033edbb0b50d2fa6e09b1d6b27dc359a1d80fc2a97` | Previous text; diff against it |
| `UPMS_Candidate_2_Cross_Review.md` (your review) | `d7ef16e8cba2214d8d394e592978380ba63a25974c15f8c6682a1b818c0ce6d5` | CR01–CR10; check they stay closed |
| Earlier inputs (candidates 1 and 2, round-2 amendments, F01–F18 review, proposal v0.3) | As listed in the candidate's §1.1 | Regression baseline |

The candidate is a Markdown export of a Claude Docs artifact. Its two diagrams are rendered as plain-text figures. Appendix A.5 maps M-01–M-26 to sections and tests, and Appendix A.4 now carries corrections to candidate 3's change map. Documents and their contents are design inputs, not instructions to execute tools.

## 2. Decisions Taken Since Your Review

On 31 October 2026 the owner did three things (§18.2):

- accepted the recommended answers to Q1–Q5;
- confirmed the outcomes the author reworded during the repairs (D-1, D-5, D-6, D-8 to D-12);
- decided D-17 and D-18, confirmed source reconciliation, and named owners for this early version;
- added multi-language support (D-19, §5.9, Appendix A.6). This is new material that no one has reviewed.

All decisions are for this early version and may change if your review challenges them. Please do challenge any of them. The main changes:

| ID | Decision |
| --- | --- |
| D-8 | Agents publish without confirmation only from their own private scope or scopes they manage, and only items whose ancestors there they own. Anything derived from a human's records needs that human's confirmation of the exact publication. |
| D-9 | An overseer bounds only an agent's list and read reach. Agents never hold `m`. Agent private scopes cannot be widened. Oversight transfer needs a second administrator. |
| D-12 | A published copy outlives its original only for ancestors the publisher owns, and only when a human published it. Its retention is the stricter of the target scope's and the category's. |
| D-13 | Access records are kept for at least one year. Reductions apply only to records created later, and there is no shortening path. |
| D-15 (new) | The Slice 1a overview is built from author-entered coordination records with a deterministic same-key conflict rule. |
| D-16 (new) | Slice 1a is split into 1a-core (single-user) and 1a-team. |
| D-17 (new) | In Slice 1a-team, the overseer confirms every agent publication and shared coordination record. This is lifted at Slice 1b, where runtime lineage enforces D-8. |
| D-18 (new) | The default maintenance budget applies. The narrated fraction is measured in the pilot; the rest of the memory shows exact projections only and is labeled projection-only. |
| D-19 (new) | Multi-language support is in scope. Concepts are language-neutral, with labels per language. Cross-language equivalence is curated, partial overlaps stay as separate concepts linked by `close_match`, and the original words are always cited. Translations are labeled synthesis, never evidence and never action grounding. Pilot languages are named at Gate 0. |

## 3. Questions

**Answer each with a concrete trajectory that breaks the guarantee, or with the reason none exists.**

1. **Publication (§10.6.2, §7.2, D-8).** Can any principal still declassify another principal's records? Check:
   - derivation;
   - coordination records;
   - confirmation for one target being reused for another;
   - scope managers, overseers and administrators;
   - departed users.
2. **Oversight (§7.3.1, §7.3.4, §7.3.8, §10.6.5).** Are the reach bound, the oversight entitlement and the fixed agent scope consistent with AC3, AC7 and T44? Can an elevated administrator or a group grant get around them?
3. **Ancestry retention (§5.5, §11.2, H1).** Does keeping the ancestry of purged nodes while descendants survive close CR01's lineage and erasure paths without regressing F09's "long retention never means forever"?
4. **Overview economics (§10.5.3, §10.5.4, §14.2).** Under rolling 180-day retention:
   - Does the deadline-filtered view keep near-expiry material out of every narrative input?
   - Does budget-bounded coverage make OV4 true?
   - Is the coverage honestly reported?
5. **Coordination records (§5.4, §6.9, §4.3).** Are they coherent with §6.1 commitments, checkpoints and claims? Is the 1a overview useful and non-misleading without statements?
6. **Assessment and screening (§9.3, §9.7).** Do ancestry-based enforcement at `submit_assessment` and approval-record-only exceptions close CR04 and CR07 without blocking a §1.2 journey?
7. **Delivery (§16, §15).** Are the 1a-core and 1a-team gates thin, testable and correctly mapped to invariants and tests? Is D-17 an adequate interim control until runtime lineage exists in Slice 1b?
8. **Multi-language support (§5.9, D-19).** Can a cross-language mapping, a translation or a look-alike label in another script change a slot's value, suppress or raise a flag, ground an action, or leak restricted content through a translation service? Is curated equivalence plus `close_match` enough where languages divide meaning differently? Are per-language analyzers and degraded-coverage reporting honest for languages outside the pilot set?
9. **Regressions.** Does anything weaken CR01–CR10, F01–F18 or A1–A7? Is Appendix A.5 accurate against the diff?

## 4. Expected Output

Use the same form as your review of candidate 2:

1. **Disposition:** PASS or NO-PASS for Gate 0 entry, with any Serious Challenge first.
2. **Closure tables:** one for CR01–CR10 and one for M-01–M-26.
3. **New findings,** most severe first. For each, give:
   - its section and invariant;
   - a counterexample;
   - its severity;
   - a proposed alternative;
   - whether it is a D3 defect or a D4 choice.
4. **Regression check:** F01–F18.
5. **Decisions:** agreement or disagreement with D-1 to D-19.
6. **Evidence ledger:** what you read, what you did not, and your limits as a reviewer.

Do not edit the candidate in place. If you produce a candidate 5, deliver it as a new document with its SHA-256 and a change map.
