# UPMS Candidate 6.4 and D1 Candidate 1.4 — Independent Review

**Reviewer / asserter:** Codex, an OpenAI GPT-6-family AI. This is outside the Claude family and **the same reviewer family as the proposal review**. No subagents were used. The exact serving-model revision is not asserted.
**Date:** 4 November 2026 (America/Chicago).
**Governing method:** SSDP 7.2.1; no task or named workplan assigns a protocol_version. Scientific-formulation and software-design skills applied.
**Status:** Independent documentary falsification findings for the product owner; no ratification, implementation authorization, qualification or product-scope acceptance.
**Repository baseline:** UPMS commit 6f5d5e2d92ebb27410628f3c48871ff2a0247c09, branch upms-candidate-6-d1-formulation; clean at intake.

**Exact subjects, verified both against the handoff manifest and their originals:**

| Key | Original under workplans/active/ | SHA-256 |
| --- | --- | --- |
| D1 | UPMS_Theory_Evidence_Formulation_D1_Candidate_1_4.md | 5e2b67f97b919d6612db6ed22bd6a3c7456b2be7141e4ef634bb3c2416afbb8f |
| C | UPMS_Architecture_Manual_Review_Candidate_6_4.md | 3c9844db1c2b99094c882f3f2bcb4e6d8cdbf9f7f9df6ab02f68f962729b2e09 |
| A | UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Anonymous_Review.md | e5becbd510ec3205a5b241062c3bdca03a2dcbf90d6f803365f994fef51738cb |

**Reading limits, stated first:** D1, C and A were read in full. The proposal review, 6.1 review, 6.2 review, mathematics review, three packaged owner-decision records and A.14 were read in full. Change history A.8 and A.11–A.12 were read directly; the rest was searched or consulted selectively. Predecessors 6.3 and D1 1.3 were compared by changed ranges, not reviewed anew; 6.2 was hash-checked only. Candidate 5 was read selectively for custody, failure behavior and invariants. The proposal was read through §2.3, including D-20–D-36; later portions were searched, not read in full. The mathematics annex was read only for hooks and their dependent record, standing, tool and brief contracts (§M.0–M.7 selectively); its mathematics D1 parent, checking annex, Slice 4 annex and SCIRE mathematics extension were not reviewed. SCIRE v0.4 and its re-review were consulted selectively for imported meanings and the objection/access boundary. The workplan index and semantic history were consulted selectively. No SSDS source, native issue tracker, external literature, implementation or live integration was audited. Appendix A gives hashes and finer coverage for all packaged inputs; hashing a file is not reading or reviewing it.

## 1. Serious Challenges

These are constructed trajectories through the bound texts, not observed software failures. They challenge proposed D1/D3 contracts. Confidence concerns the documentary inference, not operational frequency.

### SC64-01 — Tool-check objections challenge a route but need not enter its decision's applicable set

**Earliest owner:** D1 F-6 and §6.1, then C §9.9 and decision projections. **Blocking; high confidence.**

**Observation.** D1 Definition 2.5 now admits objections to a rendering relation, binding or tool check. The §6.1 challenged row expressly includes a renders link or tool check cited by a route's effective assessment. But F-6 still adds, for an inference step, only its premises and conditions as endpoints. It does not add that step's assessment-basis tool checks or renders links. C §9.9 repeats both rules. This is an interaction introduced by the 6.4 hooks.

**Trajectory.**

1. Step S concludes K. Its effective inference judgment J finds S valid and cites passed tool check T and renders link L, using the mathematics annex §M.6's stated recording path. S has established premises.
2. A decision D cites K and S by identity. Its basis does not independently cite T or L; citing the step rather than duplicating its assessor's complete basis is allowed by §6.9.
3. A critic records unresolved objection O to L's fidelity, or to T's applicability. No fidelity judgment or obligation is needed for this trajectory.
4. K's route is challenged by the explicit §6.1 rule. Nevertheless, O targets neither a member of B(D), a basis claim, nor an inference endpoint listed in F-6. It is not a dispute of a resolution already in A(D). Thus O need not be in A(D), and F-7 does not require it on D's projection or in its late-objection delta.

A broad interpretation of “in scope” in C §10.5.1 might happen to display O in an additional list. It does not repair the exactly defined A(D), which SCIRE uses for D-38. The same scientific objection cannot have its applicability determined by which view happened to be opened.

**Consequence.** A new target kind is accepted and changes route standing but falls outside the consequential decision's required objection accounting. The repair repeats the earlier R-01 failure at the new tool/rendering boundary.

**Bounded repair.** Define one D1 applicability expansion for the exact tool-check/rendering prerequisites used by an effective route assessment, and use it consistently for route challenges, A(K), A(D), mandatory lists and the late delta. Preserve the deliberate one-hop boundary elsewhere; do not require arbitrary transitive prose inference. Alternatively require these prerequisites explicitly in the decision basis and reject an incomplete structural basis. Add a case where D cites only K/S and O targets T/L, including an objection arriving during signing. Objection existence must still never make the core refuse D under D-50. D-70 need not change: no fidelity judgment is cited as support.

### SC64-02 — Conflict-based appointment outcomes remain an oracle for sealed attribution

**Earliest owner:** D3 A §7.8 conflict checks and SE1/T104; owner adjudication of the promised disclosure boundary. **Blocking; high confidence.**

**Observation.** Matching the wording and timing of a sealed decline to a voluntary decline does not make the appointment outcome independent of sealed attribution. In one world the core permits acceptance; in another it declines on the invitee's behalf because of a sealed or critic-side ground. SE1 and T104 nevertheless require released check results not to change when only sealed attribution changes.

**Trajectory.**

1. Proposed chair X has no open conflict with the work and exactly one declared collaborator Y. X is not an anonymous critic; X knows this. No other critic-side relationship applies.
2. X accepts through the normal invitation path. In world W0, Y is not an anonymous critic: X is appointed. In W1, Y is the critic: the core emits the generic conflict-rule decline at the same response time.
3. X sees acceptance in W0 and the core's conflict decline in W1. Since X can rule out being the critic and knows the sole relevant relationship, the generic message identifies Y as an anonymous critic.
4. For the proposer, an invitee who reliably accepts provides a similar distinguishing experiment. Concealing the reason class and delaying the response do not equalize the outcome.

The disclosed possibility that someone may ask a declined person why they declined does not eliminate X's **in-product** inference. D-40 and D-67 trust operators, the front end and transport; X need be none of those. This counterexample uses no writing-style, timing, log or storage attack.

**Consequence.** The absolute noninterference statement and a useful deterministic secret-dependent appointment check cannot both hold as written. F62-11's literal reason leak is removed; its inference family is still open.

