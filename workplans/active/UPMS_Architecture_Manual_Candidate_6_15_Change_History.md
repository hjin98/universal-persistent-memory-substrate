# UPMS Architecture Manual, Candidate 6.15: Change History (A.25)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.15; not architecture, decides nothing. A.1 to A.24 are in the earlier change-history files, all unchanged. This file adds A.25.

### A.25 Candidate 6.14 → candidate 6.15

Candidate 6.14 (`UPMS_Architecture_Manual_Review_Candidate_6_14.md`, SHA-256 `84df965086a16d1f6649c4e963dd072c06fd37ab8e74f5a28461c1a83e668175`) and every annex, including the anonymous-review annex 6.7 (SHA-256 `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e`), are unchanged. The changes answer the Codex review of candidate 6.14 and D1 1.14 (`UPMS_Candidate_6_14_Independent_Review.md`, SHA-256 `ecb8d25b7f1254b168ee1563eb9d4930afe2a70e015d9aee438d7d1b8ec7a7a2`; Codex, the OpenAI family of the 6.4 to 6.8, 6.12 and 6.13 reviews and the 6.11 cross-check, NO-PASS) within owner decision D-100. The D1 parent moves to 1.15 (map Q).

#### A.25.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C615-1 | SC614-01: the author's completion "conditions travel at every step" carried a hypothesis past the step that discharges it, so a valid proof with an intermediate conditional conclusion could not support an unconditional step, against D-70 and D-72 | D1 §6.1: a step's context includes the hypotheses it discharges, and what serves a step is checked against that context; a condition travels until a step discharges it, and a bypass keeps it (D-72). Core §9.9, the D-100 rows of §18.2; T140; D1 stress cases 48 to 50. This corrects the first completion so that it keeps D-70 and D-72, as the accepted recommendation said; it adds no owner decision |
| C615-2 | R614-01: D1 case 36 and T135 omitted the intermediate inference assessment their outcome now needs | Case 36 and T135 name it, with the unassessed contrast; case 35 says "terminal basis" |

**Not taken, or left open:**
- **The review's §6 simplifications** wait until the rooting rule has passed review.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 41,353 to 41,534 words; the anonymous-review annex 6.7 is unchanged at 3,293. D1 1.15 is 14,054 words. The Gate 0 package (D1 1.15, core 6.15, anonymous-review annex 6.7) is 58,881 words.

#### A.25.2 Text moved out of candidate 6.14 (D-85; moved verbatim)

#### Candidate 6.14 §1, revision paragraph

**Revision 6.14 and its files.** Revision 6.14 answers the Codex review of candidate 6.13 (NO-PASS, Serious Challenge SC613-01, findings R613-01 and R613-02) under owner decision D-100 (repairs C614-1 to C614-3 in change history A.24). The review package (D-56) is:

#### Candidate 6.14 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.13 and D1 1.13 (Codex, OpenAI family) | `UPMS_Candidate_6_13_Independent_Review.md`, SHA-256 `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b` | NO-PASS for D1 1.13 and for core 6.13 with anonymous-review annex 6.7; SC613-01, R613-01 and R613-02, repaired in this revision (change history A.24). The same reviewer and family as the 6.4 to 6.8 and 6.12 reviews and the 6.11 cross-check |
| UPMS Architecture Manual, review candidate 6.13 | `UPMS_Architecture_Manual_Review_Candidate_6_13.md`, SHA-256 `d2e59a70e3b7e746a5244cef4d97fd128019c5c039dc1c7ea390f2c22be324ca` | Immediate predecessor, unchanged; changes in change history A.24. Earlier predecessors and reviews are listed with their hashes in A.17 to A.24 |

#### Candidate 6.14 §9.9, end of the rooting sentence

with each supporting judgment's eligibility and each cited step's validity checked for the step that uses it.

#### Candidate 6.14 §15.1, T135

| T135 | Terminal basis and circularity (SC-CC611-03, D-99): a premise whose only supporting judgment cites a retained event, naming the span checked, is established and its step is assessed-sound, not circular; a premise whose only supporting judgment cites nothing is shown rootless and the route "premises not established", not broken; a premise supported only through a converse step from the conclusion makes the step circular and broken, and a further supporting judgment citing an independent evidence relation makes it sound; a premise whose support passes through a step with an event-grounded premise does not depend on the conclusion even when that premise is also supported from the conclusion; two claims supported only through each other give a step concluding from one of them "premises not established" (no root reached), never sound and never circular; a premise supported through a converse step and through that unrooted pair is circular; a premise supported through a converse step and by an event-backed judgment under an incompatible condition stays circular, and becomes sound with an event-backed judgment under the step's condition or a comparability judgment that covers it; a traversal stopped by the limit shows "rooting not determined beyond ⟨frontier⟩" and the route is not reported assessed-sound (D1 §6.1, F-25, F-30; §9.9; SC612-01, SC612-02) |

#### Candidate 6.14 §18.2, D-100 record row

| D-100 | `UPMS_Owner_Decisions_6_13_Review_2026-11-05.md` | Below, with the four completions the author makes within it |
