# UPMS Design Note: Retrieval at Scale, Translation and Economy (Revision 2), 5 November 2026

5 November 2026 · written by Claude (AI, Opus 5.5) from a discussion with the product owner (Sam) · design direction, not authority

**Status.** This note records the approach the owner directed in decisions D-101 to D-120 (`UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`, `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`). It revises revision 1 (`UPMS_Retrieval_Translation_Economy_Design_Note_2026-11-05.md`, SHA-256 `49412e997735253135885fa78bcbbfdf81fb806b89f3a7a06c29073362188abb`, frozen) to answer the Codex critique (`UPMS_Retrieval_Design_Note_Codex_Critique.md`, SHA-256 `aae43b0c104791ea35b622e1ef286a38c200d1ccc9e1a5847ee2a16661eef923`); the change map is §11. It is an input to three texts still to be written: a D1 addendum, a D2 retrieval and indexing candidate, and a revision of core 6.17. It defines nothing normatively; where it says "must", it states what those texts are to establish. Accepted-current authority is unchanged: D1 1.16, core 6.17 and anonymous-review annex 6.7. Section references (§n) are to core 6.17 unless another text is named.

## 1. The problem

Without expiry (D-25), memory grows to whatever storage permits: gigabytes within a project's life, terabytes over years or through bulk imports. At the pilot capture cap (1 event/s, §14.2) with events of about 4 KB, raw capture alone could add about 126 GB a year to one tenant, before release records, processing outputs, indexes and imports; that is a ceiling under the cap, not a forecast. At that size:

- **a full scan is too expensive** for routine questions;
- **summaries and approximate methods are fast but lossy**: a hub compresses by meaning, so a detail it dropped is a missed hit, and a model filling the gap produces what looks like hallucination;
- **speed and precision need a hybrid**, in which loss is confined to places that are declared and cannot be mistaken for fact.

Core 6.17 already makes canonical records authoritative and indexes, hubs and caches derived and rebuildable (§4.1, §9.5, §9.6, §14.3), and fixes what retrieval means: eligibility before ranking (§10.1), intent routes and the absence rule (§10.2), the coverage contract (§10.3), the hub hierarchy (§10.5) and archive (§12.2). It leaves the retrieval method to D4 ("Partition and filter strategy is D4", §10.1) and sizes the pilot at 10 GiB (§14.2). What is missing is governed design for the scale D-101 asks for and for the retrieval guarantees D-102 to D-120 direct; the decision records raise this as a SERIOUS CHALLENGE to the adequacy of core 6.17 for D-101 and open D2 (§9).

**What exactness can and cannot promise.** An index lookup can be exact for a stated predicate. Nothing makes a predicate capture the question, makes an extraction faithful to its text, or makes a passage support an answer; those are fallible judgments. This note keeps the two apart everywhere (D-118).

## 2. Two planes

| Plane | Holds | Promise |
| --- | --- | --- |
| **Fidelity** (system of record) | Canonical records, including retained model outputs with their manifests (§11.2: "Novel prompt, compaction, overview or model-generated content is itself a canonical record"); immutable, encrypted payloads; append-oriented | Complete. Completeness never depends on an index. Write work is bounded and amortized under a stated workload (§6.5), not constant at every size |
| **Serving** (derived) | Indexes, searchable materializations of retained outputs, hubs' search structures, caches, compressed vectors | Rebuildable from the fidelity plane. May be lossy or approximate, never silently: each structure declares its watermark and version, and coverage names what was searched |

A model-produced rendering cannot be reproduced by rerunning its model, so the rendering itself is a canonical record; only its searchable forms are serving state.

## 3. The deterministic tiered index (D-102, D-105)

### 3.1 Tiers

