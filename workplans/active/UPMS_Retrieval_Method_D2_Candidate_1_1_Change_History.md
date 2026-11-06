# UPMS D2 Retrieval Method, Change History (Candidate 1.0 → 1.1)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.1 repairs SC618-02, F618-03 to F618-05 and parts of F618-06 and the review's §4.3 and §7 (dispositions in core change history A.29). Each replaced passage is quoted verbatim from 1.0.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_0.md` | `fba8768d1c0ff6ac7725559054acb455fb2a0ae893e82c7c9c0275b31c736f6f` |
| `UPMS_Retrieval_Method_D2_Candidate_1_1.md` | `988733885edbe001ba6547cb9f36608a6e928ce9d16c935ecec2b13fb5fb3ebf` |

## Edits

### D2.1.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.0
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.1
````

### D2.1.2 Kind

Was:

````text
**Kind:** Numerical method family (D2), first candidate.
````

Now:

````text
**Kind:** Numerical method family (D2), first candidate, revision 1.1. Revision 1.0 (`UPMS_Retrieval_Method_D2_Candidate_1_0.md`) had NO-PASS in the Codex review of candidate 6.18 (`UPMS_Candidate_6_18_Independent_Review.md`); this revision repairs SC618-02 and F618-03 to F618-05, and its change map is `UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md`.
````

### D2.1.3 Status

Was:

````text
opened for retrieval only (D1 1.17 §9)
````

Now:

````text
opened for retrieval only (D1 1.18 §9)
````

### D2.1.4 Author

Was:

````text
at the product owner's request "Start drafting" (5 November 2026). No subagents were used.
````

Now:

````text
at the product owner's request "Start drafting" (5 November 2026); revision 1.1 under the owner's delegation of the revise-and-review cycle. No subagents were used.
````

### D2.1.5 Acceptance

Was:

````text
reviewed together with D1 1.17 and core 6.18 with its retrieval-and-scale annex
````

Now:

````text
reviewed together with D1 1.18 and core 6.19 with its retrieval-and-scale annex
````

### D2.1.6 §0.1 D1

Was:

````text
| D1 formulation candidate 1.17 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` |
````

Now:

````text
| D1 formulation candidate 1.18 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md` |
````

### D2.1.7 §0.1 core

Was:

````text
| Core 6.18 with the retrieval-and-scale annex | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18.md`, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` |
````

Now:

````text
| Core 6.19 with the retrieval-and-scale annex | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_19.md`, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md` |
````

### D2.1.8 version: D1 1.17 → 1.18 (1 places)

Was:

````text
D1 1.17
````

Now:

````text
D1 1.18
````

### D2.1.9 version: core 6.18 → 6.19 (2 places)

Was:

````text
core 6.18
````

Now:

````text
core 6.19
````

### D2.1.10 §1 item 2

Was:

````text
2. **cost is known before** the search within a stated error, **capped during** it, and reported **after** it (D1 F-49);
````

Now:

````text
2. **cost is estimated before** the search with a stated empirical error interval, **capped during** it, and reported **after** it (D1 F-49);
````

### D2.1.11 §5.3 dev and test

Was:

````text
3. **Measured recall.** `R@k_sim` is measured against exact nearest neighbours on held-out queries for each index type, quantization and parameter setting; parameters (search breadth, graph degree, number of probes) are chosen from measured recall–latency curves, never from published results on other data.
````

Now:

````text
3. **Measured recall.** `R@k_sim` is measured against exact nearest neighbours. Parameters (index type, quantization, search breadth, graph degree, number of probes) are chosen from recall–latency curves on **development** queries, never from published results on other data. The chosen variant is frozen before its final measurement on **held-out test** queries, which no selection step has used; the number of variants tried and any reuse of test queries are recorded with the result (§9.1).
````

### D2.1.12 §6 ordering

Was:

````text
## 6. Ordering within a page

