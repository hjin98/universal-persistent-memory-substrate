# UPMS Candidate 6.18 Independent Review

**Model family / model name:** OpenAI GPT family / Codex, GPT-6-based. The exact serving-model identifier is not exposed in this session. I am **the same reviewer and family as the 6.4 to 6.8 and 6.12 to 6.17 reviews, the 6.11 cross-check and the three design-note critiques**. This review is not blind. Prior exposure creates anchoring and common-mode limits. I did not author these candidates. No subagents were used.

**Date:** 5 November 2026, America/Chicago.

**Repository binding:** Branch `upms-candidate-6-d1-formulation`, HEAD `f5b58d023890692c544320b67a0f519ac253f684`.

**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`. Scientific-formulation, numerical-algorithm-design and software-design skills were applied.

**Integrity verification:** I read the request first. Before substantive review, `sha256sum` verified the request’s supplied hash and all 14 file hashes it binds: **15 checks, all matching**. Final verification repeated those checks; all matched.

**Input identities and reading coverage:** Paths below are relative to `workplans/active/`, except where stated.

| File | SHA-256 | Reading coverage |
| --- | --- | --- |
| `UPMS_Review_Request_Candidate_6_18.md` | `3f9d503f207a265a8bab23761e1295796699a3760f333c1852ef4f61ea471f38` | Read first, in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | `28bdee3084167701926da92944804cd06390f926cc3b4fe6d9019b57689d2bc8` | Complete predecessor comparison; §16 in full; targeted retained definitions, rules and §§8–15 |
| `UPMS_Retrieval_Method_D2_Candidate_1_0.md` | `fba8768d1c0ff6ac7725559054acb455fb2a0ae893e82c7c9c0275b31c736f6f` | Read in full |
| `UPMS_Architecture_Manual_Review_Candidate_6_18.md` | `9a42794b35059165ac7e3d83d5a842b4aa33c54bf06f60b003a3aa38b8fd8373` | Complete predecessor comparison and change-map reconstruction; targeted operative sections identified below |
| `UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` | `abfd09691d82cfb635986eae790c57826b581e257dce2cd26ac3e3311ad2de9e` | Read in full |
| `UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Read in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17_Change_History.md` | `43bc738dd2508fa1a7461406def62fe8c271d206014db9ad049ad1cfd1e508d4` | Read in full as claims to test |
| `UPMS_Architecture_Manual_Candidate_6_18_Change_History.md` | `bbe26907c6d0871fd37727c58dfbbc40db8d7bee9828711d60edb4b15318bae4` | Read in full; all 29 replacements applied in memory against the predecessor |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Complete comparison and targeted predecessor checks |
| `UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` | Complete comparison and reconstruction baseline; targeted retained contracts |
| `UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md` | `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Read in full |
| `UPMS_Retrieval_Design_Note_R3_Codex_Critique.md` | `66a2ae248a4ce55196561180cbdfb504b8de83ecb55909df8f4feb5835d19da4` | Read in full |
| `UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` | Read in full |
| `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` | `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Read in full |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` | Read in full as unratified context |
| `UPMS_Candidate_6_17_Independent_Review.md` | `b31cf91f8581cda5929c7dff7ff868a8924c7106e0a0e8d157e23ebbf3835029` | Read in full for form, preceding verdict and limits |
| `UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310` | Read in full; accepted-current identities checked |
| Repository-root `AGENTS.md` | `c729fc2a7b38458e6b6c8db09a4a84046d5406129f8a96a89b92da07740ad2c5` | Read in full |
| Repository-root `history/SEMANTIC_EVOLUTION.md` | `5f0e1346316bd0b71470fa20e91905af199d0fa80015459df89966b1b4b433c1` | Heading search and targeted recent authority/retrieval entries |

Procedural sources are not UPMS product authority. Here `skills/` means `/home/samjin/.codex/skills/`, and `memories/` means `/home/samjin/.codex/memories/`.

