# UPMS Architecture Manual, Candidate 6.10: Change History (A.20)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.10; not architecture, decides nothing. A.1 to A.19 are in the earlier change-history files, all unchanged. This file adds A.20.

### A.20 Candidate 6.9 → candidate 6.10

Candidate 6.9 (`UPMS_Architecture_Manual_Review_Candidate_6_9.md`, SHA-256 `80f183a6345afbe4a682b83e4f8eb5d3346e5fd106e2b05a8857e8ff0b7c7a6d`) and every annex are unchanged. The changes answer the independent review of candidate 6.9 and D1 1.9 (`UPMS_Candidate_6_9_Independent_Review.md`, SHA-256 `6c46d9aa8b6179ad8b91df4cfbcfa51cf3ffbe2aca257ed555c902659bfd2b12`; Gemini 3.8 Flash (High), Gemini family, through the Antigravity CLI, the first review of these texts by that family (D-96)) and apply **proposed** decision D-97 (`UPMS_Proposed_Decisions_6_9_Review_2026-11-05.md`), which the owner has not made. The D1 parent moves to 1.10 (map L). The review cites a "D1 §0.3" and quotes a falsification criterion that D1 1.9 does not contain; its SC69-02 trajectory stands without them, and the repair does not rely on them.

#### A.20.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C610-1 | SC69-01: F-7 did not select an objection resolved at another target, so the label T129 required could not appear | D1 F-7 selects objections open for a footprint record and shows them with the label; §4.4 and TE-04 cite F-7 instead of restating it (T129) |
| C610-2 | SC69-02: a resolution assessing K2 left K1's standing showing sound support | D-97 (pending): settled for standing only at the assessed target; workflow closed everywhere (D1 Definition 2.5, §6.1, F-28; §5.11, §6.10; T129) |
| C610-3 | SC69-03: F-4 never cleared a disputed state | D1 F-4: disputed only while a dispute is open; history keeps the earlier state (§6.10; T134) |
| C610-4 | R69-01: F-28's "disputed objection" was ill-typed | F-28 uses "open for κ" |
| C610-5 | R69-02: cross-scope rebinding was promised but impossible for objections homed in ordinary scopes | D1 F-3b and §6.10 state the review-scope condition and the new-objection route |
| C610-6 | R69-03: T128 kept a 6.8 own-record clause that no longer fit | T128 rewritten; T134 added |

**Not taken, or left open:**
- **D-97 is pending.** If the owner keeps D-94's first clause literally, Definition 2.5's "open for", F-28 and T129 revert, and `K1` may show sound support with only the label to warn.
- **Review §7's simplifications** were not taken in this revision.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 39,994 to 40,260 words. D1 1.10 is 11,649 words. The Gate 0 package (D1 1.10, core 6.10, anonymous-review annex 6.5) is 55,155 words.

#### A.20.2 Text moved out of candidate 6.9 (D-85; moved verbatim)

#### Candidate 6.9 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.8 and D1 1.8 (Codex, OpenAI GPT family) | `UPMS_Candidate_6_8_Independent_Review.md`, SHA-256 `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad` | NO-PASS for D1 1.8 and for core 6.8 with anonymous-review annex 6.5; SC68-01 to SC68-03, R68-01; repaired in this revision (change history A.19, C69-1 to C69-6). The same reviewer and family as the 6.4 to 6.7 reviews |
| UPMS Architecture Manual, review candidate 6.8 | `UPMS_Architecture_Manual_Review_Candidate_6_8.md`, SHA-256 `8dad8d5f50e9139e536cb766dab8c9806af2ce884f1826d2dba1ac6c77b73f1f` | Immediate predecessor, unchanged; changes in change history A.19. Earlier predecessors and reviews are listed with their hashes in A.17 to A.19 |

#### Candidate 6.9 §15.1, T128 and T129

| T128 | Resolution and dispute homes (SC66-01): objection O to claim K is homed in K's scope H; a `resolution` decision for O homed in scope Q, which is not a possible home of K's objections, is refused, as is one with a restriction tag of its own; the same decision homed in H commits; a dispute O2 of it homed in Q is refused and in H is accepted; reader P who reads H and every objection home registered for H, and reads the resolution only through an own-record entitlement, sees O2; a reader who does not read a registered home of H sees the coverage statement, identically whether or not O2 exists (D1 F-4, F-7a; §5.11, §6.9; D-94) |
| T129 | Target history (SC66-02, SC68-01): decision D1 cites K1, which has objection O; K1 is revised to K2 and O carried; O's author rebinds it to K2; decision D2 cites K2; both have O in their applicable sets, each projection naming the target through which it applies and O's target history; a resolution whose judgment assessed K2 shows O resolved on both, and D1's projection says "resolved by assessment at K2"; the same holds when K1 is withdrawn and O rebound to a restating claim in another scope of which O's home is a possible home; a rebind to a target of which O's home is not a possible home is refused (D1 Definition 2.5, F-3, F-3a, F-6; §5.11, §6.10; D-94) |
