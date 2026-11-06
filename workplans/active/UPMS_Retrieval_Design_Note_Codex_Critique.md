# UPMS Retrieval Design Note: Codex Critique

**Model family:** OpenAI GPT-6.  
**Model name:** GPT-6, operating as Codex; the exact serving variant is not exposed in this session.  
**Date:** 5 November 2026.  
**Reviewer:** Codex, an AI reviewer. I am the same reviewer and family as the 6.4 to 6.8 and 6.12 to 6.17 reviews and the 6.11 cross-check. This critique is not blind. Prior exposure creates anchoring and common-mode limits; earlier favorable reviews do not establish the soundness of this direction.  
**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`.  
**Repository binding:** branch `upms-candidate-6-d1-formulation`, HEAD `a9a190f2a05c765459e92035d3292b1c96004708`.

The request was read first. Its own hash and all six hashes bound in its §1 were checked with `sha256sum` before substantive review; all matched. The additional ratification-record hash also matched the decision record’s binding. No file was edited, created, renamed or deleted. No Git command that writes was run.

## Input identities and coverage

Repository paths below are relative to the repository root.

| File read | SHA-256 |
| --- | --- |
| `AGENTS.md` | `c729fc2a7b38458e6b6c8db09a4a84046d5406129f8a96a89b92da07740ad2c5` |
| `workplans/active/UPMS_Critique_Request_Retrieval_Design_Note.md` | `3d3c643b9210a57a350ac47a9bd2198c874a08cffb95846a6429e5ba56e3d24a` |
| `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_2026-11-05.md` | `49412e997735253135885fa78bcbbfdf81fb806b89f3a7a06c29073362188abb` |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` | `f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7` |
| `workplans/active/UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310` |

The brief, note, decisions, D1 formulation and ratification record were read in full. The core was inspected through its operative sections, invariant table, delivery gates and open items. **Not read:** the core’s §15.1 scenario table beyond its opening and §15.2 evaluation protocol; anonymous-review annex 6.7; mathematics texts; change histories; previous review records; earlier decision records and original discussion transcripts; SCIRE sources; implementation code or runtime configuration. References inside the supplied texts were not recursively certified.

The checking and Slice 4 annexes were inspected as unratified context. They supply no accepted authority independently of the ratified core.

Additional local procedural files were consulted. In the table, `skills/` means `/home/samjin/.codex/skills/`; `memories/` means `/home/samjin/.codex/memories/`. Procedural references were used for routing and relevant concerns, not subjected to a separate audit.

