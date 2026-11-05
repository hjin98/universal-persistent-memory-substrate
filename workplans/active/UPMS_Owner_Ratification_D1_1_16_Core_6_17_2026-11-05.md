# UPMS Owner Ratification of D1 1.16 and Core 6.17 with Annex 6.7, 5 November 2026

5 November 2026 · ratified by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · ratification record

**This is the product owner's ratification.** The author asked: "Ratify D1 1.16 and core 6.17 with annex 6.7?" The owner answered **"Ratify them"** (5 November 2026). Before answering, the owner was told that every review since 6.12 was by the same Codex reviewer, which had read the earlier rounds; that Gate 0 still needs pilot languages, a deployment profile, the D4 and executable test specifications, and runtime, storage, key-management, backup and restore feasibility; and that ratifying would make these texts the accepted ones.

## 1. Ratified texts

Each is ratified at exactly this hash; any other revision needs its own review and ratification.

| File | SHA-256 | Authority |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Accepted-current D1 authority for UPMS: the theory–evidence formulation |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` | Accepted-current D3 architecture for UPMS: the core |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Accepted-current D3 architecture: the anonymous-review annex, read with core 6.17 as its §1 says |

The texts keep their file names and their own status lines, which predate this record ("not accepted, not ratified"); they are frozen and are not edited (`AGENTS.md`). This record is what changes their status.

## 2. Evidence the owner relied on

| File | SHA-256 | Result |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_17_Independent_Review.md` | `b31cf91f8581cda5929c7dff7ff868a8924c7106e0a0e8d157e23ebbf3835029` | Codex: PASS for Gate 0 entry for D1 1.16 and core 6.17 with annex 6.7; the revision is editorial and lost nothing material |
| `workplans/active/UPMS_Candidate_6_16_Independent_Review.md` | `727afb383999fdd89c1f4103041be2a4bb86104d62855690059d34d9aa17afa4` | Codex: PASS for core 6.16 with annex 6.7 and for D1 1.15 |
| `workplans/active/UPMS_Candidate_6_15_Independent_Review.md` | `195d27b21f2917e010a732bb15740b43ea617d7a3349421ba5b159f38de7f251` | Codex: PASS for D1 1.15 |

These are technical reviews from outside the Claude family (OpenAI GPT family). They were not blind, and they are documentary: no implementation or acceptance scenario was executed.

## 3. What this ratification does not do

- **Gate 0 is not passed.** Core §16 and §18.1 still require named pilot languages and profile, a bounded D4 specification and executable evidence specification, and runtime, storage, KMS, backup and restore feasibility. Nothing is implementation-qualified.
- **Not ratified:** the checking and Slice 4 annexes of 6.3, the mathematics annex of 6.4 and the mathematics D1 candidate 1.1 (each to be reviewed at its own boundary, D-56); the proposal v0.1, which stays a direction input; every earlier candidate.
- **Owner decisions** D-1 to D-100 stand as recorded; this record adds none and changes none.
- **Product inspectability surfaces** that D1 §11 and core §17.2 mark beyond the requested deliverable are not accepted by this record.
- **Open items** stay open: D1 §15 and core §18.1 and §18.2 ("Still open").
