# UPMS Candidate 6.1 and D1 Candidate 1.1 Review (Same-Family)

3 November 2026 · requested by the product owner (Sam) · reviewer and asserter: Claude (AI), model Opus 5.5 (`claude-opus-5-5`), in a Claude Code subagent session. No further agents or tools beyond file reading, search and hashing were used.

**Governing method:** SSDP 7.2.1. No task or workplan assigns a `protocol_version`. The software-design skill was used for the D3 candidate and the scientific-formulation skill for the D1 candidate.

**Independence.** I am the same model family and the same model (Claude Opus 5.5) as the author of every text under review, of the proposal and of every earlier UPMS review except Codex's. This review **cannot be the independent falsification** that `AGENTS.md`, candidate 6.1 §1.3 and §16 (Gate 0) require. Shared blind spots are likely, so a finding I missed is not evidence that it is absent. I did not see the author's reasoning, only the files. I treated change maps (candidate 6.1 Appendix A, D1 Appendix B), the "repaired" column of A.8, §18.3's dispositions and the author's recommendations as claims to test, not as evidence. I have not softened findings on account of being same-family.

## 0. Bound inputs

All hashes were computed with `sha256sum` on the working tree at UPMS commit `468bdda224b13ea9a5e89fa3c4c0db7c70024758`. Every hash named in the request matched.

| File | SHA-256 | Role here |
| --- | --- | --- |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_1.md` | `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a` | **Under review** (D3, "C6.1") |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md` | `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | **Under review** (D1, "D1") |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction, D-20 to D-36; not read directly (see §8) |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex findings SC-TE01 to SC-TE05, TE-R01 to TE-R20 |
| `workplans/active/UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Owner decisions D-37 to D-46; untracked in Git when read |
| `workplans/active/UPMS_Review_Request_Candidate_6_1.md` | `d94d7c62b94b846e4e900c9d71d67cadf83fa82b46f1f3d0188ed244cd419a8c` | Request; §2 and §3 followed |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6.md` | `1b125d2c73aa8f78ebb28e549ef0a3a9b363b4581e0a0c4f8dadd72a8ca87062` | Predecessor, used only to diff |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md` | `65b736253c7bcb7e8a0f1d6dafc0251cc59adfb56dfd310cf336ad03766d30fc` | Predecessor; not diffed |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base; not read |
| `workplans/active/UPMS_Candidate_4_Same_Family_Review.md` | `71f424c657ec6144823012623bae9b3fb3bf82ae20009a7b66c22fd42974970c` | Format only |

Owner decisions D-37 to D-46 are treated as owner choices. I do not re-litigate them for preference. Where one contributes to a material failure, I say so and give the trajectory. Where the reviewed texts still say "pending" or "author's recommendation" for something D-37 to D-46 decided, I read it as decided (owner record §1) and do not count the wording as a defect.

## 1. Verdicts (same-family interim)

| Text | Verdict | Blocking reasons |
| --- | --- | --- |
| D1 formulation candidate 1.1 | **NO-PASS** | SC-R1 (a `superseded` resolution has no defined cause, so revising the target resolves an objection); SC-R2 (route soundness depends on "effective" judgments with no D1 definition fit for scientific use); R-01 (the applicable set and route status miss objections to observations and to premises of cited routes) |
| D3 architecture candidate 6.1 | **NO-PASS** | SC-R1, SC-R2 and SC-R3 (the sealing boundary follows "session", which §8.2 allows to merge, and leaves placement, ancestry edges and obligation assignment outside the seal); R-04 (the commit-time applicable-set check gives any objector, anonymous included, a procedural block); R-14 (restore can bring back revoked access and lose access records and deletion markers) |

Both texts are much better than the proposal Codex reviewed. Most of the Codex findings have real body-text repairs (§4). The blocking items are new trajectories through the repairs, plus two D1 gaps that the repairs depend on.

## 2. Serious Challenges

### SC-R1 — Revising a target silently resolves every objection to it (D1, then D3)

**Owner:** D1 Definition 2.5 and F-3 (objection semantics), then D3 §6.10. **Texts:** D1 Definition 2.5, F-3, F-6, F-7, F-21, F-28; C6.1 §5.11, §6.10 ("Resolution: superseded"), §9.9, §12.2, TE-04, MV1.

D1 Definition 2.5 lists `superseded` as a resolution, and `unresolved(O) ⇔ r(O) is absent`. F-3 attaches decision fields to `resolved-by-assessment` only. D1 gives `superseded` no cause, no authority and no visibility. C6.1 §6.10 fills the gap: "Resolution: superseded — the core, when the target is withdrawn or replaced — resolved for the old target; it is not carried to the new revision automatically, and the front end may re-raise it."

**Trajectory.**
1. PI P records hypothesis claim κ. Critic C records objection O against κ: an unresolved, material counterexample. O travels with every decision whose basis cites κ (F-7, TE-04).
2. P revises κ to κ′, fixing a typo. This is an ordinary `write` on P's own claim (§6.3).
3. The core marks O `superseded`. O is now resolved (Definition 2.5), so it no longer satisfies F-7's travel condition. It drops out of A(κ′), `has_open_challenge(κ′)` is false, the mandatory lists (§10.5.1, MV1) no longer carry it, and O is no longer live under §12.2, so it can be archived.
4. P records a finalization D citing κ′. A(D) contains no objection. If D is `validated`, its policy result's applicable set is empty, and the atomic check passes.
5. Every earlier decision D₀ that cited κ while O was unresolved also stops showing O in its current projection, because O is now resolved. Only `applicable_at_decision` and "as held then" retain it.

No signature, basis statement, dissent or exposure was required: the cost that F-3 and SC-41 attach to resolution is avoided entirely. D1 §10.2 names "a disputed resolution shown as settled" as falsifying. This is worse, because nobody resolved anything. F-21 already handles the analogous case for evidence relations (they become "under review" for κ′), but objections have no analogue. T73 tests only relations. No test covers this trajectory.

**Consequence.** Any author can clear dissent against their own claim at the price of a trivial edit. That defeats TE-04, MV1, F-7 and SC-41, the dissent-preservation core that SCIRE exists for.

