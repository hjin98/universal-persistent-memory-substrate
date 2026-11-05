# UPMS Candidate 6.14 Independent Review

**Model family / model name:** OpenAI GPT family / Codex, GPT-6-based. The exact serving-model identifier is not exposed in this session. I am **the same reviewer and family as the 6.4 to 6.8, 6.12 and 6.13 reviews and the 6.11 cross-check**. This review is not blind. I did not author these revisions. No subagents were used.

**Date:** 5 November 2026, America/Chicago.

**Repository binding:** Branch `upms-candidate-6-d1-formulation`, HEAD `7a81d8f30fbd431fc8a3387fc647f7e7b0d18394`.

**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`. Scientific-formulation and software-design skills were applied.

**Integrity verification:** The request and `AGENTS.md` were read first. Before substantive review, `sha256sum` verified the request’s supplied hash and every file directly bound by it: 27 checks, including the four excluded documents. All matched. Final verification repeated those checks; all matched.

**Input identities and reading coverage:** Paths below are relative to `workplans/active/`, except `AGENTS.md`. Hash verification alone is not substantive review.

| File | SHA-256 | Coverage |
| --- | --- | --- |
| `UPMS_Review_Request_Candidate_6_14.md` | `a9832a0f08c275383d4eea04b7da61d72b23834b176d6ccfebd55ed4ae59d02d` | Read first, in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_14.md` | `c163a0999e1cff6c851dff5b1200e21677807ffd209947ce65011738a1554dcb` | Read throughout; targeted passages reread |
| `UPMS_Architecture_Manual_Review_Candidate_6_14.md` | `84df965086a16d1f6649c4e963dd072c06fd37ab8e74f5a28461c1a83e668175` | Read across every section and the acceptance inventory; focused rereading of the witness consumers and derivation contracts |
| `UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Read in full |
| `UPMS_Candidate_6_13_Independent_Review.md` | `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b` | Findings, trajectories, ledgers, owner questions and limits read |
| `UPMS_Owner_Decisions_6_13_Review_2026-11-05.md` | `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343` | Read in full, including the quoted recommendation and four completions |
| `UPMS_Architecture_Manual_Candidate_6_14_Change_History.md` | `1667b4096541396110e4d55b9f853aa557b2cdc512d6bbc1a4043b72b6a3f97f` | Repair claims and moved operative passages read |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_14_Change_History.md` | `8530e5109d5ba4ac54840f08f5526ca4ce74d346698d91a2aea1b89adcf25aea` | Map P and moved substantive passages read; not every historical metadata row independently audited |
| `UPMS_Architecture_Manual_Review_Candidate_6_13.md` | `d2e59a70e3b7e746a5244cef4d97fd128019c5c039dc1c7ea390f2c22be324ca` | Selected predecessor differences; not reread in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_13.md` | `58276d56f5a474401b008a4d8d87420651ead909348cc7aba8fd5724c1b21536` | Selected predecessor differences; not reread in full |
| `UPMS_Candidate_6_12_Independent_Review.md` | `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26` | Original Serious Challenges and other finding; remaining dispositions also consulted through the 6.13 ledger |
| `UPMS_Owner_Decisions_6_11_Review_2026-11-05.md` | `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295` | Read in full |
| `UPMS_Owner_Decisions_6_8_Review_2026-11-05.md` | `5e9b40d43746059cbd4f23ff671bab735af7eccec5b940d3a36890f24cec33e9` | Read in full |
| `UPMS_Candidate_6_8_Independent_Review.md` | `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad` | Heading inventory and selected warrant, decision and ledger references |
| `UPMS_Owner_Decisions_6_5_Review_2026-11-05.md` | `8cc6ffc8e9bf89119a92b0500ac4be3fee9775e0d818821bfb30985ee0aa59fa` | Read in full |
| `UPMS_Owner_Decisions_6_4_Review_2026-11-04.md` | `20144a3a92753313d1163378c3bdf338509a0910962bdb44fd38f458104c9671` | Read in full |
| `UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Read in full |
| `UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Read in full |
| `UPMS_Owner_Decisions_Math_2026-11-03.md` | `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | Read in full |
| `UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Read in full |
| `UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Selected warrant, standing and dependency passages |
| `UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Hash only |
| `UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Hash only |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` | Hash only; excluded |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` | `f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7` | Hash only; excluded |
| `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md` | `71083419f4b9d4091153d7fd86ec32046081eca1f295d9f31e0b867015f51a58` | Hash only; excluded |
| `UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md` | `d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e` | Hash only; excluded |
| `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md` | `0fc9822778e3851fb7fec9593e1bfe150064e09a84982a02fe51aa4310ecd733` | Additional input: moved D-47–D-56 decision table |
| Repository-root `AGENTS.md` | `081ae30487a937ff8b6f45d4bf75cb3f7e5fa289387a8298b8a59253ae7559de` | Read in full |

