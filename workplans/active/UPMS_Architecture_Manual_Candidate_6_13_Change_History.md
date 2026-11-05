# UPMS Architecture Manual, Candidate 6.13: Change History (A.23)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.13 and anonymous-review annex 6.7; not architecture, decides nothing. A.1 to A.22 are in the earlier change-history files, all unchanged. This file adds A.23.

### A.23 Candidate 6.12 → candidate 6.13

Candidate 6.12 (`UPMS_Architecture_Manual_Review_Candidate_6_12.md`, SHA-256 `2ffe7c29d1b746c31893020a8f0d6493b6ed34ca48747fe0e38648fbfca27ef0`), the anonymous-review annex 6.6 (`UPMS_Architecture_Manual_Review_Candidate_6_6_Annex_Anonymous_Review.md`, SHA-256 `df0dd59de9ebce447c77caf0493f5ed29b03c87ca70683e2f38dd05410d791a4`) and the other annexes are unchanged. The changes answer the Codex review of candidate 6.12 and D1 1.12 (`UPMS_Candidate_6_12_Independent_Review.md`, SHA-256 `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26`; Codex, the OpenAI family of the 6.4 to 6.8 reviews and the 6.11 cross-check, NO-PASS) within owner decisions D-97 to D-99. The D1 parent moves to 1.13 (map O), the anonymous-review annex to 6.7. The three Serious Challenges concern the author's wording of D-99 in 6.12: it made any cited route count as a root, applied compatibility to establishment but not to the alternatives that clear a cycle, and kept an empty-set case in `broken`.

#### A.23.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C613-1 | SC612-01: a route citation counted as grounded with no event root behind it, and a rootless alternative could clear a cycle | D1 §6.1 "rooted for a step, avoiding a set", the least relation reaching a terminal basis; only rooted premises are established; core §5.3, §9.9; T135; D1 stress cases 38 and 39 |
| C613-2 | SC612-02: a judgment under an incompatible condition could clear a cycle | Supporting judgments are eligible only for the step that uses them, at every depth (D-69, D-82); T135; D1 stress case 40 |
| C613-3 | SC612-03: an empty set of effective assessments made a route `broken` | The all-negative branch needs at least one effective assessment; T137; D1 stress case 41 |
| C613-4 | R612-01: "nothing is refused" overstated D-98, since an objection keeps its target live | Annex §7.8, core §4.4 and the D-98 row say no decision is refused; D1 stress case 32 |

**Not taken, or left open:**
- **The review's §6 simplifications** were not taken in this revision.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 40,788 to 40,926 words, the anonymous-review annex from 3,286 to 3,293. D1 1.13 is 12,886 words. The Gate 0 package (D1 1.13, core 6.13, anonymous-review annex 6.7) is 57,105 words.

#### A.23.2 Text moved out of candidate 6.12 (D-85; moved verbatim)

#### Candidate 6.12 §1, revision paragraph and annex sentence

**Revision 6.12 and its files.** Revision 6.12 answers the Codex cross-check of candidate 6.11 (NO-PASS, Serious Challenges SC-CC611-01 to SC-CC611-03) and the Gemini review's informational R611-01, and applies owner decisions D-97 to D-99 (repairs C612-1 to C612-5 in change history A.22). The review package (D-56) is:

The checking and Slice 4 annexes of 6.3 and the mathematics annex of 6.4 are unchanged by this revision and remain part of it; the anonymous-review annex moves from 6.5 to 6.6, which changes one sentence of §7.8 and test T99 (D-98). Where an annex names "the core", it means this core. Section numbers are the core's, and each moved section leaves a stub here.

#### Candidate 6.12 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.11 and D1 1.11 (Gemini 3.8 Flash, Gemini family) | `UPMS_Candidate_6_11_Independent_Review.md`, SHA-256 `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4` | PASS conditional on D-97; R611-01, repaired here (C612-5). Overturned by the cross-check below |
| Cross-check of candidate 6.11 and D1 1.11 (Codex, OpenAI family) | `UPMS_Candidate_6_11_Codex_Cross_Check.md`, SHA-256 `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3` | NO-PASS for D1 1.11 and for core 6.11 with anonymous-review annex 6.5; SC-CC611-01 to SC-CC611-03, repaired in this revision (change history A.22). The same reviewer and family as the 6.4 to 6.8 reviews |
| UPMS Architecture Manual, review candidate 6.11 | `UPMS_Architecture_Manual_Review_Candidate_6_11.md`, SHA-256 `43a234db345dba99d72c58012b0e485864aa5788817120ab4228f03744feedc7` | Immediate predecessor, unchanged; changes in change history A.22. Earlier predecessors and reviews are listed with their hashes in A.17 to A.22 |

#### Candidate 6.12 §9.9, circularity sentence

Circularity is D1 §6.1's dependence on the step's conclusion (D-99), found by one traversal of the records cited at *p*; where the traversal limit (§14.2) stops it, the route shows "circularity not determined beyond ⟨frontier⟩" and is not reported assessed-sound (D1 F-30).

#### Candidate 6.12 §15.1, T135

| T135 | Terminal basis and circularity (SC-CC611-03, D-99): a premise whose only supporting judgment cites a retained event, naming the span checked, is established and its step is assessed-sound, not circular; a premise whose only supporting judgment cites nothing is shown rootless and the route "premises not established", not broken; a premise supported only through a converse step from the conclusion makes the step circular and broken, and a further supporting judgment citing an independent evidence relation makes it sound; a premise whose support passes through a step with an event-grounded premise does not depend on the conclusion even when that premise is also supported from the conclusion; a dependence traversal stopped by the limit shows "circularity not determined beyond ⟨frontier⟩" and the route is not reported assessed-sound (D1 §6.1, F-25, F-30; §9.9) |

#### A.23.3 Text moved out of anonymous-review annex 6.6 (D-85; moved verbatim)

**Status:** part of review candidate 6.12, proposed D3 architecture; not accepted-current. Reviewed with the core at Gate 0 (D-56). Section and test numbers are those of the core, `UPMS_Architecture_Manual_Review_Candidate_6_12.md`, which leaves a stub at each moved section and whose terms, invariants and decisions govern this text. It replaces the 6.5 annex, which stays unchanged (it was carried unchanged into 6.6 to 6.11); the changes are mapped in change history A.22. They apply owner decision D-98 to the Codex cross-check of candidate 6.11 (SC-CC611-01).

and nothing is refused because of the objection (D1 F-8, D-37, D-98).
