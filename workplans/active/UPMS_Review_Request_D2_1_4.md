# UPMS Review Request (D2 Retrieval Method 1.4)

5 November 2026 · prepared by Claude (AI, Opus 5.5) under the owner's delegation of the revise-and-review cycle · run with the Codex CLI (OpenAI family)

**Please review D2 1.4, a revision of the accepted-current D2 1.3, and decide PASS or NO-PASS for ratification as accepted-current D2.** The reviewer must be **outside the Claude family**. If you are Codex, say that you are the same reviewer and family as the 6.18 to 6.21 reviews, the 6.4 to 6.8 and 6.12 to 6.17 reviews, the 6.11 cross-check and the three design-note critiques, so this review is not blind.

## 1. Review package

**Under review:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_4.md` | `60374b78500503e7d108b449d798281d8a4a52e941c0fe86e5c060a854ddd1b9` | D2, revision of the ratified 1.3: planted-fact references (§9.1), calibration before qualification and acceptance on confidence bounds (§§10.3, 10.6), reopening (§14) |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md` | `132a795d1c0c710b3514576c85bc9ec4dbdb52ccb901f22c09634e731c156ea9` | Every edit from 1.3 verbatim. Read as claims to test; applied in order to 1.3 it should give 1.4 byte for byte |
| `workplans/active/UPMS_Owner_Decisions_Pilot_Languages_Evaluation_2026-11-05.md` | `2f7d25814aaa045e95902a13d6e5feaaf8be418ac27b293e4627e90f43d77e58` | D-121 (pilot languages English and Chinese) and D-122 (the evaluation plan this revision realizes); its §3 corrects two statements the owner was shown |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_3.md` | `84e61686c74e2a07a8eace77b12afa6bb4789e334634928d68c64508b15c84f6` | Ratified predecessor |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20.md` | `d8bc3558d64e627b739189a6a92d1e42c4c2df2d47dd9bc42b927ad9dec72eab` | Ratified D1 parent |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_21.md` | `e1f28af693ae8805acf2ed2d8cccbca5a1f90038440b7de9a3d3e93d53464f8c` | Ratified core (§§14.2, 15.2, 16 bear on this revision) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_21_Annex_Retrieval_Scale.md` | `1e12a4313742426b12bda5b1df5f94c86a39d41318e56f42b94c4661da2f284f` | Ratified retrieval-and-scale annex |
| `workplans/active/UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md` | `ff6a4493b4cf44f55d8488bb22ae9ea9bbe096ea66db0afa08e60847c0c29866` | Ratification record |
| `workplans/active/UPMS_Candidate_6_21_Independent_Review.md` | `8f2b567b177e38da3938ac95d6dc443293d606de60012616b595b63d7f888c23` | Your review of 6.21, including F621-01 |

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **The statistics of D2 §10.6.** Whether the counting unit, the any/all episode indicators and the one-sided exact bounds are valid and conservative as claimed, including for `a_u` (whose denominator excludes unknown `k*`), for `u + u_partial`, and for rates computed over different subsets; whether the table and the worked example are numerically right; and whether multiple classes and multiple rates per class need a multiplicity correction the text omits.
2. **Selection and leakage.** Whether calibration, owner setting, qualification and fresh held-out sets (§10.6 phases 1 and 2) leave a path by which held-out data influences a frozen value or variant, and whether planted-fact episodes (§9.1) can leak answers into retrieval or adjudication.
3. **Consistency with the ratified parents.** Whether §10.6 contradicts core 6.21 §15.2 (200 synthetic episodes, 100 held out) or §16 ("evaluation frozen before measurement"), D1 1.20 §16, or the reading D-122 records; whether the change is within D2's ownership or needs a D1 or D3 revision; and whether D-121 needs any text change.
4. **That nothing changed outside the change map**, and new defects.

Quote the texts exactly and cite sections that exist.

## 3. Requested output

A review record in the form of `UPMS_Candidate_6_21_Independent_Review.md`, beginning with your model family and model name, the date, the SHA-256 of each file you reviewed, and the parts you did not read. Give any Serious Challenge, then findings by earliest owning domain, each with a counterexample trajectory, a consequence and a bounded repair. Give **PASS or NO-PASS for ratification** of D2 1.4, and list any questions for the owner. It is saved as `workplans/active/UPMS_D2_1_4_Independent_Review.md`.

## 4. How it is run

The author runs the reviewer through the Codex CLI in the owner's terminal, under the owner's delegation, in a read-only sandbox with no file writes; the reviewer's final message is saved verbatim as the review record.
