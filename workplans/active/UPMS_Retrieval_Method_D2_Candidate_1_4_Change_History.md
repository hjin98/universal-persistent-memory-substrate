# UPMS D2 Retrieval Method, Change History (Candidate 1.3 → 1.4)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.4 realizes owner decisions D-121 and D-122 (`UPMS_Owner_Decisions_Pilot_Languages_Evaluation_2026-11-05.md`): planted-fact references, calibration before qualification, and acceptance on exact binomial bounds over independent episodes. Each replaced passage is quoted verbatim; applied in order to revision 1.3, the edits give revision 1.4 byte for byte.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_3.md` | `84e61686c74e2a07a8eace77b12afa6bb4789e334634928d68c64508b15c84f6` |
| `UPMS_Retrieval_Method_D2_Candidate_1_4.md` | `60374b78500503e7d108b449d798281d8a4a52e941c0fe86e5c060a854ddd1b9` |

## Edits

### D2.4.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.3
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.4
````

### D2.4.2 Kind a

Was:

````text
revision 1.3. Revisions 1.0 to 1.2 had NO-PASS
````

Now:

````text
revision 1.4. Revisions 1.0 to 1.2 had NO-PASS
````

### D2.4.3 Kind b

Was:

````text
revision 1.3 repairs SC620-01 to SC620-03 and simplifies §10 (`UPMS_Retrieval_Method_D2_Candidate_1_3_Change_History.md`).
````

Now:

````text
revision 1.3 repaired SC620-01 to SC620-03 and simplified §10 (`UPMS_Retrieval_Method_D2_Candidate_1_3_Change_History.md`), passed the Codex review of 6.21 and was ratified (`UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md`); revision 1.4 adds how evaluation values are set and how acceptance is decided on confidence bounds (§§9.1, 10.3, 10.6), under D-121 and D-122 (`UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md`).
````

### D2.4.4 Status

Was:

````text
**Status:** PROPOSED D2 authority. Not accepted, not ratified. It is the first D2 text for UPMS and is opened for retrieval only (D1 1.20 §9).
````

Now:

````text
**Status:** PROPOSED revision of the accepted-current D2 1.3. Not accepted, not ratified; D2 1.3 governs until this revision is reviewed and ratified. D2 is opened for retrieval only (D1 1.20 §9).
````

### D2.4.5 Author

Was:

````text
revision 1.1 under the owner's delegation of the revise-and-review cycle. No subagents were used.
````

Now:

````text
revision 1.1 under the owner's delegation of the revise-and-review cycle; revision 1.4 after the owner's answer "Go ahead" to the evaluation plan recorded as D-122. No subagents were used.
````

### D2.4.6 Acceptance route

Was:

````text
reviewed together with D1 1.20 and core 6.21 with its retrieval-and-scale annex, then ratification
````

Now:

````text
reviewed against the accepted-current D1 1.20 and core 6.21 with its retrieval-and-scale annex, then ratification
````

### D2.4.7 §0.1 D1 row

Was:

````text
| Proposed D1 parent: §16
````

Now:

````text
| Accepted-current D1 parent: §16
````

### D2.4.8 §0.1 core row

Was:

````text
| Proposed D3 consumer: realizes
````

Now:

````text
| Accepted-current D3 consumer: realizes
````

### D2.4.9 §0.1 ratification and decisions rows

Was:

````text
| Accepted-current D1 1.16 and core 6.17 | As bound in `workplans/active/UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | The pilot profile (core §14.2) stays in force until a larger profile is bound |
````

Now:

````text
| Owner ratification of D1 1.20, D2 1.3 and core 6.21 | `workplans/active/UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md`, SHA-256 `ff6a4493b4cf44f55d8488bb22ae9ea9bbe096ea66db0afa08e60847c0c29866` | Binds the accepted-current parents and D2 1.3, of which this text is a revision; the pilot profile (core §14.2) stays in force until a larger profile is bound |
| Owner decisions D-121 and D-122 | `workplans/active/UPMS_Owner_Decisions_Pilot_Languages_Evaluation_2026-11-05.md`, SHA-256 `2f7d25814aaa045e95902a13d6e5feaaf8be418ac27b293e4627e90f43d77e58` | Pilot languages English and Chinese; evaluation values set after calibration and acceptance decided on confidence bounds (§§9.1, 10.3, 10.6) |
````

### D2.4.10 §0.2 owned

Was:

````text
the evaluation of answers (§10);
````

Now:

````text
the evaluation of answers, including calibration, qualification and the confidence bounds that decide acceptance (§10);
````

### D2.4.11 §7.3 values

Was:

````text
These are **proposed starting values** for the owner to set. Each class
````

Now:

````text
These are **proposed starting values** for the owner to set after calibration (§10.6). Each class
````

### D2.4.12 §9.1 planted-fact references

Was:

````text
User corrections and endorsements enter development data only; final scores use held-out data only.
````

Now:

````text
User corrections and endorsements enter development data only; final scores use held-out data only.

**Planted-fact references.** For plans, passages and answers (§§9.3, 10), a generator may build synthetic episodes around facts it plants, with the questions about them and their correct answers fixed at generation; the generator version, seed and planted facts are recorded with each episode. Such a reference is exact for what was planted and for nothing else: the adjudicator still fixes each request's parts and `k*` (§10.1), and statements about content that was not planted are adjudicated as there. A person audits a random sample of each generator version's episodes (**initial default** 50, with at least one per consequence class and per pilot language) for wrong, ambiguous or leaked answers; a failed audit voids that version's episodes until the cause is fixed and the audit repeated. Planted-fact references measure the mechanism; they do not establish behaviour on real users' sessions (core §15.2), and they do not replace the gold set for extraction rates on real text (§9.2).
````

### D2.4.13 §10.3 acceptance

Was:

````text
every requirement of that class holds, and, componentwise,
````

Now:

````text
every requirement of that class holds as decided in §10.6, and, componentwise,
````

### D2.4.14 §10.3 values a

Was:

````text
**Proposed starting values for the owner to set before measurement** (D-120):
````

Now:

````text
**Proposed starting values for the owner to set after calibration and before qualification** (D-120, D-122; §10.6):
````

### D2.4.15 §10.3 values b

Was:

````text
These are placeholders that make the asymmetry concrete, not estimates of achievable performance.
````

Now:

````text
These are placeholders that make the asymmetry concrete, not estimates of achievable performance; §10.6 gives the qualification sizes they would imply.
````

### D2.4.16 §10.6 new

Was:

````text
each stops the variant's acceptance until fixed, whatever its scores.

````

Now:

````text
each stops the variant's acceptance until fixed, whatever its scores.

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

### D2.4.17 §14 reopen

Was:

````text
`e_wc` exceeds its limit in any class;
````

Now:

````text
in operation, the lower 95% bound of the confident-error rate found in a class exceeds that class's frozen limit (§10.6);
````

### D2.4.18 §14 question 1

Was:

````text
1. Whether a gold set large enough for stable per-field rates is affordable in the pilot, given that it needs human annotation.
````

Now:

````text
1. Whether a gold set large enough for stable per-field rates (§9.2) is affordable in the pilot, given that it needs human annotation; answer evaluation can use planted-fact references (§9.1), real-text extraction rates cannot.
````

### D2.4.19 §14 question 4

Was:

````text
3. Whether the proposed budgets leave decision-basis answers complete often enough at 1 TB.
````

Now:

````text
3. Whether the proposed budgets leave decision-basis answers complete often enough at 1 TB.
4. Whether the qualification sizes of §10.6 at the limits the owner sets are affordable to generate and to audit.
````

### D2.4.20 App A read

Was:

````text
- **Read directly:** the Codex reviews of 1.0 to 1.2 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`);
````

Now:

````text
- **Read directly:** the Codex reviews of 1.0 to 1.3 (`UPMS_Candidate_6_18_Independent_Review.md`, `UPMS_Candidate_6_19_Independent_Review.md`, `UPMS_Candidate_6_20_Independent_Review.md`, `UPMS_Candidate_6_21_Independent_Review.md`); decision records D-121 and D-122;
````

### D2.4.21 App A external

Was:

````text
the approximate HNSW link footprint cited in the Codex critique of revision 1 (Faiss documentation).
````

Now:

````text
the approximate HNSW link footprint cited in the Codex critique of revision 1 (Faiss documentation); the exact (Clopper–Pearson) one-sided binomial bound, with the sizes and examples of §10.6 computed from SciPy's beta quantile function.
````