**Bounded repair / owner choice.** Specify the minimum intentionally disclosed predicate: an appointment may fail because an undisclosed conflict exists, with the resulting inference risk stated before anonymous submission. Narrow SE1/T104 accordingly if the owner accepts it. If that disclosure is unacceptable, change appointment governance or withhold this feature pending a design that meets the chosen guarantee. Do not add another euphemistic decline reason, random delay or wrapper and call it noninterference. Recheck both the invitee's and proposer's observations, including singleton relationship sets. This is a challenge to the strong guarantee, not a request to disclose identities or remove conflict checks silently.

### SC64-03 — Objection homing is not a maintained audience invariant

**Earliest owner:** D3 C §5.11, §6.7, §7.3.4, §9.9 and §10.3; D1 F-7 if the owner chooses a qualified visibility guarantee. **Blocking; high confidence.**

**Observation.** C §5.11 checks at record_objection that the objection's home includes every reader of its target. Later access changes, own-record entitlements and rebinding can separate those audiences. No corresponding lifecycle validation is stated. C §10.3 then filters objection metadata by the reader's rights.

**Trajectory A, even with one home scope.**

1. P owns claim K and C owns objection O to it in team scope S. Both are initially readable by the team.
2. P loses S's read membership. Under §7.3.4 and AC7, P still reads P's own K. P has no own-record entitlement to C's O.
3. P requests K's standing or a view presenting K. O is filtered out because P cannot read it, while K remains readable. The creation-time homing check was satisfied, yet the claim that every target reader can read its objection is now false.

**Trajectory B.** K lives in S and O is validly homed in a different scope R whose readers initially include S's. A manager widens S, or narrows R. New target readers can read K without O. “No live permission inheritance” makes this possible without any malformed write. A rebind to a wider-audience restatement has the same obligation; the rebind row does not state it.

**Consequence.** The default profile can have hidden applicable objections without embargoed data or the deferred strict profile. The declared C6-4/SC-42 reconciliation is too narrow. An unqualified complete dissent projection and the access rules cannot both hold for these reads.

**Bounded repair / owner choice.** Maintain objection audience compatibility across target/objection permission and tag changes, own-record reads and rebinds, or explicitly qualify every affected partial-coverage view using a policy independent of whether a hidden objection exists. Sharing/copying a target needs a stated objection treatment too. Do not reveal hidden existence through conditional warnings or silently grant access to dissent. Whether a partial-coverage consequential use may proceed remains SCIRE policy, not a new core veto. Retain D-50 and AC1. Reuse the existing permission/projection owners rather than introducing a second permission system.

## 2. Verdicts and what remains strong

| Subject | Gate 0 entry technical verdict | Basis |
| --- | --- | --- |
| D1 formulation 1.4 | **NO-PASS** | SC64-01; R64-01 and R64-02 below leave consequential route/compatibility semantics insufficiently bounded |
| Core 6.4 with anonymous-review annex 6.3 | **NO-PASS** | SC64-01–SC64-03 and the dependent D1 gaps |
| Frozen proposal v0.1 | Earlier **NO-PASS remains historical** | A later candidate can repair its direction; this review does not rewrite or retroactively pass the proposal |
| Checking, Slice 4 and mathematics packages | **No verdict in this review** | Deferred/separate review boundaries are retained; selected hook dependencies were inspected |

The one-store direction remains sound: Event/Claim/Judgment, separate exposure and support, attributed acts, conditional evidence, projected standing, one committer, mandatory dissent lists, and workflow policy in SCIRE should stay. The ordinary project-memory path does not need the entire theory layer. There is no demonstrated need for a universal score, theorem prover, general policy engine or separate scientific-result database.

The 6.3 repairs substantially defeat the specifically reported revision, supersession, anonymous-judgment, stored-delta and pending-signature trajectories. D-71/D-72 correctly distinguish carried conditions from established premises and discharge by path. Keeping fidelity, inspection and inference validity separate is also right. Those positive findings are bounded documentary judgments; they are not empirical adequacy or acceptance.

Absence of implementation evidence is **not** the reason for these conceptual NO-PASS verdicts. Planned T cases and E1–E5 remain legitimate future obligations, not executed evidence. A coherent candidate can be reviewed before they run.

## 3. Other findings by earliest owning domain

### R64-01 — Evidence usability is not target-directed support (D1 §5.1, §6.1–§6.2; High, blocking ambiguity)

**Trajectory.** E has kind refutes(K), a current observation and an effective evidential assessment of usable. There are no objections or obligations. Under §6.1, usability makes that assessment positive; E has no inference premises and satisfies assessed-sound. F-28 therefore gives has-sound-route(K) = true. The same calculation works for consistent-with(K), which Definition 5.1 explicitly says does not discriminate, and for a usable comparative relation favoring B over K.

**Consequence.** The predicate does not distinguish a usable negative/neutral route from a route supporting K, although the core describes routes as supporting claims and gives the predicate to front ends. This does **not** demonstrate that the implementation labels K supported: no implementation exists, and standing has no aggregate verdict. It demonstrates a consequential missing interpretation. Reading the predicate as mere “a usable bearing relation exists” is coherent, but then it must not be consumed or presented as positive support.

**Bounded repair.** Keep usability and evidential bearing separate in the projection. Define the predicate's intended consumer meaning, preserving kind, target direction, comparative alternative, purpose and conditions. Either restrict a positive-support predicate to appropriately assessed bearing, or name the existing predicate as route usability and forbid a positive-support inference from it. No probability or new score is required. Test entails/refutes, favors in both target directions, adequacy by purpose, consistent-with, and bears-on-unassessed as distinct cases. This is the still-open TE-R11 family, now with a finite concrete discriminator.

### R64-02 — Compatibility can select a favorable judgment despite concurrent disagreement (D1 §6.1; High, blocking)

**Trajectory.** P has an effective supported-under(H) judgment. S uses P under condition K. An effective comparability judgment says H covers K; another assessor's concurrent effective comparability judgment says it does not. Neither supersedes the other under Definition 2.8. There is no negative claim assessment of P, negative inference assessment of S, objection or obligation.

Compatibility is established by the existence of **an** effective covering comparability judgment. The route's disputed row only tests positive/negative assessments of the route; it does not test concurrent disagreement over compatibility. The favorable witness can therefore establish P for S and yield assessed-sound even though that applicability bridge is disputed.

**Consequence.** D-69 solves ruleset identity across scopes but not conflicting applicability judgments. Preserving both records somewhere is insufficient when a derived enabling predicate silently uses one.

**Bounded repair.** State how concurrent comparability outcomes affect that bridge: no established compatibility while an applicable contradiction remains unresolved, with both judgments shown; or an explicit attributed adjudication under a registered rule. Use the existing judgment-lineage and dispute semantics. Add this sibling to T98/T109. Do not choose by recency, majority, or whichever positive judgment is found first.

### R64-03 — Withdrawn basis records need an explicit decision-kind boundary (D1 F-3b; C §6.9; Medium)

