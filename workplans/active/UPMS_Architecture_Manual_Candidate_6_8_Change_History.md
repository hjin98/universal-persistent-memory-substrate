# UPMS Architecture Manual, Candidate 6.8: Change History (A.18)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.8; not architecture, decides nothing. A.1 to A.17 are in the earlier change-history files, all unchanged. This file adds A.18.

### A.18 Candidate 6.7 → candidate 6.8

Candidate 6.7 (`UPMS_Architecture_Manual_Review_Candidate_6_7.md`, SHA-256 `1108d7c496d447ed3886b339dce4f183ddc1ad9c99c2b7e805786c7ac9ada3c0`) and every annex are unchanged. The changes answer the independent review of candidate 6.7 and D1 1.7 (`UPMS_Candidate_6_7_Independent_Review.md`, SHA-256 `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 to 6.6 reviews). They apply **proposed** decisions (`UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md`: D-90 and D-92 amended, D-93 new), which the owner has not made. The D1 parent moves to 1.8 (map J).

#### A.18.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C68-1 | SC67-01: the 6.7 homing rule did not survive a chain of registrations, so a dispute of a dispute could be hidden without the coverage statement | D-90 amended: possible homes are transitive; resolutions homed by the bindings they resolve; §5.11 states the induction that makes the footprint test sufficient (D1 F-4, F-7a; T131) |
| C68-2 | SC67-02: Definition 5.3 called an independent refutation an independent confirmation | D1 Definition 5.3 separates an independent test from an independent confirmation, which also needs a confirming kind and an effective positive assessment (TE-05; T132) |
| C68-3 | SC67-03: one global resolution closed an objection on a target the resolution did not answer | D-93: resolution and withdrawal per binding (D1 Definition 2.5, F-3, F-3a, F-7; §5.11, §6.9, §6.10; T129) |
| C68-4 | R67-01: D-92 promised universal visibility the access rules do not give | D-92 amended: not promised confidential; disclosure stays with the access rules (D1 §8.2; §5.11) |
| C68-5 | Review §7 items 1, 2 and 5 | §9.9's route-status paraphrase cut to a citation of D1 §6.1; D1 F-4 and F-7a leave the homing construction to §5.11; §17.2 cites D1 §11's surface list |
| C68-6 | The new trajectories | T129 rewritten; T131 and T132 added |

**Not taken, or left open:**
- **Review §7 items 3 and 4** (revision-count narratives and retired-mechanism commentary) were not taken in this revision.
- **D-90 to D-93 are pending.** If the owner prefers a global administrative resolution to D-93, T129 and Definition 2.5 change back and the label "resolved at K2" must say what was assessed.
- **Cost of D-90 as amended:** a reader who misses any scope in a registration chain sees the coverage statement on every record of the chain's root; how often that happens is for E1, E4 and E5.
- **Independence:** this would be the fifth review by the same reviewer and family.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 39,718 to 39,862 words. D1 1.8 is 11,352 words. The Gate 0 package (D1 1.8, core 6.8, anonymous-review annex 6.5) is 54,460 words.

#### A.18.2 Text moved out of candidate 6.7 (D-85; moved verbatim)

#### Candidate 6.7 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.6 and D1 1.6 (Codex, OpenAI GPT family) | `UPMS_Candidate_6_6_Independent_Review.md`, SHA-256 `ac282071dbe79aa61262b70237a5f6e981ddb156a44e652dfb422eb1f0cc39f4` | NO-PASS for D1 1.6 and for core 6.6 with anonymous-review annex 6.5; SC66-01, SC66-02, R66-01, R66-02; repaired in this revision (change history A.17, C67-1 to C67-6). The same reviewer and family as the 6.4 and 6.5 reviews |
| UPMS Architecture Manual, review candidate 6.6 | `UPMS_Architecture_Manual_Review_Candidate_6_6.md`, SHA-256 `d0637531d39d1db6578d70bfe4c180fe59f7e6e71bc4637e415a727376179757` | Immediate predecessor, unchanged; changes in change history A.17. Earlier predecessors and reviews are listed with their hashes in A.17 |

#### Candidate 6.7 §5.11, "Resolutions and disputes"

**Resolutions and disputes** (D-90, pending; Codex review SC66-01). A `resolution` decision is homed in a possible home of every objection it resolves, and is split when they share none; an objection disputing a resolution is homed in a possible home of the objection it disputes; neither carries a restriction tag of its own. `record_decision` and `record_objection` refuse any other home. The coverage statement below therefore covers the dispute branch of D1 F-6 without a second traversal.

#### Candidate 6.7 §9.9, route-status bullet

- **Route status:** unassessed, assessed but not effective, under review, challenged, disputed, premises not established, broken or assessed-sound, with every condition that holds; every route meets at least one (D1 §6.1). Positive and negative are as D1 §6.1 defines them for each judgment kind. Premises enter **only through their own effective judgments** at *p* (D1 Definition 6.0; §9.3's age bound and scope epochs do not apply), never through their projected standing, so the evaluation is well founded and needs no fixed point (SC-TE01). An effective adverse judgment or a new objection on the route or a premise changes the route's status even when no cited revision changed. A route is circular when, for some premise, every route that premise's effective supporting judgments cite reaches the route's conclusion (D1 §6.1, judged per derivation); it gives no positive warrant; a recursive definition is not a support cycle. A premise is established, its conditions compatible and its home scope counted exactly as D1 §6.1 defines: compatibility only by a shared condition record or a comparability judgment that no other effective comparability judgment contradicts, shown otherwise as "compatibility disputed" with both (D-82), and another scope's judgment only under the same ruleset identity (TE-R11; D-69). Each route shows its **bearing** on the claim (supporting, relative to an alternative, adequate for a purpose, adverse or neutral; D1 §6.1, D-81). Carried conditions (undischarged hypotheses and declared model relations, computed per conclusion) are not premises: the route is at most supported under them, and the report lists them with every discharge and its discharging step (D1 §6.1; D-70 to D-72). A route is challenged by exactly the objections in its D1 F-6 neighbourhood. The reader's scope is the claim's home scope unless the reader names another, and the report names the scope and ruleset of each premise's judgment. Each judgment shows whether its assessor had been shown prior assessments or standing of its target. A route whose binding is an earlier claim revision is under review (D1 F-21). A route whose evidential root was deleted is under review with cause `input_deleted` (§12.3).

#### Candidate 6.7 §15.1, T129

| T129 | Bindings (SC66-02): decision D1 cites K1, which has objection O; K1 is revised to K2 and O carried; O's author rebinds it to K2; decision D2 cites K2; both D1 and D2 have O in their applicable sets, each projection names the binding through which it applies and shows O's current handling and resolution; when O is resolved, both show it resolved; the same holds when K1 is withdrawn and O rebound to a restating claim in another scope whose readers read O's home (D1 Definition 2.5, F-3a, F-6; §5.11, §6.10; D-91 pending) |

#### Candidate 6.7 §17.2, surface list

**Beyond the requested deliverable, binding only after the owner accepts them** (proposal §16, D1 §11): question pages and the understanding section; the standing report with its basis; fact-check results; the retraction impact view; the retention recommendation queue; masked review packages and the block-and-return flow; decision status (`reported`, `recorded`, `validated` awaiting signatures or complete) with its labels and late-objection delta; deletion and withdrawal markers, with "target withdrawn, not re-examined" objections (D-63); the restore coverage line (D-65); the objection coverage statement (D-80, D-87) and its shared-copy form (D-88); the "cites a withdrawn record" label (D-83); the appointment-refusal warning shown to critics (D-79); the participant-visible fields of anonymous-review records (R-19 m). The routine questions they answer are: What do we believe about X, why, and how strongly? What bears against it? What changed since a given time? What was retracted, and what depends on it? Was this observation used to fit or to test? Which sources does this rest on, and how independent are they? What did we hold then? What is recommended for archive, and why? Technical review cannot accept any of these on the owner's behalf. No independent scientific-result database or dashboard is added.

#### Candidate 6.7 §18.2, proposed decisions table

| ID | Proposed decision (pending the owner) | Applied in |
| --- | --- | --- |
| D-90 | Resolutions and their disputes are homed among the resolved objection's possible homes, with no restriction tags of their own | D1 F-4, F-7a; §5.11, §6.9, §6.10; T128 |
| D-91 | An objection applies through every target it has been bound to; a rebind adds a binding and removes none | D1 Definition 2.5, F-3a, F-6, F-7a; §5.11, §6.10, §7.4, §9.9; T129 |
| D-92 | The existence of an objection is not confidential; hidden-existence objections are outside the first product | D1 §8.2; §5.11 |
