# UPMS Architecture Manual, Review Candidate 6.19: Retrieval-and-Scale Annex

**Status: proposed D3 architecture, part of review candidate 6.19; not accepted-current and not implementation-qualified.** This annex is read with the core of candidate 6.19 (`UPMS_Architecture_Manual_Review_Candidate_6_19.md`), which names it in its §1, and is reviewed with the core, D1 1.18 and the D2 retrieval method candidate 1.1. It realizes D1 1.18 §16 (F-43 to F-55) and consumes D2 candidate 1.1. It answers the SERIOUS CHALLENGE that core 6.17 is inadequate for memory designed up to the size storage permits (owner decision D-101; `UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` §3, as corrected in `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` §3). Its direction is design note revision 3 (`UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`), which Codex found sound to draft from. Its sections are numbered R1 to R18; "§n" means a core section.

Drafted by Claude (AI, Opus 5.5) at the product owner's request "Start drafting" (5 November 2026). Revision 6.19 of this annex repairs the Codex review of revision 6.18 (NO-PASS, `UPMS_Candidate_6_18_Independent_Review.md`) under the owner's delegation of the review cycle; change history A.29 maps each repair.

## R1. Two planes

**Fixed (proposed).**

| Plane | Holds | Contract |
| --- | --- | --- |
| **Fidelity** | Every canonical record (§5), including retained model outputs with their manifests (§11.2), declarations, renderings, resolutions and plans recorded as interpretations; immutable, encrypted payloads | Complete; never depends on an index for completeness; the only source for rebuilding anything else |
| **Serving** | Lexical and structural indexes, segment summaries and statistics, similarity indexes, hub search structures, caches | Rebuildable from the fidelity plane; each structure carries its version and covered watermark; may be approximate only where this annex says, and its limits appear in coverage (R4) |

A model output cannot be reproduced by rerunning its model, so the output is a canonical record and only its searchable forms are serving state. Core §4.1 (component ownership) and §14.3 (derived artifacts) are unchanged; this annex adds the plane boundary as a fixed constraint on them.

## R2. Index tiers and the span unit

**Fixed (proposed):** the tiers and their guarantees. **Initial default:** the product choices.

| Tier | Contents | Exact for |
| --- | --- | --- |
| **E0 Identity and references** | IDs, revisions, protected digests (§5.6), timestamps, scope, owner, session, source, file paths, citations and relation edges | Everything it holds; modification, deletion propagation, lineage, impact and standing traversal run here only |
| **E1 Lexical** | Positional inverted index over original text under a versioned analyzer, with offset maps (D2 §4) | Literal predicates under its analyzer |
| **E2 Structural** | Declared index terms and referents, coordination keys, tags, entity bindings, typed relations, rule-extracted identifiers (paths, symbols, URLs, issue numbers, dates, numbers with units) and, from Slice 3, structured statements (checking annex §5.7) | Lookup over what was recorded, by extractor version; never extraction recall (D1 F-43) |
| **A Approximate** | Embeddings, similarity indexes, hub routes | Nothing; proposals only (D1 F-44) |

The **index unit is the span**: a contiguous range of one event revision's original text (or a record field), which rolls up to its record. Citations, checks and support assessments refer to spans.

**First product (Initial default):** an established positional inverted index whose per-segment term dictionaries are the pruning summaries; PostgreSQL for canonical records and E0; object storage for payloads (§14.3); a simple embedding index for A. Custom summary trees, high-cardinality facets, disk-resident similarity indexes and parallel re-embedding wait for measured need (design note R3 §10).

## R3. Plans and the compiler

**Fixed (proposed).** Every retrieval runs a **plan** (D1 Definition 16.1): mandatory filters fixing the population, and discovery routes. Context assembly (§10.4), overviews (§10.5) and team memory (§10.6) issue plans like any other caller.

**The compiler** turns a request into a plan, in a small typed query language:

```text
Plan {
  request_ref, consequence_class            // D1 Definition 16.7
  filters: { eligibility: reader_context,   // always present; R5
             scopes?, time?, record_types?, as_of?, archive_included }
  routes: [ Lexical{ formula, representation: original | rendering, analyzer_version }
          | Structural{ formula, extractor_versions }
          | Similarity{ query_text, embedding_version, k }
          | Hub{ hub_refs } ]
  resolutions: [ resolution_ref ]           // mentions in the request (R7.4)
  budget: { class_caps, task_budget_ref }   // R9
  compiler: processor_identity, grammar_version
}
```

The compiler's output is checked against the grammar, the schema and the vocabulary; an invalid plan is rejected or repaired, and a repair is shown. The compiler over-generates routes (aliases, related concepts, original and rendered text) within the filters; routes are unioned. A plan is recorded with the release record of its answer (§8.2), so the trail of a discovery is the sequence of its plans (R14).

The compiler and the resolver (R7.4) are processors under §7.4: they run only on eligible processors, receive only inputs eligible for the reader, and record their identities.

**Early subset (Slice 1a-core).** Until the vocabulary registry (Slice 3) and processor resolution (Slice 2) exist, the compiler checks plans against the record schema, the scope's coordination-key registry (§14.2), declared index terms and the identities of principals and records, and resolves mentions in a request only deterministically: "I" and "you" from the asker's context frame, declared referents, and exact identifiers. Every other mention stays unresolved, is shown as unresolved in the plan, and is searched lexically.

## R4. Response contract

**Fixed (proposed).** `MemoryResult` (§10.3) gains these fields; existing fields keep their meanings, and the old coverage fields map into the dimensions as shown.

```text
MemoryResult += {
  plan_ref, consequence_class
  groups: { exact: [item], similarity_only: [item] }      // D1 F-43, F-44
  item += {
    exact_facts: { source_integrity, eligible_at, population_member,
                   route_matches: [{route, representation, matched | similarity_only, versions}] }
    via: original | extraction | rendering_insertion
    interpretation?: { speaker_confirmation_ref?, adoption_refs[],
                       fidelity_assessment_refs[] }        // separate facts, D1 F-50
    assessments: [{ kind: relevance | support, assessor, ref }]
  }
  coverage := {
    capture:        { capture_extent, known_gaps }         // was capture_extent, meaning unchanged
    execution:      { evaluated, skipped, reason,
                      total: { value, status: exact | lower_bound | estimate | unknown },
                      returned, continuation }
                    // was indexed_extent, traversal_extent, truncation, timeout
    processing:     { by_version, unprocessed }            // was processing_, structured_, screened_extent
    availability:   { unavailable_bytes, deletion_markers, private_source_endpoints }
                    // only about records the reader may know exist; D1 F-46
    interpretation: { interpretation_only_matches, ambiguous_sources }
    answer_support: { assessed, unassessed }
    archive_included, impact_pending, objection_coverage   // unchanged
    scope_note: "results cover only records you may read" // always present
  }
}
```

The mapping is exhaustive: every coverage field of §10.3 has a destination above, and none is dropped. Every count names its unit and its status; a candidate cap, a page limit and an incomplete execution are different events (D2 §6). **Availability** never counts a hidden record, and `scope_note` is present whether or not hidden matches exist (D1 F-46). An answer passed to an agent carries, in its text, every limitation its consequence class requires (D1 F-49); the integration's rendering of `MemoryResult` is checked by T160.

## R5. Eligibility on every path

**Fixed (proposed).** The core's complete eligibility predicate (§7.3.4, §7.4, §10.1: own-record and oversight entitlements, session grants, restriction tags, quarantine, barriers, lineage exclusions) is evaluated on every path: candidate generation, checks, ordering, snippets, the compiler's and resolver's inputs, vocabulary expansion, cost estimates, discovery counts and facets, continuation tokens and caches. Partitioning by scope is an optimization inside that predicate, never a substitute for it. Shared approximate structures follow §10.1: they may be internal to the trusted computing base only if ineligible content cannot affect exposed snippets, counts, explanations or model inputs. Timing side channels are measured separately; no constant-time claim is made (§10.1).

## R6. Partitions, segments and publication

**Fixed (proposed):** the publication protocol. **Delegated to D4:** segment sizes, merge policy and product.