**Bounded repair.**
- **D1.** Define `superseded` narrowly: the target was retracted or withdrawn with no successor revision. On a revision κ → κ′, every unresolved objection to κ is **carried** to κ′ with the state "carried, pending re-examination". It stays unresolved, travels and stays live until (a) its author withdraws it, (b) a `resolution` decision under F-3 states that κ′ no longer meets it, or (c) its author rebinds it.
- **D1.** A resolution on the old revision never removes O from the current projections of decisions that cited the old revision.
- **D3.** Change §6.10, §9.9 and §12.2 to match, and add a test: revise a target that has an unresolved and a disputed objection, then finalize on κ′. Both objections must appear on every projection.

**Confidence:** high that the text permits the trajectory. The only escape is reading "replaced" as excluding ordinary revision, and §6.10 uses "replaced" for exactly that case.

### SC-R2 — "Assessed-sound" depends on an undefined effectiveness that is either unreachable or ungoverned (D1, then D3)

**Owner:** D1 §6.1 (route status, well-foundedness), then D3 §9.3, §9.9, §14.2 and §7.6. **Texts:** D1 §6.1 ("effective judgments (fresh at `p` under the ruleset's freshness rule)"), §6.5; C6.1 §9.3 (the third paragraph: "the effective judgment must still match current scope epochs, rule assignment, validity interval and the maximum age bound … otherwise it is shown as evidence-only"), §9.3 (admission refused by ancestry), §7.6 ("other domains remain evidence-only until a domain ruleset is separately accepted"), §14.2 ("Required assessment age: at most 5 minutes plus exact current evidence epochs"), §8.2 (exposure ancestry), §9.10 and D-39.

D1 makes route status depend on premises **only through their effective judgments** and requires the route's own latest assessment to be "positive and effective". D1 says only that "effective" means fresh under the ruleset's freshness rule. C6.1 supplies the only freshness rule that exists: candidate 5's project-memory currentness rule, under which a non-fresh judgment "is shown as evidence-only". Read together, the two texts give three possibilities, and each fails:

1. **Effective = admitted and fresh under §9.3.** Then:
   - **(a)** §7.6 admits no scientific-domain judgment until a domain ruleset is separately accepted, and §16 schedules no such acceptance for Slice 2. So no route in the Slice 2 demonstration can ever be assessed-sound.
   - **(b)** The §14.2 age bound is 5 minutes. A premise judgment made yesterday is not effective today, so `has_sound_route` is false for every claim more than five minutes after its last assessment.
   - **(c)** The scope epoch advances on any new claim, statement or evidence relation anywhere in the scope (§9.3). In an active inquiry scope, every judgment loses effectiveness at the next unrelated commit. Slot-level invalidation is deferred past Slice 3.
   - **(d)** An agent assessor whose session received a question page or standing report is `exposed_to` it (§8.2). Its judgment is evidence-only for ever (§9.3), and in SCIRE that is the normal path.

   The standing projection is then empty in practice.
2. **Effective = fresh but not necessarily admitted.** Then the §9.3 firewall, which D-39 keeps as the governing rule ("judgments with a judgment basis are evidence-only"), has no effect on standing. A judgment kept evidence-only because its assessor read a standing report still drives `assessed-sound` routes downstream. That is the exact laundering Codex's SC-TE01 trajectory C names: "moving a calculation from a stored field into a view does not remove its epistemic effect". D-39's deferral then defers nothing.
3. **No status for "assessed, but no effective assessment".** D1 §6.1's table has no row for a route whose assessments all exist but none is effective. "Unassessed" says no assessment exists, and the other rows do not apply. A reader is shown nothing, or a wrong label.

**Consequence.** The central derived quantity of D1 (§1.2: "the standing of a claim at a position in history") is either vacuous or bypasses the admission rule the owner kept. E5 and the Slice 2 demonstration cannot meaningfully run on either reading.

**Bounded repair.**
- **D1.** Define effectiveness for scientific judgments separately from project-memory currentness: a judgment is effective at `p` when it is the head of its `(target, σ, ρ)` lineage, inside its validity interval, its bound target revision is current, and no review obligation is pending on its target. No wall-clock age bound applies unless the ruleset states one.
- **D1.** State explicitly whether evidence-only judgments contribute to route status. My recommendation: they contribute, labeled "assessed (evidence-only)", never as `assessed-sound`; `has_sound_route` counts only admitted ones.
- **D1.** Add the missing row "assessed, not effective (stale)".
- **D3.** Bind a Slice 2 theory ruleset, or state that Slice 2 shows only evidence-only standing. Make the 5-minute bound a project-memory current-state rule, not a standing rule. Specify target-level invalidation for the theory layer, or accept and measure the scope-wide staleness.

**Confidence:** high that the texts as written give no workable reading. Medium on which repair the owner prefers.

### SC-R3 — The sealing boundary follows "session", which can merge, and misses placement, ancestry and assignment (D3)

**Owner:** D3 §7.8 and §8.2. **Texts:** C6.1 §7.8 ("Anonymous-role sessions seal everything they produce"; "Who may assist"), §8.2 ("Session identity … Otherwise all of the principal's agent sessions count as one"; "Every later write from the same session … is `exposed_to` everything released to the session"), §5 common fields (home scope), §5.5 (ancestry), §7.3.8 (agent private and operational scopes), §9.11 step 2 (assignee), §12.3 (deletion-obligation assignee, who may delete), §6.10 (withdrawal, handling), SE1, T86 and T104.

SE1 promises that "every record an anonymous-role session causes is sealed" and that "nothing released depends on sealed attribution". Both are defined over sessions and over a closed list of fields. Five trajectories reach a sealed identity through the operative text.

