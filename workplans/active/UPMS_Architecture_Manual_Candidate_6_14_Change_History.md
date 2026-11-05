# UPMS Architecture Manual, Candidate 6.14: Change History (A.24)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.14; not architecture, decides nothing. A.1 to A.23 are in the earlier change-history files, all unchanged. This file adds A.24.

### A.24 Candidate 6.13 → candidate 6.14

Candidate 6.13 (`UPMS_Architecture_Manual_Review_Candidate_6_13.md`, SHA-256 `d2e59a70e3b7e746a5244cef4d97fd128019c5c039dc1c7ea390f2c22be324ca`) and every annex, including the anonymous-review annex 6.7 (SHA-256 `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e`), are unchanged. The changes answer the Codex review of candidate 6.13 and D1 1.13 (`UPMS_Candidate_6_13_Independent_Review.md`, SHA-256 `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b`; Codex, the OpenAI family of the 6.4 to 6.8 and 6.12 reviews and the 6.11 cross-check, NO-PASS) under owner decision D-100 (`UPMS_Owner_Decisions_6_13_Review_2026-11-05.md`, SHA-256 `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343`). The D1 parent moves to 1.14 (map P), which writes the rooting rule once as a finite root witness (D1 Definition 6.2).

#### A.24.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C614-1 | SC613-01: a step with no premises rooted a claim without any event, and could clear a converse cycle | D-100: a chain passes only through steps assessed valid and not invalid; a valid step with no premises left ends it and is labeled "rooted in a valid argument, not in an event"; core §5.3, §9.9, TE-07, the D-100 rows of §18.2; T138; D1 stress cases 42 to 44 |
| C614-2 | Review §4.5: `assessed-sound` could rest on a step judged invalid | The same rule; D1 "What rooting certifies" states what a sound route says about its premises; T139; D1 stress case 45 |
| C614-3 | R613-01: a premise that is the conclusion itself did not reach it; R613-02: stress case 41 was too broad | D1 "reaches" has the base case `Y = κ`; case 41 narrowed; T139; D1 stress case 46 |

**§9.9 traversal note.** The review's §4.4 warned that marking a node visited and caching failure on a back-edge would not compute the least relation; §9.9 now says the traversal keeps open exploration distinct from a completed negative result. T139 tests it.

**Not taken, or left open:**
- **The review's §6 simplifications** other than the D1 rooting consolidation wait until this rule has passed review.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 40,926 to 41,353 words; the anonymous-review annex 6.7 is unchanged at 3,293. D1 1.14 is 13,711 words. The Gate 0 package (D1 1.14, core 6.14, anonymous-review annex 6.7) is 58,357 words.

#### A.24.2 Text moved out of candidate 6.13 (D-85; moved verbatim)

#### Candidate 6.13 §1, revision paragraph and annex sentence

**Revision 6.13 and its files.** Revision 6.13 answers the Codex review of candidate 6.12 (NO-PASS, Serious Challenges SC612-01 to SC612-03, finding R612-01) under owner decisions D-97 to D-99 (repairs C613-1 to C613-4 in change history A.23). The review package (D-56) is:

The checking and Slice 4 annexes of 6.3 and the mathematics annex of 6.4 are unchanged by this revision and remain part of it; the anonymous-review annex moves from 6.6 to 6.7, which narrows one sentence of §7.8 (R612-01). Where an annex names "the core", it means this core. Section numbers are the core's, and each moved section leaves a stub here.

#### Candidate 6.13 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.12 and D1 1.12 (Codex, OpenAI family) | `UPMS_Candidate_6_12_Independent_Review.md`, SHA-256 `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26` | NO-PASS for D1 1.12 and for core 6.12 with anonymous-review annex 6.6; SC612-01 to SC612-03 and R612-01, repaired in this revision (change history A.23). The same reviewer and family as the 6.4 to 6.8 reviews and the 6.11 cross-check |
| UPMS Architecture Manual, review candidate 6.12 | `UPMS_Architecture_Manual_Review_Candidate_6_12.md`, SHA-256 `2ffe7c29d1b746c31893020a8f0d6493b6ed34ca48747fe0e38648fbfca27ef0` | Immediate predecessor, unchanged; changes in change history A.23. Earlier predecessors and reviews are listed with their hashes in A.17 to A.23 |

#### Candidate 6.13 §5.3, end of the support sentence

a supporting judgment that cites neither is admitted and shown, and a premise is established only when eligible judgments root it in such bases (D1 §6.1, D-99).

#### Candidate 6.13 §9.9, rooting sentence

Rooting and circularity are D1 §6.1's (D-99), found by one traversal of the records cited at *p*, with each supporting judgment's eligibility checked for the step that uses it;

#### Candidate 6.13 §15, TE-07 clause and T135

circular or rootless support is not a warrant (D1 §6.1, D-99);

| T135 | Terminal basis and circularity (SC-CC611-03, D-99): a premise whose only supporting judgment cites a retained event, naming the span checked, is established and its step is assessed-sound, not circular; a premise whose only supporting judgment cites nothing is shown rootless and the route "premises not established", not broken; a premise supported only through a converse step from the conclusion makes the step circular and broken, and a further supporting judgment citing an independent evidence relation makes it sound; a premise whose support passes through a step with an event-grounded premise does not depend on the conclusion even when that premise is also supported from the conclusion; two claims supported only through each other give a step concluding from one of them "premises not established" (no event root), never sound and never circular; a premise supported through a converse step and through that unrooted pair is circular; a premise supported through a converse step and by an event-backed judgment under an incompatible condition stays circular, and becomes sound with an event-backed judgment under the step's condition or a comparability judgment that covers it; a traversal stopped by the limit shows "rooting not determined beyond ⟨frontier⟩" and the route is not reported assessed-sound (D1 §6.1, F-25, F-30; §9.9; SC612-01, SC612-02) |
