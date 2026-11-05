# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.15: Change History (Map Q)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of D1 candidate 1.15; not D1 authority, decides nothing. Maps B to P are in the earlier D1 change-history files, all unchanged. This file adds map Q and holds the text moved out of candidate 1.14 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_14.md`, SHA-256 `c163a0999e1cff6c851dff5b1200e21677807ffd209947ce65011738a1554dcb`), which stays unchanged.

## Q. Change map, candidate 1.14 → candidate 1.15

The changes answer the Codex review of candidate 1.14 and architecture candidate 6.14 (`UPMS_Candidate_6_14_Independent_Review.md`, SHA-256 `ecb8d25b7f1254b168ee1563eb9d4930afe2a70e015d9aee438d7d1b8ec7a7a2`; Codex, the OpenAI family of the 6.4 to 6.8, 6.12 and 6.13 reviews and the 6.11 cross-check, NO-PASS). They stay within owner decision D-100 (`UPMS_Owner_Decisions_6_13_Review_2026-11-05.md`, SHA-256 `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343`). SC614-01 found that the author's first completion within D-100, "conditions travel at every step", carried a hypothesis past the step that discharges it, which broke D-70 and D-72 although the recommendation the owner accepted said "This keeps D-70 and D-71". The repair corrects that completion so it keeps them: a step's context includes the hypotheses it discharges, and a condition stops travelling where a step discharges it. The decision record is unchanged; its first completion is read as corrected here.

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.15; the 6.14 review and candidate 1.14 added; the rows they replace moved below | — |
| §6.1 Premises | A step's **context**: its stated conditions, its conclusion's carried conditions and the hypotheses it discharges; premise judgments and witness steps are checked against it | SC614-01 |
| §6.1 Roots and eligible support | Supporting judgments and "valid for" use the consuming step's context; a step's own discharged hypotheses are not its conditions; a condition travels until a step discharges it, and a bypass keeps it (D-72) | SC614-01 |
| §10.3 | Case 35 says "terminal basis"; case 36 names the intermediate assessment and its contrasts; case 44 uses the context; cases 48 to 50 | R614-01, SC614-01 |
| Appendix A | Anchoring note covers 1.15 | — |

**Not taken:** the review's §6 simplifications, including one scenario inventory shared by §10.3 and the core's tests, wait until the rooting rule has passed review. No other text changed. **Word count:** 13,711 → 14,054.

## Text moved out of candidate 1.14 (D-85; moved verbatim)

#### §0.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of D1 candidate 1.13 and architecture candidate 6.13 (Codex, OpenAI family) | `workplans/active/UPMS_Candidate_6_13_Independent_Review.md`, SHA-256 `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b` | NO-PASS; SC613-01, R613-01 and R613-02, answered here. The same reviewer and family as the reviews of 1.4 to 1.8 and 1.12 and the 1.11 cross-check |
| UPMS Theory–Evidence Formulation, D1 candidate 1.13 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_13.md`, SHA-256 `58276d56f5a474401b008a4d8d87420651ead909348cc7aba8fd5724c1b21536` | Immediate predecessor; changes in map P |

#### §6.1 Premises, establishment and compatibility

A carried condition is never shown as established, and never silently dropped. A premise is **established** for the route when it is rooted (Definition 6.2, below), which needs an effective judgment of it with status `supported`, or `supported-under(c')` with `c'` **compatible** with the step's conditions. Compatibility is established only when `c'` and the step cite the same condition record by identity, or an effective comparability judgment (§5.7) states that `c'` covers the step's conditions and no other

#### §6.1 Roots and eligible support, supporting judgment and "valid for"

`supported-under(c')` with `c'` compatible with `R`'s conditions, counted under the ruleset rule. Its basis may cite

and each of its conditions, stated (Definition 2.7) or carried, is compatible with `R`'s conditions by the compatibility rule above. A step nobody has assessed, a step judged invalid and a disputed step are valid for no step. Because each step of a chain must meet the conditions of the step it supports, a condition carried anywhere in a chain must be covered at the route's own step (D-100).

#### §10.3 cases 35, 36 and 44

35. A premise supported only through a converse step from the conclusion: the step is circular and broken; a further supporting judgment of the premise that cites an independent evidence relation or event makes it non-circular (§6.1; D-99; R-02).

36. A premise supported through a step whose own premise is grounded in an event and is also supported through a step from the conclusion: it does not depend on the conclusion, so the step is not circular (§6.1; D-99).

44. As case 43, where `Z` carries an undischarged hypothesis `h`: `Z` counts for the step concluding `K` only when that step carries `h` too or an effective comparability judgment states that `h` covers its conditions; otherwise `P` has no root (§6.1; D-70, D-71, D-100).