**Parts not read:** Hash-only documents were not substantively reviewed. Earlier candidates, reviews and change histories were not reconstructed beyond the stated coverage. Original owner conversations, external issue systems, SCIRE and SSDS source authorities, implementation, runtime sources and deployment configuration were not read. No verdict is supplied for the excluded packages. Method inputs are listed in Appendix A.

**Status:** Documentary falsification evidence asserted by Codex as an AI reviewer. This record grants no ratification, implementation authority, runtime qualification or acceptance of additional product scope.

## 1. Serious Challenges

### SC614-01 — The witness condition rule prevents a discharged hypothesis from disappearing across a multi-step proof

**Earliest owner:** D1 Definition 2.7 and §6.1, particularly “Premises,” “valid for” and Definition 6.2. Downstream: core §5.5’s derivation hook, §9.9, TE-07 and T98. This challenges the first author completion within D-100.

**Blocking formulation conflict; high confidence in the literal classification.**

D1 Definition 2.7 explicitly permits discharge:

> A hypothesis is discharged **for a conclusion** only when every path in the derivation from a step that uses it to that conclusion passes through a step that discharges it (owner decision D-72); it is then not a premise of that conclusion (D-70).

But §6.1 defines an inference step `R'` as valid for its consumer `R` only when:

> each of its conditions, stated (Definition 2.7) or carried, is compatible with `R`'s conditions by the compatibility rule above.

It then states:

> Because each step of a chain must meet the conditions of the step it supports, a condition carried anywhere in a chain must be covered at the route's own step (D-100).

Definition 6.2 requires:

> a root witness of each premise of `R'` for `R'` avoiding `X`

These clauses provide no discharge-aware context for the recursive premise check. They require a condition of an intermediate conclusion to remain compatible with the later step even where that later step validly discharges it.

**Counterexample trajectory.** The construction below is a paraphrase using ordinary implication introduction.

1. Introduce local hypothesis `h: A` in an acyclic derivation.
2. Record step `U`, deriving `B = A ∨ Q` from `h`. `U` carries `h`; after carried conditions are set aside, it has no premises left to establish.
3. Record step `D`, deriving `K = A ⇒ (A ∨ Q)` from intermediate conclusion `B`, discharging `h` by implication introduction.
4. Every path from the use of `h` to `K` passes through `D`. There is no bypass branch. Under Definition 2.7, `h` is discharged for `K`.
5. Give `U` and `D` effective positive inference assessments, with no negative assessments. Record an effective judgment of `B` as `supported-under(h)`, citing `U`, and an effective judgment of `K` as `supported`, citing `D`.
6. Record an unconditional valid step `T: K → L`, for example `L = K ∧ K`, with an effective positive assessment.
7. All revisions, rulesets and access guards hold. No objection, negative assessment, pending obligation or additional supporting basis exists.

The intended result is an unconditional valid argument for `K`, reusable by `T`. The hypothesis remains visible as introduced and discharged; it is not a condition of `K` or `L`.

The operative witness rule does not produce that result:

- To root `K` for `T`, its judgment must use `D`.
- The witness must then root `B` **for `D`**.
- `B`’s `supported-under(h)` judgment is ineligible if `D`’s conditions no longer contain `h`: identity compatibility fails, and no comparability judgment establishes that assumption `h` covers an unconditional use.
- Independently, `U` carries `h`, so `U` is not valid for an unconditional `D` under the new all-step compatibility clause.

Consequently `K` has no root witness for `T`. `T` shows “premises not established,” and `has-sound-support(L)` is false despite the stipulated valid proof and correctly discharged hypothesis.

**Keeping `h` among `D`’s stated conditions does not solve the composition problem.** It may permit the inner check, but `D` then fails “valid for `T`,” because that definition checks stated conditions as well as carried conditions. The unconditional consumer still cannot use the discharged result.

Nor does changing `B`’s claim judgment to unconditional `supported` repair the structural rule: `U` still carries `h`, and its compatibility with the discharging consumer is still required.

**Consequence.** The rule preserves open assumptions by propagating them, but lacks the corresponding operation that lets an authorized, path-scoped discharge remove one. A simple effective-empty-premise discharged step can pass; a proof containing an intermediate conditional conclusion can fail. This conflicts with D-70/D-72 and core T98’s requirement:

> a derivation that discharges its hypothesis is sound when its steps and undischarged premises are

Re-recording the whole proof as a new premise-free macro-step, or citing its textual event as a terminal basis, could supply a different root. Neither repairs the classification of the admitted multi-step derivation.

**D-100 boundary.** The recommendation shown to the owner expressly said:

> This keeps D-70 and D-71.

The first completion is therefore not harmless technical completion in its present universal form. Propagating conditions across ordinary support edges is consistent with the recommendation. Propagating them across a valid discharge without a discharge-aware rule is not shown to preserve the promised contract.

**Bounded repair.**

- Make witness eligibility account for the existing path-scoped discharge semantics. Distinguish a hypothesis needed inside a subderivation from a condition still required by its conclusion.
- Preserve the positive-assessment and no-negative-assessment requirements for every traversed inference step.
- Preserve D-72: a bypass path must keep the hypothesis as a condition.
- Add the multi-step implication-introduction trajectory above, its unconditional downstream consumer, an undisclosed/open-hypothesis contrast and a bypass-branch contrast.
- Reconcile Definition 6.2, “valid for,” the all-step condition sentence, core §9.9 and T98 together.

This needs a D1 correction and owner adjudication of the first completion, not a D4 exception or a new stored status.

## 2. Verdicts and retained strengths

| Subject | Gate 0 entry technical verdict | Reason |
| --- | --- | --- |
| D1 formulation 1.14 | **NO-PASS** | SC614-01 prevents compositional use of a valid multi-step argument with a discharged hypothesis |
| Core 6.14 with anonymous-review annex 6.7 | **NO-PASS** | Core §9.9 consumes the challenged definition, while §5.5 and T98 retain discharge semantics |
| Checking, Slice 4 and mathematics packages | **No verdict** | Excluded or separately reviewed |
| Earlier candidates and proposal | **Historical verdicts unchanged** | No retroactive acceptance |

The original empty-premise defect is repaired under the owner’s explicitly changed contract. An unassessed premise-free step roots nothing. An assessed valid premise-free step can supply a valid-argument root, with the specified label. Immediate self-dependence is now recognized, and case 41 no longer excludes independent reasons for a route to be broken.

Retain those repairs.

Also retain finite witnesses, eligibility checks at every depth, the distinction between rootlessness and circularity, the nonempty all-negative guard, attributed assessments, derived standing, deterministic mandatory lists, fixed objection homes, exact signatures and explicit access, deletion and restore limits. SC614-01 does not justify replacing these mechanisms.

## 3. Other findings by earliest owning domain

### R614-01 — Case 36 and T135 omit the intermediate validity assessment their outcome now requires

**Earliest owner:** D1 §10.3 case 36, reflecting §6.1. Downstream: core T135.

**Non-blocking scenario correction when read through the operative predicate.**

Case 36 says:

> A premise supported through a step whose own premise is grounded in an event and is also supported through a step from the conclusion: it does not depend on the conclusion, so the step is not circular (§6.1; D-99).

T135 repeats the corresponding outcome:

> a premise whose support passes through a step with an event-grounded premise does not depend on the conclusion even when that premise is also supported from the conclusion

D-100 now makes the intermediate step’s effective validity assessment essential.

**Counterexample trajectory.**

```text
S: P → K             effective positive inference assessment
U: Q → P             no inference assessment
V: K → Q

J_P: supported, citing U
J_Q: supported, citing an applicable event and V
```

All judgments and conditions otherwise qualify.

`Q` has an event root. But `U` is valid for no step because nobody has assessed it. Therefore `P` is not rooted for `S`. Reaching follows cited steps whether assessed or not, so `P` reaches `K` through `U` and `V`. `S` is circular and broken.

Adding an effective positive inference assessment of `U`, with none negative, supplies the intended event-rooted alternative and makes `S` non-circular.

**Consequence.** The old scenario’s stated record shape no longer determines its claimed outcome. An evidence specification could use the wrong expected result or silently add an unstated assessment.

**Bounded repair.** State the qualifying intermediate inference assessments explicitly in case 36 and T135. Add the unassessed and negative-assessment contrasts. Audit the other inherited soundness examples for the same newly material precondition, including terminal evidence relations’ no-effective-negative requirement.

No new owner policy is needed.

No separate D2 defect or independent D3 blocker was established.

## 4. Repair dispositions and boundary checks

“Repaired” below means that the operative text defeats the identified documentary trajectory. It does not mean executed product qualification or closure of every sibling defect.

### 4.1 Each finding of the 6.13 review

| Finding or requested boundary | Disposition against 1.14 / 6.14 |
| --- | --- |
| **SC613-01: unassessed empty-premise step** | **Repaired.** “Valid for” requires an effective positive inference assessment and no effective negative one. The original unassessed step supplies no witness |
| **SC613-01 converse-cycle sibling** | **Repaired.** The unassessed alternative clears nothing; reaching still discovers the converse dependence |
| **Assessed premise-free argument** | **Explicitly authorized by D-100.** It is a valid-argument root, not an event root; the label and conditions must travel |
| **Effective-empty-premise boundary under D-70/D-71** | **Simple cases work; general discharge remains challenged.** A valid step with only carried conditions, or no premises remaining after discharge, can terminate a witness. SC614-01 defeats composition through intermediate conditional conclusions |
| **R613-01: immediate self-dependence** | **Repaired.** Reaching now includes `Y` being `κ`; K → K is circular even when K’s judgment cites an event |
| **R613-02: case 41** | **Repaired.** The sentence now says absence of effective assessments alone does not make the route broken, preserving the other branches |
| **Review §4.5: invalid intermediate inference step** | **Repaired for that trajectory.** An effective negative inference assessment, including a disputed step, excludes the step from a witness |
| **Review §4.4: traversal order** | **Addressed in the operative architecture.** Core §9.9 distinguishes ongoing cyclic exploration from a completed negative result; T139 specifies the discriminator. No implementation was tested |

D-100 changes the governing root contract. The assessed premise-free result must therefore be judged under the revised F-25, rather than treated as a recurrence merely because it has no event.

### 4.2 The 6.12 trajectories remain repaired

| Finding | Current disposition |
| --- | --- |
| **SC612-01: isolated P–Q component without a root** | No finite witness exists. The external conclusion’s premise is not established; the upstream cycle alone does not make that external route circular |
| **SC612-01: rootless P–Q alternative beside a converse cycle** | The rootless alternative supplies no witness and clears no dependence on the conclusion |
| **SC612-02: incompatible terminal judgment** | The judgment is ineligible for the particular consumer. It cannot clear the compatible converse cycle |
| **SC612-03: empty effective-assessment set** | The all-negative branch explicitly requires at least one effective assessment |
| **R612-01: anonymous no-refusal overstatement** | Annex §7.8 limits the statement to decision refusal and expressly retains the objection’s liveness consequence |