- **A — Session merging (conditional on Gate 0).** Gate 0 may find that the bound Codex build cannot show separate model contexts. §8.2 then says "all of the principal's agent sessions count as one". The critic's own agent principal A (the assisting route allowed by §7.8) receives review package R in its anonymous-role session. Later, in its ordinary signed work, A writes note n. Under §8.2, n is `exposed_to` R, because it is the same session for provenance. Any review participant who can read R and n sees that A's signed note derives from the review package, and A's overseer is the critic. The sealed release record does not help, because the leaking edge sits on an unsealed record. The same holds for a human critic using one front-end session for both roles, since front-end views also get release records (§8.2) and nothing defines a front-end session boundary.
- **B — Placement.** The sealing list in §7.8 covers release, processing, quota and access records, `witness_principal`, owner and locator fields, submission logs and overseer links. It does not cover the **home scope**. A working note or checkpoint that the assisting agent's anonymous-role session writes lands somewhere. If it lands in A's private or operational scope, the scope's protected overseer grant (§7.3.8), which is a permission record and not something the session caused, names the critic. An administrator in administrator mode who reads A's scope sees a pseudonymous record there. If it lands in the review scope, every participant (`rw`) can read the critic's working notes. §7.8 does not say which.
- **C — Ancestry endpoints.** The sealed objection's `exposed_to` edges point to whatever the session read. If it read a draft in a two-member team scope, a member who can read that endpoint sees an anonymous objection derived from their team's private draft. That narrows the critic to one person. §8.2 releases provenance endpoints to readers who can read them, and §7.8 does not seal the edges themselves.
- **D — Assignment.** A retraction reaches an inference step or evidence relation written in the anonymous role. §9.11 assigns the review obligation to "the dependent's author, or a curator of its scope when the author has left". An erasure assigns deletion obligations to the owner, or a curator "where the owner has left" (§12.3). The assignment either names the sealed author, or switches to a curator exactly when the sealed author has left the organization. Either outcome is visible and depends on sealed attribution.
- **E — Lifecycle acts by the sealed author.** §6.10 lets "the objection's author only" withdraw, and the author or the target's author change handling. §12.3 lets an owner delete their own item. §7.8 says blocked text is "readable only by its author". Nothing requires these acts to come from an anonymous-role session. A critic who withdraws, deletes or reads their blocked text from an ordinary session produces an openly attributed control record or release record that names them.

T86 and T104 test sealed fields and released counts. None of them exercises A to E.

**Consequence.** D-33's promise, that critiques are sealed rather than unknown, fails through provenance and workflow paths the candidate itself keeps. The failure is unconditional for B to E and conditional on Gate 0 for A. TE-15 and SE1 are false as written.

**Bounded repair.**
1. Make the anonymous role a **distinct session type** whose releases never become exposure ancestry of a non-anonymous write, whatever the session-isolation result. If the bound integration cannot keep separate model contexts, offer assistance only through the temporary review-service session.
2. Drop the "critic's own agent principal" route (simpler, and see R-20). A persistent agent principal carries memory and an overseer grant that no sealing list can cover.
3. Home every record an anonymous-role session causes in a sealed per-pseudonym area of the review, readable only by sessions in that same role.
4. Seal the provenance edges of sealed records: core functions such as impact traversal and lineage exclusion use them, and readers see "sealed source".
5. Assign obligations on sealed-authored records to the pseudonym, delivered through the chair path. Never switch to a curator on the basis of the sealed author's employment state.
6. Accept withdrawal, handling, deletion and blocked-text reads of sealed records only from that author's anonymous-role session.
7. Extend T104 with A to E.

**Confidence:** high for B, D and E (direct reading). High for A given the Gate 0 condition the text itself names. Medium-high for C, because it depends on how "private source" renders to readers who can read the endpoint (§10.3 shows endpoints to them).

## 3. Findings

Severity: **Blocking** means repair before the affected contract is accepted. **High**, **Medium** and **Low** are as usual. Each finding names its earliest owner.

### 3.1 Standing, applicable set and projection

#### R-01 — Objections to an observation or to a cited route's premises never reach the decision (High; D1 F-6 and §6.1, then D3 §9.9)

**Location:** D1 F-6, §6.1 ("challenged"), F-28; C6.1 §9.9 inputs, §10.5.1 mandatory lists, TE-04.

**Trajectory.**
1. Decision D's basis statement cites claim κ and evidence relation E (observation o favors κ).
2. A critic objects to the observation itself ("the instrument was miscalibrated"). The objection O targets o's observation claim, which is a claim revision.
3. D1 §6.1 lists "challenged" for an evidence route only when the objection targets the route. Only inference steps count objections on their premises. E stays assessed-sound, and `has_open_challenge(κ)` is false.
4. A(D) = objections on B(D) ∪ basis-claims(D). The observation claim is not cited, so O is "upstream" and reported only on request.

**Variant.** D cites inference step S but not S's premise P, and O targets P. The standing report of κ shows S "challenged", because C6.1 §9.9 inputs include premises. The decision projection does not show O, because A(D) has no premise term. The two views disagree. F-6's rationale, that omitting a material premise is a visible defect, does not apply, because the decider omitted nothing: P is part of S, which was cited.

**Consequence.** The objection most likely to defeat an empirical decision, a defect in the measurement, is absent from the decider's view and from the mandatory list. TE-04 is met literally and fails in substance.

**Repair.**
- Count objections on the endpoints of a cited route toward the route's status: the observation (its event and observation claim), its conditioning model and the calibration or definition records it cites, and, for steps, the premises.
- Extend A(D) by exactly those endpoints of every cited route. This is still one hop, measured from routes rather than from records.
- Add the variant to T69.

**Confidence:** high.

#### R-02 — The cycle rule breaks valid routes, and an adverse assessor beats a positive one (Medium; D1 §6.1)

**Location:** D1 §6.1 (the "broken" and "assessed-sound" rows, "well-foundedness"); C6.1 §9.9; T75.

**Trajectory 1 (over-flagging).**
1. P is supported by an independent, assessed-sound evidence route E.
2. Step S: P → C.
3. Someone asserts step S′: C → P, for example a consistency remark.
4. "A route whose support, followed through inference steps, reaches its own conclusion is circular." From S, the support of P followed through S′ reaches C, so S is circular. T75 says "every route in the cycle is broken". C loses its well-founded route because a third party asserted a converse step.

The rule is not stated per derivation. Grounded semantics would say that S is sound if P has a derivation that does not pass through C.

**Trajectory 2 (disagreement).** In one `(σ, ρ)`, assessor A judges step S valid and assessor B later judges it invalid. "Assessed-sound" needs the *latest* assessment positive and no effective adverse judgment, so the route is "broken". If the order is reversed, the earlier adverse judgment is still effective and the route is still not sound. Disagreement is therefore always shown as "broken". Codex §4 item 5 asks for the opposite: "do not automatically convert contested into false". "Latest" is also a recency selection, which Definition 2.8 disclaims across `(σ, ρ)` but not within it.

