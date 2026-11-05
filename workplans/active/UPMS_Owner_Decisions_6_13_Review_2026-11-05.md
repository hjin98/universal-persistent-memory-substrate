# UPMS Owner Decision on the Candidate 6.13 Review, 5 November 2026 (D-100)

5 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**This is an owner decision.** The Codex review of candidate 6.13 and D1 1.13 (NO-PASS) found that an inference step with no premises let a claim count as rooted without any event (SC613-01), and said that if conditional arguments are an exception to F-25's event-root requirement, the owner must decide that exception explicitly. The author recommended a rule and asked: "Adopt my rule for conditional arguments and chain validity?" The owner answered **"Adopt the rule"** (5 November 2026). The recommendation is quoted in §2 as the author put it; the decision text is the author's wording of it, written after the answer, and binds only as far as it says what the owner was shown.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_13_Independent_Review.md` | `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b` | Codex review: NO-PASS; SC613-01, R613-01, R613-02; its §4.5 raises the chain-validity boundary and its §5 item 1 asks for this decision |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_13.md` | `58276d56f5a474401b008a4d8d87420651ead909348cc7aba8fd5724c1b21536` | Its §6.1 "Roots and eligible support" and F-25 are what this decision changes |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_13.md` | `d2e59a70e3b7e746a5244cef4d97fd128019c5c039dc1c7ea390f2c22be324ca` | Its §5.3, §9.9, TE-07 and T135 consume that rule |
| `workplans/active/UPMS_Owner_Decisions_6_11_Review_2026-11-05.md` | `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295` | Owner decision D-99 (terminal warrants), extended here |
| `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Owner decision D-70 (discharged assumptions), kept |
| `workplans/active/UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Owner decision D-71 (open assumptions and model relations are conditions), kept |

## 2. Decision

| ID | Decision | Recommendation the owner accepted | Answers |
| --- | --- | --- | --- |
| **D-100** | **Root witnesses.** A chain of support that establishes a premise passes only through inference steps that have an effective positive inference assessment and no effective negative one; a step nobody has assessed roots nothing. The chain ends at a terminal basis of D-99, or at a step so assessed that has no premises left to establish once discharged hypotheses and carried conditions are set aside (D-70, D-71). A conclusion whose chain ends at such a step holds only under that step's carried conditions and is labeled "rooted in a valid argument, not in an event". `assessed-sound` then means that each premise has a chain every step of which was assessed valid. This extends F-25 and D-99 with the valid-argument end; D-99's rules for a basis that cites nothing and for circularity are unchanged | "one rule for what a chain of support must look like. **Steps:** every step along the chain must have an attributed judgment that it is valid, and no judgment that it is invalid. **Ends:** the chain must end at a source event, or at a step judged valid that has no premises left to prove. **Labeling:** a conclusion that ends at such a step holds only under that step's stated conditions, and is labeled "rooted in a valid argument, not in an event". This keeps D-70 and D-71. **What it closes:** a bare assertion no longer counts, since an unassessed step roots nothing. It also answers Codex's other point: "assessed-sound" would no longer pass through a step someone has judged invalid." The alternative shown: "to require an event for everything, which would leave proofs from definitions unable to support anything else" | SC613-01; the review's §4.5 and §5 items 1 and 4 |

**Completions the author makes within D-100** (no further decision; the owner may overrule any of them):
- **Conditions travel at every step.** "Holds only under that step's stated conditions" is applied to every step of a chain, not only the last: a step counts in a chain only where each of its carried conditions is compatible with the conditions of the step it supports, by D1 §6.1's existing compatibility rule (D-69, D-82).
- **A terminal basis judged unusable does not root.** "No judgment that it is invalid" is applied to a cited evidence relation as well: one with an effective negative evidential assessment is not a terminal basis. A directly cited event needs no assessment of its own, as D-99 says.
- **Dependence is still read from every cited step.** Circularity stays D-99's actual dependence: a premise reaches the conclusion through any step its supporting judgments cite, assessed or not, while only steps assessed valid can root it.
- **Objections inside a chain.** An open objection to a step inside a chain does not take the step out of it; under D-98 objections change challenge state, not assessments. The objection is shown one level down.

**Corrections that need no decision** (the author's to make):
- immediate self-dependence: a premise that is the conclusion itself reaches it (R613-01);
- D1 stress case 41 says only that an empty set of effective assessments never makes a route `broken` through the all-negative branch (R613-02);
- the rooting rule is written once, as a definition of a finite root witness, in place of the parts repeated across "Premises", "Roots and eligible support" and "Well-foundedness" (the review's §6).

## 3. What this record does not decide

It accepts no text. D1 1.14 and core 6.14, which apply this decision, need independent review outside the Claude family and the owner's ratification. D-37 to D-99 stand as recorded. The wording of D-100 above is the author's statement of the accepted recommendation; if it says more than the owner was shown, the quoted recommendation governs.
