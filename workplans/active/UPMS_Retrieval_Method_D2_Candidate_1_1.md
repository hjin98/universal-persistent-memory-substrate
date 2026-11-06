# UPMS Retrieval Method: D2 Candidate 1.1

**Kind:** Numerical method family (D2), first candidate, revision 1.1. Revision 1.0 (`UPMS_Retrieval_Method_D2_Candidate_1_0.md`) had NO-PASS in the Codex review of candidate 6.18 (`UPMS_Candidate_6_18_Independent_Review.md`); this revision repairs SC618-02 and F618-03 to F618-05, and its change map is `UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md`.
**Date:** 5 November 2026
**Status:** PROPOSED D2 authority. Not accepted, not ratified. It is the first D2 text for UPMS and is opened for retrieval only (D1 1.18 §9). No file is accepted by being in the repository.
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request "Start drafting" (5 November 2026); revision 1.1 under the owner's delegation of the revise-and-review cycle. No subagents were used.
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer **outside the Claude family**, reviewed together with D1 1.18 and core 6.19 with its retrieval-and-scale annex, then ratification by the product owner.

---

## 0. Authority metadata

### 0.1 Parents and inputs

| Input | Identity | Role |
| --- | --- | --- |
| D1 formulation candidate 1.18 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md` | Proposed D1 parent: §16 (F-43 to F-55) and the §9 hand-off define what this method must guarantee or measure |
| Core 6.19 with the retrieval-and-scale annex | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_19.md`, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md` | Proposed D3 consumer: realizes the structures and records this method assumes (§14) |
| Owner decisions D-101 to D-116 and D-117 to D-120 | `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`, SHA-256 `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c`; `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`, SHA-256 `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Direction; D-120 asks this text to propose the larger-scale workload for the owner to set |
| Retrieval design note, revision 3 | `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`, SHA-256 `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Direction (§§3, 5.7, 6, 7, 9 there) |
| Accepted-current D1 1.16 and core 6.17 | As bound in `workplans/active/UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | The pilot profile (core §14.2) stays in force until a larger profile is bound |

### 0.2 What this text owns

| Owned here (D2) | Owned elsewhere |
| --- | --- |
| The pruning guarantee and the conditions under which it holds (§3); exactness of lexical and structural routes (§4); the role and measurement of approximate routes (§5); ordering within a returned page (§6); the cost model, estimation before execution and runtime caps (§7); the processing schedule (§8); measurement of translation error (§9); the evaluation of answers (§10); footprint and rebuild estimates (§11); latency measurement (§12); proposed workload defaults (§13) | Meanings: D1 1.18 §16. Structures, records, permissions, deletion, recovery, product choices: core 6.19 and its annex (D3) and D4. Theory–evidence meanings and any numeric score on claims or sources: not opened (D1 §9) |

**No numeric value produced here is stored on a claim, a source or a person**, and none is shown as confidence in an answer. Ordering keys and estimates are transient operational quantities with the meanings defined below (D1 §9, "Operational estimates").

---

## 1. Problem

Given a plan `π = (Pop, R)` (D1 Definition 16.1) over a corpus that may grow to terabytes (D-101), return the items of `Pop` that the exact routes of `R` match, plus labeled similarity proposals, within a budget, such that:

1. **no item satisfying an exact route is skipped** by any step that skips work (D1 F-44); a step that cannot guarantee this does not skip;
2. **cost is estimated before** the search with a stated empirical error interval, **capped during** it, and reported **after** it (D1 F-49);
3. **translation errors** (extraction, resolution, plan compilation) and **similarity recall** are measured against held-out references and reported as coverage, never assumed away (D1 F-43, F-46);
4. **evaluation** rewards useful supported answers and honest abstention over confident error, without rewarding abstention by default (D-111, D-120).

The method guarantees (1) exactly. It does not guarantee recall of meaning; (3) and (4) measure it.

---

## 2. Quantities

