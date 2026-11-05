# UPMS Architecture Manual, Candidate 6.6: Change History (A.16)

5 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** change history of review candidate 6.6; not architecture, decides nothing. A.1 to A.13 are in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md`, A.14 in `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md` and A.15 in `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md`, all unchanged. This file adds A.16.

### A.16 Candidate 6.5 → candidate 6.6

Candidate 6.5 (`UPMS_Architecture_Manual_Review_Candidate_6_5.md`, SHA-256 `f145b0196445b9fd5acd6625dad23183014d0defc4b2c9d176536f42651fab14`) and every annex are unchanged. The changes answer the independent review of candidate 6.5 and D1 1.5 (`UPMS_Candidate_6_5_Independent_Review.md`, SHA-256 `92ddcda5861711af8cdcdbd43a1b938767ab871cadd7ab6dbfbc8a8c8f2eb515`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 review) under owner decisions D-86 to D-89 (`UPMS_Owner_Decisions_6_5_Review_2026-11-05.md`). The D1 parent moves to 1.6 (map H). The anonymous-review annex of 6.5, the checking and Slice 4 annexes of 6.3 and the mathematics annex of 6.4 are carried unchanged.

**Why re-derive rather than patch.** SC65-01 is the second failure in a row of the applicability rule (SC64-01, then SC65-01). Following the method's rule that recurrence around one mechanism triggers re-derivation before another additive repair (§17.4), D-86 and D-87 replace the neighbourhood and its commit-time retention clause with one reliance footprint from which both applicability and coverage are derived.

#### A.16.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C66-1 | SC65-01, trajectory A: a late objection to an endpoint left a decision's set when the assessment citing the endpoint was replaced | D-86: the reliance footprint covers every assessment effective from the decision's commit to the read; `A(D)` only grows; the late-objection delta is a set difference against the policy result's position (D1 F-6; §6.9, §9.9; T118, T122) |
| C66-2 | SC65-01, trajectory B: a copy of a copy lost its first original's objections | D-86: the footprint follows the full chain of sharing originals (D1 F-6; §6.8; T123) |
| C66-3 | SC65-02, trajectory A: the coverage statement tested only basis records, not the endpoints applicability reaches | D-87: coverage over the same footprint; an unreadable footprint record triggers it (D1 F-7a; §5.11, §9.9; T124) |
| C66-4 | SC65-02, trajectory B and siblings: record-level restriction tags, lineage exclusions and retired registrations | D-87: objections carry no restriction tags of their own; any lineage exclusion triggers the statement; retired homes keep counting (D1 F-7a; §5.11, §7.4; T125) |
| C66-5 | R65-02: the rebind check tested registration, not the current audience | D-88: every current reader of the new target, including own-record readers and under its tags, must read the home (§5.11, §6.10; T126) |
| C66-6 | R65-02: sharing had no audience recheck, which D-80 required | D-88 amends D-80: sharing is labeled with the shared-copy statement and never refused (D1 F-7a; §6.8; T120, T123) |
| C66-7 | R65-01: bearing was undefined for targets outside a kind's operands | D-89: fixed target shapes; pairwise `favors`; malformed relations refused (D1 Definitions 2.6, 5.1; T127) |
| C66-8 | R65-03: §7.8 and §11.5 named the 6.3 annex; D1 §11 named candidate 6.4 §17.2; D1 §0.1 described the 6.4 review as reviewing candidate 6.5 | Stubs name annex 6.5; D1 references corrected (map H) |
| C66-9 | Review §7 items 1, 2 and 4: repeated chronology and guarantee prose | SE1 cut to its local consequence and a pointer to annex §7.8; Appendix B's revision-by-revision notes and §18.2's D-79 to D-85 table moved below; in D1, the author paragraph, §14 and the anchoring note moved to map H |

**Not taken, or left open:**
- **Review §7 item 5** (moving future-only adapter, channel and consolidation detail out of the Gate 0 reading path) was not taken: that detail is already in the checking and Slice 4 annexes, and the core keeps only the cross-cutting constraints and reopen triggers the review asks to retain.
- **How often the coverage statement shows** is not bounded by text. D-87 makes it conservative: any lineage exclusion, any retired home and any unreadable footprint record trigger it. It is to be measured in E1, E4 and E5 (D1 §15 item 5; §17.4).
- **Independence:** this revision answers the second review by the same reviewer and family (Codex). A reviewer of another family would add independence before ratification.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body grows from 38,951 to 39,499 words: the six new acceptance scenarios (T122 to T127) and the footprint and coverage text outweigh the moved SE1 detail, Appendix B notes and §18.2 table. D1 1.6 shrinks to 10,885 words. The Gate 0 package (D1 1.6, core 6.6, anonymous-review annex 6.5) is 53,630 words.

#### A.16.2 Text moved out of candidate 6.5 (D-85)

Moved verbatim so that the detail stays findable.

#### Candidate 6.5 §18.2, decisions D-79 to D-85 (moved verbatim)

| ID | Decision | Applied in |
| --- | --- | --- |
| D-79 | A conflict-based appointment refusal is the one released fact that may depend on sealed attribution, disclosed to every critic before they write anonymously | Annex §7.8, T104; D1 F-20a; SE1 |
| D-80 | Objection coverage stated uniformly; audiences rechecked on rebind and for sharing copies; no permission change refused | D1 F-6, F-7a; §5.11, §6.8, §6.10, §9.9, §10.3; T120 |
| D-81 | Support depends on direction; adverse and neutral routes never count as support | D1 §6.1, F-28; §9.9; T119 |
| D-82 | Disagreeing comparability judgments leave compatibility disputed | D1 §6.1; §9.9; T98 |
| D-83 | A withdrawn record may be cited; the decision is labeled and the record's objections apply | D1 F-3b; §6.9; T121 |
| D-84 | D-65 stands; recovery-log payload erasure, restore closure and outage behavior | §12.4, §13, §18.1; T13, T112 |
| D-85 | Simplify by owner: one applicability definition, one sealing guarantee, history out of the texts | D1 F-6, change history; §1, §18; annex §7.8 |

#### Candidate 6.5 §15, invariant SE1 (moved verbatim)

| ID | Acceptance property | Owner | First slice |
| --- | --- | --- | --- |
| SE1 | Sealed attribution (TE-15 merged here) is readable only through the review-chair role path of its review and used only for conflict and appointment checks; what a released result may depend on it is stated once, in annex §7.8: nothing, except a conflict-based appointment refusal of which every critic is warned before writing anonymously (D-79, D-85), and analyst independence across an anonymous and a signed record, or across reviews, is not established; the anonymous role is a distinct session type whose releases never become ancestry of other writes; its published records are homed in the review scope with owner, locator and provenance edges sealed, and its operational records in a sealed per-pseudonym area outside scope permissions; it submits no judgments; pseudonym assignment (to the review scope's curators after closure), role-only lifecycle acts, a review budget and pseudonymous logs; conflict checks run in the core, and sealed and critic-side grounds show only as declines, with the same words and never sooner than a voluntary one; an agent chair's model never receives a sealed identity; signing attributes every record under the pseudonym; only a temporary review-service session assists an anonymous critic; anonymity is never lifted against the writer's will; blocks never unmask; claims about people and AI critiques are never sealed; no sealed identity is collected before Slice 3 | annex 7.8 | 3 |

#### Candidate 6.5 Appendix B, revision notes (moved verbatim)

- **Revision 6.5:** repairs by the same author of the first review from outside the Claude family (Codex, OpenAI GPT-6 family, the same family as the proposal review). That reviewer read the author's change histories and earlier reviews, so it was not blind. The repairs themselves have not been reviewed by anyone.
- **Revision 6.4:** repairs by the same author of the core findings of a same-family review of the mathematics package, by a fresh Claude Fable 5.1 context. The same caveat applies.
- **Revision 6.3:** repairs written by the same author in answer to a second same-family review, by a fresh Claude Fable 5.1 context, which read the files but not the author's reasoning. The same caveat applies.
- **Revision 6.2:** repairs written by the same author in answer to a same-family review by a fresh Claude Opus 5.5 context, which read the files but not the author's reasoning. That review is not independent, and the repairs it prompted have not been reviewed by anyone.
- **Revision 6.1:** the same author re-read the Codex review in full and checked A.8 against candidate 6's §§5.4, 5.11, 6.9, 7.3, 7.8, 9.9, 9.10, 12.1–12.4 and change history A.8; the other TE-R rows were not re-checked line by line. This is a same-family check prompted by the Codex framing, not independent confirmation that the rest holds.
