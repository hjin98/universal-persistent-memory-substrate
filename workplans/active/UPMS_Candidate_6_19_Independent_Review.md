# UPMS Candidate 6.19 Independent Review

**Model family / model name:** OpenAI GPT family / Codex, GPT-6-based. The exact serving-model identifier is not exposed in this session.

**Reviewer continuity:** I am the same reviewer and family as the 6.18 review, the 6.4 to 6.8 and 6.12 to 6.17 reviews, the 6.11 cross-check and the three design-note critiques. This review is not blind. Prior exposure creates anchoring and common-mode limits. I did not author these candidates. No subagents were used.

**Date:** 5 November 2026, America/Chicago.

**Repository binding:** Branch `upms-candidate-6-d1-formulation`, HEAD `388a03e0a1f4039fc2fa71e85f2c8d26d21a0393`.

**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`. The scientific-formulation, numerical-algorithm-design and software-design skills were applied.

**Integrity:** The request was read first. Before substantive review, `sha256sum` verified its supplied hash and all 18 file hashes it binds: **19 checks, all matching**. Those checks were repeated near completion; all still matched.

**Input identities:** Paths in the following table are relative to `workplans/active/`.

| File | SHA-256 | Coverage |
| --- | --- | --- |
| `UPMS_Review_Request_Candidate_6_19.md` | `b124840b33cd89b6084f6f9f557b2b3f77642e051b3a1aa4e7daf63d718e3810` | Read first, in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md` | `efb04646f0be364ea955f269dffa38251a1a39eaae7017188e6f050414cc4fde` | Complete predecessor comparison and reconstruction; §16 and targeted retained authority, interpretation, dependency and inspectability provisions |
| `UPMS_Retrieval_Method_D2_Candidate_1_1.md` | `988733885edbe001ba6547cb9f36608a6e928ce9d16c935ecec2b13fb5fb3ebf` | Read in full |
| `UPMS_Architecture_Manual_Review_Candidate_6_19.md` | `c0fc446c4493aab2c2dd6b6f4611e3cd34b991cbcfa36235891ca73921fef3c3` | Complete predecessor comparison and reconstruction; targeted operative contracts |
| `UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md` | `a737a6a64d15d23f310bbd4e41137eacebff03a86c4c8de63ef90f1b3fb9c0bb` | Read in full |
| `UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Read, including acceptance scenarios; unchanged |
| `UPMS_Architecture_Manual_Candidate_6_19_Change_History.md` | `dfbc739bc78192511bec810ff732d9b4c0f70e3101cb40bdd0e51ed4a56cd90d` | Dispositions and owner-question answers inspected; every replacement applied in memory |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18_Change_History.md` | `2575c36361a508bf49c7d123907e20231f650540cbd2a1b7ad8c7fd349ef3ec8` | Read; every replacement applied in memory |
| `UPMS_Retrieval_Method_D2_Candidate_1_1_Change_History.md` | `a4e4482b0b45c75b0f0adf1408183e4760895d007e0647bf051346f0af03922f` | Comparison claims checked; every replacement applied in memory |
| `UPMS_Candidate_6_18_Independent_Review.md` | `9fbe6ed485cf84cae6afa1f4795ddb488660d2bb04b28e636a61c82cd5679108` | Findings, counterexamples, recommendations and owner questions reviewed |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | `28bdee3084167701926da92944804cd06390f926cc3b4fe6d9019b57689d2bc8` | Complete comparison and reconstruction baseline |
| `UPMS_Retrieval_Method_D2_Candidate_1_0.md` | `fba8768d1c0ff6ac7725559054acb455fb2a0ae893e82c7c9c0275b31c736f6f` | Complete comparison and reconstruction baseline |
| `UPMS_Architecture_Manual_Review_Candidate_6_18.md` | `9a42794b35059165ac7e3d83d5a842b4aa33c54bf06f60b003a3aa38b8fd8373` | Complete comparison and reconstruction baseline |
| `UPMS_Architecture_Manual_Review_Candidate_6_18_Annex_Retrieval_Scale.md` | `abfd09691d82cfb635986eae790c57826b581e257dce2cd26ac3e3311ad2de9e` | Complete comparison and reconstruction baseline |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Accepted baseline comparison; targeted retained meanings |
| `UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` | Accepted baseline comparison; targeted retained constraints |
| `UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md` | `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Targeted direction, especially resolution, economy, evaluation, discovery and first-product boundaries |
| `UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` | Read in full |
| `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` | `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Read in full |
| `UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310` | Read in full |
| `UPMS_Candidate_6_17_Independent_Review.md` | `b31cf91f8581cda5929c7dff7ff868a8924c7106e0a0e8d157e23ebbf3835029` | Targeted authority/history and review-coverage inspection |

