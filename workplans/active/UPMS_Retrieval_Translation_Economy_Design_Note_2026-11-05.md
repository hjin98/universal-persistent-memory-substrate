# UPMS Design Note: Retrieval at Scale, Translation and Economy, 5 November 2026

5 November 2026 · written by Claude (AI, Opus 5.5) from a discussion with the product owner (Sam) · design direction, not authority

**Status.** This note records the approach the owner directed in decisions D-101 to D-116 (`UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`). It is an input to three texts still to be written: a D1 addendum, a D2 retrieval and indexing candidate, and a revision of core 6.17. It defines nothing normatively; where it says "must", it states what those texts are to establish. Accepted-current authority is unchanged: D1 1.16, core 6.17 and anonymous-review annex 6.7. Section references (§n) are to core 6.17 unless another text is named.

## 1. The problem

Without expiry (D-25), memory grows to whatever storage permits: gigabytes within a project's life, terabytes over years or through bulk imports. At the pilot capture cap (1 event/s, §14.2) with events of about 4 KB, one tenant could add about 125 GB a year; that is a ceiling, not a forecast. At that size:

- **a full scan is too expensive** for routine questions;
- **summaries and approximate methods are fast but lossy**: a hub compresses by meaning, so a detail it dropped is a missed hit, and a model filling the gap produces what looks like hallucination;
- **speed and precision need a hybrid**, in which loss is confined to places that are declared and cannot be mistaken for fact.

The ratified texts fix what retrieval means (eligibility before ranking §10.1, intent routes §10.2, the coverage contract and the absence rule §10.3, the hub hierarchy §10.5, archive §12.2) and leave the method to D4: no algorithm, index structure, partitioning, error model or cost model exists, and the pilot envelope stops at 10 GiB (§14.2). The decision record §3 raises this as a SERIOUS CHALLENGE to D3 adequacy and opens D2.

## 2. Two planes

| Plane | Holds | Promise |
| --- | --- | --- |
| **Fidelity** (system of record) | Canonical records and immutable, encrypted, content-addressed payloads; append-only | Complete. A write costs the same at 1 GB as at 1 TB (append a payload, a metadata row and an outbox entry). Completeness never depends on an index |
| **Serving** (derived) | Indexes, hubs, caches, compressed vectors, renderings | Rebuildable from the fidelity plane. May be lossy or approximate, never silently: each structure declares its watermark, and coverage names what was searched |

The ratified core already treats indexes, hubs and caches as derived artifacts (§14.3); D-102 makes the separation an invariant.

## 3. The deterministic tiered index (D-102, D-105)

### 3.1 Tiers, by exactness

| Tier | Contents | Built by | Guarantee |
| --- | --- | --- | --- |
| **E0 Identity and references** | IDs, revisions, content hashes, timestamps, scope, author, session, source, file paths; citations and relation edges | Capture metadata and explicit acts | Exact. Modification, deletion propagation, lineage and impact run here, never through search |
| **E1 Lexical** | Positional inverted index over the original text: exact phrases, versioned normalization, n-grams for unspaced scripts | A deterministic, versioned tokenizer | Complete for literal predicates; needs no interpretation, so it bypasses both translation points of §5 |
| **E2 Structural** | Tags, coordination keys, entity bindings to the vocabulary, typed relations, structured statements, code symbols, URLs, dates, numbers with units | Rule-based extractors on everything; the writing agent's declared terms; versioned model extractors (D-103) | Exact lookup; completeness stated per extractor version ("processed 87% with extractor v3") |
| **A Approximate** | Embeddings, hubs, narratives | Models | Orientation and added candidates only |

The index unit is the **span**, which rolls up to its record, so citation and verification are exact.

### 3.2 Approximation may only over-include

- **Pruning** uses only structures with false positives and no false negatives: per-segment term dictionaries or Bloom filters, tag sets, time ranges, partition keys. A region is skipped only when a match is provably absent from it; a false positive costs time, never correctness.
- **Embeddings, nearest-neighbour search, hubs and narratives** have errors in both directions. They may add candidates and orient a reader; they never prune a region or establish absence.
- **Every candidate is verified** against the canonical text or structure before it is returned.

### 3.3 The partition tree

Tenant → scope → time segment → index segment. Each node carries exact summaries (term dictionary or filter, tag set, time range), so a query descends only into branches that can match. Partition selection also enforces eligibility before ranking (§10.1). Index segments are immutable and merged in the background; deletion uses tombstones and barrier epochs, then key destruction (D-113).

