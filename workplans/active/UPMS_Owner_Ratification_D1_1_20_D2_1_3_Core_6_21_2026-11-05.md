# UPMS Owner Ratification of D1 1.20, D2 1.3 and Core 6.21 with Its Annexes, 5 November 2026

5 November 2026 · ratified by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · ratification record

**This is the product owner's ratification.** The author asked: "Ratify D1 1.20, D2 1.3 and core 6.21 with both annexes?" The owner answered **"Ratify them"** (5 November 2026). Before answering, the owner was told:
- that every Codex review of this package (6.18 to 6.21) was by the same reviewer, which had read the earlier rounds, so none was blind, and that the reviews are documentary: nothing was executed;
- that D2 1.3 charges a partial answer against the largest number of parts one response could settle within the request's budget, so that answering two cheap parts is preferred to answering one expensive part, and that Codex asked the owner to accept this knowingly (6.21 review §4.3 and §8 item 1);
- that the numerical values D2 proposes (error and usefulness limits, budgets, the unknown-reference tolerance, partial-answer credit, workload and lifecycle assumptions) are placeholders still to be set before any measurement;
- that Gate 0 still needs pilot languages, a bound profile, the D4 and executable test specifications, and runtime, storage, KMS, backup and restore feasibility.

## 1. Ratified texts

Each is ratified at exactly this hash; any other revision needs its own review and ratification.

| File | SHA-256 | Authority |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20.md` | `d8bc3558d64e627b739189a6a92d1e42c4c2df2d47dd9bc42b927ad9dec72eab` | Accepted-current D1 for UPMS: the theory–evidence formulation with §16, answers from memory |
| `workplans/active/UPMS_Retrieval_Method_D2_Candidate_1_3.md` | `84e61686c74e2a07a8eace77b12afa6bb4789e334634928d68c64508b15c84f6` | Accepted-current D2 for UPMS, for retrieval only (D1 1.20 §9) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_21.md` | `e1f28af693ae8805acf2ed2d8cccbca5a1f90038440b7de9a3d3e93d53464f8c` | Accepted-current D3 architecture for UPMS: the core |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_21_Annex_Retrieval_Scale.md` | `1e12a4313742426b12bda5b1df5f94c86a39d41318e56f42b94c4661da2f284f` | Accepted-current D3 architecture: the retrieval-and-scale annex, read with core 6.21 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Accepted-current D3 architecture: the anonymous-review annex, read with core 6.21 as its §1 says (unchanged since its earlier ratification) |

These replace D1 1.16 and core 6.17 as accepted-current; the earlier ratification record (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`, SHA-256 `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310`) stays as history. The texts keep their own status lines, which predate this record ("not accepted, not ratified"); they are frozen and are not edited (`AGENTS.md`). This record is what changes their status.

## 2. Evidence the owner relied on

| File | SHA-256 | Result |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_21_Independent_Review.md` | `8f2b567b177e38da3938ac95d6dc443293d606de60012616b595b63d7f888c23` | Codex: PASS for Gate 0 entry for D1 1.20, D2 1.3 and core 6.21 with its annexes; no Serious Challenge; every change map reconstructs its text |
| `workplans/active/UPMS_Candidate_6_20_Independent_Review.md` | `7bbbb2ae480bc96e0ef1bf01754929dec39a3a2198a8227c0e128940530f2229` | Codex: PASS for D1 1.19; the D2 and core findings it raised are closed in the 6.21 review |

Earlier reviews of the package (6.18, 6.19) and of the design note are indexed in `workplans/README.md`. These are technical reviews from outside the Claude family (OpenAI GPT family), not blind and documentary.

## 3. What this ratification decides and does not decide

- **Decided with it:** the evaluation objective of D2 1.3 §10, including charging a partial answer against the largest jointly reachable number of parts (the 6.21 review's question 1).
- **Gate 0 is not passed.** Core §16 and §18.1 still require named pilot languages and profile, a bounded D4 specification and executable evidence specification, and runtime, storage, KMS, backup and restore feasibility. Nothing is implementation-qualified.
- **Not set:** the proposed numbers of D2 §§7.3, 10.3 and 13 and annex R15 remain proposals, to be set by the owner before measurement (D-120).
- **Not ratified:** the checking and Slice 4 annexes of 6.3, the mathematics annex of 6.4 and the mathematics D1 candidate 1.1; the proposal v0.1, which stays a direction input; the design notes; every superseded candidate.
- **Owner decisions** D-1 to D-120 stand as recorded; this record adds none and changes none.
- **Open items** stay open: D1 §15, D2 §14, core §18.1 and §18.2 ("Still open"), annex R18, and the 6.21 review's F621-01 (T148 to be qualified by T167's resource-outcome cases in the executable evidence specification).
- **Product inspectability surfaces** that D1 §11 and core §17.2 mark beyond the requested deliverable are not accepted by this record.
