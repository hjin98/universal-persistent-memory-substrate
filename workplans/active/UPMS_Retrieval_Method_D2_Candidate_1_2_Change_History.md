# UPMS D2 Retrieval Method, Change History (Candidate 1.1 → 1.2)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.2 repairs SC619-01 and SC619-02 of the Codex review of 6.19 and its §4.3 note on statistics (dispositions in core change history A.30). Version replacements marked "not followed by a digit" replace only whole version numbers (so `candidate 1.1` does not touch `candidate 1.16`). Each replaced passage is quoted verbatim.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_1.md` | `988733885edbe001ba6547cb9f36608a6e928ce9d16c935ecec2b13fb5fb3ebf` |
| `UPMS_Retrieval_Method_D2_Candidate_1_2.md` | `8b3ba18f9c4bfc85e6ba679318c2bdc0a608817f1ec91f884fb729cc207a6a73` |

## Edits

### D2.2.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.1
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.2
````

### D2.2.2 Kind

Was:

````text
**Kind:** Numerical method family (D2), first candidate, revision 1.1. Revision 1.0 (`UPMS_Retrieval_Method_D2_Candidate_1_0.md`) had NO-PASS in the Codex review of candidate 6.18 (`UPMS_Candidate_6_18_Independent_Review.md`); this revision repairs SC618-02 and F618-03 to F618-05, and its change map is `UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md`.
````

Now:

````text
**Kind:** Numerical method family (D2), first candidate, revision 1.2. Revisions 1.0 and 1.1 had NO-PASS in the Codex reviews of candidates 6.18 and 6.19 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`). Revision 1.1 repaired SC618-02 and F618-03 to F618-05 (`UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md`); revision 1.2 repairs SC619-01 and SC619-02 (`UPMS_Retrieval_Method_D2_Candidate_1_2_Change_History.md`).
````

### D2.2.3 version: D1 (3 places)

Was:

````text
D1 1.18
````

Now:

````text
D1 1.19
````

### D2.2.4 version: core (3 places)

Was:

````text
core 6.19
````

Now:

````text
core 6.20
````

### D2.2.5 file: D1 (1 places)

Was:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md
````

Now:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19.md
````

### D2.2.6 file: core and annex (2 places)

Was:

````text
UPMS_Architecture_Manual_Review_Candidate_6_19
````

Now:

````text
UPMS_Architecture_Manual_Review_Candidate_6_20
````

### D2.2.7 §0.1 D1 label (1 places)

Was:

````text
| D1 formulation candidate 1.18 |
````

Now:

````text
| D1 formulation candidate 1.19 |
````

### D2.2.8 §0.1 core label (1 places)

Was:

````text
| Core 6.19 with the retrieval-and-scale annex |
````

Now:

````text
| Core 6.20 with the retrieval-and-scale annex |
````

### D2.2.9 §2 quantities

Was:

````text
| `cost(π)` | Work of a plan: segment probes, postings decoded, candidates checked, similarity search, model tokens | normalized work units, seconds, tokens |
````

Now:

````text
| `W(π)` | Engine work of a plan (§7.1) | CPU-seconds on the bound deployment |
| `t̂(π)`, `t(π)` | Predicted and measured elapsed engine time of a plan (§12's engine component) | seconds |
| `T(π)` | Internal model tokens of a plan: compilation, resolution, support and fidelity assessment | tokens |
| `C(π)` | Returned context: tokens of the rendered result handed to the consumer | tokens |
````

### D2.2.10 §7.1 units

Was:

````text
Work and tokens are estimated separately; they are different quantities with no fixed conversion. For a plan over the segments `Seg(Pop)` that hold any of the population:
````

Now:

````text
Engine work, elapsed time, internal model tokens and returned context are four different quantities with no fixed conversion between them; each has its own budget (§7.3). Engine work `W` is measured in **CPU-seconds** on the bound deployment, and every coefficient `c_*` in CPU-seconds per operation. For a plan over the segments `Seg(Pop)` that hold any of the population:
````

### D2.2.11 §7.1 time

Was:

````text
A query for a term absent from every segment costs `W_route + W_delta + W_elig`, never zero. Constants are measured on the bound deployment; `|postings_s(α)|` comes from per-segment statistics; `c_sim` from the measured curve of §5. Elapsed time is measured, not derived from `W`.
````

Now:

````text
A query for a term absent from every segment costs `W_route + W_delta + W_elig`, never zero. Coefficients are measured on the bound deployment; `|postings_s(α)|` comes from per-segment statistics; `c_sim` from the measured curve of §5. Elapsed time is not derived from `W` by a fixed rule: it is **predicted** as `t̂(π) = g_f(W(π))`, where `g_f` is a predictor fitted per plan family `f` to measured `(W, t)` pairs on the development workload (initially a linear fit), and **measured** as `t(π)` for every run.
````

### D2.2.12 §7.2 estimation and admission

Was:

````text
### 7.2 Estimation before execution

1. **Estimate and interval.** The planner computes `W(π)` and `T(π)` from statistics and states each with an **empirical interval**: the 5th and 95th percentiles of actual-to-estimate ratios for the plan's family on the development workload, recorded per deployment. It is a diagnostic interval from past runs, not a bound.
2. **Fallback.** When statistics are missing or stale for a part of the population, that part is estimated as a full scan (no pruning), labeled "upper estimate, statistics unavailable".
3. **Eligibility.** An estimate shown to the reader is computed from statistics over content the reader may know exists, or else from quantities that do not depend on hidden content (segment counts, the reader's own population size); it never reveals hidden matches (D1 F-46, annex R5). Internal use of full statistics affects only timing and admission, which are the timing side channel that core §10.1 measures separately.
4. **Decision.** If the estimate exceeds the budget, the planner narrows the plan with the asker (D1 F-54), returns a budget-limited answer with the estimate ("an exhaustive search would cost about N"), or escalates under D-115. The ratio of actual to estimated work is recorded per plan family and is part of the evaluation (§10).
````

Now:

````text
### 7.2 Estimation before execution

1. **Estimates and intervals.** The planner computes `W(π)`, `t̂(π)`, `T(π)` and `C(π)` from statistics. `t̂` and `T` are each stated with an **empirical interval**: the 5th and 95th percentiles of measured-to-predicted ratios for the plan's family on the development workload. It is a diagnostic interval from past runs, not a bound. **Cold start:** until a family has at least 100 measured runs (**initial default**), its interval is stated as "unknown" and admission uses the point prediction from the coefficients alone.
2. **Fallback.** When statistics are missing or stale for a part of the population, that part is estimated as a full scan (no pruning), labeled "upper estimate, statistics unavailable".
3. **Eligibility.** An estimate, an explanation of an estimate and a continuation offered to the reader are computed only from statistics whose counting domain satisfies annex R5: counts over records the reader may know exist, or quantities fixed by the reader's own eligible population. A count over all segments is not of that kind when segments hold records the reader cannot read. Hidden content may affect only timing and the admission decision itself, which is the timing and resource side channel of core §10.1, measured separately (annex T167); no displayed number, explanation or continuation depends on it.
4. **Admission.** A plan is admitted when its point predictions satisfy every component of its budget (§7.3): `t̂ ≤` the effective engine cap, `T ≤` the class's internal-token limit and the remaining task budget (core §14.2 processing limits), and `C ≤` the returned-context limit. Otherwise the planner narrows the plan with the asker (D1 F-54), returns a budget-limited answer with the estimates ("an exhaustive search would take about N seconds of engine time"), or escalates under D-115. An admitted plan whose interval reaches past a cap is admitted with that risk stated; the runtime caps of §7.4 bound it.
5. **Records.** Measured-to-predicted ratios are recorded per plan family and are part of the evaluation (§10).
````

### D2.2.13 §7.3 budgets

Was:

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

Now:

````text
### 7.3 Budgets by consequence class (proposed defaults, D-120)

These are **proposed starting values** for the owner to set. Each class has three budgets, compared componentwise and never converted into one another: an **engine cap** on elapsed engine time, an **internal-token limit** on `T`, and a **returned-context limit** on `C`. They never widen the pilot profile: the **effective engine cap** of a plan is the smaller of its class's engine cap and the pilot profile's query limits (core §14.2: "200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget"; its work budget is read as elapsed engine time); internal tokens also stay within the principal's daily processing limits (core §14.2: "100 model calls and 1 million input+output tokens per principal per day"); and returned context stays inside the context allocation of core §14.2. A larger budget applies only when the request holds the deep-retrieval capability with its budget (core §10.4: "deep retrieval needs its capability and budget"); class selection alone never grants it. A plan that would need more is answered as budget-limited, or the integration requests deep retrieval, which is a new plan under the escalation rule of D-115.

| Class (D1 Definition 16.7) | Engine cap (elapsed engine time) | Internal-token limit (`T`) | Returned-context limit (`C`) | Checks |
| --- | --- | --- | --- | --- |
| Orientation | 0.2 s | 2,000 tokens (compilation only) | ≤ 1,500 tokens (the L0 hub) | exact facts only |
| Recall | 1 s | 6,000 tokens (compilation and resolution) | ≤ 4,000 tokens | exact facts; support unassessed unless asked |
| Explanation | 2 s | 20,000 tokens (plus support assessment of the answer's statements) | ≤ 8,000 tokens | exact facts and support |
| Decision basis | 2 s; with deep retrieval, its budget (proposed 10 s) | 50,000 tokens (plus fidelity checks of every interpretation relied on); with deep retrieval, its budget | within the allocation; with deep retrieval, its budget | complete execution over the stated population, or the gap stated in the answer |
| Mutating command | exact enumeration of the target set within the task budget, under deep retrieval where the set is large | as needed for the preview, within the task budget | the preview | the target set is exact or the command is refused with the estimate |
````

### D2.2.14 §7.4 caps

Was:

````text
Estimates can be wrong. Every search runs under a hard cap of its class's budget; on reaching it, the search stops, keeps what it checked, and reports execution as budget-limited with the unevaluated part (D1 F-46).
````

Now:

````text
Estimates can be wrong. Every search runs under hard caps on measured elapsed engine time and on internal tokens, at its effective budget; on reaching either, it stops, keeps what it checked, and reports execution as budget-limited with the unevaluated part (D1 F-46). Returned context beyond its limit is cut by the ordering of §6 and the cut is reported.
````

### D2.2.15 §10.1–10.3 evaluation

Was:

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
````

Now:

````text
## 10. Evaluating answers (D-111, D-120)

### 10.1 Reference adjudication

**Answerability is judged against the request, not the plan.** Before evaluation, an adjudicator fixes each evaluated request's **parts**: the atomic questions a full answer must settle. For each part, the adjudicator determines, with its **own reference budget** (offline, separate from the product's, and allowed exhaustive scans of the eligible corpus and human judgment), its **reachability within the product budget**:
- **reachable**: the adjudicator exhibits a correct, grounded answer to the part from eligible records, together with a retrieval the product's route kinds can execute within the request's effective budget (§7.3), and confirms it by running that retrieval on the product;
- **not reachable**: the adjudicator's exhaustive search finds no answer in the eligible corpus, or every answer it finds needs more than the request's effective budget;
- **unknown**: neither could be established. An unknown part is never counted as not reachable.

### 10.2 Outcomes and indicators

Each part of a response gets exactly one **part outcome**: **correct** (settled correctly and grounded), **confident wrong** (states something false about it, or presents a limitation as fact), **justified abstention** (left unsettled with a reason that holds, and the part is not reachable), **unjustified abstention** (left unsettled, for any reason, though the part is reachable), or **unknown** (the part's reachability is unknown and it was left unsettled). Each request then gets five **indicators**, which may overlap:

| Indicator | Is 1 when |
| --- | --- |
| `useful` | every part is correct |
| `useful_partial` | at least one part is correct, no part is confident wrong, and not every part is correct |
| `wc` | any part is confident wrong |
| `au` | any part is an unjustified abstention |
| `unk` | any part is unknown |

The rates `u`, `u_partial`, `e_wc` and `a_u` are the means of `useful`, `useful_partial`, `wc` and `au` over the evaluated requests with `unk = 0`; the share with `unk = 1` is reported beside them and must not exceed `k_max`, or the evaluation is incomplete. A useful partial answer to a request with a reachable remainder therefore counts as both `useful_partial` and `au`: it gets credit for what it settled and is charged for what it left that could have been settled.

**Worked example.** A two-part recall request; both parts are reachable. The response answers part 1 correctly with citations and leaves part 2 unresolved, saying so. Part outcomes: correct, unjustified abstention. Indicators: `useful = 0`, `useful_partial = 1`, `wc = 0`, `au = 1`, `unk = 0`. If all 100 evaluated recall requests look like this, `u + u_partial = 100%` meets `u_min`, but `a_u = 100%` exceeds `a_max`, so the variant is **not acceptable**.

### 10.3 Requirements, not a single score

A variant is acceptable only if, for every consequence class and workload family it is qualified for, every requirement of that class holds, and, componentwise, the 95th percentiles of measured elapsed engine time and of internal tokens are within the effective engine cap and the internal-token limit, returned context is always within its limit, and the share of budget-limited stops is at most `b_max`.

| Class | Requirements |
| --- | --- |
| Orientation | Misleading-orientation rate (an L0 or L1 line contradicted by the canonical records it summarizes) ≤ `ε_or`; cold-start orientation success (core §15.2) ≥ `o_min` |
| Recall, explanation | `e_wc ≤ ε_class`; `u + u_partial ≥ u_min`; `a_u ≤ a_max` |
| Decision basis | `e_wc ≤ ε_db`; `u ≥ u_db` (partial answers do not count); `a_u ≤ a_max`; every decision-basis answer carries the gaps F-49 requires |
| Mutating command | Wrong-target rate = 0 (any wrong target is a defect, §10.5); refusal rate for commands whose exact target set was reachable within the task budget ≤ `r_max` |

Among acceptable variants, preference uses `U = u + ½ u_partial − λ · e_wc − ν · a_u` with `λ > ν > 0`, so a confident error costs more than an unjustified abstention, and both cost something. The weight ½ on partial answers is a proposal for the owner to set.

**Proposed starting values for the owner to set before measurement** (D-120): `ε_db` = 1%, `ε_class` = 3% for explanation and 5% for recall, `ε_or` = 2%; `u_min` = 60% for recall and explanation, `u_db` = 50%; `a_max` = 15%; `o_min` = 80%; `r_max` = 5%; `b_max` = 10%; `k_max` = 5%; `λ = 5`, `ν = 1`. These are placeholders that make the asymmetry concrete, not estimates of achievable performance.
````

### D2.2.16 §10.4 heading

Was:

````text
### 10.3 Scale
````

Now:

````text
### 10.4 Scale
````

### D2.2.17 §10.5 heading

Was:

````text
### 10.4 Defects
````

Now:

````text
### 10.5 Defects
````

### D2.2.18 App A

Was:

````text
- **Read directly:** the Codex review of 1.0 (`UPMS_Candidate_6_18_Independent_Review.md`);
````

Now:

````text
- **Read directly:** the Codex reviews of 1.0 and 1.1 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`);
````

### D2.2.19 §3.4 reference to Defects

Was:

````text
and the evaluation records it (§10.4)
````

Now:

````text
and the evaluation records it (§10.5)
````
