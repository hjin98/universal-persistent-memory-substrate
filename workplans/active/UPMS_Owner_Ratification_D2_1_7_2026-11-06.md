# UPMS Owner Ratification of D2 1.7, 6 November 2026

6 November 2026 · ratified by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · ratification record

**This is the product owner's ratification.** The author asked: "Ratify D2 1.7 at its reviewed hash?" The owner answered **"Ratify D2 1.7"** (6 November 2026). Before answering, the owner was told:
- that all four Codex reviews of D2 1.4 to 1.7 were by the same reviewer, which had read the earlier rounds, so none was blind, and that the reviews are documentary: nothing was executed;
- that the owner would be accepting a strict rule: one 5% error budget for all qualification, each attempt testing everything it claims at a single level and passing all or nothing, the level halving with each attempt, so that a first attempt at a 1% limit needs about 555 questions, each retry more, and Codex lists sizes up to 7,629 by the 100th attempt;
- that which class, language and workload claims the pilot must establish is still the owner's to decide, with the qualification plan after calibration, and that no evaluation value is set.

## 1. Ratified text

Ratified at exactly this hash; any other revision needs its own review and ratification.

| File | SHA-256 | Authority |
| --- | --- | --- |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_7.md` | `620eff437d91e2db0a15cba15401edca83b173b50edd5a4023e9f0ea5e6858ac` | Accepted-current D2 for UPMS, for retrieval only (D1 1.20 §9) |

It replaces D2 1.3 (SHA-256 `84e61686c74e2a07a8eace77b12afa6bb4789e334634928d68c64508b15c84f6`) as accepted-current. Its own status line ("PROPOSED revision … Not accepted, not ratified") predates this record; the text is frozen and is not edited (`AGENTS.md`). This record is what changes its status.

**Compatibility with the retained parents.** D1 1.20, core 6.21 and its retrieval-and-scale annex stay accepted-current under `UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md` (SHA-256 `ff6a4493b4cf44f55d8488bb22ae9ea9bbe096ea66db0afa08e60847c0c29866`) and are not edited. Where they cite the D2 retrieval method candidate 1.3, they are read as citing D2 1.7. Every section they cite keeps its number in 1.7, whose only new heading is §10.6; the cited sections are unchanged in substance except §§7.3 and 10.3, whose values are now set after calibration and whose requirements §10.6's bounds decide, and §§9.1 and 14, which add planted-fact references, oracle isolation and the operational reopening rule; §0 updates parents and status. The 1.7 review found no contradiction with these parents (its §5).

## 2. Evidence the owner relied on

| File | SHA-256 | Result |
| --- | --- | --- |
| `workplans/active/UPMS_D2_1_7_Independent_Review.md` | `9c6e96ad98f0fe13376c7c64552785d8eb24cb9d86f79e3b139655e54395a7c8` | Codex: PASS for ratification of D2 1.7 with its change maps from 1.3; no Serious Challenge; F621-01 retained, open and nonblocking |
| `workplans/active/UPMS_Owner_Decisions_Pilot_Languages_Evaluation_2026-11-05.md` | `2f7d25814aaa045e95902a13d6e5feaaf8be418ac27b293e4627e90f43d77e58` | D-121 and D-122, which D2 1.7 realizes |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md` | `132a795d1c0c710b3514576c85bc9ec4dbdb52ccb901f22c09634e731c156ea9` | Edits 1.3 → 1.4, reconstructed byte for byte by Codex |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_5_Change_History.md` | `77ef58606eeea4dc3a4cb55344eedbf6914ab34056067dbacc77f76d836eb8a4` | Edits 1.4 → 1.5, likewise |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_6_Change_History.md` | `66e93d7dd13455d9700d00f4153188d599b9d172c88b53d23c296e25f7d84583` | Edits 1.5 → 1.6, likewise |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_7_Change_History.md` | `1beb0165eea13595e583f3ff25d5d04d6881a7b9b133861103d8b5489a90d5c5` | Edits 1.6 → 1.7, likewise |

The NO-PASS reviews of D2 1.4 to 1.6 are indexed in `workplans/README.md`. These are technical reviews from outside the Claude family (OpenAI GPT family), not blind and documentary.

## 3. What this ratification decides and does not decide

- **Decided with it:** the product-wide qualification procedure of D2 1.7 §10.6: one error schedule over all qualification attempts, each joint and all-or-nothing, with the 95% assurance covering the variant finally selected (the 1.7 review's question 3).
- **Gate 0 is not passed.** Core §16 and §18.1 still require a bound profile, a bounded D4 specification and executable evidence specification, and runtime, storage, KMS, backup and restore feasibility. The pilot languages are now named (D-121). Nothing is implementation-qualified.
- **Not set:** every value D2 proposes (§§7.3, 10.3, 10.6, 13; annex R15), including the error schedule's default `α_s = α / 2^s`, remains a proposal to be set by the owner after calibration and before qualification (D-120, D-122); which class, language and workload-family claims the pilot must establish is the owner's to decide with the qualification plan.
- **Unchanged:** the ratification of D1 1.20, core 6.21, its retrieval-and-scale annex and annex 6.7; owner decisions D-1 to D-122.
- **Open items** stay open: D1 §15, D2 §14 (now with question 4, affordability of the qualification sizes), core §18.1 and §18.2, annex R18, and F621-01.
