# UPMS Candidate 6.16 Independent Review

**Model family / model name:** OpenAI GPT family / Codex, GPT-6-based. The exact serving-model identifier is not exposed in this session. I am **the same reviewer and family as the 6.4 to 6.8 and 6.12 to 6.15 reviews and the 6.11 cross-check**, so this review is not blind. I did not author these revisions. No subagents were used.

**Date:** 5 November 2026, America/Chicago.

**Repository binding:** Branch `upms-candidate-6-d1-formulation`, HEAD `5ecf89a7f50fe5e7dad1f85d884f40ff936f95b6`.

**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`. Scientific-formulation and software-design skills were applied.

**Integrity verification:** I read the request first, then repository-root `AGENTS.md`. Before substantive review, `sha256sum` verified the request’s supplied hash and all 27 files directly bound by it: **28 checks**, including the four deferred documents. All matched. Final verification repeated all 28 checks; all matched.

**Input identities and reading coverage:** Paths below are relative to `workplans/active/`, except `AGENTS.md`. Hash verification alone is not substantive review.

| File | SHA-256 | Coverage |
| --- | --- | --- |
| `UPMS_Review_Request_Candidate_6_16.md` | `1aedd0f0a308e0ec38ae1933ba8583716607c99e7cdd0c68cd173763b4ad6401` | Read first, in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_15.md` | `8d934751f65cd6506d343b3ebde23a31c60ff5f57582a110023d80999d8d5b2c` | Read throughout for consistency; operative definitions and cases reread |
| `UPMS_Architecture_Manual_Review_Candidate_6_16.md` | `e9f578b32e0a6d8a9363641a4af8bfd1942ed10c86884a291e91d1295d4c8af9` | Read throughout, including the acceptance inventory |
| `UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Read in full |
| `UPMS_Candidate_6_15_Independent_Review.md` | `195d27b21f2917e010a732bb15740b43ea617d7a3349421ba5b159f38de7f251` | Findings, regression dispositions, decisions, simplicity and limits |
| `UPMS_Architecture_Manual_Candidate_6_16_Change_History.md` | `9a4b7a68930b4210a076d6af83fd6a47f0bc2f412477b5310f4a0c3b8cdb5358` | Read in full as claims to test |
| `UPMS_Architecture_Manual_Review_Candidate_6_15.md` | `6ccb71fa7d8ca3ed43db913216d94f66d9e480d7b6f2531f3500e7af3379e457` | Complete change comparison; not independently reread in full |
| `UPMS_Candidate_6_14_Independent_Review.md` | `ecb8d25b7f1254b168ee1563eb9d4930afe2a70e015d9aee438d7d1b8ec7a7a2` | Serious Challenge, trajectory, repair and verdict; targeted searches |
| `UPMS_Owner_Decisions_6_13_Review_2026-11-05.md` | `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343` | Read in full |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_15_Change_History.md` | `9777f805ef2ad659a21586b3cf51f76f392a18599702fc7476c93fbb3961e0ac` | Read in full as claims to test |
| `UPMS_Candidate_6_13_Independent_Review.md` | `0b2b2c66a38c6aef87af16518876ed90e59f424ff3a49cf82c950ac418944f7b` | Findings, regression dispositions, computation and chain-validity boundary |
| `UPMS_Candidate_6_12_Independent_Review.md` | `796d87bbb33d48f79176f15a6dee5c8d71e0e04c1bd292df8577f313a2330e26` | Rootless-cycle and incompatible-judgment trajectories; empty-set finding and targeted searches |
| `UPMS_Owner_Decisions_6_11_Review_2026-11-05.md` | `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295` | Read in full |
| `UPMS_Owner_Decisions_6_8_Review_2026-11-05.md` | `5e9b40d43746059cbd4f23ff671bab735af7eccec5b940d3a36890f24cec33e9` | Read in full |
| `UPMS_Candidate_6_8_Independent_Review.md` | `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad` | Targeted searches only; earlier dispositions obtained through later bound records |
| `UPMS_Owner_Decisions_6_5_Review_2026-11-05.md` | `8cc6ffc8e9bf89119a92b0500ac4be3fee9775e0d818821bfb30985ee0aa59fa` | Read in full |
| `UPMS_Owner_Decisions_6_4_Review_2026-11-04.md` | `20144a3a92753313d1163378c3bdf338509a0910962bdb44fd38f458104c9671` | Read in full |
| `UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Read in full |
| `UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Read in full |
| `UPMS_Owner_Decisions_Math_2026-11-03.md` | `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | Read in full |
| `UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Read in full |
| `UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Hash only |
| `UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Hash only |
| `UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Hash only |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` | Hash and targeted search; not substantively reviewed |
| `UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md` | `f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7` | Hash only; excluded |
| `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md` | `71083419f4b9d4091153d7fd86ec32046081eca1f295d9f31e0b867015f51a58` | Hash only; excluded |
| `UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md` | `d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e` | Hash only; excluded |
| `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md` | `0fc9822778e3851fb7fec9593e1bfe150064e09a84982a02fe51aa4310ecd733` | Additional input: moved D-47–D-56 table and surrounding decision summaries |
| Repository-root `AGENTS.md` | `081ae30487a937ff8b6f45d4bf75cb3f7e5fa289387a8298b8a59253ae7559de` | Read in full |

