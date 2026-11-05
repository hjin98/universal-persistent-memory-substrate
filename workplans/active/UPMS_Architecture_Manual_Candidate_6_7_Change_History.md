# UPMS Architecture Manual, Candidate 6.7: Change History (A.17)

5 November 2026 · drafted by Claude (AI, Opus 5.5) under the product owner's delegation of the review cycle

**Status:** change history of review candidate 6.7; not architecture, decides nothing. A.1 to A.16 are in the earlier change-history files, all unchanged. This file adds A.17.

### A.17 Candidate 6.6 → candidate 6.7

Candidate 6.6 (`UPMS_Architecture_Manual_Review_Candidate_6_6.md`, SHA-256 `d0637531d39d1db6578d70bfe4c180fe59f7e6e71bc4637e415a727376179757`) and every annex are unchanged. The changes answer the independent review of candidate 6.6 and D1 1.6 (`UPMS_Candidate_6_6_Independent_Review.md`, SHA-256 `ac282071dbe79aa61262b70237a5f6e981ddb156a44e652dfb422eb1f0cc39f4`; Codex, OpenAI GPT family, the same reviewer and family as the 6.4 and 6.5 reviews). They apply **proposed** decisions D-90 to D-92 (`UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md`), which the author drafted under the owner's delegation of the review cycle; the owner has not made them, and the text marks every rule that depends on them as pending. The D1 parent moves to 1.7 (map I). The anonymous-review annex of 6.5, the checking and Slice 4 annexes of 6.3 and the mathematics annex of 6.4 are carried unchanged.

#### A.17.1 Repairs

| ID | Review finding | Repair |
| --- | --- | --- |
| C67-1 | SC66-01: coverage tested footprint records, but `N(F)` also reaches disputes of resolutions, which could live in other scopes | D-90 (pending): resolutions and disputes homed among the resolved objection's possible homes, with no tags of their own, so the footprint test covers them structurally (D1 F-4, F-7a; §5.11, §6.9, §6.10; T128) |
| C67-2 | SC66-02: F-6 selected by the current target, so a rebind dropped the objection from decisions on the earlier target | D-91 (pending): append-only bindings; `N(F)` selects by any binding; readability through the applying binding's tags (D1 Definition 2.5, F-3a, F-6, F-7a; §5.11, §6.10, §7.4; T129) |
| C67-3 | R66-01: the delta's baseline used the decision's footprint over an interval ending before its commit | The evaluation baseline is the neighbourhood of the proposed basis's footprint at the policy position, derived from the policy result (§6.9; T130) |
| C67-4 | R66-02: §15.2 named the range T01–T121 | §15.2 requires every applicable scenario of the bound inventories |
| C67-5 | Review §5 item 3: restricted grounds do not hide an objection's existence | D-92 (pending): the limitation stated in D1 §8.2 and core §1.2, §5.11 |
| C67-6 | Review §7 items 1 to 4 | §1.1 cut to current parents, with the earlier rows moved below; §1.3's chronology moved below; §9.9 cites D1 F-6 instead of paraphrasing it; §5.11's no-veto explanation cut to a pointer to D1 F-8 and §6.9 |

**Not taken, or left open:**
- **Review §7 item 5** (repeated candidate-status prose) only in part: §18's readiness statement is unchanged, because it carries the live blockers.
- **D-90 to D-92 are pending.** If the owner rejects one, its marked rules fall and the finding it answers reopens.
- **Independence:** the fourth review would again be by the same reviewer and family.
- **The Gate 0 obligations** (§18.1) are not met by any revision of this text.

**Word count:** the core body goes from 39,499 to 39,718 words; the three new scenarios and the homing and baseline rules outweigh the cuts. D1 1.7 is 11,032 words. The Gate 0 package (D1 1.7, core 6.7, anonymous-review annex 6.5) is 53,996 words.

#### A.17.2 Text moved out of candidate 6.6 (D-85; moved verbatim)

