# UPMS D2 Retrieval Method, Change History (Candidate 1.4 → 1.5)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.5 repairs the Codex review of D2 1.4 (`UPMS_D2_1_4_Independent_Review.md`, NO-PASS). Each replaced passage is quoted verbatim; applied in order to revision 1.4, the edits give revision 1.5 byte for byte.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_4.md` | `60374b78500503e7d108b449d798281d8a4a52e941c0fe86e5c060a854ddd1b9` |
| `UPMS_Retrieval_Method_D2_Candidate_1_5.md` | `739abc989ca337e7e4f7a88bfbaf9efad70fd408dd6be3dbecc86bb3c22e4a5a` |

## Dispositions

| Finding | Disposition | Where |
| --- | --- | --- |
| SC-D214-01: the `a_u` bound drops known requests of mixed episodes | Accepted. Exactly one counted request per class per episode (`r` removed), so each rate's population is a set of independent requests; `a_u` counts every counted request with known `k*` | §10.6 Counting unit, Populations |
| SC-D214-02: refusals of reachable commands diluted by unreachable ones | Accepted. Every rate names its population; refusal is counted over commands whose reference establishes reachability; unknown membership counts only in the unknown share, never as a success; an empty population shows nothing | §10.6 Populations |
| SC-D214-03: repeated fresh-set attempts select a survivor without a rule | Accepted. A qualification plan fixed before its first attempt has an attempt budget `A` (default 3); every bound is at level `α/A`, so by the union bound the 95% assurance covers the variant finally selected; an attempt's sample is never enlarged and retested; a new plan is a new claim reported with every failed attempt. The owner's second question (per attempt or selected result) is answered by the stronger reading, which D-122's "never loosen a limit silently" requires; `A` is the owner's to set | §10.6 Three phases item 2, Bounds, Sizes, Worked example |
| F-D214-01: episode totals presented as the qualification budget | Accepted. The table is described as minimum sizes for one error-rate test; the plan sizes every claimed population, including conditional ones, languages and families; success rates need a stated margin | §10.6 Sizes |
| F-D214-02: oracle isolation | Accepted. Keys, manifests, seeds and adjudication records are oracle-only; the product may not read them, including when running a witness; D4 binds component inputs and includes a leaked-key negative case. The generator audit is stated not to replace core §15.2 human adjudication | §9.1 |

The review's first owner question (`r = 1`) is answered by the repair of SC-D214-01, a method simplification; its third (which claims the pilot must establish, and the budgets for them) is the owner's, to be set with the qualification plan after calibration.

## Edits

### D2.5.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.4
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.5
````

### D2.5.2 Kind a

Was:

````text
revision 1.4. Revisions 1.0 to 1.2 had NO-PASS in the Codex reviews of candidates 6.18 to 6.20 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`).
````

Now:

````text
revision 1.5. Revisions 1.0 to 1.2 had NO-PASS in the Codex reviews of candidates 6.18 to 6.20 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`), and revision 1.4 in the Codex review of D2 1.4 (`UPMS_D2_1_4_Independent_Review.md`).
````

### D2.5.3 Kind b

Was:

````text
revision 1.4 adds how evaluation values are set and how acceptance is decided on confidence bounds (§§9.1, 10.3, 10.6), under D-121 and D-122 (`UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md`).
````

Now:

````text
revision 1.4 added how evaluation values are set and how acceptance is decided on confidence bounds (§§9.1, 10.3, 10.6), under D-121 and D-122 (`UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md`); revision 1.5 repairs SC-D214-01 to SC-D214-03, F-D214-01 and F-D214-02 of that review (`UPMS_Retrieval_Method_D2_Candidate_1_5_Change_History.md`).
````

### D2.5.4 Author

Was:

````text
revision 1.4 after the owner's answer "Go ahead" to the evaluation plan recorded as D-122. No subagents were used.
````

Now:

````text
revision 1.4 after the owner's answer "Go ahead" to the evaluation plan recorded as D-122; revision 1.5 under the owner's delegation of the revise-and-review cycle. No subagents were used.
````

### D2.5.5 §9.1 oracle isolation

Was:

````text
Planted-fact references measure the mechanism; they do not establish behaviour on real users' sessions (core §15.2), and they do not replace the gold set for extraction rates on real text (§9.2).
````