**Parts not read:** Hash-only documents were not substantively reviewed. Earlier candidates, reviews and change histories were not reconstructed beyond the stated coverage. Original owner conversations, external issue systems, SCIRE and SSDS source authorities, implementation, runtime sources and deployment configuration were not read. The deferred annexes and mathematics formulation receive no verdict. Review-method inputs appear in Appendix A.

**Status:** Documentary falsification evidence asserted by Codex as an AI reviewer. This record grants no product-owner ratification, implementation authority, runtime qualification or acceptance of additional product scope.

## 1. Serious Challenges

**None established against the reviewed revision.**

SC615-01’s contradictory acceptance requirement is repaired. The wider inspection and regression trajectories below established no additional concrete blocker. This is a bounded review judgment, not proof that every possible defect has been excluded.

## 2. Verdicts and retained strengths

| Subject | Gate 0 entry technical verdict | Reason |
| --- | --- | --- |
| D1 formulation 1.15 | **PASS retained** | Unchanged; current consistency and regression checks found no reason to reverse the 6.15 judgment |
| Core 6.16 with anonymous-review annex 6.7 | **PASS** | SC615-01 and both parts of R615-01 are repaired; the referenced cases preserve the operative rooting distinctions and distinct architectural obligations |
| Checking, Slice 4 and mathematics packages | **No verdict** | Deferred or separately reviewed |
| Earlier candidates and proposal | **Historical verdicts unchanged** | No retroactive acceptance |

These are technical verdicts for **Gate 0 entry**. Gate 0 itself remains incomplete under core §§16 and 18.1. Neither text is accepted-current or implementation-ready through this review.

Retain the single custody system; distinct occurrence, proposition and assessment records; attributed judgments; derived standing; exact signatures; deterministic mandatory lists; fixed objection homes; explicit coverage; and deletion and restore limits.

For rooting, retain finite witnesses, eligibility at every depth, positive inference assessments with no effective negative assessment, discharge-aware contexts, path-scoped discharge, carried conditions, and the distinction between rootlessness and circularity.

## 3. Findings by earliest owning domain

**D1:** No new material inconsistency with core 6.16 was established. D1’s prior PASS is retained within the requested consistency scope.

**D2:** No separate numerical-method defect was established. This review does not open D2 or qualify a quantitative method.

**D3:** No new blocking finding was established. The acceptance-inventory repairs are assessed individually below.

**D4:** Not reviewed. No implementation or executable acceptance evidence was supplied or exercised.

## 4. Repair dispositions and adversarial checks

“Repaired” means the current operative text defeats the identified documentary trajectory. It does not mean executed product qualification or exhaustive closure of every sibling defect.

### 4.1 Status of every finding of the 6.15 review

