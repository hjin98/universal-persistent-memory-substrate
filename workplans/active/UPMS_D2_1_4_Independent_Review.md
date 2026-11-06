# UPMS D2 1.4 Independent Review

**Model family / model name:** OpenAI GPT family / Codex, GPT-6-based. The exact serving-model identifier is not exposed in this session.

**Date:** 5 November 2026, America/Chicago.

**Repository binding:** Branch `upms-candidate-6-d1-formulation`, HEAD `113a866016df6886b4b001d4b398252e6c81d5de`.

**Integrity:** I read the request first. Before substantive review, `sha256sum` verified the request’s supplied hash and all nine files it binds. Completion verification repeated those ten checks: **all matched**.

**Reviewed input identities:** Paths are relative to `workplans/active/` unless otherwise stated. Mechanical comparison does not imply a fresh substantive reading of every predecessor paragraph.

| File | SHA-256 | Coverage |
| --- | --- | --- |
| `UPMS_Review_Request_D2_1_4.md` | `6d3ba898de4fbe66f152b9f40467dd7adea98edc4199cba6402ace9be54d6eda` | Read first, in full |
| `UPMS_Retrieval_Method_D2_Candidate_1_4.md` | `60374b78500503e7d108b449d798281d8a4a52e941c0fe86e5c060a854ddd1b9` | Read in full |
| `UPMS_Retrieval_Method_D2_Candidate_1_4_Change_History.md` | `132a795d1c0c710b3514576c85bc9ec4dbdb52ccb901f22c09634e731c156ea9` | Read in full; every replacement reconstructed |
| `UPMS_Owner_Decisions_Pilot_Languages_Evaluation_2026-11-05.md` | `2f7d25814aaa045e95902a13d6e5feaaf8be418ac27b293e4627e90f43d77e58` | Read in full |
| `UPMS_Retrieval_Method_D2_Candidate_1_3.md` | `84e61686c74e2a07a8eace77b12afa6bb4789e334634928d68c64508b15c84f6` | Complete mechanical predecessor comparison; mapped predecessor passages read |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20.md` | `d8bc3558d64e627b739189a6a92d1e42c4c2df2d47dd9bc42b927ad9dec72eab` | Targeted ownership, §9, §§11–16 and Appendix A |
| `UPMS_Architecture_Manual_Review_Candidate_6_21.md` | `e1f28af693ae8805acf2ed2d8cccbca5a1f90038440b7de9a3d3e93d53464f8c` | Targeted language provisions, §§14–18, especially §§14.2, 15.2 and 16 |
| `UPMS_Architecture_Manual_Review_Candidate_6_21_Annex_Retrieval_Scale.md` | `1e12a4313742426b12bda5b1df5f94c86a39d41318e56f42b94c4661da2f284f` | Read in full |
| `UPMS_Owner_Ratification_D1_1_20_D2_1_3_Core_6_21_2026-11-05.md` | `ff6a4493b4cf44f55d8488bb22ae9ea9bbe096ea66db0afa08e60847c0c29866` | Read in full |
| `UPMS_Candidate_6_21_Independent_Review.md` | `8f2b567b177e38da3938ac95d6dc443293d606de60012616b595b63d7f888c23` | Read in full |
| Repository-root `AGENTS.md` | `b1408aadbaa8232d28f7170dd974eb4ecb400a5abca648b267a3671885457e21` | Read in full |
| Repository-root `history/SEMANTIC_EVOLUTION.md` | `696d29c796755f4f6da7556b55698f9e21de9e6c0fc9c9e2b200f3b38a9f16f7` | Searches and targeted retrieval/ratification entries |
| Repository-root `workplans/README.md` | `f8d226b77720bd7f397077ae275f1fe06f16188b89b45bb932ae008d186d1ea3` | Searches and authority/index entries |
| `UPMS_Candidate_6_18_Independent_Review.md` | `9fbe6ed485cf84cae6afa1f4795ddb488660d2bb04b28e636a61c82cd5679108` | Heading-level tension discovery only |
| `UPMS_Candidate_6_19_Independent_Review.md` | `35be5d6e4131d9f884ecea427102936105e9b6cc6b38ec9f1025c63c6dc9a766` | Heading-level tension discovery only |
| `UPMS_Candidate_6_20_Independent_Review.md` | `7bbbb2ae480bc96e0ef1bf01754929dec39a3a2198a8227c0e128940530f2229` | Heading-level tension discovery only; dispositions examined through the bound 6.21 review |

Procedural sources were consulted as guidance, not UPMS authority. Paths below are relative to `/home/samjin/.codex/`.

| Procedural source | SHA-256 |
| --- | --- |
| `skills/numerical-algorithm-design/SKILL.md` | `4de404bb9c1e24e82e0d26806b35a01b43b933e63294a54492769d6b6ec2826d` |
| `skills/numerical-algorithm-design/references/numerical-algorithm-design.md` | `f41f73eb5d3acb09ce7138e3f18ca5cb9c26e90a651f13548b8eee3fa7ecf267` |
| `skills/numerical-algorithm-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` |
| `skills/numerical-algorithm-design/references/testing-and-validation.md` | `ad94b0a98443a81ed35ac1ccc6a90beb067ae81fa7faf61317a7efdeb4c044c0` |
| `skills/numerical-algorithm-design/references/evidence-evolution-and-dependencies.md` | `8fe20778d49d0546a3a9523aaab3ea287dbd50f48ea43af779f30e1b7fc8001d` |
| `skills/numerical-algorithm-design/references/workflow-and-workplans.md` | `7a6261b72934ec7226dd2bc7f22436b07666466e0955fdd6eda05e8c1cc399a1` |
| `memories/MEMORY.md` | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` |

