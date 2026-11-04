# Workplans

This index lists the coordination records in `workplans/`. It routes to the documents and is not itself authority: each document states its own status. As of 3 November 2026 no architecture manual is accepted-current.

## Lifecycle

- `active/` holds records whose obligations are still open, including superseded revisions that open review packages still cite.
- `archive/` holds records that are complete, or whose remaining obligations an accepted successor owns.
- Review packages bind inputs by file name and SHA-256, so files are not renamed or edited in place. A revision is a new file.

## Active records

| File | Kind | Note |
| --- | --- | --- |
| `UPMS Architecture Proposal v0.1.md` | Proposal | Initial proposal |
| `UPMS Architecture Proposal v0.2.md` | Proposal | Introduces the Event, Claim and Judgment model |
| `UPMS Architecture Proposal v0.3.md` | Proposal | Input to the first manual |
| `UPMS Architecture Manual.md` | Manual baseline | Reviewed NO-PASS in the Codex review |
| `UPMS Architecture Review.md` | Review record | Codex review of the baseline, findings F01–F18 |
| `UPMS Architecture Manual - Refined.md` | Manual, review candidate 1 | Repairs F01–F18 |
| `UPMS_Round_2_Amendments.md` | Amendments | A1–A7, applied to candidate 1 |
| `UPMS_Architecture_Manual_Review_Candidate_2.md` | Manual, review candidate 2 | Reviewed NO-PASS in the candidate 2 cross-review (CR01–CR10) |
| `UPMS_Cross_Review_Request.md` | Review request | Requests the candidate 2 cross-review |
| `UPMS_Architecture_Manual_Review_Candidate_4.md` | Manual, review candidate 4 | First issue, SHA-256 `d2146daa…` |
| `UPMS_Re-Review_Request_Candidate_4.md` | Review request | Cites the first issue of candidate 4 |
| `check_C4.md` | Review record | Same-family check of a candidate 4 draft, findings K-01–K-20 |
| `UPMS_Architecture_Manual_Review_Candidate_4_1.md` | Manual, review candidate 4 | Revised issue, SHA-256 `19a9e3ed…`; reviewed NO-PASS in the same-family review below; superseded by candidate 5 |
| `UPMS_Re-Review_Request_Candidate_4_1.md` | Review request | Cites the revised issue under the file name `UPMS_Architecture_Manual_Review_Candidate_4.md` |
| `UPMS_Candidate_4_Same_Family_Review.md` | Review record | Same-family (Claude) review of the revised candidate 4: NO-PASS, Serious Challenge SC-1, findings N-01–N-12; not the independent review Gate 0 requires |
| `UPMS_Architecture_Manual_Review_Candidate_5.md` | Manual, review candidate 5 | Repairs SC-1 and N-01–N-12 (change map in its Appendix A.7), SHA-256 `406cf3b4…`; proposes revised outcomes for D-8, D-9, D-13, D-16 to D-19, pending the owner; not yet reviewed; frozen as an input to the theory–evidence proposal below, and its independent review is not requested (D-23) |
| `UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | Structural proposal | Owner decisions D-20 to D-36: one theory–evidence memory, SCIRE as front end, SSDS outside, security proportionate to open science, retention by importance, works judged one by one and people never scored by the system (D-32 supersedes D-26 and D-31), four rights, project memory first, open decentralized debate, with anonymous review reserved for when it is needed, under a neutral review chair (a fresh agent by default), where anonymous objections inform but never block; sets the direction for the next manual candidate; not yet reviewed |
| `UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | Review record | Codex (OpenAI GPT-6 family) review of the proposal: NO-PASS, Serious Challenges SC-TE01 to SC-TE05, findings TE-R01 to TE-R20; different-family. Indexed by the candidate 6 change |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md` | D1 formulation, candidate 1 (superseded by 1.1, kept as its predecessor) | Proposed D1 parent for UPMS: meaning of the theory–evidence records, standing, source assessment and the person guard, drawn from proposal §3–§6 and SCIRE v0.4 §§3–7; not reviewed |
| `UPMS_Architecture_Manual_Review_Candidate_6.md` | Manual, review candidate 6 (superseded by 6.1, kept as its predecessor) | Applies D-20 to D-36 to frozen candidate 5 and reconciles its §§11–13 and 15 with D-24 and D-25 (change map in its Appendix A); folds in bounded repairs for the Codex review (status of each finding in its Appendix A.8); raises Serious Challenges SC-61 and SC-62 against the proposal's text with provisional repairs; judgment on judgment carried as an open proposal; not reviewed |
| `UPMS_Review_Request_Candidate_6.md` | Review request, superseded and never sent | Superseded by `UPMS_Review_Request_Candidate_6_1.md` |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md` | D1 formulation, candidate 1.1 (superseded by 1.2, kept as its predecessor) | Revision of candidate 1: sealed authorship no longer enters independence (F-20a), only `current` judgment-basis entries count, de-attribution of derived statements proposed (F-9a), and the author's recommendations; changes in its Appendix B; not reviewed |
| `UPMS_Architecture_Manual_Review_Candidate_6_1.md` | Manual, review candidate 6.1 (superseded by 6.2, kept as its predecessor) | Revision of candidate 6 after the author re-checked its Codex dispositions against the body text: repairs C61-1 to C61-6 (decision-policy owner, sealed attribution in released results, signing, assisting agents, judgment-basis modes), channel assessment deferred (C61-7), and the author's recommendation on every open owner decision; changes in its Appendix A.9; not reviewed |
| `UPMS_Review_Request_Candidate_6_1.md` | Review request, superseded and never sent | Asks a reviewer outside the Claude family to review D1 candidate 1.1 and candidate 6.1 against the Codex findings, by hash |
| `UPMS_Owner_Decisions_2026-11-03.md` | Owner decision record | The owner accepted every author's recommendation in candidate 6.1 §18.2 and §18.3: confirmations of D-1, D-4, D-8, D-9, D-16, D-18, D-19 and the recency rule; new decisions D-37 to D-46, bound by hash; accepts neither text |
| `UPMS_Candidate_6_1_Same_Family_Review.md` | Review record (same family) | Fresh Claude Opus 5.5 context: NO-PASS for 6.1 and D1 1.1; SC-R1 to SC-R3, R-01 to R-20; not independent |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md` | D1 formulation, candidate 1.2 | Repairs SC-R1 (objections carried on revision), SC-R2 (effectiveness for scientific standing, Definition 6.0) and R-01 to R-03, R-07, R-15, R-17; folds in D-37 to D-56; channel assessment moved to a deferred appendix; not reviewed; reviewed same-family (NO-PASS), superseded by 1.3 |
| `UPMS_Architecture_Manual_Review_Candidate_6_2.md` | Manual, review candidate 6.2 (core) | Gate 0 to Slice 2 and every cross-cutting contract; repairs C62-1 to C62-12, including the reconciliation check against candidate 5; owner decisions D-47 to D-56 in its §18.2; not reviewed; reviewed same-family (NO-PASS), superseded by 6.3 |
| `UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Anonymous_Review.md` | Manual 6.2, annex | §7.8 and §11.5 with their tests; reviewed with the core at Gate 0; superseded by the 6.3 annex |
| `UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Checking.md` | Manual 6.2, annex | §5.7, §5.8, §9.7, §9.8, §9.12, deferred channel assessment and their tests; reviewed before Gate 3; superseded by the 6.3 annex |
| `UPMS_Architecture_Manual_Candidate_6_2_Change_History.md` | Change history | Change map A.1 to A.11, including the Codex dispositions and the reconciliation check; not architecture; superseded by the 6.3 change history |
| `UPMS_Review_Request_Candidate_6_2.md` | Review request, not yet sent | Asks a reviewer outside the Claude family to review D1 1.2 and the 6.2 core with its anonymous-review annex, by hash; superseded, unsent, by the 6.3 request |
| `UPMS_Candidate_6_2_Same_Family_Review.md` | Review record (same family) | Fresh Claude Fable 5.1 context, SHA-256 `255bf6a8…742b9`: NO-PASS for 6.2 core with annex and D1 1.2; S62-1 to S62-3, F62-01 to F62-18; not independent |
| `UPMS_Owner_Decisions_Math_2026-11-03.md` | Owner decision record | D-57 to D-62: models and derivations first, pure mathematics later; Lean as default formal system; LaTeX; checking and computation as SCIRE tools; agents formalize, humans inspect; proceed with the author's sequence |
| `UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md` | D1 formulation, mathematics, candidate 1 | Extends D1 1.2: expressions, symbols and bindings, dimensions, models, derivations and their conditions, tool checks, formalization fidelity, inspection coverage, designated verifiers, the inspection brief; not reviewed; reviewed same-family (NO-PASS), superseded by 1.1 |
| `UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Mathematics.md` | Manual 6.2, proposed addition | D3 realization of the mathematics formulation; needs core hooks H1 to H6 at the next core revision; not part of the 6.2 Gate 0 package; not reviewed; superseded by the 6.3 annex, whose hooks the 6.3 core absorbs |
| `UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | Owner decision record | D-63 to D-70, answering the 6.2 same-family review: withdrawal does not resolve objections; no anonymous judgments; restore keeps dissent; front-end registration; sealing TCB; closed-review obligations; cross-scope premises; discharged hypotheses |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_3.md` | D1 formulation, candidate 1.3 | Repairs S62-1, S62-3, F62-01 to F62-06 and folds in D-63, D-64, D-69, D-70; changes in Appendix E; unreviewed; superseded by 1.4 |
| `UPMS_Architecture_Manual_Review_Candidate_6_3.md` | Manual, review candidate 6.3 (core) | Repairs C63-1 to C63-12; absorbs the mathematics hooks H1 to H7; history moved to the change history; unreviewed; reviewed same-family for its hooks only (NO-PASS), superseded by 6.4 |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Anonymous_Review.md` | Manual 6.3, annex | §7.8 and §11.5 with their tests; published and operational records split; reviewed with the core at Gate 0; carried unchanged into 6.4 |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | Manual 6.3, annex | As 6.2, plus §5.9's concept-level rules and hook H4; reviewed before Gate 3; carried unchanged into 6.4 |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` | Manual 6.3, annex | Consolidation and maintenance cost, moved from the core; reviewed before Gate 4; carried unchanged into 6.4 |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Mathematics.md` | Manual 6.3, proposed addition | Mathematics records, parsing, standing of derivations, tools and the brief; hooks now in the core; reviewed separately; not reviewed; reviewed same-family (NO-PASS), superseded by the 6.4 annex |
| `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md` | Change history | A.1 to A.11 carried; A.12 the 6.2 decision status and challenges moved from the core; A.13 the 6.2 → 6.3 map; not architecture; continued by the 6.4 change history |
| `UPMS_Review_Request_Candidate_6_3.md` | Review request, not yet sent | Asks a reviewer outside the Claude family to review D1 1.3 and the 6.3 core with its anonymous-review annex, by hash; superseded, unsent, by the 6.4 request |
| `UPMS_Mathematics_Package_Same_Family_Review.md` | Review record (same family) | Fresh Claude Fable 5.1 context, SHA-256 `ea064acf…f569c0`: NO-PASS for the mathematics D1 text, the 6.3 mathematics annex with hooks H1 to H7, and the SCIRE extension proposal; SM-1 to SM-4, FM-R01 to FM-R31; not independent |
| `UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | Owner decision record | D-71 to D-78, answering the mathematics review: carried conditions; path-scoped discharge; only humans inspect; divergence triggers review; designation guards; parsing later; tool registration; checking-agent family preferred |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_4.md` | D1 formulation, candidate 1.4 | Parent-D1 rules from the mathematics review (carried conditions, path-scoped discharge, new objection targets, divergence as a cause, project roles); changes in Appendix F; unreviewed |
| `UPMS_Architecture_Manual_Review_Candidate_6_4.md` | Manual, review candidate 6.4 (core) | Repairs C64-1 to C64-8 on top of 6.3; carries the 6.3 anonymous-review, checking and Slice 4 annexes unchanged; unreviewed |
| `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md` | Manual 6.4, proposed addition | Rewritten against core 6.4 and mathematics D1 1.1; parsing and dimensional screening in a later slice; reviewed separately; unreviewed |
| `UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md` | D1 formulation, mathematics, candidate 1.1 | Repairs SM-1 to SM-4 and FM-R01 to FM-R11 under D-71 to D-78; changes in Appendix B; unreviewed |
| `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md` | Change history | A.14, 6.3 → 6.4; A.1 to A.13 stay in the 6.3 change history |
| `UPMS_Review_Request_Candidate_6_4.md` | Review request, not yet sent | Asks a reviewer outside the Claude family to review D1 1.4 and the 6.4 core with the 6.3 anonymous-review annex, by hash |
| `UPMS_Review_Handoff_Candidate_6_4/` | Review hand-off (folder) | Byte-identical copies of every file the 6.4 review request binds, plus the SCIRE sources it cites, with a `SHA256SUMS` manifest and a README telling the reviewer how to check the package and deliver the review; the originals stay authoritative |

Not in this repository, although the review packages cite them: candidate 3, the candidate 2 cross-review, the candidate 3 interim review and its sub-reports A, B and C.