**Trajectory.** K is withdrawn without a successor. A new recorded decision cites K by exact revision. K still exists and may be readable; check 1 tests existence/readability, and recorded decisions do not have the validated expected-current-basis check. None of checks 2–6 explicitly rejects withdrawal. But F-3b relies on the assertion that a withdrawn record cannot be cited by a new decision.

**Consequence.** The premise used to explain why withdrawn-target objections join no new A(D) is not concretized for all decision kinds. A historical reported decision must remain recordable even when its source decision was defective; that separate requirement should not be confused with a new act relying on the withdrawn record.

**Bounded repair.** Define the distinction in D1 and the decision integrity contract: new reliance versus recording historical decisions and explicit withdrawal/resolution acts. Enforce the chosen live-basis rule for the relevant kinds; labels suffice for historical reports. Do not impose a scientific-permission rule inside the core by accident.

### R64-04 — Recovery needs payload, dependency and outage discriminators (D3 §12.3–§12.4, §13; Medium, required before specification freeze)

**Erasure sibling.** D-65 adds objection grounds and resolution bases to the synchronously replicated recovery log. They can contain deleted source text. F62-17's reason-class-only marker repair does not test these payload classes. An appended tombstone alone would prevent serving but leave the text in active/off-site log copies. However, §12.3 already covers all content-bearing logs, journals and replicas, §6 permits physical payload erasure on explicit deletion, and §12.4/DL2 prohibit payload in surviving metadata. Those general requirements permit an erasable-payload realization; this is **not a demonstrated architectural impossibility or a separate Serious Challenge**. The concrete recovery surface inventory and executable test must include this newly payload-bearing log and its off-site copy.

**Dependency trajectory.** After the last canonical backup, create K, S, O targeting S, and a resolution decision with a judgment and exposure reference. A site loss retains O and the resolution via the recovery log, but may lose K/S, the judgment, release record or new scope/role configuration. A latest log position proves neither those endpoint bytes nor their meaning are recoverable.

**Consequence.** The restore may correctly stay closed under existing missing-reference rules, or show explicit missing records. Neither alone demonstrates the stronger claim that dissent survives on all dependent projections. A restore coverage line usefully discloses ordinary data loss; it does not supply missing dependencies.

**Bounded repair.** Specify the minimum recovery closure of each log entry and conservative rendering for missing endpoints. Include active/off-site log payload deletion in the existing purge inventory, allowing immutable ordering metadata to reference protected erasable payloads if that meets the existing contracts. T112/T13 must cover deleted objection grounds and resolution bases followed by restore, as well as new targets and resolution dependencies inside the RPO window. Also exercise off-site-copy outage during a restrictive commit: no acknowledged canonical-only transition, inconsistent retry or release; ordinary recall may degrade within the existing coverage/authorization contract. D-65's synchronous commitment has a real availability cost. These are concrete qualification obligations, not evidence that synchronous replication is impossible.

### R64-05 — An inherited T98 assertion contradicts the new scientific freshness owner (D3 acceptance oracle; Low, repair before executable tests)

C §15.1 T98 still says that a premise judgment made ineffective by an epoch advance breaks soundness. D-48, D1 Definition 6.0, C §9.9 and T109 explicitly exclude scope epochs from scientific effectiveness.

**Trajectory / consequence.** Advance an unrelated scope epoch without changing any Definition 6.0 condition. T109 requires unchanged standing. T98's unqualified epoch clause suggests the opposite. A test author can encode the obsolete five-minute/scope-epoch semantics.

**Repair.** Replace that clause with an actual scientific effectiveness invalidator, and keep the unrelated-epoch negative control. Project-memory freshness remains tested separately.

### R64-06 — The core still names parent 1.2 in its domain determination (D3 authority binding; Low)

C §1.4 says the parent is candidate 1.2, while §1.1 and the supplied review package bind 1.4. An implementer consulting the domain owner can take the older premise/discharge semantics. Rebind §1.4 in the next new candidate; the explicit 1.4 hash in this review controls this review. Do not edit the frozen candidate.

## 4. Regression dispositions

**Status vocabulary:** “Defeated” means this review found an operative contract that defeats the original constructed trajectory, not implementation qualification or amendment of the earlier frozen record. “Partial/open” names an unresolved part or new sibling. “Deferred” means explicitly outside the current product/review boundary; it is not repaired. No row inherits closure from an author's change map.

### 4.1 Codex proposal review: every finding

| Earlier finding | Status against current operative text | Basis / remaining limit |
| --- | --- | --- |
| SC-TE01 | Partial/open | Definition 6.0, concurrent heads and pinned projections are real repairs; SC64-01, R64-01/02 remain |
| SC-TE02 | Partial/open | Confined chair, no identity in model inputs, role placement and TCB disclosures are present; SC64-02 remains |
| SC-TE03 | Defeated for the screening-as-guarantee trajectory | C §10.5.1/MV1 use deterministic pageable lists; semantic detectors are fallible. Their inputs still depend on SC64-01/03 |
| SC-TE04 | Defeated within the core | D1 F-8, D-37/D-50 and A prohibit anonymous judgments and objection-based core refusal; SCIRE policy still needs its own specification |
| SC-TE05 | Defeated for the original signature/authority race | C §6.9 binds policy owner, exact revision, completeness, expected basis and owner handover; late delta is derived |
| TE-R01 | Partial/open | Same substantive disposition as SC-TE01; no arbitrary standing fixed point is adopted |
| TE-R02 | Partial/open | Same substantive disposition as SC-TE02 |
| TE-R03 | Defeated in output mechanism, qualified | Mandatory lists replace the detector promise; no guarantee of perfect natural-language characterization detection |
| TE-R04 | Defeated | Narrow no-veto meaning plus attributed adverse assessments; anonymity unavailable until Slice 3 |
| TE-R05 | Defeated for original trajectory | C §6.9/DC1/T100, with R64-03's separate withdrawn-basis boundary |
| TE-R06 | Defeated by explicit scope reduction | C §7.3.5/D-43 state direct ACL plus responsible sharing, not derivative containment; strict profile deferred |
| TE-R07 | Defeated as an overclaim | C §§8.1–8.2/10.6.4 bound UPMS capture and attestations; masking differs from rationale exclusion |
| TE-R08 | Partial/open | Archive-blind mandatory traversal and liveness are present; audience divergence remains SC64-03 |
| TE-R09 | Partial/open | Derived/authored split and erasure obligations are specified; R64-04 remain |
| TE-R10 | Defeated for target typing / dependency ownership | C §§5.3/5.5/9.11 have typed judgment targets and model/definition/condition dependencies; new applicability gap is SC64-01 |
| TE-R11 | Open | Typed inference and no ordinal arithmetic are retained, but R64-01/02 are concrete remaining propagation gaps |
| TE-R12 | Defeated within stated product limits | D1 F-39/F-41, C §9.13 and D-45/D-55 prohibit person proxies and author-assessment lists; manual compilation and detector misses are disclosed |
| TE-R13 | Partial/open | Uniform signed/anonymous independence rule defeats count differencing; conflict outcome oracle remains SC64-02 |
| TE-R14 | Partial/open | Recusal, replacement, pending appeal and opening-front-end appointment are present; SC64-02 remains |
| TE-R15 | Defeated as an efficacy overclaim | C §7.7 says “help investigate” and names weak detection regimes; no measured security claim |
| TE-R16 | Defeated in architecture contract | C §8.6/§14.2 provide quotas, refusal before acknowledgement and reserved space; scale/cost remain unmeasured |
| TE-R17 | Partial/open | Clause-level reconciliation exists; SC64-03, R64-04 and inherited exchange/terminal-warrant decisions remain |
| TE-R18 | Defeated in sequence | Slice 2 contains impact obligations and decision integrity; anonymity starts only in Slice 3 |
| TE-R19 | Partial/open | Contract checks precede studies and E5 is narrowed; new challenge cases and T98 repair must join the executable oracle |
| TE-R20 | Defeated for original history overclaim | D1 F-31/C §9.9 pin rules/projections and disclose deletion/restore gaps; R64-04 bounds recovery completeness |

