# Same-Family Review of the UPMS Mathematics Package (D1 Candidate 1, 6.3 Mathematics Annex with Hooks H1–H7, SCIRE Mathematics and Tools Extension v0.1)

**Date:** 3 November 2026
**Requested by:** the product owner (Sam)
**Reviewer and asserter:** Claude (AI), model Fable 5.1 (`claude-fable-5-1`), in a Claude Code subagent session with a fresh context. No subagents were launched.
**Tools used:** `sha256sum`, `git rev-parse`, `grep`, `sed` (Bash); file reads; the `scientific-formulation` and `software-design` skills (SSDP 7.2.1 packages) for the D1 and D3 review contracts, including the Challenge Pass. No browser, no network, no code executed beyond hashing and text search.
**Governing method:** SSDP 7.2.1. No task or workplan assigns a `protocol_version`, so the installed 7.2.1 packages apply.
**Kind:** review record. It accepts nothing. Not architecture or formulation authority.

---

## 0. Independence statement

Every text under review was written by Claude (Opus 5.5). This reviewer is Claude (Fable 5.1). This is a **same-family review**. It cannot count as the independent falsification that `AGENTS.md` and the texts' own acceptance routes require. Its value is to find defects before an outside-family reviewer is asked to spend time. Its verdicts are **interim**.

The texts' change notes, "findings raised while drafting", author's recommendations and the annex's statement that hooks were "absorbed" were treated as claims to test, not as evidence. Owner decisions D-57 to D-70 were treated as product choices and were not re-litigated; two of them (D-70, D-60) are named below where a concrete trajectory needs a sharper rule or an explicit confirmation.

**Tension search.** No accepted D1 or D2 authority exists for UPMS, so no consequential judgment here relies on accepted authority. Recorded tensions bearing on the package were searched in: the 6.2 same-family review §7 (hooks H1–H6), the two owner-decision records of 3 November 2026, and the 6.3 change history entries naming the mathematics hooks. PEM is not initialized (`PROJECT-ENGINEERING-MEMORY.md` absent). No other tension home was found. Scopes not searched: prior reviews of candidates 4 to 6.1, the Codex review of the proposal, SCIRE's own review records.

---

## 1. Bound inputs

All four stated hashes matched. No mismatch to report.

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md` | `b50638641a506ae29861cec10fc76a647d6ed961d7345cff27dc0783168047a9` | Under review (D1) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Mathematics.md` | `a2d59886c3d762f74c69eb5379228accbb986259c99055d4d84e40e4d0b424aa` | Under review (D3 annex) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3.md` | `e6c02b0a60eead112b2a0ef78b07ff849e0006c71df25e60aeefa24686590a44` | Under review only for hooks H1–H7: §5 opening, §5.1, §5.3, §5.4, §5.5, §4.3; read as dependency: §4.4, §5.11, §5.12, §7.4, §7.6, §8.2, §8.5, §9.3, §9.9, §9.11, §9.13, §10.5, §12.3, §16, §17 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` | Under review only for H4 (§5.7.1); read as dependency: §5.7, §5.8, §9.7 |
| SCIRE repository, `workplans/active/SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.1.md` | `b97974f0e0855c7c0ad815c0c38ac34180fc4b4c89b75bffa1a625ba0c1fa86a` | Under review (front end) |
| `workplans/active/UPMS_Owner_Decisions_Math_2026-11-03.md` | `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | Input: D-57 to D-62 |
| `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Input: D-63 to D-70 |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_3.md` | `4c0c81d1e62b9dbcf09c874e6ef41f626458c60c6d716e7dfba0793fa7a69d77` | Parent D1; read §1, §2, §4, §5, §6, §7, §8, §9, Appendix E |
| `workplans/active/UPMS_Candidate_6_2_Same_Family_Review.md` | `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9` (as stated by 6.3 §1.1; not re-hashed) | Read §7 only (hooks) |
| SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md` | `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` (verified) | Read §8.6, §8.7, §10.1 and the heading outline only |

**Git positions read at:** UPMS repository `73f5090b0e94c6cbfad834ae9cf2953ba1c4353c` (branch `upms-candidate-6-d1-formulation`, with the reviewed files untracked in the working tree); SCIRE repository `577fe7d093a481c17cf908d155e9333ba41ae70c`.

Note: the mathematics D1 text names parent candidate 1.2 (`219a81bb…`) while D-70's rules live in candidate 1.3; the annex acknowledges this. This review tests the package against 1.3, since the hooks depend on 1.3's Definition 2.7 and §6.1.

---

## 2. Verdicts (same-family interim)

| Text | Verdict | Why |
| --- | --- | --- |
| D1 mathematics formulation, candidate 1 | **NO-PASS** | SM-1 to SM-4: a tool-backed step stays sound after its rendering is found unfaithful; `assumed` and `defined` premises have no status rule, so TM04 cannot pass and no derivation from a model can be assessed-sound; discharge is computed by set difference, not per path; agents can empty the brief's mandatory list by judging their own renderings faithful. Plus FM-R01 (the `suggested` overload and its pre-specified-test escape) |
| D3 mathematics annex with hooks H1–H7 in core 6.3 and checking annex §5.7.1 | **NO-PASS** | Realizes SM-1 to SM-4 as written; FM-R14 (no ruleset covers `fidelity` and `inspection`, so under Definition 6.0 neither kind is ever effective); FM-R15 (no operations for the H7 kinds, bindings or tool registration); the objection-target gap (FM-R13). H1, H2, H4, H5, H6 are otherwise additive; H7 is bounded if read as closed |
| SCIRE Mathematics and Tools Extension v0.1 | **NO-PASS** | Smaller defects, but it inherits SM-4 through its role table (FM-R27), its seeded-error study is not testable before data as specified (FM-R28), and it binds its UPMS inputs without hashes and to the superseded 6.2 (FM-R26). Its repairs are mostly consequences of the D1 repairs |