#### Candidate 6.6 §1.1, earlier predecessors and reviews

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Theory–Evidence Formulation, D1 candidate 1.6 | `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_6.md`, SHA-256 `4715b231d671becd3bfc92830047122cdd1fd6e923e0c51acc10ea29a30bb7e7` | Proposed D1 parent; its F-rules are cited as "D1 F-n". Not reviewed. Its predecessors, candidates 1 to 1.5, are unchanged; candidates 1.4 and 1.5 were reviewed NO-PASS by Codex |
| Independent review of candidate 6.5 and D1 1.5 (Codex, OpenAI GPT family) | `UPMS_Candidate_6_5_Independent_Review.md`, SHA-256 `92ddcda5861711af8cdcdbd43a1b938767ab871cadd7ab6dbfbc8a8c8f2eb515` | NO-PASS for D1 1.5 and for core 6.5 with anonymous-review annex 6.5; SC65-01, SC65-02, R65-01 to R65-03; repaired in this revision (change history A.16, C66-1 to C66-9). The same reviewer and family as the 6.4 review |
| Independent review of candidate 6.4 and D1 1.4 (Codex, OpenAI GPT-6 family) | `UPMS_Candidate_6_4_Independent_Review.md`, SHA-256 `82941db24d9213921e03b6732d4101d4a58984891bd109d6da53fc4de645d5b6` | NO-PASS for D1 1.4 and for core 6.4 with the 6.3 anonymous-review annex; SC64-01 to SC64-03, R64-01 to R64-06; repaired in candidate 6.5 (change history A.15, C65-1 to C65-10). Outside the Claude family; the same family as the proposal review |
| UPMS Architecture Manual, review candidate 6.5 | `UPMS_Architecture_Manual_Review_Candidate_6_5.md`, SHA-256 `f145b0196445b9fd5acd6625dad23183014d0defc4b2c9d176536f42651fab14` | Immediate predecessor, unchanged; changes in change history A.16 |
| UPMS Architecture Manual, review candidate 6.4 | `UPMS_Architecture_Manual_Review_Candidate_6_4.md`, SHA-256 `3c9844db1c2b99094c882f3f2bcb4e6d8cdbf9f7f9df6ab02f68f962729b2e09` | Predecessor, unchanged; changes in change history A.15 |
| UPMS Architecture Manual, review candidate 6.3 | `UPMS_Architecture_Manual_Review_Candidate_6_3.md`, SHA-256 `e6c02b0a60eead112b2a0ef78b07ff849e0006c71df25e60aeefa24686590a44` | Predecessor, unchanged; changes in change history A.14 |
| UPMS Architecture Manual, review candidate 6.2 | `UPMS_Architecture_Manual_Review_Candidate_6_2.md`, SHA-256 `0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc` | Predecessor, unchanged; changes in change history A.13 |
| UPMS Architecture Manual, review candidate 6.1 | `UPMS_Architecture_Manual_Review_Candidate_6_1.md`, SHA-256 `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a` | Predecessor, unchanged; changes in change history A.10 |
| Same-family review of candidate 6.1 and D1 1.1 (Claude Opus 5.5, fresh context) | `UPMS_Candidate_6_1_Same_Family_Review.md`, SHA-256 `f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592` | NO-PASS; SC-R1 to SC-R3, R-01 to R-20; repaired in 6.2 (change history A.12, C62-1 to C62-11). Same family, so not independent |
| Same-family review of candidate 6.2 and D1 1.2 (Claude Fable 5.1, fresh context) | `UPMS_Candidate_6_2_Same_Family_Review.md`, SHA-256 `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9` | NO-PASS; S62-1 to S62-3, F62-01 to F62-18; repaired in 6.3 (§18.3, C63-1 to C63-12). Same family, so not independent |
| Same-family review of the mathematics package (Claude Fable 5.1, fresh context) | `UPMS_Mathematics_Package_Same_Family_Review.md`, SHA-256 `ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0` | NO-PASS; SM-1 to SM-4, FM-R01 to FM-R31; core findings repaired in this revision (§18.3, C64-1 to C64-8). Same family, so not independent |
| UPMS Architecture Manual, review candidate 6 | `UPMS_Architecture_Manual_Review_Candidate_6.md`, SHA-256 `1b125d2c73aa8f78ebb28e549ef0a3a9b363b4581e0a0c4f8dadd72a8ca87062` | Predecessor of this revision, unchanged; changes in change history A.9 |

#### Candidate 6.6 §1.3, second paragraph

The proposal's own sequence (§14 step 1) asked for an outside-family review of the proposal before any manual was drafted. The owner instructed this draft before that review existed. The review (Codex, 3 November 2026) then arrived during drafting and found the proposal NO-PASS. This candidate and the D1 formulation are the kind of bounded revision it asks for (its §7 step 1), but they were not written from it from the start. A reviewer should therefore check them against each of its trajectories (its revisit condition), and defects that remain in the proposal route to it (change history A.12, C6-6).

#### Candidate 6.6 §5.11, "What never blocks means here"

**What "never blocks" means here.** An anonymous objection is never a procedural veto, its argument still counts, and an attributed judgment that independently establishes what it pointed out changes route status like any judgment (D1 F-8; D-37, D-38, D-50). Anonymous-role sessions submit no judgments (D-64). The core never refuses a decision because an objection exists or arrived after the decision was evaluated (§6.9).

#### Candidate 6.6 §9.9, Inputs paraphrase of D1 F-6

the objections applicable to the claim and its routes (D1 F-6, the one definition: the objection neighbourhood of the claim's reliance footprint, which includes route endpoints, the `renders` links and tool checks a route's effective assessment cites, the chain of sharing originals, and disputes of resolutions)

#### Candidate 6.6 §18.2, decisions D-86 to D-89

| ID | Decision | Applied in |
| --- | --- | --- |
| D-86 | Replacing an assessment never ends an objection's applicability: the reliance footprint covers every assessment effective from the decision's commit to the read and the full chain of sharing originals | D1 F-6; §6.8, §6.9, §9.9; T118, T122, T123 |
| D-87 | The coverage statement is computed over the same footprint, by configuration alone; retired objection homes still count; lineage exclusions trigger it; objections carry no restriction tags of their own | D1 F-7a; §5.11, §7.4; T124, T125 |
| D-88 | Sharing is labeled, not guarded (amends D-80); a rebind checks the new target's current readers | D1 F-7a; §5.11, §6.8, §6.10; T120, T123, T126 |
| D-89 | Fixed target shapes per relation kind; several alternatives as pairwise `favors` relations | D1 Definitions 2.6, 5.1; §9.9; T127 |