| Additional file read | SHA-256 |
| --- | --- |
| `skills/scientific-formulation/SKILL.md` | `111a13625cf40a70aa95cf0c3968ca8efa533bfab55ec94a772d5790b2a81b5c` |
| `skills/numerical-algorithm-design/SKILL.md` | `4de404bb9c1e24e82e0d26806b35a01b43b933e63294a54492769d6b6ec2826d` |
| `skills/software-design/SKILL.md` | `d5f0d045ee6af2db72dfd1cd5da86362b48512cc6e6bc4d293ad363747ee2364` |
| `skills/scientific-formulation/references/scientific-formulation.md` | `246cef460328c85c6d9ca4c0d2d45586486b70ecbf76308c7b7318f7df706f99` |
| `skills/numerical-algorithm-design/references/numerical-algorithm-design.md` | `f41f73eb5d3acb09ce7138e3f18ca5cb9c26e90a651f13548b8eee3fa7ecf267` |
| `skills/software-design/references/architecture-and-design.md` | `06a7f931935ae84f11d3fd9ec52124333489d5c162fe1de6996535cee839cfd6` |
| `skills/software-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` |
| `skills/software-design/references/storage-and-io.md` | `4934daccfd87ee5ae4564644c321267ad71f560a993d0baea7da2b587d1db052` |
| `skills/software-design/references/performance-and-parallelism.md` | `c201db92e971a93211cc40165d16e56ae8a7942b0ee553de64678719fa4470e0` |
| `skills/software-design/references/security-and-trust-boundaries.md` | `ffc0093283ef93451eef87a628514089af872cd6656481ccbdffe6647880be54` |
| `skills/software-design/references/project-engineering-memory.md` | `2a410fe9e21dd0ed984b2d7371791e8d9bbd53ccc7f22577001f856dd031b3fa` |
| `memories/MEMORY.md` — selected registry passages | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` |

The memory registry supplied review-hygiene context only. No historical verdict from memory is used as current evidence. No rollout files were opened.

External primary documentation was consulted for the specific engineering comparisons cited below. Those web pages were not captured as local, hash-bound artifacts.

**Evidence limit:** this is documentary falsification with constructed counterexamples and elementary arithmetic. No UPMS implementation, extraction study, search benchmark, KMS operation, purge or restore was executed. No realized project scientific results were reviewed. No model or pipeline variants were experimentally selected. Findings below are this reviewer’s proposed findings, not owner dispositions.

## Serious Challenges

### SC-R01 — D1: exact predicate evaluation does not establish faithful retrieval or a sufficient answer

**Challenged direction:** note §§3.1–3.2, §4 and §6.1; decisions D-102, D-104 and D-106.

Note §6.1 defines Complete as:

> Exact predicate fully evaluated over the authorized corpus

That is a defensible **execution** property. It does not establish that the predicate captures the question, that extracted fields preserve the text, or that the resulting answer is supported.

The distinction becomes material because §3.1 describes E2 as:

> Exact lookup; completeness stated per extractor version ("processed 87% with extractor v3")

Processing coverage is not extraction recall. An extractor can process every record and omit every negation.

**Counterexample trajectory:** a source says, “Sam did not approve deployment; he approved another test.” Extraction records `approved(Sam, deployment)`. The index lookup is exact, the extractor watermark is complete, and the cited span exists. None of those facts makes “Sam approved deployment” faithful. A second case is an omitted entity binding: every record was processed, but an approval expressed without the expected name or terminology remains undiscovered. Exhausting the resulting predicate cannot establish that memory contains no approval.

There is also an unresolved meaning of candidate verification. Suppose a lexical predicate requires “login” and “timeout”; ANN finds “sessions stall during sign-in.” If verification requires that same lexical predicate, the added candidate is rejected. If verification instead asks whether the passage answers the question, that is a fallible semantic assessment. Note §3.2’s:

> Every candidate is verified against the canonical text or structure before it is returned.

does not distinguish these operations.

**Why it matters:** the design could satisfy every index invariant while confidently answering the wrong question. This would defeat D-110’s purpose and the accepted absence rule in core §10.2:

> Absence is assertable only for a deterministic predicate over a fully enumerated authorized corpus.

**Bounded repair:** distinguish source integrity, current eligibility, exact predicate satisfaction, extraction fidelity, and answer support. Report execution completeness separately from semantic adequacy. Define mandatory filters separately from optional discovery predicates so approximate candidates can add useful passages without pretending to satisfy an unrelated lexical condition. Preserve unconfirmed-interpretation labels and the existing confirmation/adoption boundary.

This challenges the proposed retrieval/answer semantics. It does not establish that accepted D1 1.16 is false.

### SC-R02 — D2: the proposed broad map has no general cheap-exact guarantee

**Challenged direction:** note §8 item 1, an expressly proposed completion of D-116.

The note proposes:

> exact facet counts over the pruned partitions

and says they are:

> computed cheaply from posting-list lengths and bitmaps

It then concludes:

> Counts are exact, so the map is not lossy the way a summary is

These claims need substantial qualification.

For a query result set \(Q\), facet bucket \(F_v\), live-record set \(L\), and eligible set \(A\), an exact count generally requires the cardinality of \(Q \cap F_v \cap L \cap A\), with additional archive, revision and lineage conditions where applicable. A posting-list length alone supplies none of those intersections. Multi-valued facets also overlap; their counts do not partition the unexplored corpus.

**Counterexample trajectory:** a common term occurs in every time segment. The user requests counts by entity across many scopes, subject to record tags and a lineage exclusion. The tree cannot prune those segments using term absence. Entity counts require query-conditioned intersections, and many mentions have no entity extraction. The result can be expensive while remaining incomplete as a map of the source’s actual entities.

At 500 million span positions, one dense bitmap already occupies 62.5 MB before auxiliary structures. This is not an impossibility result for exact facets; it is a counterexample to treating their cost as uniformly small. Established search engines themselves distinguish exact from approximate aggregation behavior; Elasticsearch documents that distributed `terms` counts may remain approximate even after increasing `shard_size`. [Elastic terms aggregation documentation](https://www.elastic.co/docs/reference/aggregations/search-aggregations-bucket-terms-aggregation)

**Why it matters:** a mandatory broad pass can cost more than the targeted search it precedes. Exact counts of extracted annotations can also give a misleading impression of semantic coverage.

**Bounded repair:** make cheap metadata summaries the initial option, with explicitly defined counting units and snapshot identities. Make query-conditioned facets optional and budgeted; permit partial enumeration, bounds, or estimates with distinct labels. Preserve an “unstructured/unknown” population. Never infer that exact bucket cardinalities establish a complete semantic overview. The owner should decide this correction to the author’s completion before drafting it into authority.

### SC-R03 — D3: deduplication, independently deletable records and segment-key destruction lack a compatible ownership design

**Challenged direction:** note §3.3 and §6.2; decision D-113.

D-113 proposes key destruction of:

> per-object or per-segment data keys, with lazy rewrite

Note §6.2 simultaneously says:

> Exact duplicates: content-addressed, stored once.

**Counterexample trajectory:** independently retained records A and B occupy one encrypted segment. Deleting A cannot destroy the segment key immediately without losing B. Keeping the key while merely tombstoning A leaves A’s ciphertext decryptable. The surviving content must first be rewritten under an appropriate surviving key, unless encryption already provides finer erasure granularity.

Content deduplication introduces another boundary: A and B may reference one encrypted chunk. Removing A’s key wrapper does not make that chunk unrecoverable while B retains a usable route to its key. That can be legitimate when B is an independently retained source, but it cannot be described as unqualified destruction of the shared content. Core §12.3 deliberately permits surviving authored descendants and sharing copies; storage reuse must preserve that distinction.

**Why it matters:** a serving barrier, removal of a logical reference, cryptographic erasure and physical reclamation are different events. NIST’s definition of cryptographic erase depends on making recovery of the target plaintext infeasible through key sanitization. A remaining usable key path defeats that claim. [NIST cryptographic erase definition](https://csrc.nist.gov/glossary/term/cryptographic_erase)

**Bounded repair:** define the independently deletable unit, deduplication domain, chunk-reference ownership and complete key hierarchy before selecting either alternative. Specify all recoverable key copies, wrappers, backups and caches. For segment encryption, make survivor rewrite precede destruction and give it a bounded admission/capacity policy. For shared content, disclose surviving authorized references and distinguish reference deletion from content erasure. Preserve the existing deletion states until the stronger cryptographic claim is qualified.

D-113 correctly reopens core §12.4, which currently says:

> Per-unit cryptographic erasure is not claimed

The challenge is to the adequacy of the proposed replacement, not an allegation that the existing core secretly promised crypto-shredding.

## D1 findings

### R-01 — Completeness statuses must compose, and the loss ledger cannot enumerate unknown semantic loss

**What is wrong:** note §6.1 mixes execution state, source ambiguity, processing coverage and answer sufficiency in one status list. They are independently variable.

A response can be budget-limited, contain ambiguous sources, and include unprocessed records simultaneously. A fully evaluated structural predicate can still have unavailable source bytes. An exact search can return only a ranked page of its matches.

“Insufficient record” needs particular restraint: fully searching a compiled predicate does not prove that all relevant natural-language evidence has been examined. “Approximate only” also conflicts with §3.2 if every returned candidate must already be verified; the design needs a separate explicitly unverified candidate presentation.

Note §6.4 says:

> Every lossy step records what it dropped

Known omitted partitions and truncated result IDs can be recorded. Unknown facts omitted by an extractor or summary cannot generally be enumerated without an independent semantic oracle.

**Why it matters:** a single reassuring status can conceal another material limitation. A complete-looking loss ledger can make unknown loss appear measured.

**Bounded repair:** use composable dimensions for execution coverage, processing coverage, availability, interpretation state and answer support. Record counting units, total matches versus returned matches, continuation state, and reasons. For semantic loss, record the method, inputs, processing extent and measured error limits; do not claim to list every omitted meaning. Carry material limitations into prose, as D-110 requires.

### R-02 — The translation layer reduces some errors but cannot make context interpretation deterministic

**What is wrong:** note §5.2 says context-frame fields:

> resolve "I" and "you" without a model

Authenticated speaker metadata resolves the outer utterance’s speaker. It does not resolve quoted speech, reported dialogue, role-play, multiple addressees, or references inside pasted content.

Write-time declarations are useful first-party evidence, but an authoring agent can attach the wrong issue ID or supply a rendering inconsistent with its text. It cannot confirm a human speaker’s intended meaning merely by writing a declaration.

Standalone renderings are useful when bracketed insertions remain interpretations. They become misleading if “standalone” implies that omitted conditions, earlier turns or nested attribution are unnecessary for understanding the span. Citations alone do not establish support.

**Bounded repair:** preserve known context fields and explicitly unknown ones. Define the linguistic scope of each binding and the context needed to interpret a cited span. Treat declarations as authenticated assertions, with validation of identity and revision, rather than automatic fidelity certification. Keep text and rendering available together and distinguish original-text matches from insertion-only matches.

The note also paraphrases F-2 too strongly in §5.1:

> an unconfirmed interpretation never supports a decision

Accepted D1 F-2 actually says:

> An interpretation `I(s)` never supports a decision basis unless it is confirmed by the speaker or adopted (Definition 2.3).

Adoption is a separate permitted route and leaves the original interpretation unconfirmed. Preserve that distinction in the addendum.

### R-03 — The three resolution rules need historical and dependency semantics

**What is wrong:** recording when a resolution was made and which records it used, as note §5.4 proposes, supports auditing. It does not itself prevent hindsight.

**Counterexample:** a pronoun in a Monday message is resolved on Friday using Wednesday’s records. The Friday interpretation may be useful now, but it was not held on Monday. Accepted D1 F-31 and core §9.9 already distinguish these reads.

The no-self-reinforcement rule excludes unconfirmed resolutions as bases, but confirmation is not evidence of independence or correctness. Two confirmed readings can still depend on the same mistaken identification.

**Bounded repair:** distinguish reconstruction at the original position from current interpretation of an older source. Bind basis revisions and the applicable snapshot; never backdate a later interpretation into an earlier view. Track actual resolution dependencies so corrections invalidate descendants. Describe confirmation as attribution of intended meaning, not independent verification.

### R-04 — Opening D2 is justified; the rationale and domain allocation need correction

**What is right:** D-101 introduces a materially larger design envelope. D-110, D-111 and D-114 make retrieval error and resource behavior consequential. Routing their governed algorithmic and error semantics to D2 is sound.

**What needs correction:** the decision record’s §3 statement that none of the existing triggers fires is too categorical. Core §1.4 includes:

> no consumer relying on a guaranteed approximation bound

A no-false-negative pruning guarantee is precisely the kind of relied-on error property whose relationship to that trigger must be explained. Calling a Bloom filter deterministic during execution does not remove its approximate membership semantics.

Similarly, note §6.3’s claim that a value-of-information optimizer requires probabilities D1 forbids storing is too broad. D1 restricts truth confidence and numeric interpretation weights. Operational estimates of runtime, retrieval yield or expected cost require their own meanings; they are not automatically probabilities of a claim’s truth.

**Bounded repair:** explicitly revise the D1/D2 handoff and core §1.4. Give D2 the governed retrieval/error/cost semantics. Keep encryption layout, ordinary deduplication ownership and service topology in D3/D4 unless a particular algorithmic guarantee requires otherwise. Deferring a value optimizer is sensible without making an unnecessarily broad prohibition.

## D2 findings

### R-05 — One-sided pruning is realizable, but only under a defined predicate and publication protocol

**What is wrong:** note §3.2 states a valid principle but omits conditions needed to preserve it.

A conservative region summary must cover every matching visible record under the query’s analyzer, field semantics, revision view and index version. A stale summary can be safe after deletion because it over-includes; it can be unsafe after insertion, alias expansion or a changed extractor.

The rule must also account for Boolean polarity. Absence of term `foo` justifies pruning a region for `contains(foo)`. It does not justify pruning it for `NOT contains(foo)`.

**Bounded repair:**

- For ordinary Bloom filters, do not clear shared bits on deletion. Retain conservative summaries until rebuilding them from the surviving population.
- Build merged summaries over the complete merged input. Bitwise union is safe only for compatible filter configurations; otherwise rebuild.
- Publish segment contents, summaries, analyzer identities and covered watermarks together. Cover concurrent additions through an explicit delta or report incomplete coverage.
- Treat missing, corrupt, incompatible or insufficiently current summaries as “cannot prune.”
- Specify safe summary reasoning for conjunction, disjunction, negation and unknown structural values.
- Preserve phrase matches across indexing boundaries, with original-text offset mappings and explicit normalization semantics.

This requires a correctness argument and adversarial qualification. It does not require a bespoke index engine.

### R-06 — The partition tree supplies locality, not a general sublinear search guarantee

**What is wrong:** note §3.3 assumes that summaries let a query descend only into matching branches. Common terms and broad predicates can match every branch. Large ancestor filters can saturate or become expensive to maintain.

Time segmentation is especially useful for bounded historical questions. It is less selective for “find the earlier decision about this,” where the time is unknown. A scope partition can also be extremely large.

**Why it matters:** “provably absent” pruning is safe but may prune very little. No false negatives does not imply useful selectivity or low latency.

**Bounded repair:** define a workload family and cost envelope rather than a corpus-size-only promise. Include common and rare terms, broad negatives, phrases, many-scope queries and poorly structured imports. Permit direct term-to-segment routing or established inverted-index facilities rather than requiring a duplicate term-summary tree at every level. Keep budget-limited exact search available when selectivity is poor.

### R-07 — Scale arithmetic is mostly correct; the architectural conclusion is stronger than the arithmetic

For the note’s rounded 500 million chunks, independent arithmetic gives:

| Component | Decimal storage |
| --- | ---: |
| 1,024-dimensional float32 vectors | 2,048 GB |
| 1,024-dimensional int8 vectors | 512 GB |
| 64-byte codes | 32 GB |
| HNSW links using an approximate `8M` bytes/vector, `M=16` | 64 GB |
| Same link estimate, `M=32` | 128 GB |

The first three estimates in §3.4 are sound planning approximations. The statement:

> Graph links of an in-memory HNSW index alone exceed 100 GB.

needs an explicit degree and representation assumption. Faiss documents the approximate HNSW memory formula `4d + 8M` bytes per vector; the link contribution does not exceed 100 GB for every admissible `M`. [Faiss index-selection documentation](https://github.com/facebookresearch/faiss/wiki/Guidelines-to-choose-an-index)

These estimates omit IDs, metadata, offsets, graph overhead, lexical positions, replicas, staging, compaction headroom and concurrent rebuilds. One 64-bit identifier per chunk alone adds 4 GB. The note’s 125 GB/year capture arithmetic is also reasonable—4,000 bytes/s gives about 126 GB/year—but excludes these other records and structures and assumes capacity admission permits continued capture.

Disk-resident ANN with compressed memory representations is technically credible. DiskANN demonstrates billion-point search using SSD storage and bounded RAM, but its published dataset and recall measurements do not qualify UPMS’s embeddings, filters or workloads. [DiskANN paper and reported conditions](https://www.microsoft.com/en-us/research/publication/diskann-fast-accurate-billion-point-nearest-neighbor-search-on-a-single-node/)

**Bounded repair:** retain the arithmetic, parameterize HNSW, define TB versus TiB and chunk population, and add peak rather than only steady-state footprint. Replace the unconditional “therefore” choice of ANN layout and the unsupported GPU-days estimate with a candidate design and a throughput-based rebuild estimate.

### R-08 — Evaluation must measure the whole retrieval chain and avoid rewarding universal abstention

**What is missing:** per-field precision/recall and coreference accuracy are useful but insufficient. A perfectly executed index cannot repair a compiled question that excludes the answer.

**Bounded repair:** define separate measurements for:

- exact-predicate agreement with an independently justified exhaustive reference;
- ingestion fidelity, including negation, conditions, quantities and attribution;
- question-to-plan fidelity;
- end-to-end passage recall and supported-answer error;
- abstention, unresolved questions, latency and spend;
- permission-filtered, archived, stale-index and deletion-heavy conditions.

Keep ANN recall against exact vector neighbors separate from recall of passages that actually answer a question. Use held-out sessions and queries; corrections reused for development cannot also supply an uncontaminated final score.

D-111’s asymmetric loss is sensible, but penalizing confident errors more than abstention does not by itself prevent an always-abstain system. The owner must set useful-answer and cost requirements alongside error limits.

Define engine latency separately from compilation, remote inference, source fetch, first-use deepening and release-record commit. Note §7 preserves pilot exclusions, but D-114’s larger-scale target still lacks a workload, concurrency, hardware and measurement boundary. Pre-execution cost estimates need runtime caps because estimates can be wrong.

## D3 findings

### R-09 — Append-oriented capture does not establish constant write cost

Note §2 promises:

> A write costs the same at 1 GB as at 1 TB

Appending payloads is a useful scaling strategy. The total acknowledged operation also includes identity checks, metadata indexes, authority validation, expected revisions, dependency handling, epochs and durable outbox work. Background compaction and rebuilding consume shared resources. Their costs cannot be removed from the system model by placing them after acknowledgement.

Core §9.1 requires:

> One logical owner serializes canonical commits within the tenant

Corpus size does not by itself invalidate that architecture. A single logical committer may comfortably handle the pilot. Conversely, TB bulk import, release records and processing outputs can create a write workload much larger than the raw capture rate.

**Bounded repair:** promise bounded or amortized work under a stated workload, rather than equal cost at all corpus sizes. Account for total canonical transactions and background amplification. Preserve the tenant’s ordering and consistent-snapshot semantics; do not silently turn scope partitions into independent commit domains. Establish a bulk-ingestion requirement before deciding whether batching or a different topology is necessary.

### R-10 — Scope partitioning does not implement complete eligibility

Note §3.3 says:

> Partition selection also enforces eligibility before ranking (§10.1).

It enforces part of eligibility. Core §7.3.4 also includes own-record and oversight entitlements, session grants, restriction tags, quarantine, barriers and lineage exclusions. Core §10.1 applies before snippets, rankers and processors, not merely at final return.

This affects the resolver, vocabulary expansion, cost estimates, facet maps and continuation tokens as well as ordinary hits. A service that reads every record in a source’s scope may still read records unavailable under the relevant tags, sealing or task exclusions. Conversely, selecting only scopes with a scope-wide grant can omit readable own records.

**Bounded repair:** reuse the core’s complete eligibility predicate on every path. State whose authority a resolver uses, which processors may receive its context, and how derived outputs preserve the union of input restrictions. Keep hidden records out of exposed counts and plans. Do not add a separate, weaker “scope visibility” interpretation.

### R-11 — Content sharing must preserve occurrence identity and contextual differences

Note §6.2 proposes:

> the shared rendering is indexed once

Sharing byte storage or a posting representation can be valid. Sharing one interpretation is not valid merely because source text matches.

“He fixed it yesterday” can occur in two sessions with different speakers, referents and dates. Identical factual text can also have different authorship, correction state, archive state, permissions and evidential independence. A count may mean spans, records, unique payloads or sources; those are different quantities.

Content addressing also requires a declared confidentiality domain. Core §5.6 requires protected, tenant-scoped digests and says:

> no durable plaintext hash of a sensitive value

**Bounded repair:** keep logical records and contextual interpretations distinct. Let any shared physical representation map back to separately authorized occurrences with their own dependencies and lifecycle. Specify deduplication boundaries and protected digest handling; do not treat a content hash as an access capability or a source identity.

### R-12 — Physical tiering needs an explicit relationship to archive, completeness and recovery

D-112 is compatible with the accepted architecture if placement remains separate from semantic archive state. Cold placement must not silently perform the curator-confirmed archive transition of core §12.2. A hot-only search is incomplete for a whole-corpus predicate when relevant cold data remains unsearched.

The note does not supply the recovery plan that makes disposable serving state practical at TB scale. Core §14.2 binds pilot RPO/RTO targets, while §12.4 requires recovery-log application before serving or derivation. A full TB transfer within four hours alone requires about 69 MB/s sustained, before metadata recovery, validation, log replay and index work. Rebuilding embeddings may take much longer.

**Bounded repair:** identify the minimum service available after recovery, which indexes are restored versus rebuilt, and how partial availability is reported. Preserve the requirement to prove the latest recovery-log position. State which numeric targets remain pilot-specific and what larger-scale profile will require requalification. D-101 does not require a TB recovery experiment now; it does require avoiding an architecture whose recovery path is “rebuild everything before useful service.”

### R-13 — Immutable index segments need a purge mechanism independent of ordinary merging

Tombstones and barrier epochs can immediately prevent serving deleted content. They do not erase lexical terms, stored snippets, vectors or copied metadata from immutable segments.

A background merge policy optimized for search can leave a deleted term in an old segment indefinitely. Segment-key destruction has the survivor problem in SC-R03. Plaintext index files and temporary merge outputs also remain deletion surfaces.

**Bounded repair:** define targeted purge/rewrite scheduling, maximum segment sizes, temporary-copy cleanup, reserved I/O and failure reporting. Measure purge debt and ensure ordinary ingestion cannot starve it. Preserve the core’s distinction among `serving_blocked`, `purged_live` and `complete`; the 24-hour target must not be treated as automatically satisfied by tombstoning.

### R-14 — Lazy deepening needs discovery coverage, starvation protection and stable retained outputs

Note §6.3 says:

> most records are never read again

That is an empirical workload assumption, not established evidence here. More importantly, first-retrieval deepening cannot repair records that the shallow retrieval route never finds.

The accepted core already provides a stronger liveness condition in §9.5: explicit requests, obligations, retrieval need, consequential reliance and a bounded age-weighted background sweep. The new direction should preserve it.

The two-plane table also needs to distinguish disposable serving materializations from retained interpretation outputs. Core §11.2 states:

> Novel prompt, compaction, overview or model-generated content is itself a canonical record

A model-produced rendering cannot be reconstructed exactly merely by rerunning its model.

**Bounded repair:** retain the lexical baseline and visible unprocessed populations; protect obligation-driven and background work from popularity starvation. Allow first use to return a qualified shallow result or deferred processing. Keep canonical model outputs and their manifests in fidelity custody while treating their searchable materializations as rebuildable. Author-supplied renderings can precede capture, but no model invocation should be introduced into the core’s synchronous capture path, contrary to §9.2.

### R-15 — Exact mutating targets need commit-time binding, and the D3 challenge should be scoped to the new requirement

Preview and confirmation are useful, but an exact preview can become stale. “Delete all matching records” must not silently expand to include records added after confirmation.

**Bounded repair:** bind confirmation to the exact plan and target revisions, authorization context and relevant preconditions. Revalidate at commit; materially changed effects require a fresh preview. Internal worker transitions should retain their existing typed authority rather than requiring an unnecessary conversational confirmation on every operation.

The decision record correctly routes the scaling issue upstream of D4. Its statement that core 6.17 has “no fidelity–serving invariant” overstates the omission: canonical ownership, derived indexes, rebuild and bounded fallback already appear in §§4.1, 9.5–9.6 and 14.3. What is missing is sufficient governed design for the newly directed scale and retrieval guarantees.

The Serious Challenge is therefore justified as **D3 adequacy for D-101**, not proof that the ratified pilot architecture was false under its prior envelope. Core §17.4 already recognizes scaling-related reopen conditions. Preserve the ratification and its limits while revising affected owners.

## D4 findings and evidence obligations

No implementation was reviewed, so no implementation defect is asserted. D4 should receive these bounded acceptance obligations after the semantic and architectural repairs:

| Boundary | Required discriminator |
| --- | --- |
| Index and summary publication | Concurrent insert, merge, deletion and rebuild cannot produce a false-negative prune; an uncovered delta prevents a completeness claim |
| Predicate semantics | Exact reference agreement for Boolean polarity, phrase boundaries, normalization versions and unknown structural fields |
| Translation and answer presentation | Missing negation, wrong referent, insertion-only hit and unsupported citation remain distinguishable from verified source evidence |
| Eligibility | Own-record entitlement, tags, lineage exclusion, resolver inputs, facets and cached continuations use the real access owner |
| Deletion and recovery | Shared chunks, mixed live/deleted segments, temporary files, key recovery and restore cannot resurrect served content or falsely complete purge |
| Resource limits | Underestimated cost, exhausted budget and first-use deepening produce bounded, honestly qualified outcomes |

These are proposed evidence requirements, not executed results or additions to accepted product scope.

Two reference errors should also be repaired: note §4 item 1 points query compilation to §5.3, which is Standalone renderings; compilation is §5.5. Note §1 associates the absence rule with core §10.3, while its explicit normative sentence is in §10.2.

## Simplicity and first-product scope

Retain the two-plane separation, canonical original text, stable references, lexical baseline, attributed annotations, versioned processing, eligibility enforcement, coverage and budgeted escalation. These provide useful invariants without requiring every TB-scale acceleration immediately.

The first product can use an established positional inverted index and ordinary canonical storage. A custom summary tree, high-cardinality exact discovery facets, content-defined near-duplicate chunking, disk ANN, full-precision vector reranking and parallel embedding rebuild machinery can wait for measured need. Their ownership and lifecycle boundaries should be decided now; their full implementation need not be.

Retain D-107 and D-109 as owner direction. Minimize their cost through author-supplied declarations and marked edits where needed. Deferring those obligations would require changing the decisions, rather than treating them as optional implementation choices.

Do not require TB experiments before drafting or pilot qualification. Require a credible cost model and lifecycle design now, with larger-scale qualification attached to the profile that actually claims that scale. Approximate discovery can be useful before it is highly sophisticated; its limitation is already expressible.

## Verdict

**REVISE BEFORE DRAFTING.**

The basic direction is technically credible: canonical fidelity separated from serving structures, deterministic retrieval over stated predicates, approximate candidate addition, attributed interpretation and explicit resource limits are strong foundations.

Before drafting the three authority texts, revise the note to:

1. Separate exact execution from extraction fidelity, relevance and answer support.
2. Replace the uniformly cheap, exact discovery-map claim with a budgeted and coverage-qualified design.
3. Resolve erasure units, deduplication boundaries and segment/key lifecycle compatibility.
4. State the pruning publication contract, recovery strategy and workload-dependent performance envelope.

These repairs do not require selecting every library or running a TB benchmark. They require decisions precise enough that D1, D2 and D3 can be drafted without independently inventing incompatible meanings. This verdict grants no Gate 0 passage, ratification or implementation qualification.

Questions for the owner:

1. May procedural discovery begin with cheap metadata summaries and offer budgeted partial or estimated facets, rather than require a complete exact facet map?
2. Should verified source identity and exact predicate matching be reported separately from fallible semantic verification, with unverified semantic candidates available through an explicitly labeled route?
3. Should the first product favor simple independent deletion boundaries over cross-boundary deduplication, accepting additional storage where necessary?
4. For the larger-scale profile, what representative query workload, concurrency, bulk-import rate and degraded recovery service should determine the latency and recovery targets?

