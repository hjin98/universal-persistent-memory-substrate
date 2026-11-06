# UPMS Retrieval Method: D2 Candidate 1.0

**Kind:** Numerical method family (D2), first candidate.
**Date:** 5 November 2026
**Status:** PROPOSED D2 authority. Not accepted, not ratified. It is the first D2 text for UPMS and is opened for retrieval only (D1 1.17 §9). No file is accepted by being in the repository.
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request "Start drafting" (5 November 2026). No subagents were used.
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer **outside the Claude family**, reviewed together with D1 1.17 and core 6.18 with its retrieval-and-scale annex, then ratification by the product owner.

---

## 0. Authority metadata

### 0.1 Parents and inputs

| Input | Identity | Role |
| --- | --- | --- |
| D1 formulation candidate 1.17 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | Proposed D1 parent: §16 (F-43 to F-55) and the §9 hand-off define what this method must guarantee or measure |
| Core 6.18 with the retrieval-and-scale annex | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18.md`, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` | Proposed D3 consumer: realizes the structures and records this method assumes (§14) |
| Owner decisions D-101 to D-116 and D-117 to D-120 | `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`, SHA-256 `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c`; `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`, SHA-256 `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Direction; D-120 asks this text to propose the larger-scale workload for the owner to set |
| Retrieval design note, revision 3 | `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`, SHA-256 `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Direction (§§3, 5.7, 6, 7, 9 there) |
| Accepted-current D1 1.16 and core 6.17 | As bound in `workplans/active/UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | The pilot profile (core §14.2) stays in force until a larger profile is bound |

### 0.2 What this text owns

| Owned here (D2) | Owned elsewhere |
| --- | --- |
| The pruning guarantee and the conditions under which it holds (§3); exactness of lexical and structural routes (§4); the role and measurement of approximate routes (§5); ordering within a returned page (§6); the cost model, estimation before execution and runtime caps (§7); the processing schedule (§8); measurement of translation error (§9); the evaluation of answers (§10); footprint and rebuild estimates (§11); latency measurement (§12); proposed workload defaults (§13) | Meanings: D1 1.17 §16. Structures, records, permissions, deletion, recovery, product choices: core 6.18 and its annex (D3) and D4. Theory–evidence meanings and any numeric score on claims or sources: not opened (D1 §9) |

**No numeric value produced here is stored on a claim, a source or a person**, and none is shown as confidence in an answer. Ordering keys and estimates are transient operational quantities with the meanings defined below (D1 §9, "Operational estimates").

---

## 1. Problem

Given a plan `π = (Pop, R)` (D1 Definition 16.1) over a corpus that may grow to terabytes (D-101), return the items of `Pop` that the exact routes of `R` match, plus labeled similarity proposals, within a budget, such that:

1. **no item satisfying an exact route is skipped** by any step that skips work (D1 F-44); a step that cannot guarantee this does not skip;
2. **cost is known before** the search within a stated error, **capped during** it, and reported **after** it (D1 F-49);
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
3. **Measured recall.** `R@k_sim` is measured against exact nearest neighbours on held-out queries for each index type, quantization and parameter setting; parameters (search breadth, graph degree, number of probes) are chosen from measured recall–latency curves, never from published results on other data.
4. **Versions.** An embedding model and quantization form one version. A change is a versioned rebuild; both versions serve until the new one is complete and measured, and each proposal names its version.
5. **Two recalls kept apart.** `R@k_sim` (nearest-neighbour recall) is not passage recall `R_pass` (§9.3); neither stands for the other.

---

## 6. Ordering within a page

1. **Groups.** Exact-route matches and similarity-only proposals are separate groups (D1 F-43, D-118).
2. **Within a group**, results are ordered by reciprocal rank fusion of the routes that found them, `key(x) = Σ_r 1 / (k0 + rank_r(x))` (**initial default** `k0 = 60`), then by the ratified orderings of core §10.2 (time and task scope, explicit priority, freshness and open obligations; source assessments may order within an intent, authorship never).
3. **Ordering never excludes.** Total-match counts are computed independently of ordering and pagination; a page shows "312 matches, 30 shown" (D1 Definition 16.5).
4. **Keys are transient.** The ordering key is never stored on a record and never shown as a score.

---

## 7. Cost model, estimation and caps

### 7.1 Model

For a plan over the population's segments `s ∈ Seg(Pop)`:

```text
cost(π) = Σ_{s not pruned} [ c_probe + Σ_{atoms α} c_post · |postings_s(α)| ]
        + c_check · |candidates|
        + c_sim(N_elig, params) + c_rerank · N_rerank
        + tokens(compile, resolve, assess)