### 4.2 Same-family review of 6.1: every finding

| Finding | Status | Operative basis / residual |
| --- | --- | --- |
| SC-R1 | Defeated for typo revisions | D1 F-3a, C §6.10 carry objections; do not infer audience closure from this |
| SC-R2 | Defeated for undefined effectiveness | Definition 6.0 and C §7.6 separate inquiry standing from project-memory admission; R64-01/02 are further gaps |
| SC-R3 | Partial/open | Distinct anonymous role, sealed operational area, sealed edges and pseudonymous assignment exist; SC64-02/03 remain |
| R-01 | Partial/open | Ordinary observation/premise endpoints were added; SC64-01 is its new tool/rendering sibling |
| R-02 | Defeated for original routes | Concurrent positive/negative route assessments show disputed; converse step alone does not destroy an independent route |
| R-03 | Defeated | D1 F-31/C §9.9 pin projection version |
| R-04 | Defeated | D-50 and derived late delta permit commit without an objection-based refusal |
| R-05 | Defeated | Awaiting versus complete signatures are explicit |
| R-06 | Defeated for specified substitution | Outgoing-owner attestation/admin fallback and operator registration disclosure; no anonymous policy-owner write |
| R-07 | Defeated for core-refusal issue | C §6.9 labels sole uninstrumented backing; T79 now agrees. Evidential selection still needs the policy owner |
| R-08 | Defeated | Historical applicable set and late delta are derived, not editable decision fields |
| R-09 | Partial/open | Critic-side grounds, equal timing and generic words exist; SC64-02 defeats the absolute outcome guarantee |
| R-10 | Defeated | Appointment belongs to the opening front end; operator registration and appointment are visible |
| R-11 | Defeated | Review-owned budget charged per pseudonym, not the sealed person's ordinary quota |
| R-12 | Defeated for renderer discretion | A §11.5 enumerates participant fields; no permission for arbitrary extra fields |
| R-13 | Defeated for silent decision removal | C §12.3 restricts marker-free removal; decisions/resolutions excluded |
| R-14 | Partial/open | Recovery includes restrictive controls/access/markers; R64-04 remain |
| R-15 | Defeated | Accountability renderings exempt from de-attribution; presentational limit disclosed |
| R-16 | Defeated | Uniform preview sentence replaces unseen-dependent counts, including T84 |
| R-17 | Defeated | Author search omits assessment values; a work's assessment appears on opening that work |
| R-18 | Defeated as an overclaim | Self-declared subject_kind and fallible backstops are explicitly a partly normative guard |
| R-19 a–m | Defeated or explicitly deferred | Conditions/ranges/slices/targets/citations/corpus term/surface marks were repaired; judgment-on-judgment subitem k is deferred. R64-05/06 identify current wording defects separately |
| R-20 | Partly adopted, no blanket closure | Deferred judgment basis removed, persistent assisting agents removed, annex split made; reported/recorded distinction reasonably retained; §7 below names remaining reductions |

### 4.3 Same-family review of 6.2: every finding

| Finding | Status | Operative basis / residual |
| --- | --- | --- |
| S62-1 | Defeated for automatic resolution on withdrawal | D1 F-3b leaves O unresolved on marker/question page; it need not automatically recognize a fresh restatement as identical |
| S62-2 | Defeated for published-versus-operational placement | A splits published review-scope records from protected operational records; the area is outside scope-management APIs |
| S62-3 | Defeated for the missing-premise row | Premises not established is explicit, with positive/negative per assessment kind; R64-01/02 challenge additional meanings |
| F62-01 | Defeated | Same-assessor supersession only; another assessor remains a concurrent head |
| F62-02 | Defeated | D-64/F-8/submit_sealed refuse anonymous judgments |
| F62-03 | Partial/open | Exact condition identity or explicit comparability judgment makes Slice 2 computable; R64-02 covers disagreement |
| F62-04 | Defeated for cross-scope impossibility | D-69 counts premise-home judgments under the same ruleset identity and names the scope |
| F62-05 | Defeated for supersedes bypass | Same-conclusion steps and same-observation/target relations count as revisions |
| F62-06 a–e | Defeated | Validity default, version registration, exposure label, endpoints in A(K), sentence placement all present |
| F62-07 | Partial/open | Off-site synchronous log and restore gap disclosure are present; R64-04 limit the repair |
| F62-08 | Defeated | Late delta derived; no signed-revision mutation |
| F62-09 | Defeated | Owner change names pending decisions and re-evaluates as new revisions |
| F62-10 | Defeated at recorded-choice level | D-66 explicitly authorizes operator registration and displays its act; no claim to audit original conversations |
| F62-11 | Literal reason leak defeated; inference family open | Generic wording does not defeat SC64-02 |
| F62-12 | Defeated for omitted TCB/logs | D-67 adds front end/transport and pseudonymous operational logs |
| F62-13 | Defeated for closed-review orphan assignee | D-68 uniformly assigns pending/future obligations to review-scope curators |
| F62-14 | Defeated for sealed-edge omission oracle | Uniform exclusion and sealed-record count independent of actual lineage |
| F62-15 a–c | Defeated | Operational records remain sealed after signing, no persistent assisting-agent route, review manage held only by opening front end |
| F62-16 | Defeated for silent effective-judgment deletion | C §12.2 makes effective judgments live; T115 requires a withdrawal marker |
| F62-17 | Marker-reason case defeated; new payload tests required | Log stores reason classes; objection grounds/bases require the all-surface erasure evidence in R64-04 |
| F62-18 | Listed stale tests defeated | T79/T84/T86/T100/T105/T13 now match repaired contracts; R64-05 is a separate inherited oracle mismatch |
| §3.6 a–l | Listed defects substantially repaired | Registration right, validity field, lineage heads, reserve capacity and range wording are present; R64-06 identifies the remaining parent-reference sibling |
| §3.7 items 1–11 | Partly adopted | History/consolidation/concept moves and derived delta are real; further simplification is §7 |

