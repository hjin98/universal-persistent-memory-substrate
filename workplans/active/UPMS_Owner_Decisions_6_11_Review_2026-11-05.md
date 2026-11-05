# UPMS Owner Decisions on the Candidate 6.11 Reviews, 5 November 2026 (D-97 to D-99)

5 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**These are owner decisions.** The author recommended them after the Gemini review and the Codex cross-check of candidate 6.11 and D1 1.11, and asked: "Accept my recommendations on D-97, D-64 and terminal warrants?" The owner answered **"Accept all three"** (5 November 2026). The recommendations the owner accepted are quoted in §2 as the author put them; the decision text is the author's wording of them, written after the answer, and binds only as far as it says what the owner was shown.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_11_Independent_Review.md` | `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4` | Gemini 3.8 Flash (High) review: PASS conditional on D-97; R611-01 |
| `workplans/active/UPMS_Candidate_6_11_Codex_Cross_Check.md` | `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3` | Codex cross-check: NO-PASS; SC-CC611-01 to SC-CC611-03; its §6 lists the dispositions these decisions make |
| `workplans/active/UPMS_Proposed_Decisions_6_9_Review_2026-11-05.md` | `4d5b32f04d94950b7cd0536f1874d0873c62623d41e8a201dc559f37159a56b6` | The author's proposal of D-97, decided here in amended form |
| `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Owner decision D-64, clarified here by D-98 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_11.md` | `43a234db345dba99d72c58012b0e485864aa5788817120ab4228f03744feedc7` | Its §18.2 holds the amended D-97 wording adopted here |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_11.md` | `32bb7a7a6b3d0ea93cc0210a0aedbf9725531c3f0b35e7929bc9d17089c2830e` | Its Definition 2.5 holds the operative D-97 text |

## 2. Decisions

| ID | Decision | Recommendation the owner accepted | Answers |
| --- | --- | --- | --- |
| **D-97** | **A resolution settles an objection for scientific standing only at the target it assessed; its workflow closes everywhere; a dispute applies through the resolution it disputes.** This is the amended form of the author's proposal, as worded in core 6.11 §18.2, with the operative text of D1 1.11 Definition 2.5 ("applies through", "settled for", "open for", "open in"). It replaces the proposal's narrower wording | "adopt it in its amended form. A resolution settles an objection only for the target it assessed; its workflow closes everywhere; a dispute applies through the resolution it disputes." | SC69-02, SC610-01; cross-check §6 item 2 |
| **D-98** | **Clarifies D-64.** An anonymous objection, while it is open in a view, marks routes `challenged` and sets the challenge predicates exactly as a signed objection does. It never supplies an assessment: whether a route is valid, invalid, usable or not usable, and a claim's epistemic status, change only through attributed judgments. The memory refuses no decision because of an objection, anonymous or signed. D-64's rule that anonymous-role sessions submit no judgments stands; its sentence "an anonymous participant's lead changes a route's status only through an attributed judgment" is read as "changes a route's assessed result only through an attributed judgment" | "an anonymous objection may mark a route 'challenged', but it never supplies an assessment and never blocks a decision. Invalidity still comes only through an attributed judgment. This keeps D-64's protection against anonymous vetoes." | SC-CC611-01; cross-check §6 item 1 |
| **D-99** | **Terminal warrants.** A supporting claim judgment may cite an applicable retained event directly, naming what in it was checked; that event is a terminal basis. A supporting judgment that cites neither a route nor an applicable event is rootless: it establishes nothing, and its premise is not established, not circular. A step is circular only when the premise's grounded support actually depends on the step's conclusion through cited inference steps; an empty set of cited routes is never a cycle | "a supporting judgment may cite a source event directly, and that counts as a terminal basis. A route is circular only when an actual cycle of inferences exists, never because a premise cites no route." | SC-CC611-03; cross-check §6 item 3; the terminal-warrant question open since the 6.8 ledger |

**Corrections that need no decision** (the author's to make):
- D1 Definition 5.3 applies only to a target revision of the relation (SC-CC611-02);
- core T83 names §12.2's liveness predicate instead of "an unresolved objection" (R611-01);
- the Gemini review's route-level overstatement and its nonexistent "D1 §0.3" stay recorded in the cross-check and are not repaired in the frozen review.

## 3. What this record does not decide

It accepts no text. D1 1.12, core 6.12 and annex 6.6, which apply these decisions, need independent review outside the Claude family and the owner's ratification. D-37 to D-96 stand as recorded. The wording of D-98 and D-99 above is the author's statement of the accepted recommendations; if it says more than the owner was shown, the quoted recommendation governs.