| Symbol | Quantity | Unit |
| --- | --- | --- |
| `N` | Spans in the population | spans |
| `C_s`, `S_s`, `w_s` | Content, summary and covered watermark of index segment `s` | — |
| `Δ` | Spans committed after the newest published watermark | spans |
| `p_fp` | False-positive rate of a membership summary | probability per absent atom |
| `cost(π)` | Work of a plan: segment probes, postings decoded, candidates checked, similarity search, model tokens | normalized work units, seconds, tokens |
| `ε_x(f)` | Error rate of extractor `x` for field type `f` on held-out references | errors per field instance |
| `R@k_sim` | Recall of the similarity route against exact nearest neighbours | fraction |
| `R_pass` | End-to-end recall of passages judged relevant | fraction |
| `e_wc`, `a_j`, `a_u`, `u` | Rates of confident wrong answers, justified and unjustified abstentions, useful answers | fraction of evaluated requests |

Every reported rate states its denominator, its reference set and the versions it was measured at.

---

## 3. The pruning guarantee (D1 F-44)

### 3.1 Predicates

An exact route is a Boolean formula over **atoms**: a term `t` (after the analyzer), a phrase `t1 … tn`, or a structural atom `field = value` over recorded interpretations or references. Formulas are put in negation normal form, so negation applies to atoms only.

### 3.2 Summaries

A summary `S_s` of segment `s` answers, for an atom `α`, **absent** or **maybe**. It is **covering** if: `α` matches some span of `C_s` ⇒ `S_s(α) = maybe`. A covering summary has no false negatives; its false positives cost work only. An exact term dictionary (as in an established inverted index) is covering with `p_fp = 0`; a Bloom filter is covering with `p_fp > 0`.

### 3.3 The rule

Evaluate `φ` on `S_s` in three-valued (Kleene) logic:
- a positive atom is **false** if `S_s(α) = absent`, otherwise **unknown**;
- a negated atom is **unknown** (absence of `α` in some spans says nothing about every span);
- a structural atom over a span not processed by the atom's extractor version is **unknown**;
- `AND` is false if any operand is false; `OR` is false only if every operand is false; otherwise unknown.

**Prune segment `s` for `φ` only if the result is false.**

**Proposition 3.1.** If `S_s` is covering for every positive atom of `φ` at the plan's analyzer and extractor versions, and the rule prunes `s`, then no span of `C_s` satisfies `φ`.

*Proof sketch.* By induction on `φ` in negation normal form. A positive atom evaluates false only when `S_s(α) = absent`, which by covering means no span of `C_s` matches `α`. Negated and unprocessed atoms never evaluate false. `AND` false needs a false operand, so no span satisfies that operand; `OR` false needs every operand false, so no span satisfies any. Kleene evaluation is monotone in this sense, so false at the formula means no span satisfies it. ∎

A phrase atom is treated as the `AND` of its terms for pruning (sound, since a phrase match needs every term), and matched exactly afterwards (§4).

### 3.4 Conditions that keep summaries covering

The proposition holds only while every summary used is covering for the content it claims. D3 realizes these conditions (annex §R6); this text states them as the guarantee's premises:

1. **Insertion.** A segment's content and summary are published together, with its analyzer and extractor identities and watermark. Spans in `Δ` are either scanned exactly (a delta buffer) or reported as unevaluated in execution coverage. A summary built before an insertion is never used for content that includes it.
2. **Deletion.** Deleted spans leave a summary covering (its content only shrinks), so bits or entries are never cleared; the summary is rebuilt from surviving content when its false-positive load makes it inefficient (§3.5).
3. **Merge.** A merged segment's summary is built over the complete merged input; bitwise union is used only for Bloom filters with identical size, hash count and seeds, whose union is covering for the union of contents.
4. **Versions.** A summary is keyed by analyzer and extractor version. A plan compiled under another version **cannot prune** with it. Alias and vocabulary expansion add atoms at compile time and need no summary change.
5. **Failure.** A missing, corrupt, incompatible or insufficiently current summary evaluates every atom **unknown**: the segment is searched or reported unevaluated, never skipped.