### 4.4 Mathematics same-family review: every finding, respecting the separate gate

“Hook repaired” below is only a check of the core/parent obligation. “Separate” means the full mathematics or SCIRE repair is **not reviewed here**.

| Finding | Disposition in this review |
| --- | --- |
| SM-1 | Partial/open: divergence is now an impact cause (D-74/F-32), but ordinary objections to T/L still miss decision applicability (SC64-01); async/recovery qualification remains |
| SM-2 | Parent hook repaired: carried conditions in Definition 2.7/§6.1; full mathematics adequacy separate |
| SM-3 | Parent structural hook repaired: per-conclusion path discharge, exclusive step membership, acyclic derivations and listed discharges; semantic validity remains assessed, not proved by reachability |
| SM-4 | Core human-inspection refusal and fidelity labels repaired; mandatory-brief behavior belongs to the separate mathematics review |
| FM-R01 | Separate: numerical-check/use-history semantics not accepted here |
| FM-R02 | Separate: effective inspection/designation interval and scope lifecycle not fully reviewed |
| FM-R03 | Separate; sampled §M.5 now distinguishes derivation verification, premises and conditions |
| FM-R04 | Separate; sampled expression context and conventions paths exist |
| FM-R05 | Separate / D2 boundary remains closed; no numerical-disagreement method was qualified |
| FM-R06 | Separate: mathematics assumptions/limitations not reviewed |
| FM-R07 | Hook identities now bind current core/parent; mathematics D1 text not reviewed |
| FM-R08 | Separate; sampled records no longer list faithful_under |
| FM-R09 | Separate: statement-kind/modality combinations not reviewed |
| FM-R10 | Separate; sampled brief subject is explicitly a derivation or result revision |
| FM-R11 | Separate: synthesis ordering not reviewed |
| FM-R12 | Parent hook repaired: F-20 records project roles as membership, not inferred quality |
| FM-R13 | Partial/open: target kinds and route challenges added, but F-6 incomplete (SC64-01) |
| FM-R14 | Core hook repaired: §7.6 inquiry ruleset covers fidelity/inspection with restrictions |
| FM-R15 | Core hook repaired: typed record/binding/tool operations and person-only designation; complete mathematics lifecycle remains separate |
| FM-R16 | Structural hook repaired: one derivation per step and cycle refusal; no claim that structural checks establish valid deductions |
| FM-R17 | Core hook repaired: exactly four annex kinds, model folded into symbol context |
| FM-R18 | Separate; sampled §M.6 cites tool checks/renders in judgment bases instead of misusing evidence relations |
| FM-R19 | Meaning-family hook repaired in §5.5; full binding confirmation/impact behavior separate |
| FM-R20 | Separate; core fidelity authorship fields do not by themselves qualify inference self-assessment labels or mandatory membership |
| FM-R21 | Separate; T116/T117 and extended T98 add core cases, but no TM suite was executed or fully reviewed |
| FM-R22 | Separate; sampled tool record offers image/lock identity or description-only label |
| FM-R23 | Core hook repaired: D-77/register_tool specify and display the operator act |
| FM-R24 | Owner choice recorded in D-76; deferred parsing/dimensional screening not reviewed |
| FM-R25 | Core hook repaired: parses and screening cues explicitly on deletion surfaces |
| FM-R26 | Separate: SCIRE extension v0.2 bindings not reviewed |
| FM-R27 | Separate: SCIRE role-table behavior not reviewed; D-73/D-78 recorded choices alone are not its qualification |
| FM-R28 | Separate: no seeded-error study design or statistical analysis accepted here |
| FM-R29 | Separate: SCIRE qualification/travel rule not reviewed |
| FM-R30 | Separate: script/artifact execution path not reviewed |
| FM-R31 | Separate: brief time-estimate removal not reviewed |

### 4.5 Reconciliation same-family check A.11: each item and its remaining open rows

| Earlier item | Current disposition |
| --- | --- |
| U1 | Partial: restrictive-control recovery is present; R64-04 remain |
| U2 | Partial: listed controls and sealed-store consistency are required; payload/dependency closure remains |
| U3 | Off-site RPO-zero log supplies the missing durability condition; actual atomicity/outage proof unexecuted |
| U4 | No-payload-survivor invariant restored as DL2; R64-04 requires explicit surface evidence |
| U5 | Input-manifest fields restored in §5.4 |
| U6 | Endorsement revocation restored in A3, §13 and T20 |
| U7 | AC4/T51 restore no-lasting-rights and admin-sharing limits; implementation enforcement untested |
| U8 | Uniform unseen-dependence preview sentence, no hidden count |
| U9 | §7.4/T111 union tags for UPMS-derived representations |
| U10 | §13 applies traversal failure at commit and use; no independence from missing ancestry |
| U11 | §11.4 protects access-record deletion from ordinary cascade/curate |
| U12 | §12.5 permits redaction erasure obligations; default authored-descendant exception remains explicit |
| M1 | Whole-event/subject discovery explicitly includes redaction replacements |
| M2 | §12.4 contains unknown coverage and names independent sources |
| M3 | Purge-controller minimization restored |
| M4 | Backup never serves recall; restore audited |
| M5 | Sensitive links stripped after the last descendant; opaque metadata remains protected |
| M6 | Missed live-purge target yields purge_failed, never false success |
| M7 | §13/§14.2 reserve space for restrictive controls/recovery log, not only barriers |
| M8 | Manifest-commit failure forbids provider submission |
| M9 | T43 positive fidelity-endorsement case restored |
| X1 | Own-record/oversight entitlement restored in AC1 |
| X2 | Changes are intentional scope reductions, not unchanged clauses: D-24 removes runtime/requirement closure, D-48 changes scientific freshness. AC2/§8.2 still require current recipient checks at release-record commit, including oversight changes; H1 reporting alone is not authorization, and §13 still refuses unsafe use. No old full-runtime fence is claimed |
| X3 | No surviving-descendant counter requirement inferred; it is an implementation choice if H1/§11.2 hold |
| X4 | Pending fence and purge deadline semantics are now explicit; exact old intermediate state name need not return |
| X5 | Declared mixed-policy splitting need not survive the first-product exclusions and capture limits. “Journals”/all-content-bearing surfaces must include actual WAL/redo/log replicas in D4's inventory; omission of the acronym cannot exempt them. R64-04 requires the newly payload-bearing log in the surface inventory |
| X6 | X/R on import is intentional and correct for historical source class; assessment changes usability, not capture history |
| X7 | Removing runtime egress rights is a D-24 boundary change; UPMS release records/barriers and stale-writer fencing remain |
| X8 | §10.6.2 and T50 explicitly retain/find sharing copies after original deletion; old expiry semantics retired under D-25 and publication-waiver semantics under D-24. No descendant-containment claim transferred |
| X9 | Scenario range updated to T117, with R64-05's distinct semantic drift still open |
| X10 | A route exists: admin-mode ownership transfer under §7.3.6, then authorized deletion, or administrator acting on a verified external request. §7.3.7 is not standalone authorization to delete any departed user's scope. Clarify that cross-reference in the next revision; no unrestricted offboarding erasure inferred |