Now:

````text
Planted-fact references measure the mechanism; they do not establish behaviour on real users' sessions (core §15.2), and they do not replace the gold set for extraction rates on real text (§9.2) or the human adjudication of core §15.2.

**Oracle isolation.** Answer keys, planted-fact manifests, generator seeds and adjudication records are **oracle-only**: they are stored apart from the product-visible material of an episode. The adjudicator may use them; the product may not, whether it is producing an evaluated response or running a witness (§10.1), through retrieval, prompts, caches, models or any other input. The D4 evidence specification binds the permitted inputs of every evaluated component and includes a negative case in which a key is deliberately placed in product-visible material and the leak must be detected.
````

### D2.5.6 §10.6 replaced

Was:

````text
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


````

Now:

````text
### 10.6 Calibration, qualification and sample size (D-122)

**Structural requirements are checked case by case.** The defects of §10.5, the rule that a mutating command has no wrong target, the grounding of every answer statement in cited spans, and the gaps F-49 requires of decision-basis answers are deterministic contract checks: each evaluated case passes or fails, and one failure blocks the variant. The bounds below decide only the rates of §10.3.

**Three phases.**
1. **Calibration** uses development episodes and development queries only. The parameters of §§5 to 7 are tuned, the cost models of §7.2 fitted, and each class's rates measured to show what is achievable. The owner then sets the values of §§7.3 and 10.3; each is recorded with the calibration results it was set from, and frozen. The number of variants tried is recorded (§9.1).
2. **Qualification** uses held-out episodes that no calibration step has used, under a **qualification plan** fixed before its first attempt: the frozen variant and values, the counted populations below and their sizes, the population and sampling mechanism episodes are drawn from, the language and workload-family proportions, and an **attempt budget** `A` (**initial default** `A = 3`). Each attempt is a new study of fixed size on fresh held-out episodes, with every bound taken at level `α/A`, `α` = 5%; an attempt's sample is never enlarged and tested again. If an attempt fails and a changed variant is tried, the episodes already used become development data, and the next attempt, on fresh episodes, counts against `A`. By the union bound, the probability that any of the `A` attempts accepts a variant that fails a requirement is at most `α`, so the 95% assurance covers the variant finally selected, not only each attempt. When `A` attempts have failed, the class is not qualified under that plan. A new plan is a new claim: it is reported with every earlier failed attempt, and it never turns a failed attempt into a pass (core §15.2: "the rule is never relaxed after results").
3. **Operation.** After qualification, confident errors found in real use, through users' corrections and audits, are counted per class. Errors found only through corrections are a **lower bound** on real errors, since unnoticed errors are not counted: operation can reopen a qualified value (§14) but never confirm it. Confirmation from real use needs an audited random sample of real answers, which needs the permission core §15.2 names.

**Counting unit.** The unit of count is an **independently generated episode**, or an independently sampled real session: two units share no generator seed, planted fact or source session. Each counted episode contributes **exactly one** counted request of each class it is counted for, chosen before any response is seen; one episode may carry counted requests of several classes. Requests within one episode are not independent, which is why only one per class is counted. Every other evaluated request is reported at request level and is never qualification evidence.

**Populations.** Each rate is a proportion over a stated population of counted requests of one class:

| Rate | A counted request is indicated when | Population |
| --- | --- | --- |
| `e_wc` | `wc = 1` | all counted requests (as in §10.2) |
| unknown share | `k*` is unknown, or for a mutating command whether its exact target set was reachable within the task budget is unknown | all counted requests |
| `a_u` | `au = 1` | counted requests whose `k*` is known |
| `u`; `u + u_partial` | `useful = 1`; `useful = 1` or `useful_partial = 1` | all counted requests |
| misleading orientation | any L0 or L1 line of the response is contradicted by the canonical records it summarizes | all counted orientation requests |
| cold-start orientation success | the success criterion of core §15.2 holds | counted cold-start orientation requests |
| refusal | the command is refused | counted mutating commands whose reference establishes that the exact target set was reachable within the task budget |
| budget-limited stops | the response stopped at a runtime cap (§7.4) | all counted requests |

A counted request whose membership in a conditional population is unknown is counted only in the unknown share, whose bound must meet `k_max`; it is never counted as a success or as a pass. A population with no counted request shows nothing.