1. **Groups.** Exact-route matches and similarity-only proposals are separate groups (D1 F-43, D-118).
2. **Within a group**, results are ordered by reciprocal rank fusion of the routes that found them, `key(x) = Σ_r 1 / (k0 + rank_r(x))` (**initial default** `k0 = 60`), then by the ratified orderings of core §10.2 (time and task scope, explicit priority, freshness and open obligations; source assessments may order within an intent, authorship never).
3. **Ordering never excludes.** Total-match counts are computed independently of ordering and pagination; a page shows "312 matches, 30 shown" (D1 Definition 16.5).
4. **Keys are transient.** The ordering key is never stored on a record and never shown as a score.

---
````

Now:

````text
## 6. Ordering within a page

1. **Groups.** Exact-route matches and similarity-only proposals are separate groups (D1 F-43, D-118).
2. **Within a group**, the **baseline** order is the ratified ordering of core §10.2 (time and task scope, explicit priority, freshness and open obligations; source assessments may order within an intent, authorship never), with exact-route matches ordered by their lexical rank where a route has one. Reciprocal rank fusion, `key(x) = Σ_g 1 / (k0 + rank_g(x))` over **route groups** `g` (**initial default** `k0 = 60`), is a candidate to beat the baseline, adopted only if it does on development data (§10). Routes the compiler generated from one expansion (aliases, renderings and phrasings of one term) form one route group, ranked by their best member, so over-generation does not multiply one item's weight.
3. **Ordering never excludes.** Totals are computed independently of ordering and pagination and are stated with their status: **exact**, a **lower bound** (counting stopped at a cap), an **estimate**, or **unknown** (D1 Definition 16.5). A candidate cap, a page limit and an incomplete execution are reported as different events.
4. **Keys are transient.** The ordering key is never stored on a record and never shown as a score.

---
````

### D2.1.13 §7.1–7.2 cost model

Was:

````text
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
````

Now:

````text
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
````

### D2.1.14 §7.3 budgets

Was:

````text
### 7.3 Budgets by consequence class (proposed defaults, D-120)

These are **proposed starting values** for the owner to set; they sit inside the context allocation of core §14.2 (UPMS extras at most min(8,000 tokens, 20% of remaining input)) except where deep retrieval is requested with its capability and budget (core §10.4).

| Class (D1 Definition 16.7) | Engine work cap | Model calls | Returned context | Checks |
| --- | --- | --- | --- | --- |
| Orientation | 0.2 s | none beyond compilation | ≤ 1,500 tokens (the L0 hub) | exact facts only |
| Recall | 1 s | compilation and resolution | ≤ 4,000 tokens | exact facts; support unassessed unless asked |
| Explanation | 2 s | plus support assessment of the answer's statements | ≤ 8,000 tokens | exact facts and support |
| Decision basis | 10 s, or deep retrieval budget | plus fidelity checks of every interpretation relied on | deep retrieval budget | complete execution over the stated population, or the gap stated in the answer |
| Mutating command | exact enumeration of the target set, whatever it costs within the task budget | as needed for the preview | the preview | the target set is exact or the command is refused with the estimate |
````

Now:

````text
### 7.3 Budgets by consequence class (proposed defaults, D-120)

These are **proposed starting values** for the owner to set. They never widen the pilot profile: the **effective cap** of a plan is the smaller of its class cap and the pilot profile's query limits (core §14.2: "200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget"), and the returned context stays inside the context allocation of core §14.2. A larger cap applies only when the request holds the deep-retrieval capability with its budget (core §10.4: "deep retrieval needs its capability and budget"); class selection alone never grants it. A plan that would need more than its effective cap is answered as budget-limited, or the integration requests deep retrieval, which is a new plan under the escalation rule of D-115.

