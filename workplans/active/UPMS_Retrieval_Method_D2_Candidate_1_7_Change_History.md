# UPMS D2 Retrieval Method, Change History (Candidate 1.6 → 1.7)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.7 repairs the Codex review of D2 1.6 (`UPMS_D2_1_6_Independent_Review.md`, NO-PASS). Each replaced passage is quoted verbatim; applied in order to revision 1.6, the edits give revision 1.7 byte for byte.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Retrieval_Method_D2_Candidate_1_6.md` | `41f56c196eaceac6c1507a4bccb69b823aa712056d02b1bc153b29f7bdc33b62` |
| `UPMS_Retrieval_Method_D2_Candidate_1_7.md` | `620eff437d91e2db0a15cba15401edca83b173b50edd5a4023e9f0ea5e6858ac` |

## Dispositions

| Finding | Disposition | Where |
| --- | --- | --- |
| SC-D216-01: separate requirement schedules do not protect the selected class qualification | Accepted, with the review's common-envelope repair widened to the whole of §10.3's acceptance: all qualification attempts form one lineage with one schedule; each attempt is joint, declares its class set and requirements (per-language and per-family ones included), tests every declared bound at the attempt's single level `α_s`, and accepts all or nothing. A variant failing any declared requirement is accepted only by passing that bound, so the lineage's false-acceptance probability is at most 5% for every requirement the selected variant is accepted under. Per-class lineages were not used because §10.3 accepts a variant over every class it is qualified for, and accepting passing subsets of an attempt would reopen the same composition problem across classes | §10.6 phase 2, Bounds, Languages, worked example |

The review's owner questions: the first and second (assurance over all requirements; one common schedule) are answered by the stronger reading, as before; the third (which class, family and language claims the pilot must establish) is the owner's, with the qualification plan after calibration.

## Edits

### D2.7.1 title

Was:

````text
# UPMS Retrieval Method: D2 Candidate 1.6
````

Now:

````text
# UPMS Retrieval Method: D2 Candidate 1.7
````

### D2.7.2 Kind a

Was:

````text
revision 1.6. Revisions 1.0 to 1.2 had NO-PASS
````

Now:

````text
revision 1.7. Revisions 1.0 to 1.2 had NO-PASS
````

### D2.7.3 Kind b

Was:

````text
and revisions 1.4 and 1.5 in the Codex reviews of D2 1.4 and 1.5 (`UPMS_D2_1_4_Independent_Review.md`, `UPMS_D2_1_5_Independent_Review.md`).
````

Now:

````text
and revisions 1.4 to 1.6 in the Codex reviews of D2 1.4 to 1.6 (`UPMS_D2_1_4_Independent_Review.md`, `UPMS_D2_1_5_Independent_Review.md`, `UPMS_D2_1_6_Independent_Review.md`).
````

### D2.7.4 Kind c

Was:

````text
revision 1.6 repairs SC-D215-01 and F-D215-01 of the 1.5 review (`UPMS_Retrieval_Method_D2_Candidate_1_6_Change_History.md`).
````

Now:

````text
revision 1.6 repaired SC-D215-01 and F-D215-01 of the 1.5 review (`UPMS_Retrieval_Method_D2_Candidate_1_6_Change_History.md`); revision 1.7 repairs SC-D216-01 of the 1.6 review (`UPMS_Retrieval_Method_D2_Candidate_1_7_Change_History.md`).
````

### D2.7.5 Author

Was:

````text
revisions 1.5 and 1.6 under the owner's delegation
````

Now:

````text
revisions 1.5 to 1.7 under the owner's delegation
````

### D2.7.6 §10.6 one schedule for joint attempts

Was:

````text
   **One error budget per claim.** A **qualification claim** is one class with one of its requirements (§10.3). Every attempt at a claim belongs to that claim's single **lineage**, whatever plan, variant, limit, population or name it is made under. The lineage spends a total `α` = 5% by a schedule fixed before its first attempt: attempt `t` of the lineage (`t` = 1, 2, …) takes that claim's bound at level `α_t` (**initial default** `α_t = α / 2^t`: 2.5%, 1.25%, 0.625%, …). The levels sum to at most `α`, so by the union bound the probability that any attempt of the lineage accepts a variant failing its requirement is at most `α`, however many attempts are made and however variants change between them: the 95% assurance covers the variant finally selected. Each further attempt needs a larger sample, which is the price of trying again. A new plan, a renamed plan or a changed limit continues the lineage and never restarts its schedule. Every attempt is reported with the lineage's earlier attempts, and none turns a failed attempt into a pass (core §15.2: "the rule is never relaxed after results").
