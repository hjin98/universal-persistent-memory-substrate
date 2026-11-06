# UPMS Review Request (Candidate 6.19 with the Retrieval-and-Scale Annex, D1 Formulation 1.18, D2 Retrieval Method 1.1)

5 November 2026 · prepared by Claude (AI, Opus 5.5) under the owner's delegation of the revise-and-review cycle · run with the Codex CLI (OpenAI family)

**Please review the revision that answers your review of 6.18, and decide PASS or NO-PASS for Gate 0 entry for each of D1 1.18, D2 1.1, and core 6.19 with its annexes.** The reviewer must be **outside the Claude family**. If you are Codex, say that you are the same reviewer and family as the 6.18 review, the 6.4 to 6.8 and 6.12 to 6.17 reviews, the 6.11 cross-check and the three design-note critiques, so this review is not blind.

## 1. Review package

**Under review:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md` | `efb04646f0be364ea955f269dffa38251a1a39eaae7017188e6f050414cc4fde` | D1, revision of 1.17 |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_1.md` | `988733885edbe001ba6547cb9f36608a6e928ce9d16c935ecec2b13fb5fb3ebf` | D2, revision of 1.0 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_19.md` | `c0fc446c4493aab2c2dd6b6f4611e3cd34b991cbcfa36235891ca73921fef3c3` | Core, revision of 6.18 (version references only) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md` | `a737a6a64d15d23f310bbd4e41137eacebff03a86c4c8de63ef90f1b3fb9c0bb` | Retrieval-and-scale annex, revision of 6.18's |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Unchanged |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_19_Change_History.md` | `dfbc739bc78192511bec810ff732d9b4c0f70e3101cb40bdd0e51ed4a56cd90d` | A.29: the disposition table for every finding of your 6.18 review, and every core and annex edit verbatim. Read as claims to test |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18_Change_History.md` | `2575c36361a508bf49c7d123907e20231f650540cbd2a1b7ad8c7fd349ef3ec8` | Map T, D1 edits verbatim |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md` | `a4e4482b0b45c75b0f0adf1408183e4760895d007e0647bf051346f0af03922f` | D2 edits verbatim |
| `workplans/active/UPMS_Candidate_6_18_Independent_Review.md` | `9fbe6ed485cf84cae6afa1f4795ddb488660d2bb04b28e636a61c82cd5679108` | Your review of 6.18 (NO-PASS) |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | `28bdee3084167701926da92944804cd06390f926cc3b4fe6d9019b57689d2bc8` | Predecessor, for diffing |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_0.md` | `fba8768d1c0ff6ac7725559054acb455fb2a0ae893e82c7c9c0275b31c736f6f` | Predecessor, for diffing |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18.md` | `9a42794b35059165ac7e3d83d5a842b4aa33c54bf06f60b003a3aa38b8fd8373` | Predecessor, for diffing |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` | `abfd09691d82cfb635986eae790c57826b581e257dce2cd26ac3e3311ad2de9e` | Predecessor, for diffing |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Ratified D1 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` | Ratified core |
| `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md` | `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | The direction |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` | D-101 to D-116 |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` | `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | D-117 to D-120 |

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **Closure:** for every Serious Challenge and finding of your 6.18 review, whether the operative text now resolves it, not merely A.29's claim. Say which remain open, partly closed or newly introduced.
2. **The author's answers to your owner questions** (A.29): whether restoring the resolution-basis rule, refusing deliberate agent writes without declarations while bounding missing declarations on capture, and capping class budgets by the pilot limits are within D-107 and D-120, or need the owner.
3. **That nothing else changed:** diff each text against its predecessor; any change outside the change maps is a defect.
4. **New defects** the repairs introduce, including contradictions with the ratified D1 1.16 and core 6.17.
5. **Simplicity:** whether the repairs grew where they did not need to.

Quote the texts exactly and cite sections that exist.

## 3. Requested output

A review record in the form of `UPMS_Candidate_6_18_Independent_Review.md`, beginning with your model family and model name, the date, the SHA-256 of each file you reviewed, and the parts you did not read. Give a closure table for your 6.18 review, then any Serious Challenge and new findings by earliest owning domain, each with a counterexample trajectory, a consequence and a bounded repair. Give **PASS or NO-PASS for Gate 0 entry** separately for D1 1.18, D2 1.1, and core 6.19 with its annexes, and list any questions for the owner. It is saved as `workplans/active/UPMS_Candidate_6_19_Independent_Review.md`.

## 4. How it is run

The author runs the reviewer through the Codex CLI in the owner's terminal, under the owner's delegation, in a read-only sandbox with no file writes; the reviewer's final message is saved verbatim as the review record.