A pruned segment that is later found to contain a match is a **critical defect**: pruning stops for that summary type until the cause is fixed, and the evaluation records it (§10.4).

### 3.5 Cost of false positives

For a Bloom filter of `m` bits over `n` distinct atoms with `k` hash functions, `p_fp ≈ (1 − e^{−kn/m})^k`, minimized at `k = (m/n) ln 2`, giving about `1.44 · log2(1/p_fp)` bits per atom (about 9.6 bits for `p_fp = 0.01`). Stale entries from deleted content raise the effective `n`; a summary is rebuilt when the surviving share of its atoms falls below a threshold (**initial default** 0.7). A false positive costs one wasted probe of the segment.

**First product:** the inverted index's own exact per-segment term dictionaries are the summaries (`p_fp = 0`); Bloom filters are used only if measurement shows a coarser routing level is worth it (design note R3 §10).

---

## 4. Exact routes

1. **Analyzer.** Tokenization, Unicode normalization, case folding, n-gram generation for unspaced scripts and any stemming are one versioned analyzer identity. The same identity is used to index and to check. An offset map from normalized positions to the original text is kept, so every match cites original characters.
2. **Phrases and boundaries.** Positions are indexed over a span's whole text, not over chunks used for embeddings, so a phrase is never lost at a chunk boundary.
3. **Checking.** A lexical or structural match is confirmed by re-evaluating the atom on the canonical revision with the same analyzer or the same recorded interpretation. The confirmation is the route-match exact fact (D1 Definition 16.2).
4. **Structural atoms** are exact over what was recorded: they match recorded interpretations and references of the stated extractor versions, and say nothing about what an extractor missed (D1 F-43).
5. **Multilingual text.** Each analyzer declares the languages it covers. Spans in other languages are reachable through n-gram routes and reported in processing coverage as outside the language-specific analyzer.

---

## 5. Approximate routes

1. **Role.** Similarity and hub routes propose items; they never skip and never support absence (D1 F-44, F-45). Their proposals are returned in a separately labeled list (D-118).
2. **Filters first.** Mandatory filters, including eligibility, apply before or inside the similarity search, never only after it: post-filtering loses eligible neighbours and, for an untrusted reranker, is too late (core §10.1). The recall loss of the chosen filter strategy is measured at the selectivities of §13.
3. **Measured recall.** `R@k_sim` is measured against exact nearest neighbours. Parameters (index type, quantization, search breadth, graph degree, number of probes) are chosen from recall–latency curves on **development** queries, never from published results on other data. The chosen variant is frozen before its final measurement on **held-out test** queries, which no selection step has used; the number of variants tried and any reuse of test queries are recorded with the result (§9.1).
4. **Versions.** An embedding model and quantization form one version. A change is a versioned rebuild; both versions serve until the new one is complete and measured, and each proposal names its version.
5. **Two recalls kept apart.** `R@k_sim` (nearest-neighbour recall) is not passage recall `R_pass` (§9.3); neither stands for the other.

---

## 6. Ordering within a page

1. **Groups.** Exact-route matches and similarity-only proposals are separate groups (D1 F-43, D-118).
2. **Within a group**, the **baseline** order is the ratified ordering of core §10.2 (time and task scope, explicit priority, freshness and open obligations; source assessments may order within an intent, authorship never), with exact-route matches ordered by their lexical rank where a route has one. Reciprocal rank fusion, `key(x) = Σ_g 1 / (k0 + rank_g(x))` over **route groups** `g` (**initial default** `k0 = 60`), is a candidate to beat the baseline, adopted only if it does on development data (§10). Routes the compiler generated from one expansion (aliases, renderings and phrasings of one term) form one route group, ranked by their best member, so over-generation does not multiply one item's weight.
3. **Ordering never excludes.** Totals are computed independently of ordering and pagination and are stated with their status: **exact**, a **lower bound** (counting stopped at a cap), an **estimate**, or **unknown** (D1 Definition 16.5). A candidate cap, a page limit and an incomplete execution are reported as different events.
4. **Keys are transient.** The ordering key is never stored on a record and never shown as a score.