SC-61 (curator removes dissent) is defeated for normal-operation silent removal by attributed markers, but remains qualified by audience and recovery issues above. SC-62 (identity-bearing operational metadata) has substantial explicit placement and logging repairs; that does not close the conflict-output oracle.

### 4.6 SCIRE transfer limits

The packaged SCIRE re-review is an input, not a newly reviewed SCIRE candidate. Its original verdicts are unchanged. The following are bounded transfer assessments; **none claims that UPMS acceptance accepts SCIRE**.

| SCIRE item | UPMS disposition / boundary |
| --- | --- |
| SC-41 / V4-01 | F-3/F-4 and resolution decisions preserve disputed resolution visibility, subject to SC64-03 |
| SC-42 / V4-02 | Still materially applicable in the default profile through audience changes; SC64-03. It cannot be assigned solely to deferred strict containment |
| SC-43 / V4-03 | Full derivative containment intentionally excluded by D-24/D-27; UPMS provenance has explicit coverage limits; strict profile remains unreviewed |
| V4-04 | SCIRE must specify mandatory basis versus optional source review; storing a basis reference is not proof it addressed objections |
| V4-05 | Consequential-use scope/exemptions remain SCIRE; R64-03 also needs a D1 recording/reliance distinction |
| V4-06 | F-6 supplies bounded identity-based coverage; SC64-01/03 prevent full transfer closure |
| V4-07 | Attributed reassessment and traveling qualifications are explicit in F-33/F-34 |
| V4-08 | Only UPMS releases/processing are covered; no global clean-runtime inference |
| V4-09 | Two-sided strict-profile evaluation remains deferred; blind exclusion still needs measured over-exclusion cost |
| V4-10 | Processing extent is not extraction recall; §10.3 gaps and §15.2 evaluation preserve that distinction |
| V4-11 | Core mediates only its own commits/releases; informal external reliance cannot be certified |
| V4-12 | Statuses, uninstrumented labels and de-attribution restored; terminal argument/warrant meaning remains explicitly open. Carried conditions improve mathematical termination but do not settle every inference type |
| V4-13 | Snapshot qualification is as-of, later changes unknown |
| V4-14 | Materiality, overlap and decision permission stay with SCIRE; concrete front-end specification required before Gate 2 |
| V4-15 | Versioned SSDS exchange vocabulary remains open; no enumeration adopted by this review |
| V4-16 | One relation store and derived eligibility reduce duplicate ownership; SC64-01 shows two applicability descriptions still diverge |
| V4-17 | SSDS remains external authority; no receiving guarantee is manufactured |
| V4-18 | Old source-owner disclosure manifest is not a first-product requirement after D-24; release/processing manifests remain |
| V4-19 | E4 includes effort/blocks/overrides; real study limits and behavior unmeasured |
| V4-20 | Exact signatures and historical gaps are addressed; derivative erasure now follows D-41 rather than the old containment promise |

## 5. Owner decisions and readiness boundary

Owner records are treated as the product choices supplied for this review, with their own provenance limits. Their account of the original conversation was not independently authenticated. They explicitly accept **no candidate text**.

| Decisions | Review disposition / required next action |
| --- | --- |
| D-37/D-38/D-50/D-64 | Keep no anonymous veto, attributed judgments and no core objection-based refusal; repair applicability under SC64-01/03 without moving scientific policy into the core |
| D-39/D-48/D-69 | Keep separate scientific effectiveness and deferred judgment-on-judgment. Decide R64-01/02's remaining predicate/applicability semantics |
| D-40/D-49/D-52/D-66/D-67/D-68 | Keep explicit service/transport/operator boundaries and uniform assignments. **New owner decision needed:** accept the bounded conflict-existence disclosure in SC64-02, or change/withhold the conflicting guarantee |
| D-41/D-44/D-46/D-53/D-54/D-63/D-65 | Keep explicit erasure obligations, accountable markers, dissent preservation and restore coverage. Make the replicated dissent-payload lifecycle explicit in the D4 inventory and evidence (R64-04), keeping the already-required all-surface erasure contract. Resolve audience continuity in SC64-03 |
| D-42/D-43/D-45/D-56 | Keep staging and separate annex gates. No sealed identity collection before qualification; no restricted-data containment promise in the first product |
| D-47/D-51 | Revision carrying and signature completeness are materially specified; no owner reversal needed |
| D-55 | Author-search restriction and residual are coherent; no owner reversal needed |
| D-57–D-62/D-70–D-72 | Core hooks change D1 premise/discharge meaning, and are now located in the parent. Keep carried conditions/path-scoped discharge; full mathematics review remains separate |
| D-73–D-78 | Core restrictions/registration are present where sampled; this is not acceptance of mathematics or SCIRE implementations |
| Earlier pending choices | C §18.1's blanket statement that D-8/D-9/D-16/D-18/D-19 were never confirmed is stale against the packaged D-37–D-46 record §2 and change history A.12. Do not ask the owner to repeat those already recorded confirmations. Resolve only genuinely outstanding D-13/D-17 implications, C6-6 acknowledgement, terminal-warrant/type-specific rules, and SSDS vocabulary as applicable |

The next candidate needs owner adjudication of the guarantee tradeoffs above, D1 closure of the applicability/route questions, and a new hash-bound independent review. Technical review cannot accept the surfaces marked beyond the requested deliverable in D1 §11 and C §17.2; only the product owner can bind those surfaces.

Gate 0 completion also needs the named pilot languages/profile, a bounded D4 specification and executable evidence specification, and bound runtime/storage/KMS/restore feasibility as C §16 requires. This review did not supply them. These are open gate obligations, not reasons to perform unauthorized implementation now. Gate 2 still requires SCIRE's concrete policy contract, including overlap, materiality and partial coverage.

## 6. Requested interaction checks

