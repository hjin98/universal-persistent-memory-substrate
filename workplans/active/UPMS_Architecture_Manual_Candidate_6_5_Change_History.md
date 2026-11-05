# UPMS Architecture Manual, Candidate 6.5: Change History (A.15)

4 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** change history of review candidate 6.5; not architecture, decides nothing. A.1 to A.13 are in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md` and A.14 in `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md`, both unchanged. This file adds A.15.

### A.15 Candidate 6.4 → candidate 6.5

Candidate 6.4 (`UPMS_Architecture_Manual_Review_Candidate_6_4.md`, SHA-256 `3c9844db1c2b99094c882f3f2bcb4e6d8cdbf9f7f9df6ab02f68f962729b2e09`) and every annex are unchanged. The changes answer the independent review of candidate 6.4 and D1 1.4 (`UPMS_Candidate_6_4_Independent_Review.md`, SHA-256 `82941db24d9213921e03b6732d4101d4a58984891bd109d6da53fc4de645d5b6`; Codex, OpenAI GPT-6 family) under owner decisions D-79 to D-85. The D1 parent moves to 1.5 (its change history, map G). The anonymous-review annex moves to 6.5; the checking and Slice 4 annexes of 6.3 and the mathematics annex of 6.4 are carried unchanged.

#### A.15.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C65-1 | SC64-01: objections to a tool check or rendering a route's assessment cites challenged the route but did not join a decision's applicable set | D1 F-6 is the one applicability definition, with the objection neighbourhood `N(X)`; `A(D)` keeps what it held at commit; §9.9 and §6.9 cite it; T118 (D-85) |
| C65-2 | SC64-02: a conflict-based appointment refusal can reveal an anonymous critic | D-79: the one disclosed exception, warned of before anonymous writing; annex §7.8 states the single sealing guarantee; D1 F-20a; SE1; T104 |
| C65-3 | SC64-03: creation-time homing did not keep objections visible after access changes, rebinds or sharing | D-80: registered objection homes; the coverage statement independent of whether an objection exists; rebind check; copies carry their original's objections (D1 F-6, F-7a; §5.11, §6.8, §6.10, §9.9, §10.3; T120) |
| C65-4 | R64-01: the sound-route predicate held for refuting and neutral relations | D-81: bearing per relation kind; `has_sound_support` and `has_sound_adverse_route` (D1 §6.1, F-28; §9.9; T119) |
| C65-5 | R64-02: one favorable comparability judgment established compatibility despite a contrary one | D-82: "compatibility disputed" (D1 §6.1; §9.9; T98) |
| C65-6 | R64-03: F-3b relied on an unenforced citation ban | D-83: withdrawn records citable and labeled, their objections applicable (D1 F-3b; §6.9 check 1; T121) |
| C65-7 | R64-04: the payload-bearing recovery log lacked erasure, restore-closure and outage rules | D-84: §12.4 erasure on both log copies, restore closure with named missing records, outage behavior; §13 row; §18.1 inventory; T13, T112 |
| C65-8 | R64-05: T98's epoch clause contradicted D-48 and T109 | T98 rewritten with an actual invalidator and the unrelated-epoch control |
| C65-9 | R64-06 and review §5: §1.4 named parent 1.2; §18.1 said D-8, D-9, D-16, D-18 and D-19 were never confirmed | §1.4 names 1.5; the §18.1 row replaced by the Gate 0 obligations, with the candidate 5 decisions' recorded status |
| C65-10 | Review §7: simplify by shared owner | D-85: the D1 change maps moved to the D1 change history; §1's drafting chronology cut; §18.2 and §18.3 cut to bindings, their 6.4 tables moved below; one applicability definition; one sealing guarantee |

**Not taken, or left open:**
- **Recovering the needed canonical subset at zero RPO** instead of logging more (review §7 item 3) was not taken: D-84 keeps D-65's recovery log.
- **Restating a derivation to hide its conditions** (review §6): the reviewer's repair, exact linked conditions for a machine-supported transfer, belongs to the mathematics texts and their separate review; it is not applied here.
- **Lifetime growth of "target withdrawn" objections** (review §6) is not bounded by text; it is to be measured in E1, E4 and E5, as the review recommends.
- **The Gate 0 obligations** the review names (§18.1) are not met by any revision of this text.

**Word count:** the core body grows by about 200 words, to about 39,000: the moved §18.2 and §18.3 tables (about 1,400 words) roughly pay for the repairs. D1 1.5 stays about 11,400 words after its change maps moved out. The Gate 0 package (D1 1.5, core 6.5, anonymous-review annex 6.5) is about 53,500 words.

#### A.15.2 Text moved out of candidate 6.4 (D-85)

Moved verbatim so that D-47 to D-56, recorded only in candidate 6.4 §18.2, and the C63 and C64 repair tables stay findable.

#### Candidate 6.4 §18.2, owner decisions (moved verbatim)

The status of D-1 to D-36 at 6.2 is in change history A.12; none changed in this revision. D-37 to D-46 are in `UPMS_Owner_Decisions_2026-11-03.md`, D-57 to D-62 in `UPMS_Owner_Decisions_Math_2026-11-03.md` and D-63 to D-70 in `UPMS_Owner_Decisions_6_2_Review_2026-11-03.md`. D-47 to D-56 were decided when the owner directed revision 6.2 on the author's recommendations ("Draft on these", 3 November 2026). Owner decisions are product choices; they verify nothing technically.

| ID | Decision | Where |
| --- | --- | --- |
| D-37 to D-46 | D-36 read narrowly; SCIRE's basis-statement rule; judgment on judgment deferred; operator custody; erasure by obligation; anonymity in Slice 3; first-product boundary; de-attribution; channel assessment deferred; the SC-61 and SC-62 repairs | As recorded |
| D-47 | Objections on revision | A revision carries every objection to the successor, unresolved, until withdrawn, rebound or resolved by decision (D1 F-3a; §6.10; T108) |
| D-48 | Effectiveness for scientific standing | Defined by D1 Definition 6.0, with no wall-clock bound unless the ruleset states one; candidate 5 §9.3 governs project-memory facts only; a Slice 2 inquiry ruleset (§7.6, §9.9, §14.2; T109) |
| D-49 | Anonymous role as a session type | Distinct session type; sealed placement, edges, assignment and lifecycle acts; assistance only by a temporary review-service session, amending D-9 as confirmed; without proven session separation, critics write only through the front end's anonymous mode (annex §7.8; T110) |
| D-50 | Objections at decision commit | The core never refuses a decision because an objection exists or arrived late; late objections travel as a delta; SCIRE's policy decides whether to re-evaluate (§6.9; T100) |
| D-51 | Signature completeness | `validated` decisions are awaiting signatures or complete; only complete ones make a position current (§6.9; T100) |
| D-52 | Front-end and chair authority | Front-end registration is an operator act; a change of decision-policy owner needs the outgoing owner's attestation or an administrator-mode act and is shown; chair appointment belongs to the front end that opened the review, shown to participants; the core drops its `manage` rule for person chairs (§6.9, §14.2; T88, T100) |
| D-53 | Recovery log | Every restrictive or sealing control (permission revisions, access records, quarantines, corrections, tags, obligations, blocks, transfers, markers, sealing records, signatures) joins the tombstones in the separately backed-up recovery log applied before restore serves (§12.4, §14.2; T13) |
| D-54 | De-attribution and accountability | Accountability renderings are exempt from D-44; de-attribution is presentational (§12.3; T107) |
| D-55 | Author search | Works without their assessment values; a work's assessments appear when it is opened (§9.13, D1 F-39; T81) |
| D-56 | Structure of the review package | Core plus anonymous-review and checking annexes plus a separate change history; the outside reviewer reviews the core and the anonymous-review annex at Gate 0, and the checking annex before Gate 3 (§1, §16) |
| D-57 to D-62 | Mathematics: models and derivations first; Lean later; LaTeX; checking outside the memory; agents formalize, humans inspect | Mathematics annex; hooks H1 to H7 (§5) |
| D-63 | Withdrawing a target does not resolve its objections | D1 F-3b; §5.11, §6.10, §12.2, §12.3; T108 |
| D-64 | Anonymous-role sessions submit no judgments | D1 F-8; §4.3; annex §7.8; T99 |
| D-65 | Restore keeps dissent and discloses its gap; the recovery log has a synchronous off-site copy | §12.4, §14.2; D1 F-31; T13 |
| D-66 | Operators register front ends; the registration is shown on validated decisions | §6.9 |
| D-67 | The front end that opened a review and the transport are in the sealing TCB; logs are pseudonymous | §7.7, §8.5; annex §7.8; T113 |
| D-68 | Obligations on anonymous records go to the review scope's curators after the review closes | §9.11; annex §7.8; T110 |
| D-69 | Another scope's premise judgment counts under the same ruleset identity | D1 §6.1; §9.9; T98 |
| D-70 | A discharged hypothesis is not a premise; fidelity is never cited in an inference basis | D1 Definition 2.7, §6.1; §5.3, §5.5; T98 |
| D-71 | Open assumptions and model relations are carried conditions, not premises | D1 Definition 2.7, §6.1; §5.5, §9.9; T98 |
| D-72 | Discharge is path-scoped, checked at commit and listed | D1 Definition 2.7; §4.3, §5.5, §9.9; T98, T117 |
| D-73 | Only humans inspect; self-assessed fidelity is labeled and never clears the mandatory list | §4.3, §5.3, §7.6; mathematics annex; T117 |
| D-74 | A fidelity divergence triggers review | D1 F-32; §5.12, §9.11; T116 |
| D-75 | A designated verifier is a person; self-designation is labeled | §4.3; T117 |
| D-76 | Parsing and dimensional screening may run in UPMS, in a later slice | Mathematics annex |
| D-77 | Registering a tool is an operator act, shown on its tool checks | §4.3, §5.4; T117 |
| D-78 | A checking agent of another model family is preferred; a same-family check is labeled | Mathematics annex; SCIRE |

#### Candidate 6.4 §18.3, challenges and findings (moved verbatim)

The challenges and findings of candidates 6 to 6.2 (SC-61, SC-62, C6-1 to C6-14, C61-1 to C61-7, C62-1 to C62-12) are in change history A.12. Revision 6.3 answered the same-family review of 6.2 (C63); revision 6.4 answers the core findings of the mathematics package review (C64). Each repair is the author's and needs an independent check.

| ID | Review finding | Repair here |
| --- | --- | --- |
| C63-1 | S62-1: retracting or deleting a target resolved its objections | D-63; D1 F-3b; §5.11, §6.3, §6.10, §12.2, §12.3; T108 |
| C63-2 | S62-2: the annex's placement rule contradicted objection homing | Published and operational records split; the sealed per-pseudonym area defined outside scope permissions (annex §7.8; AC5, SE1; T86, T110) |
| C63-3 | S62-3, F62-03, F62-04: the route-status table was not total; positive, negative, compatibility and cross-scope premises undefined | D1 §6.1 "premises not established" and definitions; D-69; §9.9; T98 |
| C63-4 | F62-01, F62-05, F62-06: another assessor could supersede a judgment; replaced steps escaped carrying; validity and ruleset versions undefined | Same-assessor supersession (§5.3, §4.3); relation lifecycle `replaced` (§5.5); `validity_interval`; §7.6; T108, T109 |
| C63-5 | F62-02: anonymous judgments undefined | D-64 (§4.3, §5.11; annex §7.8; T99) |
| C63-6 | F62-07, F62-17: restore lost dissent silently; the log could not prove it was latest; the log held deletable text | D-65; §12.4, §13, §14.2; T13, T112 |
| C63-7 | F62-08, F62-09, F62-10: the stored delta on an immutable revision; decisions stranded by an owner change; front-end registration undecided | Derived delta (§5.4, §6.9); pending decisions handed over; D-66; T100 |
| C63-8 | F62-11 to F62-15: decline reasons, the TCB, closed-review obligations, omission reports, smaller annex gaps | Annex §7.8; D-67, D-68; §7.7, §8.5, §9.11, §10.6.4; T88, T105, T106, T113, T114 |
| C63-9 | F62-16: an effective negative judgment could be removed without a marker | §12.2 liveness; T115 |
| C63-10 | F62-18 and §3.6: tests and wording contradicting their contracts | T79, T84, T86, T100, T105, T13 and §13 rewritten; the stale wording fixed throughout |
| C63-11 | §3.7: text that can go | §18.2 and §18.3 history, §5.9 concept rules, consolidation and maintenance moved out; §1's 6.1 paragraph, §9.3 and the D-36 restatements shortened. Not taken: folding `Rebind` into handling, since D-63 lets it move an objection to a restatement; deriving nothing else from §12.4's honest claims |
| C63-12 | Review §7: hooks H1 to H6; H3 not purely additive | D-70; hooks absorbed (§5, §5.1, §5.3, §5.4, §5.5, §4.3). The author also found that the mathematics annex adds record kinds the core's §5 did not allow, absorbed as hook H7 |
| C64-1 | SM-1: a divergent rendering left a tool-backed route sound | D-74; D1 F-32; §5.12, §9.11; T116 |
| C64-2 | SM-2: no derivation from a model could be sound | D-71; D1 §6.1; §9.9; T98 |
| C64-3 | SM-3, FM-R16: discharge by set difference; a step in two derivations; unchecked cycles | D-72; D1 Definition 2.7; §4.3 `record_derivation`, §5.5; T98, T117 |
| C64-4 | SM-4: agents could inspect, or clear fidelity on their own renderings | D-73; §4.3, §5.3; T117 |
| C64-5 | FM-R13: renderings, bindings and tool checks could not be objected to | D1 Definition 2.5; §5.11; §9.9 |
| C64-6 | FM-R14: no ruleset covered fidelity and inspection | §7.6 |
| C64-7 | FM-R15, FM-R17: no operations for the annex records or tools; designation gaps; H7 open-ended | §4.3; §5 opening; D-75, D-77 |
| C64-8 | FM-R25: parses and cues missing from deletion's derived representations | §12.3 |
