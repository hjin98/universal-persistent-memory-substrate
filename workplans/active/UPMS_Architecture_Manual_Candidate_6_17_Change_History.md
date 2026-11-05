# UPMS Architecture Manual, Candidate 6.17: Change History (A.27)

5 November 2026 · drafted by Claude (AI, Opus 5.5) at the product owner's request "Simplify first" (5 November 2026)

**Status:** change history of review candidate 6.17; not architecture, decides nothing. A.1 to A.26 are in the earlier change-history files, all unchanged and indexed below. This file adds A.27.

### A.27 Candidate 6.16 → candidate 6.17

**Editorial only.** Candidate 6.16 (`UPMS_Architecture_Manual_Review_Candidate_6_16.md`, SHA-256 `e9f578b32e0a6d8a9363641a4af8bfd1942ed10c86884a291e91d1295d4c8af9`) and every annex are unchanged; the D1 parent moves to 1.16, itself an editorial revision of 1.15 (its map R). The Codex review of 6.16 (`UPMS_Candidate_6_16_Independent_Review.md`, SHA-256 `727afb383999fdd89c1f4103041be2a4bb86104d62855690059d34d9aa17afa4`, §6) recommended replacing the long predecessor sequences and reviewer ancestry in §1, Appendix A and Appendix B with a route to the change history, and §18.1's enumeration of historical finding identifiers with a reference to the review ledgers. No contract, invariant, test, decision row or open item changed.

| Where | Change |
| --- | --- |
| Title, §1 | Revision 6.17; the list of change-history files and the revision paragraph moved below |
| §1.1 | Rows for D1 1.16, the 6.16 review and predecessor 6.16 replace those for D1 1.15, the 6.15 review and predecessor 6.15 |
| §1.4 | Parent named as 1.16 |
| §18.1 | The finding-identifier enumeration and the §18.3 check row shortened |
| §18.3, Appendix A, Appendix B | Repair, change-map and reviewer chronology moved below |

**Word count:** the core body goes from 41,347 to 40,995 words; D1 1.16 is 13,791 words; the anonymous-review annex 6.7 is unchanged at 3,293. The Gate 0 package is 58,079 words.

#### A.27.1 Index of change histories

| File | SHA-256 |
| --- | --- |
| `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md` | `c2a7ded8dd9198a92989c81ca8216718b7a3af8ff2875bf48cce60c40775e571` |
| `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md` | `d7501e2ea209e8710ada727c0ea4c2f3e3d698b138708c52aff2c6116e9c40b3` |
| `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md` | `0fc9822778e3851fb7fec9593e1bfe150064e09a84982a02fe51aa4310ecd733` |
| `UPMS_Architecture_Manual_Candidate_6_6_Change_History.md` | `3070c0844718d8503ec9f9cda878dd02b320c774569c2a79f153ead23cbf306f` |
| `UPMS_Architecture_Manual_Candidate_6_7_Change_History.md` | `4ccf6c8861780713737fee12492e62cc7ececea3d608ccdb4c0dc4233cee35ab` |
| `UPMS_Architecture_Manual_Candidate_6_8_Change_History.md` | `76fce2b7e520d234014a9fbc13ef24e1f1b2d10643702c347b401e9c50d34cd6` |
| `UPMS_Architecture_Manual_Candidate_6_9_Change_History.md` | `c944d64829642cb57e6fd1fd1859f44e272410f572322adba671c9dbf002b543` |
| `UPMS_Architecture_Manual_Candidate_6_10_Change_History.md` | `8bbd17d10fab3f94ffa532d5c0ae195f7e2ea5785d9ae4f6b9ade5e7239f7055` |
| `UPMS_Architecture_Manual_Candidate_6_11_Change_History.md` | `2b618ba48a4d901e535431e9309d031d1fb2c9eaee3ab80bd71ceae51d974ded` |
| `UPMS_Architecture_Manual_Candidate_6_12_Change_History.md` | `5918b18d86a2b61d9e1605315d2755df68d1e11beb0075d9c4a4891432470bb2` |
| `UPMS_Architecture_Manual_Candidate_6_13_Change_History.md` | `5c13716b9929a0784b6640d469bbdf80348ee101b1dd1129df84cd7da535a080` |
| `UPMS_Architecture_Manual_Candidate_6_14_Change_History.md` | `1667b4096541396110e4d55b9f853aa557b2cdc512d6bbc1a4043b72b6a3f97f` |
| `UPMS_Architecture_Manual_Candidate_6_15_Change_History.md` | `c56d0c7c78cfc0fb18f52d5a24f1bf0b2c87242d2f4406eec1c55196f59fc85b` |
| `UPMS_Architecture_Manual_Candidate_6_16_Change_History.md` | `9a4b7a68930b4210a076d6af83fd6a47f0bc2f412477b5310f4a0c3b8cdb5358` |
| `UPMS_Architecture_Manual_Candidate_6_17_Change_History.md` | this file |

A.1 to A.13 are in the first file, A.14 to A.26 one per file in the rest.

#### A.27.2 Index of independent reviews of candidates 6.4 to 6.16

