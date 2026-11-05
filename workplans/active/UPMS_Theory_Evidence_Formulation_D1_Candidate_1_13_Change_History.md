# UPMS Theory–Evidence Memory: D1 Formulation, Candidate 1.13: Change History (Map O)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of D1 candidate 1.13; not D1 authority, decides nothing. Maps B to N are in the earlier D1 change-history files, all unchanged. This file adds map O and holds the text moved out of candidate 1.12 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_12.md`, SHA-256 `60c6630f198cbc94e2a1fafe9b7ed1262ba2cea5d1304de1128e2dce28c1799c`), which stays unchanged.

## O. Change map, candidate 1.12 → candidate 1.13

The changes answer the Codex review of candidate 1.12 and architecture candidate 6.12 (`UPMS_Candidate_6_12_Independent_Review.md`, SHA-256 `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26`; Codex, the OpenAI family of the 6.4 to 6.8 reviews and the 6.11 cross-check, NO-PASS). They stay inside owner decisions D-97 to D-99: the review's findings concern how the author wrote D-99, and the repair makes F-25's "applicable root in events" and D-99's "actual cycle" exact. No owner decision is added.

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.13; the 6.12 review and candidate 1.12 added; the rows they replace moved below | — |
| §6.1 Premises, Roots and eligible support | "Grounded basis" replaced by "rooted for a step, avoiding a set": the least relation reaching a terminal basis through eligible supporting judgments at every depth. A premise is rooted, circular or without a root; only a rooted premise is established | SC612-01, SC612-02 |
| §6.1 table | "no event root" joins the premise list; the all-negative branch of `broken` needs at least one effective assessment | SC612-01, SC612-03 |
| §6.1 Well-foundedness | Circularity defined through the premise classes; rootless alternatives, unrooted cycles and ineligible judgments clear nothing | SC612-01, SC612-02 |
| §10.3 | Case 32 says no decision is refused; cases 38 to 41 | R612-01, SC612-01 to SC612-03 |
| Appendix A | Anchoring note covers 1.13 | — |

No other text changed. **Word count:** 12,553 → 12,886.

## Text moved out of candidate 1.12 (D-85; moved verbatim)

#### §0.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of D1 candidate 1.11 and architecture candidate 6.11 (Gemini 3.8 Flash, Gemini family) | `workplans/active/UPMS_Candidate_6_11_Independent_Review.md`, SHA-256 `9dc7622e2e81393fcb039e1076dbbfbb62f43b1d870047658eb50213f0742ab4` | PASS conditional on D-97; R611-01. Overturned by the cross-check below |
| Cross-check of D1 candidate 1.11 and architecture candidate 6.11 (Codex, OpenAI family) | `workplans/active/UPMS_Candidate_6_11_Codex_Cross_Check.md`, SHA-256 `068d3f6365616253ad2558ffa86c2f13853e64ed07c938924cf3f87cd67c0fa3` | NO-PASS; SC-CC611-01 to SC-CC611-03, answered here. The same reviewer and family as the reviews of 1.4 to 1.8 |
| UPMS Theory–Evidence Formulation, D1 candidate 1.11 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_11.md`, SHA-256 `32bb7a7a6b3d0ea93cc0210a0aedbf9725531c3f0b35e7929bc9d17089c2830e` | Immediate predecessor; changes in map N |

#### §6.1, grounded-basis paragraph

**Grounded basis and terminal events** (owner decision D-99; Codex cross-check SC-CC611-03). A *supporting judgment* of a premise `P` is an effective claim assessment of `P` with status `supported` or `supported-under(c')`. Its basis may cite routes of `P` and retained events. A cited event is a **terminal basis** when it is applicable (condition 3 of Definition 6.0) and the judgment names the part of it that it checked, for example a span of its payload: support that reaches it has an applicable root in events, and nothing beyond the event is followed (F-25). A basis is **grounded** when it cites at least one terminal basis or route. A supporting judgment whose basis cites neither is **rootless**: it is shown with the premise, it establishes nothing, so a human's assertion is never a warrant (F-25), and a premise whose supporting judgments are all rootless is not established. Whether a cited route is itself sound is that route's own status, shown one level down (F-30); it is not recomputed into this route.

#### §6.1 table, start of the broken row

| **broken** | every effective assessment of the route is negative

#### §6.1 Well-foundedness, circularity sentences

so it is computed in one pass, with no fixed point over standing. **Circularity is judged per derivation, by actual dependence** (same-family review R-02; owner decision D-99; Codex cross-check SC-CC611-03). For a conclusion `κ`, a claim `Y` **depends on** `κ` at `p` when `Y = κ`, or when `Y` has a supporting judgment with a grounded basis and everything that each such judgment cites is an inference step one of whose premises depends on `κ`. This is the least such relation over the records committed at `p`, so it is found by one traversal from `κ`, and a cycle that does not pass through `κ` creates no dependence on it. An inference step `S` with conclusion `κ` is **circular** when some premise of `S` depends on `κ`. A premise with one terminal basis, one cited evidence relation, or one cited step none of whose premises depends on `κ` keeps `S` non-circular, so a third party's converse step cannot break a well-founded route. A premise with no grounded supporting judgment never makes `S` circular: it is not established (Premises above), and an empty basis is never a cycle.