| Finding | Disposition against 6.16 | Operative basis |
| --- | --- | --- |
| **SC615-01:** T138 rejects a hypothesis that its consumer discharges | **Repaired** | T138 uses the consuming step’s context and incorporates D1 cases 42–44; T140 incorporates cases 48–50 |
| **R615-01 A:** T75 calls an external rootless cycle circular | **Repaired** | T75 distinguishes whether the cycle reaches the consuming conclusion, citing cases 38–39 |
| **R615-01 B:** T135 treats any independent evidence relation as sufficient | **Repaired** | T135 incorporates D1’s terminal-basis cases, subject to §6.1’s guards; T139 incorporates the effective-negative contrast in case 47 |

No new owner policy choice is needed to make these repairs: they reconcile the acceptance inventory with existing semantics.

### 4.2 C616-1: discharge is tested by context

Core §15.1 now states:

> Where a scenario reproduces D1 §10.3 stress cases, those cases are its whole statement of records and outcomes, with the guards D1 §6.1 requires; the scenario adds only the architectural obligations it names

T138 then specifies:

> whether a hypothesis counts is decided by the consuming step's context (D1 §6.1), never by what that step carries alone

This agrees with D1 §6.1, “Premises”:

> A step's **context** is its stated conditions (`c` in Definition 2.7), the carried conditions of its conclusion, and the hypotheses it discharges

D1 case 44 expressly includes the discharge alternative:

> `h` is in that step's context (it carries or discharges `h`)

**Replay of the former counterexample — paraphrase.**

```text
U: h → B       carries h
D: B → K       discharges h
T: K → L       unconditional

J_B: supported-under(h), citing U
J_K: supported, citing D
```

Assume one acyclic derivation for U/D, effective positive inference assessments with none negative, and all other eligibility guards. There is no bypass or comparability judgment.

D’s context contains h internally. J_B qualifies for D; U is valid for D and ends the branch once its carried hypothesis is set aside. D exports K without h. D is therefore eligible for unconditional T, and K has a valid-argument root witness for T.

T138 no longer rejects this construction because D does not carry h. T140 requires the same outcome through D1 case 48.

**Bypass contrast.** If h also reaches K on a branch bypassing D, Definition 2.7 keeps h as a condition of K. Case 49 then requires T’s context or qualifying comparability to cover it. T140’s phrase “the discharged conclusion” does not authorize dropping h in this case: h is not discharged **for K** under the all-path rule.

**Open-hypothesis contrast.** Without D, B remains conditional. Case 50 excludes its unconditional use and retains “compatibility not established.”

**Consequence:** The formerly conflicting acceptance obligations now agree. No flattening step, new stored status or discharge exception is required.

### 4.3 C616-2: cycles and terminal eligibility remain distinct

T75 now requires:

> a route whose premise is supported only through the cycle shows "premises not established" when the cycle does not reach the route's conclusion and is circular when it does

**Counterexample replay — paraphrase.**

```text
U: Q → P
V: P → Q
S: P → K
```

Let P and Q have eligible supporting judgments citing U and V, with no terminal or valid-argument exit. K lies outside that component.

P has no finite root witness for S and does not reach K. S therefore has “premises not established” and is non-circular. Adding an eligible cited converse path K → P makes the dependence on K real; S becomes circular. The rootless P–Q alternative clears nothing.

T75 now gives those two outcomes. It also retains the distinct theory-channel flagging requirement and the requirement that a human assertion alone adds no route.

T135 incorporates:

> D1 §10.3 cases 33 to 36 and 38 to 40, with the outcomes stated there

The former “independent evidence relation makes it sound” shortcut is gone. D1 §6.1’s terminal-basis rule requires that a cited evidence relation:

> has no effective negative evidential assessment

**Negative-terminal replay — paraphrase.** Start with S: P → K and converse-only support K → P. Add an eligible positive claim judgment of P citing independent relation E, whose only effective evidential assessment is `not-usable`. E supplies no terminal basis; the converse dependence remains circular. D1 case 47, incorporated by T139, makes this contrast explicit.

Replacing that E with a qualifying terminal basis permits a witness avoiding K, subject to the remaining guards. Independence and terminal eligibility remain separate questions.

