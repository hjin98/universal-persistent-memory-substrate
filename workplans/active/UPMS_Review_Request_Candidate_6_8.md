# UPMS Review Request (D1 Formulation 1.8, Candidate 6.8)

5 November 2026 · prepared by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle · run with the Codex CLI

**Please independently review the D1 formulation candidate 1.8, and the core of UPMS architecture manual candidate 6.8 with its anonymous-review annex 6.5. Decide PASS or NO-PASS for Gate 0 entry.** The reviewer must be **outside the Claude family**. Every text here was written by Claude. These revisions repair the fourth review from outside the Claude family: Codex (OpenAI GPT family) found D1 1.7 and core 6.7 NO-PASS, with Serious Challenges SC67-01 to SC67-03 and finding R67-01. Nobody has reviewed the repairs. **Several apply decisions D-90 to D-93 that the author proposed and the owner has not made;** the texts mark them pending. Review them as proposals: say whether each is sound, and what fails if the owner rejects it. If Codex reviews again, say that it is the same reviewer, and the same family, as the 6.4 to 6.7 reviews.

## 1. Review package

**Under review** (about 54,460 words):

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_8.md` | `cbbf2c07b0bfd042952c00a392ad5693f329f39dbd3808445b88571dc30ae1da` | Proposed D1 parent |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_8.md` | `8dad8d5f50e9139e536cb766dab8c9806af2ce884f1826d2dba1ac6c77b73f1f` | Proposed D3 core: Gate 0 to Slice 2, every cross-cutting contract, and the mathematics hooks |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_5_Annex_Anonymous_Review.md` | `b2567c2fa8580d2873f6b18c039e80ea258c22c503eaa2b5531673aa2a363f55` | §7.8, §11.5 and their tests; holds the single sealing guarantee. Unchanged since the 6.5 review |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_7_Independent_Review.md` | `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168` | The review these revisions answer; its §4 ledgers give the status of every earlier finding |
| `workplans/active/UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md` | `3a0741c43d9d71802f99c5cce148bba8ab0c19c33878fc0ce1c87c3640c99d8a` | Proposals D-90 and D-92 amended and D-93, **pending the owner** |
| `workplans/active/UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md` | `3a9fd1d4a46f70e115664e8233c6aad4fc07bde86a610a24442bd30ff1ed4236` | Proposals D-90 to D-92 as first made, **pending the owner** |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_8_Change_History.md` | `76fce2b7e520d234014a9fbc13ef24e1f1b2d10643702c347b401e9c50d34cd6` | A.18: repairs C68-1 to C68-6, what was not taken, and the moved text. Read as claims to test |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_8_Change_History.md` | `c4c986d630c6b78aa21c32aabcfaf922297af90cb3573609c36ab35ef8dde7d8` | D1 map J, 1.7 → 1.8. Read as claims to test |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_7.md` | `1108d7c496d447ed3886b339dce4f183ddc1ad9c99c2b7e805786c7ac9ada3c0` | Predecessor, for diffing only |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_7.md` | `34bc64c07341ef694875379a110880f614931ba94b51a8f03be8944c065b2052` | Predecessor, for diffing only |
| `workplans/active/UPMS_Candidate_6_6_Independent_Review.md` | `ac282071dbe79aa61262b70237a5f6e981ddb156a44e652dfb422eb1f0cc39f4` | Codex review of 6.6 and D1 1.6 |
| `workplans/active/UPMS_Owner_Decisions_6_5_Review_2026-11-05.md` | `8cc6ffc8e9bf89119a92b0500ac4be3fee9775e0d818821bfb30985ee0aa59fa` | Owner decisions D-86 to D-89 |
| `workplans/active/UPMS_Owner_Decisions_6_4_Review_2026-11-04.md` | `20144a3a92753313d1163378c3bdf338509a0910962bdb44fd38f458104c9671` | Owner decisions D-79 to D-85 |
| `workplans/active/UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Owner decisions D-71 to D-78 |
| `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Owner decisions D-63 to D-70 |
| `workplans/active/UPMS_Owner_Decisions_Math_2026-11-03.md` | `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | Owner decisions D-57 to D-62 |
| `workplans/active/UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Owner decisions D-37 to D-46 |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex review of the proposal |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction and owner decisions D-20 to D-36 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base (D-23), for context only |

Older predecessors and reviews are listed with their hashes in change histories A.17 and A.18 and D1 maps I and J. **Not under review now** (D-56), all unchanged since the 6.4 review: `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` (`e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51`), before Gate 3; `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` (`f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7`), before Gate 4; `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md` (`71083419f4b9d4091153d7fd86ec32046081eca1f295d9f31e0b867015f51a58`), separately; `UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md` (`d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e`), separately, with the mathematics annex.

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **Each trajectory of the 6.7 review against the repairs** (A.18, C68-1 to C68-6): SC67-01 against transitive possible homes and the induction in core §5.11; SC67-02 against D1 Definition 5.3; SC67-03 against per-binding resolution (D1 Definition 2.5, F-3, F-3a, F-7; core §5.11, §6.10); R67-01 against D1 §8.2 and core §5.11.
2. **The §5.11 induction:** is it actually valid for every admitted transition (record, carry, rebind, resolve, withdraw, dispute, share, retire a registration, narrow a scope), including objections with several bindings and resolutions that name several bindings? Find a transition that breaks it.
3. **Per-binding resolution (D-93):** is "unresolved in a projection" coherent for standing (F-28), mandatory lists and the late-objection delta; can it make an objection look live forever on old decisions in a way that defeats the purpose of resolving it?
4. **Definition 5.3:** are the confirming kinds right, and does the independent-test label leak anything misleading?
5. **Transitive registration:** does it widen where objections may be homed in a way that weakens access control or the audience guarantees of D-80 and D-88?
6. **Each open or partial row of the 6.7 review's §4 ledgers** against the operative text, not against A.18.
7. **The owner decisions D-37 to D-89 and the proposals D-90 to D-93:** raise a Serious Challenge with a trajectory where one causes a material failure.
8. **Simplicity:** the Gate 0 package is about 54,460 words. Name what can go.

## 3. Requested output

Write a review record in the form of `UPMS_Candidate_6_7_Independent_Review.md`. List any Serious Challenge first. Then give findings by earliest owning domain, each with a counterexample trajectory, a consequence and a bounded repair. Include PASS or NO-PASS for the D1 text, and for the core with its annex, and say whether either verdict depends on a pending proposal; the status of each finding of the 6.7 review; and the owner decisions you think the texts still need. State your model family and the parts you did not read. It is saved as `workplans/active/UPMS_Candidate_6_8_Independent_Review.md`.

## 4. How it is run

The author runs the reviewer through the Codex CLI in the owner's terminal, under the owner's delegation, with a read-only sandbox; the reviewer's final message is saved verbatim as the review record.