| Interaction | Result |
| --- | --- |
| Withdrawn-target objections accumulate | They may grow until explicit withdrawal/rebind/resolution or quota exhaustion. D-25/D-63 intentionally disallow silent expiry. §8.6 quotas, backpressure and pageable lists bound individual operations; they do not bound lifetime human attention. Measure withdrawn-objection queue size, continuation use and resolution effort in E1/E4/E5. Not an independent contradiction requiring automatic deletion |
| Rebind to a restatement | Author-only rebinding is not a new adversarial power over the objection's substance: that author can already withdraw it. Preserve old target/decision history, require endpoint authority and audience validation on rebind (SC64-03), and label identity/equivalence as an attributed assertion. Do not introduce a semantic-equality detector as authority |
| Restate a derivation to hide conditions | Within a declared derivation, per-conclusion reachability and condition compatibility block silent discharge. Across a newly asserted restatement, the system cannot infer honest equivalence; F-1's modality rule alone does not prove condition preservation. Require exact linked conditions for a machine-supported transfer or leave it an unassessed attributed restatement. Add TM/T98 siblings spanning derivation boundaries; R64-01/02 must close first |
| Off-site log changes failure behavior | Yes: protected commits depend on off-site durability. No acknowledged canonical-only control or false recovery success is permissible. R64-04 specifies the discriminators; no measured latency/RTO claim follows |
| Mathematics hooks change old meanings | H3 materially changes what needs an established judgment and how discharge works; it is now explicitly D1-owned. New target kinds also need the F-6 closure in SC64-01. H1/H2/H5–H7 otherwise have bounded record/role hooks; H4's checking semantics remain separate |
| Front-end boundary | Keeping decision permission/materiality in SCIRE is correct. Structural expected-revision/signature checks remain core integrity. Partial-coverage policy must not be “repaired” as an objection-based backend veto |
| Deletion/restore | Ordinary derived barriers, redaction replacement and authored-descendant exceptions are explicit. Complete replicated-payload erasure and minimum recovery closure are not yet established (R64-04) |
| Sealed identities | Counts and cross-mode independence are now uniform; conflict outcomes remain secret-dependent. No blanket sealing PASS |

## 7. Simplicity and family-level repair

The history shows repeated attempts to close the same boundaries: objection revision/withdrawal/endpoint visibility, sealing side channels, and recovery retention. These are **candidate repair iterations**, not proven recurrence after an accepted repair; no candidate architecture is accepted-current.

Do a bounded shared-owner pass before another list of local exceptions:

1. **One applicability definition.** Define the required objection neighborhood once in D1, including the 6.4 tool/rendering dependencies, and derive standing, decision applicability, mandatory lists and late deltas from it. Keep the declared coverage boundary. Remove duplicate endpoint prose that can diverge.
2. **One honest sealing release contract.** Separate protected mapping/operational records, pseudonym-visible data and deliberately disclosed appointment predicates. Replace repeated absolute “nothing depends” statements with the single owner-approved guarantee. No new anonymization wrapper or parallel identity registry is warranted.
3. **One recovery/deletion ownership decision.** The recovery log is now a payload-bearing recovery subsystem, not merely a “small” tombstone list. Use the existing canonical payload lifecycle and explicit replica inventory for its content. Compare this with recovering the necessary canonical subset at zero RPO before choosing more synchronized representations. Preserve D-65 unless its owner changes it.
4. **Remove cold history from the core's operating path.** C §1's drafting chronology and most of §18.2/§18.3 can be replaced by short bindings to frozen history and a table of current decisions/open obligations. D1 Appendices B/D/E/F are change history; move them to a companion in a new candidate while retaining live normative Definitions/F-rules. This is a proposal for the next revision, not permission to mutate frozen inputs.
5. **Keep the useful distinctions.** Do not merge reported/recorded merely to save a status: self-entered versus externally reported decisions differ in attribution and exposure. Do not remove deterministic dissent lists, explicit restoration gaps, condition propagation or negative-information checks to shorten the text.
6. **Keep deferred machinery deferred.** Channel track records, adapters, persisted prose and strict containment need their separate measured gates. The first useful inquiry should establish faithful records and bounded projections before adding them.

No new permanent census, evidence registry or process layer is requested. The regression ledgers here are review evidence, not a replacement authority.

## 8. Evidence, inspectability, selection and limits

**Executed.** Local reads/searches, Git-state inspection, SHA-256 validation of all 25 manifest entries, byte comparison of all 21 packaged UPMS files against their originals, changed-range comparison of D1 1.3→1.4 and core 6.3→6.4, and constructed documentary trajectories. Long tool outputs sometimes truncated; all three subjects were covered through smaller reads, and unreviewed/selective inputs are explicitly identified. A range diff is not a fresh review of a predecessor.

**Not executed.** No standing evaluator, database, capture adapter, attack test, purge/restore run, TM/T test suite, benchmark, user study, numerical method, model invocation or deployment. Planned cases are UNEXECUTED. A documentary counterexample is not an observed exploit or an incidence estimate.

**Scientific findings / null envelope.** This prepares evidence for a human design gate. The material findings are exactly the three Serious Challenges and six other findings above, including their coverage limits. The materiality criterion is whether compliant-looking execution could misstate evidence/applicability/dissent, disclose a protected identity, or fail an explicit custody guarantee. No empirical scientific result was produced, run or reinterpreted. Scientific adequacy, human comprehensibility, error rates, social behavior, performance, storage economics and operational security remain unexamined. The report is an AI asserter's documentary evidence.

**Selection.** One reviewing agent and one adaptively developed review record; several constructed sibling trajectories and proposed repairs were considered. No analysis/model/parameter variants, held-out dataset or selected empirical survivor exists. Earlier drafting/review/search histories were not reconstructed beyond the bound records and cannot establish independence or a total trial count. This is falsification reasoning, not preregistered confirmation.

**Authority/tension search.** No accepted UPMS D1/D2 authority exists. The bound candidate/review/owner-decision lineage, A.11 reconciliation and selected SCIRE objections were searched for recorded tensions; their statuses are preserved separately in §4. No external/native issue tracker or original owner chat was accessed, and no accepted SSDS authority was relied on for a consequential judgment. No current authority is inferred from main or from a document's presence. PEM is stated uninitialized by AGENTS.md; no PEM was created or updated.

**Independence limits.** Different family from the Claude authors, but not blind: this review read their histories, recommendations and earlier OpenAI-family findings. Shared SSDP sources and the earlier proposal-review framing can anchor it. A short persistent-memory lookup informed hypotheses about lineage/freshness and authority separation; every substantive finding was rebound to the current hashed texts, and no old verdict was used as proof.

**Record retention and product surfaces.** This requested review retains its source identities, counterexamples, proposed repairs, every requested prior-finding disposition and explicit coverage. It changes no product retention/projection behavior. D1 §11 and C §17.2 state the material record, readers and routine questions and mark theory inspection surfaces beyond the deliverable; those scope markings are retained. Technical review does not accept beyond-deliverable surfaces. No extra inspectability product is proposed here.

**Persistence and mutation boundary.** This is the sole new repository artifact. Frozen candidates, reviews, handoff, workplan index and history remain unchanged. The README's delivery request is a new review branch and a commit containing this file only. No push, pull request, merge, tag, implementation, ratification or archive is authorized by this record.

**Revisit condition.** Review a new hash-bound revision against each trajectory in §§1/3 and each open ledger row, then check its applicability definition, release disclosures and replicated-payload lifecycle across their full affected consumer sets. A change map saying “repaired”, a passing proxy or a favorable aggregate study cannot close these contracts.

