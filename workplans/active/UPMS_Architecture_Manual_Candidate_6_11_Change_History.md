# UPMS Architecture Manual, Candidate 6.11: Change History (A.21)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.11; not architecture, decides nothing. A.1 to A.20 are in the earlier change-history files, all unchanged. This file adds A.21.

### A.21 Candidate 6.10 → candidate 6.11

Candidate 6.10 (`UPMS_Architecture_Manual_Review_Candidate_6_10.md`, SHA-256 `4e396576403ba1fe445e59888647d8af01c952c22bc61207f9a1fdedaf549ebd`) and every annex are unchanged. The changes answer the independent review of candidate 6.10 and D1 1.10 (`UPMS_Candidate_6_10_Independent_Review.md`, SHA-256 `2645faef1aed615b859decb02074724c0175ebb4bed9fb689eb4141e3b8258fb`; Gemini 3.8 Flash (High), the same family as the 6.9 review) and keep applying **proposed** decision D-97, which the owner has not made. The D1 parent moves to 1.11 (map M). Both findings the review calls Serious were introduced by the author's 6.10 repair: the new "open for" test was not applied to disputes, and four consumers kept the old test.

#### A.21.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C611-1 | SC610-01: a resolved dispute stayed open for the claim forever | D1 Definition 2.5: a dispute applies through the resolution it disputes; "open in" a view defined once (T134; D1 stress case 31) |
| C611-2 | SC610-02: T129 required D2 to show a settled objection that F-7 does not select | F-7 lists open objections only, settled ones staying in history; T129 rewritten |
| C611-3 | R610-01: D1 F-6, F-8, core §10.5.1 and MV1 kept the old "unresolved or disputed" test | Each uses "open in" (D1 Definition 2.5); the author searched both texts for the old test and found no other use |
| C611-4 | R610-02: "for scientific standing" made the test seem not to govern decisions | Definition 2.5 lists every consumer of "open in" |

**Not taken, or left open:**
- **D-97 is pending,** now including the dispute clause the review recommends.
- **Review §7's simplifications** were not taken in this revision.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 40,260 to 40,338 words. D1 1.11 is 11,812 words. The Gate 0 package (D1 1.11, core 6.11, anonymous-review annex 6.5) is 55,396 words.

#### A.21.2 Text moved out of candidate 6.10 (D-85; moved verbatim)

#### Candidate 6.10 §1.1 rows

| Input | Identity | Role |
| --- | --- | --- |
| Independent review of candidate 6.9 and D1 1.9 (Gemini 3.8 Flash, Gemini family) | `UPMS_Candidate_6_9_Independent_Review.md`, SHA-256 `6c46d9aa8b6179ad8b91df4cfbcfa51cf3ffbe2aca257ed555c902659bfd2b12` | NO-PASS for D1 1.9 and for core 6.9 with anonymous-review annex 6.5; SC69-01 to SC69-03, R69-01 to R69-03; repaired in this revision (change history A.20, C610-1 to C610-6). The first review by a Gemini-family model |
| UPMS Architecture Manual, review candidate 6.9 | `UPMS_Architecture_Manual_Review_Candidate_6_9.md`, SHA-256 `80f183a6345afbe4a682b83e4f8eb5d3346e5fd106e2b05a8857e8ff0b7c7a6d` | Immediate predecessor, unchanged; changes in change history A.20. Earlier predecessors and reviews are listed with their hashes in A.17 to A.20 |

#### Candidate 6.10 §15.1, T134

| T134 | Dispute lifecycle (SC69-03): O is resolved by R; dispute U of R makes every projection that shows O read "resolved by assessment, disputed" and routes through K challenged; U's author withdraws U: R is no longer disputed and the routes are no longer challenged by O; a view at a position before the withdrawal still shows R disputed; the same holds when U is resolved (D1 F-4, F-31; §6.10) |