````

Now:

````text
   **One error budget for qualification.** All qualification attempts for the product form one **lineage**, numbered `s` = 1, 2, … across every plan, variant, limit, population, class set, name and reopening in operation (§14). Each attempt is **joint**: its plan declares the class set and the requirements of §10.3 it qualifies, including any requirement for one language or workload family, and every bound of every declared requirement is taken at the attempt's single level `α_s`, from one schedule fixed before the first attempt with `Σ α_s ≤ α`, `α` = 5% (**initial default** `α_s = α / 2^s`: 2.5%, 1.25%, 0.625%, …). The attempt accepts its declared class set only if every one of those bounds passes, and otherwise accepts nothing. If the variant of attempt `s` fails any declared requirement, accepting it means passing that requirement's bound, which has probability at most `α_s` given everything before the attempt; summing over attempts, the probability that the lineage ever accepts a variant failing a requirement it is accepted under is at most `α`, however many attempts are made and however variants, limits and class sets change between them. So the 95% assurance covers the variant finally selected, for every requirement it is accepted under. Each further attempt needs a larger sample, which is the price of trying again; a new plan, a renamed plan or a changed limit never restarts the schedule. Every attempt is reported with the lineage's earlier attempts, and none turns a failed attempt into a pass (core §15.2: "the rule is never relaxed after results").
````

### D2.7.7 §10.6 Bounds a

Was:

````text
binomial bound at the attempt's level `α_t` for that claim is used.
````

Now:

````text
binomial bound at the attempt's level `α_s` is used.
````

### D2.7.8 §10.6 Bounds b

Was:

````text
An attempt accepts only if every applicable bound passes, so a level-`α_t` test of each requirement also bounds the chance of accepting a variant that fails any one of them. This covers acceptance; it is not simultaneous coverage of every reported interval, and it does not cover claims made afterwards for the subsets that passed (classes, languages or workload families).
````

Now:

````text
Because an attempt accepts its declared class set only if every declared bound passes, a variant failing any declared requirement is accepted only by passing that requirement's bound. This covers acceptance; it is not simultaneous coverage of every reported interval, and no claim is made for a subset that passed (classes, languages or workload families) unless a later joint attempt declares and accepts it.
````

### D2.7.9 §10.6 Sizes placeholder

Was:

````text
in the first attempt of each lineage, the confident-error tests alone need
````

Now:

````text
in the lineage's first attempt, the confident-error tests alone need
````

### D2.7.10 §10.6 Languages

Was:

````text
Rates and bounds are also reported per language; acceptance of a class makes no claim for one language unless that language's own bound meets the limit.
````

Now:

````text
Rates and bounds are also reported per language. A claim for one language separately is made only when the plan declares that language's requirements, which then belong to the joint attempt like any other; otherwise per-language figures are descriptive.
````

### D2.7.11 §10.6 worked example

Was:

````text
**Worked example.** Decision basis with `ε_db` = 1%, in the first attempt of its lineage (level 2.5%):
````

Now:

````text
**Worked example.** Decision basis with `ε_db` = 1%, in the lineage's first attempt (level 2.5% for every declared requirement):
````

### D2.7.12 §10.6 failed attempt

Was:

````text
**When a limit is not shown,** the attempt fails for that class.
````

Now:

````text
**When a limit is not shown,** the attempt fails and accepts nothing.
````

### D2.7.13 App A read

Was:

````text
`UPMS_D2_1_5_Independent_Review.md`);
````

Now:

````text
`UPMS_D2_1_5_Independent_Review.md`, `UPMS_D2_1_6_Independent_Review.md`);
````

### D2.7.14 App A read label

Was:

````text
Codex reviews of D2 1.4 and 1.5 (`UPMS_D2_1_4
````

Now:

````text
Codex reviews of D2 1.4 to 1.6 (`UPMS_D2_1_4
````