**Parts not read:** D1 and core bodies outside the targeted sections were not freshly reread throughout. Earlier reviews were not recursively reaudited. The anonymous-review, checking, mathematics and Slice 4 annexes, design notes and their critiques, original owner conversations, implementation, generators, datasets, prompts, runtime configuration and executable evidence specifications received no fresh substantive review. Embedded references were not recursively hash-verified. Native issue records were not inspected. Procedural evidence guidance was consulted in part. Memory supplied review discipline only; current authority was verified directly.

**Reviewer continuity:** I am the same reviewer and family as the 6.18 to 6.21 reviews, the 6.4 to 6.8 and 6.12 to 6.17 reviews, the 6.11 cross-check and the three design-note critiques. **This review is not blind.** Prior exposure creates anchoring and common-mode limits. I am outside the author’s Claude family. No subagents were used.

**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`. The numerical-algorithm-design skill was applied.

**Evidence status:** Documentary falsification and read-only arithmetic by Codex as an AI reviewer. Counterexamples below are constructed, not observed UPMS behavior.

## 1. Serious Challenges

### SC-D214-01 — D2: the `a_u` bound excludes known requests and is not conservative for the defined rate

**Earliest owning domain:** D2, §§10.2 and 10.6. **Blocks ratification.**

Section 10.2 defines:

> `a_u` is the mean of `au` over requests with known `k*`.

Section 10.6 instead states:

> the `au` bound counts the episodes whose counted requests all have known `k*`.

For `r > 1`, these are different populations. A known request in an episode containing another request with unknown `k*` remains in §10.2’s denominator but disappears from §10.6’s bound.

The claimed conservatism therefore does not follow:

> Because every episode counts the same `r` requests, an episode-level error rate is at least, and an episode-level success rate at most, the request-level rate of §10.2 over the same counted requests, so bounds on episodes are conservative for those requests.

Equal `r` before exclusion does not preserve equal counting domains after exclusion.

**Counterexample trajectory — constructed recall qualification:**

1. Fix `r = 2` and 10,000 independent episodes before observing responses.
2. In 9,600 episodes, both requests have known `k*`. Of these, 1,344 episodes have `au = 1` on both requests; the remaining episodes have neither request indicated.
3. In 400 episodes, one request has known `k*` and `au = 1`; the other has unknown `k*`.
4. Every response can be a correctly grounded partial answer with `wc = 0`. The unknown requests can remain partial with unresolved maximum reachability. Thus partial usefulness need not rescue or invalidate the discriminator.

The candidate’s acceptance calculations are:

| Quantity | Count | One-sided 95% upper bound |
| --- | ---: | ---: |
| `au`, after excluding mixed episodes | 1,344 / 9,600 | **14.5958%** |
| Episode-level `unk` | 400 / 10,000 | **4.3374%** |

Both pass the placeholder limits `a_max = 15%` and `k_max = 5%`.

But the request-level rate that §10.2 defines is:

```text
known requests = 2 × 9,600 + 400 = 19,600
au requests    = 2 × 1,344 + 400 = 3,088
a_u            = 3,088 / 19,600 = 15.7551%
```

The supposedly conservative upper bound is below even the observed governed request rate.

**Consequence:** The bound can declare the abstention requirement shown while the defined request-level rate exceeds its limit. Reporting both numbers does not repair the acceptance rule.

**Bounded repair:** The simplest repair is to require one preselected counted request per episode per class for qualification. Alternatively, define a cluster method that retains all known requests from mixed episodes and bounds the intended conditional request rate. Do not silently redefine `a_u` to mean only requests in wholly adjudicated episodes. Preserve the separate unknown-reference ceiling.

This challenges the new aggregation method; it does not reopen D1’s answer meanings or the ratified maximum-cardinality reference objective.

### SC-D214-02 — D2: the refusal bound can dilute wrongful refusals with unreachable commands

**Earliest owning domain:** D2, §§10.3 and 10.6. **Blocks ratification.**

Section 10.3 requires:

> refusal rate for commands whose exact target set was reachable within the task budget ≤ `r_max`

That is a rate conditional on reachability.

Section 10.6 includes:

> a refusal of a reachable command

among episode error indicators, but specifies no reachability-conditioned denominator for its bound. The only explicit special denominator there is for `au`.

**Counterexample trajectory — constructed, with the default `r = 1`:**

1. Evaluate 1,000 independent mutating-command episodes.
2. In 100, the exact authorized target set is reachable within budget.
3. The product refuses 10 of those 100 commands.
4. The other 900 commands have no reachable authorized target set and are correctly refused before execution. These need not be runtime budget-limited stops.
5. Count the specified indicator across all 1,000 episodes.

The unconditional upper bound is **1.6903%**, which passes `r_max = 5%`.

The governed conditional refusal rate is **10 / 100 = 10%**. Its corresponding upper bound is **16.3718%**.

**Consequence:** Adding correctly refused unreachable commands improves the reported acceptance bound without improving behavior on reachable commands. This defect survives `r = 1`; fixing SC-D214-01 alone does not close it.

**Bounded repair:** Define the refusal numerator and denominator explicitly over reference-established reachable commands. For clustered requests, preserve that conditional population rather than discarding mixed episodes or treating unreachable requests as successful trials. Specify the disposition of unknown reachability and zero eligible trials: neither establishes a passing refusal rate.

### SC-D214-03 — D2: repeated fresh-set qualification lacks a rule for selection across attempts

**Earliest owning domain:** D2, §10.6. **Blocks an unqualified statistical acceptance claim.**

The fresh-data rule correctly prevents direct reuse of failed qualification data as fresh evidence:

> If it fails and a changed variant or value is tried, the held-out episodes already used become development data and the next qualification uses fresh held-out episodes; every reuse is recorded with the result.

However, the procedure permits repeated attempts and selects a variant when it passes. It supplies no bound on attempts, error allocation across attempts, or sequentially valid stopping rule.

Freshness preserves the validity of each fixed attempt. It does not by itself preserve 95% control for a survivor selected by repeated qualification.

**Counterexample trajectory — exact probability calculation:**

1. Freeze a 1% confident-error limit and 473 episodes per attempt.
2. Consider successive variants whose true episode error probability remains 1.01%; none satisfies the limit.
3. Other requirements can hold. Each attempt uses an independent fresh set.
4. At 473 episodes, zero or one indicated episode passes the candidate’s 1% bound.
5. Stop and qualify the first variant that passes.

For each attempt:

```text
P(pass | p = 0.0101)
  = P[Binomial(473, 0.0101) ≤ 1]
  = 0.0478707310
