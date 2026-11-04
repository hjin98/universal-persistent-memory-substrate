# UPMS Owner Decisions on the 6.2 Same-Family Review, 3 November 2026 (D-63 to D-70)

3 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**The product owner accepted the author's recommendations on the owner questions raised by the same-family review of candidate 6.2.** The author put eight recommendations to the owner in a Claude Code session, and the owner answered: "Proceed with your recommendation." This record states those recommendations as decided, binds them to the review they answer, and states what they do not decide. Claude wrote this record and cannot widen the decisions: where this record and the recommendations as put to the owner differ, the recommendations govern.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_2_Same_Family_Review.md` | `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9` | The review whose §6 owner questions, S62-1, F62-02, F62-04, F62-07, F62-10, F62-12, F62-13 and §7 (hook H3) these decisions answer |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2.md` | `0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc` | The core the decisions amend |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md` | `219a81bbfa061cf5914df1c144246416ce1b28ea15a6f5985c1a4151ecd01ed2` | The D1 text the decisions amend |

No bound file is changed by this record. Candidate 6.3 and D1 candidate 1.3 apply the decisions.

## 2. Decisions

| ID | Decision | Answers |
| --- | --- | --- |
| **D-63** | **Withdrawing a target does not resolve its objections.** When a claim, step or relation with an unresolved objection is retracted, withdrawn or deleted by its author with no successor revision, the objection stays unresolved and live, shown as "target withdrawn, not re-examined", on the target's tombstone and on every question page where the target was a position. `superseded` is no longer a resolution. The objection ends only when its author withdraws it, rebinds it to another record, or a resolution decision resolves it | S62-1 |
| **D-64** | **Anonymous-role sessions submit objections, critiques, questions and claims that are not about a person. They never submit judgments.** The core refuses any judgment from an anonymous-role session. An anonymous participant's lead changes a route's status only through an attributed judgment (D-37) | F62-02 |
| **D-65** | **Restore discloses what it may have lost, and dissent survives it.** The recovery log is small and has a synchronous off-site copy (recovery point zero for the log). Objections, objection handling and lifecycle changes, and resolution decisions join it. Every restore commits a restore record naming the backup position and the log position it applied, and every read that the gap between them could affect says so | F62-07 |
| **D-66** | **Operators may register front ends.** This extends D-40's operator residual explicitly. Every projection of a `validated` decision shows its front end, that front end's registration and the operator act that registered it | F62-10 |
| **D-67** | **The anonymity guarantee depends on the front end that opened the review and on the transport.** Both are named in the trusted computing base for sealing. Critics are told so before they write, with D-40's disclosure. For anonymous-role operations, operational and transport logs record the pseudonym or nothing, never the principal | F62-12 |
| **D-68** | **Obligations on anonymous records after a review closes** go uniformly to the review scope's curator, under a rule fixed when the review opens. The rule applies to every sealed-authored record of the review alike, so it reveals nothing | F62-13 |
| **D-69** | **A premise judged in another scope counts when both scopes register the same ruleset identity.** Otherwise the premise shows "assessed under another ruleset", and the route falls under "premises not established". The standing report names the scope and ruleset under which each premise was judged. A reader's scope is the claim's home scope by default | F62-04 |
| **D-70** | **A discharged assumption is not a premise that needs support.** A hypothesis introduced by a derivation and discharged by a later step of the same derivation does not need a `supported` judgment for the route to be sound; the step that discharges it is assessed like any step. Fidelity judgments (mathematics hook H1) stay a separate status: they are never cited in an inference assessment's basis, so Definition 6.0 condition 5 is unchanged | Review §7, hooks H1 and H3 |

## 3. What this record does not decide

- **It accepts neither text.** Candidate 6.3 and D1 candidate 1.3 stay proposed. Acceptance still needs independent falsification by a reviewer outside the Claude family, then the owner at Gate 0 (`AGENTS.md`).
- **Owner choices are not technical verification.** Whether the 6.3 repairs defeat the review's trajectories is for the next reviewer.
- **The review's technical repairs need no owner decision** and are the author's: S62-2, S62-3, F62-01, F62-03, F62-05, F62-06, F62-08, F62-09, F62-11, F62-14 to F62-18, §3.6 and the simplicity moves of §3.7 items 1 to 10.
- **Still open,** as before:
  - C6-6, the owner's acknowledgement of the process deviation;
  - V4-12 (iv), where an argument may stop;
  - V4-15, the versioned exchange vocabulary with SSDS;
  - type-specific propagation beyond §9.9 (TE-R11);
  - the strict profile's SC-42 rule;
  - candidate 5 reconciliation rows X2, X5, X6, X8 and X10 (change history A.11).
- **D-65 is a deployment commitment.** It adds an off-site synchronous copy of the recovery log to the first deployment profile. It implies no date.
