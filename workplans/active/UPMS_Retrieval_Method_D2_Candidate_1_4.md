# UPMS Retrieval Method: D2 Candidate 1.4

**Kind:** Numerical method family (D2), first candidate, revision 1.4. Revisions 1.0 to 1.2 had NO-PASS in the Codex reviews of candidates 6.18 to 6.20 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`). Revision 1.1 repaired SC618-02 and F618-03 to F618-05 (`UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md`); revision 1.2 repaired SC619-01 and SC619-02 (`UPMS_Retrieval_Method_D2_Candidate_1_2_Change_History.md`); revision 1.3 repaired SC620-01 to SC620-03 and simplified §10 (`UPMS_Retrieval_Method_D2_Candidate_1_3_Change_History.md`), passed the Codex review of 6.21 and was ratified (`UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md`); revision 1.4 adds how evaluation values are set and how acceptance is decided on confidence bounds (§§9.1, 10.3, 10.6), under D-121 and D-122 (`UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md`).
**Date:** 5 November 2026
**Status:** PROPOSED revision of the accepted-current D2 1.3. Not accepted, not ratified; D2 1.3 governs until this revision is reviewed and ratified. D2 is opened for retrieval only (D1 1.20 §9). No file is accepted by being in the repository.
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request "Start drafting" (5 November 2026); revision 1.1 under the owner's delegation of the revise-and-review cycle; revision 1.4 after the owner's answer "Go ahead" to the evaluation plan recorded as D-122. No subagents were used.
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer **outside the Claude family**, reviewed against the accepted-current D1 1.20 and core 6.21 with its retrieval-and-scale annex, then ratification by the product owner.

---

## 0. Authority metadata

### 0.1 Parents and inputs

| Input | Identity | Role |
| --- | --- | --- |
| D1 formulation candidate 1.20 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20.md` | Accepted-current D1 parent: §16 (F-43 to F-55) and the §9 hand-off define what this method must guarantee or measure |
| Core 6.21 with the retrieval-and-scale annex | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_21.md`, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_21_Annex_Retrieval_Scale.md` | Accepted-current D3 consumer: realizes the structures and records this method assumes (§14) |
| Owner decisions D-101 to D-116 and D-117 to D-120 | `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`, SHA-256 `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c`; `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`, SHA-256 `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Direction; D-120 asks this text to propose the larger-scale workload for the owner to set |
| Retrieval design note, revision 3 | `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`, SHA-256 `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Direction (§§3, 5.7, 6, 7, 9 there) |
| Owner ratification of D1 1.20, D2 1.3 and core 6.21 | `workplans/active/UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md`, SHA-256 `ff6a4493b4cf44f55d8488bb22ae9ea9bbe096ea66db0afa08e60847c0c29866` | Binds the accepted-current parents and D2 1.3, of which this text is a revision; the pilot profile (core §14.2) stays in force until a larger profile is bound |
| Owner decisions D-121 and D-122 | `workplans/active/UPMS_Owner_Decisions_Pilot_Languages_Evaluation_2026-11-05.md`, SHA-256 `2f7d25814aaa045e95902a13d6e5feaaf8be418ac27b293e4627e90f43d77e58` | Pilot languages English and Chinese; evaluation values set after calibration and acceptance decided on confidence bounds (§§9.1, 10.3, 10.6) |

### 0.2 What this text owns