| Tier | Contents | Built by | What is exact, and what is not |
| --- | --- | --- | --- |
| **E0 Identity and references** | IDs, revisions, protected digests, timestamps, scope, author, session, source, file paths; citations and relation edges | Capture metadata and explicit acts | Exact. Modification, deletion propagation, lineage and impact run here, never through search |
| **E1 Lexical** | Positional inverted index over the original text: exact phrases, versioned normalization with offset maps back to the original, n-grams for unspaced scripts | A deterministic, versioned analyzer | Exact for literal predicates under that analyzer; needs no interpretation, so it bypasses both translation points of §5 |
| **E2 Structural** | Tags, coordination keys, entity bindings to the vocabulary, typed relations, structured statements, code symbols, URLs, dates, numbers with units | Rule-based extractors; the writing agent's declared terms; versioned model extractors (D-103) | Lookup is exact over what was extracted. **Processing extent** ("v3 processed 87%") is reported, and is not extraction recall: an extractor can process every record and miss every negation. Extraction fidelity is a measured error (§5.7), never implied by the watermark |
| **A Approximate** | Embeddings, hubs, narratives | Models | Neither; orientation and added candidates only |

The index unit is the **span**, which rolls up to its record. The first product uses an established positional inverted index and ordinary canonical storage (§10).

### 3.2 A query: mandatory filters plus discovery routes

A compiled query has two parts:

- **Mandatory filters** define the population: eligibility (always the core's complete predicate, §3.4), scope, time window, record types, archive inclusion. Every returned item satisfies them exactly.
- **Discovery routes** find candidates within the population: lexical predicates, structural predicates, approximate similarity and hub routing. Their results are unioned, and each item names the routes that found it.

An approximate candidate must satisfy the mandatory filters; it need not satisfy a lexical predicate it was found without. This is what lets "sessions stall during sign-in" surface for a query about "login timeout".

### 3.3 Approximation may only over-include, under a publication protocol

**Pruning** a region is allowed only through summaries with false positives and no false negatives for the predicate in question. Relying on that guarantee is relying on an error property, so its correctness belongs to D2 (§9). It holds only if:

- **a summary covers every matching visible span** under the query's analyzer, field semantics, revision view and index version. A stale summary is safe after deletion (it over-includes) and unsafe after insertion, alias expansion or an extractor change;
- **Bloom-filter bits are never cleared** on deletion; a summary is rebuilt from the surviving population;
- **merged summaries are built over the complete merged input**; bitwise union only for compatible filter configurations;
- **segment contents, summaries, analyzer identities and covered watermarks are published together**; concurrent additions are covered by an explicit delta, or coverage is reported incomplete;
- **a missing, corrupt, incompatible or insufficiently current summary means "cannot prune"**;
- **polarity is respected**: absence of `foo` prunes a region for `contains(foo)`, never for `NOT contains(foo)`; conjunction, disjunction, negation and unknown structural values each get a stated safe rule;
- **phrases are preserved** across indexing boundaries, with offset maps to the original text.

Embeddings, nearest-neighbour search, hubs and narratives have errors in both directions; they never prune and never establish absence.

**Exact checks on every returned item** (D-118): the source is the intact current canonical revision (or the stated historical one); the item is eligible now; it satisfies the mandatory filters; and, per route, the exact predicate it matched. These are reported as separate facts. Whether the item is relevant, whether its interpretation is faithful and whether it supports the answer are separate, fallible assessments (§4).

### 3.4 Partitions give locality, not a speed guarantee

Tenant → scope → time segment → index segment. This gives locality and lets bounded questions ("this scope, last quarter") skip most of the corpus. It is not a sublinear guarantee: a common term or a broad predicate matches every branch, and "the earlier decision about this", with no time, gets little from time segmentation. D2 states a cost envelope per **workload family** (common and rare terms, broad negatives, phrases, many-scope queries, poorly structured imports), not per corpus size alone (D-120). The summaries used for pruning may be the inverted index's own per-segment term dictionaries; no duplicate summary tree is required. Where selectivity is poor, an exact budgeted search remains available (§6.1).

**Partitioning does not implement eligibility.** Eligibility is the core's complete predicate (§7.3.4: own-record and oversight entitlements, session grants, restriction tags, quarantine, barriers, lineage exclusions), applied before anything reaches a ranker, snippet generator or processor (§10.1). It is applied on every path: hits, the resolver's inputs, vocabulary expansion, cost estimates, facet summaries and continuation tokens. Hidden records never appear in exposed counts or plans. Partition choice is an optimization inside that predicate.

### 3.5 Scale arithmetic (planning estimates)

Decimal units. For 1 TB of text in chunks of about 2 KB (about 500 million chunks):

| Component | Size |
| --- | ---: |
| float32 vectors, 1,024 dimensions | 2,048 GB |
| int8 vectors | 512 GB |
| 64-byte product-quantized codes | 32 GB |
| HNSW links at about 8·M bytes per vector, M = 16 / 32 | 64 GB / 128 GB |
| one 64-bit identifier per chunk | 4 GB |

These omit metadata, offsets, lexical positions, replicas, staging, compaction headroom and concurrent rebuilds; D2 replaces them with measured steady-state and peak footprints. They show that full-precision vectors for a TB corpus do not fit in memory, so a disk-resident approximate index with compressed codes in memory is a candidate design (DiskANN-style designs are credible, but their published results do not qualify UPMS's embeddings, filters or workloads). An embedding-model change is a versioned rebuild whose duration D2 estimates from measured throughput.

## 4. Answers (D-104, D-118)

1. **The request is compiled** into mandatory filters and discovery routes (§5.5).
2. **The engine runs them**: exact routes exactly over the pruned partitions; approximate routes add candidates.
3. **Each item carries separate facts and assessments**: source intact; eligible; mandatory filters satisfied; route matched (exact predicate, or "similarity only"); match via original text or via an interpretation (an extraction or a rendering insertion), and that interpretation's state (unconfirmed, confirmed by its speaker, adopted, fidelity-checked); and, where made, an attributed assessment of relevance or answer support.
4. **The response returns the plan**: filters, routes, partitions, tiers, index and extractor versions, and coverage (§6.1). The asker can see what was looked for, so a question the plan does not capture is visible.
5. **Answers are grounded in cited spans.** A citation shows where an answer comes from; it does not by itself show that the span supports it. Support is an assessment, labeled. Uncited hub text is orientation only.
6. **Semantic candidates no exact predicate matched** appear only in an explicitly labeled route ("similar passages, not matched by your query terms") (D-118).
7. **Absence is stated only for the plan**: "no eligible record in population X satisfies predicate P", never "memory contains no approval". This is the accepted absence rule (§10.2) applied to compiled predicates.
8. **Consequential questions may scan exhaustively** over a pruned region (one scope, one quarter): exact for its predicates, budgeted, explicit.
9. **Mutating commands bind exact targets** (§5.5 item 4).

## 5. The translation layer (D-106 to D-109)

Fidelity is at risk at two points, both translations from natural language into structure driven by a model's reading: **ingestion** (text to structured decomposition) and **query compilation** (request to predicates). They share one schema, one vocabulary and one resolver, so a query meets the records in the representation they were decomposed into. The layer reduces some errors and makes others visible; it cannot make interpretation deterministic.

### 5.1 Annotate, never replace

The original text is never replaced. Every structure, resolution or rendering is an attributed, versioned layer over exact spans, with its basis, and can be corrected and re-derived. This generalizes D1 Definition 2.3 (an extraction is an interpretation attributed to its extractor, shown unconfirmed until the speaker confirms it) and D1 F-2 ("An interpretation `I(s)` never supports a decision basis unless it is confirmed by the speaker or adopted"; adoption is a separate route and leaves the interpretation unconfirmed), and the core's time rule (§5.6: a relative expression keeps its raw wording, its resolution and the basis). "Text wins" when text and structure disagree (checking annex §5.7).

### 5.2 Ingestion

1. **Context frame.** Speaker, addressee, session, task, time zone, scope, preceding turns, open files and project are captured as metadata (E0), with unknown fields recorded as unknown. Authenticated speaker metadata resolves the outer utterance's "I" and "you"; it does not resolve quoted speech, reported dialogue, role-play, several addressees or references inside pasted content, which stay interpretations.
2. **Declaration at the source** (D-107). An agent's write declares its referents and index terms. A declaration is an authenticated assertion by its author: the core validates that each declared identity and revision exists and is eligible for the writer, and labels the declaration as the author's. It is not a certificate of fidelity, and an agent cannot confirm a human speaker's meaning by declaring it.
3. **A small typed schema over a curated vocabulary.** Unknown terms become proposals, never invented concepts (checking annex §5.8).
4. **Slots for the operators models drop:** negation, modality (D1 F-1), conditions, quantifiers, tense and time, nested attribution, hedges. Verification concentrates on them.
5. **Field anchoring.** Each field points to the substring it came from; a field without one is marked inferred and states its basis.
6. **Ambiguity kept:** `ambiguous{candidates}` rather than a guess.
7. **Independent checks, by priority:** a round trip (structure rendered back and checked against the span by a different model, for nothing invented and nothing important omitted); two extractors, with disagreement recorded as ambiguity, not settled by vote; deterministic checks of dates, units and entity IDs. Each check is an attributed fidelity assessment, not proof.
8. **No model on the synchronous capture path** (§9.2). Author-supplied declarations and renderings arrive with the write; extraction by UPMS processors runs after capture.

### 5.3 Standalone renderings

A span's **standalone rendering** is a minimal edit in which every insertion is marked as added and linked, like an editor's brackets:

```text
original:   "He fixed it yesterday."
standalone: "[Bob Lee →principal] fixed [login timeout bug #412 →record] on [2026-11-04 ←capture time]."
```

Both are indexed; a hit found only through an insertion is labeled "matched via interpretation". The original and the rendering are always shown together. "Standalone" does not mean the span needs no other context: a rendering states the context it drew on (earlier turns, conditions, nested attribution), and a citation names the context needed to read the span. Most spans need no insertion, so a rendering is stored as an edit over the original. Agent writes get one at write time from the authoring agent; human text gets one in later passes by priority (D-109). Renderings are canonical records; their searchable forms are serving state (§2).

### 5.4 Resolving with the memory

Resolution proceeds in rings: the context frame, the local discussion, the task and scope entities, then wider memory. Each resolution is an interpretation with its candidates and basis. The rules:

- **Two distinct reads** (D1 F-31, §9.9): reconstruction as held at the source's position uses only what existed then; a current interpretation of an older source may use later records and is labeled as current. A later interpretation is never backdated into an earlier view.
- **Bound bases:** a resolution binds the exact revisions it used and its snapshot.
- **Dependencies are tracked:** a correction of a resolution, or of a record it used, creates review obligations on what depends on it (§9.11).
- **Scope:** resolution uses only inputs eligible under the core's complete predicate for the source's scope and the resolving principal, states whose authority it ran under and which processors received its context (§7.4 processor eligibility). A resolution or rendering made by a UPMS processor is a UPMS-derived representation and "carries the union of its inputs' tags" (§7.4); one declared by an authoring agent is an authored record, governed by its own scope and tags as the writer decides, with its provenance shown (§5.5, §7.4).
- **No self-reinforcement:** a resolution never cites another unconfirmed resolution as its basis. Confirmation attributes intended meaning to the speaker; it is not independent verification, and two confirmed readings can share one mistaken identification.

Linking a mention to a person is an identification act: an interpretation the speaker can confirm, limited to identities eligible in the source's scope (D-108).

### 5.5 Query compilation

1. **A small typed query language**, produced under a grammar and checked against the schema and vocabulary; an invalid query is rejected or visibly repaired.
2. **The same resolver**, from the asker's context frame and session; the plan shows each resolution ("he = Bob Lee, from your previous turn").
3. **Over-generate discovery routes, then check:** aliases, related concepts, both renderings and several phrasings, unioned within the mandatory filters.
4. **Mutating commands bind exact targets.** A command that changes or deletes records compiles to an exact target set, shown as a preview (§12.3 for deletion), and the confirmation binds the plan, the target revisions, the authorization context and the preconditions. The core revalidates them at commit; if the effect changed (a matching record was added, a target was revised), a fresh preview is required. "Delete all matching records" never expands silently. If a referent is ambiguous, the system asks. Internal workers keep their existing typed authority and need no conversational confirmation.
5. **Misses are diagnosable:** for a reported miss, the system shows which filter or route excluded it, or that no route reached it. The fix goes into the vocabulary or an extraction.

### 5.6 What is irreducible

If the source is itself ambiguous, or the writer was vague, no method recovers what was not said; the system preserves the ambiguity and says so. A compiled plan can miss the question; showing the plan makes that visible but does not prevent it. Full checking of every span at TB scale is unaffordable, so checks run by priority (§6.3).

### 5.7 Measuring the chain (D-111, D2)

Per-field precision and recall and coreference accuracy are needed but not enough; a perfectly executed index cannot repair a plan that excludes the answer. D2 measures separately:

- exact-predicate agreement with an independently justified exhaustive reference;
- ingestion fidelity, including negation, conditions, quantities and attribution;
- question-to-plan fidelity;
- end-to-end passage recall and supported-answer error;
- abstention, unresolved questions, latency and spend;
- the same under permission filtering, archive, stale indexes and heavy deletion.

Approximate-index recall against exact vector neighbours is kept apart from recall of passages that answer the question. Final scores use held-out sessions and queries; corrections used for development do not also score it. Asymmetric loss (D-111) does not by itself stop a system that always abstains, so the owner sets useful-answer and cost requirements alongside error limits (D-120).

## 6. Economy (D-110 to D-115, D-117 to D-119)

**Spend in proportion to value; report what was lost in proportion to its consequence.** Lossless everywhere is unaffordable; silent loss is unacceptable; between them is budgeted, declared loss.

### 6.1 Coverage dimensions

A response reports independent dimensions, each with its counting unit (spans, records, sources) and reasons; several can apply at once. The answering agent carries any limitation material to the question into its reply (D-110).

| Dimension | Reports | Example |
| --- | --- | --- |
| **Execution** | Partitions and tiers evaluated or skipped; budget stop; total matches against returned matches; continuation | "Searched 2 of 9 partitions; an exhaustive search would cost about N. Continue?" / "312 matches, 30 shown" |
| **Processing** | Extractor and resolver versions and their extent; unprocessed populations | "40 matching sessions not yet indexed for entities" |
| **Availability** | Source bytes unavailable, restricted or deleted | "2 sources are restricted; 1 was deleted" |
| **Interpretation** | Matches via interpretations and their state; ambiguous sources | "The note supports either A or B" / "matched via an unconfirmed reading" |
| **Answer support** | Whether the answer's statements are assessed as supported by cited spans, by whom | "Supported by 2 cited spans (assessed by the answering agent)" |

"No match for this plan over population X" replaces revision 1's "insufficient record": a full search of a compiled plan does not show that memory holds no relevant natural-language evidence. "Similarity only" items are a route (§4 item 6), not a completeness status.

The planner **estimates cost before running**, from index statistics, so "too costly" can come before the spending; estimates can be wrong, so runtime caps apply as well. **Evaluation is asymmetric** (D-111; §5.7).

### 6.2 Storage

- **Deletion boundaries first** (D-119). Content is deduplicated only within an independently deletable unit (the core's default units: an event revision for sources, an object revision for derived content, §12.3), accepting extra storage. Wider deduplication waits for measured need, and then needs a defined deduplication domain, reference ownership and erasure disclosure.
- **Occurrences stay distinct.** Shared bytes or postings are never a shared interpretation: "He fixed it yesterday" in two sessions has two speakers, referents and dates, and identical text can differ in authorship, correction, archive state, permissions and evidential independence (§5.3: copies of one source are not independent support). Counts state whether they count spans, records, payloads or sources.
- **Digests are protected**, tenant-scoped and keyed (§5.6: "no durable plaintext hash of a sensitive value"); a digest is never an access capability or a source identity.
- **Indexes:** compressed posting lists; for the approximate tier, compressed codes in memory and full vectors on disk where measured need justifies it; embeddings only for spans worth embedding; renderings stored as edits.
- **Physical tiers** (D-112): RAM, SSD and object storage by liveness and use. Placement is not the curator-confirmed archive transition (§12.2). A search of hot tiers only is incomplete for a whole-population predicate while relevant cold data is unsearched, and coverage says so.

### 6.3 Compute and tokens

- **Ingestion cascade:** metadata, the lexical index and rule-based extractors on everything; cheap local models by priority; LLM extraction, rendering and checks by value. A skipped step never drops text; the record is reported unprocessed (checking annex §9.8).
- **Lazy deepening within the core's liveness rule.** Deep processing responds to "explicit requests, obligations, retrieval need, consequential reliance and a bounded age-weighted background sweep, so rarely retrieved obligations are not starved" (§9.5). First use may return a qualified shallow result or deferred processing. The lexical baseline covers everything, so a record that shallow routes cannot find is still reachable literally; unprocessed populations are always visible. That most records are rarely re-read is a workload assumption to measure, not a premise.
- **Checks by consequence:** double extraction and round trips for records a decision relies on or that are retrieved often.
- **Budgets by consequence class:** orientation, recall, explanation, decision basis, mutating command, each with a cap and a check level; stop once the answer suffices for the request's stakes.
- **References, not documents;** nothing a session already received is resent (release records track it); plans, resolutions and expansions are cached under the eligibility rule of §10.1.
- **Escalation** (D-115): within the task budget an agent escalates on its own; beyond it, it asks a human with a cost estimate.
- **Value model:** budgets by class, the ratified importance ordering (§12.1 rule 4: it ranks, never decides) and measured cost-versus-quality curves. A value-of-information optimizer is deferred for simplicity. Operational estimates of runtime, yield or cost are not probabilities of a claim's truth, so D1's bar on stored confidence does not forbid them; each would need its own defined meaning.

### 6.4 Loss ledger

Known losses are recorded: truncation, skipped partitions, unprocessed spans, quantization on the approximate route, summarization in hubs, an exhausted budget. Meaning silently dropped by an extractor or a summary cannot be listed without an independent oracle, so for semantic loss the ledger records the method, inputs, processing extent and measured error limits (§5.7), never a claim to list every omission. A test checks, for example, that a budget-truncated search never returns "no match".

### 6.5 Write path

Appending payloads keeps write work from growing with the archive, but an acknowledged commit also includes identity checks, metadata indexes, authority validation, expected revisions, dependencies, epochs and outbox work, and background compaction and rebuilds consume shared resources. The promise is bounded, amortized work under a stated workload, including that background amplification. The single logical committer per tenant (§9.1) and its ordering and snapshot semantics are kept; scope partitions do not become independent commit domains. Whether bulk import needs batching or another topology is decided after D2 states a bulk-ingestion requirement (D-120).

### 6.6 Deletion at scale (D-113, D-119)

Serving block, removal of a reference, cryptographic erasure and physical reclamation are different events, and the core's states are kept: `serving_blocked`, `purging`, `purge_failed`, `purged_live`, `complete` (§12.4).

- **Keys:** each independently deletable unit's payload has its own data key under a key hierarchy that names every recoverable copy: wrappers, caches, backups, replicas. Destroying a unit's key is cryptographic erasure of that payload only if no other usable key path remains. No key is destroyed while it protects surviving content; survivors are rewritten first (D-119).
- **Index segments hold derived plaintext** (terms, snippets, vectors, metadata). Tombstones and barrier epochs stop serving at once but erase nothing. A **purge scheduler independent of ordinary merging** rewrites affected segments: bounded segment sizes, cleanup of temporary merge outputs, reserved I/O so ingestion cannot starve it, measured purge debt, failures reported as `purge_failed`. The 24-hour live-surface target (§14.2) is met by that rewrite, never by tombstoning.
- **The stronger claim waits:** "Per-unit cryptographic erasure is not claimed" (§12.4) stays until the key hierarchy and the KMS are qualified (Gate 0 feasibility).

### 6.7 Recovery at scale

Restoring 1 TB in four hours alone needs about 69 MB/s sustained, before metadata recovery, validation, recovery-log replay and index work; rebuilding embeddings takes longer. So recovery must not mean "rebuild everything before useful service". The core revision states: the minimum service after recovery (the fidelity plane with the latest recovery-log position proven, §12.4, then the lexical baseline); which indexes are restored from backup and which rebuilt; and how partial availability is reported in coverage. The RPO and RTO of §14.2 are pilot targets; a larger profile states its own and is requalified (D-120).

## 7. Latency (D-114)

p95 at most 1 to 2 s on hot tiers, set exactly with the D2 cost model for a stated workload, concurrency and hardware (D-120). Engine latency is measured apart from query compilation, remote inference, source fetch, first-use deepening and release-record commit. Cold-tier queries may be slower and are labeled with the tiers searched. The ratified pilot targets (§14.2: 500 ms warm, 2 s cold, excluding remote inference) stay in force at the pilot size.

## 8. Procedural discovery (D-116, D-117)

**When the target is unknown, start broad and cheap and narrow; when it is known (an ID, a key, an exact phrase), go straight to exact lookup.** Start at the cheapest step that can answer.

1. **The broad step starts with cheap metadata summaries** over the asker's eligible population: counts by scope, time segment and record type, with defined counting units and a snapshot identity; hub orientation and a sample of approximate candidates, labeled (D-117). Summaries are computed under the complete eligibility predicate; where a maintained count cannot be shown to cover only eligible records, it is computed or withheld.
2. **Facets conditioned on the query** (by entity, tag or open obligation within the matches) are optional and budgeted; they may be partial, bounded or estimated, each labeled as such. An **unstructured or unknown** population is always shown, so counts of extracted annotations never read as a complete overview of meaning.
3. **Each narrowing step refines the previous plan**, reusing cached results through continuation tokens (§10.1).
4. **Unexplored is not excluded.** Branches not pursued are reported in the final coverage with their known sizes, so a narrowed search never reads as exhaustive. This follows the ratified frontier rule: "nothing beyond it is reported as sound or absent" (§13).
5. **The investigator's weights are working estimates,** held by the investigator; they are not stored as confidence on a record (D1 §9). If recorded, they are an attributed claim with reasons.
6. **The trail is kept:** each step's plan and coverage (release records already record what was returned), so a later investigator resumes rather than repeating the broad pass, and a miss can be diagnosed.
7. **Stop rule:** the target is found with its checks reported, the asker is satisfied, or the budget is reached; the answer then carries its coverage (§6.1), with escalation under D-115.

The rule applies to people and agents alike; a person's interface presents the same map.

## 9. Routing

**Why D2 opens.** Core §1.4 needs no D2 parent while, among other conditions, there is "no consumer relying on a guaranteed approximation bound". The no-false-negative pruning guarantee of §3.3 is a relied-on error property of approximate membership structures, so that condition is at least engaged; and D-101, D-110, D-111 and D-114 put requirements on estimators, error models and cost models. D2 opens on both grounds, and the D1 addendum and core revision revise the domain determination of D1 §9 and core §1.4 explicitly.

| Text | Establishes |
| --- | --- |
| **D1 addendum** (a successor to D1 1.16) | Mandatory filter, discovery route and retrieval predicate; execution completeness relative to a plan, kept apart from interpretation fidelity, relevance and answer support; the coverage dimensions; grounded answer and assessed support; absence stated only for a plan; context frame with unknown fields; standalone rendering with marked insertions and stated context; resolution as an interpretation with candidates, bound basis and the two reads; declaration as an authenticated assertion; the principle that a loss is never presented as fact; how strongly limitations are stated per consequence class; the revised D1 → D2 hand-off |
| **D2 candidate** (new) | The pruning guarantee and its publication protocol, with false-positive and cost models; safe rules for Boolean polarity and unknown values; the chain measurements of §5.7 with held-out evaluation; cost estimation with runtime caps; workload families and the cost envelope; the processing cascade and default budgets by class; quantization, footprint (steady and peak) and rebuild-time estimates; proposed defaults for workload, concurrency, bulk import and degraded recovery for the owner to set (D-120); the latency target |
| **Core revision** (a successor to core 6.17) | The two planes, with retained model outputs in fidelity custody; tiers E0 to E2 and A; mandatory filters and discovery routes; the complete eligibility predicate on every retrieval, resolution, estimate and facet path; partitions and segment lifecycle with the publication protocol; the shared resolver and compiler and the typed query language; context frames and declarations on the agent write interface; mutating commands bound at commit; extractor versioning; index rebuild and migration; physical tiering kept apart from archive; deletion units, the key hierarchy and the purge scheduler, keeping the §12.4 states; minimum service after recovery; the write-path workload statement; budgets in the profile; deterministic extraction and coverage dimensions moved into Slice 1a-core; the revised §1.4 |

Encryption layout, deduplication ownership and service topology stay in D3 and D4 unless an algorithmic guarantee needs them in D2. The three texts are reviewed together outside the Claude family and ratified by the owner before the Slice 1a-core D4 specification. The checking annex's structured statements stay where they are until the core revision says which parts move.

## 10. First product and what waits

**Now, as invariants and lifecycle decisions:** the two planes; original text kept; stable references; the lexical baseline; attributed annotations and declarations (D-107, D-109); versioned processing; complete eligibility on every path; coverage dimensions; budgets and escalation; deletion units and the purge scheduler; the minimum recovery service.

**Built in the first product:** an established positional inverted index; ordinary canonical storage; rule-based extractors; the context frame; author declarations and renderings; a simple approximate tier.

**Waits for measured need, with its ownership and lifecycle decided now:** custom summary trees; high-cardinality query-conditioned facets; deduplication beyond a deletable unit; disk-resident approximate indexes; full-precision vector reranking; parallel embedding-rebuild machinery; a value-of-information optimizer. No TB experiment is required before drafting or pilot qualification; larger-scale qualification attaches to the profile that claims that scale.

## 11. Change map from revision 1

| Critique item | Change |
| --- | --- |
| SC-R01 | §1 "What exactness can and cannot promise"; §3.1 E2 row (processing extent is not recall); §3.2 mandatory filters and discovery routes; §3.3 exact checks reported separately; §4 items 3 to 7; §6.1 (D-118) |
| SC-R02 | §8 items 1 and 2 replace the exact cheap map (D-117) |
| SC-R03 | §6.2 deletion boundaries; §6.6 keys, survivors and purge (D-119) |
| R-01 | §6.1 composable coverage dimensions with counting units; "no match for this plan" replaces "insufficient record"; "similarity only" becomes a route; §6.4 semantic loss recorded by method and measured limits |
| R-02 | §5.2 items 1 and 2 (outer speaker only; declarations as authenticated assertions); §5.3 renderings state their context and are shown with the original; §5.1 quotes F-2 exactly, including adoption |
| R-03 | §5.4 two reads, bound bases, tracked dependencies, confirmation is not verification |
| R-04 | §9 "Why D2 opens"; §6.3 value-model wording; D2's scope limited to retrieval, error and cost semantics |
| R-05 | §3.3 publication protocol |
| R-06 | §3.4 locality, workload families, no duplicate summary tree, exact budgeted fallback |
| R-07 | §3.5 decimal units, parameterized HNSW, omitted overheads, candidate design not conclusion, rebuild time from measured throughput; GPU-days estimate removed |
| R-08 | §5.7 chain measurements; §7 latency components and runtime caps; useful-answer requirement (D-120) |
| R-09 | §2 and §6.5 bounded amortized write work; single committer kept |
| R-10 | §3.4 complete eligibility on every path; §5.4 resolver authority, processor eligibility and the tag rules of core §7.4 |
| R-11 | §6.2 occurrences distinct, counting units, protected digests |
| R-12 | §6.2 placement is not archive, hot-only coverage; §6.7 recovery |
| R-13 | §6.6 purge scheduler, states kept |
| R-14 | §6.3 lazy deepening within §9.5, measured assumption, lexical baseline; §2 retained outputs canonical; §5.2 item 8 no model on the capture path |
| R-15 | §5.5 item 4 commit-time binding; §1 the challenge scoped to D-101 (see the D-117 to D-120 record §3) |
| Reference errors | §4 item 1 now points to §5.5; §1 places the absence rule in §10.2 |
| Simplicity | §10 |
