# UPMS D2 Retrieval Method, Change History (Candidate 1.2 → 1.3)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.3 repairs SC620-01 to SC620-03 of the Codex review of 6.20 and simplifies §10 to one jointly reachable count per request (dispositions in core change history A.31). Replacements marked "not followed by a digit" replace whole version numbers only. Each replaced passage is quoted verbatim.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_2.md` | `8b3ba18f9c4bfc85e6ba679318c2bdc0a608817f1ec91f884fb729cc207a6a73` |
| `UPMS_Retrieval_Method_D2_Candidate_1_3.md` | `84e61686c74e2a07a8eace77b12afa6bb4789e334634928d68c64508b15c84f6` |

## Edits

### D2.3.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.2
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.3
````

### D2.3.2 Kind a

Was:

````text
revision 1.2. Revisions 1.0 and 1.1 had NO-PASS in the Codex reviews of candidates 6.18 and 6.19 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`).
````

Now:

````text
revision 1.3. Revisions 1.0 to 1.2 had NO-PASS in the Codex reviews of candidates 6.18 to 6.20 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`).
````

### D2.3.3 Kind b

Was:

````text
revision 1.2 repairs SC619-01 and SC619-02 (`UPMS_Retrieval_Method_D2_Candidate_1_2_Change_History.md`).
````

Now:

````text
revision 1.2 repaired SC619-01 and SC619-02 (`UPMS_Retrieval_Method_D2_Candidate_1_2_Change_History.md`); revision 1.3 repairs SC620-01 to SC620-03 and simplifies §10 (`UPMS_Retrieval_Method_D2_Candidate_1_3_Change_History.md`).
````

### D2.3.4 version: D1 (3 places, not followed by a digit)

Was:

````text
D1 1.19
````

Now:

````text
D1 1.20
````

### D2.3.5 version: core (3 places, not followed by a digit)

Was:

````text
core 6.20
````

Now:

````text
core 6.21
````

### D2.3.6 file: D1 (1 places, not followed by a digit)

Was:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19.md
````

Now:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20.md
````

### D2.3.7 file: core and annex (2 places, not followed by a digit)

Was:

````text
UPMS_Architecture_Manual_Review_Candidate_6_20
````

Now:

````text
UPMS_Architecture_Manual_Review_Candidate_6_21
````

### D2.3.8 §0.1 D1 label (1 places, not followed by a digit)

Was:

````text
| D1 formulation candidate 1.19 |
````

Now:

````text
| D1 formulation candidate 1.20 |
````

### D2.3.9 §0.1 core label (1 places, not followed by a digit)

Was:

````text
| Core 6.20 with the retrieval-and-scale annex |
````

Now:

````text
| Core 6.21 with the retrieval-and-scale annex |
````

### D2.3.10 §7.2 cold start

Was:

````text
**Cold start:** until a family has at least 100 measured runs (**initial default**), its interval is stated as "unknown" and admission uses the point prediction from the coefficients alone.
````

Now:

````text
**Cold start.** A family needs at least 20 measured `(W, t)` pairs (**initial default**) before `g_f` is fitted, and 100 before its interval is stated; with fewer, the interval is stated as "unknown". Qualification runs every plan family of the bound workload at least 20 times on the development workload, so in qualified operation a family without a predictor is a new family. For such a family, **elapsed-time prediction is unavailable**: admission compares only `T` and `C` with their limits, the plan runs under the hard caps of §7.4, and the answer states "no time estimate yet for this kind of plan"; its measured run counts toward the family's fit.
````

### D2.3.11 §7.2 item 3 residual

Was:

````text
Hidden content may affect only timing and the admission decision itself, which is the timing and resource side channel of core §10.1, measured separately (annex T167); no displayed number, explanation or continuation depends on it.
````

Now:

````text
Hidden content may affect only resource outcomes: timing, the admission decision and whether a runtime cap is reached. Those are the timing and resource side channel of core §10.1, measured separately (annex T167). The resulting execution status is still reported honestly (admitted or refused, complete or budget-limited), but no displayed number, explanation or continuation is computed from hidden content.
````

### D2.3.12 §10.1–10.2 evaluation

Was:

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
````

Now:

````text
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
````

### D2.3.13 App A

Was:

````text
- **Read directly:** the Codex reviews of 1.0 and 1.1 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`);
````

Now:

````text
- **Read directly:** the Codex reviews of 1.0 to 1.2 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`);
````