| File | Family | SHA-256 |
| --- | --- | --- |
| `UPMS_Candidate_6_4_Independent_Review.md` | Codex | `82941db24d9213921e03b6732d4101d4a58984891bd109d6da53fc4de645d5b6` |
| `UPMS_Candidate_6_5_Independent_Review.md` | Codex | `92ddcda5861711af8cdcdbd43a1b938767ab871cadd7ab6dbfbc8a8c8f2eb515` |
| `UPMS_Candidate_6_6_Independent_Review.md` | Codex | `ac282071dbe79aa61262b70237a5f6e981ddb156a44e652dfb422eb1f0cc39f4` |
| `UPMS_Candidate_6_7_Independent_Review.md` | Codex | `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168` |
| `UPMS_Candidate_6_8_Independent_Review.md` | Codex | `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad` |
| `UPMS_Candidate_6_9_Independent_Review.md` | Gemini | `6c46d9aa8b6179ad8b91df4cfbcfa51cf3ffbe2aca257ed555c902659bfd2b12` |
| `UPMS_Candidate_6_10_Independent_Review.md` | Gemini | `2645faef1aed615b859decb02074724c0175ebb4bed9fb689eb4141e3b8258fb` |
| `UPMS_Candidate_6_11_Independent_Review.md` | Gemini | `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4` |
| `UPMS_Candidate_6_11_Codex_Cross_Check.md` | Codex | `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3` |
| `UPMS_Candidate_6_12_Independent_Review.md` | Codex | `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26` |
| `UPMS_Candidate_6_13_Independent_Review.md` | Codex | `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b` |
| `UPMS_Candidate_6_14_Independent_Review.md` | Codex | `ecb8d25b7f1254b168ee1563eb9d4930afe2a70e015d9aee438d7d1b8ec7a7a2` |
| `UPMS_Candidate_6_15_Independent_Review.md` | Codex | `195d27b21f2917e010a732bb15740b43ea617d7a3349421ba5b159f38de7f251` |
| `UPMS_Candidate_6_16_Independent_Review.md` | Codex | `727afb383999fdd89c1f4103041be2a4bb86104d62855690059d34d9aa17afa4` |

#### A.27.3 Text moved out of candidate 6.16 (D-85; moved verbatim)

#### §1, scope paragraph and revision paragraph

