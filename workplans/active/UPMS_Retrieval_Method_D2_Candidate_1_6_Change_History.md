# UPMS D2 Retrieval Method, Change History (Candidate 1.5 → 1.6)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.6 repairs the Codex review of D2 1.5 (`UPMS_D2_1_5_Independent_Review.md`, NO-PASS). Each replaced passage is quoted verbatim; applied in order to revision 1.5, the edits give revision 1.6 byte for byte.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_5.md` | `739abc989ca337e7e4f7a88bfbaf9efad70fd408dd6be3dbecc86bb3c22e4a5a` |
| `UPMS_Retrieval_Method_D2_Candidate_1_6.md` | `41f56c196eaceac6c1507a4bccb69b823aa712056d02b1bc153b29f7bdc33b62` |

## Dispositions

| Finding | Disposition | Where |
| --- | --- | --- |
| SC-D215-01: a new plan resets the attempt budget | Accepted. A qualification claim is one class with one requirement; every attempt at it, under any plan, variant, limit, population or name, belongs to one lineage that spends a total 5% by a schedule fixed before its first attempt (default `α_t = α/2^t`). The schedule never runs out and never restarts, so the 95% assurance covers the selected variant across any number of plans; later attempts need larger samples. A changed limit continues the lineage, and a pass at it establishes only the changed limit | §10.6 phase 2, Bounds, Sizes, remedies, changed limit, worked example |
| F-D215-01: "only in the unknown share" read globally | Accepted. Unknown membership removes a request from that conditional population only; it stays in every unconditional population with its established errors, successes and stops, and is never success evidence for the conditional requirement | §10.6 Populations |

The review's owner questions: the first (selected-survivor or per-plan assurance) is answered by the stronger reading, as for SC-D214-03; the third (what makes a replacement a different claim) is answered by the claim identity above, under which nothing does; the second (which claims the pilot must establish) is the owner's, with the qualification plan after calibration.

## Edits

### D2.6.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.5
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.6
````

### D2.6.2 Kind a

Was:

````text
revision 1.5. Revisions 1.0 to 1.2 had NO-PASS
````

Now:

````text
revision 1.6. Revisions 1.0 to 1.2 had NO-PASS
````

### D2.6.3 Kind b

Was:

````text
and revision 1.4 in the Codex review of D2 1.4 (`UPMS_D2_1_4_Independent_Review.md`).
````

Now:

````text
and revisions 1.4 and 1.5 in the Codex reviews of D2 1.4 and 1.5 (`UPMS_D2_1_4_Independent_Review.md`, `UPMS_D2_1_5_Independent_Review.md`).
````

### D2.6.4 Kind c

Was:

````text
revision 1.5 repairs SC-D214-01 to SC-D214-03, F-D214-01 and F-D214-02 of that review (`UPMS_Retrieval_Method_D2_Candidate_1_5_Change_History.md`).
````

Now:

````text
revision 1.5 repaired SC-D214-01 to SC-D214-03, F-D214-01 and F-D214-02 of the 1.4 review (`UPMS_Retrieval_Method_D2_Candidate_1_5_Change_History.md`); revision 1.6 repairs SC-D215-01 and F-D215-01 of the 1.5 review (`UPMS_Retrieval_Method_D2_Candidate_1_6_Change_History.md`).
````

### D2.6.5 Author

Was:

````text
revision 1.5 under the owner's delegation of the revise-and-review cycle.
````

Now:

````text
revisions 1.5 and 1.6 under the owner's delegation of the revise-and-review cycle.
````

### D2.6.6 §10.6 phase 2 and lineage

Was:

````text
under a **qualification plan** fixed before its first attempt: the frozen variant and values, the counted populations below and their sizes, the population and sampling mechanism episodes are drawn from, the language and workload-family proportions, and an **attempt budget** `A` (**initial default** `A = 3`). Each attempt is a new study of fixed size on fresh held-out episodes, with every bound taken at level `α/A`, `α` = 5%; an attempt's sample is never enlarged and tested again. If an attempt fails and a changed variant is tried, the episodes already used become development data, and the next attempt, on fresh episodes, counts against `A`. By the union bound, the probability that any of the `A` attempts accepts a variant that fails a requirement is at most `α`, so the 95% assurance covers the variant finally selected, not only each attempt. When `A` attempts have failed, the class is not qualified under that plan. A new plan is a new claim: it is reported with every earlier failed attempt, and it never turns a failed attempt into a pass (core §15.2: "the rule is never relaxed after results").
````

Now:

````text
under a **qualification plan** fixed before each attempt: the frozen variant and values, the counted populations below and their sizes, the population and sampling mechanism episodes are drawn from, and the language and workload-family proportions. Each attempt is a new study of fixed size on fresh held-out episodes; an attempt's sample is never enlarged and tested again. If an attempt fails and a changed variant is tried, the episodes already used become development data, and the next attempt uses fresh episodes.

   **One error budget per claim.** A **qualification claim** is one class with one of its requirements (§10.3). Every attempt at a claim belongs to that claim's single **lineage**, whatever plan, variant, limit, population or name it is made under. The lineage spends a total `α` = 5% by a schedule fixed before its first attempt: attempt `t` of the lineage (`t` = 1, 2, …) takes that claim's bound at level `α_t` (**initial default** `α_t = α / 2^t`: 2.5%, 1.25%, 0.625%, …). The levels sum to at most `α`, so by the union bound the probability that any attempt of the lineage accepts a variant failing its requirement is at most `α`, however many attempts are made and however variants change between them: the 95% assurance covers the variant finally selected. Each further attempt needs a larger sample, which is the price of trying again. A new plan, a renamed plan or a changed limit continues the lineage and never restarts its schedule. Every attempt is reported with the lineage's earlier attempts, and none turns a failed attempt into a pass (core §15.2: "the rule is never relaxed after results").