The direction is sound and the separation of statuses (check, fidelity, inspection coverage) is right. The defects are in the rules that compute standing from those statuses, and in who may set them.

---

## 3. Serious Challenges

### SM-1 — A tool-backed step stays "assessed-sound" after its rendering is found unfaithful (math D1 FM-11/FM-14/FM-15; parent D1 §6.4; D3 §9.11, §5.12)

**Claim under test.** FM-11: "if the tool input renders the step unfaithfully, the check says nothing about the step." FM-15: "Each divergence is an objection to the rendering, so it travels (TE F-7)." D-70: fidelity judgments are never cited in an inference assessment's basis.

**Trajectory.**
1. The derivation agent renders step S7 as a SymPy input and runs it; the check `passed`.
2. A human or agent assessor submits an inference assessment of S7 (valid) whose basis cites the tool check. This is what FM-11 and annex §M.6 invite. The judgment is effective (Definition 6.0: the tool check is current, no obligation pending, no other judgment cited). Route: assessed-sound.
3. Two days later an inspector records a `fidelity` judgment on the `renders` link: `diverges(at: sign of the second term)`.
4. Nothing changes for S7. Definition 6.0 condition 3 asks only that cited evidence be current and not retracted, corrected or deleted; the tool check is none of those. Condition 4 asks for no pending review obligation; §9.11 step 1 lists the causes that create one (correction, retraction, revision, deletion, quarantine, definition change, requalification), and `ReviewObligation.cause` has no value for a fidelity divergence. The objection FM-15 creates targets the rendering, which is not an endpoint of the inference step under F-6 (premises and conditions), so the route is not even "challenged".
5. The standing report shows S7 as **assessed-sound** on one line and the rendering as **diverges** on another. MP4 is satisfied to the letter. The result's `has_sound_route` stays true. A decision that cites the route sees no objection in its applicable set unless its basis statement happened to cite the rendering.

**Consequence.** The formulation's own failure definition (§1.2, second bullet: "shown a computer-checked step as if the derivation were verified") is met by a trajectory the formulation permits. The evidence the assessor relied on is known, by FM-11, to say nothing, and the judgment stands.

**Why this is a Challenge, not a finding.** The repair needs a D1 rule, not a wording fix, and it sits next to D-70's boundary. It does not require re-litigating D-70: the fidelity judgment still never enters a basis.

**Bounded repair (D1, then D3).**
- Parent D1 F-32 already lists "found inapplicable" as a cause. The math D1 should state: an effective `fidelity` judgment with result `diverges` on a `renders` link makes every tool check that realizes that link **inapplicable as evidence** for the claim or step it was about to bear on, and creates a review obligation (F-32) on every route whose effective assessment cites one of those tool checks. The route is then under review (Definition 6.0 condition 4) until reassessed.
- D3: add `rendering_diverges` (or reuse `inapplicability`) to `ReviewObligation.cause`; add fidelity judgments with result `diverges` to §9.11 step 1's causes; impact traversal follows `renders` links to tool checks and from tool checks to the judgments whose basis cites them (the basis is already recorded by identity).
- Also let an objection target a `renders` link, a tool check and a binding, and let an objection on a `renders` link count toward "challenged" for every route whose effective assessment cites a tool check realizing that link (see FM-R13).
- Add a test: TM05 as written stops at "until a fidelity judgment locates the divergence"; extend it to require that the step's route then shows under review and that a decision citing the route shows the obligation.

### SM-2 — `assumed` and `defined` premises have no status rule; TM04 cannot pass, and no derivation from a model can ever be assessed-sound (parent D1 §6.1 and Definition 2.7; math D1 Definition M.7, FM-5; D3 §9.9, §M.5)

**Claim under test.** Math D1 Definition M.7: premises are "model relations, assumptions, previously derived results and imported results"; `cond(Δ)` includes "undischarged assumptions" and "regimes of the models it uses"; FM-5: routes through Δ are at most `supported-under(cond(Δ))`. TM04: a never-discharged case hypothesis `x > 0` gives `supported_under(x > 0)`.

**What the parent says.** §6.1 "Premises": the premises of a step are its premise claims other than hypotheses **discharged** inside the same derivation. A premise is established only through an effective judgment with status `supported` or compatible `supported-under(c')`. Otherwise the route is **premises not established**. §9.9 realizes this exactly and says premises enter only through their own effective judgments.

**Trajectory A (TM04).** A step introduces `x > 0` as a claim of modality `assumed` and uses it as a premise. It is never discharged. Under the parent, it is a premise; it has no `supported` judgment (nobody judges an assumption supported; it asserts nothing); the route shows **premises not established**, listing `x > 0` as unassessed. It never shows `supported_under(x > 0)`. TM04's required discriminator contradicts the parent's rule. An implementer following §9.9 fails TM04; one passing TM04 violates §9.9.