```

Across 20 independent attempts, the probability of at least one such pass is **62.5098%**; across 100, **99.2594%**.

No held-out episode was reused. Recording all attempts exposes the selection history but does not correct the selected assurance.

The alternative remedy—

> the second is a larger sample

—also needs an explicit rule against inspecting ordinary fixed-sample bounds repeatedly while enlarging the same qualification set.

**Consequence:** The text does not close whether its 95% assurance concerns a prespecified individual attempt or the ultimately selected qualification. Those are materially different claims.

**Bounded repair:** Define the statistical acceptance scope. For assurance over repeated qualification, use a prespecified finite attempt plan with suitable error allocation, another justified sequential procedure, or a final confirmation design whose selection and stopping rules preserve the claimed guarantee. Specify whether enlargement requires a new fixed-size study or uses a sequentially valid method.

If only per-attempt assurance is intended, state that limit explicitly and put the selected-result risk before the owner. Do not present ordinary per-attempt bounds as a 95% guarantee for an unrestricted first-passing survivor.

## 2. Other findings by earliest owning domain

### F-D214-01 — D2: the reported episode totals are error-test floors, not a complete qualification budget

**Status:** Nonblocking planning correction once the acceptance defects are repaired.

Section 10.6 says:

> since an episode may carry one counted request of each class, the decision-basis size sets the number of episodes.

The listed 473 episodes address one pooled confident-error requirement under the stated planning assumption. They do not establish sufficiency for conditional denominators, success requirements, each workload family, or language-specific claims.

**Counterexample trajectory:** Split 473 decision-basis episodes into 237 English and 236 Chinese episodes. One error in the English subset gives an upper bound of approximately **1.9859%**, failing a 1% English-language claim despite the pooled sample-size calculation.

The operative language clause correctly prevents that claim:

> acceptance of a class makes no claim for one language unless that language's own bound meets the limit.

**Consequence:** This does not independently produce a false language pass, but the summary can understate the generation and audit budget required for the intended pilot claims.

**Bounded repair:** Describe the table as marginal error-test minima. Size the actual design from all intended acceptance populations, including conditional denominators and language/workload claims. Success-rate planning must include a margin above the required minimum; observing exactly 60% success, for example, does not yield a lower confidence bound of 60%.

### F-D214-02 — D2 → D4: oracle isolation needs an explicit executable evidence boundary

**Status:** Qualification-specification obligation; no actual leak was demonstrated.

Section 9.1 appropriately requires:

> a random sample of each generator version's episodes

to be audited:

> for wrong, ambiguous or leaked answers

It also correctly retains independent adjudication of parts and `k*`; knowing planted answers does not establish maximum joint reachability.

The remaining specification boundary is where the generator’s answer keys, seeds, manifests and adjudication material may flow.

**Counterexample trajectory — proposed negative test:** A harness retains an answer-key manifest as an ordinary readable episode record. Retrieval, a model prompt, a cache or a reference witness receives that manifest and returns the planted answer directly. Correctness against the key can look good while the intended source-recovery mechanism remains broken.

**Consequence:** Unique seeds and new planted facts do not prevent this channel. A sample audit can discover leakage, but is not a substitute for an explicit oracle-access contract.

**Bounded repair:** The D4 evidence specification should separate product-visible source material from oracle-only keys and adjudication records, bind the permitted inputs of every evaluated component, and include a deliberately leaked-key negative case. Adjudication may use the key; product retrieval and answer production must not gain an unintended shortcut through it.

The generator audit also does not replace core §15.2’s human adjudication obligations. No generator or harness was available for inspection, so actual isolation remains unverified.

## 3. Statistical checks that survived

### 3.1 The table and worked example are numerically correct

I computed the bounds using SciPy 1.15.3, then independently checked all 18 table minima using direct binomial sums at `m` and `m − 1`.

Every published table entry is the smallest qualifying integer:

| Limit | Zero indicated | One indicated | Two indicated |
| --- | ---: | ---: | ---: |
| 1% | 299 | 473 | 628 |
| 2% | 149 | 236 | 313 |
| 3% | 99 | 157 | 208 |
| 5% | 59 | 93 | 124 |
| 10% | 29 | 46 | 61 |
| 15% | 19 | 30 | 40 |

Direct inversion of the binomial lower tail at 473 episodes gives:

| Indicated episodes | Upper bound |
| --- | ---: |
| 0 | 0.6313458% |
| 1 | 0.9989707% |
| 2 | 1.3250032% |

Thus §10.6’s rounded 0.63% and 1.33%, and its two-error point estimate of 0.42%, are correct.

For a fixed binomial experiment, the upper endpoint solves `P_p(X ≤ x) = 0.05`; the zero-error endpoint is `1 − 0.05^(1/m)`. SciPy’s official documentation identifies its exact proportion-interval method as Clopper–Pearson; the numerical minima here were additionally checked without using its beta quantile result as the sole oracle. [SciPy documentation](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats._result_classes.BinomTestResult.proportion_ci.html)

Correct arithmetic does not repair a wrong counting population or a post-selection guarantee.

### 3.2 Any/all aggregation works for common denominators

For equally sized clusters over the same counted requests:

- An episode’s **any-error** indicator dominates its within-episode request error fraction.
- An episode’s **all-success** indicator is bounded above by its within-episode request success fraction.

Under an appropriate fixed sampling model, this supports conservative request-rate testing through episode probabilities.

For `u + u_partial`, the success indicator must mean that **every request satisfies the union** `useful OR useful_partial`. It must not mean “all useful” or “all partial.” Full and partial usefulness are disjoint under §10.2, so their request-level sum is that union rate.

The argument fails when numerator and denominator populations change, as SC-D214-01 and SC-D214-02 demonstrate. The executable plan must also identify the frozen sampling population and mechanism; distinct seeds alone are not a complete sampling specification.

### 3.3 Multiple required rates do not automatically require Bonferroni correction

For one prespecified qualification of one frozen variant, suppose acceptance requires **every** applicable constraint to pass. If any constraint is false, joint acceptance implies falsely passing that particular constraint. A valid level-5% test for each constraint therefore controls this conjunction’s false-acceptance probability at at most 5%, without requiring independence between endpoints.

Accordingly, I do **not** find a missing multiplicity correction merely because the same episodes contribute to several mandatory rates or classes.

That conclusion does not establish simultaneous 95% coverage of every reported interval. Nor does it cover selecting successful classes, languages, variants or qualification attempts and issuing a broader family of claims. SC-D214-03 concerns that separate selection boundary.

## 4. Consistency with ratified parents and owner direction

### 4.1 D1 meanings remain intact

D1 §9 delegates evaluation within these constraints:

> Confident wrong answers cost more than abstentions, and a useful-answer floor and cost limits set by the owner keep abstention from winning by default (D-111, D-120)

D2 1.4 retains those requirements, the shared-budget maximum `k*`, honest unknowns, separate known-error counting and the prohibition on converting limitations into findings.

The new failures concern computational evaluation semantics. Their earliest owner is **D2**. No new D1 semantic revision is required to repair them.

The core and annex continue to require exact command binding, eligible counting domains, grounded answers and honest limitations. Statistical rates cannot override their deterministic checks. D2 §10.6 correctly says one structural failure blocks the variant.

### 4.2 Supplementary qualification does not inherently contradict the 200-episode initial evaluation

Core §15.2 states:

> Initial evaluation: 200 synthetic continuing-project episodes, 100 for development and 100 held out

D2 §10.6 preserves the held-out scenario minimum and adds supplementary episodes where a class needs more evidence.

These provisions can coexist: retain the prescribed initial evaluation, category coverage, baselines, matched budgets and comparative decision rule; add separately identified qualification evidence. Supplementary planted-fact episodes cannot replace the required scenario coverage or comparative study.

### 4.3 Calibration before freezing qualification values is a coherent proposed clarification

Core §15.2 requires:

> Corpus, implementation and configuration, oracle, prompts, models and judges, budget and decision rule are frozen before measuring.

Core §16 requires:

> evaluation frozen before measurement

D-122 expressly records the intended reading:

> both mean before the **qualifying** measurement on held-out data

Development-only calibration followed by freezing the variant, values and qualification procedure preserves that separation. I find no inherent need to change D1 meanings or D3 runtime architecture for this clarification.

However, D-122 §4 says:

> It accepts no text and changes no ratified text.

A successor ratification must therefore explicitly bind the repaired D2 and its compatibility with the retained parents, including their references to D2 1.3. The candidate cannot promote itself through its status or change history.

Core §15.2’s comparative rule also remains:

> the rule is never relaxed after results

A newly authorized study or qualification cannot retroactively turn a failed frozen study into a pass. Any future change of limit needs explicit owner authority and a new evidential claim; recording the change alone does not supply that authority or repair selection effects.

### 4.4 D-121 fits the existing language-profile choice

Core §14.2 already leaves pilot languages to be named at Gate 0. Core §5.9 provides word segmentation for Chinese and language-degradation reporting; T60 covers cross-language and mixed-language retrieval.

Naming English and Chinese therefore requires profile and evidence bindings, not a new D1 meaning or architecture mechanism. The recorded `zh-Hans` assumption should remain visible when binding the pilot. T54 retains its later-slice scope; naming two languages does not move consolidation qualification into the first slice.

Per-language claims remain subject to their own bounds, as §10.6 correctly states.

## 5. Change fidelity, prior findings and coverage

**All 21 change-map replacements applied in order to D2 1.3 reproduce D2 1.4 byte for byte**, with SHA-256:

```text
60374b78500503e7d108b449d798281d8a4a52e941c0fe86e5c060a854ddd1b9
```

**No unmapped edit was found.**

The earlier dispositions remain bounded as follows:

| Earlier item | Assessment for this revision |
| --- | --- |
| SC620-01: unavailable cold-start predictor | The operative cold-start rule is retained; no reopening established |
| SC620-02: individually reachable parts exceeding one shared budget | The largest jointly reachable count remains unchanged |
| SC620-03: unknown reachability erasing known confident errors | `wc` still counts all requests; the new `a_u` clustering defect is distinct |
| F621-01: T148/T167 resource-outcome qualification | Remains open as the ratification record states; this D2 revision does not close it |

The tension search covered the bound request, candidate, change map, owner decisions, ratification, 6.21 review, relevant history/index entries and earlier review headings. Earlier repair judgments were considered through the bound 6.21 record rather than independently re-proved. Native issues and original owner conversations were outside coverage. This is not an omission-free historical audit.

D1 §11 and core §17.2 retain the intended readers, material records, routine questions and marked product inspection surfaces. D2 adds evaluation records—counts, denominators, bounds, calibration choices, variants and reuse—without proposing a new product dashboard. Technical review does not accept surfaces marked beyond the requested deliverable.

No file was edited, created, renamed or deleted by an explicit review operation, and no writing Git command was run. HEAD remained unchanged and all ten hash-bound files still matched. Completion status showed unrelated untracked configuration paths; they were left untouched and their origin was not established.

## 6. Ratification decision and owner questions

**D2 1.4: NO-PASS for ratification.**

SC-D214-01 and SC-D214-02 provide concrete failures of the claimed conservative acceptance method. SC-D214-03 leaves the assurance of a selected qualification materially unspecified.

The revision has useful parts worth preserving: correct sample-size arithmetic, development/qualification separation, episode-level treatment of correlation, retained unknown-reference reporting, synthetic-versus-real-user limits and deterministic structural checks. Repair the existing D2 evaluation owner directly.

D2 1.3 remains accepted-current. This review neither ratifies a successor nor passes Gate 0, authorizes implementation, or qualifies an executable system.

Questions for the owner:

1. **Counting simplicity:** Should qualification require `r = 1` per class per independent episode? This removes the mixed-episode `a_u` defect with the least additional method machinery; refusal still needs its own conditional denominator.
2. **Statistical assurance:** Should the 95% acceptance assurance cover the ultimately selected qualification across retries, or only each individual attempt? The procedure must make that choice explicit.
3. **Qualification scope and resources:** Which class, workload and language claims must the pilot establish? Bind sample and audit budgets to those claims after calibration; 473 pooled episodes alone is not a complete plan.

**Review claim limit:** This review produced documentary ratification evidence, exact reconstruction, direct binomial calculations and constructed counterexamples. It produced no UPMS benchmark, user study or implementation result. No product variants were executed or selected; the retry calculation is analytical. Generator correctness, oracle isolation, actual episode independence, human adjudication and operational sampling remain unverified. The authorized persistence home is this review record, saved verbatim by the invoking process.