**Bounds.** For a population of `m` counted requests of which `x` are indicated, the one-sided exact (Clopper–Pearson) binomial bound at level `α/A` is used. An error or abstention rate passes only if its **upper** bound is at most its limit (`ε_or`, `ε_class`, `ε_db`, `a_max`, `r_max`, `b_max`, `k_max`); a success rate passes only if its **lower** bound is at least its minimum (`u_min`, `u_db`, `o_min`). A point estimate that meets a limit while its bound does not is reported as **not shown at this sample size**, never as passing. An attempt accepts only if every applicable bound passes, so a level-`α/A` test of each requirement also bounds the chance of accepting a variant that fails any one of them. This covers acceptance; it is not simultaneous coverage of every reported interval, and it does not cover claims made afterwards for the subsets that passed (classes, languages or workload families).

**Sizes.** The smallest population whose upper bound meets a limit with `x` indicated requests, for a single attempt (`A = 1`) and under the default plan (`A = 3`):

| Limit | `A = 1`, `x = 0` | `A = 1`, `x = 1` | `A = 3`, `x = 0` | `A = 3`, `x = 1` |
| --- | --- | --- | --- | --- |
| 1% | 299 | 473 | 408 | 603 |
| 2% | 149 | 236 | 203 | 300 |
| 3% | 99 | 157 | 135 | 200 |
| 5% | 59 | 93 | 80 | 119 |
| 10% | 29 | 46 | 39 | 58 |
| 15% | 19 | 30 | 26 | 38 |

These are **minimum sizes for one error-rate test**, not a qualification budget. The plan sizes every population it makes a claim for, including the conditional ones (`a_u` over known `k*`, refusal over reachable commands) and each language and workload family claimed, planning for `x = 1` (**initial default**) so that a single error does not by itself leave a limit unshowable. Success rates need a margin: a population whose observed rate equals the minimum never has a lower bound that meets it, so they are sized from the rate calibration measured, with the margin stated. At the placeholder limits of §10.3 under `A = 3`, the confident-error tests alone need 603 counted decision-basis requests, 300 orientation, 200 explanation and 119 recall, and the refusal test 119 reachable mutating commands; a claim for each language separately needs these sizes in each. Core §15.2's 100 held-out episodes, with their scenario categories, baselines and comparative rule, remain required; where a population needs more, supplementary held-out planted-fact episodes (§9.1) are added for it, separately identified, and never replace that coverage.

**When a limit is not shown,** the attempt fails for that class. The first remedy is a more cautious variant, one that abstains or reports gaps more, still subject to `a_max` and the success minimums; the second is a larger fresh sample in the next attempt. Both count against `A`. Only the owner may change a limit; a limit changed after a qualification result is seen starts a new plan, is recorded with its reason and the results it was changed after, and is reported as set after those results.

**Languages.** Counted episodes are drawn across the pilot languages, English and Chinese (D-121), and mixed-language work, in proportions fixed in the plan. Rates and bounds are also reported per language; acceptance of a class makes no claim for one language unless that language's own bound meets the limit.

**Worked example.** Decision basis with `ε_db` = 1% under the default plan (`A = 3`, each bound at level 5%/3): each attempt uses 603 fresh counted requests. With no confident error the upper bound is 0.68%, and with one it is 0.999%: the limit is shown. With two it is 1.28%, although the point estimate is 0.33%: not shown. A variant whose true rate is 1.01% passes one attempt with probability 1.6%, and at least one of three with probability 4.6%, within the 5% the plan claims.


````

### D2.5.7 App A read

Was:

````text
`UPMS_Candidate_6_21_Independent_Review.md`); decision records D-121 and D-122;
````

Now:

````text
`UPMS_Candidate_6_21_Independent_Review.md`) and the Codex review of D2 1.4 (`UPMS_D2_1_4_Independent_Review.md`); decision records D-121 and D-122;
````

### D2.5.8 App A external

Was:

````text
the exact (Clopper–Pearson) one-sided binomial bound, with the sizes and examples of §10.6 computed from SciPy's beta quantile function.
````

Now:

````text
the exact (Clopper–Pearson) one-sided binomial bound and the union bound over attempts, with the sizes and examples of §10.6 computed from SciPy's beta quantile and binomial distribution functions.
````