**Trajectory B (every model).** Definition M.5: a model is recorded as claims of modality `defined`; Definition M.7: its relations are premises. A derivation from Maxwell's equations within a model has four `defined` premises. None has, or should have, a `supported` judgment ("defining a model asserts nothing about nature"). Every such derivation is **premises not established** for ever. The package's central object cannot reach the status the package is built to compute.

**Consequence.** The math D1 and the parent D1 contradict each other on the most common premises a derivation has. The annex (§M.5) realizes the math D1's wording ("`supported_under(cond(Δ))`") on top of a projection (§9.9) that cannot produce it. This is the kind of upstream contradiction the kernel says to raise rather than patch around.

**Bounded repair (parent D1, owner decision as for D-70).**
- Parent Definition 2.7 / §6.1: a premise of modality `assumed` that a derivation introduces and does not discharge is **not a premise to be established**; it is a **condition** of every conclusion reached through it, and the route is at most `supported-under(h)`. A premise of modality `defined` that belongs to a model the derivation declares (a model relation or model assumption) is likewise not a premise to be established; the derivation's conclusions carry the condition "within model 𝔐 at version v, in regime ρ". Nothing else changes: `asserted`, `found`, `reported`, imported results and previously derived results remain premises that need effective judgments.
- Math D1: state the result's modality separately (the asserter chooses `asserted`, `predicted` or `hypothesized`), and that "within 𝔐" is a condition, so MP7 holds by construction. Fix Definition M.7 to say which premises need judgments and which become conditions.
- D3 §9.9 and §M.5: compute `cond(Δ)` as the union of (undischarged introduced hypotheses) ∪ (approximation conditions) ∪ ({model identity, version, regime} for each declared model); exclude those premises from the "established" check. T98 and TM04 then agree.

### SM-3 — Discharge is computed by set difference, not per path, and discharges are invisible; `discharges[]` can drop an assumption the conclusion still needs (parent D1 Definition 2.7; D-70; D3 §5.5 H3, §9.9, §M.5; math D1 Definition M.6, FM-19)

**Claim under test.** D-70: "a hypothesis introduced by a derivation and discharged by a later step of the same derivation does not need a `supported` judgment … the step that discharges it is assessed like any step." Core §5.5 H3: "the projection uses `discharges[]` only to exclude discharged hypotheses from a conclusion's premises." §M.5: `cond(Δ)` derived from "undischarged assumptions".

**What natural deduction requires.** A hypothesis H is discharged for a conclusion K only if **every** path from a use of H to K passes through a step that discharges H, and that step has the right form (→-introduction concludes H→K', not K'; case analysis concludes K from A∨B with both A and B discharged and A∨B still a premise; reductio concludes ¬H from ⊥; induction concludes ∀n P(n) from the base case and a step discharging the induction hypothesis), and no eigenvariable of a discharged hypothesis is free in another open hypothesis. The first condition is structural and deterministic. The others need an assessor.

**Trajectory.**
1. Step S1 introduces H1 = `x > 0`; S2 introduces H2 = `x ≤ 0`.
2. Branch 1 derives K from H1 at S3. Branch 2 derives K from H2 at S4. S5 (case analysis) concludes K from `x > 0 ∨ x ≤ 0`, S3 and S4, with `discharges: [H1, H2]`. So far correct.
3. S6 derives K' from H1 directly (a bound that holds only for positive x) and S7 concludes the result R from K and K'.
4. The projection computes undischarged = introduced \ discharged = ∅. `cond(Δ)` carries no `x > 0`. R shows no condition. But R depends on K', which depends on H1 along a path that never passes S5.
5. The assessor of S5 (the discharging step) finds S5 valid, which it is. The assessor of S7 sees premises K and K', both derived. Nobody is shown that H1 is still open on the S6 path, because the standing report (§7) shows `cond(Δ)` and FM-19 lists "undischarged assumptions", and H1 is counted as discharged. Discharged hypotheses appear nowhere in the report or the brief.

**Abuse variant.** An author (or agent) writes `discharges: [H]` on a step whose conclusion is K rather than H→K. The projection drops H from the premises before any human sees the derivation. The error is recoverable only by opening that step. The brief's mandatory part (FM-19) has no category for "hypotheses discharged, and where".

**Consequence.** `supported-under(cond(Δ))` is computed wrongly for a legal derivation, and the mandatory part cannot surface the one place where the drop happened. D-70's rule is sound as the owner stated it; its realization as a set difference is not.