### 3.4 Scale arithmetic

For 1 TB of text in chunks of about 2 KB (about 500 million chunks): float32 vectors of 1,024 dimensions take about 2 TB, more than the text; int8 about 512 GB; 64-byte product-quantized codes about 32 GB. Graph links of an in-memory HNSW index alone exceed 100 GB. The approximate tier is therefore disk-resident with compressed codes in memory and full-precision reranking from SSD, and an embedding-model change is a versioned, parallel rebuild measured in GPU-days. These numbers are planning estimates for D2 to replace with measured ones.

## 4. Queries (D-104)

1. **The request is compiled into explicit predicates** (§5.3): terms with their aliases, entity IDs, tags, scope and time window. Hubs and embeddings help find the terms.
2. **The deterministic engine runs them exactly** over the pruned partitions; approximate routes add candidates, which are verified.
3. **The response returns the plan with the results**: the predicates, partitions, tiers, index and extractor versions, and what was not covered. This fills the ratified `indexed_extent`, `structured_extent` and truncation fields of §10.3.
4. **Answers are grounded in cited spans.** Hub text without citations is orientation only.
5. **Consequential questions may scan exhaustively** over a pruned region (one scope, one quarter): exact, budgeted, explicit.
6. **Commands that change or delete records** compile to an exact target set, are shown as a preview and act only after confirmation. If a referent is ambiguous, the system asks; it never picks. The deletion preview of §12.3 becomes the rule for every mutating command.

## 5. The translation layer (D-106 to D-109)

Fidelity is at risk at two points, both translations from natural language into structure driven by a model's reading: **ingestion** (text to structured decomposition) and **query compilation** (request to predicates). They share one schema, one vocabulary and one resolver, so a query meets the records in the representation they were decomposed into.

### 5.1 Annotate, never replace

The original text is never replaced. Every structure, resolution or rendering is an attributed, versioned layer over exact spans, with its basis, and can be corrected and re-derived. This generalizes D1 Definition 2.3 (an extraction is an interpretation attributed to its extractor, unconfirmed until the speaker confirms it), D1 F-2 (an unconfirmed interpretation never supports a decision) and the core's time rule (§5.6: a relative expression keeps its raw wording, its resolution and the basis). "Text wins" when text and structure disagree (checking annex §5.7).

### 5.2 Ingestion

1. **Context frame.** Speaker, addressee, session, task, time zone, scope, preceding turns, open files and project are captured exactly as metadata (E0). They resolve "I" and "you" without a model.
2. **Resolution at the source.** An agent's write declares its referents (entity IDs for the people, files, issues and decisions it mentions) and index terms (D-107). This is the author's declaration and outranks a later reader's interpretation; it is also the cheapest, since the context is already in the agent's window.
3. **A small typed schema over a curated vocabulary.** Unknown terms become proposals, never invented concepts (checking annex §5.8).
4. **Slots for the operators models drop:** negation, modality (D1 F-1), conditions, quantifiers, tense and time, nested attribution, hedges. Verification concentrates on them.
5. **Field anchoring.** Each field points to the substring it came from; a field without one is marked inferred and states its basis.
6. **Ambiguity kept:** `ambiguous{candidates}` rather than a guess.
7. **Independent verification, by priority:** a round trip (structure rendered back and checked against the span by a different model, for nothing invented and nothing important omitted); two extractors, with disagreement recorded as ambiguity rather than settled by vote; deterministic checks of dates, units and entity IDs.
8. **Versions and measurement.** Each extractor has a recorded identity; corrections become evaluation data; a gold set of annotated real sessions measures precision and recall per field type and coreference accuracy per version (D2).

### 5.3 Standalone renderings

A span's **standalone rendering** is a minimal edit in which every insertion is marked as added and linked, like an editor's brackets:

```text
original:   "He fixed it yesterday."
standalone: "[Bob Lee →principal] fixed [login timeout bug #412 →record] on [2026-11-04 ←capture time]."
```

Both versions are indexed; a hit found only through an insertion is labeled "matched via interpretation". Citations return the original words, with the rendering beside them as an interpretation. Most spans need no insertion, so the rendering is stored as an edit over the original. Agent writes get one at write time from the authoring agent; human text gets one in later passes by priority (D-109).

