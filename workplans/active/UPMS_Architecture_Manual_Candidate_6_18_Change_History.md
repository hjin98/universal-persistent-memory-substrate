# UPMS Architecture Manual, Change History A.28 (Candidate 6.17 → 6.18)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not architecture

**What changed.** Revision 6.18 answers the SERIOUS CHALLENGE recorded with owner decisions D-101 to D-116 (`UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` §3, as corrected by `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` §3): core 6.17 had no governed design for memory beyond its pilot envelope. It adds the retrieval-and-scale annex (`UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md`), opens a D2 parent for retrieval (§1.4), and points the core to the annex. Every other rule of core 6.17 is kept; the edits below are the complete list, with each replaced passage verbatim (owner decision D-85).

| Input | SHA-256 |
| --- | --- |
| `UPMS_Architecture_Manual_Review_Candidate_6_17.md` (predecessor, accepted-current) | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` |
| `UPMS_Architecture_Manual_Review_Candidate_6_18.md` (this revision) | `9a42794b35059165ac7e3d83d5a842b4aa33c54bf06f60b003a3aa38b8fd8373` |
| `UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` (new annex) | `abfd09691d82cfb635986eae790c57826b581e257dce2cd26ac3e3311ad2de9e` |
| `UPMS_Architecture_Manual_Candidate_6_17_Change_History.md` (A.27, index of A.1 to A.27 and of reviews) | `c0012fd927e43d9932338a5479a0dd2b5e95d35d90d41259848ceaafbcc3583d` |

**Author's choices for the reviewer to test** (not decided by the owner):
- the annex form: the retrieval design is a new annex read with the core, rather than rewritten into core sections, so the ratified core changes only at the 29 points below;
- R7.2: an agent's write without declarations is accepted and flagged `declarations: missing` rather than refused, so that capture never loses a record; D-107's "required" is enforced by measurement and integration qualification;
- R12 and R15: the delta-buffer limits, the 0.7 summary-rebuild threshold and the 20% sweep share are initial defaults;
- the test numbers T141 to T162 and invariant IDs RT1 to RT12.

## Edits

### A.28.1 title

Was:

````text
# UPMS Architecture Manual (Review Candidate 6.17)
````

Now:

````text
# UPMS Architecture Manual (Review Candidate 6.18)
````

### A.28.2 §1 status

Was:

````text
**Status: proposed D3 architecture, review candidate 6.17; not accepted-current and not implementation-qualified.**
````

Now:

````text
**Status: proposed D3 architecture, review candidate 6.18; not accepted-current and not implementation-qualified.** Core 6.17 with anonymous-review annex 6.7 stays accepted-current until this revision is ratified (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`).
````

### A.28.3 §1 D1 parent

Was:

````text
and concretizes the D1 formulation, now candidate 1.16.
````

Now:

````text
and concretizes the D1 formulation, now candidate 1.17.
````

### A.28.4 §1 histories

Was:

````text
the change histories A.1 to A.27 are indexed with their files and hashes in A.27 (`UPMS_Architecture_Manual_Candidate_6_17_Change_History.md`) and cited below as "change history A.n".
````

Now:

````text
the change histories A.1 to A.27 are indexed with their files and hashes in A.27 (`UPMS_Architecture_Manual_Candidate_6_17_Change_History.md`), A.28 is in `UPMS_Architecture_Manual_Candidate_6_18_Change_History.md`, and all are cited below as "change history A.n".
````

### A.28.5 §1 revision para

Was:

````text
**Revision 6.17 and its files.** Revision 6.17 is editorial: at the product owner's request "Simplify first" (5 November 2026), it moves predecessor and review history out of this text into change history A.27 and changes no rule of candidate 6.16, which had a technical PASS for Gate 0 entry in the Codex review of 6.16. The review package (D-56) is:
````

Now:

````text
**Revision 6.18 and its files.** Revision 6.18, at the product owner's request "Start drafting" (5 November 2026), answers the SERIOUS CHALLENGE that core 6.17 has no governed design for memory beyond its pilot envelope (owner decision D-101). It adds the retrieval-and-scale annex, opens a D2 parent for retrieval (§1.4), and points §§4.3, 10, 12.4, 14, 15, 16 and 18 to the annex; every other rule of core 6.17 is kept (change history A.28). The review package (D-56) is:
````