### 4.4 No architectural obligation was lost by referencing D1

| Revised surface | Retained obligation |
| --- | --- |
| §15.1 introduction | Exercise the real enforcing owners; inherit D1 records, outcomes and guards |
| T75 | Theory-channel flag; external-cycle/converse-cycle distinction; assertion alone supplies no route; an existing qualifying witness survives an added converse |
| T135 | Cases 33–36 and 38–40; explicit traversal frontier; no assessed-sound result when rooting is undetermined |
| T138 | Cases 42–44; context distinction; valid-argument label on the predicate; top-level valid steps with no premises left |
| T139 | Cases 45–47; discovery of a later successful branch regardless of traversal order |
| T140 | Cases 48–50; discharge computed through §5.5; introduced/discharged hypotheses displayed without exporting a discharged condition |

The shorter references preserve semantic outcomes through D1 §6.1 and the incorporated cases. For example, case 33 supplies establishment and non-circularity; the otherwise-qualifying positive-assessment guards and route-status table still determine assessed-sound status. Removing a duplicate sentence does not remove that governing rule.

### 4.5 Other rooting summaries and scenarios

I checked core §5.3, §9.9, TE-07, T98, T137 and §18.2 against D1 §6.1 and cases 33–50.

- **§5.3** retains the distinction between an admitted judgment and an established premise, and refers establishment to Definition 6.2’s eligible, assessed-valid witness.
- **§9.9** explicitly checks each witness step against its consumer’s context, including hypotheses the consumer discharges. It retains traversal-order and frontier requirements.
- **TE-07** retains the warrant restriction and valid-argument qualification; it does not supply a replacement rooting algorithm.
- **T98** retains compatibility, cross-ruleset, discharge, model-condition and bypass discriminators. Its condition-reference wording does not exclude discharge: the discharging step names the hypothesis, and operative eligibility is governed by its context.
- **T137** concerns evidence relations without effective assessments. Unlike inference steps, those examples have no premise or self-dependence branch that independently makes them broken.
- **§18.2** describes D-100 through Definition 6.2 and the step’s context, and identifies the corrected first completion.

No remaining carry-only replacement for the operative context rule was established in these surfaces.

### 4.6 The 6.15 review’s §4 trajectories remain repaired

The following are documentary replays against current operative text, under otherwise-qualifying access, revision, ruleset and assessment guards.

| Trajectory or boundary | Current result |
| --- | --- |
| Multi-step discharge followed by unconditional use | Valid-argument witness; discharged h is not exported |
| Nested discharge of h and then g | Each local context admits its hypothesis; each stops only at its discharging boundary |
| Open h without discharge | Conditional use only; unconditional consumer lacks a root |
| Bypass around discharge | h remains carried |
| Model condition alongside discharged h | Model condition remains; discharging h does not remove it |
| Unsupported discharge or cyclic derivation | Existing core §§4.3 and 5.5 guards remain |
| Unassessed premise-free step | No root; its converse-cycle sibling stays circular |
| Positively assessed premise-free step, none negative | Authorized valid-argument root, with its label and conditions |
| Unassessed, invalid or disputed intermediate inference step | No witness through that step |
| Direct K → K with a checked-event judgment of K | Immediate equality establishes self-dependence; circular and broken |
| External rootless P–Q component | No finite witness; external consumer is non-circular with premises not established |
| Rootless P–Q alternative beside a converse path | Clears no dependence on the consuming conclusion |
| Incompatible event-backed judgment | Supplies no eligible alternative; qualifying compatibility is required |
| Effective-negative evidence relation | Not terminal |
| Empty effective-assessment set | Does not alone satisfy the all-negative branch of broken |
| Root encountered after a cyclic branch | Must remain discoverable; cyclic exploration is not completed failure |
| Traversal limit before witness determination | Frontier reported; no assessed-sound claim beyond the determined extent |
| Anonymous objection without a new judgment | Challenge state changes; assessed result does not; no decision refusal; liveness consequence remains |

Cases 33–50 retain the corresponding distinctions, including case 37’s target-specific independence labels and case 41’s limited empty-assessment guarantee.