The repaired compatible-root trajectories require the validity and eligibility guards that now apply to every intermediate step. R614-01 concerns a scenario that does not state those guards.

### 4.3 D1 stress cases 13, 14 and 33–47

| Case | Check against the operative text |
| --- | --- |
| **13** | A model-only argument with an open assumption can terminate as a valid argument under the listed model relations and assumption. This does not establish general discharge composition |
| **14** | A bypass branch leaves the hypothesis carried under Definition 2.7. It must remain a condition; SC614-01’s repair must preserve this |
| **33** | Direct checked-event support establishes the premise under the stipulated effectiveness and access guards |
| **34** | An empty supporting basis supplies no root and creates no cycle by itself |
| **35** | Converse-only support is circular. An eligible terminal alternative defeats it; an evidence-relation terminal must satisfy the new no-effective-negative guard |
| **36** | **Qualified by R614-01:** the intermediate step must have the required effective validity assessment |
| **37** | The target-membership guard still excludes unrelated Q from the test and confirmation labels |
| **38** | A P–Q component without either kind of terminal root supplies no finite witness |
| **39** | The rootless component does not clear the additional converse dependence on K |
| **40** | An incompatible judgment clears nothing. Compatible event support works, including compatibility established without effective disagreement |
| **41** | Correctly narrowed to the assessment-set cause alone |
| **42** | An unassessed premise-free step supplies no root; adding a converse basis makes the consuming route circular |
| **43** | A positively assessed, non-disputed premise-free step supplies a valid-argument root and the required label |
| **44** | Correct for an ordinary undischarged hypothesis. It does not supply the missing discharge-aware witness rule |
| **45** | Negative or disputed intermediate inference assessments prevent rooting through that step |
| **46** | Immediate equality supplies the reaching base case; the self-premise route is circular |
| **47** | An evidence relation with an effective negative evidential assessment is not a terminal basis |

### 4.4 Well-definedness, computability and claim limits

For a fixed finite readable record graph, fixed position, ruleset context, compatibility results and avoided set, Definition 6.2 describes finite witnesses in an AND/OR dependency graph. Event terminals and eligible valid arguments seed successful witnesses; an inference alternative succeeds only when every required premise has a witness.

This is computable by graph discovery and propagation of successful witnesses. It does not require treating projected standing as evidence or choosing an arbitrary fixed point over standing.

Core §9.9 preserves the bounded failure result:

> "rooting not determined beyond ⟨frontier⟩"

and prevents an assessed-sound report when the required calculation is stopped.

No general computability impossibility was established. SC614-01 concerns the adequacy of the condition context in that computation. The declared latency and traversal envelope remain unqualified by execution.

The strengthened rule certifies inference-step validity along one qualifying witness. It still does not certify that every recorded support of every upstream claim is sound, or eliminate all upstream disagreement. “What rooting certifies” appropriately limits that claim; front ends and E5 must preserve the distinction.

### 4.5 Earlier ledgers

The earlier dispositions carried by the 6.13 review remain historical, bounded assessments. Current inspection retained the objection-footprint, fixed-home, target-specific settlement, dispute-lifecycle, independent-test provenance, signature, deletion and recovery contracts behind those dispositions.

This is not a fresh reconstruction of every 6.4–6.11 trajectory. In particular, earlier general statements that discharge semantics were retained must now be qualified by SC614-01. The broader warrant family cannot be declared closed.

## 5. D-100 completions and owner decisions

### 5.1 The four author completions

| Completion | Assessment against what the owner was shown |
| --- | --- |
| **Conditions travel at every step** | **Not established within the accepted recommendation as written.** Ordinary propagation is appropriate, but the universal rule fails valid discharge composition. D-100 expressly promised to keep D-70/D-71; D-72 also stands. SC614-01 needs correction and owner adjudication |
| **A terminal basis judged unusable does not root** | A bounded, conservative extension of the no-invalid-support direction. It excludes an evidence relation with an effective negative evidential assessment while retaining D-99’s direct-event terminal. No counterexample requiring reversal was established |
| **Dependence is read from every cited step** | Consistent with D-99’s actual-dependence rule. An unassessed or invalid alternative cannot root a premise, but its cited dependence can still explain circularity |
| **Objections inside a chain do not remove a step from the witness** | Consistent with D-98’s distinction between challenge state and attributed assessment. The one-level display and coverage boundary remain material; this supplies no end-to-end absence-of-objections guarantee |