````

### D2.6.7 §10.6 unknown membership

Was:

````text
A counted request whose membership in a conditional population is unknown is counted only in the unknown share, whose bound must meet `k_max`; it is never counted as a success or as a pass.
````

Now:

````text
A counted request whose membership in a conditional population is unknown is left out of that conditional population only, and is counted in the unknown share, whose bound must meet `k_max`. It stays in every unconditional population with whatever errors, successes and budget-limited stops are established for it (an unknown `k*` never removes a known error, §10.2), and it is never evidence of success for the conditional requirement.
````

### D2.6.8 §10.6 Bounds a

Was:

````text
binomial bound at level `α/A` is used.
````

Now:

````text
binomial bound at the attempt's level `α_t` for that claim is used.
````

### D2.6.9 §10.6 Bounds b

Was:

````text
so a level-`α/A` test of each requirement also bounds
````

Now:

````text
so a level-`α_t` test of each requirement also bounds
````

### D2.6.10 §10.6 Sizes lead

Was:

````text
for a single attempt (`A = 1`) and under the default plan (`A = 3`):
````

Now:

````text
at level 5% (a single prespecified study, for reference) and at the default levels of a lineage's first three attempts:
````

### D2.6.11 §10.6 Sizes table

Was:

````text
| Limit | `A = 1`, `x = 0` | `A = 1`, `x = 1` | `A = 3`, `x = 0` | `A = 3`, `x = 1` |
| --- | --- | --- | --- | --- |
| 1% | 299 | 473 | 408 | 603 |
| 2% | 149 | 236 | 203 | 300 |
| 3% | 99 | 157 | 135 | 200 |
| 5% | 59 | 93 | 80 | 119 |
| 10% | 29 | 46 | 39 | 58 |
| 15% | 19 | 30 | 26 | 38 |
````

Now:

````text
| Limit | 5%, `x = 0` | 5%, `x = 1` | attempt 1 (2.5%), `x = 1` | attempt 2 (1.25%), `x = 1` | attempt 3 (0.625%), `x = 1` |
| --- | --- | --- | --- | --- | --- |
| 1% | 299 | 473 | 555 | 636 | 715 |
| 2% | 149 | 236 | 277 | 317 | 356 |
| 3% | 99 | 157 | 184 | 210 | 237 |
| 5% | 59 | 93 | 110 | 125 | 141 |
| 10% | 29 | 46 | 54 | 62 | 69 |
| 15% | 19 | 30 | 35 | 40 | 45 |
````

### D2.6.12 §10.6 Sizes placeholder

Was:

````text
At the placeholder limits of §10.3 under `A = 3`, the confident-error tests alone need 603 counted decision-basis requests, 300 orientation, 200 explanation and 119 recall, and the refusal test 119 reachable mutating commands;
````

Now:

````text
At the placeholder limits of §10.3, in the first attempt of each lineage, the confident-error tests alone need 555 counted decision-basis requests, 277 orientation, 184 explanation and 110 recall, and the refusal test 110 reachable mutating commands;
````

### D2.6.13 §10.6 remedies

Was:

````text
Both count against `A`.
````

Now:

````text
Both are further attempts of the lineage, at its next level.
````

### D2.6.14 §10.6 changed limit

Was:

````text
Only the owner may change a limit; a limit changed after a qualification result is seen starts a new plan, is recorded with its reason and the results it was changed after, and is reported as set after those results.
````

Now:

````text
Only the owner may change a limit. A limit changed after a qualification result is seen continues the same lineage at its next level; it is recorded with its reason and the results it was changed after, is reported as set after those results, and a pass at it establishes only the changed limit, never the former one.
````

### D2.6.15 §10.6 worked example

Was:

````text
**Worked example.** Decision basis with `ε_db` = 1% under the default plan (`A = 3`, each bound at level 5%/3): each attempt uses 603 fresh counted requests. With no confident error the upper bound is 0.68%, and with one it is 0.999%: the limit is shown. With two it is 1.28%, although the point estimate is 0.33%: not shown. A variant whose true rate is 1.01% passes one attempt with probability 1.6%, and at least one of three with probability 4.6%, within the 5% the plan claims.
````

Now:

````text
**Worked example.** Decision basis with `ε_db` = 1%, in the first attempt of its lineage (level 2.5%): the attempt uses 555 fresh counted requests. With no confident error the upper bound is 0.66%, and with one it is 0.9998%: the limit is shown. With two it is 1.30%, although the point estimate is 0.36%: not shown. A second attempt, at 1.25%, needs 636 fresh requests, and a third, at 0.625%, 715. A variant whose true rate is 1.01% passes these attempts with probabilities 2.4%, 1.2% and 0.58%; over the whole schedule the chance that any attempt passes it stays below 5% (4.6% over the first eleven attempts, each sized this way).
````

### D2.6.16 App A read

Was:

````text
and the Codex review of D2 1.4 (`UPMS_D2_1_4_Independent_Review.md`);
````

Now:

````text
and the Codex reviews of D2 1.4 and 1.5 (`UPMS_D2_1_4_Independent_Review.md`, `UPMS_D2_1_5_Independent_Review.md`);
````