**Bounded repair (D1 precision of D-70, then D3).**
- Parent Definition 2.7 / §6.1: a hypothesis is discharged **for a conclusion** only when every path in the derivation from a step that uses it to that conclusion passes through a step whose `discharges[]` names it; a hypothesis not so discharged is undischarged for that conclusion (and, under SM-2's repair, becomes its condition).
- D3 §9.9, §M.5: compute undischarged hypotheses per conclusion by graph reachability over the Derivation record, not by set difference. At commit, refuse a step whose `discharges[]` names a hypothesis that is not introduced upstream of it in the same derivation (an integrity check like "endpoints must exist", not a semantic judgment).
- Math D1 Definition M.6: add the discharging rules to the curated step-rule set (`implication_introduction`, `case_analysis`, `reductio`, `induction`, `existential_elimination`), each with the form the assessor must check and its eigenvariable condition. D-70 says the discharging step is assessed like any step; there must be a rule to assess it against.
- Math D1 §7 and FM-19: the standing report lists each discharged hypothesis with the step that discharged it; the brief's mandatory part gains the category "hypotheses discharged, with the discharging step". SCIRE §8 item 3 lists them as objective signals.
- Add tests: the trajectory above; a `discharges[]` naming a hypothesis from another derivation is refused; a `discharges[]` on a step whose conclusion is K (not H→K) is recorded, shown in the mandatory part and left to the assessor.

### SM-4 — Agents can empty the brief's mandatory list by judging their own renderings faithful; nothing refuses an `inspection` judgment from an agent (math D1 MP5, FM-14, FM-19, Definition M.10; D3 §4.3, §5.3 H1, §7.6; SCIRE §5)

**Claim under test.** FM-14: a rendering bears on its claim only through an **effective** fidelity judgment. FM-19: the mandatory part lists "renderings without an effective fidelity judgment". Definition M.10: an inspection judgment is "an attributed act by a human inspector". D-61: agents formalize, humans inspect.

**What the core allows.** `submit_assessment` (§4.3) accepts judgments from a "registered assessor or worker, or a human assessor". §7.6's inquiry ruleset covers "attributed human and agent assessments", labeled. Nothing in H1, §4.3 or §5.3 restricts the assessor of a `fidelity` or `inspection` judgment, and nothing refuses a judgment whose assessor authored the target.

**Trajectory.**
1. The derivation agent renders 23 steps as tool inputs. All 23 are in the mandatory part under "renderings without an effective fidelity judgment".
2. The same agent, or a checking agent of the same model family, submits 23 `fidelity` judgments: `faithful`. They are labeled agent assessments. Under Definition 6.0 they are effective once a ruleset covers them (and FM-R14 notes none does yet; once that is fixed, this trajectory opens).
3. The mandatory part's category now has count 0. The coverage line still says "0 inspected", but the reader asked "does this rendering say what the claim says?" gets "faithful (agent assessment)" and the brief no longer puts the renderings in front of a person.
4. An agent principal submits an `inspection` judgment of depth `end_to_end`, outcome `no defect found`. The core accepts it (nothing refuses it). FM-17 asks for designated verifiers, so it does not make the derivation verified end-to-end; but the coverage line counts it as "inspected", and FM-16's "which were checked only by tools" line is now wrong.

**Consequence.** The texts promise that a brief "never omits a mandatory item" (MP6) and that "people inspect" (MP5, D-61), but the mandatory membership is defined by a status that an agent can set on its own work. This is the trajectory in §1.2's fourth bullet ("shown an agent's summary as if a person had inspected the work") in a structured form.

**Bounded repair.**
- Math D1: Definition M.10 becomes a refusal, not a description: the memory accepts an `inspection` judgment only from a human principal. FM-14: an agent's `fidelity` judgment is an agent assessment and never removes a rendering from the mandatory category; the category is "renderings without an effective fidelity judgment **by a human other than the rendering's author**", with agent-judged renderings shown as "fidelity: agent-judged only". A fidelity judgment by the rendering's author is labeled "self-judged" (as F-5 labels self-resolution) wherever shown.
- D3 §4.3 and §5.3: the core refuses `inspection` judgments from agent principals and from anonymous-role sessions (the latter already follows from D-64); it records, on every `fidelity` judgment, whether the assessor is an agent and whether the assessor authored the target; §M.7 computes the mandatory category accordingly. Add MA7 and tests.
- SCIRE §5: the role table should say the derivation agent never submits fidelity or inspection judgments on its own renderings, and whether it may submit inference assessments of its own steps at all (today the "Never" column omits this; see FM-R27).

---

## 4. Findings

Findings are ordered by earliest owning domain. Each has a trajectory, a consequence and a bounded repair. Severity: High blocks acceptance of the text; Medium should be repaired before an outside-family review; Low is a wording or consistency defect.

### 4.1 Mathematics D1 (candidate 1)

**FM-R01 (High) — FM-12 overloads `suggested` and opens a pre-specified-test escape that §9 forbids.**
Parent Definition 5.2's `use ∈ {suggested, fitted, selected, tested-pre-specified, …}` describes how **data** were used relative to a hypothesis: `suggested` means the data suggested it. FM-12 uses `suggested` to mean "only suggests confirmation". Same label, different meaning; a reader of the use history later asks "which data suggested this result?" and finds ten sample points that did not. Worse, FM-12's "unless a pre-specified test is declared" lets a numerical run be recorded `tested-pre-specified`; Definition 5.3 then admits it as an **independent confirmation** if the other conditions hold, while §9 says "no numerical check is offered as confirming" until D2. *Repair:* record numerical exploration as an evidence relation of kind `consistent-with(T)` or `bears-on(T), unassessed` (Definition 5.1), with the use-history entry describing the actual use (normally `model-check` or `not-applicable`); state that until D2 is accepted no numerical check takes `tested-pre-specified`, `entails` or `prediction-succeeded`. Remove the escape clause or route it to §9 explicitly.

**FM-R02 (Medium) — FM-17 does not require inspection judgments to be effective, nor designation at the time of inspection, nor a designation scope.**
*Trajectory:* a verifier records `no defect found`, then supersedes it with `defects found`; or sets a validity interval that has passed; or is designated for derivation A and inspects derivation B; or is designated after inspecting, or revoked after. FM-17 says "within one or more `end-to-end` inspections by designated verifiers" and none of these cases is decided. Definition M.9 requires fidelity judgments to be effective under Definition 6.0; Definition M.10 says nothing about inspection judgments. *Repair:* FM-17 counts only **effective** inspection judgments (Definition 6.0, with condition 5 trivially met); the verifier must hold a designation **for that work or its scope** whose effective interval covers the inspection's `applicable_time`; `revoke_designation` changes nothing retroactively ("as held then") but removes the status for current reads unless the project's rule says otherwise, and the report says which.

**FM-R03 (Medium) — "verified end-to-end" is a derivation property that reads as a result property.**
FM-17 says "a derivation is shown as verified end-to-end"; SCIRE §7 step 6 says "the result is shown as verified end-to-end"; SCIRE §10 hands SSDS a "verification status". A derivation whose every step is verified end-to-end from premises that are "premises not established" is correctly verified and its result is not established. *Repair:* the status line always reads "derivation verified end-to-end; premises: ⟨status⟩; conditions: ⟨cond(Δ)⟩"; SCIRE §7 step 6 and §10 say "derivation", and the SSDS package carries premise standing beside verification status.

**FM-R04 (Medium) — FM-1 compares through bindings only and ignores conventions; `MathExpression` has no context reference.**
*Trajectory:* two papers bind `g_{\mu\nu}` to definitions linked `identical`; one context uses signature (+,−,−,−), the other (−,+,+,+). FM-1 compares them as the same mathematics. Convention lives on the `SymbolContext` (Definition M.2), not on the definition, so the `identical` link is not where the difference shows. Also, an expression reaches its context only through its bindings → definitions → context; an unbound or partially parsed expression has no context, so FM-4's review obligations on a convention change cannot reach it (annex §M.3 traverses bindings). *Repair:* every `MathExpression` carries `context_ref`; comparison requires the same context or a meaning link between the contexts' conventions, else raises the cue "conventions differ"; impact traversal on a convention change follows `context_ref`.

**FM-R05 (Medium; D1 → D2) — numerical disagreement is called a "strong cue" without the tolerance that agreement is denied.**
FM-12 sends numerical agreement with a stated tolerance to D2 but treats "disagreement at a sample point" as a counterexample candidate. Whether two floating-point values disagree is the same tolerance question. *Trajectory:* a check at `x = 10⁶` disagrees in the eighth digit because of cancellation; the brief lists a counterexample candidate. *Repair:* until D2, record "values differ" with both raw values and the environment; whether that is a counterexample is the asserter's objection, and the §9 table gains the row.

**FM-R06 (Medium) — no assumptions or limitations section; the honesty of inspection judgments is an unstated assumption.**
The parent has §8 (A-1 to A-4, limitations). The math text has none. Its load-bearing assumption is that an inspection judgment reports what was inspected and to what depth; the memory cannot verify this and must not try (D-32). A `no defect found, end_to_end` recorded thirty seconds after exposure is accepted. *Repair:* add §8-style assumptions: A-M1 inspection and fidelity judgments are honest reports; A-M2 the project's designation rule, not the memory, carries verifier qualification; and the limitation that the "robust route" (D-61) is robust only as far as the designated person's work is.

**FM-R07 (Low) — §10 says "four small additions"; the annex has seven hooks (H5 designations, H6 `renders`, H7 record kinds are missing from §10). The front matter and §0.1 name parent 1.2 while D-70 is in 1.3.** *Repair:* list all seven; rebind to 1.3 with its hash.

**FM-R08 (Low) — `faithful_under(c)` has no consequence anywhere.** Fidelity never enters route status (D-70), and `c` joins neither `cond(Δ)` nor the mandatory part. *Repair:* either drop it (simplicity) or list `c` beside the tool check in the mandatory part as "tool check bears only under c".

**FM-R09 (Low) — statement kinds `assumption` and `definition` (Definition M.4) overlap with modalities `assumed` and `defined`; the allowed combinations are not stated.** An `assumption`-kind statement on an `asserted` claim is representable and means nothing. *Repair:* either restrict (kind `assumption` ⇒ modality `assumed` or `hypothesized`; kind `definition` ⇒ `defined`) or say the kind is purely presentational.

**FM-R10 (Low) — the brief's subject is undefined.** FM-19 speaks of "the work's applicable set" but never says a brief is about a derivation revision, a result claim revision or a model version. Counts and the coverage line depend on this. *Repair:* a brief is a projection over one derivation revision (or one result claim revision and every derivation to it).

**FM-R11 (Low) — ordering the synthesis "by the producer's stated uncertainty" (FM-20) requires an ordinal confidence, which is a soft score.** *Repair:* say the order is itself the producer's claim, labeled synthesis, and that no ordinal or numeric value is stored on any record.

### 4.2 Parent D1 (candidate 1.3), as the package depends on it

**FM-R12 (Medium) — F-20 says who did an analysis enters assessment "only through identity relations"; FM-17 adds designation.**
"Verified end-to-end" is computed from a person attribute: whether the inspector holds a designation. This is a role under the project's rule, like a decider's authority basis (Definition 2.10), not an assessment, and it is defensible. But F-20's "only" is now false, and D-32's "no labeling of a person" needs the explicit carve-out that a designation is a project act, not a label the memory assigns. *Repair:* parent F-20 (or a math-D1 rule the parent admits): designation and decision authority are recorded roles under a project rule; they enter computed status only as membership and are never inferred, ranked or aggregated.

**FM-R13 (Medium) — the objection target set excludes renderings, bindings, conventions and tool checks.**
Parent Definition 2.5 and core §5.11 allow targets: claim, inference step, evidence relation, applicability condition, resolution. FM-15 makes each divergence "an objection to the rendering"; SCIRE §4 says objections can target "a binding, a convention or a rendering". Core §5.5 says "every relation … is itself a target for objection", which the §5.11 schema contradicts. A convention is a `defined` claim and is fine; a `renders` link, a binding and a tool check are not targets. *Repair:* parent Definition 2.5 adds "a relation (including a `renders` link or a binding) and an observation (including a tool check)" to targets; core §5.11 follows; §6.1 "challenged" covers an objection on a `renders` link for the routes whose assessments cite a tool check realizing it (see SM-1).

**FM-R14** is listed under D3 because its home is §7.6, but it depends on parent Definition 6.0 condition 6; see below.

### 4.3 D3 core hooks (H1–H7 in core 6.3; H4 in checking annex §5.7.1)

**FM-R14 (High) — no ruleset covers `fidelity` or `inspection` judgments, so neither is ever effective.**
Definition 6.0 condition 6 requires a ruleset registered for the scope. §7.6's inquiry ruleset "covers attributed human and agent assessments of claims, evidence relations, inference steps and objection resolutions". `fidelity` and `inspection` are not covered. Definition M.9 requires fidelity judgments to be effective. *Trajectory:* every rendering is "fidelity not assessed" for ever, however many judgments exist; FM-17 can never be met once FM-R02's repair requires effective inspections. *Repair:* §7.6 extends the inquiry ruleset to the two kinds (with SM-4's assessor restrictions), or the annex names the ruleset. Also extend §5.3's `result` comment to the fidelity and inspection results.

**FM-R15 (Medium) — §4.3 has no operation for the H7 kinds, for bindings or for tool registration, and `designate_verifier` has gaps.**
Expressions, symbol contexts, models, derivations and inspection scopes are "canonical record kinds" (§5 opening) with no row in §4.3; tool registration (§M.6, "operator act") has no operation and no §4.3 guard; bindings have no operation (they are embedded fields, see FM-R19). `designate_verifier`: the right is `write`, on an unnamed scope; the subject may be an agent principal or the designator; nothing shows "designated by the work's author". *Repair:* add rows (`record_derivation`, `record_model`, `record_inspection_scope`, `bind_symbol`, `register_tool` as an operator control); `designate_verifier` requires `write` on the work's home scope, refuses a non-human subject, and every projection that uses a designation shows the designator and labels "designated by the work's author" or "self-designated", as F-5 does for resolutions. Whether the core should refuse those two cases, or only label them, is an owner decision (§5).

**FM-R16 (Medium) — a step's membership in a Derivation record is not exclusive, so "within the same derivation" (D-70) is ambiguous; acyclicity is not checked.**
Inference steps are recorded independently (`record_inference`); a `Derivation` record lists `steps[]`. One step can be listed in two derivations with different `introduces[]`/`discharges[]` structure. §9.9 evaluates routes per step and must choose a derivation to apply discharges. The parent already judges circularity "per derivation". Definition M.7 says a derivation is acyclic; nothing checks it. *Repair:* a step belongs to at most one Derivation record (or H3 fields live on the Derivation's step entries, not on the step); the core refuses a cyclic `Derivation` at commit; §9.9 states that route status for a step is computed under the derivation that owns it.

**FM-R17 (Low) — §5 opening H7 reads as a general licence for annexes to add record kinds.** It names five kinds, which is bounded; but the heading "Annex record kinds" suggests more may follow without a core revision. *Repair:* say "exactly these five; any further kind reopens §5".

### 4.4 D3 mathematics annex

**FM-R18 (Medium) — §M.6's evidence semantics misuse the parent's evidence relation.**
"A symbolic `passed` is evidence bearing on an inference assessment of the checked step, through an evidence relation whose conditioning model is the `renders` link." Parent Definition 2.6 defines an evidence relation from an observation to **target claims** `T` under a conditioning **model** `m`; Definition 5.1's kinds (entails, refutes, favors, …) have no kind that targets an inference step, and a `renders` link is a relation, not a model. *Repair:* a tool check enters an inference assessment as a record cited in that judgment's `supporting_refs` (its basis), with the `renders` link cited beside it; no evidence relation is created. This also makes SM-1's traversal (judgment basis → tool check → `renders` link) well defined.

**FM-R19 (Medium) — bindings are embedded fields of `MathExpression`, but the text treats them as authored interpretations with their own lifecycle.**
§M.3: "Bindings are records with authors. An agent's proposed binding is an interpretation until confirmed or adopted." Schema: `bindings[]: {occurrence, symbol_definition_ref | unbound}` inside the expression. An expression is authored by the speaker (its span); the binding is proposed by the secretary. Confirmation (Definition 2.3) is of an interpretation claim by the speaker of the span; a binding is not a claim. Also, `occurrence` is undefined: if it is a parse node, every re-parse (§M.2) orphans every binding; if it is a source range, it needs no parse at all. Impact traversal (§9.11) names "meaning-link graphs" but not bindings. *Repair:* a binding is a relation in the Meaning family from a **source range** of the span to a `SymbolDefinition` claim, with author, lifecycle, `interpretation | confirmed | adopted` state and its own objection target; §9.11 names it. Parsing is then optional for bindings (see §6, simplicity).

**FM-R20 (Medium) — the derivation agent may assess its own steps with its own tool checks, and nothing labels it.**
Under §7.6 an agent's inference assessment is a judgment, labeled as an agent assessment. The derivation agent can run SymPy on its own renderings, judge each step valid citing the run, and `has_sound_route` is true with no person and no other agent involved. The coverage line shows "tool-checked only", which is honest, but the route word "assessed-sound" is strong, and the assessor's identity with the author is not surfaced. *Repair:* label an inference assessment whose assessor authored the step "self-assessed" (as F-5); the brief's mandatory part lists "steps whose only effective assessment is self-assessed or agent-assessed" (FM-19 today lists "steps checked only by tools", which no longer describes this case once the agent has judged).

**FM-R21 (Medium) — the acceptance tests do not cover the Challenge trajectories, and TM04 cannot pass under the parent.**
TM04 (SM-2), TM05 (stops before SM-1's consequence), no test for path-scoped discharge (SM-3), none for agent fidelity self-judgment or agent inspection (SM-4), none for designation by the work's author, none for a revised step losing its inspection coverage. *Repair:* add TM13–TM18 as sketched in §3, and restate TM04 after the parent rule exists.

**FM-R22 (Low) — `environment_identity` is "a hash of the environment description".** A description can be stale; a symbolic check offered as evidence should be re-runnable. *Repair:* where available, an image digest or lockfile hash; otherwise "description only", shown with the check.

**FM-R23 (Low) — tool registration cites D-52, which decides front-end registration and chair authority, not tools.** D-66 extended D-40 to front ends explicitly; tools need the same explicit extension. *Repair:* name it as proposed and ask the owner (§5).

**FM-R24 (Low; owner confirmation) — dimensional screening (§M.4) and LaTeX parsing (§M.2) run inside UPMS.** D-60 says "checking and computation run outside the memory". Screening that only flags, replayably, is consistent with the core's existing theory–theory channel ("unit and dimension errors in typed equations"), and parsing is derivation like extraction. But the owner should confirm that D-60 means "no tool executes and no verdict is computed in the memory", not "no computation at all". Open challenge 2 (natural units) predicts a high "not covered" rate, which bears on whether to defer §M.4 (§6).

**FM-R25 (Low) — §M.8 says parses and cues are purged when an input is deleted; §12.3's list of UPMS-derived representations does not name them.** *Repair:* name them in §12.3 or say the list is open by example.

### 4.5 SCIRE front end (Mathematics and Tools Extension v0.1)

**FM-R26 (Low) — inputs are bound without hashes and to candidate 6.2.** The UPMS D1 mathematics text, core 6.2 and the 6.2 mathematics annex are named without SHA-256; the annex under review is the 6.3 one. *Repair:* bind to 6.3 and the annex and D1 by hash.

**FM-R27 (Medium) — the role table leaves the gaps that SM-4 and FM-R20 exploit.** The derivation agent's "Never" column omits submitting inference, fidelity or inspection judgments; the checking agent is "preferably" of another family (open question 2); the Inspector row says a person records fidelity judgments but no row forbids an agent from doing so. *Repair:* the derivation agent never submits fidelity or inspection judgments and never assesses its own steps; agents never submit inspection judgments; whether a checking agent must be of another family is an owner decision (§5).

**FM-R28 (Medium; evaluation / D2) — the seeded-error study is not testable before data as specified.**
§8 proposes injecting errors and comparing three inspection conditions on "errors found, errors missed and inspector time". Missing before data: the primary outcome; blinding (inspectors must not know which derivations are seeded or which condition is being tested); the error catalogue frozen before inspection; the number of derivations and inspectors (inspectors are few, so a within-subject design with order balancing is needed); what "full inspection without a brief" shows (without the mandatory part, the inspector does not even see the coverage line); and the form of the owner's limit. Also, two different things are mixed: whether the **mandatory part** lists every seeded dropped condition and unfaithful rendering that was recorded as such is a deterministic test (TM09 family), not a study; whether **people** find seeded sign errors faster with a brief is the study. *Repair:* split them; pre-register the study (outcome, hypotheses, catalogue, assignment, analysis) as a SCIRE evaluation item with owner-set limits before any data; hand D2 nothing until a statistical comparison is actually needed.

**FM-R29 (Low) — "a decision may proceed on less only with an explicit qualification that travels (UPMS D1 TE F-33)".** F-33 is about routes under a pending review obligation. A derivation that is not verified end-to-end is not under review. *Repair:* cite F-7/overrides for the qualification's travel, or add a math-D1 rule.

**FM-R30 (Low) — stored agent-written scripts and notebooks (§6.1 "artifacts … stored as payloads") are executable text that a later agent may read from memory.** "Data, never instructions" covers reading; it does not say the artifact is never re-executed from memory. *Repair:* artifacts carry source class M and are never executed by any UPMS worker; a re-run is a new tool invocation through the front end with the artifact as recorded input.

**FM-R31 (Low) — §8 item 6, "an estimate of the time each takes", is an agent-produced number in the brief.** Harmless if labeled synthesis; drop it for the first version (§6).

### 4.6 D2

No D2 authority is opened by the package, correctly. The two hand-off rows in math §9 are right as far as they go. Two items should join them: the disagreement tolerance (FM-R05) and the evaluation design's statistical comparison if the study (FM-R28) is run with a quantitative limit.

---

## 5. Owner decisions still needed

1. **Status of `assumed` and `defined` premises** (SM-2): adopt the rule that an undischarged introduced hypothesis and a declared model's relations and assumptions are conditions of the conclusion, not premises needing judgments. A parent-D1 rule, like D-70.
2. **Path-scoped discharge** (SM-3): confirm that D-70's "discharged by a later step" means discharged on every path to the conclusion, and that discharges are listed in the standing report and the brief.
3. **Who may set fidelity and inspection** (SM-4): agents never submit `inspection` judgments; an agent's or the author's `fidelity` judgment never removes a rendering from the mandatory part. Confirm or choose a weaker labeling-only rule.
4. **Fidelity divergence as inapplicability** (SM-1): confirm that a `diverges` judgment creates review obligations on assessments that cited the affected tool checks. This keeps D-70's "never cited in a basis" and uses F-32.
5. **Designation guards** (FM-R15): should the core refuse designation of a non-human subject and designation by the work's author, or only label them?
6. **Dimensional screening and parsing inside UPMS under D-60** (FM-R24).
7. **Tool registration as an operator act** (FM-R23), as D-66 did for front ends.
8. **Checking agent of another model family**: required or preferred (SCIRE open question 2).
9. **Slice split** (§6): records, bindings-by-range, derivations, tool checks, fidelity, inspection and the brief first; parsing and dimensional screening after.

---

## 6. Simplicity: what can go or be deferred for a first useful version

1. **Defer parsing (§M.2) and dimensional screening (§M.4).** With bindings on source ranges (FM-R19), MP1, FM-1, FM-4, impact traversal and the brief need no parse. Dimensional screening needs a full parse, a dimension algebra, and convention handling that open challenge 2 predicts will mostly report "not covered". Ship them as a later slice with their own measured value.
2. **Fold `Model` into `SymbolContext` of kind `model`** with `defining_claims[]`, `regime`, `version` and `ssds_package_ref`. Variables, parameters and domain are symbol definitions in that context. One record kind fewer.
3. **Collapse inspection depth to scope plus a boolean `end_to_end`.** `spot` and `step_by_step` change no computed status; they are labels on the scope. If kept, rename `end_to_end` to `full`, since an "end-to-end inspection of three steps" is a contradiction in terms.
4. **Drop `faithful_under(c)`** (FM-R08) unless it is given a consequence.
5. **Drop the per-step time estimate** from the brief (FM-R31).
6. **Keep** the three separate statuses, the `renders` link with fidelity, the mandatory part as an exact projection, exposure-not-inspection, designation as a stored control, and the tool contract. They are the package.
7. **Cheapest evidence for adequacy:** TM-tests are deterministic and cover the stress cases; run them on two or three real derivations from a project draft before any seeded-error study.

---

## 7. Scientific inspectability (O1) check

Both the math D1 (§12) and the SCIRE proposal (§13) state the material realized record, readers and routine questions, and mark their product surfaces (derivation view, symbol view, brief, coverage view, tool-run view, workflow) as **beyond the requested deliverable**. That is correct, and this review's technical findings do not accept any of them; only the owner can. One inspectability-driven requirement is unmarked because it did not exist: the **discharge listing** in the standing report and brief (SM-3). If adopted it belongs in the derivation view, already marked beyond the deliverable. No realized scientific results were produced, run or reviewed in this review; no variants were evaluated.

---

## 8. What was not read

- Core 6.3 §§2, 3, 6 (except as cited), 7.1–7.3, 7.5, 7.7–7.9 (skimmed 7.7), 8.1, 8.3–8.4, 8.6, 9.1–9.2, 9.4–9.6, 9.10, 9.12–9.14 (9.13 read), 10.1–10.4, 10.6, 11, 13, 14, 15 (grep hits only), 18 (grep hits only), Appendices.
- The anonymous-review annex and the Slice 4 annex.
- Checking annex §9.8, §9.12, §9.13a and its acceptance tests.
- The 6.3 change history beyond grep hits for the hooks.
- SCIRE v0.4 beyond §8.6, §8.7, §10.1 and the heading outline; the SCIRE re-review and earlier reviews.
- SSDS texts; any external literature on proof assistants, computer algebra, natural deduction or inspection studies. The natural-deduction conditions in SM-3 are stated from the reviewer's own knowledge, not from a cited source, and should be checked by the outside-family reviewer.
- Earlier UPMS reviews (candidates 4 to 6.1) and the Codex review of the proposal, except where 6.3 or the 6.2 review quotes them.

---

## Appendix A. Coverage and method

- Hashes verified for the four files under review and the four inputs listed with hashes; none mismatched.
- Falsification targets 1–9 of the review request were each pursued: meaning (SM-1, SM-2, SM-4, FM-R01, FM-R03), bindings and notation (FM-R04, FM-R19), the brief (SM-3, SM-4, FM-R10, FM-R11), designated verifiers (FM-R02, FM-R12, FM-R15), D-70 (SM-2, SM-3), hooks (FM-R13 to FM-R17), tools and boundary (FM-R18, FM-R22 to FM-R24, FM-R30), evaluation and D2 (FM-R05, FM-R28), simplicity (§6).
- Materiality basis: a defect is material when a reader following the texts can be misled about a result's status in one of the ways the math D1 §1.2 names, or when the D1 and D3 texts cannot both be satisfied by one implementation.
- Realized results: none produced, run or reviewed. Variants: none evaluated. Gate evidence: none prepared; this record is review evidence for a same-family interim, not for Gate 0 or Gate 3.