## Appendix A. Input identity and coverage ledger

All paths in this table are relative to workplans/active/UPMS_Review_Handoff_Candidate_6_4/. All 25 entries passed SHA256SUMS; all 21 UPMS originals matched their packaged copies byte for byte. The three SCIRE copies were checked against the package manifest, not against a remote branch. The request is the remaining entry. Hash identities do not validate source assertions or acceptance.

| Packaged path | SHA-256 | Actual coverage |
| --- | --- | --- |
| inputs/UPMS_Architecture_Manual_Candidate_6_3_Change_History.md | c2a7ded8dd9198a92989c81ca8216718b7a3af8ff2875bf48cce60c40775e571 | A.8, A.11 and A.12 read; other portions searched/selected |
| inputs/UPMS_Architecture_Manual_Candidate_6_4_Change_History.md | d7501e2ea209e8710ada727c0ea4c2f3e3d698b138708c52aff2c6116e9c40b3 | Read in full (A.14) |
| inputs/UPMS_Architecture_Manual_Review_Candidate_5.md | 406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750 | Selected: §12, §13, §15 invariants; heading/identity searches elsewhere |
| inputs/UPMS_Architecture_Manual_Review_Candidate_6_2.md | 0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc | Hash and original-copy equality only; not substantively read |
| inputs/UPMS_Architecture_Manual_Review_Candidate_6_3.md | e6c02b0a60eead112b2a0ef78b07ff849e0006c71df25e60aeefa24686590a44 | Changed-range comparison to 6.4 only |
| inputs/UPMS_Candidate_6_1_Same_Family_Review.md | f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592 | Read in full |
| inputs/UPMS_Candidate_6_2_Same_Family_Review.md | 255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9 | Read in full |
| inputs/UPMS_Mathematics_Package_Same_Family_Review.md | ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0 | Read in full |
| inputs/UPMS_Owner_Decisions_2026-11-03.md | c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e | Read in full |
| inputs/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md | e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485 | Read in full |
| inputs/UPMS_Owner_Decisions_Math_Review_2026-11-03.md | 161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f | Read in full |
| inputs/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_3.md | 4c0c81d1e62b9dbcf09c874e6ef41f626458c60c6d716e7dfba0793fa7a69d77 | Changed-range comparison to 1.4 only |
| inputs/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md | 0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc | Read through §2.3, including decisions; headings/searches later |
| inputs/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md | cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1 | Read in full |
| not-under-review/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md | e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51 | Hash/original equality only; deferred |
| not-under-review/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md | f328d51e4e1422cf603b2059fcb9795e01720832ea858d32df34b2fe6bd5c5c7 | Hash/original equality only; deferred |
| not-under-review/UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md | 71083419f4b9d4091153d7fd86ec32046081eca1f295d9f31e0b867015f51a58 | §M.0–M.3 and §M.5–M.6 read; selected §M.4/§M.7; tests searched; no full verdict |
| not-under-review/UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md | d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e | Hash/original equality only; separate review |
| scire/SCIRE_Conceptual_Proposal_v0.4.md | 181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002 | Selected searches/excerpts on objections and conditional evidence; not full review |
| scire/SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.2.md | c9ce9a0ed1a72bf76cf165a669db9e36d658b9b7704afacb096682855cf1cb79 | Hash only; separate review |
| scire/SCIRE_v0.4_Re-Review.md | 2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e | SC-42 and findings ledger §5 read; headings elsewhere; no new SCIRE verdict |
| under-review/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Anonymous_Review.md | e5becbd510ec3205a5b241062c3bdca03a2dcbf90d6f803365f994fef51738cb | Read in full; under review |
| under-review/UPMS_Architecture_Manual_Review_Candidate_6_4.md | 3c9844db1c2b99094c882f3f2bcb4e6d8cdbf9f7f9df6ab02f68f962729b2e09 | Read in full; under review |
| under-review/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_4.md | 5e2b67f97b919d6612db6ed22bd6a3c7456b2be7141e4ef634bb3c2416afbb8f | Read in full; under review |
| UPMS_Review_Request_Candidate_6_4.md | b7bb91d81d86bd04cb40e782a4f6121fb2209855a3d6f2fe1ee95de1fbea98c5 | Read in full; task brief |

Additional local context identities (not extra review subjects):

| Path | SHA-256 | Coverage |
| --- | --- | --- |
| AGENTS.md | 081ae30487a937ff8b6f45d4bf75cb3f7e5fa289387a8298b8a59253ae7559de | Read in full; project instructions |
| workplans/active/UPMS_Review_Handoff_Candidate_6_4/README.md | 02dcdfb241455dbce849dd1b01c6ffa855d7c513079774bc05dea6dd7be98840 | Read in full; authorized review/delivery scope |
| workplans/active/UPMS_Review_Handoff_Candidate_6_4/SHA256SUMS | f966801e1aa2a5cf44b4357bda80a34acce25a96b894d01569f5b2dc8a58e205 | All entries verified |
| workplans/README.md | 1ccf2ea75d24f9367c4aeb738deb836b868a70a5667a9a102746c56bcde84c61 | Selected index/lifecycle/current-status content; not full substantive review |
| history/SEMANTIC_EVOLUTION.md | 5ecd5c7c2fcf09662d3fe2f538bd1c637103b9125ef24a1473cc64598b842193 | Selected candidate/decision evolution; no accepted authority inferred |

Method sources were the installed SSDP 7.2.1 scientific-formulation/software-design entrypoints and triggered formulation, architecture, authority/Challenge, workflow, semantic-definition, evidence, convergence and PEM references. They set review method, not UPMS product semantics. No specialist skill grants acceptance, a new product commitment or a change to the supplied candidates.

## Appendix B. Primary source locators

Line numbers refer to the exact subjects bound at the start; they are navigation aids, not substitute authority.

| Finding | Primary operative locations |
| --- | --- |
| SC64-01 | D1 F-6, lines 181–195; route challenge row, line 317; C §9.9, lines 829–834; mathematics annex §M.6 |
| SC64-02 | A §7.8, lines 12 and 17; A T104, line 79; C SE1, line 1333 |
| SC64-03 | C §5.11, line 439; own-record entitlement, line 633; C §10.3 response filtering; D1 F-7 |
| R64-01 | D1 Definition 5.1; positive/negative, line 308; assessed-sound, line 321; F-28, line 347 |
| R64-02 | D1 Definition 2.8; premises/compatibility, line 310; disputed and assessed-sound rows, lines 318–321 |
| R64-03 | D1 F-3b; C §6.9 checks 1–6 and recorded/validated distinction |
| R64-04 | C §12.3 all content-bearing surfaces; §12.4 recovery log, no-payload survivors and T13/T112 |
| R64-05 | C T98, line 1439, versus T109, line 1445, and §9.9, line 830 |
| R64-06 | C §1.4 versus §1.1's D1 1.4 hash |
