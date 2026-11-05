# UPMS Architecture Manual, Candidate 6.9: Change History (A.19)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.9; not architecture, decides nothing. A.1 to A.18 are in the earlier change-history files, all unchanged. This file adds A.19.

### A.19 Candidate 6.8 → candidate 6.9

Candidate 6.8 (`UPMS_Architecture_Manual_Review_Candidate_6_8.md`, SHA-256 `8dad8d5f50e9139e536cb766dab8c9806af2ce884f1826d2dba1ac6c77b73f1f`) and every annex are unchanged. The changes answer the independent review of candidate 6.8 and D1 1.8 (`UPMS_Candidate_6_8_Independent_Review.md`, SHA-256 `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 to 6.7 reviews) under owner decisions D-92 and D-94 to D-96 (`UPMS_Owner_Decisions_6_8_Review_2026-11-05.md`). The D1 parent moves to 1.9 (map K).

**Why simplify rather than repair.** The objection-propagation family failed in five reviews in a row (SC64-01, SC65-01/02, SC66-01/02, SC67-01/03, SC68-01/02), each time where two of the mechanisms added to repair it met. Following the rule that recurrence around one mechanism triggers re-derivation before another additive repair (§17.4), the author put a simplification to the owner, who chose it (D-94). It removes three mechanisms instead of adding a fourth: registration chains, per-target resolution and homing by binding.

#### A.19.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C69-1 | SC68-01: per-binding status was undefined for recursively added disputes | D-94: one resolution per objection, labeled with the target it assessed (D1 Definition 2.5, F-3, F-3a, F-7; §5.11, §6.10; T129) |
| C69-2 | SC68-02: the homing induction failed across bindings of one objection | D-94: only review scopes are registered, and they register none; a resolution and its disputes live in the objection's own home, which is a possible home of every target in its history; §5.11's proof restated over that (T131) |
| C69-3 | SC68-03: missing provenance could satisfy the independent-test predicate | D1 Definition 5.3 requires recorded provenance (F-19; T132) |
| C69-4 | R68-01: the identity-only delta did not show a known objection newly applying through another target | D-95: the delta stays by identity; projections show the target history (§6.9; T133) |
| C69-5 | Pending proposals and C6-6 | D-92 decided; D-90, D-91 and D-93 superseded by D-94; C6-6 closed (§1.3, §18.2) |
| C69-6 | Review §7 | The binding-aware relation the review asked for is replaced by the simpler model; T131 retains its trajectory with the new discriminators |

**Not taken, or left open:**
- **Review §7 items 1, 2 and 4** (revision-count narratives, retired-mechanism commentary, duplicated invariant prose) were not taken.
- **What D-94 gives up:** objection homes other than review scopes, and resolving an objection for one target while it stays live for another. D1 §15 item 6 asks whether real projects need them.
- **Independence:** the 6.9 review is to be by a reviewer of another family (D-96).
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 39,862 to 39,994 words. D1 1.9 is 11,397 words. The Gate 0 package (D1 1.9, core 6.9, anonymous-review annex 6.5) is 54,637 words.

#### A.19.2 Text moved out of candidate 6.8 (D-85; moved verbatim)

#### Candidate 6.8 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.7 and D1 1.7 (Codex, OpenAI GPT family) | `UPMS_Candidate_6_7_Independent_Review.md`, SHA-256 `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168` | NO-PASS for D1 1.7 and for core 6.7 with anonymous-review annex 6.5; SC67-01 to SC67-03, R67-01; repaired in this revision (change history A.18, C68-1 to C68-6). The same reviewer and family as the 6.4 to 6.6 reviews |
| Proposed decisions D-90 to D-92 | `UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md`, SHA-256 `3a9fd1d4a46f70e115664e8233c6aad4fc07bde86a610a24442bd30ff1ed4236` | Applied here as **pending**; the owner has not made them (§18.2) |
| Proposed decisions D-90 and D-92 amended, D-93 | `UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md`, SHA-256 `3a0741c43d9d71802f99c5cce148bba8ab0c19c33878fc0ce1c87c3640c99d8a` | Applied here as **pending**; amends the 6.6 proposals (§18.2) |
| UPMS Architecture Manual, review candidate 6.7 | `UPMS_Architecture_Manual_Review_Candidate_6_7.md`, SHA-256 `1108d7c496d447ed3886b339dce4f183ddc1ad9c99c2b7e805786c7ac9ada3c0` | Immediate predecessor, unchanged; changes in change history A.18. Earlier predecessors and reviews are listed with their hashes in A.17 and A.18 |

#### Candidate 6.8 §5.11, possible homes

The **possible homes** of a record are its home scope and every **objection home** registered, now or earlier, for a scope among its possible homes, so registration is transitive (D-90 as amended, pending; Codex review SC67-01). An objection home is a review scope opened to review a scope's work, or another scope registered by a holder of `manage` on the registering scope as an attributed configuration revision, whose readers include every reader of the registering scope at registration. 

#### Candidate 6.8 §5.11, "Resolutions and disputes"

**Resolutions and disputes** (D-90 as amended, D-93, pending; Codex reviews SC66-01, SC67-01, SC67-03). A `resolution` decision resolves objections **at named bindings** (D1 F-3) and is homed in a possible home of every binding it names; one whose bindings share no possible home is split. A dispute of a resolution is an objection to it, homed in a possible home of the resolution. Neither carries a restriction tag of its own. `record_decision` and `record_objection` refuse any other home. **Why coverage closes.** Let `t` be a record in a footprint. An objection with binding `t` is homed among `t`'s possible homes; a resolution of it at `t` is homed among them; a dispute of that resolution is homed among the resolution's possible homes, which, registration being transitive, are among `t`'s; and so on at every depth. So every objection in D1 F-6's neighbourhood reached from `t` is homed among `t`'s possible homes and readable by a reader who reads all of them and satisfies `t`'s tags, unless a lineage exclusion applies. Each of these cases triggers the coverage statement below, which is therefore sufficient.

#### Candidate 6.8 §15.1, T129 and T131

| T129 | Bindings (SC66-02, SC67-03): decision D1 cites K1, which has objection O; K1 is revised to K2 and O carried; O's author rebinds it to K2; decision D2 cites K2; both have O in their applicable sets, each projection naming the binding through which it applies; a resolution that answers O at K2 only shows O resolved on D2 and unresolved on D1; the author's withdrawal of a binding as misapplied labels it so on the decisions that relied on it and keeps it in history; the same holds when K1 is withdrawn and O rebound to a restating claim in another scope whose readers read O's home (D1 Definition 2.5, F-3, F-3a, F-6; §5.11, §6.10; D-91, D-93 pending) |
| T131 | Dispute chains (SC67-01): Q is registered as an objection home for H and Z for Q; O1 targets claim K in H; resolution R1 is homed in Q; dispute O2 of R1 in Q; resolution R2 of O2 in Z; dispute O3 of R2 in Z; reader P reads H and Q but not Z, and reads R2 only through an own-record entitlement; P's view of a decision citing K carries the coverage statement, identically whether or not O3 exists; a resolution naming bindings with no common possible home is refused until split (§5.11; D1 F-7a; D-90 amended, pending) |

#### Candidate 6.8 §18.2, proposal rows and table

| D-90 to D-92 (**proposed, pending**) | `UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md` | Below; D-90 and D-92 as amended |
| D-90 and D-92 amended, D-93 (**proposed, pending**) | `UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md` | Below |

| ID | Proposed decision (pending the owner) | Applied in |
| --- | --- | --- |
| D-90, amended | Possible homes are transitive; every objection is homed in a possible home of its target, and a resolution in a possible home of every binding it resolves, with no restriction tags of their own | D1 F-4, F-7a; §5.11, §6.9, §6.10; T128, T131 |
| D-91 | An objection applies through every target it has been bound to; a rebind adds a binding and removes none | D1 Definition 2.5, F-3a, F-6, F-7a; §5.11, §6.10, §7.4; T129 |
| D-92, amended | The existence of an objection is not promised confidential; hidden-existence objections are outside the first product | D1 §8.2; §1.2, §5.11 |
| D-93 | Resolution and withdrawal are per binding; an objection is unresolved in a projection when it is unresolved at a binding in its footprint | D1 Definition 2.5, F-3, F-3a, F-7; §5.11, §6.9, §6.10; T129 |