```

Constants are measured on the bound deployment. `|postings_s(α)|` comes from per-segment statistics (document frequencies); `c_sim` from the measured curve of §5.

### 7.2 Estimation before execution

The planner computes `cost(π)` from statistics before running and compares it with the request's budget (§7.3). If the estimate exceeds the budget, the planner either narrows the plan with the asker (D1 F-54), returns a budget-limited answer with the estimate ("an exhaustive search would cost about N"), or escalates under D-115. The ratio of actual to estimated cost is recorded per plan family; its distribution is part of the evaluation (§10).

### 7.3 Budgets by consequence class (proposed defaults, D-120)

These are **proposed starting values** for the owner to set; they sit inside the context allocation of core §14.2 (UPMS extras at most min(8,000 tokens, 20% of remaining input)) except where deep retrieval is requested with its capability and budget (core §10.4).

| Class (D1 Definition 16.7) | Engine work cap | Model calls | Returned context | Checks |
| --- | --- | --- | --- | --- |
| Orientation | 0.2 s | none beyond compilation | ≤ 1,500 tokens (the L0 hub) | exact facts only |
| Recall | 1 s | compilation and resolution | ≤ 4,000 tokens | exact facts; support unassessed unless asked |
| Explanation | 2 s | plus support assessment of the answer's statements | ≤ 8,000 tokens | exact facts and support |
| Decision basis | 10 s, or deep retrieval budget | plus fidelity checks of every interpretation relied on | deep retrieval budget | complete execution over the stated population, or the gap stated in the answer |
| Mutating command | exact enumeration of the target set, whatever it costs within the task budget | as needed for the preview | the preview | the target set is exact or the command is refused with the estimate |

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
3. **Checks by consequence.** An interpretation relied on by a decision basis gets two independent extractions and a round-trip check before use; one retrieved more than a threshold number of times (**initial default** 5) gets a round-trip check. Disagreement is recorded as ambiguity, never settled by vote.
4. **Fairness is measured:** queue age by priority class, sweep coverage per month, and the share of first retrievals that returned a shallow result.

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

Exact routes are checked against an independent exhaustive reference (a brute-force scan of the same population with the same analyzer) on sampled plans, including after insertions, deletions, merges and rebuilds. Any disagreement is a defect, not an error rate.

---

## 10. Evaluating answers (D-111, D-120)

### 10.1 Outcomes

Each evaluated request is classed: **useful** (correct, grounded, within budget); **confident wrong** (states something false, or presents a limitation as fact); **justified abstention** (says it cannot settle the question, with a reason that holds); **unjustified abstention** (abstains when the plan within budget would have answered).

### 10.2 Requirements, not a single score

A variant is acceptable only if, per consequence class and workload family:
- `e_wc ≤ ε_class`;
- `u ≥ u_min`;
- `a_u ≤ a_max`;
- mean and 95th-percentile cost within the class budget.

Among acceptable variants, preference uses `U = u − λ · e_wc − ν · a_u` with `λ > ν > 0`, so a confident error costs more than an unjustified abstention, and both cost something.

**Proposed starting values for the owner to set before measurement** (D-120): `ε` = 1% for decision basis, 3% for explanation, 5% for recall; `u_min` = 60% for recall and explanation; `a_max` = 15%; `λ = 5`, `ν = 1`. These are placeholders chosen to make the asymmetry concrete, not estimates of achievable performance.

### 10.3 Scale ladder

Each measurement is repeated at the pilot envelope and at 10× and 100× it, by adding held-out-compatible synthetic growth drawn from the distribution of permitted real sessions, plus every real session available. The curves reported are passage recall, `e_wc`, latency by component and footprint against corpus size. Larger multiples are measured only for a profile that claims them (D-120).

### 10.4 Defects

A false-negative prune (§3.4), an exact-route disagreement (§9.4), a hidden record in coverage (D1 F-46) and a limitation reported as a finding are defects: each stops the variant's acceptance until fixed, whatever its scores.

---

## 11. Footprint and rebuild estimates

| Component | Steady-state estimate |
| --- | --- |
| Full vectors | `N · d · b` bytes (`d` dimensions, `b` bytes per value) |
| Compressed codes | `N · c` bytes |
| Graph links (HNSW-type) | about `8 · M · N` bytes for degree parameter `M` |
| Identifiers | `8 · N` bytes for 64-bit identifiers |
| Lexical index | `ρ · T`, with `T` the indexed text size and `ρ` measured on the deployment's text (**unverified**) |

**Peak** footprint adds a rebuild copy of each structure rebuilt at once, merge headroom up to the largest segment, staging and replicas. **Rebuild time** is `N / θ` for measured throughput `θ` (spans per second) per structure; re-embedding is `N / θ_embed`. Planning numbers for 1 TB in about 2 KB spans (about 500 million spans) are in design note R3 §3.5; whether full vectors fit is decided against the bound profile's RAM, not the corpus alone.

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

---

## 14. Hand-off to D3, validity and reopening

**D3 must realize** (core 6.18 retrieval annex): atomic publication of segments with summaries, versions and watermarks; a delta buffer or uncovered-delta reporting; per-segment statistics for estimation; runtime caps; the processing queue with its reserved share; separate groups for exact and similarity results; and the measurement hooks of §§9 to 12.

**In regime:** text and structured records up to the size storage permits, with the guarantee of §3 at any size. **Out of regime:** recall of meaning as a guarantee; calibrated probabilities of truth; any score on claims, sources or people.

**Reopen** this text if: a false-negative prune is ever observed; `e_wc` exceeds its limit in any class; estimate-to-actual cost ratios make budget-limited answers frequent enough that the owner's `u_min` cannot be met; a new route kind (for example graph traversal for retrieval) is proposed; or a profile claims a scale this text has not measured.

**Open questions.**
1. Whether a gold set large enough for stable per-field rates is affordable in the pilot, given that it needs human annotation.
2. Whether filter-first similarity search keeps acceptable recall at 0.1% selectivity, or such plans should use exact routes only.
3. Whether the proposed budgets leave decision-basis answers complete often enough at 1 TB.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the author of the design note, D1 and the core. Shared blind spots are likely; a reviewer outside the Claude family is required before acceptance.
- **Read directly:** design note revision 3, its three Codex critiques, decision records D-101 to D-120, D1 1.16 §§9 and 16 as drafted in 1.17, and the core sections the annex changes.
- **External facts used:** the Bloom-filter false-positive formula and optimum; reciprocal rank fusion's form and conventional `k0`; the approximate HNSW link footprint cited in the Codex critique of revision 1 (Faiss documentation). None is used as a measured property of UPMS.
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated. Every number marked initial default or proposed is a placeholder for measurement or the owner's setting.