### 5.4 Resolving with the memory

Resolution proceeds in rings: the context frame (deterministic), the local discussion, the task and scope entities, then wider memory. Each resolution is an interpretation with its candidates and basis. Three rules:

- **No hindsight:** a resolution records when it was made and which records it used, as "as held then" reads do (§9.9).
- **No leaks:** resolution uses only records the source's own scope can see.
- **No self-reinforcement:** a resolution never cites another unconfirmed resolution as its basis, mirroring F-2.

Linking a mention to a person is an identification act: an interpretation the speaker can confirm, limited to identities visible in the source's scope (D-108).

### 5.5 Query compilation

1. **A small typed query language**, produced under a grammar and checked against the schema and vocabulary; an invalid query is rejected or visibly repaired.
2. **The same resolver**, using the asker's context frame and session; the plan shows each resolution ("he = Bob Lee, from your previous turn").
3. **Over-generate, then verify:** aliases, related concepts, both renderings and several phrasings, unioned. The deterministic engine is cheap, and over-including is the safe direction.
4. **Reads and writes differ:** reads may be approximate if coverage says so; mutating commands need exact, confirmed targets (§4 item 6).
5. **Misses are diagnosable:** for a reported miss, the system shows which predicate would have found it and why it did not. The fix goes into the vocabulary or an extraction, which is deterministic and visible.

### 5.6 What is irreducible

If the source is itself ambiguous, or the writer was vague, no method recovers what was not said; the system preserves the ambiguity and says so. Full verification of every span at TB scale is unaffordable, so verification runs by priority (§6.3).

## 6. Economy (D-110 to D-115)

**Spend in proportion to value; report what was lost in proportion to its consequence.** Lossless everywhere is unaffordable; silent loss is unacceptable; between them is budgeted, declared loss.

### 6.1 Completeness status

Every answer carries a machine-readable status with its reason, and the answering agent carries any reason material to the question into its reply.

| Status | Meaning | Example |
| --- | --- | --- |
| Complete | Exact predicate fully evaluated over the authorized corpus | "Found 3; this is all of them in scope S" |
| Budget-limited | Stopped at the cost cap; the remainder is quantified | "Searched 2 of 9 partitions; an exhaustive search would cost about N. Continue?" |
| Ambiguous source | The text supports several readings | "The note supports either A or B" |
| Insufficient record | Fully searched; memory does not settle it | "Memory does not say who approved this" |
| Unprocessed | Records exist but are not yet structured or resolved | "40 matching sessions are not yet indexed for entities" |
| Approximate only | Found by similarity, not verified | "Possible match, not verified against the text" |

The query planner **estimates cost before running**, from index statistics (posting-list sizes, partition counts), so "too costly" comes before the spending. **Evaluation is asymmetric** (D-111): a confident wrong answer costs more than an honest abstention, so optimization cannot drift toward hallucination.

### 6.2 Storage

- Exact duplicates: content-addressed, stored once.
- Near-duplicates (repeated tool output, file versions): content-defined chunking; only changed chunks are stored; reconstruction stays exact.
- The same fact stated many times: records are never merged (attribution, and copies are not independent support, §5.3); a same-content relation links them, and the shared rendering is indexed once.
- Indexes: compressed posting lists; quantized vectors in memory and full ones on disk; embeddings only for spans worth embedding; renderings stored as edits.
- Tiers: RAM, SSD and object storage by liveness and use (D-112). Derived artifacts can be evicted under pressure with a label; "delete suggested" stays limited to rebuildable artifacts and bulky duplicates (§12.1).

### 6.3 Compute and tokens

- **Ingestion cascade:** metadata, the lexical index and rule-based extractors on everything; cheap local models by priority; LLM extraction, rendering and verification by value. A skipped step never drops text; the record is reported unprocessed (checking annex §9.8).
- **Lazy deepening:** most records are never read again, so deep processing runs at first retrieval or reliance, and its result is kept.
- **Verification by consequence:** double extraction and round trips for records a decision relies on or that are retrieved often.
- **Budgets by consequence class:** orientation, recall, explanation, decision basis, mutating command, each with a cap and a verification level; stop once the answer suffices for the request's stakes.
- **References, not documents;** nothing the session already received is resent (release records track it); query plans, resolutions and expansions are cached under the eligibility rule of §10.1.
- **Escalation** (D-115): within the task budget an agent escalates on its own; beyond it, it asks a human with a cost estimate.
- **Value model:** budgets by class, the ratified importance ordering (§12.1 rule 4: it ranks, never decides) and measured cost-versus-quality curves. A value-of-information optimizer needs calibrated probabilities that D1 does not permit storing; it is a later D2 option, adopted only if measurement shows it pays.