---

## 7. Cost model, estimation and caps

### 7.1 Model

Work and tokens are estimated separately; they are different quantities with no fixed conversion. For a plan over the segments `Seg(Pop)` that hold any of the population:

```text
W(π) = W_route + W_exec + W_delta + W_elig + W_check + W_count + W_sim + W_rerank

W_route  = Σ_{s ∈ Seg(Pop)} c_sum · atoms(π)          consulting summaries, including of segments then pruned
W_exec   = Σ_{s not pruned} Σ_{α} c_post · |postings_s(α)|
W_delta  = c_scan · |Δ|                                exact scan of the delta buffer
W_elig   = c_elig(Pop)                                 building or checking the eligible population
W_check  = c_check · |candidates|                      confirming matches on canonical text
W_count  = c_count(total status requested)             exact totals can cost more than a page
W_sim    = c_sim(N_elig, params)                       filter-first similarity search (§5)
W_rerank = c_rerank · N_rerank

T(π) = tokens(compile, resolve, assess)
```

A query for a term absent from every segment costs `W_route + W_delta + W_elig`, never zero. Constants are measured on the bound deployment; `|postings_s(α)|` comes from per-segment statistics; `c_sim` from the measured curve of §5. Elapsed time is measured, not derived from `W`.

### 7.2 Estimation before execution

