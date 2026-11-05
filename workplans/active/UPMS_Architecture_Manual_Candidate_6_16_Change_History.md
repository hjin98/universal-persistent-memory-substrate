# UPMS Architecture Manual, Candidate 6.16: Change History (A.26)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.16; not architecture, decides nothing. A.1 to A.25 are in the earlier change-history files, all unchanged. This file adds A.26.

### A.26 Candidate 6.15 → candidate 6.16

Candidate 6.15 (`UPMS_Architecture_Manual_Review_Candidate_6_15.md`, SHA-256 `6ccb71fa7d8ca3ed43db913216d94f66d9e480d7b6f2531f3500e7af3379e457`), D1 1.15 (SHA-256 `8d934751f65cd6506d343b3ebde23a31c60ff5f57582a110023d80999d8d5b2c`) and every annex, including the anonymous-review annex 6.7 (SHA-256 `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e`), are unchanged. The changes answer the Codex review of candidate 6.15 (`UPMS_Candidate_6_15_Independent_Review.md`, SHA-256 `195d27b21f2917e010a732bb15740b43ea617d7a3349421ba5b159f38de7f251`; Codex, the OpenAI family of the 6.4 to 6.8 and 6.12 to 6.14 reviews and the 6.11 cross-check: PASS for D1 1.15, NO-PASS for core 6.15). Both findings concern this core's acceptance scenarios, which restated D1's rooting scenarios and had drifted from them; the repair takes the review's §6 advice and gives those scenarios one home, D1 §10.3.

#### A.26.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C616-1 | SC615-01: T138 excluded a premise whose supporting step carries a hypothesis the consuming step "does not carry", contradicting D1's context rule and T140 when the consuming step discharges it | T138 cites D1 cases 42 to 44 and decides by the consuming step's context; §15.1 states that a scenario reproducing D1 cases takes its records and outcomes from them |
| C616-2 | R615-01: T75 called any cycle-only premise circular without requiring that it reach the conclusion; T135 called any independent evidence relation sufficient | T75 distinguishes the two outcomes (D1 cases 38 and 39); T135, T139 and T140 cite D1 cases 33 to 36, 38 to 40 and 45 to 50 instead of restating them |

**Not taken, or left open:**
- **The review's other §6 simplifications** (chronology in the opening material, repeated retirement explanations and root-rule summaries) are not taken in this revision.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 41,534 to 41,347 words; D1 1.15 (14,054) and the anonymous-review annex 6.7 (3,293) are unchanged. The Gate 0 package is 58,694 words.

#### A.26.2 Text moved out of candidate 6.15 (D-85; moved verbatim)

#### Candidate 6.15 §1, revision paragraph

**Revision 6.15 and its files.** Revision 6.15 answers the Codex review of candidate 6.14 (NO-PASS, Serious Challenge SC614-01, finding R614-01) within owner decision D-100 (repairs C615-1 and C615-2 in change history A.25). The review package (D-56) is:

#### Candidate 6.15 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.14 and D1 1.14 (Codex, OpenAI family) | `UPMS_Candidate_6_14_Independent_Review.md`, SHA-256 `ecb8d25b7f1254b168ee1563eb9d4930afe2a70e015d9aee438d7d1b8ec7a7a2` | NO-PASS for D1 1.14 and for core 6.14 with anonymous-review annex 6.7; SC614-01 and R614-01, repaired in this revision (change history A.25). The same reviewer and family as the 6.4 to 6.8, 6.12 and 6.13 reviews and the 6.11 cross-check |
| UPMS Architecture Manual, review candidate 6.14 | `UPMS_Architecture_Manual_Review_Candidate_6_14.md`, SHA-256 `84df965086a16d1f6649c4e963dd072c06fd37ab8e74f5a28461c1a83e668175` | Immediate predecessor, unchanged; changes in change history A.25. Earlier predecessors and reviews are listed with their hashes in A.17 to A.25 |

#### Candidate 6.15 §15.1, intro sentence and scenarios T75, T135, T138, T139 and T140

Candidate 5's scenario identities are kept; retired scenarios are listed after the table.

| T75 | An inference cycle supports a claim: the theory–theory channel flags it, a route whose premise is supported only through the cycle is circular, and a human's assertion of the conclusion adds no route; a premise that also has an independent sound route keeps its step sound when someone asserts a converse step (R-02) |
| T135 | Terminal basis and circularity (SC-CC611-03, D-99): a premise whose only supporting judgment cites a retained event, naming the span checked, is established and its step is assessed-sound, not circular; a premise whose only supporting judgment cites nothing is shown rootless and the route "premises not established", not broken; a premise supported only through a converse step from the conclusion makes the step circular and broken, and a further supporting judgment citing an independent evidence relation makes it sound; a premise whose support passes through a step assessed valid with an event-grounded premise is rooted without the conclusion even when that premise is also supported from the conclusion, and is circular when that step is unassessed; two claims supported only through each other give a step concluding from one of them "premises not established" (no root reached), never sound and never circular; a premise supported through a converse step and through that unrooted pair is circular; a premise supported through a converse step and by an event-backed judgment under an incompatible condition stays circular, and becomes sound with an event-backed judgment under the step's condition or a comparability judgment that covers it; a traversal stopped by the limit shows "rooting not determined beyond ⟨frontier⟩" and the route is not reported assessed-sound (D1 §6.1, F-25, F-30; §9.9; SC612-01, SC612-02) |
| T138 | Valid-argument roots (SC613-01, D-100): a premise whose only supporting judgment cites an unassessed step with no premises shows "no root reached" and the route "premises not established", and with a converse step also cited the route is circular; once the premise-free step has an effective positive inference assessment and none negative, the route is assessed-sound and shown "rooted in a valid argument, not in an event", also in `has_sound_support`; if that step carries a hypothesis the supported step does not carry and no comparability judgment covers, the premise has no root; a route that is itself a valid step with no premises left is assessed-sound under its carried conditions with the same label (D1 §6.1, F-25, F-28; §9.9) |
| T139 | Chain validity and self-dependence (R613-01, review of 6.13 §4.5): a premise rooted only through a step with an effective negative inference assessment, or a disputed one, shows "no root reached" although its own judgment is positive; an evidence relation whose effective evidential assessment is `not-usable` is not a terminal basis; a step concluding K from K, with K's judgment citing an applicable event, is circular and broken; a premise first met along a cycle and rooted through another branch is reported rooted, whatever the traversal order (D1 §6.1; §9.9) |
| T140 | Discharge across a witness (SC614-01): in one derivation, U concludes B from hypothesis h and D concludes K from B discharging h, both assessed valid; B's judgment is `supported_under(h)` citing U and K's is `supported` citing D; an unconditional valid step T from K is assessed-sound, and the report shows h introduced and discharged, not as a condition of K; with h also used on a branch to K that bypasses D, T shows "premises not established" unless h is in its context; an unconditional valid step from B, with no step discharging h, shows "premises not established" with "compatibility not established" (D1 §6.1, Definition 2.7; §5.5, §9.9; D-70, D-72) |