For a fixed finite readable graph and fixed eligibility context, witness existence remains a finite-tree question over claim/consumer-step pairs. A successful-witness calculation can evaluate it without using projected standing as evidence. This is not a runtime performance qualification.

### 4.7 Broader package inspection

I also examined the current contracts for:

- objection footprints, historical assessment endpoints and sharing-original closure;
- fixed-home resolution/dispute chains and configuration-based coverage;
- target-specific settlement, dispute withdrawal and historical reads;
- exact decision revisions, policy ownership and signature completeness;
- target-directed independent-test labels and missing-provenance exclusions;
- access evaluation, processor eligibility and lineage exclusion;
- anonymous-role placement, operational records, logs and the disclosed appointment-refusal residual;
- deletion barriers, authored-descendant obligations, recovery-log erasure, missing restore context and off-site outage behavior.

No additional concrete blocker was established in those examined contracts. This does not freshly reconstruct every historical 6.4–6.11 trajectory or qualify any enforcement mechanism.

The limit in D1 §6.1, “What rooting certifies,” remains material: one qualifying witness is not a certificate that every recorded upstream support is valid or that upstream objections are absent. E5 and front-end explanations must preserve that distinction.

## 5. Owner decisions and remaining closure

### 5.1 D-100 and its completions

The recommendation recorded in the D-100 decision expressly says:

> This keeps D-70 and D-71.

The current context rule preserves that commitment and D-72’s bypass rule.

| Author completion | Current assessment |
| --- | --- |
| Conditions travel at every step | Consistent for the tested trajectories when read through the corrected context rule: ordinary conditions travel; valid discharge stops its hypothesis; bypass preserves it |
| A terminal basis judged unusable does not root | Preserved through the effective-negative exclusion |
| Dependence follows every cited step | Preserved; validity is required for rooting, while actual cited dependence can include unassessed steps |
| Objections inside a chain do not remove its steps from the witness | Preserved; objections and attributed assessments remain distinct, with upstream challenge state available at the stated depth |

No new policy decision or reversal of D-70, D-71, D-72, D-98, D-99 or D-100 is justified by the examined trajectories.

### 5.2 Decisions and evidence still needed

The texts still require the existing owner actions and closure:

1. **Ratify or reject the exact reviewed texts.** This PASS supplies technical review evidence, not product acceptance. Decisions accepting recommendations did not accept these candidates.
2. **Complete Gate 0’s named deliverables:** pilot languages, a bound deployment profile, bounded D4 and executable evidence specifications, and runtime, storage, KMS, backup and restore feasibility.
3. **Freeze evaluation decisions before measurement,** including E1–E5 error and cost limits and applicability by slice.
4. **Complete the SCIRE front-end contract before Gate 2** without narrowing the back-end objection guarantees.
5. **Review the deferred packages at their stated boundaries.**

D-37–D-100 were considered through the bound decision records and moved D-47–D-56 table. D-90, D-91 and D-93 remain superseded proposals under the D-94 record. The decision records are Claude’s accounts of owner answers; the original conversations were not independently inspected.

D1 §11 and core §17.2 state material records, intended readers, routine questions and inspection surfaces. Technical review does not accept surfaces marked beyond the requested deliverable.

## 6. Simplicity

The package count was confirmed: **58,694 words**—D1 14,054, core 41,347, anonymous-review annex 3,293. The core is 187 words shorter than 6.15.

The revision makes a useful substantive reduction: the affected rooting scenarios now have one home. Keep that change.

Further text can go in a separately bound revision:

- Long predecessor sequences and reviewer ancestry in core §1, Appendix A and Appendix B can be replaced by a concise route to the change history.
- D1’s opening predecessor catalogue and historical input rows can move to its companion history, retaining exact current parent and decision bindings.
- Core §18.1’s long enumeration of historical finding identifiers can become a reference to the bound review ledger, while retaining live obligations and current repair dispositions.
- Repeated retirement explanations can be consolidated in the retirement/change map.
- Other genuinely duplicated scenario narratives can follow the same arrangement: one full semantic case, plus references and distinct architectural obligations.