### A.28.6 §1 annex list

Was:

````text
- the **anonymous-review annex** (`UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md`): §7.8, §11.5 and their tests, reviewed with the core;
````

Now:

````text
- the **anonymous-review annex** (`UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md`): §7.8, §11.5 and their tests, reviewed with the core;
- the **retrieval-and-scale annex** (`UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md`): sections R1 to R18 (planes, index tiers, plans, the response contract, eligibility on every path, publication, translation components, commands, budgets, storage, deletion and recovery at scale, the write path, stepwise discovery, invariants RT1 to RT12 and tests T141 to T162), reviewed with the core, D1 1.17 and the D2 retrieval method candidate 1.0;
````

### A.28.7 §1 annexes unchanged

Was:

````text
The checking and Slice 4 annexes of 6.3, the mathematics annex of 6.4 and the anonymous-review annex of 6.7 are unchanged by this revision and remain part of it.
````

Now:

````text
The checking and Slice 4 annexes of 6.3, the mathematics annex of 6.4 and the anonymous-review annex of 6.7 are unchanged by this revision and remain part of it; the retrieval-and-scale annex is new in it.
````

### A.28.8 §1.1 inputs

Was:

````text
| UPMS Theory–Evidence Formulation, D1 candidate 1.16 | `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md`, SHA-256 `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Proposed D1 parent; its F-rules are cited as "D1 F-n". Editorial revision of 1.15, which had a technical PASS; not accepted. Its predecessors are listed in its map R |
````

Now:

````text
| UPMS Theory–Evidence Formulation, D1 candidate 1.17 | `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | Proposed D1 parent; its F-rules are cited as "D1 F-n". It keeps every rule of 1.16 and adds §16 (F-43 to F-55) and a revised §9; reviewed with this candidate |
| D2 retrieval method, candidate 1.0 | `UPMS_Retrieval_Method_D2_Candidate_1_0.md` | Proposed D2 parent for retrieval (§1.4); reviewed with this candidate |
| D1 1.16 and core 6.17 with annex 6.7 (accepted-current) | `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md`, SHA-256 `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54`; `UPMS_Architecture_Manual_Review_Candidate_6_17.md`, SHA-256 `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976`; ratified in `UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`, SHA-256 `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310` | Immediate predecessors; govern until this revision is ratified |
| Owner decisions D-101 to D-116 and D-117 to D-120 | `UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`, SHA-256 `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c`; `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`, SHA-256 `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Folded in through the retrieval-and-scale annex; listed in §18.2 |
| Retrieval design note, revision 3 | `UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`, SHA-256 `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Direction for the annex; Codex found it sound to draft from (`UPMS_Retrieval_Design_Note_R3_Codex_Critique.md`, SHA-256 `66a2ae248a4ce55196561180cbdfb504b8de83ecb55909df8f4feb5835d19da4`) |
````

### A.28.9 §1.4 D1 parent

Was:

````text
The parent is the D1 formulation candidate 1.16, which is unaccepted; this manual must not redefine its meanings and cites them as D1 F-n.
````

Now:

````text
The parent is the D1 formulation candidate 1.17, which is unaccepted (1.16 is accepted-current until it is ratified); this manual must not redefine its meanings and cites them as D1 F-n.
````

### A.28.10 §1.4 D2 parent

Was:

````text
**No D2 parent is required** while the conditions of D1 §9 hold: no numeric score, calibrated confidence or automatic source-assessment mapping; no statistical comparison model or threshold relied on by screening; no consumer relying on a guaranteed approximation bound; no screening, small-model score or adapter output deciding a consequential outcome without confirmation. Any of these reopens the domain determination, and D2 authority is required first.
````

Now:

````text
**A D2 parent is now required for retrieval.** Owner decisions D-101 to D-120 make retrieval rest on a relied-on error property (no false-negative pruning, retrieval annex R6), measured translation error, asymmetric evaluation and latency targets; core 6.17's condition "no consumer relying on a guaranteed approximation bound" no longer holds for retrieval. The parent is the D2 retrieval method candidate 1.0, which is unaccepted. **No other D2 parent is required** while the remaining conditions of D1 §9 hold: no numeric score, calibrated confidence or automatic source-assessment mapping; no statistical comparison model or threshold relied on by screening; no screening, small-model score or adapter output deciding a consequential outcome without confirmation. Any of these reopens the domain determination, and D2 authority is required first.
````

### A.28.11 §4.3 pointer

Was:

````text
### 4.3 Typed operation families
````

Now:

````text
### 4.3 Typed operation families

Agent principals' writes carry context frames and declarations, and commands that change or delete records bind exact targets at commit (retrieval annex R7, R8).
````

### A.28.12 §10.1 partition

Was:

````text
Partition and filter strategy is D4 and must be qualified;
````

Now:

````text
Partition and filter strategy follows the retrieval annex (R5, R6); its products are D4 and must be qualified;
````

### A.28.13 §10.2 plan

Was:

````text
Graph sophistication needs measured incremental value.
````

Now:

````text
Graph sophistication needs measured incremental value. Every route runs inside a plan (retrieval annex R3): ordering works within a group and never excludes, and similarity and hub routes only propose (D1 F-44).
````

### A.28.14 §10.3 annex fields

Was:

````text

All metadata is access-controlled:
````

Now:

````text

The retrieval annex (R4) adds the plan, the exact and similarity-only groups, each item's exact facts, interpretation facts and assessments, and the coverage dimensions, into which the coverage fields above map.

All metadata is access-controlled:
````

### A.28.15 §12.4 pointer

Was:

````text
Per-unit cryptographic erasure is not claimed (candidate 5 §12.4 is reduced to this, proposal §8.2).
````

Now:

````text
Per-unit cryptographic erasure is not claimed (candidate 5 §12.4 is reduced to this, proposal §8.2); the per-unit keys and purge scheduler that could later support such a claim are in the retrieval annex (R11).
````

### A.28.16 §14.2 envelope

Was:

````text
beyond this, backpressure, archive review and requalification. Without expiry the envelope is reached by growth; its rate is measured (T97) |
````

Now:

````text
beyond this, backpressure, archive review and requalification. Without expiry the envelope is reached by growth; its rate is measured (T97). The architecture is designed beyond this envelope (D-101, retrieval annex); a claim above it needs a bound larger profile (D-120; D2 candidate 1.0 §13) |
````

### A.28.17 §14.2 annex rows

Was:

````text

Retention controllers, deadlines
````

Now:

````text

The retrieval annex (R15) adds rows for budgets by consequence class, the delta buffer, summary rebuild, the processing sweep share, purge rewrite and declarations.

Retention controllers, deadlines
````

### A.28.18 §14.3

Was:

````text
**Initial default:** PostgreSQL for canonical records,
````

Now:

````text
**Initial default:** the planes, index tiers and physical tiers of the retrieval annex (R1, R2, R10); PostgreSQL for canonical records,
````

### A.28.19 §15 pointer

Was:

````text
## 15. Invariants and Acceptance Evidence
````

Now:

````text
## 15. Invariants and Acceptance Evidence

The retrieval annex adds invariants RT1 to RT12 and acceptance scenarios T141 to T162 (R16), mapped to D1 F-43 to F-55.
````

### A.28.20 §16 Gate 0

Was:

````text
| Gate 0 | The proposal, the D1 formulation and this candidate reviewed together by a
````

Now:

````text
| Gate 0 | The proposal, the D1 formulation, the D2 retrieval method and this candidate with its retrieval-and-scale annex reviewed together by a
````

### A.28.21 §16 annex slices

Was:

````text

Slice 1 is split (D-16)
````

Now:

````text

The retrieval annex adds its parts to each slice (R17); Slice 1a-core gains the planes, exact tiers, plans, the response contract, declarations, command binding, deletion units and the purge scheduler.