**Consequence.** Asserters can break valid routes. Two-assessor disagreement is shown as failure, not as dispute, which defeats P7.

**Repair.**
- Define circularity per derivation: a route is circular only if no premise has a support derivation that avoids its conclusion.
- Add a route status "disputed" for coexisting positive and negative effective assessments, listing both.
- Replace "latest" with the lineage head, as for judgments in C6.1 §5.3.

**Confidence:** medium-high.

#### R-03 — "As held then" pins the ruleset but not the projection version (Low–Medium; D1 F-31, D3 §9.9)

The history read evaluates "under the ruleset versions in force at *t*". Route status and the applicable set are computed by the projection code, and the cache keys include the projection version, but the history contract does not. A later projection change, such as the repairs proposed in R-01 or R-02, would silently change "as held then". **Repair:** pin the projection version in F-31 and §9.9 history, as Codex §4 item 2 proposed, and include it in T78. **Confidence:** medium.

### 3.2 Decisions and the front-end boundary

#### R-04 — The core's applicable-set check lets any objector block a commit, anonymous objectors included (High; D3 §6.9, with the SCIRE front end)

**Location:** C6.1 §6.9 ("the applicable set has not changed since the policy result; otherwise it refuses with a conflict"), §4.4 ("the back end itself blocks nothing"), §5.11; D-37, D-38.

**Trajectory.**
1. SCIRE evaluates a joint finalization and obtains a policy result with an applicable-set snapshot. PIs A and B are about to sign.
2. Any participant, or a sealed critic in an open-review project, records one new objection on a basis record each time a signature is about to commit.
3. Each signature commit is refused, the front end re-evaluates, a new decision revision results, and every earlier signature stops counting (check 5).
4. D-38 then requires the basis statement to address the new objection before the decision can proceed.

**Consequence.** Under D-37, an anonymous objection is "never a procedural veto", yet the back end converts its existence into a commit refusal. That contradicts §4.4. The same lever is a denial-of-service path for any writer, bounded only by write quotas. D-38 does not create this, but it offers no cut-off.

**Repair.** Choose one.
- (a) The core refuses only on expected *basis* revisions and signatures. For applicable-set changes, it commits and records the delta ("objections recorded after the policy result"), which travels with the decision under F-7. The front end's policy decides whether the delta requires re-evaluation.
- (b) Keep the refusal, but let the policy result fix a cut-off position: objections recorded after it travel and are not grounds for refusal.

Either way, state in §4.4 that the back end refuses no decision because of an objection's existence. Add a flood test to T100.

**Owner:** D3, with a SCIRE decision on D-38's cut-off. **Confidence:** high.

#### R-05 — Signature completeness is not defined, so a `validated` decision may show a position as current with signatures missing (Medium–High; D3 §6.9)

§6.9 checks "that every required signature binds this exact decision revision" at the commit of the decision and of each signature. It never says that a `validated` decision makes a position current only once every required signer has a committed signature. T100's "no position becomes current" implies that rule, but the body text does not state it. Nor does §6.9 say what a validated decision shows while signatures are pending, or whether it ever expires.

**Trajectory.** The front end commits validated decision D with required signers {A, B}. A signs. B never signs. The position is "current" for D's purpose, because §6.9's only condition is the `validated` status.

**Repair.** Add the states `validated, awaiting signatures` (renders as pending, makes nothing current) and `validated, complete`. Only the completing signature's commit makes the position current. Add this to DC1 and T100.

**Confidence:** high that the rule is missing. Medium on the effect, because a reasonable D4 might infer it.

#### R-06 — A scope manager can swap the decision-policy owner and bypass joint sign-off (Medium–High; D3 §6.9, §7.3.3, §7.3.1)

The decision-policy owner is "a registered front-end principal, set by a holder of `manage`" (§6.9). Front-end principals are "governed by component roles" (§7.3.1), and no section says who registers them.

**Trajectory.** A PI who holds `manage` on the project scope (the default lead is `rwcm`, §7.3.8) names a different registered client, such as a project-memory tool, as the policy owner. That client transmits a `validated` decision with a single-signer "policy result". The core checks only the transmitter and the structure, so joint sign-off under SCIRE's policy is bypassed.

**Consequence.** This reintroduces the conflation SC-TE05 warned against: access administration (`manage`) is used as scientific authority.

**Repair.**
- Name who may register front-end principals, as an operator act recorded as a control.
- Require a change of decision-policy owner to be attested by the outgoing owner, or by an approval record under the outgoing policy.
- Render the policy owner, and any change to it, on every projection of a validated decision.
- Extend T100 accordingly.

**Confidence:** medium-high.

#### R-07 — Check 3 (sole uninstrumented backing) is easy to bypass, and its refusal sits at the front-end boundary (Medium; D3 §6.9, D1 F-17)

Check 3 examines "evidential backing" without saying how far the core looks. Two bypasses:
- cite a claim whose only route rests on the uninstrumented observation, instead of citing the observation;
- add an unrelated instrumented observation with a `consistent-with` relation.

The refusal also makes the core decide that a finalization may not proceed, which §4.4 assigns to SCIRE (C6-11 asked exactly this).

**Repair.** Compute the check over the routes of the basis claims, through the standing projection: are any routes rooted only in uninstrumented observations? Render the result as a **label** on the decision, as is already done for `reported` decisions, rather than as a refusal. SCIRE's policy then decides.

**Confidence:** medium.

#### R-08 — `applicable_at_decision` duplicates "as held then" (Low; D3 §5.4)

The decision record stores a snapshot of the applicable set that the history read already computes from the commit position. Two owners for one meaning (V4-16) will diverge once R-01 or SC-R1 changes the projection. **Repair:** derive the snapshot, or declare the stored snapshot authoritative and the history read a check against it.

### 3.3 Anonymous-review back end (beyond SC-R3)

#### R-09 — Conflict checks ignore critic-side conflicts; the decline is a timing oracle (Medium; D3 §7.8)

§7.8's conflict set compares the proposed person with the *work*: author, collaborator, co-author, critic, PI. A person chair who is the anonymous critic's declared collaborator or supervisor passes the check, yet that chair reads the critic's identity and adjudicates the critic's blocks and appeals. That is the neutrality gap of TE-R14. Adding critic-side grounds as open reasons would leak, because "fails: declared collaborator" plus public collaborations narrows the critic. They must therefore also show as declines.