Do not remove terminal and valid-argument base cases, eligibility guards, bypass contrasts, traversal limits, mandatory lists, the homing proof or deletion/restore obligations.

No new rooted flag, discharge ledger, exception registry or reconciliation service is warranted. No further reduction estimate was measured.

## 7. Evidence, inspectability and limits

**Executed:** Read-only inspection, searches, predecessor comparison, reference-existence checks, word counts, initial and final `sha256sum` verification, and branch/HEAD and working-tree checks. All referenced D1 cases in T135 and T138–T140 exist.

**Current documentary evidence:** The repaired scenarios and the adversarial trajectories in §4 were checked against current operative definitions. A.26’s repair claims were not used as proof.

**Reused evidence:** Earlier review records supplied counterexample constructions and historical dispositions. The 6.15 review’s 25-configuration illustration was not rerun and is not counted as current executable evidence.

**Not executed:** No UPMS implementation, database transaction, KMS operation, restore exercise, integration test, benchmark or reader study. Every product acceptance scenario remains **UNEXECUTED in this review**.

**Findings and null envelope:** No new material defect was established within the examined documentary package. SC615-01 and R615-01 are repaired. Runtime feasibility, security enforcement, performance, storage growth, warning fatigue, reader comprehension and lifecycle cost remain unmeasured. The materiality test was whether a trajectory could change support, conditions, dissent visibility, authority, confidentiality, retained evidence or gate acceptance.

**Selection:** One current package was reviewed, with its predecessor used for comparison. Documentary probes were selected adaptively after reading the request, prior findings and candidate. No held-out, preregistered or exhaustive-search claim is made. No empirical model or pipeline survivor was selected.

**Authority and tension search:** No accepted UPMS D1 authority exists. The search covered the current package, supplied review records, relevant change maps and owner decisions D-37–D-100. Original conversations, external issue systems and SCIRE/SSDS source authorities were not accessed. Historical dispositions remain attributed evidence in their existing homes.

**Independence:** This provides outside-Claude-family review, with no new reviewer-family independence from the earlier Codex records. Prior findings and author change maps create anchoring and common-mode risk. Historical memory supplied review-boundary orientation only; substantive conclusions were checked against current files.

**Persistence and mutation boundary:** The user-designated destination is `workplans/active/UPMS_Candidate_6_16_Independent_Review.md`, populated by saving this response. I created, edited, renamed or deleted no file and ran no writing Git command. Branch, HEAD and all 28 directly checked hashes remained unchanged. Initial and final working-tree listings showed the same untracked configuration entries; I did not open or modify them.

**Revisit condition:** New material counterevidence, a changed bound text, failed executable conformance, or E1/E4/E5 evidence that the stated conditions, witness labels, coverage or objection boundaries mislead readers reopens the affected judgment. Product-owner ratification and the remaining Gate 0 evidence must be recorded separately.

## Appendix A. Review-method inputs

These are method and orientation inputs, not UPMS product authority. Skill paths are relative to `/home/samjin/.codex/skills/`.

| Source | SHA-256 | Coverage |
| --- | --- | --- |
| `scientific-formulation/SKILL.md` | `111a13625cf40a70aa95cf0c3968ca8efa533bfab55ec94a772d5790b2a81b5c` | Entry and review obligations |
| `software-design/SKILL.md` | `d5f0d045ee6af2db72dfd1cd5da86362b48512cc6e6bc4d293ad363747ee2364` | Entry and review obligations |
| `scientific-formulation/references/scientific-formulation.md` | `246cef460328c85c6d9ca4c0d2d45586486b70ecbf76308c7b7318f7df706f99` | Read |
| `software-design/references/architecture-and-design.md` | `06a7f931935ae84f11d3fd9ec52124333489d5c162fe1de6996535cee839cfd6` | Read |
| `software-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` | Read |
| `software-design/references/convergence-and-cycle-economy.md` | `25015789764f5f631c869715f695588ec095563e6927d3866edd52ae8a11747e` | Read |
| `/home/samjin/.codex/memories/MEMORY.md` | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` | Selected historical review-boundary guidance |

