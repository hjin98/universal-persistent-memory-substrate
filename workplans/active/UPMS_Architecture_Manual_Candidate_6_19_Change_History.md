# UPMS Architecture Manual, Change History A.29 (Candidate 6.18 → 6.19)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not architecture

Revision 6.19 repairs the Codex review of candidate 6.18, D1 1.17 and D2 1.0 (NO-PASS), under the owner's delegation of the revise-and-review cycle. The core changes only in its version references; the repairs are in the retrieval-and-scale annex, D1 1.18 (map T) and D2 1.1 (its change history). Each replaced passage is quoted verbatim.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Architecture_Manual_Review_Candidate_6_18.md` | `9a42794b35059165ac7e3d83d5a842b4aa33c54bf06f60b003a3aa38b8fd8373` |
| `UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` | `abfd09691d82cfb635986eae790c57826b581e257dce2cd26ac3e3311ad2de9e` |
| `UPMS_Architecture_Manual_Review_Candidate_6_19.md` | `c0fc446c4493aab2c2dd6b6f4611e3cd34b991cbcfa36235891ca73921fef3c3` |
| `UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md` | `a737a6a64d15d23f310bbd4e41137eacebff03a86c4c8de63ef90f1b3fb9c0bb` |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18_Change_History.md` | `2575c36361a508bf49c7d123907e20231f650540cbd2a1b7ad8c7fd349ef3ec8` |
| `UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md` | `a4e4482b0b45c75b0f0adf1408183e4760895d007e0647bf051346f0af03922f` |

## Dispositions of the Codex review of 6.18

Review: `UPMS_Candidate_6_18_Independent_Review.md`, SHA-256 `9fbe6ed485cf84cae6afa1f4795ddb488660d2bb04b28e636a61c82cd5679108`. "Repaired" is the author's claim, for the next review to test.

| Finding | Repair | Where |
| --- | --- | --- |
| SC618-01 (adoption let unconfirmed resolutions be bases) | The design note's rule restored: a resolution never rests on a resolution its speaker has not confirmed; adoption creates the adopter's claim and does not qualify the resolution | D1 1.18 F-51 item 2; annex R7.4, RT8, T152 |
| SC618-02 (cost model omitted pruning work) | Work split into routing, execution, delta, eligibility, checking, counting, similarity and reranking; tokens estimated separately; empirical interval; full-scan fallback; estimates shown only from statistics over content the reader may know exists | D2 1.1 §7.1, §7.2; annex T167 |
| SC618-03 (declarations not enforced) | Deliberate agent record writes are refused without declarations (an explicit empty declaration suffices); captured turns are never refused but are integration defects, and an integration fails Gate 1a-core qualification above 1% missing | Annex R7.2, R15, T150 |
| F618-01 (lexical representation) | Lexical routes name their representation; rendering matches are exact facts about the rendering, citing the original span; no original-text match for absent words | D1 1.18 Definitions 16.1, 16.2; annex R3, R4, R7.3, RT13, T163 |
| F618-02 (predecessor metadata) | §13 names the ratified predecessor and assesses the recorded tension's applicability, marked proposed | D1 1.18 §13 |
| F618-03 (selection on held-out data) | Development queries for selection; frozen variant; separate held-out test; variants and reuse recorded | D2 1.1 §5.3 |
| F618-04 (abstention judged against the plan; incomplete classes) | Answerability adjudicated against the request; useful-partial outcome; requirements for every class | D2 1.1 §10.1, §10.2 |
| F618-05 (scale ladder; lifecycle workload) | Larger steps optional until a profile claims them; lifecycle workload, maintenance concurrency and purge envelope proposed; peak headroom for concurrent maintenance | D2 1.1 §10.3, §11, §13; annex R11, T168 |
| F618-06 (caps and counts) | Effective cap is the smaller of the class cap and the §14.2 query limits, larger only with deep retrieval; totals carry status | D2 1.1 §6, §7.3; annex R4, R9, R15, RT14, T165, T166 |
| F618-07 (delivery map) | Author renderings and an early deterministic compiler and resolver subset placed in Slice 1a-core | Annex R3, R17, RT7, RT8 |
| F618-08 (capture extent) | `capture` dimension kept; the field mapping made exhaustive | D1 1.18 Definition 16.5; annex R4, RT14, T164 |
| §4.2 test discriminators | T144 to T147, T150, T152, T161 strengthened; T163 to T168 added | Annex R16.2 |
| §4.3 independence of checks | Different model identities, shared inputs recorded; agreement is not a probability | D2 1.1 §8 item 3 |
| §7 ordering | Baseline is the ratified ordering; reciprocal rank fusion only if it beats it; correlated routes grouped | D2 1.1 §6 |
| §5.1 map S wording | Map T lists replaced text from the actual 1.17 file | Map T |

**The review's owner questions.** (1) Resolution bases: the reviewed direction is restored, so no owner decision is needed. (2) Declarations: answered within D-107 ("required for agent principals"): refusal for deliberate writes, a bounded defect for capture. (3) Budgets: answered within D-120: class selection never widens the pilot profile. (4) Values before measurement: left to the owner under D-120; D2 §10.2 and §13 propose them.

## Core edits

### A.29.c.1 title

Was:

````text
# UPMS Architecture Manual (Review Candidate 6.18)
````

Now:

````text
# UPMS Architecture Manual (Review Candidate 6.19)
````

### A.29.c.2 status

Was:

````text
review candidate 6.18; not accepted-current
````

Now:

````text
review candidate 6.19; not accepted-current
````

### A.29.c.3 annex file (1 places)

Was:

````text
UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md
````

Now:

````text
UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md
````

### A.29.c.4 D1 file (1 places)

Was:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md
````

Now:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md
````

### A.29.c.5 D2 file (1 places)

Was:

````text
UPMS_Retrieval_Method_D2_Candidate_1_0.md
````

Now:

````text
UPMS_Retrieval_Method_D2_Candidate_1_1.md
````

### A.29.c.6 D1 version a (3 places)

Was:

````text
candidate 1.17
````

Now:

````text
candidate 1.18
````

### A.29.c.7 D1 version b (3 places)

Was:

````text
D1 1.17
````

Now:

````text
D1 1.18
````

### A.29.c.8 D2 version (7 places)

Was:

````text
candidate 1.0
````

Now:

````text
candidate 1.1
````

### A.29.c.9 §1 histories

Was:

````text
A.28 is in `UPMS_Architecture_Manual_Candidate_6_18_Change_History.md`, and all are cited below
````

Now:

````text
A.28 is in `UPMS_Architecture_Manual_Candidate_6_18_Change_History.md`, A.29 in `UPMS_Architecture_Manual_Candidate_6_19_Change_History.md`, and all are cited below
````

### A.29.c.10 §1 revision 6.19

Was:

````text
every other rule of core 6.17 is kept (change history A.28). The review package (D-56) is:
````

Now:

````text
every other rule of core 6.17 is kept (change history A.28). **Revision 6.19** repairs the Codex review of 6.18 (NO-PASS, `UPMS_Candidate_6_18_Independent_Review.md`), under the owner's delegation of the review cycle: the repairs are in the annex, D1 1.18 and D2 1.1, and the core changes only in its version references (change history A.29). The review package (D-56) is:
````

### A.29.c.11 §1.1 review row

Was:

````text
| D2 retrieval method, candidate 1.1 |
````

Now:

````text
| Independent review of candidate 6.18 with D1 1.17 and D2 1.0 (Codex, OpenAI family) | `UPMS_Candidate_6_18_Independent_Review.md` | NO-PASS for all three; SC618-01 to SC618-03 and F618-01 to F618-08, repaired in this revision (A.29) |
| D2 retrieval method, candidate 1.1 |
````

### A.29.c.12 §18.1 challenge row

Was:

````text
and that revision 6.18 changes no other rule of 6.17 (A.28) |
````

Now:

````text
and that revisions 6.18 and 6.19 change no other rule of 6.17 (A.28, A.29) |
````

### A.29.c.13 §18.3

Was:

````text
change history A.28 maps it. The repairs of earlier revisions
````

Now:

````text
change histories A.28 and A.29 map it; A.29 also maps the repairs of the Codex review of 6.18. The repairs of earlier revisions
````

### A.29.c.14 App A range

Was:

````text
from candidate 5 to 6.18 (
````

Now:

````text
from candidate 5 to 6.19 (
````

### A.29.c.15 App A files

Was:

````text
and in A.28 (`UPMS_Architecture_Manual_Candidate_6_18_Change_History.md`).
````

Now:

````text
in A.28 (`UPMS_Architecture_Manual_Candidate_6_18_Change_History.md`) and in A.29 (`UPMS_Architecture_Manual_Candidate_6_19_Change_History.md`).
````

### A.29.c.16 App B

Was:

````text
- **Revisions 6.1 to 6.18:**
````

Now:

````text
- **Revisions 6.1 to 6.19:**
````

### A.29.c.17 App B read

Was:

````text
for 6.18, design note revision 3, its three Codex critiques and decision records D-101 to D-120.
````

Now:

````text
for 6.18, design note revision 3, its three Codex critiques and decision records D-101 to D-120; for 6.19, the Codex review of 6.18.
````

## Annex edits

### A.29.a.1 title

Was:

````text
# UPMS Architecture Manual, Review Candidate 6.18: Retrieval-and-Scale Annex
````

Now:

````text
# UPMS Architecture Manual, Review Candidate 6.19: Retrieval-and-Scale Annex
````

### A.29.a.2 status

Was:

````text
part of review candidate 6.18;
````

Now:

````text
part of review candidate 6.19;
````

### A.29.a.3 core file

Was:

````text
the core of candidate 6.18 (`UPMS_Architecture_Manual_Review_Candidate_6_18.md`)
````

Now:

````text
the core of candidate 6.19 (`UPMS_Architecture_Manual_Review_Candidate_6_19.md`)
````

### A.29.a.4 version: D1 (2 places)

Was:

````text
D1 1.17
````

Now:

````text
D1 1.18
````

### A.29.a.5 version: D2 (2 places)

Was:

````text
candidate 1.0
````

Now:

````text
candidate 1.1
````

### A.29.a.6 drafted by

Was:

````text
Drafted by Claude (AI, Opus 5.5) at the product owner's request "Start drafting" (5 November 2026).
````

Now:

````text
Drafted by Claude (AI, Opus 5.5) at the product owner's request "Start drafting" (5 November 2026). Revision 6.19 of this annex repairs the Codex review of revision 6.18 (NO-PASS, `UPMS_Candidate_6_18_Independent_Review.md`) under the owner's delegation of the review cycle; change history A.29 maps each repair.
````

### A.29.a.7 R3 schema

Was:

````text
routes: [ Lexical{ formula, analyzer_version }
````

Now:

````text
routes: [ Lexical{ formula, representation: original | rendering, analyzer_version }
````

### A.29.a.8 R3 early subset

Was:

````text
The compiler and the resolver (R7.4) are processors under §7.4: they run only on eligible processors, receive only inputs eligible for the reader, and record their identities.
````

Now:

````text
The compiler and the resolver (R7.4) are processors under §7.4: they run only on eligible processors, receive only inputs eligible for the reader, and record their identities.

**Early subset (Slice 1a-core).** Until the vocabulary registry (Slice 3) and processor resolution (Slice 2) exist, the compiler checks plans against the record schema, the scope's coordination-key registry (§14.2), declared index terms and the identities of principals and records, and resolves mentions in a request only deterministically: "I" and "you" from the asker's context frame, declared referents, and exact identifiers. Every other mention stays unresolved, is shown as unresolved in the plan, and is searched lexically.
````

### A.29.a.9 R4 representation

Was:

````text
route_matches: [{route, matched | similarity_only, versions}] }
````

Now:

````text
route_matches: [{route, representation, matched | similarity_only, versions}] }
````

### A.29.a.10 R4 capture and totals

Was:

````text
  coverage := {
    execution:      { evaluated, skipped, reason, total_matches, returned, continuation }
                    // was indexed_extent, traversal_extent, truncation, timeout
````

Now:

````text
  coverage := {
    capture:        { capture_extent, known_gaps }         // was capture_extent, meaning unchanged
    execution:      { evaluated, skipped, reason,
                      total: { value, status: exact | lower_bound | estimate | unknown },
                      returned, continuation }
                    // was indexed_extent, traversal_extent, truncation, timeout
````

### A.29.a.11 R4 mapping

Was:

````text
Every count names its unit.
````

Now:

````text
The mapping is exhaustive: every coverage field of §10.3 has a destination above, and none is dropped. Every count names its unit and its status; a candidate cap, a page limit and an incomplete execution are different events (D2 §6).
````

### A.29.a.12 R7.2 declarations

Was:

````text
### R7.2 Declarations at the agent write interface

**Fixed (proposed).** The write operations an agent principal's content reaches UPMS through (`record_event` for its captured turns, and the record-writing operations of §4.3 it issues) take a `declarations` field: referents (identities and record revisions the span refers to) and index terms. For **agent principals the field is required** (D-107): a write without it is accepted with `declarations: missing` recorded and reported in processing coverage, so a careless integration is visible rather than blocked; the integration's qualification measures the missing rate. For people it is optional.

The core validates each declared referent: it exists, and the writer may read it. A referent the writer may not read is refused, as it would disclose by reference. A declaration is labeled as the speaker's (D1 Definition 16.9) and indexed into E2.
````

Now:

````text
### R7.2 Declarations at the agent write interface

**Fixed (proposed).** Declarations (D1 Definition 16.9) are required for agent principals (D-107). Two cases differ:

1. **Deliberate record writes.** The record-writing operations of §4.3 that an agent principal issues (`propose`, `record_question`, `record_inference`, `record_evidence_relation`, `record_objection`, `record_decision`, `record_coordination` and the like) take a `declarations` field, and a call without it is **refused**. An explicit empty declaration ("no referents") satisfies it.
2. **Captured turns.** `record_event` capture of an agent's turns never refuses, so that no evidence is lost: a captured turn without declarations is committed with `declarations: missing`, recorded as an **integration defect** of the capturing integration, and reported in processing coverage. An integration fails qualification at Gate 1a-core if more than the bound share of its captured agent turns lack declarations (R15).

For people, declarations are optional in both cases.

The core validates each declared referent: it exists, and the writer may read it. A referent the writer may not read is refused, as it would disclose by reference. A declaration is labeled as the speaker's and indexed into E2.
````

### A.29.a.13 R7.3 representation

Was:

````text
Both versions are indexed in E1 and E2; matches through an insertion carry `via: rendering_insertion`.
````

Now:

````text
Both versions are indexed in E1 and E2; matches through an insertion carry `via: rendering_insertion`. A lexical route names the representation it searches: a match in a rendering is reported against the rendering revision, with the original span cited (D1 Definition 16.2), and an insertion-only match never appears as an original-text match. Author-supplied renderings are part of Slice 1a-core (R17).
````

### A.29.a.14 R7.4 basis

Was:

````text
It never uses an unconfirmed, unadopted resolution as a basis.
````

Now:

````text
It never uses as a basis a resolution its speaker has not confirmed; an adoption of a resolution is the adopter's own claim and does not qualify the resolution as a basis (D1 F-51).
````

### A.29.a.15 R9.1 caps

Was:

````text
1. **Budgets by consequence class** (D2 §7.3) are profile values (§14.2 additions, R15). Every plan runs under its class's cap (D2 §7.4).
````

Now:

````text
1. **Budgets by consequence class** (D2 §7.3) are profile values (§14.2 additions, R15). A plan's **effective cap** is the smaller of its class cap and the §14.2 query limits; a larger cap needs the deep-retrieval capability with its budget (§10.4), requested as a new plan under item 3. Class selection never widens the pilot profile. Every plan runs under its effective cap (D2 §7.4).
````

### A.29.a.16 R11.2 aggregate purge

Was:

````text
Purge debt (bytes and segments awaiting rewrite) is measured.
````

Now:

````text
Purge debt (bytes and segments awaiting rewrite) is measured. Purge capacity is sized to the bound lifecycle workload and maintenance concurrency (D2 §13): purge rewrites take priority over merges, and nonessential ingestion stops before purge would miss its target (§14.2 disk admission). Meeting the target for one segment does not show the aggregate target is met; T168 tests the aggregate, and a missed target is reported as `purge_failed`, never hidden.
````

### A.29.a.17 R15 effective cap

Was:

````text
| Budgets by consequence class | D2 §7.3, as proposed defaults until the owner sets them (D-120) |
````

Now:

````text
| Budgets by consequence class | D2 §7.3, as proposed defaults until the owner sets them (D-120) |
| Effective cap | The smaller of the class cap and the §14.2 query limits; larger only with the deep-retrieval capability and its budget |
````

### A.29.a.18 R15 declarations

Was:

````text
| Declarations | Required for agent principals; missing rate measured per integration |
````

Now:

````text
| Declarations | Required for agent principals' record writes (refused without); on captured agent turns, at most 1% missing at Gate 1a-core qualification, each missing one an integration defect |
````

### A.29.a.19 RT7 slice

Was:

````text
| RT7 | Interpretations never replace text; confirmation, adoption and fidelity assessments are separate facts | F-50 | 1a-core (declarations, rule extraction); 2 (model extraction, renderings) |
````

Now:

````text
| RT7 | Interpretations never replace text; confirmation, adoption and fidelity assessments are separate facts | F-50 | 1a-core (declarations, rule extraction, author renderings); 2 (model extraction, processor renderings) |
````

### A.29.a.20 RT8

Was:

````text
| RT8 | Resolutions record basis and position, are labeled current or as-held, and never rest on unconfirmed, unadopted resolutions | F-51 | 2 |
````

Now:

````text
| RT8 | Resolutions record basis and position, are labeled current or as-held, and never rest on resolutions their speakers have not confirmed | F-51 | 1a-core (deterministic subset, R3); 2 (processor resolution) |
````

### A.29.a.21 RT13 RT14

Was:

````text
| RT12 | Placement in tiers never changes eligibility, completeness or archive state | — (D-112) | 4 |
````

Now:

````text
| RT12 | Placement in tiers never changes eligibility, completeness or archive state | — (D-112) | 4 |
| RT13 | A lexical match names the representation it matched in; no original-text match is reported for words absent from the original | F-43; Definition 16.2 | 1a-core |
| RT14 | Coverage carries capture extent, and every count carries its status | F-46; Definition 16.5 | 1a-core |
````

### A.29.a.22 T144

Was:

````text
| T144 | Insertion during a query (RT3): a span committed after the newest watermark is found through the delta buffer, or the delta is reported unevaluated; a brute-force reference agrees |
````

Now:

````text
| T144 | Insertion during a query (RT3): with the query's snapshot pinned, and publication, delta visibility and merge completion controlled independently, a span committed after the newest watermark, and an interpretation newly added to an old span, are each found through the delta buffer or reported unevaluated; a brute-force reference agrees |
````

### A.29.a.23 T145

Was:

````text
| T145 | Deletion, merge and rebuild (RT3): after a sequence of deletions, merges and a summary rebuild, sampled plans agree with a brute-force scan of the same population and analyzer |
````

Now:

````text
| T145 | Deletion, merge and rebuild (RT3): after a sequence of deletions, merges and a summary rebuild, sampled plans agree with an independently implemented brute-force matcher over the same population (D2 §9.4) |
````

### A.29.a.24 T146

Was:

````text
| T146 | Version mismatch (RT3): after an analyzer change, summaries of the old version are not used to prune plans of the new one |
````

Now:

````text
| T146 | Version mismatch (RT3): after an analyzer change, neither the summaries nor the postings of the old version are used for plans of the new one; segments not yet rebuilt are scanned under the new analyzer or reported unevaluated |
````

### A.29.a.25 T147

Was:

````text
| T147 | Negated predicates (RT3): a plan `NOT contains(foo)` prunes no segment |
````

Now:

````text
| T147 | Pruning logic (RT3): `NOT contains(foo)` prunes no segment; nested conjunctions and disjunctions of positive and negated atoms prune exactly where D2 §3.3 allows; a structural atom over unprocessed spans prunes nothing; a phrase is checked positionally after a term-level prune, including phrases near span boundaries |
````

### A.29.a.26 T150

Was:

````text
| T150 | Declarations (R7.2): an agent's write without declarations is accepted with `declarations: missing` and reported; a declared referent the agent cannot read is refused; a wrong but readable declared referent is labeled the agent's, and its correction creates review obligations on dependents |
````

Now:

````text
| T150 | Declarations (R7.2): an agent's `record_inference` without declarations is refused, and with an explicit empty declaration accepted; an agent's captured turn without declarations is committed with `declarations: missing` and an integration defect; an integration missing declarations on more than the bound share of turns fails qualification; a declared referent the agent cannot read is refused; a wrong but readable declared referent is labeled the agent's, and its correction creates review obligations on dependents |
````

### A.29.a.27 T152

Was:

````text
| T152 | Resolution basis (RT8): a resolution whose only basis is another unconfirmed, unadopted resolution is refused |
````

Now:

````text
| T152 | Resolution basis (RT8): a resolution whose only basis is another resolution its speaker has not confirmed is refused, including when that resolution has been adopted; the adopter's claim stays usable as that claim |
````

### A.29.a.28 T161

Was:

````text
| T161 | Fairness (D2 §8): an obligation-bearing span that is never retrieved is processed by the sweep within its window |
````

Now:

````text
| T161 | Fairness (D2 §8): under the bound lifecycle workload, an obligation-bearing span that is never retrieved is processed within the processing window (D2 §8 item 4), or reported overdue |
````

### A.29.a.29 T163-T168

Was:

````text
| T162 | Occurrences (RT7): the same sentence in two sessions gets two resolutions with different referents and dates; neither inherits the other's interpretation |
````

Now:

````text
| T162 | Occurrences (RT7): the same sentence in two sessions gets two resolutions with different referents and dates; neither inherits the other's interpretation |
| T163 | Rendering matches (RT13): a lexical query for "Bob Lee" over "He fixed it yesterday." with the rendering "[Bob Lee] fixed …" returns a match against the rendering revision, with the original span cited and `via: rendering_insertion`; no original-text match is reported |
| T164 | Capture gaps (RT14): with a known capture gap for a session, a complete execution over the retained population still reports the gap under `capture`, and the agent's reply carries it where its class requires |
| T165 | Count status (RT14): a plan stopped at its effective cap reports its total as a lower bound; a page limit on a complete execution reports an exact total with 30 returned |
| T166 | Effective cap (R9): a decision-basis plan estimated at 4 s without the deep-retrieval capability stops at the §14.2 work budget and is reported budget-limited; with the capability and budget, it runs as a new plan |
| T167 | Estimates and hidden content (R5, D2 §7.2): two worlds that differ only by hidden matching records show the same estimate to the reader |
| T168 | Aggregate purge (RT11): deleting one item in each of many segments during sustained ingestion and a concurrent rebuild either meets the live-surface target for every deletion, with ingestion throttled first, or reports `purge_failed` for those missed; purge debt is reported throughout, and a crash during a rewrite leaves no deleted content served |
````

### A.29.a.30 R17 1a-core

Was:

````text
| Slice 1a-core | R1 to R6; R7.1, R7.2 and rule-based E2 extraction; R8 to R11; R12 order of service at pilot size; R13; R14 items 1, 3, 4 and 5; RT1 to RT7 (declarations and rule extraction), RT9 to RT11; T141 to T150, T153 to T156, T158 to T160 |
````

Now:

````text
| Slice 1a-core | R1 to R6, with the R3 early subset; R7.1, R7.2, author-supplied renderings (R7.3) and rule-based E2 extraction; R8 to R11; R12 order of service at pilot size; R13; R14 items 1, 3, 4 and 5; RT1 to RT7 (declarations, rule extraction, author renderings), RT8 (deterministic subset), RT9 to RT11, RT13, RT14; T141 to T150, T153 to T156, T158 to T160, T163 to T168 |
````

### A.29.a.31 R17 slice 2

Was:

````text
| Slice 2 | R7.3 renderings for human text and R7.4 resolution by processors;
````

Now:

````text
| Slice 2 | R7.3 processor renderings for human text and R7.4 resolution by processors;
````