Additional repository files:

| File | SHA-256 | Coverage |
| --- | --- | --- |
| `AGENTS.md` | `c729fc2a7b38458e6b6c8db09a4a84046d5406129f8a96a89b92da07740ad2c5` | Read in full |
| `history/SEMANTIC_EVOLUTION.md` | `5f0e1346316bd0b71470fa20e91905af199d0fa80015459df89966b1b4b433c1` | Searches and targeted ratification/retrieval entries |

Procedural sources are not UPMS product authority. Skill paths below are relative to `/home/samjin/.codex/skills/`; the memory path is relative to `/home/samjin/.codex/`.

| Procedural source | SHA-256 |
| --- | --- |
| `scientific-formulation/SKILL.md` | `111a13625cf40a70aa95cf0c3968ca8efa533bfab55ec94a772d5790b2a81b5c` |
| `numerical-algorithm-design/SKILL.md` | `4de404bb9c1e24e82e0d26806b35a01b43b933e63294a54492769d6b6ec2826d` |
| `software-design/SKILL.md` | `d5f0d045ee6af2db72dfd1cd5da86362b48512cc6e6bc4d293ad363747ee2364` |
| `scientific-formulation/references/scientific-formulation.md` | `246cef460328c85c6d9ca4c0d2d45586486b70ecbf76308c7b7318f7df706f99` |
| `numerical-algorithm-design/references/numerical-algorithm-design.md` | `f41f73eb5d3acb09ce7138e3f18ca5cb9c26e90a651f13548b8eee3fa7ecf267` |
| `software-design/references/architecture-and-design.md` | `06a7f931935ae84f11d3fd9ec52124333489d5c162fe1de6996535cee839cfd6` |
| `software-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` |
| `memories/MEMORY.md` | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` |

**Parts not read:** The unchanged D1 and core bodies were not freshly reread throughout. Core inspection concentrated on authority, incorporation, eligibility, response and context contracts, resource/profile limits, deletion/recovery, invariants, delivery and inspectability. Historical candidates and reviews were not recursively rereviewed. The three design-note critiques, checking, mathematics and Slice 4 annexes, original owner conversations, SCIRE/SSDS source authorities, implementation, deployment configuration and external technical references received no fresh substantive review. Embedded references were not recursively hash-verified. Filename discovery across `workplans/active/` was broader than substantive reading. Native GitHub issues were not inspected; no connected issue tool was available.

**Evidence status:** Documentary falsification by Codex as an AI reviewer. Counterexamples below are constructed trajectories, not executed system results. No file was created, edited, renamed or deleted, and no writing Git command was run. The designated persistence route is the user's verbatim saving of this response.

## 1. Closure of the 6.18 review

“Closed” below means closed in the proposed design text within this review's scope. It does not mean implemented, measured, ratified or qualified.

| Earlier item | Status | Operative-text assessment |
| --- | --- | --- |
| **SC618-01 — unconfirmed resolutions as bases after adoption** | **Closed** | D1 F-51 item 2 restores the strict prohibition. R7.4, RT8 and T152 preserve it. Adoption remains the adopter's own claim and does not confirm the source resolution. |
| **SC618-02 — omitted pruning work and incomplete cost model** | **Partly closed** | D2 §7.1 now includes routing, delta, eligibility, checking and counting; tokens are separate. §7.2 supplies an empirical interval and fallback. The zero-engine-work counterexample is repaired. The comparison between these quantities and the budgets remains undefined in material respects: **SC619-01**. |
| **SC618-03 — unbounded missing-declaration exception** | **Closed** | R7.2 refuses deliberate agent record writes without declarations, preserves defective capture, and records each missing captured declaration as an integration defect. R15 and T150 add a qualification ceiling. The 1% value remains an initial default requiring the profile's acceptance, not an independently established reliability result. |
| **F618-01 — lexical representation target** | **Closed at the normative boundary** | D1 Definitions 16.1–16.2 identify original text versus a named rendering revision. R3, R4, R7.3 and T163 preserve the distinction and both citations. Exact matching of rendering text no longer purports to establish an original-text match. |
| **F618-02 — predecessor/tension metadata** | **Partly closed; residual is nonblocking** | §13 now names the accepted predecessor and gives a proposed applicability assessment. The contradictory sentence in §0.1 remains: **F619-01**. The actual accepted-current identities are nevertheless explicit and externally hash-bound. |
| **F618-03 — selection on held-out queries** | **Closed** | D2 §5.3 now selects on development queries, freezes the variant before final held-out testing, and records variants and test reuse. |
| **F618-04 — plan-relative abstention and incomplete classes** | **Partly closed** | D2 §10 covers every class and explicitly judges the request rather than its chosen plan. The new reference procedure and partial-answer classification still admit materially different acceptance outcomes: **SC619-02**. |
| **F618-05 — scale ladder and lifecycle workload** | **Closed as a design proposal** | D2 §10.3 makes larger steps conditional. §§11 and 13 add lifecycle, maintenance-concurrency and aggregate-headroom assumptions. Their feasibility remains unmeasured. T168 needs a stronger qualification discriminator: **F619-02**. |
| **F618-06 — pilot/class caps and count status** | **Closed for precedence and counting** | D2 §7.3 and R9/R15 expressly take the smaller applicable cap and require a new deep-retrieval plan for widening. D1 Definition 16.5, D2 §6 and R4 qualify counts. Cost-unit closure is separately challenged in SC619-01. |
| **F618-07 — delivery ownership** | **Closed** | R17 assigns author renderings to Slice 1a-core. R3 defines an early schema/vocabulary subset and deterministic resolution boundary. Full vocabulary and processor resolution remain later work. |
| **F618-08 — capture extent lost in replacement coverage** | **Closed** | D1 Definition 16.5 and R4 expressly retain capture extent and known gaps. T164 tests complete retained-population execution alongside incomplete capture. |

The additional recommendations also received substantive attention:

- T144–T147 now distinguish publication, delta visibility, merge completion, version mismatch and more Boolean cases.
- D2 §8 item 3 distinguishes model identities and records shared inputs. It does not turn agreement into a probability or speaker confirmation.
- D2 §6 makes the retained ordering the baseline, makes reciprocal rank fusion contingent on development evidence, and groups correlated expansions.
- Map T accurately reconstructs this revision. That does not retrospectively correct every wording claim in frozen map S.
- The earlier storage, recovery, multilingual, hidden-result and consumer-availability qualification limits remain applicable. Added scenarios are specifications of evidence to obtain, not that evidence.

## 2. Serious Challenges

### SC619-01 — D2: work, time and token caps still lack a complete comparison rule

**Earliest owning domain:** D2. **Blocking for D2 and its proposed D3 consumer.**

D2 §7.1 correctly separates quantities:

> Work and tokens are estimated separately; they are different quantities with no fixed conversion.

It then states:

> Elapsed time is measured, not derived from `W`.

However, §7.2 item 4 directs:

> If the estimate exceeds the budget, the planner narrows the plan with the asker

The class-cap column in §7.3 is denominated in seconds—such as `0.2 s`, `1 s` and `2 s`—while §10.2 requires:

> its mean and 95th-percentile work and tokens stay within the class's effective cap (§7.3).

The revised method does not finish defining this comparison. It does not bind `W` to a particular unit or distinguish, for admission, work-seconds from elapsed seconds. Section 2 still gives the old `cost(π)` the combined unit entry “normalized work units, seconds, tokens”. The new `W` and `T` do not receive a complete replacement quantity contract.

There is a second distinction within tokens: `T(π)` is compilation, resolution and assessment expenditure, while §7.3's returned-context column constrains text returned to the consumer. Those are different costs. A returned-context allowance is not an internal inference-token allowance.

**Counterexample trajectory — constructed:**

1. A deployment measures the operation coefficients and computes a plan's `W` in normalized work units.
2. The request has the recall class's one-second engine cap and 4,000-token returned-context allowance.
3. The engine estimate is 10,000 work units; compilation and checks require an estimated 12,000 model tokens; the returned page needs 500 tokens.
4. One implementation converts work to predicted engine time using a deployment-specific throughput model and admits the plan. Another compares a different normalization or time quantity and refuses it.
5. For tokens, one implementation compares internal `T` with the returned-context allowance and refuses; another treats that allowance correctly as output context and admits under a separate task allowance.
6. The text supplies neither the common conversion nor the class-level internal-token binding needed to determine which admission and acceptance decisions conform.

Defining coefficients in CPU-seconds could be a valid repair. Defining an empirical elapsed-time predictor could also be valid. The candidate must choose or explicitly parameterize the meaning; measurement of coefficients alone does not identify it.

**Consequence:** The omission repaired in SC618-02 is real progress, but the central “estimate before execution, compare with budget” operation remains underdetermined. A hard runtime stop limits damage after admission; it does not define the promised admission decision or the acceptance test.

**Bounded repair:**

- Give `W` and every coefficient a coherent unit.
- Specify which time or work quantity each engine cap limits.
- If admission uses predicted elapsed time, define that prediction and its empirical uncertainty separately from measured elapsed time.
- Bind internal model-token/call expenditure separately from returned-context size, using explicit class and task limits.
- Replace §10.2's comparison with the applicable componentwise requirements.
- State the cold-start behavior when no empirical ratio interval exists yet.

This requires a small quantity-and-budget contract, not another planner service or a benchmark campaign before the text can be repaired.

### SC619-02 — D2: the repaired answerability and partial-answer rules do not yet determine evaluation

**Earliest owning domain:** D2. **Blocking evaluation-method ambiguity.**

D2 §10.1 begins with the correct principle:

> **Answerability is judged against the request, not the plan.**

Its proposed reference procedure nevertheless says:

> an adjudicator, using an exhaustive search of the eligible corpus within the request's budget class and the request's own wording, records whether an answer was reachable.

An exhaustive reference search and an efficient answer-producing search need not fit the same budget.

**Counterexample trajectory A — constructed:**

1. A request names an exact identifier.
2. An eligible record contains the complete answer. E0 can retrieve it within the request's cap.
3. Exhaustively scanning the eligible corpus exceeds that cap.
4. The tested system produces a bad plan and abstains.
5. If the adjudicator must also complete its exhaustive search inside that cap, its failure cannot establish that no answer was reachable. Treating that failure as a negative reference answer reproduces the original abstention loophole through the oracle.

If the intended meaning is that adjudication may spend more offline effort while judging whether a conforming answer was reachable within the product budget, that distinction needs to be stated. If the exhaustive procedure cannot decide, the reference result is unknown, not “no reachable answer”.

The new mixed-outcome rules have another material ambiguity. Section 10.1 defines:

> **useful partial**: correct and grounded for part of the request, with the unresolved remainder stated;

and:

> **unjustified abstention**: abstains, or answers only partially, where the adjudicator found a reachable answer, whatever the reason the system gave.

Section 10.2 then uses both `u_partial` and `a_u`, including:

```text
u + u_partial ≥ u_min
a_u ≤ a_max
```

and:

```text
U = u + ½ u_partial − λ · e_wc − ν · a_u
```

The text does not state whether these are exclusive outcome buckets, overlapping indicators, or categories resolved by precedence.

**Counterexample trajectory B — constructed:**

1. Evaluate 100 two-part recall requests whose complete answers are reachable within budget.
2. For every request, the system answers the first part correctly and with citations, and explicitly leaves the second part unresolved.
3. Every response satisfies the wording of both “useful partial” and “unjustified abstention”.
4. A bucket-based evaluator assigning “useful partial” can report `u_partial = 100%` and `a_u = 0%`.
5. An evaluator applying the unjustified-abstention condition as an additional indicator reports `a_u = 100%`.
6. The former can satisfy the proposed recall usefulness and abstention requirements; the latter fails them.

The second treatment may be exactly what the author intends. It is not enough to leave that choice implicit when the choice changes acceptance.

**Consequence:** The revision removes the explicit plan-relative definition and fills the class table, but it does not yet provide a reproducible adjudication rule. The same request and response can acquire different acceptance dispositions without changing the product.

**Bounded repair:**

- Separate the reference adjudication budget from the product's answer-production budget.
- Require a justified determination of reachability; preserve an unknown/adjudication-incomplete state where needed.
- Define outcome indicators or exclusive categories explicitly, including overlap, precedence and denominators.
- State whether a useful partial answer also incurs unjustified-abstention cost when a full answer was reachable.
- Include a fixed two-part-request example showing all resulting indicators and its acceptance disposition.

The owner still sets the numerical thresholds. These repairs define what the thresholds measure.

## 3. Other findings by earliest owning domain

### F619-01 — D1: §0.1 still denies the existence of accepted D1 authority

**Status:** Residual documentary defect from F618-02. **Nonblocking for Gate 0 entry.**

D1 §13 is substantially repaired, but §0.1 still says exactly:

> No accepted D1 authority exists for UPMS.

This conflicts with the opening status, the accepted-current input row, §13 and the ratification record.

**Counterexample trajectory — constructed:** A reader extracts the §0.1 authority summary for a downstream handoff and reports that no accepted D1 predecessor exists, despite the explicit ratification of 1.16.

**Consequence:** The authority inventory remains internally inconsistent. I do not treat this isolated stale sentence as defeating the revised interpretation rules: the exact accepted-current identity and the proposed applicability assessment are now recoverable without inference.

**Bounded repair:** Remove the sentence or label it as historical context for the original formulation, in a separately bound successor. Also distinguish 1.17 as the immediate candidate predecessor from 1.16 as the accepted predecessor; both currently receive “Immediate predecessor” wording in the input table.

### F619-02 — D3: T168 does not distinguish aggregate purge qualification from honest failure reporting

**Status:** Evidence-specification defect to close before purge qualification. **Not an independent Gate 0 entry blocker.**

R11 appropriately requires aggregate sizing and honest failure reporting. T168, however, accepts this alternative:

> either meets the live-surface target for every deletion, with ingestion throttled first, or reports `purge_failed` for those missed

D2 §13's proposed purge envelope is stronger:

> every deletion reaches `purged_live` within the 24 h live-surface target

**Counterexample trajectory — constructed:**

1. Bind an in-envelope lifecycle workload and maintenance concurrency.
2. Run the aggregate deletion scenario.
3. Every deletion misses 24 hours.
4. Every miss is accurately reported as `purge_failed`, and the barrier remains effective.
5. T168's stated alternative is satisfied, although the bound throughput envelope has failed.

**Consequence:** The scenario tests honest degraded behavior but cannot, by itself, qualify the aggregate purge target. Honest failure remains a necessary property; it is not evidence of sufficient capacity.

**Bounded repair:** Give the existing scenario two explicit dispositions: an in-envelope qualification case must meet the target, while an overload or injected-failure case must preserve barriers and report failure correctly. Bind the pilot lifecycle workload separately; §13 explicitly makes its larger-profile values proposals until that profile is bound.

R18 already leaves purge feasibility and owner-bound workload evidence open. This finding sharpens that existing obligation rather than demanding a TB experiment now.

## 4. Fidelity, authority and regression assessment

### 4.1 No unmapped edit was found

I applied every change-map replacement to its exact predecessor in memory:

| Comparison | Replacements | Result |
| --- | ---: | --- |
| D1 1.17 → 1.18, map T | 14 | Byte-identical to supplied 1.18 |
| D2 1.0 → 1.1 | 21 | Byte-identical to supplied 1.1 |
| Core 6.18 → 6.19, A.29 core edits | 17 | Byte-identical to supplied 6.19 |
| Retrieval annex 6.18 → 6.19, A.29 annex edits | 31 | Byte-identical to supplied annex |

Thus the claim that the change maps cover the revisions survives. The core changes include mapped status, review and history prose as well as version references; no additional operative-rule mutation was found.

The comparison with ratified D1 1.16 and core 6.17 found no newly introduced reversal of their retained theory–evidence, eligibility, commit, deletion or pilot-cap contracts within the inspected scope. This is a bounded incremental finding, not a fresh exhaustive certification of every retained clause.

### 4.2 The answers to the three owner questions are within the existing direction

| Earlier question | Assessment |
| --- | --- |
| Resolution bases | Restoring the reviewed strict rule needs no new policy decision. D1 F-51 and R7.4 do so without turning adoption into confirmation. |
| Declarations | Separating evidence-preserving capture from conforming deliberate writes is a reasonable concretization of D-107. Every missing capture remains a defect. The proposed qualification tolerance is an engineering default requiring profile acceptance, not a claim that D-107 authorized omission. |
| Budgets | Taking the smaller cap and requiring the existing capability and a new plan for deep retrieval preserves D-120 and core §§10.4/14.2. Class selection alone no longer widens the pilot. |

The fourth question remains properly with the owner: set the evaluation requirements and workload/profile values before measurement. I do not select those values in this review.

### 4.3 Retain the repaired architecture and its explicit limits

The following remain sound design directions within this documentary review:

- canonical custody separated from rebuildable serving structures;
- exact lexical/structural facts separated from semantic assessments;
- similarity proposals separated from exact matches and never used for absence;
- conservative pruning under covering, versioned summaries;
- explicit capture, execution, processing, availability and support limitations;
- rendering matches bound to their own representation;
- current consumer availability required for reference-only reuse;
- independent deletion units, reserved purge work and qualified recovery stages;
- pilot qualification separated from larger-profile claims.

The conditional proof in D2 §3.3 remains sound under its covering and publication premises. Neither the proof nor map reconstruction establishes that an implementation maintains those premises.

D2 §7.2 item 3 also needs careful qualification at the security boundary. Segment counts are not inherently independent of hidden content; their counting domain must satisfy R5. The statement that full-statistics use affects “timing and admission” must be tested against the retained timing/resource residual and the prohibition on exposing hidden-dependent counts or explanations. T167 checks the displayed estimate, but does not alone cover all admission, continuation and explanation behavior. I have not established an implementation disclosure from this text review.

### 4.4 Tension and inspectability coverage

I searched `workplans/active/` and semantic history for the accepted 1.16/6.17 identities, D-101 and the 6.18 finding identifiers, then inspected the bound decisions, predecessor review, revision dispositions and relevant history.

The material recorded items are:

- **D-101 adequacy challenge:** attributed in the records to Claude on the owner's expanded requirement, bound to core 6.17's concretization. The D-117–D-120 record narrows the earlier description: it is inadequacy for the larger requirement, not a demonstrated defect of the ratified pilot. D1 §13 now assesses it as applicable, explicitly proposed until acceptance.
- **SC618-01–03 and F618-01–08:** Codex's documentary findings against 1.17/1.0/6.18. A.29's dispositions are Claude's repair claims; this review's closure table supplies the current technical assessment.

Native issue coverage is unavailable, so this is not an omission-free tension search. It supplies no authority to close historical records in their homes.

D1 §11 and core §17.2 retain the required realized-record, reader, routine-question and inspectability distinctions. D1 explicitly marks plan, coverage and support-state surfaces within the owner-requested deliverable under D-104/D-110. Technical review does not accept the separately marked beyond-deliverable surfaces on the owner's behalf.

## 5. Simplicity

The repairs largely modify existing owners directly. They do not add a confidence service, another semantic registry or a second pruning hierarchy. The first-product use of the positional index's own dictionaries remains appropriate pending measurement.

Keep the remaining repairs equally local:

- define the cost quantities and their budget comparisons;
- define reference answerability and mixed outcomes;
- remove the stale authority sentence;
- distinguish purge-capacity qualification from safe failure.

The proposed extractions, model checks, queue window and lifecycle defaults create real cost obligations. They remain proposals to bind and measure, not reasons to add more scheduling machinery before evidence shows a need.

## 6. Gate 0 entry decisions

| Subject | Verdict | Basis |
| --- | --- | --- |
| **D1 formulation 1.18** | **PASS for Gate 0 entry** | SC618-01 and the lexical-representation defect are resolved at their semantic owner. Capture/count meaning is explicit. F619-01 is a bounded documentary correction, not an unresolved substantive D1 rule. |
| **D2 retrieval method 1.1** | **NO-PASS** | SC619-01 leaves admission/acceptance quantities underdefined; SC619-02 leaves answerability and mixed-outcome evaluation materially ambiguous. |
| **Core 6.19 with retrieval-and-scale annex and anonymous-review annex 6.7** | **NO-PASS** | Its new retrieval contract consumes the challenged D2 cost and evaluation method. Declaration enforcement, coverage migration, cap precedence and early delivery ownership are repaired; they do not close the parent-method blockers. |

The D1 PASS is a technical entry decision within the stated reading scope. It does not ratify 1.18 or pass Gate 0. D1 1.16, core 6.17 and anonymous-review annex 6.7 remain accepted-current at their ratification hashes.

The D-101 expanded-scale challenge is not closed by this package. Its architectural response is credible, but the method contract still needs the two bounded repairs above. No pilot, larger-profile, KMS, runtime, capture-path, purge or recovery qualification was performed.

## 7. Questions and required next decisions

1. **Before measurement:** The owner must set the complete class requirements and bind the workload/profile, including internal model expenditure, lifecycle load and maintenance assumptions. D2 §§10.2/13 remain proposals.
2. **Partial answers:** After D2 explicitly defines the overlapping indicators or exclusive categories, the owner should set the intended tradeoff and thresholds. This review does not choose whether half-credit or another weight is appropriate.
3. **No renewed policy question is needed** for strict resolution bases, deliberate-write declarations or pilot-cap precedence; the current repairs fit the existing decisions.

SC619-01 and SC619-02 can be repaired within the existing direction. They require clarified method text and a separately bound revision, followed by review. Frozen inputs should remain unchanged.

**Review claim limit:** This work produced documentary gate evidence and concrete counterexamples. It produced no benchmark, scientific-result dataset, user study or implementation acceptance result; no product variants were executed or selected. The intended persistence home is this review record, saved verbatim by the user.