| Procedural file read | SHA-256 |
| --- | --- |
| `skills/scientific-formulation/SKILL.md` | `111a13625cf40a70aa95cf0c3968ca8efa533bfab55ec94a772d5790b2a81b5c` |
| `skills/numerical-algorithm-design/SKILL.md` | `4de404bb9c1e24e82e0d26806b35a01b43b933e63294a54492769d6b6ec2826d` |
| `skills/software-design/SKILL.md` | `d5f0d045ee6af2db72dfd1cd5da86362b48512cc6e6bc4d293ad363747ee2364` |
| `skills/scientific-formulation/references/scientific-formulation.md` | `246cef460328c85c6d9ca4c0d2d45586486b70ecbf76308c7b7318f7df706f99` |
| `skills/numerical-algorithm-design/references/numerical-algorithm-design.md` | `f41f73eb5d3acb09ce7138e3f18ca5cb9c26e90a651f13548b8eee3fa7ecf267` |
| `skills/software-design/references/architecture-and-design.md` | `06a7f931935ae84f11d3fd9ec52124333489d5c162fe1de6996535cee839cfd6` |
| `skills/software-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` |
| `memories/MEMORY.md` | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` |

**Parts not read:** The unchanged D1 and core bodies were not freshly reread throughout. Core inspection concentrated on §§1–2, §4.3, selected permission provisions, §7.4, resource boundaries, §§9.1–9.5, retrieval and response contracts, deletion and restore, profile defaults, delivery and reopen rules. Older review bodies other than 6.17, earlier change histories, original owner conversations, the proposal, mathematics and Slice 4 annexes, SCIRE and SSDS source authorities, implementation and deployment configuration were not substantively reviewed. Embedded references were not recursively verified. The repository’s GitHub issue page could not be fetched, and no connected issue tool was available; native issue coverage is therefore unavailable.

**Status:** Documentary falsification evidence asserted by Codex as an AI reviewer. No file was created, edited, renamed or deleted, and no writing Git command was run. The user-designated persistence route is saving this response verbatim.

## 1. Serious Challenges

### SC618-01 — D1: the no-self-reinforcement rule was weakened during translation

**Owning domain:** D1, with D3 consequences in R7.4. **Blocking.**

Design note R3 §5.4 says exactly:

> a resolution never cites another unconfirmed resolution as its basis.

D1 1.17 F-51 instead says:

> A resolution never rests on another resolution that is neither confirmed by its speaker nor adopted, mirroring F-2.

Annex R7.4 repeats the adopted-resolution exception. These rules differ. An adopted resolution can remain unconfirmed: retained Definition 2.3 expressly says:

> Adoption changes nothing about `I(s)`.

**Counterexample trajectory — paraphrase:**

1. A processor guesses that “he” in an ambiguous message means Bob, producing resolution A.
2. An agent adopts A; that creates the agent’s new claim. The original resolution remains unconfirmed.
3. The resolver uses A as the basis for resolution B of a later mention.
4. F-51 and R7.4 permit that dependency because A was adopted. R3 §5.4 prohibits it because A remains unconfirmed.

**Consequence:** A participant’s willingness to adopt a reading now authorizes propagation of an unconfirmed identification through the resolver. This is a substantive relaxation of the direction, not merely preservation of F-2’s separate route for decision reliance. It can amplify one mistaken identification across later interpretations.

This does not establish that every adoption-based resolution policy is unsound. It establishes that the candidate silently chooses one the reviewed direction excluded.

**Bounded repair:** Restore R3’s prohibition in F-51 and R7.4. If adoption is intended to be an exception, obtain an explicit owner decision on that change and specify how reliance on the adopter’s new claim remains distinguishable from confirmation of the source’s meaning. Do not modify Definition 2.3 to make adoption act like confirmation.

### SC618-02 — D2: the cost model omits the work of establishing that segments can be pruned

**Owning domain:** D2. **Blocking.**

D2 §1 requires:

> cost is known before the search within a stated error

But §7.1 places engine probe work inside:

```text
Σ_{s not pruned} [ c_probe + Σ_{atoms α} c_post · |postings_s(α)| ]
```

No term accounts for consulting summaries of pruned segments.

**Counterexample trajectory — paraphrase:**

1. Use the first-product design: per-segment term dictionaries, without a separate summary tree.
2. Run a lexical-only query for a term absent from every segment; the delta is empty.
3. Every segment is pruned, there are no candidates, and there is no similarity or reranking work.
4. The formula assigns zero engine work, regardless of the number of segment dictionaries consulted.

Compilation tokens do not account for those engine operations. No calibration of constants inside an empty sum can repair the omission.

The model also lacks explicit treatment of the delta scan and the work needed to construct or check the eligible population. Those costs can dominate precisely the broad-negative, heavily filtered and stale-index workloads the method promises to characterize.

**Consequence:** The planner’s central estimate can be structurally wrong before measurement begins. Recording actual/estimated ratios afterwards does not define the promised error envelope, particularly when the engine estimate is zero.

**Bounded repair:** Account separately for routing/summary examination, surviving-segment execution, delta work, eligibility work, confirmation and counting. Separate time/work estimates from token estimates rather than adding unlike quantities without a defined conversion. State whether estimation error is an empirical interval, conservative bound or diagnostic distribution, and define the fallback when suitable statistics are unavailable. Secure statistics handling must preserve R5; hidden-content statistics cannot simply be exposed as estimates.

This needs a corrected model and measurement specification, not a TB benchmark before drafting can continue.

### SC618-03 — D3: “required” declarations have become an unbounded acceptance exception

**Owning domain:** D3, under D-107 and D1 Definition 16.9. **Blocking pending a bounded contract or owner decision.**

D-107’s accepted recommendation is:

> required for agent principals, optional for humans.

R7.2 instead applies this rule across captured turns and agent-issued record-writing operations:

> a write without it is accepted with `declarations: missing` recorded and reported in processing coverage

It says integration qualification measures the missing rate, but supplies no acceptance condition distinguishing a conforming integration from one that omits declarations on every write. T150 positively requires acceptance of a missing-declaration write.

**Counterexample trajectory — paraphrase:**

1. An agent integration never supplies declarations.
2. Every write is accepted and marked missing.
3. Qualification reports a 100% missing rate.
4. Nothing in R7.2, R15 or R18 makes that integration fail the declaration requirement or distinguishes its writes from conforming authored writes.

**Consequence:** Measurement makes nonconformance visible but does not enforce the requirement. The exception also extends beyond the capture-loss rationale to deliberate record-writing operations.

Preserving captured evidence when an integration is defective is sensible. Rejecting raw capture indiscriminately would be a poor repair.

**Bounded repair:** Separate preservation of captured events from conformance of agent-authored operations. Preserve malformed capture with an explicit integration defect; define the requirement for intentional record writes and the qualification disposition for missing declarations. Alternatively, ask the owner to authorize a measured best-effort policy, with its scope and acceptance criterion. A measured rate alone cannot decide that policy.

## 2. Verdicts and retained strengths

| Subject | Gate 0 entry verdict | Basis |
| --- | --- | --- |
| D1 formulation 1.17 | **NO-PASS** | SC618-01 changes the directed resolution rule; the lexical representation boundary also needs clarification |
| D2 retrieval method 1.0 | **NO-PASS** | SC618-02; evaluation selection and abstention rules remain incomplete |
| Core 6.18 with retrieval-and-scale annex and anonymous-review annex 6.7 | **NO-PASS** | SC618-03, unresolved parent findings, and delivery/resource-contract ambiguities below |

The direction remains technically credible. Retain:

- canonical custody separated from rebuildable serving structures;
- deterministic lexical and structural routes, with approximate proposals separately labeled;
- exact facts separated from fidelity, relevance and support assessments;
- conservative pruning under versioned publication;
- hidden records excluded from exposed coverage;
- explicit consumer availability before reference-only reuse;
- deduplication confined to deletion units;
- purge scheduling independent of ordinary merging;
- pilot qualification separated from larger-profile claims.

The conditional pruning proposition survives the mathematical review below. These NO-PASS verdicts do not reject the entire retrieval approach.

D1 1.16, core 6.17 and anonymous-review annex 6.7 remain accepted-current at the ratification record’s hashes. Their pilot acceptance is not revoked. The already-recorded D-101 adequacy challenge remains open for the expanded requirement.

## 3. Additional findings by earliest owning domain

### 3.1 D1 — F618-01: lexical matching needs an explicit representation target

**Material clarification required.**

Definition 16.1 defines a lexical route as:

> a lexical predicate over original text

R7.3 says of original text and standalone renderings:

> Both versions are indexed in E1 and E2

R4 permits `via: rendering_insertion`. D2 §4.1 requires an offset map to original text, but an inserted name may have no corresponding original characters.

**Counterexample trajectory — paraphrase:** The original is “He fixed it yesterday.” Its rendering inserts “[Bob Lee]”. A lexical query for “Bob Lee” finds the insertion. Checking that predicate against the original fails; checking it against the rendering succeeds.

**Consequence:** The package does not clearly establish which representation supplies the exact lexical fact. Treating the rendering as a separate canonical record can resolve this, but that interpretation must identify the searched representation and preserve its relation to the source. A consumer must not receive an exact original-text match for words absent from the original.

**Bounded repair:** Define the route’s target representation explicitly: original text or a named rendering revision. Bind matches, offsets, versions and interpretation facts to that representation, while retaining the original source citation. This is an exact match against an interpretation’s text, not an assessment that the interpretation is faithful. Add an insertion-only lexical acceptance case.

### 3.2 D1 — F618-02: predecessor and tension metadata contradict current authority

**Documentary correction required.**

D1 §13 still says:

> **No accepted predecessor:** there are no recorded tensions against accepted D1 authority to carry, because none exists.

This is false for 1.17. Its own opening metadata and §0.1 correctly identify ratified D1 1.16.

**Counterexample trajectory — paraphrase:** A reviewer follows §13 and treats predecessor tension reconciliation as inapplicable, although this revision succeeds an accepted formulation and accompanies a recorded challenge to its accepted concretization.

**Consequence:** The revision’s dependency-impact account can incorrectly bypass an applicability assessment. This does not by itself demonstrate a defective retained theory–evidence rule.

**Bounded repair:** Name accepted predecessor 1.16 and assess relevant recorded tensions for this revision. Distinguish the accepted pilot design from the D-101 expanded-scale challenge; do not turn the latter into a retroactive pilot defect.

### 3.3 D2 — F618-03: parameter selection and final held-out evaluation are not separated

**Blocking evaluation-method ambiguity.**

D2 §5.3 measures nearest-neighbour recall:

> on held-out queries for each index type, quantization and parameter setting

It then chooses parameters from the measured recall–latency curves. Section 9.1 distinguishes development and held-out data, but does not reserve another evaluation set after the selection described in §5.3.

**Counterexample trajectory — paraphrase:** Try many index and search-parameter variants on the held-out queries, select the most favorable curve, and report that same curve as final held-out performance.

**Consequence:** The selection procedure permits tuning to the purported final evaluation set. Calling queries held out does not remove this selection effect.

**Bounded repair:** Use development queries for parameter curves and selection; freeze the selected variant before final held-out evaluation. Record variants and test-set reuse. If “held-out” in §5.3 means a validation set, name it accordingly and distinguish it from the final test set.

### 3.4 D2 — F618-04: abstention is judged against the system’s own plan, and class requirements are incomplete

**Blocking evaluation-method gap.**

Section 10.1 defines unjustified abstention as abstaining:

> when the plan within budget would have answered

Section 10.2 proposes `u_min` only for recall and explanation, although its acceptance requirements apply per consequence class and workload family. Decision-basis usefulness therefore has no proposed floor. Orientation and mutating-command acceptance also lack a complete mapping to the listed requirements.

**Counterexample trajectory — paraphrase:**

1. The request is answerable within budget.
2. The compiler produces an unnecessarily narrow plan that cannot find the answer.
3. The system abstains, correctly reporting that plan’s limitation.
4. The abstention can escape the “unjustified” category because the defective plan would not have answered.
5. A decision-basis variant can additionally avoid a stated useful-answer floor.

**Consequence:** Compiler failure can be converted into apparently justified abstention. The separate plan-fidelity metric records a problem but has no stated acceptance requirement that closes this loophole.

**Bounded repair:** Judge answerability against an independently specified request, eligible corpus and budget, not only the chosen plan. Supply proposed requirements, or explicit exclusions, for every consequence class. Distinguish honest disclosure of a bad plan from successful handling of the request. Define adjudication for mixed outcomes such as a useful partial answer with an unresolved remainder.

The owner should set values before measurement; this review does not select them.

### 3.5 D2 — F618-05: scale qualification needs a lifecycle workload and a conditional ladder

**Required design completion before larger-profile qualification; the ladder wording should be repaired now.**

D2 §10.3 says:

> Each measurement is repeated at the pilot envelope and at 10× and 100× it

R3 §10 expressly says:

> No TB experiment is required before drafting or pilot qualification

D2 §13, meanwhile, makes larger-profile defaults nonbinding until a larger profile is bound.

**Counterexample trajectory — paraphrase:** Pilot qualification attempts to apply §10.3 literally and acquires a mandatory 100× measurement obligation, despite the owner’s pilot-first direction.

**Bounded repair:** Make larger ladder steps conditional on the profile being qualified; distinguish optional scaling diagnostics from pilot acceptance obligations.

There is also a substantive workload omission. Section 13 proposes query mix, concurrency and import, but no deletion, correction or concurrent maintenance workload. Section 11’s peak estimate allows merge headroom “up to the largest segment” without binding concurrent merge, rebuild and purge activity.

**Counterexample trajectory — paraphrase:** Delete one item in each of many segments while ingestion and a rebuild continue. Every individual segment is small enough to rewrite, yet the aggregate purge workload greatly exceeds reserved I/O. Several concurrent outputs also exceed one-segment headroom.

**Consequence:** Bounded segment size does not establish an aggregate purge-time envelope or peak disk requirement.

**Bounded repair:** Propose lifecycle workloads, maintenance concurrency and aggregate headroom assumptions. Measure purge debt and service under those workloads. R11’s honest `purge_failed` behavior remains appropriate when a target is missed; it is not evidence that the target is feasible.

Lucene’s documentation independently confirms that delete-merging can be expensive and that merge policy controls which segments are selected; an established search product does not supply UPMS’s purge qualification automatically. [Apache Lucene 10.3.1 `IndexWriter`](https://lucene.apache.org/core/10_3_1/core/org/apache/lucene/index/IndexWriter.html)

### 3.6 D3 — F618-06: reconcile class budgets with retained pilot caps and count semantics

**Material contract clarification required.**

Core §14.2 retains:

> 200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget; truncation explicit

D2 §7.3 proposes 10 seconds for decision-basis searches; R9 applies class caps. Core §14.2 says the annex adds rows, rather than stating how overlapping caps compose.

**Counterexample trajectory — paraphrase:** A decision-basis search has an estimate of four seconds within the task budget. The class table admits it; the retained ordinary-query cap stops it after two seconds. Neither the plan schema nor profile additions state which transition makes the longer search authorized deep retrieval.

Both caps can mathematically apply by taking the smaller value. The defect is the missing operational rule, not a proof that the inequalities are inconsistent.

**Consequence:** Integrations can differ on whether escalation changes the cap, whether a new plan is required, and whether ordinary class selection authorizes the larger budget.

**Bounded repair:** State effective-cap precedence and the deep-retrieval transition explicitly. Preserve pilot targets under D-120 unless an authorized profile or capability changes them.

Likewise, D2 §6 requires total-match counts independently of pagination, while capped execution may stop before the total is known. R4 provides an unqualified `total_matches` field.

**Bounded repair:** Give counts a domain and status: exact total, lower bound, estimate or unknown. A candidate cap, an output page limit and incomplete search execution are different events. Exact counting can itself be costly; Elastic documents this tradeoff and distinguishes accurate counts from lower bounds. [Elastic search API documentation](https://www.elastic.co/docs/solutions/search/the-search-api)

### 3.7 D3 — F618-07: the delivery map omits author renderings and early translation prerequisites

**Blocking delivery-map gap.**

R17 assigns R7.1 and R7.2 to Slice 1a-core. It assigns:

> R7.3 renderings for human text and R7.4 resolution by processors

to Slice 2. No row explicitly assigns author-supplied renderings, although R7.3 requires them at agent write time and R3 §10 includes them in the first product.

R3 also requires the compiler to check against the schema and vocabulary and to use the resolver. The retained core §16 leaves the vocabulary registry in Slice 3. No early subset is identified.

**Counterexample trajectory — paraphrase:** Slice 1a-core implements its enumerated R17 sections, accepts declarations, and ships without author renderings or a defined vocabulary/resolution subset. Slice 2 later adds only human renderings. Each team follows its row, but the first-product direction is never fully delivered.

**Consequence:** The work cannot be handed to D4 with a reliable slice boundary.

**Bounded repair:** Assign author-supplied renderings to Slice 1a-core explicitly. Identify the minimum versioned vocabulary/schema and deterministic resolution behavior needed by early plans, including what happens when processor resolution is unavailable. Keep full structured statements and screening in Slice 3. Do not import the entire unratified checking annex into the first slice by implication.

### 3.8 D3 — F618-08: the coverage replacement does not account for capture extent

**Material schema ambiguity requiring repair.**

Core §10.3 includes `capture_extent`. R4 says existing fields keep their meanings, but then replaces coverage using `coverage := { ... }`. Its mapping comments cover indexing, traversal, processing, structuring, screening, truncation and timeout; `capture_extent` has no destination.

**Counterexample trajectory — paraphrase:** An integration has a known capture gap. Its renderer follows the new R4 coverage structure and omits the old field. Execution over the retained population is complete, and the final answer carries no indication that part of the source history was never captured.

**Consequence:** Index completeness can be mistaken for capture completeness. The opening preservation sentence and replacement schema admit different implementations.

**Bounded repair:** Preserve capture extent explicitly, either as a separate field or a clearly defined coverage dimension. Make the field migration exhaustive. Extend T160 to check a known capture gap, not merely search and support limitations.

## 4. Pruning, exactness and engineering checks

### 4.1 Proposition 3.1 survives, subject to its premises

The induction is sound for the stated conservative rule:

- a positive atom becomes false only through a covering absence result;
- a negated atom never causes pruning;
- an unprocessed structural atom remains unknown;
- a false conjunction has an impossible conjunct;
- a false disjunction has no possible disjunct.

Replacing a positive phrase with conjunction of its terms is a safe necessary condition for pruning, followed by exact positional checking. It is conservative rather than maximally selective.

Deletion preserves covering when the summarized population only shrinks. Compatible Bloom-filter union preserves covering. Version mismatch, missing summaries and uncovered deltas correctly require search or incomplete execution rather than a false absence.

This proves a conditional pruning property. It does not prove extraction recall, semantic relevance, snapshot publication correctness or complete answer generation.

### 4.2 The acceptance cases need stronger discriminators

The following are documentary test-design assessments; none of these scenarios was executed.

| Cases | Assessment and needed discriminator |
| --- | --- |
| T141–T143 | Useful separation of exact matches, interpretation error and absence. Add an insertion-only rendering match and qualified totals under a cap |
| T144–T146 | Useful lifecycle skeleton. Pin a query snapshot and independently control publication, delta visibility and merge completion. Include an interpretation added to an old span, not only a newly captured span |
| T147 | A lone negative predicate tests one conservative branch. Add nested conjunction/disjunction, mixed positive and negative atoms, and unprocessed structural values |
| Phrase behavior | Add positional checks across embedding boundaries and the actual source-to-span boundary policy. Indexing each span whole does not itself specify what happens to a phrase crossing two spans |
| Version behavior | Test incompatible postings as well as incompatible summaries. Refusing to prune with an old summary is insufficient if exact execution still uses old-analysis postings without a suitable fallback |
| T148 | Preserves the repaired hidden-count principle. Extend the paired worlds to exposed estimates, facets, continuation behavior and explanations; treat timing as the disclosed separate residual |
| T149 | Preserves the compaction repair. Also test resumed consumers, a different rendering revision and current eligibility changes |
| T150 | Currently codifies SC618-03’s acceptance exception. Revise after the declaration contract is decided |
| T151–T152 | Good temporal and basis checks. Add the adopted-but-unconfirmed trajectory from SC618-01 |
| T153 | Good changed-target-set discriminator. Retain authorization and precondition changes, even where the target identities stay the same |
| T154–T156 | Good unit-isolation and degraded-service cases. Add multi-segment purge pressure, concurrent maintenance, recoverable key copies and crash recovery during rewrite |
| T157–T160 | Good tier, escalation, discovery and grounding coverage. Resolve F618-06–08 and include the original discovery scope when reporting unexplored branches |
| T161 | “Within its window” needs a bound workload and a named processing-age/window criterion. A reserved percentage alone supplies no completion-time bound |
| T162 | Correct occurrence distinction; retain separate attribution, source positions and interpretation histories |

D2 §9.4’s independent exhaustive reference is a good obligation. Its matching semantics should be independently justified; sharing an analyzer identity is necessary for comparison, but does not independently validate a defective tokenizer or offset map.

### 4.3 LLM checks need operational independence language

D2 §8 requires two independent extractions and a round-trip check for consequential use. The package should identify what varies between those checks and retain processor/model identities and shared inputs. Repeated calls to the same model are not evidence of independent failure modes.

These checks remain attributed fidelity assessments. They neither confirm a human speaker’s meaning nor replace F-2’s confirmation/adoption requirements. No numerical probability of correctness follows merely from agreement.

### 4.4 Storage and recovery choices are credible, not yet qualified

Per-unit payload keys, deletion-unit-local deduplication and independent segment rewrite are a coherent first-product direction. The explicit refusal to claim cryptographic erasure before KMS qualification is correct.

R12’s E0-first degraded recovery can be useful when other routes are visibly unavailable. It must not be described as restored lexical recall. The larger profile needs to bind service stages and timing separately; the current pilot RPO/RTO remain governing.

The retained single committer, asynchronous indexing and no-model synchronous capture path are preserved. I found no new text authorizing scope partitions to become independent commit domains.

## 5. Fidelity, regression and author-choice assessment

### 5.1 The core change list is accurate

I applied all 29 A.28 `Was` → `Now` replacements to the exact 6.17 predecessor in memory. The result was **byte-identical to 6.18**.

Thus no additional core edit outside that map was found. This verifies the map’s coverage of the core changes; it does not establish compatibility of the newly incorporated annex.

The D1 comparison likewise confines changes to the identified metadata, domain/validity updates, §9, inspectability and dependency references, additions to §15, and new §16. Map S’s blanket “verbatim” description is imprecise: some old passages use the already-renamed consumer version, and some entries are shorthand such as `candidate 6.17 (x11)`. The actual predecessor remains available, so this is a documentary correction rather than an established loss of a retained rule.

### 5.2 The previous R3 repairs are substantially preserved

| Earlier repair | Current assessment |
| --- | --- |
| Exact facts versus semantic assessments | Preserved by Definitions 16.2–16.3, F-43 and R4; representation targeting needs F618-01 |
| Qualified discovery map | Preserved by F-54 and R14; no renewed promise of cheap exact query-conditioned facets |
| Deletion units and surviving keys | Preserved by R10–R11 |
| Hidden-source counts | Preserved by F-46, R4–R5 and T148 |
| Reference reuse after compaction | Preserved by R9.4 and T149 |
| Confirmation, adoption and fidelity as separate facts | Preserved in F-50 and R4; SC618-01 concerns the different question of permitted resolution bases |

These are assessments of the current text, not retrospective changes to earlier review dispositions.

### 5.3 Domain placement and author choices

Opening D2 for the relied-on pruning property, translation error, evaluation and cost is correctly argued in D1 §9 and core §1.4. It does not open statistical comparison models, person scoring or numerical truth confidence.

The annex form is acceptable. Its cross-cutting incorporation is explicit, but it needs complete schema migration, cap precedence and slice ownership.

The initial numerical defaults are generally labeled as proposals or initial defaults. I found no benchmark claim establishing them. Keep them configurable at their owning layer; distinguish defaults from guarantees.

RT1–RT12 and T141–T162 do not collide with the retained core inventory. Their numbering is acceptable. The missing discrimination and delivery issues concern content, not identifiers.

## 6. Questions and closure for the owner

1. **Resolution bases:** Should the strict R3 prohibition remain, or may adoption authorize use of an otherwise unconfirmed resolution? Restoring the reviewed direction requires no new policy; allowing the exception does.
2. **Declarations:** Is missing-declaration acceptance limited to preserving captured evidence, or is best-effort declaration also intended for deliberate agent record writes? The latter needs an explicit policy and qualification criterion.
3. **Budgets:** Confirm the relationship between retained pilot caps, consequence-class defaults and authorized deep retrieval. Class selection alone should not silently widen the pilot profile.
4. **Before measurement:** Set complete class-specific error, usefulness, abstention and cost requirements, and bind the workload/profile being qualified. Larger-scale requirements remain proposals under D-120.

The required next step is a separately bound revision addressing the findings, followed by independent review and owner ratification. No frozen input should be edited in place.

## 7. Simplicity

Keep the established positional index and its own dictionaries. There is no demonstrated need for a second summary tree, graph store, confidence service or generic value optimizer.

Repair the existing owners directly:

- define the searched representation;
- restore or explicitly decide the resolution-basis rule;
- distinguish capture preservation from write conformance;
- give budgets and counts one coherent interpretation;
- complete the slice map.

Reciprocal rank fusion is a plausible starting method, but the draft has not justified making it the durable ordering rule. Compare it with a simpler lexical-plus-existing-priority baseline. If retained, define route ranks and how correlated alias routes contribute, so compiler over-generation does not arbitrarily multiply one item’s influence. This is an evaluation recommendation, not an additional truth or authority score.

## 8. Evidence, inspectability and limits

**Executed:** Read-only inspection, initial and final hash verification, complete predecessor comparisons, in-memory reconstruction of the core from all 29 A.28 replacements, targeted exact-text checks, branch/HEAD and working-tree checks, local authority/tension searches, and primary search-engine documentation lookup.

**Not executed:** No UPMS implementation, retrieval benchmark, model extraction, database transaction, KMS operation, purge, restore or integration test. RT1–RT12 and T141–T162 remain **UNEXECUTED in this review**.

**Findings and materiality:** The material findings above concern fidelity to owner direction, propagation of ambiguous identity, cost estimation, evaluation bias, declaration conformance, capture disclosure and delivery feasibility. Materiality means a trajectory could change what a reader relies on, what an agent writes, what work is authorized, or whether a gate claim is justified.

**Selection:** One current package was reviewed against its bound predecessors and direction. Documentary probes were chosen adaptively. No empirical model or pipeline variants were evaluated or selected, and no exhaustive-defect-search claim is made.

**Authority and tension coverage:** Searches covered the bound decision records, ratification, R3 critique, 6.17 review, current candidates, change maps and selected semantic-history entries. The recorded D3 adequacy challenge for D-101 remains applicable to the expanded requirement; its own record distinguishes that from a defect in the ratified pilot design. These records identify Claude as their AI recorder and attribute the decisions to the owner; this review did not access the original conversations. Native GitHub issues were unreachable. Older tensions were not comprehensively re-adjudicated.

**Inspectability:** D1 §11 explicitly marks the new plan, coverage and answer-support surfaces within the requested deliverable under D-104 and D-110. Existing surfaces marked beyond the deliverable remain beyond it; technical review accepts none on the owner’s behalf. F618-08 identifies an unresolved preservation issue in the proposed coverage surface.

**Independence:** This is outside-Claude-family review, with no additional reviewer-family independence from the earlier Codex records. Historical memory supplied procedural orientation only; current conclusions rest on the inspected files.

**Mutation and persistence:** No repository file was changed. Initial and final HEAD and working-tree listings matched. Unrelated untracked configuration entries were not opened or modified. The designated review file is populated by the caller saving this final response.

**Revisit condition:** A separately hash-bound repair, explicit owner disposition of the policy questions, or a new material counterexample reopens the affected verdict. Technical PASS, if later earned, would still not constitute Gate 0 passage, ratification, implementation authorization or runtime qualification.