| Owned here (D2) | Owned elsewhere |
| --- | --- |
| The pruning guarantee and the conditions under which it holds (§3); exactness of lexical and structural routes (§4); the role and measurement of approximate routes (§5); ordering within a returned page (§6); the cost model, estimation before execution and runtime caps (§7); the processing schedule (§8); measurement of translation error (§9); the evaluation of answers, including calibration, qualification and the confidence bounds that decide acceptance (§10); footprint and rebuild estimates (§11); latency measurement (§12); proposed workload defaults (§13) | Meanings: D1 1.20 §16. Structures, records, permissions, deletion, recovery, product choices: core 6.21 and its annex (D3) and D4. Theory–evidence meanings and any numeric score on claims or sources: not opened (D1 §9) |

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
| `W(π)` | Engine work of a plan (§7.1) | CPU-seconds on the bound deployment |
| `t̂(π)`, `t(π)` | Predicted and measured elapsed engine time of a plan (§12's engine component) | seconds |
| `T(π)` | Internal model tokens of a plan: compilation, resolution, support and fidelity assessment | tokens |
| `C(π)` | Returned context: tokens of the rendered result handed to the consumer | tokens |
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

A pruned segment that is later found to contain a match is a **critical defect**: pruning stops for that summary type until the cause is fixed, and the evaluation records it (§10.5).

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

Engine work, elapsed time, internal model tokens and returned context are four different quantities with no fixed conversion between them; each has its own budget (§7.3). Engine work `W` is measured in **CPU-seconds** on the bound deployment, and every coefficient `c_*` in CPU-seconds per operation. For a plan over the segments `Seg(Pop)` that hold any of the population:

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

A query for a term absent from every segment costs `W_route + W_delta + W_elig`, never zero. Coefficients are measured on the bound deployment; `|postings_s(α)|` comes from per-segment statistics; `c_sim` from the measured curve of §5. Elapsed time is not derived from `W` by a fixed rule: it is **predicted** as `t̂(π) = g_f(W(π))`, where `g_f` is a predictor fitted per plan family `f` to measured `(W, t)` pairs on the development workload (initially a linear fit), and **measured** as `t(π)` for every run.

### 7.2 Estimation before execution

1. **Estimates and intervals.** The planner computes `W(π)`, `t̂(π)`, `T(π)` and `C(π)` from statistics. `t̂` and `T` are each stated with an **empirical interval**: the 5th and 95th percentiles of measured-to-predicted ratios for the plan's family on the development workload. It is a diagnostic interval from past runs, not a bound. **Cold start.** A family needs at least 20 measured `(W, t)` pairs (**initial default**) before `g_f` is fitted, and 100 before its interval is stated; with fewer, the interval is stated as "unknown". Qualification runs every plan family of the bound workload at least 20 times on the development workload, so in qualified operation a family without a predictor is a new family. For such a family, **elapsed-time prediction is unavailable**: admission compares only `T` and `C` with their limits, the plan runs under the hard caps of §7.4, and the answer states "no time estimate yet for this kind of plan"; its measured run counts toward the family's fit.
2. **Fallback.** When statistics are missing or stale for a part of the population, that part is estimated as a full scan (no pruning), labeled "upper estimate, statistics unavailable".
3. **Eligibility.** An estimate, an explanation of an estimate and a continuation offered to the reader are computed only from statistics whose counting domain satisfies annex R5: counts over records the reader may know exist, or quantities fixed by the reader's own eligible population. A count over all segments is not of that kind when segments hold records the reader cannot read. Hidden content may affect only resource outcomes: timing, the admission decision and whether a runtime cap is reached. Those are the timing and resource side channel of core §10.1, measured separately (annex T167). The resulting execution status is still reported honestly (admitted or refused, complete or budget-limited), but no displayed number, explanation or continuation is computed from hidden content.
4. **Admission.** A plan is admitted when its point predictions satisfy every component of its budget (§7.3): `t̂ ≤` the effective engine cap, `T ≤` the class's internal-token limit and the remaining task budget (core §14.2 processing limits), and `C ≤` the returned-context limit. Otherwise the planner narrows the plan with the asker (D1 F-54), returns a budget-limited answer with the estimates ("an exhaustive search would take about N seconds of engine time"), or escalates under D-115. An admitted plan whose interval reaches past a cap is admitted with that risk stated; the runtime caps of §7.4 bound it.
5. **Records.** Measured-to-predicted ratios are recorded per plan family and are part of the evaluation (§10).

### 7.3 Budgets by consequence class (proposed defaults, D-120)

These are **proposed starting values** for the owner to set after calibration (§10.6). Each class has three budgets, compared componentwise and never converted into one another: an **engine cap** on elapsed engine time, an **internal-token limit** on `T`, and a **returned-context limit** on `C`. They never widen the pilot profile: the **effective engine cap** of a plan is the smaller of its class's engine cap and the pilot profile's query limits (core §14.2: "200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget"; its work budget is read as elapsed engine time); internal tokens also stay within the principal's daily processing limits (core §14.2: "100 model calls and 1 million input+output tokens per principal per day"); and returned context stays inside the context allocation of core §14.2. A larger budget applies only when the request holds the deep-retrieval capability with its budget (core §10.4: "deep retrieval needs its capability and budget"); class selection alone never grants it. A plan that would need more is answered as budget-limited, or the integration requests deep retrieval, which is a new plan under the escalation rule of D-115.

| Class (D1 Definition 16.7) | Engine cap (elapsed engine time) | Internal-token limit (`T`) | Returned-context limit (`C`) | Checks |
| --- | --- | --- | --- | --- |
| Orientation | 0.2 s | 2,000 tokens (compilation only) | ≤ 1,500 tokens (the L0 hub) | exact facts only |
| Recall | 1 s | 6,000 tokens (compilation and resolution) | ≤ 4,000 tokens | exact facts; support unassessed unless asked |
| Explanation | 2 s | 20,000 tokens (plus support assessment of the answer's statements) | ≤ 8,000 tokens | exact facts and support |
| Decision basis | 2 s; with deep retrieval, its budget (proposed 10 s) | 50,000 tokens (plus fidelity checks of every interpretation relied on); with deep retrieval, its budget | within the allocation; with deep retrieval, its budget | complete execution over the stated population, or the gap stated in the answer |
| Mutating command | exact enumeration of the target set within the task budget, under deep retrieval where the set is large | as needed for the preview, within the task budget | the preview | the target set is exact or the command is refused with the estimate |

### 7.4 Runtime caps

Estimates can be wrong. Every search runs under hard caps on measured elapsed engine time and on internal tokens, at its effective budget; on reaching either, it stops, keeps what it checked, and reports execution as budget-limited with the unevaluated part (D1 F-46). Returned context beyond its limit is cut by the ordering of §6 and the cut is reported.

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

**Planted-fact references.** For plans, passages and answers (§§9.3, 10), a generator may build synthetic episodes around facts it plants, with the questions about them and their correct answers fixed at generation; the generator version, seed and planted facts are recorded with each episode. Such a reference is exact for what was planted and for nothing else: the adjudicator still fixes each request's parts and `k*` (§10.1), and statements about content that was not planted are adjudicated as there. A person audits a random sample of each generator version's episodes (**initial default** 50, with at least one per consequence class and per pilot language) for wrong, ambiguous or leaked answers; a failed audit voids that version's episodes until the cause is fixed and the audit repeated. Planted-fact references measure the mechanism; they do not establish behaviour on real users' sessions (core §15.2), and they do not replace the gold set for extraction rates on real text (§9.2).

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

### 10.1 Reference adjudication

**Answerability is judged against the request and its one budget, not against the plan.** Before evaluation, an adjudicator fixes each evaluated request's **parts**: the atomic questions a full answer must settle, `n` of them. Then, with its **own reference budget** (offline, separate from the product's, allowed exhaustive scans of the eligible corpus and human judgment), it determines the request's **jointly reachable count** `k*`: the largest number of parts that **one** response can settle correctly and grounded within the request's effective budget (§7.3), all components shared. It records:
- a **witness**: one such response with its retrieval, run on the product within that budget, settling `k*` parts;
- when `k* < n`, the **reason** the other parts do not fit: no answer exists in the eligible corpus, or settling them as well would exceed a named budget component.

If the adjudicator can establish neither the witness nor the reason, `k*` is **unknown**. An unknown `k*` is never treated as zero.

### 10.2 Indicators

For each response, count `k_c`, the parts settled correctly and grounded. Each request gets five indicators, which may overlap:

| Indicator | Is 1 when | Needs `k*` |
| --- | --- | --- |
| `wc` | any part is **confident wrong**: the response states something false about it, or presents a limitation as fact | no |
| `useful` | `k_c = n` | no |
| `useful_partial` | `0 < k_c < n` and `wc = 0` | no |
| `au` | `k*` is known and `k_c < k*` | yes |
| `unk` | `k*` is unknown | — |

**Denominators.** `e_wc`, `u` and `u_partial` are means over **all** evaluated requests; an unknown `k*` never removes a known error. `a_u` is the mean of `au` over requests with known `k*`. The share with `unk = 1` is reported and must not exceed `k_max`, or the evaluation is incomplete. Parts left unsettled beyond `k*`, with an honest reason, cost nothing: that is a budget-justified partial answer.

**Worked examples.**
1. *Avoidable partial answer.* Two parts, both fit in one response (`k* = 2`). The response settles part 1 and says part 2 is unresolved: `useful = 0`, `useful_partial = 1`, `wc = 0`, `au = 1`. If all 100 recall requests look like this, `u + u_partial = 100%` meets `u_min` but `a_u = 100%` exceeds `a_max`: **not acceptable**.
2. *Budget-justified partial answer.* Two parts, each the full text of a record needing 2,400 tokens, with a returned-context limit of 4,000 tokens: one response can settle only one (`k* = 1`, reason: returned context). The response returns record A and reports the remainder as budget-limited: `useful_partial = 1`, `au = 0`. It is not charged.
3. *Known error beside an unknown.* 100 decision-basis requests with two parts each. On 96, both parts are settled correctly. On 4, part 1 is confidently wrong and part 2's reachability is unknown (`wc = 1`, `unk = 1`). Then `e_wc = 4%` over all 100, which exceeds `ε_db = 1%`: **not acceptable**, whatever `a_u` is.

### 10.3 Requirements, not a single score

A variant is acceptable only if, for every consequence class and workload family it is qualified for, every requirement of that class holds as decided in §10.6, and, componentwise, the 95th percentiles of measured elapsed engine time and of internal tokens are within the effective engine cap and the internal-token limit, returned context is always within its limit, and the share of budget-limited stops is at most `b_max`.

| Class | Requirements |
| --- | --- |
| Orientation | Misleading-orientation rate (an L0 or L1 line contradicted by the canonical records it summarizes) ≤ `ε_or`; cold-start orientation success (core §15.2) ≥ `o_min` |
| Recall, explanation | `e_wc ≤ ε_class`; `u + u_partial ≥ u_min`; `a_u ≤ a_max` |
| Decision basis | `e_wc ≤ ε_db`; `u ≥ u_db` (partial answers do not count); `a_u ≤ a_max`; every decision-basis answer carries the gaps F-49 requires |
| Mutating command | Wrong-target rate = 0 (any wrong target is a defect, §10.5); refusal rate for commands whose exact target set was reachable within the task budget ≤ `r_max` |

Among acceptable variants, preference uses `U = u + ½ u_partial − λ · e_wc − ν · a_u` with `λ > ν > 0`, so a confident error costs more than an unjustified abstention, and both cost something. The weight ½ on partial answers is a proposal for the owner to set.

**Proposed starting values for the owner to set after calibration and before qualification** (D-120, D-122; §10.6): `ε_db` = 1%, `ε_class` = 3% for explanation and 5% for recall, `ε_or` = 2%; `u_min` = 60% for recall and explanation, `u_db` = 50%; `a_max` = 15%; `o_min` = 80%; `r_max` = 5%; `b_max` = 10%; `k_max` = 5%; `λ = 5`, `ν = 1`. These are placeholders that make the asymmetry concrete, not estimates of achievable performance; §10.6 gives the qualification sizes they would imply.

### 10.4 Scale

**Pilot qualification measures at the pilot envelope only.** Measurements at 10× and 100× it, by adding synthetic growth drawn from the distribution of permitted real sessions, are **optional diagnostics** until a profile claiming that scale is bound; for such a profile, they become its qualification obligations at the corpus steps it claims (§13). The curves reported are passage recall, `e_wc`, latency by component, footprint and purge debt against corpus size.

### 10.5 Defects

A false-negative prune (§3.4), an exact-route disagreement (§9.4), a hidden record in coverage (D1 F-46), a limitation reported as a finding and a wrong target of a mutating command are defects: each stops the variant's acceptance until fixed, whatever its scores.

### 10.6 Calibration, qualification and sample size (D-122)

**Structural requirements are checked case by case.** The defects of §10.5, the rule that a mutating command has no wrong target, the grounding of every answer statement in cited spans, and the gaps F-49 requires of decision-basis answers are deterministic contract checks: each evaluated case passes or fails, and one failure blocks the variant. The bounds below decide only the rates of §10.3.

**Three phases.**
1. **Calibration** uses development episodes and development queries only. The parameters of §§5 to 7 are tuned, the cost models of §7.2 fitted, and each class's rates measured to show what is achievable. The owner then sets the values of §§7.3 and 10.3; each is recorded with the calibration results it was set from, and frozen. The number of variants tried is recorded (§9.1).
2. **Qualification** uses held-out episodes that no calibration step has used. One frozen variant is qualified against the frozen values by the bounds below. If it fails and a changed variant or value is tried, the held-out episodes already used become development data and the next qualification uses fresh held-out episodes; every reuse is recorded with the result.
3. **Operation.** After qualification, confident errors found in real use, through users' corrections and audits, are counted per class. Errors found only through corrections are a **lower bound** on real errors, since unnoticed errors are not counted: operation can reopen a qualified value (§14) but never confirm it. Confirmation from real use needs an audited random sample of real answers, which needs the permission core §15.2 names.

**Counting unit.** The unit of count is an **independently generated episode**, or an independently sampled real session: two units share no generator seed, planted fact or source session. For each class, every counted episode contributes the same number `r` of evaluated requests of that class (**initial default** `r = 1`), chosen before any response is seen; one episode may carry counted requests of several classes. A counted episode's indicator for an error or abstention rate (`wc`, `au`, a misleading orientation line, a refusal of a reachable command, a budget-limited stop, `unk`) is 1 if any of its `r` requests has it; its indicator for a success rate (`useful`; `useful` or `useful_partial`; cold-start orientation success) is 1 only if all of its `r` requests have it. Because every episode counts the same `r` requests, an episode-level error rate is at least, and an episode-level success rate at most, the request-level rate of §10.2 over the same counted requests, so bounds on episodes are conservative for those requests. Requests within one episode are not independent, which is why they are not counted separately. Request-level rates over all evaluated requests are still reported.

**Bounds.** With `x` of `m` counted episodes indicated, the one-sided 95% exact (Clopper–Pearson) binomial bound is used. An error or abstention rate passes only if its **upper** bound is at most its limit (`ε_or`, `ε_class`, `ε_db`, `a_max`, `r_max`, `b_max`, `k_max`); a success rate passes only if its **lower** bound is at least its minimum (`u_min`, `u_db`, `o_min`). The `wc` bound counts all counted episodes, as `e_wc` does (§10.2); the `au` bound counts the episodes whose counted requests all have known `k*`. A point estimate that meets a limit while its bound does not is reported as **not shown at this sample size**, never as passing.

**Sizes.** The smallest `m` whose upper bound meets a limit with `x` indicated episodes:

| Limit | `x = 0` | `x = 1` | `x = 2` |
| --- | --- | --- | --- |
| 1% | 299 | 473 | 628 |
| 2% | 149 | 236 | 313 |
| 3% | 99 | 157 | 208 |
| 5% | 59 | 93 | 124 |
| 10% | 29 | 46 | 61 |
| 15% | 19 | 30 | 40 |

Each class's qualification set is sized before qualification from its frozen limits, planning for `x = 1` (**initial default**), so that a single error does not by itself leave a limit unshowable; success rates are sized from their lower bound at the rate calibration measured. At the placeholder limits of §10.3 the largest sizes are 473 episodes for decision basis (`ε_db` = 1%), 236 for orientation (`ε_or` = 2%), 157 for explanation and 93 for recall and for mutating commands; since an episode may carry one counted request of each class, the decision-basis size sets the number of episodes. Core §15.2's 100 held-out episodes remain the minimum for the scenario categories it names; where a class needs more, a supplementary held-out set of planted-fact episodes (§9.1) is generated for that class.

**When a limit is not shown,** the class is not qualified at that limit. The first remedy is a more cautious variant, one that abstains or reports gaps more, still subject to `a_max` and the success minimums; the second is a larger sample. Only the owner may change a limit; a changed limit is recorded with its reason and the results it was changed after, and the next qualification uses fresh held-out episodes.

**Languages.** Counted episodes are drawn across the pilot languages, English and Chinese (D-121), and mixed-language work, in proportions fixed before qualification. Rates and bounds are also reported per language; acceptance of a class makes no claim for one language unless that language's own bound meets the limit.

**Worked example.** Decision basis with `ε_db` = 1%: the set is planned at 473 episodes. With no confident error, the upper bound is 0.63%, and the limit is shown. With two, it is 1.33% although the point estimate is 0.42%: not shown. Calibration tries a more cautious variant, and qualification is repeated on fresh held-out episodes.

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

**D3 must realize** (core 6.21 retrieval annex): atomic publication of segments with summaries, versions and watermarks; a delta buffer or uncovered-delta reporting; per-segment statistics for estimation; runtime caps; the processing queue with its reserved share; separate groups for exact and similarity results; and the measurement hooks of §§9 to 12.

**In regime:** text and structured records up to the size storage permits, with the guarantee of §3 at any size. **Out of regime:** recall of meaning as a guarantee; calibrated probabilities of truth; any score on claims, sources or people.

**Reopen** this text if: a false-negative prune is ever observed; in operation, the lower 95% bound of the confident-error rate found in a class exceeds that class's frozen limit (§10.6); estimate-to-actual cost ratios make budget-limited answers frequent enough that the owner's `u_min` cannot be met; a new route kind (for example graph traversal for retrieval) is proposed; or a profile claims a scale this text has not measured.

**Open questions.**
1. Whether a gold set large enough for stable per-field rates (§9.2) is affordable in the pilot, given that it needs human annotation; answer evaluation can use planted-fact references (§9.1), real-text extraction rates cannot.
2. Whether filter-first similarity search keeps acceptable recall at 0.1% selectivity, or such plans should use exact routes only.
3. Whether the proposed budgets leave decision-basis answers complete often enough at 1 TB.
4. Whether the qualification sizes of §10.6 at the limits the owner sets are affordable to generate and to audit.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the author of the design note, D1 and the core. Shared blind spots are likely; a reviewer outside the Claude family is required before acceptance.
- **Read directly:** the Codex reviews of 1.0 to 1.3 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`, `UPMS_Candidate_6_21_Independent_Review.md`); decision records D-121 and D-122; design note revision 3, its three Codex critiques, decision records D-101 to D-120, D1 1.16 §§9 and 16 as drafted in 1.17, and the core sections the annex changes.
- **External facts used:** the Bloom-filter false-positive formula and optimum; reciprocal rank fusion's form and conventional `k0`; the approximate HNSW link footprint cited in the Codex critique of revision 1 (Faiss documentation); the exact (Clopper–Pearson) one-sided binomial bound, with the sizes and examples of §10.6 computed from SciPy's beta quantile function. None is used as a measured property of UPMS.
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated. Every number marked initial default or proposed is a placeholder for measurement or the owner's setting.