1. **Estimate and interval.** The planner computes `W(π)` and `T(π)` from statistics and states each with an **empirical interval**: the 5th and 95th percentiles of actual-to-estimate ratios for the plan's family on the development workload, recorded per deployment. It is a diagnostic interval from past runs, not a bound.
2. **Fallback.** When statistics are missing or stale for a part of the population, that part is estimated as a full scan (no pruning), labeled "upper estimate, statistics unavailable".
3. **Eligibility.** An estimate shown to the reader is computed from statistics over content the reader may know exists, or else from quantities that do not depend on hidden content (segment counts, the reader's own population size); it never reveals hidden matches (D1 F-46, annex R5). Internal use of full statistics affects only timing and admission, which are the timing side channel that core §10.1 measures separately.
4. **Decision.** If the estimate exceeds the budget, the planner narrows the plan with the asker (D1 F-54), returns a budget-limited answer with the estimate ("an exhaustive search would cost about N"), or escalates under D-115. The ratio of actual to estimated work is recorded per plan family and is part of the evaluation (§10).

### 7.3 Budgets by consequence class (proposed defaults, D-120)

These are **proposed starting values** for the owner to set. They never widen the pilot profile: the **effective cap** of a plan is the smaller of its class cap and the pilot profile's query limits (core §14.2: "200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget"), and the returned context stays inside the context allocation of core §14.2. A larger cap applies only when the request holds the deep-retrieval capability with its budget (core §10.4: "deep retrieval needs its capability and budget"); class selection alone never grants it. A plan that would need more than its effective cap is answered as budget-limited, or the integration requests deep retrieval, which is a new plan under the escalation rule of D-115.

| Class (D1 Definition 16.7) | Class cap (engine work) | Model calls | Returned context | Checks |
| --- | --- | --- | --- | --- |
| Orientation | 0.2 s | none beyond compilation | ≤ 1,500 tokens (the L0 hub) | exact facts only |
| Recall | 1 s | compilation and resolution | ≤ 4,000 tokens | exact facts; support unassessed unless asked |
| Explanation | 2 s | plus support assessment of the answer's statements | ≤ 8,000 tokens | exact facts and support |
| Decision basis | 2 s; with deep retrieval, its budget (proposed 10 s) | plus fidelity checks of every interpretation relied on | within the allocation; with deep retrieval, its budget | complete execution over the stated population, or the gap stated in the answer |
| Mutating command | exact enumeration of the target set within the task budget, under deep retrieval where the set is large | as needed for the preview | the preview | the target set is exact or the command is refused with the estimate |

### 7.4 Runtime caps

Estimates can be wrong. Every search runs under a hard cap of its class's budget; on reaching it, the search stops, keeps what it checked, and reports execution as budget-limited with the unevaluated part (D1 F-46).

---

## 8. Processing schedule

1. **Cascade.** Tier 0 (metadata, the lexical index, rule-based extractors) runs on every committed span; tier 1 (local small models: embeddings, classifiers) by priority; tier 2 (LLM extraction, rendering, checks) by value (checking annex §9.8). A skipped tier never drops text.
2. **Queue order**, within the core's liveness rule (core §9.5: "explicit requests, obligations, retrieval need, consequential reliance and a bounded age-weighted background sweep"):
   1. obligations and consequential reliance (a decision basis, a review obligation);
   2. explicit requests;
   3. first retrieval of an unprocessed span (lazy deepening);
   4. the age-weighted background sweep, with a **reserved share** of processing capacity (**initial default** 20%) so that unpopular spans are not starved.
3. **Checks by consequence.** An interpretation relied on by a decision basis gets two independent extractions and a round-trip check before use. "Independent" means different model identities, preferably of different families, with their shared inputs (the span, the context given, the prompt template) recorded; two calls to one model are not independent. Agreement is an attributed fidelity assessment, not a probability of correctness, and confirms nobody's meaning (D1 F-2); one retrieved more than a threshold number of times (**initial default** 5) gets a round-trip check. Disagreement is recorded as ambiguity, never settled by vote.
4. **Fairness is measured:** queue age by priority class, sweep coverage per month, and the share of first retrievals that returned a shallow result. Under the bound lifecycle workload (§13), every span with an open obligation is processed within a **processing window** (**initial default** 30 days); a span past its window is reported in processing coverage as overdue.

---

## 9. Measuring translation error

### 9.1 References

A **gold set** of permitted real sessions, stratified by language, source kind (agent, human, pasted, tool output) and scope, is annotated by people for: entities and their referents, negation, modality, conditions, quantities with units, times, and nested attribution. Annotation guidelines are versioned; each item is annotated twice and inter-annotator agreement is reported. The gold set is split by time into **development** and **held-out** parts. User corrections and endorsements enter development data only; final scores use held-out data only.

### 9.2 Extraction and resolution

- `ε_x(f)` per field type, as precision and recall, with the **polarity error rate** (negation or modality flipped) reported separately, since it produces confident falsehoods;
- resolution: correct binding, wrong binding and abstention (kept ambiguous) rates per kind of mention (pronoun, definite description, name, quoted speech, pasted content);
- declarations (D1 Definition 16.9): the rate of wrong declared referents in agents' writes, measured on a sample, since declarations are the cheapest route and the one leaned on most (D-103);
- standalone renderings: insertion errors per rendering, and the share of renderings whose stated context omits something needed.

### 9.3 Plans and passages

For held-out questions with exhaustive relevance judgments over a bounded corpus:
- **plan fidelity:** the share of relevant passages that the compiled plan's exact routes match;
- **passage recall** `R_pass` of exact routes alone and of exact routes with similarity proposals;
- **supported-answer error:** the share of answer statements whose cited spans do not support them.

### 9.4 Exact-route agreement

Exact routes are checked against an independent exhaustive reference on sampled plans, including after insertions, deletions, merges and rebuilds. The reference is a separately implemented matcher that follows the analyzer's written specification (normalization, tokenization, n-grams, offsets); sharing an analyzer identity is needed for comparison but does not validate the analyzer itself, so the specification is also tested on fixed examples, including offsets back to the original text and phrases across span boundaries. Any disagreement is a defect, not an error rate.

---

## 10. Evaluating answers (D-111, D-120)

### 10.1 Outcomes

**Answerability is judged against the request, not the plan.** For each evaluated request, an adjudicator, using an exhaustive search of the eligible corpus within the request's budget class and the request's own wording, records whether an answer was reachable. Each request is then classed:
- **useful**: correct, grounded, within budget;
- **useful partial**: correct and grounded for part of the request, with the unresolved remainder stated;
- **confident wrong**: states something false, or presents a limitation as fact;
- **justified abstention**: says it cannot settle the question, with a reason that holds, where the adjudicator found no reachable answer;
- **unjustified abstention**: abstains, or answers only partially, where the adjudicator found a reachable answer, whatever the reason the system gave. A correctly disclosed bad plan is honest, but it is still an unjustified abstention.

### 10.2 Requirements, not a single score

A variant is acceptable only if, for every consequence class and workload family it is qualified for, every requirement of that class holds and its mean and 95th-percentile work and tokens stay within the class's effective cap (§7.3).

| Class | Requirements |
| --- | --- |
| Orientation | Misleading-orientation rate (an L0 or L1 line contradicted by the canonical records it summarizes) ≤ `ε_or`; cold-start orientation success (core §15.2) ≥ `o_min` |
| Recall, explanation | `e_wc ≤ ε_class`; `u + u_partial ≥ u_min`; `a_u ≤ a_max` |
| Decision basis | `e_wc ≤ ε_db`; `u ≥ u_db` (partial answers do not count); `a_u ≤ a_max`; every decision-basis answer carries the gaps F-49 requires |
| Mutating command | Wrong-target rate = 0 (any wrong target is a defect, §10.4); refusal rate for commands whose exact target set was reachable within the task budget ≤ `r_max` |

Among acceptable variants, preference uses `U = u + ½ u_partial − λ · e_wc − ν · a_u` with `λ > ν > 0`, so a confident error costs more than an unjustified abstention, and both cost something.

**Proposed starting values for the owner to set before measurement** (D-120): `ε_db` = 1%, `ε_class` = 3% for explanation and 5% for recall, `ε_or` = 2%; `u_min` = 60% for recall and explanation, `u_db` = 50%; `a_max` = 15%; `o_min` = 80%; `r_max` = 5%; `λ = 5`, `ν = 1`. These are placeholders that make the asymmetry concrete, not estimates of achievable performance.

### 10.3 Scale

**Pilot qualification measures at the pilot envelope only.** Measurements at 10× and 100× it, by adding synthetic growth drawn from the distribution of permitted real sessions, are **optional diagnostics** until a profile claiming that scale is bound; for such a profile, they become its qualification obligations at the corpus steps it claims (§13). The curves reported are passage recall, `e_wc`, latency by component, footprint and purge debt against corpus size.

### 10.4 Defects

A false-negative prune (§3.4), an exact-route disagreement (§9.4), a hidden record in coverage (D1 F-46), a limitation reported as a finding and a wrong target of a mutating command are defects: each stops the variant's acceptance until fixed, whatever its scores.

---

## 11. Footprint and rebuild estimates

| Component | Steady-state estimate |
| --- | --- |
| Full vectors | `N · d · b` bytes (`d` dimensions, `b` bytes per value) |
| Compressed codes | `N · c` bytes |
| Graph links (HNSW-type) | about `8 · M · N` bytes for degree parameter `M` |
| Identifiers | `8 · N` bytes for 64-bit identifiers |
| Lexical index | `ρ · T`, with `T` the indexed text size and `ρ` measured on the deployment's text (**unverified**) |

**Peak** footprint adds a rebuild copy of each structure rebuilt at once, headroom for the maintenance outputs that may run concurrently (merges, purge rewrites and rebuilds, up to the concurrency bound of §13, each up to its segment's size), staging and replicas. **Rebuild time** is `N / θ` for measured throughput `θ` (spans per second) per structure; re-embedding is `N / θ_embed`. Planning numbers for 1 TB in about 2 KB spans (about 500 million spans) are in design note R3 §3.5; whether full vectors fit is decided against the bound profile's RAM, not the corpus alone.

---

## 12. Latency

Latency is measured by component: plan compilation, engine (segment probes, postings, checks), similarity search, remote inference, source fetch, first-use deepening and release-record commit. The pilot targets of core §14.2 (p95 ≤ 500 ms warm, ≤ 2 s cold, excluding remote inference and source fetch) stay in force at the pilot size. For a larger profile, D-114's target (p95 at most 1 to 2 s on hot tiers) applies to the **engine component** for the workload families named in that profile's binding; this text proposes **1.5 s** for the rare-term, key and bounded-scope families and leaves broad families to report their measured envelope (§13).

---

## 13. Proposed defaults for a larger profile (D-120)

**All values here are proposals for the owner to set**; none binds until a larger profile is bound.

| Item | Proposed default |
| --- | --- |
| Workload families and mix | Exact key or identifier lookup 20%; rare-term lexical 25%; common-term within a bounded scope or time window 20%; semantic recall (similarity with exact routes) 20%; entity and tag facets 10%; broad negatives, many-scope and phrase queries 5% |
| Filter selectivities to measure | Eligible population 100%, 10%, 1% and 0.1% of the corpus |
| Concurrency | 50 concurrent queries; 10 concurrent writers |
| Bulk import | 10 GB per day sustained, in batches, without breaking the single committer's ordering (core §9.1) |
| Degraded recovery service | Within the RTO: the fidelity plane with the latest recovery-log position proven, and exact references (E0); within 24 h: the lexical baseline (E1); within 72 h: structural and similarity routes. Coverage reports what is not yet restored |
| Corpus steps | 100 GB, 1 TB, each qualified separately |
| Lifecycle workload | Deletions of 1% of records per month, spread uniformly across segments, with bursts of 10,000 deletions in an hour; corrections and redactions at 0.5% per month; one re-extraction of the whole corpus per year; one embedding-model change per year |
| Maintenance concurrency | At most 4 concurrent merges, 2 concurrent purge rewrites and 1 rebuild per tier; purge has priority over merges, and nonessential ingestion stops before purge misses its target (core §14.2 disk admission) |
| Purge envelope | Under the lifecycle workload and maintenance concurrency above, every deletion reaches `purged_live` within the 24 h live-surface target; purge debt is measured and reported |

---

## 14. Hand-off to D3, validity and reopening

**D3 must realize** (core 6.19 retrieval annex): atomic publication of segments with summaries, versions and watermarks; a delta buffer or uncovered-delta reporting; per-segment statistics for estimation; runtime caps; the processing queue with its reserved share; separate groups for exact and similarity results; and the measurement hooks of §§9 to 12.

**In regime:** text and structured records up to the size storage permits, with the guarantee of §3 at any size. **Out of regime:** recall of meaning as a guarantee; calibrated probabilities of truth; any score on claims, sources or people.

**Reopen** this text if: a false-negative prune is ever observed; `e_wc` exceeds its limit in any class; estimate-to-actual cost ratios make budget-limited answers frequent enough that the owner's `u_min` cannot be met; a new route kind (for example graph traversal for retrieval) is proposed; or a profile claims a scale this text has not measured.

**Open questions.**
1. Whether a gold set large enough for stable per-field rates is affordable in the pilot, given that it needs human annotation.
2. Whether filter-first similarity search keeps acceptable recall at 0.1% selectivity, or such plans should use exact routes only.
3. Whether the proposed budgets leave decision-basis answers complete often enough at 1 TB.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the author of the design note, D1 and the core. Shared blind spots are likely; a reviewer outside the Claude family is required before acceptance.
- **Read directly:** the Codex review of 1.0 (`UPMS_Candidate_6_18_Independent_Review.md`); design note revision 3, its three Codex critiques, decision records D-101 to D-120, D1 1.16 §§9 and 16 as drafted in 1.17, and the core sections the annex changes.
- **External facts used:** the Bloom-filter false-positive formula and optimum; reciprocal rank fusion's form and conventional `k0`; the approximate HNSW link footprint cited in the Codex critique of revision 1 (Faiss documentation). None is used as a measured property of UPMS.
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated. Every number marked initial default or proposed is a placeholder for measurement or the owner's setting.
