# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.14: Change History (Map P)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of D1 candidate 1.14; not D1 authority, decides nothing. Maps B to O are in the earlier D1 change-history files, all unchanged. This file adds map P and holds the text moved out of candidate 1.13 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_13.md`, SHA-256 `58276d56f5a474401b008a4d8d87420651ead909348cc7aba8fd5724c1b21536`), which stays unchanged.

## P. Change map, candidate 1.13 → candidate 1.14

The changes answer the Codex review of candidate 1.13 and architecture candidate 6.13 (`UPMS_Candidate_6_13_Independent_Review.md`, SHA-256 `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b`; Codex, the OpenAI family of the 6.4 to 6.8 and 6.12 reviews and the 6.11 cross-check, NO-PASS) under owner decision D-100 (`UPMS_Owner_Decisions_6_13_Review_2026-11-05.md`, SHA-256 `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343`). The record lists four completions the author makes within D-100 (conditions travel at every step; a terminal basis judged unusable does not root; dependence is still read from every cited step; objections inside a chain) and three corrections that need no decision.

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.14; the 6.13 review, D-100 and candidate 1.13 added; the rows they replace moved below | — |
| §5.8 F-25 | A valid argument with no premises left is a root too, holding under its carried conditions and labeled so | D-100; SC613-01 |
| §6.1 Premises | "Established" points to Definition 6.2 | Consolidation (review §6) |
| §6.1 Roots and eligible support | Rewritten once around Definition 6.2, a finite root witness: terminal bases and valid arguments end it; every step in it must be valid for the step it supports, with its carried conditions compatible; an evidence relation judged not usable is not a terminal basis; event-rooted and "rooted in a valid argument, not in an event"; "reaches" has the base case `Y = κ`; "What rooting certifies" | D-100; SC613-01, R613-01, review §4.5 and §6 |
| §6.1 table | "no event root" becomes "no root reached"; `assessed-sound` carries the valid-argument label | D-100 |
| §6.1 Well-foundedness | Circularity sentences shortened to point at Definition 6.2 | Consolidation (review §6) |
| §6.2 F-28 | The valid-argument label is a qualifier; pointer to what a sound route certifies | D-100; review §4.5 |
| §10.3 | Case 38 says "no root witness"; case 41 narrowed; cases 42 to 47 | SC613-01, R613-01, R613-02 |
| §15 | Item 8, whether the valid-argument label is read for what it is | D-100 |
| Appendix A | Anchoring note covers 1.14 | — |

**Not taken:** the review's other §6 simplifications (chronology in §0.1, repeated inventories and inline repair ancestry, the parallel scenario descriptions in §10.3 and the core's tests) wait until this rule has passed review. No other text changed. **Word count:** 12,886 → 13,711.

## Text moved out of candidate 1.13 (D-85; moved verbatim)

#### §0.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of D1 candidate 1.12 and architecture candidate 6.12 (Codex, OpenAI family) | `workplans/active/UPMS_Candidate_6_12_Independent_Review.md`, SHA-256 `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26` | NO-PASS; SC612-01 to SC612-03, R612-01, answered here. The same reviewer and family as the reviews of 1.4 to 1.8 and the 1.11 cross-check |
| UPMS Theory–Evidence Formulation, D1 candidate 1.12 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_12.md`, SHA-256 `60c6630f198cbc94e2a1fafe9b7ed1262ba2cea5d1304de1128e2dce28c1799c` | Immediate predecessor; changes in map O |

#### §5.8 F-25, first and last sentences

**F-25 — Warrants, not actors.** Support that is circular, or that has no applicable root in events, is not a warrant, whoever produced it.

How a basis reaches a root, what a basis that cites nothing means, and when support is circular are defined in §6.1 (owner decision D-99).

#### §6.1 Premises, established

A premise is **established** for the route when it is rooted (Roots and eligible support, below) and has an effective judgment with status `supported`, or `supported-under(c')` with `c'` **compatible** with the step's conditions.

#### §6.1 Roots and eligible support

**Roots and eligible support** (owner decision D-99; F-25; Codex cross-check SC-CC611-03; Codex review SC612-01, SC612-02). A *supporting judgment* of a claim `Y` **for** an inference step `R` that has `Y` as a premise is an effective claim assessment of `Y` that could establish it for `R` by the rules above: status `supported`, or `supported-under(c')` with `c'` compatible with `R`'s conditions, counted under the ruleset rule. Its basis may cite routes of `Y` and retained events. A cited event is a **terminal basis** when it is applicable (condition 3 of Definition 6.0) and the judgment names the part of it that it checked, for example a span of its payload; a cited evidence relation is a terminal basis too, since its observation is an event that Definition 6.0 requires to be applicable. A supporting judgment whose basis cites neither a terminal basis nor a route is **rootless** and is shown with the premise.

`Y` is **rooted for** `R`, **avoiding** a set of claims `X`, at `p` when `Y ∉ X` and some supporting judgment of `Y` for `R` cites a terminal basis, or cites an inference step `R'` concluding `Y` each of whose premises is rooted for `R'` avoiding `X`. This is the least such relation over the records committed at `p`: a support cycle with no exit to a terminal basis roots nothing, and a rootless judgment or an ineligible one (under incompatible conditions, or another ruleset) never counts at any depth. It is found by one traversal of cited records, never from projected standing. A premise `P` of a step `S` with conclusion `κ` is
- **rooted** when it is rooted for `S` avoiding `{κ}`;
- **circular** when it is not rooted and **reaches** `κ`: some supporting judgment of it for `S` cites an inference step one of whose premises is `κ` or reaches `κ` for that step, so an actual cycle runs through `κ` and nothing roots `P` without it;
- **without a root** otherwise.

Reaching, like rooting, uses only eligible supporting judgments, so a rootless judgment reaches nothing. A premise is established only when it is rooted. A premise without a root is not established and never circular: the route shows "premises not established", with "rootless" when the premise's supporting judgments cite nothing and "no event root" otherwise. Rooting checks roots, eligibility and dependence on `κ`, not whether every step on the path is valid; that is each step's own status, shown one level down (F-30).

#### §6.1 table, end of the assessed-sound row

none of the above holds; it is sound under its carried conditions, which are listed |

#### §6.1 Well-foundedness, circularity sentences

so it is computed in one pass, with no fixed point over standing. **Circularity is judged per derivation, by actual dependence** (same-family review R-02; owner decision D-99; Codex cross-check SC-CC611-03; Codex review SC612-01): an inference step `S` is **circular** when some premise of it is circular (Roots and eligible support, above). A premise with one eligible rooted support that avoids `κ` keeps `S` non-circular, so a third party's converse step cannot break a well-founded route; a rootless alternative, a cycle that never reaches an event, or a judgment under incompatible conditions never clears a dependence on `κ`. An empty basis is never a cycle.

#### §6.2 F-28, qualifiers sentence

Each true predicate is shown with the routes that make it true and their qualifiers: the alternative and model of a relative support, the purpose of an adequacy, and the carried conditions.

#### §10.3 cases 38 and 41

38. Claims `P` and `Q` support each other through two steps, neither supported by any event, and a valid step concludes `K` from `P`: `P` has no event root, so the step shows "premises not established", is not circular, and `has-sound-support(K)` is false (§6.1, F-25; SC612-01).

41. A route with no assessment, or with assessments none of which is effective: "unassessed" or "assessed, not effective", never "broken" (§6.1; SC612-03).
