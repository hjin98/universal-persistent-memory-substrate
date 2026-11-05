# UPMS Review Request (D1 Formulation 1.12, Candidate 6.12)

5 November 2026 · prepared by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle · run with the Codex CLI (OpenAI family)

**Please independently review the D1 formulation candidate 1.12, and the core of UPMS architecture manual candidate 6.12 with its anonymous-review annex 6.6. Decide PASS or NO-PASS for Gate 0 entry.** The reviewer must be **outside the Claude family**. Every text here was written by Claude. These revisions repair the Codex cross-check of 6.11 (NO-PASS: SC-CC611-01 to SC-CC611-03) and the Gemini review's R611-01, and apply owner decisions D-97 to D-99, which the owner made on 5 November 2026 on the author's recommendations. If you are Codex, say that you are the same reviewer and family as the 6.4 to 6.8 reviews and the 6.11 cross-check, so this review is not blind. Nobody has reviewed these revisions.

## 1. Review package

**Under review** (about 56,627 words):

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_12.md` | `60c6630f198cbc94e2a1fafe9b7ed1262ba2cea5d1304de1128e2dce28c1799c` | Proposed D1 parent |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_12.md` | `2ffe7c29d1b746c31893020a8f0d6493b6ed34ca48747fe0e38648fbfca27ef0` | Proposed D3 core: Gate 0 to Slice 2, every cross-cutting contract, and the mathematics hooks |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_6_Annex_Anonymous_Review.md` | `df0dd59de9ebce447c77caf0493f5ed29b03c87ca70683e2f38dd05410d791a4` | §7.8, §11.5 and their tests; holds the single sealing guarantee. Changed from annex 6.5 in one sentence of §7.8 and in T99 (D-98) |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_11_Codex_Cross_Check.md` | `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3` | The cross-check these revisions answer (Codex); its §4 ledgers give the status of earlier findings |
| `workplans/active/UPMS_Candidate_6_11_Independent_Review.md` | `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4` | Gemini review of 6.11: PASS conditional on D-97, overturned by the cross-check; R611-01 |
| `workplans/active/UPMS_Owner_Decisions_6_11_Review_2026-11-05.md` | `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295` | Owner decisions D-97 to D-99 |
| `workplans/active/UPMS_Proposed_Decisions_6_9_Review_2026-11-05.md` | `4d5b32f04d94950b7cd0536f1874d0873c62623d41e8a201dc559f37159a56b6` | The author's proposal of D-97, decided in amended form |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_12_Change_History.md` | `5918b18d86a2b61d9e1605315d2755df68d1e11beb0075d9c4a4891432470bb2` | A.22: repairs C612-1 to C612-5, including annex 6.6. Read as claims to test |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_12_Change_History.md` | `d23b9f33cbaf57b714bdaf80132cf1e68ed977ae957bea03ccc3daabd9d70969` | D1 map N, 1.11 → 1.12. Read as claims to test |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_11.md` | `43a234db345dba99d72c58012b0e485864aa5788817120ab4228f03744feedc7` | Predecessor, for diffing only |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_11.md` | `32bb7a7a6b3d0ea93cc0210a0aedbf9725531c3f0b35e7929bc9d17089c2830e` | Predecessor, for diffing only |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_5_Annex_Anonymous_Review.md` | `b2567c2fa8580d2873f6b18c039e80ea258c22c503eaa2b5531673aa2a363f55` | Predecessor annex, for diffing only |
| `workplans/active/UPMS_Owner_Decisions_6_8_Review_2026-11-05.md` | `5e9b40d43746059cbd4f23ff671bab735af7eccec5b940d3a36890f24cec33e9` | Owner decisions D-92, D-94 to D-96 |
| `workplans/active/UPMS_Candidate_6_8_Independent_Review.md` | `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad` | Codex review of 6.8 and D1 1.8 |
| `workplans/active/UPMS_Owner_Decisions_6_5_Review_2026-11-05.md` | `8cc6ffc8e9bf89119a92b0500ac4be3fee9775e0d818821bfb30985ee0aa59fa` | Owner decisions D-86 to D-89 |
| `workplans/active/UPMS_Owner_Decisions_6_4_Review_2026-11-04.md` | `20144a3a92753313d1163378c3bdf338509a0910962bdb44fd38f458104c9671` | Owner decisions D-79 to D-85 |
| `workplans/active/UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Owner decisions D-71 to D-78 |
| `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Owner decisions D-63 to D-70 |
| `workplans/active/UPMS_Owner_Decisions_Math_2026-11-03.md` | `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | Owner decisions D-57 to D-62 |
| `workplans/active/UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Owner decisions D-37 to D-46 |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex review of the proposal |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction and owner decisions D-20 to D-36 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base (D-23), for context only |

Older predecessors and reviews are listed with their hashes in change histories A.17 to A.22 and D1 maps I to N. **Not under review now** (D-56): `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` (`e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51`), before Gate 3; `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` (`f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7`), before Gate 4; `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md` (`71083419f4b9d4091153d7fd86ec32046081eca1f295d9f31e0b867015f51a58`), separately; `UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md` (`d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e`), separately, with the mathematics annex.

Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **Each trajectory of the 6.11 cross-check against the repairs** (A.22, C612-1 to C612-5): SC-CC611-01 against D1 P2 and F-8, core §4.4 and annex §7.8 and T99; SC-CC611-02 against D1 Definition 5.3 and T136; SC-CC611-03 against D1 §6.1 (grounded basis, terminal basis, rootless basis, dependence and circularity), F-25, core §5.3 and §9.9, and T135; R611-01 against T83.
2. **The new terminal-warrant semantics (D-99):** whether "depends on" is well defined and computable, whether it classifies a direct-event premise, a rootless premise, a genuine cycle, a cycle with an independent root and a cycle that does not pass through the conclusion as D1 stress cases 33 to 36 say, and whether a terminal basis lets an unwarranted assertion count as support.
3. **The anonymous-objection rule (D-98):** whether any rule still says route status changes only through attributed judgments, and whether an anonymous objection can now veto or block anything.
4. **Anything else, anywhere in the package, that is materially false, contradictory, ambiguous or unrealizable.**
5. **The owner decisions D-37 to D-99:** raise a Serious Challenge with a trajectory where one causes a material failure.
6. **Simplicity:** the Gate 0 package is about 56,627 words. Name what can go.

Quote the texts exactly and cite sections that exist; say so when you paraphrase.

## 3. Requested output

Write a review record in the form of `UPMS_Candidate_6_11_Codex_Cross_Check.md`. Begin with your model family and model name, the date, the SHA-256 of each file you reviewed, and the parts you did not read. List any Serious Challenge first. Then give findings by earliest owning domain, each with a counterexample trajectory, a consequence and a bounded repair. Include PASS or NO-PASS for the D1 text, and for the core with its annex, the status of each finding of the 6.11 cross-check and of R611-01; and the owner decisions you think the texts still need. It is saved as `workplans/active/UPMS_Candidate_6_12_Independent_Review.md`.

## 4. How it is run

The author runs the reviewer through the Codex CLI in the owner's terminal, under the owner's delegation, in a read-only sandbox with no file writes; the reviewer's final message is saved verbatim as the review record.
