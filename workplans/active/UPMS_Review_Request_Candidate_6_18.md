# UPMS Review Request (Candidate 6.18 with the Retrieval-and-Scale Annex, D1 Formulation 1.17, D2 Retrieval Method 1.0)

5 November 2026 · prepared by Claude (AI, Opus 5.5) at the product owner's request "Start drafting" and under the owner's delegation of the revise-and-review cycle · run with the Codex CLI (OpenAI family)

**Please independently review the three texts drafted from design note revision 3, and decide PASS or NO-PASS for Gate 0 entry for each:** D1 formulation candidate 1.17, the D2 retrieval method candidate 1.0, and core candidate 6.18 with its new retrieval-and-scale annex (and its unchanged annex 6.7). The reviewer must be **outside the Claude family**; every text was written by Claude. If you are Codex, say that you are the same reviewer and family as the 6.4 to 6.8 and 6.12 to 6.17 reviews, the 6.11 cross-check and the three critiques of the design note, so this review is not blind.

## 1. Review package

**Under review:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | `28bdee3084167701926da92944804cd06390f926cc3b4fe6d9019b57689d2bc8` | Proposed D1 successor of the ratified 1.16: new §16 (Definitions 16.1 to 16.11, F-43 to F-55), revised §9, §15 items 9 to 11 |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_0.md` | `fba8768d1c0ff6ac7725559054acb455fb2a0ae893e82c7c9c0275b31c736f6f` | New D2 text, opened for retrieval only |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18.md` | `9a42794b35059165ac7e3d83d5a842b4aa33c54bf06f60b003a3aa38b8fd8373` | Proposed D3 core successor of the ratified 6.17: 29 targeted edits |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` | `abfd09691d82cfb635986eae790c57826b581e257dce2cd26ac3e3311ad2de9e` | New D3 annex, sections R1 to R18 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Unchanged; part of the core package |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17_Change_History.md` | `43bc738dd2508fa1a7461406def62fe8c271d206014db9ad049ad1cfd1e508d4` | Map S: 1.16 → 1.17 with replaced text verbatim. Read as claims to test |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_18_Change_History.md` | `bbe26907c6d0871fd37727c58dfbbc40db8d7bee9828711d60edb4b15318bae4` | A.28: every core edit with replaced text verbatim, and the author's choices to test. Read as claims to test |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Ratified predecessor, for diffing |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` | Ratified predecessor, for diffing |
| `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md` | `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | The direction the texts must implement |
| `workplans/active/UPMS_Retrieval_Design_Note_R3_Codex_Critique.md` | `66a2ae248a4ce55196561180cbdfb504b8de83ecb55909df8f4feb5835d19da4` | Your verdict: sound to draft from |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` | Decisions D-101 to D-116 |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` | `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Decisions D-117 to D-120 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` | Unratified context the annex refers to |

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **Fidelity to the direction:** whether the three texts implement design note revision 3 and D-101 to D-120 without dropping, weakening or contradicting any of them, and without inventing meanings the note did not give. Pay particular attention to the repairs your critiques demanded (exact facts apart from assessments; the qualified discovery map; deletion units and keys; hidden-source counts; reference reuse after compaction).
2. **Domain placement:** whether each rule sits with its owner: meanings in D1 §16, guarantees, error and cost in D2, structures and records in the annex and core. Whether the opening of D2 (D1 §9, core §1.4) is argued and bounded correctly.
3. **The D2 method itself:** whether the pruning rule and Proposition 3.1 are correct, including negation, phrases, unprocessed structural atoms, deltas, merges, deletions and version changes; whether the cost model, budgets, schedule, measurement and evaluation designs are sound and do not reward abstention by default; whether any proposed number is presented as more than a proposal.
4. **Consistency with the ratified texts:** whether D1 1.17 keeps every rule of 1.16 and core 6.18 every rule of 6.17 except where map S and A.28 say; whether any new rule contradicts a kept one (for example §7.4 tag rules, §9.1 single committer, §9.2 no model on the capture path, §10.1 eligibility, §12.3 to §12.4 deletion, §14.2 profile).
5. **The author's choices** listed in A.28 (the annex form; accepting an agent write without declarations and flagging it; the initial defaults; numbering).
6. **Realizability and tests:** whether RT1 to RT12 and T141 to T162 discriminate the failures they target, and whether the slice placement in annex R17 is coherent with core §16.
7. **Anything else** materially false, contradictory, ambiguous or unrealizable, and what could be simpler.

Quote the texts exactly and cite sections that exist; say so when you paraphrase.

## 3. Requested output

A review record in the form of `UPMS_Candidate_6_17_Independent_Review.md`. Begin with your model family and model name, the date, the SHA-256 of each file you reviewed, and the parts you did not read. List any Serious Challenge first, then findings by earliest owning domain, each with a counterexample trajectory, a consequence and a bounded repair. Give **PASS or NO-PASS for Gate 0 entry** separately for D1 1.17, for D2 1.0, and for core 6.18 with its annexes, and list any questions for the owner. It is saved as `workplans/active/UPMS_Candidate_6_18_Independent_Review.md`.

## 4. How it is run

The author runs the reviewer through the Codex CLI in the owner's terminal, under the owner's delegation, in a read-only sandbox with no file writes; the reviewer's final message is saved verbatim as the review record.