Slice 1 is split (D-16)
````

### A.28.22 §18.1 rows

Was:

````text
| Challenges in §18.3 | Independent check that revision 6.17 changes no rule of candidate 6.16 (A.27) | Reviewer outside the Claude family |
````

Now:

````text
| Challenges in §18.3 | Independent check that the retrieval annex, D1 1.17 §16 and D2 candidate 1.0 answer the D-101 challenge, and that revision 6.18 changes no other rule of 6.17 (A.28) | Reviewer outside the Claude family |
| Retrieval and scale | The open items of the retrieval annex (R18): pruning correctness, translation error, the owner's workload and limits, key hierarchy and purge feasibility, declaration reliability, a larger profile | Owners named there |
````

### A.28.23 §18.2 rows

Was:

````text
TE-07; T138 to T140 |
````

Now:

````text
TE-07; T138 to T140 |
| D-101 to D-116 | Retrieval at scale, translation and economy: GB to TB by design; fidelity and serving planes; deterministic tiered index; one translation layer; declared loss; stepwise discovery (`UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`) | D1 §16, §9; D2 candidate 1.0; retrieval annex |
| D-117 to D-120 | Cheap qualified discovery map; exact checks apart from assessments; deduplication within deletion units; larger workload deferred to D2 (`UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`) | D1 F-43, F-54; D2 §13; annex R4, R10, R14 |
````

### A.28.24 §18.3

Was:

````text
Revision 6.17 makes no repair. The repairs of earlier revisions are mapped in their change histories, indexed in A.27. Each repair is the author's and needs an independent check.
````

Now:

````text
Revision 6.18 answers the SERIOUS CHALLENGE recorded with D-101 to D-116 (their record §3, as corrected by the D-117 to D-120 record §3): core 6.17 had no governed design for memory beyond its pilot envelope. The answer is the retrieval-and-scale annex with D1 1.17 §16 and D2 candidate 1.0; change history A.28 maps it. The repairs of earlier revisions are mapped in their change histories, indexed in A.27. Each repair is the author's and needs an independent check.
````

### A.28.25 App A range

Was:

````text
The change map of this candidate, from candidate 5 to 6.17 (
````

Now:

````text
The change map of this candidate, from candidate 5 to 6.18 (
````

### A.28.26 App A files

Was:

````text
is in the change-history files indexed in A.27 (`UPMS_Architecture_Manual_Candidate_6_17_Change_History.md`).
````

Now:

````text
is in the change-history files indexed in A.27 (`UPMS_Architecture_Manual_Candidate_6_17_Change_History.md`) and in A.28 (`UPMS_Architecture_Manual_Candidate_6_18_Change_History.md`).
````

### A.28.27 App B revisions

Was:

````text
- **Revisions 6.1 to 6.17:**
````

Now:

````text
- **Revisions 6.1 to 6.18:**
````

### A.28.28 App B read

Was:

````text
`workplans/README.md`; `history/SEMANTIC_EVOLUTION.md`.
````

Now:

````text
`workplans/README.md`; `history/SEMANTIC_EVOLUTION.md`; for 6.18, design note revision 3, its three Codex critiques and decision records D-101 to D-120.
````

### A.28.29 §2 terms

Was:

````text
| Front end | A registered client that runs a process over UPMS records (SCIRE for inquiry; project-memory clients); owns its policies, never the record semantics | 4.4 |
````

Now:

````text
| Front end | A registered client that runs a process over UPMS records (SCIRE for inquiry; project-memory clients); owns its policies, never the record semantics | 4.4 |
| Plan | Mandatory filters fixing a population plus discovery routes (D1 Definition 16.1) | Retrieval annex R3 |
| Exact facts, assessments | What is decidable about a returned item, and the attributed judgments that may be wrong (D1 Definitions 16.2, 16.3) | Retrieval annex R4 |
| Fidelity plane, serving plane | Canonical records, complete; and everything rebuildable from them | Retrieval annex R1 |
| Context frame, declaration, rendering, resolution | D1 Definitions 16.8 to 16.11 | Retrieval annex R7 |
````