1. **Layout.** Tenant → scope → time segment → index segment. This gives locality, not a speed guarantee (D2 §13 states cost envelopes by workload family).
2. **Atomic publication.** A segment becomes searchable only with its summary, statistics, analyzer and extractor identities and covered watermark, published in one step.
3. **Delta.** Spans committed after the newest published watermark are held in a delta buffer that every plan scans exactly, or execution coverage reports them as unevaluated.
4. **Versions.** Summaries and statistics are keyed by version; a plan under another version cannot prune with them (D2 §3.4).
5. **Failure.** A missing, corrupt, incompatible or stale summary means the segment is searched or reported unevaluated, never skipped.
6. **Deletion and merge.** Summaries are never edited to remove deleted content; they are rebuilt from surviving content (D2 §3.4). A merged segment's summary is built from the complete merged input.
7. **Statistics** for cost estimation (per-segment term and field frequencies) are published with each segment.
8. **A false-negative prune** is an incident: pruning on that summary type stops, and the incident is recorded (§11.3).

## R7. Translation components

### R7.1 Context frames

**Fixed (proposed).** Capture (§9.2) records a **context frame** (D1 Definition 16.8) for each span from authenticated metadata: speaker, addressees, session, task, time and time zone, scope, preceding turn references, project and files in use. Unknown fields are recorded as unknown. No model runs on the synchronous capture path (§9.2).

### R7.2 Declarations at the agent write interface

**Fixed (proposed).** Declarations (D1 Definition 16.9) are required for agent principals (D-107). Two cases differ:

1. **Deliberate record writes.** The record-writing operations of §4.3 that an agent principal issues (`propose`, `record_question`, `record_inference`, `record_evidence_relation`, `record_objection`, `record_decision`, `record_coordination` and the like) take a `declarations` field, and a call without it is **refused**. An explicit empty declaration ("no referents") satisfies it.
2. **Captured turns.** `record_event` capture of an agent's turns never refuses, so that no evidence is lost: a captured turn without declarations is committed with `declarations: missing`, recorded as an **integration defect** of the capturing integration, and reported in processing coverage. An integration fails qualification at Gate 1a-core if more than the bound share of its captured agent turns lack declarations (R15).

For people, declarations are optional in both cases.

The core validates each declared referent: it exists, and the writer may read it. A referent the writer may not read is refused, as it would disclose by reference. A declaration is labeled as the speaker's and indexed into E2.

### R7.3 Renderings

**Fixed (proposed).** A standalone rendering (D1 Definition 16.10) is stored as an edit over the span: marked insertions, each with its link and basis, and the context it drew on. An agent's rendering arrives with its write (D-109); a processor's rendering for human text is produced later by priority (D2 §8). Both versions are indexed in E1 and E2; matches through an insertion carry `via: rendering_insertion`. A lexical route names the representation it searches: a match in a rendering is reported against the rendering revision, with the original span cited (D1 Definition 16.2), and an insertion-only match never appears as an original-text match. Author-supplied renderings are part of Slice 1a-core (R17).

### R7.4 Resolution

**Fixed (proposed).** The resolver produces resolution records (D1 Definition 16.11) in rings: context frame, local discussion, task and scope entities, wider memory. Each records its candidates, its basis revisions and the history position it was made at, and is labeled current or as-held (D1 F-51). It never uses as a basis a resolution its speaker has not confirmed; an adoption of a resolution is the adopter's own claim and does not qualify the resolution as a basis (D1 F-51). A correction of a resolution, or of a record it used, creates review obligations on what depends on it (§9.11). A processor's resolution is a UPMS-derived representation and carries the union of its inputs' tags (§7.4); a declaration is an authored record governed by its own scope and tags (§5.5, §7.4).

### R7.5 Extractors and migration

**Fixed (proposed).** Every extractor and resolver has a versioned processor identity (§11.1). A new version is introduced by background re-extraction; both versions serve until the new one covers the population it claims, and processing coverage names the version of every structural match. Retained outputs of earlier versions stay canonical records.

## R8. Commands that change or delete records