Separately, §7.8 does not say *when* the core declines on the person's behalf. An instant decline is distinguishable from a voluntary one, which arrives after human delay.

**Repair.**
- Add critic-side grounds, all rendered as declines.
- Emit a sealed decline only when the proposed person responds, or at the same timeout as non-response.
- Disclose the residual social channel: the person may be asked why they declined.
- Add both to T104.

**Confidence:** medium-high on the gap, medium on the timing channel.

#### R-10 — Who may appoint a chair is inconsistent, and the administrator can reach sealed reads through it (Medium; D3 §4.4, §4.3, §14.2, §7.3.6)

The texts disagree on who appoints a chair:
- §4.4: appointing the chair is SCIRE's.
- §4.3: `record_chair_appointment` is open to the "front end for the review process", with no binding to the front end that opened the review.
- §14.2 and T88: the core refuses a person chair without "a `manage` holder's assignment".

So the core enforces a rule that belongs to the front end, and the rule is weak: the manage holder is often the PI whose work is under review. An administrator who controls front-end registration (see R-06) can register a client, have it appoint a colluding person chair who passes the conflict check, and read sealed attribution through the chair path. §7.3.6 says administrators can never do this, and D-40 accepts operator custody, not administrator-role access.

**Repair.**
- Bind appointment to the front end that opened the review.
- Render the appointment, naming the appointer and the chair, to all participants (§11.5).
- Move the `manage` rule out of the core or into SCIRE's policy.
- State that front-end registration is an operator act inside the D-40 residual.

**Confidence:** medium.

#### R-11 — Quota and processing limits for anonymous sessions (Low–Medium; D3 §7.8, §8.6, §14.2)

Per-principal limits ("1 deep job per principal", "100 model calls … per principal per day") must be charged to someone:
- If they are charged to the sealed principal, their visible effect (refusals, and any usage view) moves in step with the pseudonym's activity. That is differencing.
- If they are charged to the pseudonym, the critic gets a second budget.

"Quota records" are sealed, but the counter's effect is not. **Repair:** give each review a budget owned by the review and charged per pseudonym, and state this in §7.8. **Confidence:** medium.

#### R-12 — §11.5 "as far as they reveal no sealed identity" is a judgment, not a rule (Low; D3 §11.5)

Which fields of chair appointments, sealed-read records, blocks and appeals participants see is left to whoever renders them. **Repair:** enumerate the participant-visible fields per record type (pseudonym, time bucket, kind, chair), and test them in T104. Also disclose that the review scope's write grants and their timing narrow the candidate critic set.

### 3.4 Deletion, archive, retention, de-attribution

#### R-13 — `or nothing where the author asked for complete removal` contradicts D-44 and lets accountability records vanish (Medium–High; D3 §12.3)

§12.3 says a record deleted by its own author shows "withdrawn and deleted by its author", **"or nothing where the author asked for complete removal of their own contribution."** The same section's de-attribution paragraph, D1 F-9a and D-44 all say that deletion of one's own contribution leaves the withdrawal marker.

**Trajectory.** A PI's own `resolution` decision or finalization, or a curator's dissent-relevant judgment, is relied on by others. Its author asks for complete removal, and the record disappears from every projection that showed it, with no marker. A resolution can be erased this way after it has done its work, and a decision others relied on vanishes.

**Repair.** Delete the "or nothing" clause. If complete removal is wanted for records nothing relied on, restrict it to records with no live dependents (§12.2) and no decision or resolution kind. **Confidence:** high on the contradiction.

#### R-14 — Restore can resurrect revoked access and lose access records and deletion markers (High; D3 §12.4, §14.2, Appendix A.3)

A.3 reduces candidate 5's "separately durable recovery control plane for deletion, revocation, permission history and access records" to a tombstone log that covers **deletions** only. §14.2 allows site-loss RPO ≤ 15 minutes.

**Trajectory.**
1. At t, a member is removed from a team scope.
2. An administrator reads a personal scope in administrator mode; the access record is committed before release (§11.4).
3. A curator deletes a critic's objection with a reason and an attributed marker (SC-61). The tombstone is logged.
4. At t + 5 minutes the site is lost. Restore uses a backup from t − 10 minutes and applies the tombstone log.

Result:
- The removed member's read is back.
- The owner never sees the administrator's access record, although content was released.
- The objection is deleted, because the tombstone applies, but its **marker** is lost, so the deletion is now silent. This is exactly what SC-61 exists to prevent.

D-25's "nothing lost" and §11.4's "committed before release" assume durability that the restore path does not give these records. A.3 gives no disposition for revocation or access-record restore safety.

**Repair.** Put permission revisions, access records, deletion markers, sealing and signature records in the separately backed-up log alongside the tombstones, or require zero RPO for them. Extend T13 with a revocation and a marker inside the RPO window. **Confidence:** high.

#### R-15 — De-attribution reaches accountability renderings (Medium; D1 F-9a, D3 §12.3; D-44)

D-44 makes UPMS-derived representations name a person by role on request. In C6.1, decisions render as "decided by ⟨decider⟩" (§6.9), markers as "deleted by ⟨curator⟩" (§12.3), resolutions as "self-resolved" (§6.9), and personal scopes show access records with the principal (§11.4). All of these are derived representations. A PI or curator who requests de-attribution then appears in every overview and projection as "a participant": the SC-61 marker loses its accountability, and the decision's authority display loses its decider.

D1 F-1 also requires attribution to be recoverable from every derived rendering. F-9a only partly reconciles this, by leaving canonical authorship unchanged, and it does not tell the requester that any reader who can open the record sees the name one step away.

**Repair.**
- Exempt accountability renderings from de-attribution: decider, signer, resolver, curator in a deletion marker, administrator in an access record, chair in a block.
- State that de-attribution is presentational and limits repetition, not identification.

**Confidence:** medium-high. This does not re-litigate D-44: it bounds which renderings D-44 can reach without breaking SC-61, which D-46 also chose.

#### R-16 — The deletion preview's count of unseen dependents is an existence disclosure (Low; D3 §12.3, T27)