This candidate applies the direction of the theory–evidence proposal v0.1 (owner decisions D-20 to D-36) to candidate 5, which stays frozen as an input (D-23), and concretizes the D1 formulation, candidate 1.15, which this revision leaves unchanged and which names candidate 6.15 as its concretization; that name means this candidate. Front-end matters, namely discussion, facilitation, the review process and inquiry policy, stay with SCIRE; this manual specifies only the back-end contract for them (§4.4). Proposal §15 item 6, judgment on judgment, is deferred (§9.10). How earlier revisions and reviews shaped this text is change history, not architecture (owner decision D-85): A.1 to A.13 in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md`, A.14 in `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md`, A.15 in `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md`, A.16 in `UPMS_Architecture_Manual_Candidate_6_6_Change_History.md` A.17 in `UPMS_Architecture_Manual_Candidate_6_7_Change_History.md` A.18 in `UPMS_Architecture_Manual_Candidate_6_8_Change_History.md` A.19 in `UPMS_Architecture_Manual_Candidate_6_9_Change_History.md` A.20 in `UPMS_Architecture_Manual_Candidate_6_10_Change_History.md`, A.21 in `UPMS_Architecture_Manual_Candidate_6_11_Change_History.md`, A.22 in `UPMS_Architecture_Manual_Candidate_6_12_Change_History.md`, A.23 in `UPMS_Architecture_Manual_Candidate_6_13_Change_History.md`, A.24 in `UPMS_Architecture_Manual_Candidate_6_14_Change_History.md`, A.25 in `UPMS_Architecture_Manual_Candidate_6_15_Change_History.md` and A.26 in `UPMS_Architecture_Manual_Candidate_6_16_Change_History.md`, cited below as "change history A.n".

**Revision 6.16 and its files.** Revision 6.16 answers the Codex review of candidate 6.15 (PASS for D1 1.15; NO-PASS for the core, Serious Challenge SC615-01 and finding R615-01), which concern only this core's acceptance scenarios (repairs C616-1 and C616-2 in change history A.26). The review package (D-56) is:

#### §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Theory–Evidence Formulation, D1 candidate 1.15 | `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_15.md`, SHA-256 `8d934751f65cd6506d343b3ebde23a31c60ff5f57582a110023d80999d8d5b2c` | Proposed D1 parent; its F-rules are cited as "D1 F-n". Technical PASS in the 6.15 review; not accepted. Unchanged by this revision. Its predecessors are listed in its maps I to Q |
| Independent review of candidate 6.15 and D1 1.15 (Codex, OpenAI family) | `UPMS_Candidate_6_15_Independent_Review.md`, SHA-256 `195d27b21f2917e010a732bb15740b43ea617d7a3349421ba5b159f38de7f251` | PASS for D1 1.15; NO-PASS for core 6.15 with anonymous-review annex 6.7; SC615-01 and R615-01, repaired in this revision (change history A.26). The same reviewer and family as the 6.4 to 6.8 and 6.12 to 6.14 reviews and the 6.11 cross-check |
| UPMS Architecture Manual, review candidate 6.15 | `UPMS_Architecture_Manual_Review_Candidate_6_15.md`, SHA-256 `6ccb71fa7d8ca3ed43db913216d94f66d9e480d7b6f2531f3500e7af3379e457` | Immediate predecessor, unchanged; changes in change history A.26. Earlier predecessors and reviews are listed with their hashes in A.17 to A.26 |

#### §18.1 rows

| Codex review findings | Each of SC-TE01 to SC-TE05 and TE-R01 to TE-R20, of the 6.4 review's SC64-01 to SC64-03 and R64-01 to R64-06, of the 6.5 review's SC65-01, SC65-02 and R65-01 to R65-03, of the 6.6 review's SC66-01, SC66-02, R66-01 and R66-02, of the 6.7 review's SC67-01 to SC67-03 and R67-01, of the 6.8 review's SC68-01 to SC68-03 and R68-01, of the 6.9 review's SC69-01 to SC69-03 and R69-01 to R69-03, of the 6.10 review's SC610-01, SC610-02, R610-01 and R610-02, and of the 6.11 cross-check's SC-CC611-01 to SC-CC611-03 and the 6.11 review's R611-01, of the 6.12 review's SC612-01 to SC612-03 and R612-01, of the 6.13 review's SC613-01, R613-01 and R613-02, of the 6.14 review's SC614-01 and R614-01, and of the 6.15 review's SC615-01 and R615-01, checked against this body text; change history A.8 is the author's view only, and a finding closes only when the operative text resolves it (the review's revisit condition) | Reviewer outside the Claude family; the owner for the decisions in the review's §9 |
| Challenges in §18.3 | Independent check of each repair C616-1 and C616-2, and of the rows the 6.15 review left qualified (its §4) | Reviewer outside the Claude family |

#### §18.3

The repairs of this revision, C616-1 and C616-2, are mapped in change history A.26; C615-1 and C615-2 are in A.25, C614-1 to C614-3 in A.24, C613-1 to C613-4 in A.23, C612-1 to C612-5 in A.22, C611-1 to C611-4 in A.21, C610-1 to C610-6 in A.20, C69-1 to C69-6 in A.19, C68-1 to C68-6 in A.18, C67-1 to C67-6 in A.17, C66-1 to C66-9 in A.16 and C65-1 to C65-10 in A.15, which also holds the C63 and C64 tables of candidate 6.4 §18.3; those of candidates 6 to 6.2 are in A.12. Each repair is the author's and needs an independent check.

#### Appendix A

The change map of this candidate (candidate 5 → 6 → 6.1 → 6.2 → 6.3 → 6.4 → 6.5 → 6.6 → 6.7 → 6.8 → 6.9 → 6.10 → 6.11 → 6.12 → 6.13 → 6.14 → 6.15 → 6.16, the reconciliation of candidate 5 §§11–13 and 15, the re-review and Codex dispositions, and the edits inside copied text) is in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md`, with 6.3 → 6.4 in `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md` 6.4 → 6.5 in `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md` 6.5 → 6.6 in `UPMS_Architecture_Manual_Candidate_6_6_Change_History.md` 6.6 → 6.7 in `UPMS_Architecture_Manual_Candidate_6_7_Change_History.md` 6.7 → 6.8 in `UPMS_Architecture_Manual_Candidate_6_8_Change_History.md` 6.8 → 6.9 in `UPMS_Architecture_Manual_Candidate_6_9_Change_History.md` 6.9 → 6.10 in `UPMS_Architecture_Manual_Candidate_6_10_Change_History.md` 6.10 → 6.11 in `UPMS_Architecture_Manual_Candidate_6_11_Change_History.md` 6.11 → 6.12 in `UPMS_Architecture_Manual_Candidate_6_12_Change_History.md` 6.12 → 6.13 in `UPMS_Architecture_Manual_Candidate_6_13_Change_History.md` 6.13 → 6.14 in `UPMS_Architecture_Manual_Candidate_6_14_Change_History.md` 6.14 → 6.15 in `UPMS_Architecture_Manual_Candidate_6_15_Change_History.md` and 6.15 → 6.16 in `UPMS_Architecture_Manual_Candidate_6_16_Change_History.md`. It is change history, not architecture.

#### Appendix B, revisions bullet

- **Revisions 6.1 to 6.16:** each written by the same author in answer to a review or owner decisions (§1.1), so the repairs were fitted to existing text and need an independent check. The reviews of 6.4 to 6.8 were by Codex, the same reviewer and family, which read the author's change histories and earlier reviews and was not blind; the reviews of 6.9 to 6.11 were by a Gemini-family model (D-96), and Codex cross-checked 6.11 and reviewed 6.12 to 6.15. The revision-by-revision notes are in change history A.16 to A.26.