**Fixed (proposed).** A mutating command compiles to an exact target set and a preview (§12.3 for deletion; the same pattern for every bulk change). The confirmation binds the plan, the target revision set, the authorization context and the stated preconditions. At commit the core re-evaluates them; if the set or an effect differs, the commit is refused with a fresh preview (D1 F-53). An ambiguous referent in the command is asked about. Internal workers keep their existing typed authority (§4.3) and need no conversational confirmation.

## R9. Budgets, estimates and reuse

1. **Budgets by consequence class** (D2 §7.3) are profile values (§14.2 additions, R15). A plan's **effective cap** is the smaller of its class cap and the §14.2 query limits; a larger cap needs the deep-retrieval capability with its budget (§10.4), requested as a new plan under item 3. Class selection never widens the pilot profile. Every plan runs under its effective cap (D2 §7.4).
2. **Estimate before execution** from published statistics; an estimate above the budget leads to narrowing, a budget-limited answer with the estimate, or escalation.
3. **Escalation** (D-115): within its task budget an agent escalates on its own; beyond it, the integration asks a human, showing the estimate. The request and answer are recorded with the plan.
4. **Reference reuse.** A reference may replace text a session already received only where the exact revision and rendering are shown to be available to the current consumer; a release record proves exposure, not availability after compaction or resume (§8.2). An authorized explicit refetch is always allowed under current eligibility and budget; where availability is unknown, the span is supplied or the budget limit reported.
5. **Caches** of plans, resolutions and expansions follow §10.1: cache identity includes principal and rights context, scope, barrier epochs, snapshot and versions, and hits recheck eligibility.
6. **Processing queue:** order and reserved sweep share as in D2 §8, inside §9.5's liveness rule.

## R10. Storage economy