The recommendation and decision record are author-recorded evidence of the owner’s answer. The original conversation was not independently inspected.

### 5.2 Required dispositions

1. **Reconcile discharge with witness eligibility.** Preserve the owner’s valid-argument direction while making correctly discharged hypotheses local to the subderivations that require them.
2. **Adjudicate the first completion.** The current all-step condition rule cannot be accepted as preserving D-70/D-72 without resolving SC614-01. Restricting the product to flattened arguments instead would be a scope decision the owner was not shown here.
3. **Correct the inherited scenario preconditions.** R614-01 needs no new policy, but the expected evidence outcomes must match the operative predicate.
4. **Ratify only a separately bound, reviewed revision.** Acceptance of D-100’s recommendation did not accept these candidates.

D-37–D-100 were examined through the bound decision records and the moved D-47–D-56 table. D-90, D-91 and D-93 remain superseded proposals under the D-94 record.

No additional concrete reason was established to reverse D-97’s target-specific settlement, D-98’s assessment/challenge distinction, D-94’s fixed-home construction, D-92’s existence boundary, D-95’s identity-only delta, D-79’s disclosed appointment-refusal residual or D-65/D-84’s recovery tradeoff. This is not blanket validation of that decision range.

Gate 0 also retains the operational and product obligations in core §§16 and 18.1: pilot languages, a bound profile, bounded D4 and executable evidence specifications, and runtime, storage, KMS, backup and restore feasibility. This review supplies none of that qualification.

D1 §11 and core §17.2 identify the material realized record, readers, routine questions and inspection surfaces. Technical review does not accept surfaces marked beyond the requested deliverable.

## 6. Simplicity

The package’s **58,357-word** count was confirmed: D1 13,711, core 41,353 and anonymous-review annex 3,293 words. The finite-witness consolidation is useful, but it has not removed the condition/discharge conflict.

Text that can move to cold, discoverable history in a separately bound revision:

- The long predecessor/change-map chronology in D1’s opening metadata and §0.1, and core §1/§1.1. Keep the current parent, package identities and governing decision bindings prominent.
- Repeated inventories of reviewer ancestry and repair identifiers inside normative paragraphs. Keep their substantive constraints in the owner text and their chronology in the change maps.
- Repeated retirement explanations for handles, dispatch, publication machinery and time-based retention. One retirement map can own that history; current sections need only their current contracts.
- Parallel full scenario descriptions in D1 §10.3 and core T135–T139. Keep one exact scenario inventory with cross-references from the semantic owner, so new preconditions cannot diverge as in R614-01.
- Repeated summaries of the root rule in core §5.3, TE-07 and decision tables. These can cite Definition 6.2 and retain only their distinct architectural obligations.

Keep the witness base cases, condition eligibility, discharge boundaries, cycle discriminators, homing proof, mandatory lists, traversal limits and deletion/restore coverage.

The next repair should reconcile conditions and discharge at their existing D1 owner. A stored “rooted” flag, special-case registry or second discharge ledger would add competing authority without resolving the definition.

No reduction estimate was measured. No frozen file was changed.

## 7. Evidence, inspectability and limits

**Executed:** Read-only source inspection, searches, selected predecessor comparisons, initial and final `sha256sum` verification, branch/HEAD and working-tree checks, and documentary trajectories over roots, validity, conditions, discharge, cycles, assessment sets, objection semantics, signatures, access, archival, deletion and restore.

A small in-memory illustration evaluated **21 adaptively selected configurations** using a finite-witness saturation calculation and visited-set reachability. They included event and empty bases, unassessed/valid/negative/disputed premise-free steps, converse alternatives, open conditions, effective-empty premises, immediate self-dependence, rootless cycles, event exits, invalid intermediate steps, the case-36 contrast and three discharge representations.

