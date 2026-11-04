# UPMS Architecture Manual, Candidate 6.4: Change History (A.14)

3 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** change history of review candidate 6.4; not architecture, decides nothing. A.1 to A.13 are in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md` (SHA-256 `c2a7ded8dd9198a92989c81ca8216718b7a3af8ff2875bf48cce60c40775e571`), unchanged. This file adds A.14.

### A.14 Candidate 6.3 → candidate 6.4

Candidate 6.3 and its annexes are unchanged. The anonymous-review, checking and Slice 4 annexes of 6.3 are carried into 6.4 as they are. The changes below answer the same-family review of the mathematics package (`UPMS_Mathematics_Package_Same_Family_Review.md`, SHA-256 `ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0`) under owner decisions D-71 to D-78. The D1 parent moves to 1.4 (its Appendix F) and the mathematics D1 text to 1.1 (its Appendix B).

| Where | Change | Finding or decision |
| --- | --- | --- |
| §1, §1.1 | Revision 6.4; D1 parent 1.4; 6.3, the review and the decision record as inputs; the package names the 6.3 annexes and the 6.4 mathematics annex | — |
| §4.3 | Inspection only from humans; fidelity records agent and authorship; designation guards and labels; operations for the annex records with derivation integrity checks; `register_tool` | SM-3, SM-4, FM-R15, FM-R16; D-72, D-73, D-75, D-77 |
| §5 opening | H7 bounded to exactly four kinds; models are symbol contexts | FM-R17; simplicity |
| §5.3, §5.4 | Fidelity and inspection results; `assessor_is_agent`, `assessor_authored_target`; tool registrations among controls | D-73, D-77 |
| §5.5 | Bindings as Meaning relations; one derivation per step; carried conditions and discharges computed per conclusion | FM-R19, SM-2, SM-3; D-71, D-72 |
| §5.11, §5.12 | Objections on other relations and observations; cause `rendering_diverges` | FM-R13, SM-1; D-74 |
| §7.6 | The inquiry ruleset covers fidelity and inspection | FM-R14 |
| §9.9 | Carried conditions listed; objections on cited `renders` links and tool checks challenge the route | SM-1, SM-2, SM-3 |
| §9.11 | A divergence is a traversal cause | SM-1; D-74 |
| §12.3 | Parses and screening cues named | FM-R25 |
| §15, §16 | T98 extended; T116, T117 new, in Slice 3 | — |
| §18 | D-71 to D-78; C64-1 to C64-8 | — |
| Mathematics annex 6.4 | Rewritten against core 6.4 and mathematics D1 1.1: hooks table; records (context on expressions, bindings as relations, models as contexts, environment identity, depth `full`, no `faithful_under`); parsing and dimensional screening later (D-76); carried conditions and discharges; self-assessed and agent-assessed labels; tool checks cited in judgment bases; divergence; brief subject and mandatory part; MA7; TM13 to TM18; slices | SM-1 to SM-4, FM-R18 to FM-R24; D-71 to D-78; simplicity |

**Not taken from the review:** collapsing inspection depth to a boolean (simplicity item 3); depth stays as a label, renamed `full`, as the owner accepted.

**Word count:** the core body grows by about 900 words, to about 38,300; the Gate 0 package (D1 1.4, core and the 6.3 anonymous-review annex) is about 53,100 words.