"Records you cannot see depend on this" contradicts §10.3 ("without `read`, even 'restricted supporting material exists' is not shown") and T28. For an anonymous review, a work's author previewing a deletion learns that private notes depend on the work, which correlates in time with the critic's drafts. **Repair:** declare it as a named exception with a coarse bucket ("some" or "none"), or drop it. **Confidence:** medium.

**Archive and retention (§12.1, §12.2).** I found no further defect beyond SC-R1, which makes superseded objections non-live and therefore archivable. The substantive-reason rule, the liveness predicate and the archive-blind mandatory traversal answer TE-R08 and C6-2 and C6-3 in the body text. One residual for the owner: any `write` holder's "attributed irrelevance judgment" is a sufficient reason, so a single participant's judgment can queue a null result for archive. Archive affects only proactive surfaces, so this is Low.

### 3.5 Person guard

#### R-17 — Author search juxtaposes a person's works with their assessments (Medium–High; D1 F-39, D3 §9.13)

§9.13: "Author search returns works with their own assessments, ordered by ordinary relevance or time, with no per-author aggregate." A list of all of X's works, each shown with its ordinal source assessment, is a per-author collection of assessments. The reader computes the aggregate by looking at it. D1 F-39 says "no view aggregates works by author to compare or characterize authors", and TE-R12 names disguised author collections. Works are assessed from Slice 3 (D-45), so this arrives in Slice 3.

**Repair.** Author search returns works without their source-assessment values, which appear only when a single work is opened. Add this to T81. **Confidence:** medium-high.

#### R-18 — `subject_kind` is self-declared, so the core refusal is a norm (Low–Medium; D3 §9.13, §7.8)

The core refuses agent-authored and anonymous claims "whose `subject_kind` is person". Nothing sets that field except its author, so a claim about a person without the field passes both refusals. The chair's block and the fallible synthesis detector are the only backstops. **Repair:** move the row to the "norm" side of §9.13's table, or define who may set `subject_kind`, and state the residual.

### 3.6 Internal consistency and stale wording

#### R-19 — Invariants, tests, slices and cross-references (Low unless stated)

| # | Location | Defect | Repair |
| --- | --- | --- | --- |
| a | C6.1 §15 E3 | "its four conditions hold"; §9.10 lists five (stale since candidate 6) | "the conditions of §9.10" |
| b | C6.1 §15.2; A.3 §15 row; A.4 | "T01–T103", "T65–T103"; T104–T107 exist | Update the ranges |
| c | C6.1 §16 Slice 2 | Lists T70 and T99, both anonymous-objection cases, though anonymity is unavailable before Slice 3 (§7.8, D-42). **Medium:** Gate 2 cannot run them | Move them to Slice 3, or rewrite them as signed |
| d | C6.1 §16 Slice 1a-core, T03, DL1 | T03 requires an `input_deleted` review obligation at 1a-core; review obligations arrive in Slice 2 (§5.12, TE-08) | Split T03, or show "input deleted" only at 1a-core |
| e | C6.1 §5.11 | "unresolved, whatever its handling (D1 F-5)"; F-5 is self-resolution | Cite D1 Definition 2.5 and P3 |
| f | D1 Definition 2.5 | Target list omits "resolution", which F-4 and C6.1 §5.11 use | Add it |
| g | C6.1 §4.4 against §14.2 and T88 | Chair appointment is SCIRE's in §4.4 and a core check in §14.2 and T88 (R-10) | Pick one owner |
| h | C6.1 §10.5 figure and §10.5.1 "Archive" row | "Archive" means the canonical corpus, while §2 defines Archive as the curator-moved tier (Codex §5.3 asked to separate the two) | Rename the corpus "canonical records" |
| i | D1 §10.3 case 8 | "A narrative that drops the live alternative: flagged"; after SC-TE03 the guarantee is the mandatory list, and the flag is a cue | Rewrite as "shown by the mandatory list; flag is a cue" |
| j | D1 §11 | "Candidate 6 §17.2 repeats this marking" | Candidate 6.1 |
| k | C6.1 §9.10 conditions 1 and 5 | Condition 1 requires *every* cited judgment to be admitted, fresh and head; condition 5 says only `current` entries count for admission | Restrict condition 1 to `current` entries (moot while D-39 defers) |
| l | C6.1 §4.4 and §18.2 against §6.9 | §4.4: "the back end itself blocks nothing"; §6.9 refuses on applicable-set change (R-04) | See R-04 |
| m | C6.1 §17.2, D1 §11 | Decision status (`reported`, `recorded`, `validated`), deletion markers and the participant-visible anonymous-review records are product inspectability surfaces not listed or marked | Mark them as within or beyond the deliverable |

Under the owner record §5, "pending" and "author's recommendation" wording for D-37 to D-46 is to be folded in after the outside review. I do not count it.

### 3.7 Simplicity: text and mechanisms that can go

#### R-20 — Removals (C6-13)

1. **§9.10's full contract, T94 and E3's conditional clause.** D-39 defers this. Keep one paragraph naming D1 §6.5 and this candidate's hash as the proposal to revisit. Consider removing `judgment_basis[]` from the Judgment schema too: a field with no semantics while deferred invites D4 to give it some.
2. **The "critic's own agent principal" assistance route (C61-6).** Keeping only the temporary review-service session removes the overseer-link sealing, agent-scope placement and persistent-memory leaks (SC-R3 A and B).
3. **Channel assessment text deferred by D-45** (D1 Definition 7.2, F-41a, the track-record paragraph of C6.1 §9.13, T82). Move it to a deferred annex so it is not reviewed as current text each round.
4. **`reported` and `recorded`.** Both are non-validated and render "as what they are". One non-validated status, labeled with the result of each integrity check, gives the same information.
5. **Check 3 as a refusal** becomes a label (R-07).
6. **`applicable_at_decision`**, if derived (R-08).
7. **Duplicated invariant prose.** SE1 and TE-15 overlap almost entirely; merge them. §4.4's bullet list restates TE-01 to TE-15; cite them instead. §7.7's anonymity row restates §7.8.
8. **Slice 3 and 4 machinery** (§5.7–§5.9 statement language, §9.7–§9.8 screening and adapters, §10.5.3–§10.5.4 consolidation and narrative economics) could move to slice annexes bound by hash, leaving the Gate 0 to Slice 2 core reviewable at about half the size. Persisted narratives are already conditional on E2.
9. **Appendix A.1 to A.7 and the moot rows of §18.2** are change history, not architecture. After acceptance they belong in a review record or `history/SEMANTIC_EVOLUTION.md`.