That illustration used preclassified judgment eligibility and simple identity/set condition coverage. It did not implement UPMS effectiveness, comparability judgments, derivation validation, access control, transactions or the complete standing projection. It supports the stated documentary classifications; it is not product qualification.

**Not executed:** No UPMS implementation, database transaction, KMS operation, recovery exercise, integration test, benchmark or empirical reader study. All product acceptance scenarios remain **UNEXECUTED in this review**.

**Findings and null envelope:** The blocking finding concerns valid discharge across intermediate conclusions. The additional finding concerns inherited scenario preconditions. Broader inspection established no additional concrete blocker in the examined cross-cutting contracts. Security efficacy, runtime feasibility, performance, warning fatigue, human comprehension and cost remain unmeasured.

**Selection:** One adaptively developed documentary review. The 21 configurations are a local count, not the whole historical search. They were selected after reading the candidate and prior findings, with no held-out or preregistered claim. No empirical model or pipeline survivor was selected. Earlier search history is known only through the supplied records.

**Authority and tension search:** No accepted UPMS D1 authority exists. The search covered the current package, bound reviews and change maps, owner decisions D-37–D-100 and selected earlier warrant references. Historical findings retain their attributed statuses; this record does not rewrite their homes. Original conversations, external issue systems and SCIRE/SSDS source authorities were not accessed.

**Independence:** This supplies outside-Claude-family review, with no new reviewer-family independence from the earlier Codex records. Reading the author’s decomposition and prior reviews creates anchoring risk.

**Persistence and mutation boundary:** The user-designated home is `workplans/active/UPMS_Candidate_6_14_Independent_Review.md`, populated by saving this final response. I created, edited, renamed or deleted no file and ran no writing Git command. HEAD and all 27 bound hashes remained unchanged. Initial `git status --short` was empty; the final check listed untracked dotfiles/configuration entries. Their origin was not investigated, and I neither opened nor modified them.

**Revisit condition:** Review a new hash-bound revision resolving SC614-01 at D1 Definition 2.7/§6.1 and its core consumers. Retest multi-step discharge, unconditional downstream use, open assumptions and bypass paths; preserve the repaired empty-premise, invalid-step, incompatible-condition, cycle and assessment-set trajectories. New material counterevidence also reopens this judgment.

## Appendix A. Review-method inputs

These are method and orientation inputs, not UPMS product authority. Skill paths are relative to `/home/samjin/.codex/skills/`. Historical memory supplied review-boundary orientation; substantive findings were rebound to current files.

| Source | SHA-256 | Coverage |
| --- | --- | --- |
| `scientific-formulation/SKILL.md` | `111a13625cf40a70aa95cf0c3968ca8efa533bfab55ec94a772d5790b2a81b5c` | Entry and review obligations |
| `software-design/SKILL.md` | `d5f0d045ee6af2db72dfd1cd5da86362b48512cc6e6bc4d293ad363747ee2364` | Entry and review obligations |
| `scientific-formulation/references/scientific-formulation.md` | `246cef460328c85c6d9ca4c0d2d45586486b70ecbf76308c7b7318f7df706f99` | Read |
| `software-design/references/architecture-and-design.md` | `06a7f931935ae84f11d3fd9ec52124333489d5c162fe1de6996535cee839cfd6` | Read |
| `software-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` | Definition, warrant and review passages |
| `scientific-formulation/references/evidence-evolution-and-dependencies.md` | `8fe20778d49d0546a3a9523aaab3ea287dbd50f48ea43af779f30e1b7fc8001d` | Selected applicability, evidence and authority passages |
| `software-design/references/convergence-and-cycle-economy.md` | `25015789764f5f631c869715f695588ec095563e6927d3866edd52ae8a11747e` | Selected recurrence, simplification and revision-economy passages |
| `/home/samjin/.codex/memories/MEMORY.md` | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` | Selected historical review-boundary guidance |