| Class (D1 Definition 16.7) | Class cap (engine work) | Model calls | Returned context | Checks |
| --- | --- | --- | --- | --- |
| Orientation | 0.2 s | none beyond compilation | ≤ 1,500 tokens (the L0 hub) | exact facts only |
| Recall | 1 s | compilation and resolution | ≤ 4,000 tokens | exact facts; support unassessed unless asked |
| Explanation | 2 s | plus support assessment of the answer's statements | ≤ 8,000 tokens | exact facts and support |
| Decision basis | 2 s; with deep retrieval, its budget (proposed 10 s) | plus fidelity checks of every interpretation relied on | within the allocation; with deep retrieval, its budget | complete execution over the stated population, or the gap stated in the answer |
| Mutating command | exact enumeration of the target set within the task budget, under deep retrieval where the set is large | as needed for the preview | the preview | the target set is exact or the command is refused with the estimate |
````

### D2.1.15 §8.3 independence

Was:

````text
3. **Checks by consequence.** An interpretation relied on by a decision basis gets two independent extractions and a round-trip check before use;
````

Now:

````text
3. **Checks by consequence.** An interpretation relied on by a decision basis gets two independent extractions and a round-trip check before use. "Independent" means different model identities, preferably of different families, with their shared inputs (the span, the context given, the prompt template) recorded; two calls to one model are not independent. Agreement is an attributed fidelity assessment, not a probability of correctness, and confirms nobody's meaning (D1 F-2);
````

### D2.1.16 §8.4 window

Was:

````text
4. **Fairness is measured:** queue age by priority class, sweep coverage per month, and the share of first retrievals that returned a shallow result.
````

Now:

````text
4. **Fairness is measured:** queue age by priority class, sweep coverage per month, and the share of first retrievals that returned a shallow result. Under the bound lifecycle workload (§13), every span with an open obligation is processed within a **processing window** (**initial default** 30 days); a span past its window is reported in processing coverage as overdue.
````

### D2.1.17 §9.4 reference

Was:

````text
### 9.4 Exact-route agreement

Exact routes are checked against an independent exhaustive reference (a brute-force scan of the same population with the same analyzer) on sampled plans, including after insertions, deletions, merges and rebuilds. Any disagreement is a defect, not an error rate.
````

Now:

````text
### 9.4 Exact-route agreement

Exact routes are checked against an independent exhaustive reference on sampled plans, including after insertions, deletions, merges and rebuilds. The reference is a separately implemented matcher that follows the analyzer's written specification (normalization, tokenization, n-grams, offsets); sharing an analyzer identity is needed for comparison but does not validate the analyzer itself, so the specification is also tested on fixed examples, including offsets back to the original text and phrases across span boundaries. Any disagreement is a defect, not an error rate.
````

### D2.1.18 §10 evaluation

Was:

````text
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
````

Now:

````text
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
````

### D2.1.19 §11 peak

Was:

````text
**Peak** footprint adds a rebuild copy of each structure rebuilt at once, merge headroom up to the largest segment, staging and replicas.
````

Now:

````text
**Peak** footprint adds a rebuild copy of each structure rebuilt at once, headroom for the maintenance outputs that may run concurrently (merges, purge rewrites and rebuilds, up to the concurrency bound of §13, each up to its segment's size), staging and replicas.
````

### D2.1.20 §13 lifecycle

Was:

````text
| Corpus steps | 100 GB, 1 TB, each qualified separately |
````

Now:

````text
| Corpus steps | 100 GB, 1 TB, each qualified separately |
| Lifecycle workload | Deletions of 1% of records per month, spread uniformly across segments, with bursts of 10,000 deletions in an hour; corrections and redactions at 0.5% per month; one re-extraction of the whole corpus per year; one embedding-model change per year |
| Maintenance concurrency | At most 4 concurrent merges, 2 concurrent purge rewrites and 1 rebuild per tier; purge has priority over merges, and nonessential ingestion stops before purge misses its target (core §14.2 disk admission) |
| Purge envelope | Under the lifecycle workload and maintenance concurrency above, every deletion reaches `purged_live` within the 24 h live-surface target; purge debt is measured and reported |
````

### D2.1.21 App A

Was:

````text
- **Read directly:** design note revision 3,
````

Now:

````text
- **Read directly:** the Codex review of 1.0 (`UPMS_Candidate_6_18_Independent_Review.md`); design note revision 3,
````
