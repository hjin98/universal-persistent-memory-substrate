# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.6: Change History (Map H)

5 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** change history of D1 candidate 1.6; not D1 authority, decides nothing. Maps B to G are in `UPMS_Theory_Evidence_Formulation_D1_Change_History.md`, which stays unchanged. This file adds map H and holds the text moved out of candidate 1.5 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_5.md`, SHA-256 `c8876fded8756e93d74bd7885554103e691b84e0f929bd202f0b17b6858ee3b4`), which stays unchanged.

## H. Change map, candidate 1.5 → candidate 1.6

The changes answer the independent review of candidate 1.5 and architecture candidate 6.5 (`UPMS_Candidate_6_5_Independent_Review.md`, SHA-256 `92ddcda5861711af8cdcdbd43a1b938767ab871cadd7ab6dbfbc8a8c8f2eb515`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 review) under owner decisions D-86 to D-89 (`UPMS_Owner_Decisions_6_5_Review_2026-11-05.md`).

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.6; the 6.5 review, the D-86 to D-89 record, candidate 1.5 and this file added as inputs; the 6.4 review's row, which described it as a review of architecture candidate 6.5, corrected; architecture references name candidate 6.6; the author paragraph cut to the current revision | R65-03; D-85 |
| Definitions 2.6, 5.1 | Target shapes fixed per relation kind: `favors` takes two distinct claims, every other kind one; several alternatives as pairwise relations; malformed relations refused | R65-01, D-89 |
| F-6 | Re-derived around the reliance footprint `F(X, I)`: endpoints of every assessment effective at any position in the interval, and the full chain of sharing originals; `A(D)` over `[commit(D), p]` only grows; `A(κ)` and "challenged" current-only; the rule that `A(D)` keeps what it held at commit is removed, because the footprint subsumes it | SC65-01, D-86 |
| F-7a | Coverage over the same footprint; unreadable footprint records, retired objection homes and lineage exclusions trigger it; the shared-copy form; objections carry no restriction tags of their own; rebind checks the new target's current readers; shares never refused | SC65-02, R65-02; D-87, D-88 |
| §6.1 | "challenged" cites the footprint | SC65-01 |
| F-20a | Cites annex §7.8 for the disclosed exception instead of restating it | Review §7 item 2; D-85 |
| §10.2, §10.3 | Reopen condition on the statement's frequency; stress cases 20 to 24 | — |
| §11 | The coverage statement's shared-copy form marked beyond the deliverable; the stale "candidate 6.4 §17.2" reference corrected | D-88; R65-03 |
| §14 | Cut to a pointer; its table moved below | Review §7 item 3; D-85 |
| §15 | Open challenge 5, the statement's frequency | — |
| Appendix A | Anchoring note cut to one statement; the revision-by-revision note moved below | Review §7 item 1; D-85 |

No other text changed. **Word count:** 11,357 → 10,885.

**Not taken:** review §7 item 5 (moving future-only detail out of the Gate 0 reading path) concerns the architecture; D1 has no such detail beyond Appendix B, which stays.

## Text moved out of candidate 1.5 (D-85)

#### Candidate 1.5 author paragraph (moved verbatim)

**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request. No subagents were used. Revision 1.1 follows the author's re-reading of the Codex review against the operative text, at the product owner's request. Revision 1.2 repairs the findings of a same-family review of 1.1 and folds in the owner's decisions D-37 to D-46 and those of §16 here, at the owner's direction ("Draft on these", 3 November 2026). Revision 1.3 repairs the findings of a second same-family review, of 1.2, by Claude Fable 5.1, and folds in owner decisions D-63 to D-70 ("Proceed with your recommendation", 3 November 2026). Revision 1.4 applies, in this parent text, the findings of a same-family review of the mathematics package that are parent-D1 rules, and owner decisions D-71, D-72 and D-74 ("Accept, draft it", 3 November 2026). Revision 1.5 repairs the D1 findings of the first review of these texts from outside the Claude family (Codex, OpenAI GPT-6 family, NO-PASS) and folds in owner decisions D-79 to D-85 ("Proceed with youre recommendation", 4 November 2026).

#### Candidate 1.5 §14, findings raised while drafting (moved verbatim)

These are the author's findings on the proposal's D1 content, recorded for the reviewer. None is a Serious Challenge to a D1 meaning; the D3-level challenges, including two Serious Challenges to the proposal's text, are in the architecture change histories (A.12 to A.15).

| ID | Finding | Disposition here |
| --- | --- | --- |
| D1-F1 | The proposal says authorship is never an input to assessment (§6.4), and also counts independence by analyst (§5.4) and checks reviewer conflicts by identity (§7.1). Read literally, these conflict | F-20: identity relations only, never attributes or aggregates |
| D1-F2 | The proposal's decision kinds omit resolution by assessment, while SC-41's repair (carried with a back-end fix, proposal §13.2) needs resolution to carry decision fields | Definition 2.10 adds `resolution`; F-3 |
| D1-F3 | "Applies" was unbounded in SCIRE v0.4 and is a back-end invariant in the proposal (TE-04) | F-6 fixes a one-hop default from the cited basis, which a front end may widen |
| D1-F4 | Re-review V4-12 (iii), de-attribution of a person from derived statements on request, and (iv), where an argument may stop, are carried by neither the proposal nor this text | (iii): F-9a, proposed; owner decision. (iv): open (candidate 6.5 §18.2) |
| D1-F5 | The re-review's D1 note on V3-10 asks which test or threshold a statistical disagreement uses | F-22 and §9: no disagreement without a declared model and rule; method is D2 |
| D1-F6 | The Codex review (SC-TE01) shows that exact judgment references alone do not make support current: an unchanged revision can lose effectiveness, a new adverse judgment supersedes nothing, and cyclic support has no defined evaluation | §6.1 well-foundedness; §6.5 dependency modes and currentness. Judgment on judgment stays open |
| D1-F7 | The Codex review (SC-TE04) shows that an absolute reading of D-36 would let anonymity shield an independently verified invalidity | F-8 narrow reading; owner decision |
| D1-F8 | The Codex review (TE-R12) shows channel assessment can proxy for a person or lab | F-41, F-41a |
| D1-F9 | (Revision 1.1.) Candidate 1 let `content` judgment-basis entries count as epistemic dependencies while only `current` entries went stale, so a judgment could keep relying on an overturned judgment's content | §6.5: only `current` entries count |
| D1-F10 | (Revision 1.1.) Candidate 1's F-20 used same sealed author in independence counting. Between an anonymous and a signed record, any released result of that check reveals whether they share an author (the Codex review's TE-R13 trajectory), and candidate 6's count rule covered only critic counts | F-20 narrowed; F-20a |
| D1-F11 | (Revision 1.2; same-family review SC-R1.) Candidate 1.1 never said when `superseded` applies, and the architecture applied it to every revision, so a trivial edit resolved every objection | Definition 2.5 narrowed; F-3a carries objections |
| D1-F12 | (1.2; SC-R2.) "Effective" was undefined for scientific judgments; read as project-memory admission, no route was ever sound, and read otherwise, the admission rule kept by D-39 was bypassed | Definition 6.0; statuses "assessed, not effective" and "disputed" |
| D1-F13 | (1.2; R-01.) Objections to a cited route's observation, model, calibration or premises never reached the decision | F-6 endpoints; §6.1 "challenged" |
| D1-F14 | (1.2; R-02.) A converse step broke a well-founded route, and disagreement between assessors showed as "broken" | Per-derivation circularity; "disputed" |
| D1-F15 | (1.2; R-03, R-07, R-15, R-17.) History did not pin the projection version; F-17 made the memory refuse a front-end decision; de-attribution reached accountability renderings; author views could juxtapose assessments | F-31; F-17 as a label; F-9a exemptions; F-39 |
| D1-F16 | (Revision 1.3; same-family review S62-1.) Retracting or deleting a target resolved its objections as `superseded`, so restating the claim gave a clean position | `superseded` removed from resolutions; F-3b; D-63 |
| D1-F17 | (1.3; S62-3, F62-03, F62-04.) The route-status table had no status for a positive route on an unestablished premise; positive and negative, condition compatibility and cross-scope premises were undefined | "premises not established"; definitions in §6.1; D-69 |
| D1-F18 | (1.3; F62-01, F62-02, F62-05, F62-06.) Another assessor, or an anonymous session, could supersede or submit a judgment that broke a route; a step replaced through `supersedes` escaped F-3a; validity interval and ruleset version were undefined | Definition 2.8 supersession and attribution; F-3a steps and relations; Definition 6.0; D-64 |
| D1-F19 | (1.3; review §7.) A derivation with a discharged hypothesis could never be sound, because the hypothesis could never be `supported` | Definition 2.7 discharge; §6.1 premises; D-70 |
| D1-F20 | (Revision 1.4; mathematics review SM-2, SM-3.) Open assumptions and model relations could never be established, so no derivation from a model was ever sound; discharge was computed by set difference, so a side-branch use of a hypothesis vanished | Carried conditions; path-scoped discharge; one derivation per step (Definition 2.7, §6.1; D-71, D-72) |
| D1-F21 | (1.4; SM-1, FM-R12, FM-R13.) A divergent rendering left a tool-backed route sound; renderings, bindings and tool checks could not be objected to; F-20's "only" omitted project roles | F-32 cause (D-74); Definition 2.5 targets; "challenged"; F-20 roles |
| D1-F22 | (Revision 1.5; Codex review SC64-01.) Objections to a cited tool check or rendering challenged a route but did not join a decision's applicable set, because F-6 and the "challenged" row listed endpoints differently | One neighbourhood `N(X)` in F-6, cited by every other rule (D-85) |
| D1-F23 | (1.5; R64-01.) `has-sound-route` was true for a usable refuting or neutral relation | Bearing per kind in §6.1; predicates by direction in F-28 (D-81) |
| D1-F24 | (1.5; R64-02, R64-03.) One favorable comparability judgment established compatibility despite a concurrent contrary one; F-3b relied on a citation ban nothing enforced | "compatibility disputed" (D-82); withdrawn records citable and labeled (D-83) |
| D1-F25 | (1.5; SC64-02, SC64-03.) "Nothing shown depends on a sealed identity" was false for appointment refusals; projections could silently omit objections after access changed | F-20a narrowed with the disclosed exception (D-79); F-7a coverage statement (D-80) |

#### Candidate 1.5 Appendix A, anchoring note (moved verbatim)

- **Anchoring:** the Codex review was read after drafting; the repairs it prompted were fitted to an existing text, and their adequacy is for the reviewer to judge. Revision 1.1 came from the same author re-reading that review against the operative text; it is a same-family check, not independent confirmation that the rest holds. Revision 1.2 answers a same-family review by a fresh Claude context; the author then wrote the repairs, so they too need an independent check. Revision 1.3 answers a second same-family review, by Claude Fable 5.1 in a fresh context; the same caveat applies. Revision 1.4 answers the parent-D1 findings of a same-family review of the mathematics package, also by Claude Fable 5.1. Revision 1.5 answers the first review from outside the Claude family (Codex, OpenAI GPT-6 family, the same family as the proposal review); the same author wrote the repairs, so they need a new independent check.