## 4. Codex findings: status against the operative text

"Resolved" means the operative body text defeats the Codex trajectory, as far as this same-family check can tell. It is not closure: Codex's revisit condition requires an independent check.

| Finding | Status (this review) | Basis in operative text; residual |
| --- | --- | --- |
| **SC-TE01** / TE-R01 | **Open** | One-pass evaluation through premise judgments, negative information and cycle rejection are present (D1 §6.1, C6.1 §9.9, T98). Judgment on judgment is deferred (D-39), which is acceptable. Open: "effective" has no fit definition and the firewall is bypassed or the projection is empty (SC-R2); the cycle rule over-flags; disagreement becomes "broken" (R-02); the projection version is not pinned in history (R-03) |
| **SC-TE02** / TE-R02 | **Open** | The chair is a confined service role outside D-9, no model sees identities, metadata fields are sealed, replacement and recovery are stated, and operator custody is accepted by D-40 with disclosure. Open: session merging, placement, ancestry edges, assignment and lifecycle acts (SC-R3); administrator reach through front-end registration (R-10) |
| **SC-TE03** / TE-R03 | **Resolved in mechanism; residual** | Deterministic, paginated mandatory lists with exact counts (§10.5.1, MV1, T93). The detectors are stated to be cues. Residual: the lists inherit the applicable-set gaps (R-01, SC-R1) |
| **SC-TE04** / TE-R04 | **Resolved in meaning; contradicted in mechanism** | D-37 and D1 F-8 with C6.1 §5.11 give the narrow no-veto reading, and T99 tests it. But §6.9's commit-time applicable-set refusal gives anonymous objections a procedural block (R-04) |
| **SC-TE05** / TE-R05 | **Partly resolved** | The `reported`, `recorded` and `validated` statuses, atomic expected-revision and signature checks, the policy owner and re-evaluation as a new revision are all present (§6.9, DC1, T100). Open: signature completeness (R-05), policy-owner substitution (R-06), commit-refusal liveness (R-04) |
| TE-R06 | **Resolved** | The weaker guarantee is stated (§7.3.5), the first-product boundary is set with an attestation (§1.2, D-43), and the strict profile is deferred |
| TE-R07 | **Resolved** | Coverage gaps are declared (§8.1, §10.6.4). Masking and rationale exclusion are separate contracts (§7.8, §10.6.4) |
| TE-R08 | **Resolved, except SC-R1** | Liveness predicate (§12.2); mandatory traversal ignores archive (T103). Superseded objections become non-live (SC-R1) |
| TE-R09 | **Partly resolved** | Derived and authored descendants, erasure obligations (D-41) and restore tombstones are in place. Open: revocations, access records and markers on restore (R-14) |
| TE-R10 | **Mostly resolved** | Typed judgment kinds; relations carry no assessment status (§5.5); traversal includes cited definitions, models and calibrations (§9.11). Residual: objections on route endpoints (R-01) |
| TE-R11 | **Partly resolved; open by owner record** | Condition compatibility, definition recursion distinct from cycles, and no ordinal arithmetic are present. Type-specific propagation remains open (owner record §4). The cycle rule needs a per-derivation definition (R-02) |
| TE-R12 | **Partly resolved** | Channels must be technical mechanisms (F-41) and are deferred (D-45). Track-record coverage is stated. Open: author-search juxtaposition (R-17) |
| TE-R13 | **Open** | Pseudonym counts are disclosed, and F-20a's uniform rule (T101, T104) defeats the specific Codex differencing trajectory. New paths through session, placement, edges and assignment (SC-R3), the conflict decline (R-09), quota (R-11) and §11.5's unenumerated fields (R-12) |
| TE-R14 | **Partly resolved** | Later conflicts, replacement without loss, pending appeals and the self-identification warning are present. Open: critic-side conflicts (R-09); appointment authority (R-10) |
| TE-R15 | **Resolved** | §7.7 now uses bounded wording ("help investigate"; "need not raise any flag") |
| TE-R16 | **Resolved** | Per-scope quota, refusal before acknowledgement, reserved capacity and the manager's choice (§8.6, §14.2) |
| TE-R17 | **Partly resolved** | A.3 reconciles candidate 5 §§11–13 and 15 clause by clause. The recovery-control-plane reduction drops revocation and access-record restore safety without a disposition (R-14). V4-12 (iv) and V4-15 remain open (owner record §4) |
| TE-R18 | **Resolved, with slice-mapping defects** | Impact traversal and `validated` decisions are in Slice 2, and anonymity is unavailable before Slice 3 (D-42). T70 and T99 are misplaced in Slice 2, and T03 needs obligations before they exist (R-19 c, d) |
| TE-R19 | **Partly resolved** | Contract checks precede studies, E5 is narrowed and the narrative go/no-go is restored. Missing contract checks: target revision with an unresolved objection (SC-R1); stale-but-present assessments (SC-R2); the objection flood (R-04); incomplete signatures (R-05); policy-owner swap (R-06); session merging and placement (SC-R3); revocation restore (R-14). Ranges are stale (R-19 b) |
| TE-R20 | **Mostly resolved** | Deletion gaps are disclosed, and exposure is what was released, not what was read. Residual: projection version (R-03) |

**On candidate 6.1 Appendix A.8.** It marks SC-TE03, TE-R08, TE-R10, TE-R12, TE-R14 and TE-R18 "Repaired", and SC-TE05 and TE-R13 "Repaired in 6.1". By this review, SC-TE05 and TE-R13 are still open or partly open. TE-R12 and TE-R14 are partly open. TE-R08 and TE-R10 have the residuals named above. A.8's self-corrections for SC-TE01, SC-TE02, SC-TE05 and TE-R13 were directionally right, but the repairs created or left the paths above.

## 5. Answers to the request's other questions