1. **Deduplication within a deletion unit only** (D-119). Payload bytes are shared only within one independently deletable unit (§12.3: an event revision for sources, an object revision for derived content). Wider deduplication needs a later decision with a defined domain, reference ownership and erasure disclosure.
2. **Occurrences stay distinct** (D1 F-52): shared postings or bytes never share interpretations, attribution, history or tags. Counts name their unit.
3. **Digests** are protected, tenant-scoped and keyed (§5.6).
4. **Physical tiers** (D-112): RAM, SSD and object storage, placed by liveness (§12.2's predicate) and use. Placement never changes eligibility, completeness or archive state; a curator-confirmed archive (§12.2) is a separate act. A plan that searched only some tiers reports the others in execution coverage.

## R11. Deletion at scale

**Fixed (proposed).** The states of §12.4 are kept (`requested`, `serving_blocked`, `purging`, `purge_failed`, `purged_live`, `complete`).

1. **Keys.** Each deletion unit's payload is encrypted under its own data key, wrapped by scope keys in the KMS. The key inventory names every recoverable copy: wrappers, caches (§14.2: at most 60 s), replicas and backups. No key is destroyed while it protects surviving content; survivors are rewritten first (D-119).
2. **Index segments** hold derived plaintext. The barrier stops serving at once (§9.4); a **purge scheduler independent of ordinary merging** rewrites every segment holding the target, removes temporary merge outputs, uses reserved I/O so ingestion cannot starve it, bounds segment size so a rewrite meets the live-surface target (§14.2: 24 h), and reports failures as `purge_failed`. Purge debt (bytes and segments awaiting rewrite) is measured. Purge capacity is sized to the bound lifecycle workload and maintenance concurrency (D2 §13): purge rewrites take priority over merges, and nonessential ingestion stops before purge would miss its target (§14.2 disk admission). Meeting the target for one segment does not show the aggregate target is met; T168 tests the aggregate, and a missed target is reported as `purge_failed`, never hidden.
3. **Claim.** Destroying a unit's data key would make its payload unrecoverable only if no other usable key path remains. Until the key hierarchy and KMS are qualified (Gate 0 feasibility), §12.4's sentence stands: "Per-unit cryptographic erasure is not claimed."

## R12. Recovery at scale

**Fixed (proposed):** the order of service. The RPO and RTO of §14.2 remain pilot targets.

1. **Minimum service** after a restore: the fidelity plane with the latest recovery-log position proven (§12.4), then E0. Until the other tiers are restored or rebuilt, execution coverage names them as unavailable, and no answer reports absence through them (D1 F-45).
2. **Restore or rebuild:** E1 and summaries are restored from backup where compatible and rebuilt otherwise; similarity indexes may be rebuilt last.
3. **A larger profile** states its own service order and targets (D2 §13 proposes them) and is requalified (D-120).

## R13. Write path

**Fixed (proposed).** The single logical committer per tenant (§9.1) and its ordering and snapshot semantics are kept; scope partitions are not commit domains. An acknowledged commit does bounded work under the bound workload; indexing, summaries, extraction and merges run after acknowledgement, within budgets that include their amplification. Bulk import runs in batches through the same committer and is admitted under the disk-admission rule of §14.2; a larger profile's bulk-import requirement (D2 §13) decides whether another topology is needed, which would reopen §9.1.

## R14. Stepwise discovery

**Fixed (proposed).**

1. **Broad step.** A first plan with only mandatory filters returns metadata summaries over the eligible population: counts by scope, time segment and record type, each with its unit and the snapshot it counted (D-117). Counts are computed under R5; a maintained count that cannot be shown to cover only eligible records is computed or withheld. Hub orientation and a small sample of similarity proposals are added, labeled.
2. **Facets** conditioned on the query (entity, tag, open obligation) are optional and budgeted, and labeled exact, partial, bounded or estimated. An unstructured or unknown population is always shown.
3. **Narrowing** issues a new plan that refines the last; continuation tokens (§10.1) carry the reuse.
4. **Unexplored parts** are carried in the final answer's execution coverage with their known sizes (D1 F-54).
5. **The trail** is the sequence of plans in the release records; a later investigator can start from it.

## R15. Profile additions (initial defaults)

These rows are added to the pilot profile of §14.2 by core 6.18.

| Parameter | Initial value or rule |
| --- | --- |
| Budgets by consequence class | D2 §7.3, as proposed defaults until the owner sets them (D-120) |
| Effective cap | The smaller of the class cap and the §14.2 query limits; larger only with the deep-retrieval capability and its budget |
| Engine latency | Pilot: the §14.2 targets. Larger profile: D2 §12 |
| Delta buffer | Scanned exactly by every plan; at most 10,000 spans or 60 s before publication |
| Summary rebuild | When the surviving share of a summary's atoms falls below 0.7 (D2 §3.5) |
| Processing sweep share | At least 20% of processing capacity (D2 §8) |
| Purge rewrite | Segment size bounded so one rewrite fits the 24 h live-surface target; purge I/O reserved ahead of merges |
| Declarations | Required for agent principals' record writes (refused without); on captured agent turns, at most 1% missing at Gate 1a-core qualification, each missing one an integration defect |

## R16. Invariants and tests

### R16.1 Invariants

| ID | Invariant | D1 | Slice |
| --- | --- | --- | --- |
| RT1 | Exact facts and assessments are separate fields; no assessment is derived from an exact fact | F-43 | 1a-core |
| RT2 | Similarity and hub routes never skip work and never support absence; their results are a separate group | F-44 | 1a-core |
| RT3 | Pruning uses only covering summaries under the publication protocol (R6); no false-negative prune | F-44 | 1a-core |
| RT4 | Absence is stated only for a plan with complete execution | F-45 | 1a-core |
| RT5 | Coverage reports every material limitation, never counts hidden records, and always carries the scope note | F-46 | 1a-core |
| RT6 | Every answer is grounded with per-statement support state; uncited text is orientation | F-47 | 1a-core |
| RT7 | Interpretations never replace text; confirmation, adoption and fidelity assessments are separate facts | F-50 | 1a-core (declarations, rule extraction, author renderings); 2 (model extraction, processor renderings) |
| RT8 | Resolutions record basis and position, are labeled current or as-held, and never rest on resolutions their speakers have not confirmed | F-51 | 1a-core (deterministic subset, R3); 2 (processor resolution) |
| RT9 | A mutating command commits only the confirmed exact set | F-53 | 1a-core |
| RT10 | Stepwise discovery reports unexplored parts and qualifies its counts | F-54 | 1a-core (metadata summaries); 3 (facets) |
| RT11 | Deduplication stays within deletion units; no key is destroyed while it protects survivors; purge rewrites segments within the target | — (D-119, §12) | 1a-core |
| RT12 | Placement in tiers never changes eligibility, completeness or archive state | — (D-112) | 4 |
| RT13 | A lexical match names the representation it matched in; no original-text match is reported for words absent from the original | F-43; Definition 16.2 | 1a-core |
| RT14 | Coverage carries capture extent, and every count carries its status | F-46; Definition 16.5 | 1a-core |

### R16.2 Acceptance scenarios

| Test | Scenario |
| --- | --- |
| T141 | Exact and similarity groups (RT1, RT2): a query for "login timeout" returns a passage "sessions stall during sign-in" only in `similarity_only`, labeled; it is not counted in `total_matches` of the exact group |
| T142 | Negation (RT1, RT7): a span "Sam did not approve deployment" with an extraction `approved(Sam, deployment)`: a structural match is returned with `via: extraction`, no speaker confirmation and no fidelity assessment shown as such, beside the original text; no support is implied |
| T143 | Absence for a plan (RT4): with execution complete, the answer states "no item of the population satisfies the plan at these versions"; with one partition skipped for budget, no absence is stated and the skip is reported |
| T144 | Insertion during a query (RT3): with the query's snapshot pinned, and publication, delta visibility and merge completion controlled independently, a span committed after the newest watermark, and an interpretation newly added to an old span, are each found through the delta buffer or reported unevaluated; a brute-force reference agrees |
| T145 | Deletion, merge and rebuild (RT3): after a sequence of deletions, merges and a summary rebuild, sampled plans agree with an independently implemented brute-force matcher over the same population (D2 §9.4) |
| T146 | Version mismatch (RT3): after an analyzer change, neither the summaries nor the postings of the old version are used for plans of the new one; segments not yet rebuilt are scanned under the new analyzer or reported unevaluated |
| T147 | Pruning logic (RT3): `NOT contains(foo)` prunes no segment; nested conjunctions and disjunctions of positive and negated atoms prune exactly where D2 §3.3 allows; a structural atom over unprocessed spans prunes nothing; a phrase is checked positionally after a term-level prune, including phrases near span boundaries |
| T148 | Hidden sources (RT5): a reader without `read` on a tagged record that matches gets the same coverage text and counts as a reader for whom no hidden match exists; `scope_note` is present in both |
| T149 | Reuse after compaction (R9): a session compacts, then asks for an exact source it received earlier; the span is supplied |
| T150 | Declarations (R7.2): an agent's `record_inference` without declarations is refused, and with an explicit empty declaration accepted; an agent's captured turn without declarations is committed with `declarations: missing` and an integration defect; an integration missing declarations on more than the bound share of turns fails qualification; a declared referent the agent cannot read is refused; a wrong but readable declared referent is labeled the agent's, and its correction creates review obligations on dependents |
| T151 | Resolution position (RT8): a Monday message resolved on Friday using a Wednesday record is labeled a current interpretation; the as-held view at Monday shows the mention unresolved |
| T152 | Resolution basis (RT8): a resolution whose only basis is another resolution its speaker has not confirmed is refused, including when that resolution has been adopted; the adopter's claim stays usable as that claim |
| T153 | Command binding (RT9): "delete all records tagged X" is previewed; a new record tagged X is committed before confirmation is committed; the commit is refused with a fresh preview |
| T154 | Deletion units (RT11): two event revisions with identical payloads are stored as separate units; deleting one leaves the other readable and intact |
| T155 | Purge (RT11): a deleted term is absent from every live segment within the live-surface target under sustained ingestion; purge debt is reported throughout |
| T156 | Minimum recovery service (R12): after a restore, E0 serves before E1 is rebuilt; lexical plans report E1 unavailable and state no absence |
| T157 | Tiers (RT12): a record placed in the cold tier still appears in proactive retrieval unless archived; a plan that searched only hot tiers reports the cold tier as not searched |
| T158 | Escalation (R9): a decision-basis question whose estimate exceeds the task budget asks a human with the estimate; within the task budget it proceeds and records the escalation |
| T159 | Stepwise discovery (RT10): the broad step shows counts with units and a snapshot, an unknown population, and labeled similarity samples; after narrowing, the final answer lists the unexplored parts with their sizes |
| T160 | Grounding (RT6): every statement of an answer an agent receives cites spans with its support state; hub text without citations is labeled orientation; the integration's rendering keeps the limitations its class requires |
| T161 | Fairness (D2 §8): under the bound lifecycle workload, an obligation-bearing span that is never retrieved is processed within the processing window (D2 §8 item 4), or reported overdue |
| T162 | Occurrences (RT7): the same sentence in two sessions gets two resolutions with different referents and dates; neither inherits the other's interpretation |
| T163 | Rendering matches (RT13): a lexical query for "Bob Lee" over "He fixed it yesterday." with the rendering "[Bob Lee] fixed …" returns a match against the rendering revision, with the original span cited and `via: rendering_insertion`; no original-text match is reported |
| T164 | Capture gaps (RT14): with a known capture gap for a session, a complete execution over the retained population still reports the gap under `capture`, and the agent's reply carries it where its class requires |
| T165 | Count status (RT14): a plan stopped at its effective cap reports its total as a lower bound; a page limit on a complete execution reports an exact total with 30 returned |
| T166 | Effective cap (R9): a decision-basis plan estimated at 4 s without the deep-retrieval capability stops at the §14.2 work budget and is reported budget-limited; with the capability and budget, it runs as a new plan |
| T167 | Estimates and hidden content (R5, D2 §7.2): two worlds that differ only by hidden matching records show the same estimate to the reader |
| T168 | Aggregate purge (RT11): deleting one item in each of many segments during sustained ingestion and a concurrent rebuild either meets the live-surface target for every deletion, with ingestion throttled first, or reports `purge_failed` for those missed; purge debt is reported throughout, and a crash during a rewrite leaves no deleted content served |

## R17. Delivery

| Slice | Adds from this annex |
| --- | --- |
| Slice 1a-core | R1 to R6, with the R3 early subset; R7.1, R7.2, author-supplied renderings (R7.3) and rule-based E2 extraction; R8 to R11; R12 order of service at pilot size; R13; R14 items 1, 3, 4 and 5; RT1 to RT7 (declarations, rule extraction, author renderings), RT8 (deterministic subset), RT9 to RT11, RT13, RT14; T141 to T150, T153 to T156, T158 to T160, T163 to T168 |
| Slice 2 | R7.3 processor renderings for human text and R7.4 resolution by processors; model extraction for theory records; RT7 (model extraction), RT8; T151, T152, T161, T162 |
| Slice 3 | Structured statements from the checking annex into E2; query-conditioned facets (R14 item 2); T159's facet part |
| Slice 4 | Physical tiers beyond one tier (RT12, T157); disk-resident similarity indexes; a larger profile's qualification (D2 §13) |

## R18. Open items

| Item | Evidence still required | Owner and boundary |
| --- | --- | --- |
| Pruning correctness | Brute-force agreement under concurrent insert, merge, deletion and rebuild (T144 to T147) | Architecture and evaluation owners; Gate 1a-core |
| Translation error | The gold set and per-field, polarity, resolution and declaration error rates (D2 §9) | Evaluation owner; before Gate 2 relies on model extraction |
| Workload and limits | The owner's setting of D2 §10.2 and §13 values (D-120) | Product owner; before measurement |
| Key hierarchy and purge | KMS feasibility for per-unit keys; purge-rewrite throughput at the pilot size | Security and infrastructure owner; Gate 0 feasibility, tests at Gate 1a-core |
| Declaration reliability | Missing and wrong-referent rates for the Codex integration | Runtime and evaluation owners; Gate 1a-core |
| Larger profile | A bound profile above the pilot envelope, with its service order and targets | Product owner; before any claim above 10 GiB |