### 6.4 Loss ledger

Every lossy step records what it dropped: truncation, skipped partitions, unprocessed spans, quantization on the approximate route, summarization in hubs, an exhausted budget. The response carries the entries. A test checks, for example, that a budget-truncated search never returns "not found".

## 7. Latency (D-114)

p95 at most 1 to 2 s on hot tiers, set exactly with the D2 cost model; cold-tier queries may be slower and are labeled with the tiers searched. The ratified pilot targets (§14.2: 500 ms warm, 2 s cold, excluding remote inference) stay in force at the pilot size.

## 8. Procedural discovery (D-116)

**When the target is unknown, start broad and cheap and narrow; when it is known (an ID, a key, an exact phrase), go straight to exact lookup.** The rule of thumb is to start at the cheapest step that can answer. The author's completions, proposed:

1. **The broad step returns a map, not an answer:** exact facet counts over the pruned partitions (by scope, time segment, entity, tag, record type, open obligations), computed cheaply from posting-list lengths and bitmaps; hub orientation; a sample of approximate candidates. Counts are exact, so the map is not lossy the way a summary is; hub and approximate parts are labeled.
2. **Each narrowing step refines the previous predicate,** reusing cached results through continuation tokens (§10.1).
3. **Unexplored is not excluded.** Branches not pursued are reported in the final coverage with their sizes from the map, so a narrowed search never reads as exhaustive. This follows the ratified frontier rule: "nothing beyond it is reported as sound or absent" (§13).
4. **The investigator's weights are working estimates,** held by the investigator; they are never stored as confidence on a record (D1 §9). If recorded, they are an attributed claim with reasons.
5. **The trail is kept:** each step's plan and coverage (release records already record what was returned), so a later investigator resumes rather than repeating the broad pass, and a miss can be diagnosed.
6. **Stop rule:** the target is found and verified, the asker is satisfied, or the budget is reached; the answer then carries its completeness status (§6.1), with escalation under D-115.

The rule applies to people and agents alike; a person's interface presents the same map.

## 9. Routing

| Text | Establishes |
| --- | --- |
| **D1 addendum** (a successor to D1 1.16) | Retrieval predicate; completeness relative to a predicate; coverage; grounded answer; completeness statuses; context frame; standalone rendering with marked insertions; resolution as an interpretation with candidates, basis and resolution position; the principle that a loss is never presented as fact; how strongly uncertainty must be stated per consequence class |
| **D2 candidate** (new) | The one-sided-error rule and pruning structures with false-positive and cost models; verification; extraction, resolution and compilation error models with the gold set; recall of the approximate tier at 10×, 100× and 1000× the pilot corpus; cost estimation before execution; the processing cascade and default budgets by class; deduplication; asymmetric evaluation; quantization and rebuild cost; the latency target |
| **Core revision** (a successor to core 6.17) | The two planes; tiers E0 to E2 and A; the partition tree and segment lifecycle; the shared resolver and compiler; the typed query language; context frames and declared referents on the agent write interface; resolution limited to the source's scope; exact targets with preview for mutating commands; extractor versioning; index rebuild and migration; physical tiering; key destruction for deletion; budgets in the profile; deterministic extraction and completeness statuses moved into Slice 1a-core |

The three are reviewed together outside the Claude family and ratified by the owner before the Slice 1a-core D4 specification. The checking annex's structured statements stay where they are until the core revision says which parts move.

## 10. What a reviewer should test

- whether the one-sided-error rule can be kept at TB scale within D-114, including deletion, segment merging and index rebuilds;
- whether E0 to E2 answer the questions agents and people actually ask, or whether most real questions fall to the approximate tier;
- whether the completeness statuses are distinguishable in practice, and whether agents carry them into replies;
- whether write-time declaration by agents is reliable enough to lean on, and how its errors are found;
- whether resolution limited to a scope leaves too many mentions unresolved;
- whether lazy deepening leaves consequential records shallow when they are first needed;
- whether procedural discovery's map is cheap enough at TB scale to be the default first step.