- **§2 item 3: reconciliation of candidate 5 §§11, 12, 13 and 15 (A.3).** Each clause has a row, and I found no omitted clause *in A.3's own list*. I could not verify that list against candidate 5, which I did not read. One disposition is materially wrong in effect: the recovery control plane row (R-14). The §13 row "Identity provider unavailable: reads within the cache bound" is consistent with §7.3.7.
- **§2 item 4: SC-61 and SC-62.** The SC-61 repair (reason plus attributed marker) is sound in normal operation, but it fails on restore (R-14), under self-deletion with complete removal (R-13) and under de-attribution (R-15). SC-62's list is necessary but not sufficient (SC-R3). Other record classes that leak, or can leak: home scope, provenance edges, obligation assignees, lifecycle controls by the sealed author, release ancestry under session merging, quota effects, and the timing of sealed declines.
- **§2 item 5: the front-end boundary.** The back end decides two things that are SCIRE's: refusal by applicable-set change (R-04) and the `manage` rule for person chairs (R-10). Check 3's refusal is borderline (R-07). Checks 1, 2, 4, 5 and 6 are integrity checks and stay in the core.
- **§2 item 7: person guard and de-attribution.** One person-level output is reachable: author-search juxtaposition (R-17). De-attribution conflicts with accountability renderings (R-15), with F-1's recoverability unless the presentational nature is stated, and with deletion where the "or nothing" clause applies (R-13). It does not conflict with fact-checking or with the identity relations, which stay unchanged.
- **§2 item 8: the author's recommendations, now D-37 to D-46.**
  - I agree with D-37, D-38 (subject to R-04's cut-off), D-39, D-41, D-42, D-43, D-45 and D-46.
  - On D-40, the custody residual is acceptable only if "operator" is kept distinct from the administrator role (R-10).
  - On D-44, I agree, bounded by R-15.
  - D-39's deferral is safe only once SC-R2 defines effectiveness. Otherwise the deferral is bypassed through the projection.

## 6. Owner decisions the texts still need

| Decision | Why it needs the owner | Reviewer's suggested framing |
| --- | --- | --- |
| What happens to an objection when its target is revised (SC-R1) | Allocates the cost of revision against the visibility of dissent | Carried and unresolved until withdrawn, re-bound or resolved by decision |
| What "effective" means for scientific standing; whether evidence-only judgments count; a Slice 2 theory ruleset (SC-R2) | Decides whether Slice 2 shows any soundness, and on what authority | Lineage head and validity interval, no wall-clock bound; evidence-only counted only as labeled assessment |
| Whether anonymous assistance by a persistent agent principal stays, and whether Slice 3 requires proven session separation (SC-R3) | Trades convenience against the D-33 promise | Temporary review-service session only; anonymous role as a distinct session type |
| Applicable-set changes at commit: refuse, or commit with a delta; SCIRE cut-off under D-38 (R-04) | D-37 forbids a procedural veto; liveness of decisions | Commit with a recorded delta, or a policy-fixed cut-off |
| Who may change a scope's decision-policy owner; who registers front ends (R-06, R-10) | Separates access administration from scientific authority | Operator registers; outgoing-owner attestation; rendered on every validated decision |
| Recovery: zero RPO, or separate logging, for revocations, access records and markers (R-14) | Changes a deployment profile commitment | Same separate log as tombstones |
| Exemptions from de-attribution for accountability renderings (R-15) | Bounds D-44 against D-46 | Decider, signer, resolver, curator, administrator and chair always named |
| Author search without per-work assessments (R-17) | Fairness boundary under D-32 | Values shown only when a single work is opened |
| Still open from the owner record | — | C6-6 acknowledgement; V4-12 (iv); V4-15; TE-R11 type-specific propagation; strict-profile SC-42 rule; this review's R-20 list for C6-13 |

## 7. Scientific inspectability and evidence

- **O1 content.** D1 §11 and C6.1 §17.2 state the material realized record, readers and routine questions, and mark the theory surfaces as beyond the requested deliverable. Unmarked surfaces are listed in R-19 m. Technical acceptance of either text, by any reviewer, does not accept a surface marked beyond the deliverable; only the owner can.
- **Accepted-authority tensions.** No accepted D1 or D2 authority exists for UPMS, so no tension search against accepted authority was owed or performed. I relied on no accepted authority for a consequential judgment.
- **Evidence executed.** Hash verification, and reading and searching the bound files. Each counterexample is a constructed trace through the text, not observed behavior. No prototype, test, benchmark or study was run.

## 8. Coverage

**Read in full:**
- D1 candidate 1.1 (all 555 lines);
- the Codex review (all 276 lines);
- the owner decisions record;
- the review request.

**Read in full in candidate 6.1:**
- §§1–4;
- §§5.1–5.6 and §§5.10–5.12;
- §6;
- §7;
- §8;
- §§9.1–9.3 and §§9.9–9.14;
- §10, apart from §10.5.4 and §10.5.5, which I skimmed;
- §§11–14;
- the §15 invariant table, §15.1 scenarios T01–T107 and §15.2;
- §§16–18;
- Appendices A.3, A.8, A.9 and B.

**Sampled in candidate 6.1:**
- §§5.7–5.9;
- §§9.4–9.8, of which §9.4 was read in part;
- §10.5.4 and §10.5.5;
- A.4 (read in part).

**Diffed only:** candidate 6 against 6.1. 154 changed lines; spot-checked against A.9, and §9.10's condition 5 confirmed as the C61-1 change.

**Not read:**
- candidate 6.1 Appendices A.1, A.2, A.5, A.6 and A.7;
- the proposal v0.1 (relied on through the Codex review, the owner record and the candidates' citations, so proposal-level defects may be missed);
- candidate 5 (frozen base; A.3's clause list could not be checked against it);
- D1 candidate 1 (not diffed);
- the SCIRE v0.4 proposal and its re-review;
- SSDS sources;
- `history/SEMANTIC_EVOLUTION.md`.

**Working tree.** Before writing this file, the working tree showed modifications to `history/SEMANTIC_EVOLUTION.md` and `workplans/README.md`, and untracked dotfiles. These were not made by this review, and I did not touch them.

**Realized results and variants.** None produced, run or reviewed. This record is a same-family input to the owner's Gate 0 preparation. It is not gate evidence that can satisfy the independent-review requirement. One review pass was made; no alternative reviews or variants were generated or selected among.

**Persistence.** This file is the only change made. No commit, push or other file edit.
