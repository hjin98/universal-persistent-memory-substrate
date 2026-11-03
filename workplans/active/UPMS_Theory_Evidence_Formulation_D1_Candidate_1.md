# UPMS Theory–Evidence Memory: D1 Formulation (Candidate 1)

**Kind:** Scientific Method Paper family (D1), first candidate.
**Date:** 3 November 2026
**Status:** PROPOSED D1 authority. Not reviewed, not accepted, not ratified. It is the D1 parent that UPMS architecture manual candidate 6 (`UPMS_Architecture_Manual_Review_Candidate_6.md`) concretizes. Neither file is accepted by being in the repository.
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request. No subagents were used.
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer **outside the Claude family**, then ratification by the product owner. Same-family review does not count (`AGENTS.md`).

---

## 0. Authority metadata

### 0.1 Inputs

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Theory–Evidence Memory: Structural Proposal v0.1 | `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md`, SHA-256 `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction; §3–§6 are the source of this formulation (§14 step 2); owner decisions D-20 to D-36 |
| SCIRE Conceptual Proposal v0.4 | SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md`, SHA-256 `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Theory semantics, §§3–7 (principles, record, inquiry, evidence, history) |
| SCIRE v0.4 same-family re-review | SCIRE repository, `workplans/active/SCIRE_v0.4_Re-Review.md`, SHA-256 `2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e` | Repairs SC-41, V4-06, V4-07, V4-12, V4-13 adopted here where they are D1 |
| Independent review of the proposal (Codex, OpenAI GPT-6 family) | `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md`, SHA-256 `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | NO-PASS for the proposal; its D1 findings (SC-TE01, SC-TE04, TE-R10 to TE-R12) are answered in §6, §4.2 and §7. It arrived after the first draft of this text |
| UPMS Architecture Manual, review candidate 5 | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md`, SHA-256 `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen input (D-23): record types, modality, screening, the §1.4 reopen triggers |

No accepted D1 authority exists for UPMS. Candidate 5 §1.4 needed none; its triggers 1 (source-reliability scores) and 4 (custody of scientific records) now fire (proposal §2.3). Nothing here amends SSDS authority or the SCIRE proposals.

### 0.2 What this document owns, and what it does not

| Owned here (D1) | Owned elsewhere |
| --- | --- |
| The meaning of every theory–evidence record and relation: modality, objection state, evidential relation kinds, use history, independence, origin, qualification, usability, warrants, tension kinds, comparability, standing, review obligations, source assessment, meaning identity, historical reads | Storage, commits, permissions, retrieval, sealing, deletion mechanics: candidate 6 (D3) |
| What may and may not be concluded from those records; which conclusions are reserved for attributed acts | Statistical comparison models, thresholds and any numeric score: D2, not yet opened (§9) |
| Adequacy and falsification criteria for this formulation | Discussion process, facilitation, review process, inquiry policy (the objection rule, finalization, authority): SCIRE front end (D-22) |

Security mechanisms (data-never-instructions, quarantine, scope rights) are not D1. They are D3 side constraints and appear here only where a scientific meaning depends on them.

---

## 1. Problem and intended use

### 1.1 The question

What must a project memory record, and what must it refuse to infer, so that a later reader (a person or an agent) can recover **what the project believed, why, how strongly, what bore against it, and how that changed**, without the memory itself deciding scientific truth?

The memory serves open, academic-like science (D-24): collaborative research among people and agents, with unpublished work inside projects and ordinary attribution. It also serves ordinary project memory, which uses the same records without the theory layer (proposal §7).

### 1.2 What the memory's "observables" are

The memory measures nothing physical. Its realized quantities are **epistemic records**: attributed statements with modality, assessments with their basis, relations with their conditions, objections with their state, decisions with their authority. The derived quantity of interest is the **standing** of a claim at a position in history (§6). Failure means a reader is misled about status, dissent, support, independence or history, for example an interpretation shown as an assertion, a disputed resolution shown as settled, or a fitted observation shown as independent confirmation.

### 1.3 Validity regime

- **In regime:** qualitative and ordinal epistemic states; explicit typed statements; human and agent assessors; projects of the pilot scale of candidate 6 §14.2.
- **Out of regime, by design:** calibrated probabilities of truth; automated scoring of sources; general theorem proving; inference of a speaker's intent or motive; any judgment of a person by the system (D-32).
- **Out of regime until D2 is opened:** quantitative statistical comparison of measurements (§5.6) and any numeric weight (§9).

---

## 2. Terminology and primitive notions

Every term is defined before later sections use it. "Record" means an immutable revision with identity, attribution and record time; "attributed act" means a record whose author is an authenticated principal (a human, or an agent principal with a human overseer) and that names what it acts on.

**Definition 2.1 — Event and observation.** An *event* `e` is an immutable record that something was said, received, observed or run, by whom, when and through which channel. It is not proof of its contents. An *observation* is an event whose payload is a measured, computed or reported result `o`. Its observation statement carries, where known: value `x`; unit; uncertainty `u`; conditions and regime `c`; instrument, code or method `μ`; origin `ω(o)` (Definition 2.9); qualification `q(o)`; observation time.

**Definition 2.2 — Claim and statement.** A *claim revision* `κ` is an attributed proposition with a modality `mod(κ) ∈ M`, conditions and regime `c(κ)`, optional time scope `τ(κ)` and links to source spans. `M` is:

| Modality | Meaning | Establishes truth? |
| --- | --- | --- |
| asserted | put forward as true by its asserter | No; it records that someone asserted |
| quoted | recorded words of another; fidelity is separate from content | No |
| reported | relayed from literature or another party | No |
| hypothesized | proposed for investigation | No |
| assumed | adopted for an inquiry, without a claim of truth | No |
| defined | a definition; establishes no truth or existence | No |
| predicted | an explicit prediction, with the conditions it covers | No |
| found | a recorded outcome of an investigation | No; it records that the investigation reported it |
| intended, committed, preferred | agentive project modalities | No |
| normative | a rule, with an external authority source | No; authority stays with the source |

A *statement* is a structured rendering of a claim (concept identifiers, typed value, qualifiers). Text is the record; structure is derived from it.

**Definition 2.3 — Three acts on an interpretation.** For a source span `s`:
- an *interpretation* `I(s)` is a claim extracted from `s`, attributed to its extractor (an AI or a person) as that extractor's reading;
- a *confirmation* is an attributed act by the speaker of `s`, and only the speaker, that `I(s)` is what they meant;
- an *adoption* is an attributed act by any participant that creates a new claim `κ'`, linked to `I(s)`, under the adopter's own attribution.

`I(s)` stays "interpretation, unconfirmed" until confirmed. Adoption changes nothing about `I(s)`.

**Definition 2.4 — Question.** A *question* `Q` is a record of an open problem with scope, kind (`ordinary` or `discrepancy`), live positions `pos(Q)` (claim references), status (`open`, `closed-answered`, `closed-unresolved`, `closed-unproductive`, `split`) and outcomes. Questions organize records and own none of them.

**Definition 2.5 — Objection.** An *objection* `O` has a target `tgt(O)` (a claim revision, an inference step, an evidence relation or an applicability condition), a ground, an author, a *handling* `h(O) ∈ {open, acknowledged, deferred, answered}` and an optional *resolution* `r(O) ∈ {resolved-by-assessment, withdrawn, superseded}`. The predicate

```text
unresolved(O)  ⇔  r(O) is absent
```

does not depend on `h(O)`.

**Definition 2.6 — Evidence relation.** An *evidence relation* `E = (o, T, k, m, c, a, U, b)` states how observation `o` bears on target claims `T` under:
- relation kind `k` (Definition 5.1);
- conditioning model `m` and conditions `c`;
- assessor `a`;
- use history `U` (Definition 5.2);
- binding `b` = the exact claim revisions, regime and method it assessed.

**Definition 2.7 — Inference step.** An *inference step* `S = ({P₁…Pₙ}; c) --[t]--> C` asserts that premises `Pᵢ` (claim revisions) under conditions `c` support conclusion `C`, with type `t ∈ {deductive, computational, statistical, causal, abductive, analogical, heuristic}`. It exists only when someone asserts it as an argument. A *stated reason* (one claim given as the reason for another inside a speaker's words) is claim content and is never an inference step until someone asserts it as one.

**Definition 2.8 — Judgment.** A *judgment* `J` is an attributed assessment of one target revision under a named scope `σ`, a ruleset `ρ` and an evidence snapshot `π`. Its kinds are: claim assessment, evidential assessment (of an evidence relation), inference assessment (of a step's validity under its conditions), comparability assessment (§5.7), objection resolution (§4.2), source assessment (§7), retention recommendation (candidate 6 §12). A claim assessment carries an epistemic status

```text
status(J) ∈ {supported, refuted, contested, unknown,
             supported-under(c), disfavored-under(c)}
```

where `c` is a stated condition set. Judgments in different `(σ, ρ)` coexist; none overrides another by recency.

**Definition 2.9 — Origin, qualification, usability.** For observation `o`:
- origin `ω(o) ∈ {external-system run, project-recorded, external-reported, uninstrumented}`;
- qualification `q(o) ∈ {qualified-for(scope), unqualified, provisional, failed, unknown}`, as stated by a named qualifying authority;
- usability `ν(o, use) ∈ {usable, usable-with-limits, under-review, not-usable}`, as concluded by an assessor for a given use.

**Definition 2.10 — Decision.** A *decision* `D` is an attributed act of kind `{inquiry, outcome, finalization, override, external, resolution}` with decider, authority basis (a reference to a project rule), scope and purpose, effective interval, basis statement reference, cited basis records `B(D)`, applicable objections and overrides, dissent, and exposure (the record versions and views the decider was shown). Which decisions are permitted, and when, is SCIRE policy; what a decision record means is defined here. The kind `resolution` is the decision that records an objection resolution by assessment (§4.2).

**Definition 2.11 — Review obligation.** A *review obligation* `R = (dependent, cause, assignee, state)` exists on a dependent relation or claim because a cause (retraction, correction, inapplicability, definition change, claim revision) reached it (§6.4). `state ∈ {pending, closed}`.

**Definition 2.12 — Meaning link.** A *meaning link* between two terms or statements is an attributed, contestable claim of kind `identical`, `equivalent-under(c)`, `refines` or `related`. The default for two similar statements is `unresolved possible match`.

**Definition 2.13 — Discovery link.** `arose_from(X, Y)` records that `X` was pursued because of `Y`.

**Definition 2.14 — Principal, person, work, channel.** A *person* is a human principal, or a group or institution of humans (labs, groups, venues count as persons here, D-32). An *agent principal* is not a person. A *work* is a bounded product: a publication, dataset, measurement, analysis, argument, reported result, model output. A *channel* is the route by which works of a kind reach the memory: an instrument, a dataset, a database, a model family, a person's reported results.

---

## 3. Principles (normative)

These restate SCIRE v0.4 §3 as memory semantics.

- **P1 — Record, interpretation and decision are distinct** (Definitions 2.1–2.3, 2.10).
- **P2 — Status changes only by an attributed act.** Repetition, summarization, persistence, retrieval rank, copying, age or archive placement change no status.
- **P3 — Handling an objection is not resolving it** (Definition 2.5).
- **P4 — Evidence is conditional** on a model and conditions (§5.1).
- **P5 — How data were used matters** (§5.2).
- **P6 — Agreement is not corroboration;** independence is a claim with dimensions (§5.4).
- **P7 — Competing explanations may coexist;** uncertainty does not justify choosing one.
- **P8 — Formal structure is not strength.** Length, connectivity, citation count, retrieval rank and consensus are not support.
- **P9 — Inquiry need not converge.** A null result, an exclusion or an unresolved contradiction can be a complete outcome.
- **P10 — Works are judged, people are not** (D-32; §7).
- **P11 — Importance is not truth.** What is kept active, archived or recommended for archive never changes standing (D-25).

---

## 4. Claims, objections and decisions

### 4.1 Modality preservation (normative)

**F-1.** For every derived rendering `ρ(κ)` (copy, summary, projection, export, narrative, translation), the modality and attribution of `κ` are recoverable from `ρ(κ)`, and `ρ(κ)` never presents `κ` in a stronger modality than `mod(κ)`. "Stronger" is any move from {quoted, reported, hypothesized, assumed, defined, predicted, interpretation-unconfirmed} to asserted or found.

**F-2.** An interpretation `I(s)` never supports a decision basis unless it is confirmed by the speaker or adopted (Definition 2.3). Confirmation and adoption never remove restrictions the source carries.

### 4.2 Objection semantics (normative)

**F-3 — Resolution.** `r(O) = resolved-by-assessment` only through a decision `D` of kind `resolution` that cites an objection-resolution judgment. That decision carries the fields of Definition 2.10 (authority basis, basis statement, exposure, dissent), so resolution costs what an override costs in visibility (re-review SC-41 repair).

**F-4 — Disputed resolution.** If an objection `O'` targets the resolution of `O`, then `O'` applies wherever `O` applied, and every projection that would have shown `O` shows "resolved by assessment, disputed" with both records. A dispute is never absorbed into the resolution's own record.

**F-5 — Self-resolution.** If the principal who resolved `O` is also the decider of a decision `D` whose basis `O` targeted, every projection of `D` labels the resolution "self-resolved". Whether self-resolution is permitted is SCIRE policy.

**F-6 — Applicability.** For a decision `D` with cited basis records `B(D)` (its basis claims and every record its basis statement cites by identity: premises, inference steps, evidence relations, applicability conditions), the applicable set is

```text
A(D) = { O : tgt(O) ∈ B(D) ∪ basis-claims(D) } ∪ { O' : O' disputes the resolution of some O ∈ A(D) }
```

`A(D)` is one hop from the basis, following re-review V4-06: the basis statement sets the coverage boundary, and omitting a material premise is a visible defect of the basis, not a way to escape objections. A front end may widen `A(D)`; nothing narrows it. Objections further upstream are reported on request with their coverage, as "upstream", and are not part of `A(D)`.

**F-7 — Travel.** Every `O ∈ A(D)` with `unresolved(O)` or a disputed resolution, and every override covering `D`, is part of every projection of `D`, whatever `O`'s handling, mode (open, single-blind, double-blind) or archive placement.

**F-8 — Anonymous objections.** An anonymous objection has the same semantics as any objection (F-3 to F-7): it is unresolved until resolved, it travels, and it is judged on its argument. Anonymity neither adds nor removes argumentative weight. That it never **blocks** a decision (D-36) is part of SCIRE's objection rule, not of its meaning; the memory records whether an objection was anonymous at each time, so the rule can be applied and audited. **This formulation reads D-36 narrowly** (Codex review SC-TE04): an anonymous objection is never a procedural veto, but an attributed judgment that independently establishes what it pointed out (for example, that a relied-on inference step is invalid) changes the route's status (§6.1) like any judgment, whoever supplied the lead. A reading of D-36 under which such a judgment could not affect the route would contradict F-25 and needs the owner's decision. A critic who later signs makes it a signed objection from then on; the earlier interval stays anonymous in history.

**F-9 — Claims about people are never anonymous** (D-32, D-33). A claim whose subject is a person's reliability, competence, conduct or motive is a signed, attributed claim, linked to any reply by the person judged.

### 4.3 Decisions (normative)

**F-10 — Exposure.** A decision's exposure is evidence about the decision process, never about the science. It identifies the record revisions and the as-of position of each view shown.

**F-11 — Joint sign-off binds content.** A signature binds one exact decision revision. Any change to the decision content creates a new revision on which earlier signatures do not count (re-review V4-20a).

**F-12 — A decision is not support.** A decision that makes a position "current" for a purpose never adds evidential or inferential support to it. Its dissent and applicable objections appear with it (F-7).

---

## 5. Evidence semantics

### 5.1 Relation kinds (normative)

**Definition 5.1.** `k` is one of:
- `entails(T)` or `refutes(T)`: deductive, under stated hypotheses;
- `favors(A over B | m)`: comparative, under model `m`;
- `adequate(A, purpose)` or `inadequate(A, purpose)`: absolute, under stated criteria;
- `prediction-succeeded(P)` or `prediction-failed(P)`: for an explicit `predicted` claim `P`;
- `consistent-with(T)`: no discrimination among the live positions;
- `bears-on(T), unassessed`.

**F-13.** Comparative and absolute relations are recorded separately: `favors(A over B)` together with `inadequate(A)` and `inadequate(B)` is consistent. No relation implies another kind.

**F-14.** Reassessment adds a judgment on `E`; it never rewrites `o` or an earlier judgment.

### 5.2 Use history and warrant

**Definition 5.2.** The use history `U(E)` is a chronological, non-exclusive sequence of entries `(dataset, subset, analysis revision, use, breadth, leakage, coverage)`, where `use ∈ {suggested, fitted, selected, tested-pre-specified, model-check, not-applicable}`, `breadth` records the variants tried, `leakage` records known shared dependence, and `coverage` marks intervals where the history is unknown.

**Definition 5.3 — Independent confirmation.** `E` is an *independent confirmation* of `κ` within coverage `Γ` if and only if
1. no entry of `U(E)` within `Γ` has `use ∈ {suggested, fitted, selected}` for `κ` or an ancestor revision of `κ`;
2. no shared leakage, instrument, code or population dependence between `o` and the data that suggested, fitted or selected `κ` is recorded within `Γ`;
3. `Γ` is stated, and an unknown interval inside `Γ` falsifies the label.

The label is narrow. Uses that fail it can still carry evidential value; they are not called independent confirmation.

**F-15 — Inference-specific warrant.** What `E` justifies is decided by the warrant its assessor names (for example, a selection-adjusted analysis under its assumptions, or a proof under its hypotheses and checking basis). Use-history roles may be `not-applicable` for proofs.

### 5.3 Origin, qualification, usability

**F-16.** `ω`, `q` and `ν` are recorded separately. `ω(o)` never implies `q(o)`: an external-system run may be unqualified, failed or provisional.

**F-17 — Uninstrumented observations.** If `ω(o) = uninstrumented`, `o` is carried with that label and is never the **sole** backing of a finalization or published outcome until *upgraded*: its material inputs, conditions and regime are recovered and its admissibility assessed. Re-entering the same number elsewhere is not an upgrade (re-review V4-12 (ii), restored).

**F-18 — Snapshots of external results.** A retained snapshot of an external result (for example from SSDS) is evidence of the value at the cited revision. Its qualification is "as of the snapshot; later changes unknown", and a claim relying on it states this (re-review V4-13).

### 5.4 Independence

**Definition 5.4.** An *independence claim* between two lines of evidence states the dimensions in which they are independent (data, method, instrument or code, model, analyst, model family, prompt, retrieved sources) and a coverage statement.

**F-19.** Missing provenance never establishes independence. Unknown authorship is never treated as independent (from SSDS). Copies of one source are one source. Several agents agreeing from shared inputs are one line of evidence for counting, though each argument stays inspectable.

**F-20 — Identity relations, not attributes.** Who did an analysis enters assessment **only** through identity relations: same principal or not, declared collaboration, declared conflict of interest, same sealed author (for anonymous critiques). Using these to count independence, or to check a reviewer's conflict, is not judging a person. No attribute or aggregate of a person (§7.3) enters any assessment.

### 5.5 Applicability over time

**F-21 — Staleness.** `E` binds the claim revision, regime and method it assessed (`b`). When `κ` is revised to `κ'`, `E` is **under review** for `κ'` and does not carry over silently. A stale failing observation is not admissible evidence against `κ'`, and a stale passing one is not admissible confirmation of `κ'` (from SSDS).

### 5.6 Tension kinds

**Definition 5.5.** A tension between records is one of:
- **logical contradiction:** two statements cannot both hold under the same premises;
- **statistical disagreement:** observations of the same estimand differ by more than a **declared comparison model** makes plausible under a **declared decision rule**;
- **failed prediction:** an observation differs from what a `predicted` claim says in the conditions it covers;
- **not comparable for this target:** the compared quantities answer different questions, relative to a stated target claim (§5.7);
- **unexpected observation:** against expectation, not against a statement;
- **data error,** including unit and definition errors;
- **incommensurable models:** the frameworks define the compared quantity differently.

**F-22.** A statistical disagreement is never called a logical contradiction. Without a declared comparison model and decision rule there is no statistical disagreement, only a cue that values differ (§9, D2 hand-off).

**F-23 — Regime as the test.** If a claim asserts invariance across regimes, a difference between regimes is the test, not a reconciliation. A claim's coverage is recorded so that narrowing the framing cannot hide a mismatch (SCIRE §5.3, subgroup example).

**F-24 — No automatic reconciliation.** Pooled means with inflated errors presuppose a shared estimand; stratification by a variable affected by cause and outcome can create bias; a parameter fitted to the same data is not independent confirmation. Each is a claim needing its own justification.

### 5.7 Comparability

**Definition 5.6.** A *comparability assessment* is a judgment relative to a target claim. It names: the target claim and the population, regime and quantity it is about; the compared quantities, their estimand definitions, units and conventions; what the target predicts about change or invariance between the compared conditions; the uncertainty, the comparison model and known shared dependencies. Completing it does not settle the question.

### 5.8 Warrants

**F-25 — Warrants, not actors.** Support that is circular, or that has no applicable root in events, is not a warrant, whoever produced it. Shared roots are not new independent evidence. A flag, a view, a narrative, a retrieval rank or a recommendation is never evidence. A machine proof checker can supply a valid check under named assumptions; a human's insertion does not validate a circular warrant.

**F-26 — Discovery is not support.** `arose_from` is never traversed as support.

### 5.9 Meaning

**F-27.** Curating a vocabulary label is indexing; it asserts no scientific equivalence. Scientific equivalence is a meaning link (Definition 2.12). A label may be recorded as **contested**, and statements using it are then compared only within the meaning each statement declares. A change of meaning creates review obligations, never truth changes.

---

## 6. Standing

### 6.1 Route status

For a claim revision `κ`, a *route* is one evidence relation `E` with `κ ∈ T`, or one inference step `S` with conclusion `κ`. Each route has a status computed from recorded judgments, objections and obligations:

| Route status | Condition |
| --- | --- |
| **unassessed** | no evidential or inference assessment of the route under the reader's `(σ, ρ)` |
| **under review** | a pending review obligation exists on the route, or the route binds an earlier revision of `κ` (F-21) |
| **challenged** | an objection targeting the route (or, for an inference step, one of its premises or conditions) is unresolved or has a disputed resolution |
| **broken** | the route's assessment is negative (step invalid; observation not usable for this use); or a premise is retracted, superseded or has status `refuted` in `(σ, ρ)`; or the route is circular or rootless (F-25) |
| **assessed-sound** | the route's latest assessment in `(σ, ρ)` is positive and effective, every premise has an effective judgment in `(σ, ρ)` with status `supported`, or `supported-under(c')` with `c'` compatible with the step's conditions, no effective adverse judgment applies to the route or a premise, and none of the above holds |

Several conditions can hold; the report lists all of them, and the table order is used only to choose a one-word label.

**Well-foundedness** (Codex review SC-TE01, TE-R11). Route status depends on premises only through their own **effective judgments** (fresh at `p` under the ruleset's freshness rule), never through their projected standing, so it is computed in one pass with no fixed point. A route whose support, followed through inference steps, reaches its own conclusion is **circular** and gives no positive warrant; a recursive definition (modality `defined`) or a proof by induction is not a support cycle. Negative information counts: an added adverse judgment or objection changes a route's status even when no cited revision changed. Ordinal statuses are never multiplied, averaged or voted on.

### 6.2 Standing report (normative)

**Definition 6.1.** The *standing* of `κ` for a reader at position `p` is the report

```text
standing(κ, p) = { judgments of κ per (σ, ρ), with status;
                   routes of κ, each with its status and its own standing one level down;
                   A(κ): objections targeting κ or its routes, with state and mode;
                   review obligations on κ and its routes;
                   source assessments of the works κ rests on;
                   decisions that rely on κ, with dissent;
                   coverage: what the reader may not read, what is unprocessed,
                             and where traversal stopped }
```

computed over the exact revisions committed at `p` that the reader may read.

**F-28 — Status, not winners.** `standing` contains no aggregate verdict, score or ranking of alternatives. Two derived predicates are defined exactly, for front ends to use:

Standing never merges kinds of assessment that SCIRE v0.4 §5.4 keeps apart: qualitative plausibility, evidential bearing, inferential validity, model adequacy, quantitative probability, participant judgment and decision each stay in their own records and labels.

```text
has-sound-route(κ)      ⇔  some route of κ is assessed-sound and no O ∈ A(κ) is unresolved or disputed
has-open-challenge(κ)   ⇔  some O targeting κ or one of its routes is unresolved or disputed
```

A position is shown as "current" only where a recorded decision makes it so (F-12).

**F-29 — Projection, not admission.** Propagating standing from premises to conclusions is computed at read time over exact revisions and is recomputed when an input changes. No stored judgment is created or changed by propagation.

**F-30 — Depth and coverage.** The report is exact to the depth it is computed. Where the traversal is bounded, the bound is part of `coverage`, and nothing beyond it is reported as sound or as absent.

### 6.3 History

**F-31.** Two reads are answerable and distinct:
- **as held then** at record position `t`: the records and standing as committed by `t`, evaluated under the rules in force at `t` (from SSDS: historical decisions are never recomputed under newer rules);
- **as now assessed about then:** current assessments of records dated before `t`.

A later correction is never reported as what was held earlier. The memory never invents when somebody learned something. Where explicit deletion removed records (candidate 6 §12), "as held then" is incomplete and says so (re-review V4-20c).

### 6.4 Retraction and review obligations

**F-32 — Creation.** When a source is retracted or corrected, found inapplicable, or has a definition changed, or a claim is revised, a deterministic traversal of the provenance, evidential, inferential and meaning-link graphs within stated coverage creates a review obligation on each dependent route and claim, with an assignee.

**F-33 — Present eligibility.** While an obligation on a route is pending, the route is under review (§6.1) and cannot newly back a consequential use unless an explicit qualification is recorded. That qualification travels like an override (F-7).

**F-34 — Closure.** An obligation closes **only** through an attributed reassessment of the route's usability. Assigning, acknowledging, archiving or answering it does not close it (re-review V4-07).

**F-35 — No truth propagation.** Retraction, revision and definition change never make anything true or false. Past decisions are flagged, never undone.

### 6.5 Judgment on judgment (open; owner decision §15 item 6)

Candidate 5 §9.3 admits no assessment whose inputs include another judgment's status. F-29 removes most of the need: standing propagation is a projection. One case remains: an assessor who cites premises' judgments in a new judgment.

**Proposed (open):** such a judgment is epistemically legitimate if and only if
1. it records the exact judgment revisions it relied on (its *judgment basis*), alongside its sources, each with a **dependency mode**: `exposure` (it was shown), `historical` (cited as a fact about what was assessed), `content` (its assessed content is relied on) or `current` (it must stay effective). Only `content` and `current` entries are epistemic dependencies (Codex review §4 item 1);
2. the judgment basis is acyclic: no judgment depends, through judgment bases, on itself or on a judgment about its own target;
3. it becomes **stale** when any `current` entry stops being effective (superseded, made ineffective by new evidence or a rule change without being superseded, under a pending review obligation, or itself stale), or when an adverse judgment or unresolved objection is added on a cited judgment's target; a stale judgment's status is reported as historical until reassessed;
4. a judgment basis never includes a flag, a view, a narrative, a recommendation or a source assessment as support (F-25).

The D3 realization and the decision whether such judgments may be admitted are in candidate 6 §9.10. Until the owner decides, candidate 5's rule governs admission, and judgments with a judgment basis are evidence-only.

---

## 7. Source assessment

### 7.1 Meaning

**Definition 7.1.** A *source assessment* is a judgment about a **work or a non-person channel** as an evidence channel **for a kind of claim**. Its value is ordinal:

```text
established > generally-reliable > mixed > unreliable,  plus  unknown (unordered)
```

It is never a probability or a calibrated quantity. Its recorded basis is: provenance class and channel integrity; for non-person channels only, track record (Definition 7.2); retractions and corrections; declared conflicts of interest; known shared dependencies.

**Definition 7.2 — Track record (non-person channels only).** For channel `ch` and claim kind `k`, the track record is the set of later judgments `J` on claims of kind `k` from `ch` such that `J`'s assessor is not among the authors of the assessed claim, and `J`'s basis consists of evidence independent of `ch` in the sense of Definition 5.4. A judgment whose basis is agreement with the prevailing position, rather than independent evidence, is excluded.

**F-36 — Assessment, not computation.** A source assessment is made by an attributed assessor, who states how the basis yields the ordinal value. No rule maps counts to a value automatically in this formulation. An automatic mapping, a numeric score or calibration reopens D2 (§9).

**F-37 — Limited use.** A source assessment may order retrieval and fact-checking work. It never sets a claim's standing alone and never hides a claim.

### 7.2 Guards

**F-38 — No reward for agreement.** Disagreeing with the prevailing theory is never a mark against a source; only outcomes assessed independently of the source and of the claim's own position count (Definition 7.2).

**F-39 — No person-level output** (D-32). For any person `π`, no score, rank, rating, track record, tendency, outcome count or label is computed, stored or shown. Authorship is never an input to a work's assessment, to a source assessment or to retrieval ranking. No view aggregates works by author to compare or characterize authors. A work never borrows standing, good or bad, from its author's other work. F-20's identity relations are the only use of authorship in assessment.

**F-40 — Humans judge people, accountably.** A judgment of a person exists only as a signed human claim (F-9), linked to the person's replies. It never feeds any assessment or ranking, is never surfaced proactively and is never repeated by an agent as its own view.

**F-41 — Proxies.** Institutions, groups and venues are persons for F-39. A channel must be a technical production or measurement mechanism with its own error behavior; a collection defined by authorship or affiliation (one researcher's papers, a lab's outputs, a venue's articles) is not a channel (Codex review TE-R12). An agent principal is a channel (a model family as a technical system), not a person; its assessment must not serve as a proxy for its human overseer.

**F-41a — Track-record coverage.** A track record is reported with its denominator and coverage: the channel's claims of the kind, how many were later assessed, and how they came to be assessed. Preferential checking of disfavored sources biases an otherwise independent collection.

**F-42 — Conflicts of interest** are facts about the work they concern, never judgments of a person.

---

## 8. Assumptions, limitations and uncertainty

### 8.1 Assumptions

- **A-1:** Attribution is authentic within the deployment's trust boundary (candidate 6 §7). If attribution can be forged, every F-rule that names an author fails.
- **A-2:** Assessors state their warrant and basis. The memory cannot make an assessor honest; it makes the assessor's basis inspectable.
- **A-3:** The front end records basis statements that cite records by identity. F-6 is only as strong as those citations.
- **A-4:** Use history is reported by people and agents. Unknown intervals are recorded as unknown, never as "no use".

### 8.2 Limitations

- Truth-based robustness (proposal §8.3) resists planted falsehoods only where independent, well-supported evidence exists. A plausible fabrication in a sparsely evidenced area is resisted weakly. Instruction injection and disclosure are not truth problems and are not addressed by this formulation.
- Internal consistency of natural-language arguments is mostly not checkable deterministically; it is flagged for human review.
- Blinding is best effort: style, self-citation and timing can identify authors.

### 8.3 Uncertainty semantics

- Model-stated percentages are not calibrated probabilities and are never stored as such.
- Uncertainty attached to an observation (`u`) is recorded as stated, with its type (standard uncertainty, interval, distribution reference). Its use in comparison is a D2 matter (§9).
- Standing is ordinal and structural. Its uncertainty is expressed by coverage (what was not read, not processed, not traversed) and by conditions on status, never by a number.

---

## 9. D1 → D2 hand-off

D2 is not opened by this candidate. The formulation hands over only these items, each of which is currently realized without any numeric method:

| Item | D1 constraint handed to D2 | Until D2 is accepted |
| --- | --- | --- |
| Statistical disagreement (F-22) | A disagreement candidate is defined only relative to a declared comparison model and decision rule, with the estimand, uncertainty type and independence assumptions named | The evidence–evidence channel emits only unit, definition and "values differ, no comparison model" cues |
| Prediction check | Whether an observation falls outside what a typed prediction allows needs a stated tolerance or model | The evidence–theory channel emits "prediction check" flags only for exact typed values and stated intervals, and "not covered" cues |
| Any numeric score, calibrated confidence, automatic source-assessment mapping | Must preserve F-36 to F-42 and P8 | Not permitted |
| Small-model and embedding candidates | Propose only; never decide | No D2 needed (candidate 5 §1.4 trigger 3 stays closed) |

---

## 10. External adequacy and falsification

### 10.1 What would show this formulation adequate

The formulation is adequate if real readers, using its records, recover status, dissent, support, independence and history more faithfully than with an archive plus search, at acceptable cost. The proposal's experiments test this:
- **E1 (status and dissent loss),** **E2 (orientation)** and **E4 (elicitation cost)** from SCIRE v0.4, run on UPMS records;
- **E5 (standing faithfulness),** new: given real histories, does `standing` and the understanding section report status, dissent and retractions more faithfully, and at what reader cost?

The owner sets error and cost limits before each study. No experiment has been run; nothing here claims adequacy.

### 10.2 What would falsify or reopen it

- A trajectory in which a reader, following F-1 to F-42, is shown a disputed resolution as settled, an interpretation as an assertion, a fitted observation as independent confirmation, a stale relation as current, or a person characterized by the system.
- A trajectory in which F-6's one-hop boundary systematically hides material objections despite complete basis statements.
- E5 showing that `standing` misleads readers more than an archive plus search.
- A need for calibrated probability, automatic source scoring or person-level outputs. The last is excluded by D-32 and would need the owner.

### 10.3 Stress cases carried from the SCIRE reviews

Each must fail as intended against this formulation:
1. Acknowledge and defer, then finalize: fails by F-7.
2. Resolve, dispute, then finalize: fails by F-3, F-4 and F-7 (SC-41).
3. Retract a source, acknowledge the obligation, then rely: fails by F-34 (V4-07).
4. Fitted data presented as confirmation: fails by Definition 5.3.
5. Two agents agree from shared inputs: one line of evidence (F-19).
6. Constant-across-regimes claim against regime-varying data: a failed prediction, not a reconciliation (F-23).
7. A dissenting source down-ranked for disagreeing: fails by F-38.
8. A narrative that drops the live alternative: flagged (candidate 6 §10.5.3).

---

## 11. Scientific inspectability (O1)

**Material realized record.** Events and observations with origin and qualification; claims with modality, conditions and acts; questions; evidence relations with use history; inference steps; objections with handling, resolution and mode; judgments, including comparability, source and retention-recommendation judgments; decisions with authority, exposure and dissent; review obligations; flags with cues; archive and deletion records; sealed attribution, blocks and appeals for anonymous review. **Destructive boundaries:** only explicit deletion (candidate 6 §12); archival is not destructive.

**Intended readers.** Researchers, PIs, reviewers and their agents; for project memory, the users, overseers, incident investigators and operators of candidate 5 §1.4.

**Routine questions.** What do we believe about X, why and how strongly? What bears against it? What changed since a given time? What was retracted, and what depends on it? Was this observation used to fit or to test? Which sources does this rest on, and how independent are they? What did we hold then? What is recommended for archive, and why?

**Product inspectability surfaces.** All are **beyond the requested deliverable** of this formulation and bind only after the owner accepts them: question pages and the understanding section; the standing report with its basis; fact-check results; the retraction impact view; the retention recommendation queue; masked review packages and the block-and-return flow. Candidate 6 §17.2 repeats this marking. Technical acceptance of this formulation does not accept them.

No realized scientific results were produced or examined in drafting this document, and no variants were evaluated.

---

## 12. Supporting rationale and provenance

| Source | Contribution |
| --- | --- |
| SCIRE v0.4 §3 | P1–P9 |
| SCIRE v0.4 §4.3, §4.4, §4.5 | Definition 2.3; F-3 to F-7, with the re-review's SC-41 and V4-06 repairs |
| SCIRE v0.4 §5.3 | Definitions 5.5 and 5.6; F-22 to F-24 |
| SCIRE v0.4 §6 | Definitions 5.1 to 5.4, 2.9; F-13 to F-19; F-25; F-32 to F-35 with the V4-07 repair |
| SCIRE v0.4 §7.1 | F-31 |
| Re-review V4-12 | The status vocabulary in Definition 2.8 and F-17, restored |
| SSDS 8.0 (through the proposal §10.2) | F-19 (unknown authorship), F-21 (stale evidence), F-31 (historical rules), the judgment basis in §6.5 |
| Proposal §6.4 and D-32 | §7 |

Literature is not cited as authority. The formulation borrows the distinctions of argumentation and evidence theory as used in the SCIRE texts; it does not import any external theorem.

---

## 13. Evidence and dependency impact

- **Concretized by:** UPMS candidate 6 (D3), which maps each F-rule to a record, check or projection and an acceptance test (its §15 and Appendix A).
- **Front-end dependents:** SCIRE's front-end specification (proposal §14 step 2) relies on F-3 to F-12 and must not narrow them.
- **Reopen triggers** in candidate 5 §1.4: triggers 1 and 4 are answered by this formulation; trigger 1 reopens again for any numeric score (§9). Triggers 2 and 3 are unchanged.
- **No accepted predecessor:** there are no recorded tensions against accepted D1 authority to carry, because none exists. Tensions recorded against the SCIRE v0.4 texts are carried as listed in §12.

---

## 14. Findings raised while drafting

These are the author's findings on the proposal's D1 content, recorded for the reviewer. None is a Serious Challenge to a D1 meaning; the D3-level challenges, including two Serious Challenges to the proposal's text, are in candidate 6 §18.3.

| ID | Finding | Disposition here |
| --- | --- | --- |
| D1-F1 | The proposal says authorship is never an input to assessment (§6.4), and also counts independence by analyst (§5.4) and checks reviewer conflicts by identity (§7.1). Read literally, these conflict | F-20: identity relations only, never attributes or aggregates |
| D1-F2 | The proposal's decision kinds omit resolution by assessment, while SC-41's repair (carried with a back-end fix, proposal §13.2) needs resolution to carry decision fields | Definition 2.10 adds `resolution`; F-3 |
| D1-F3 | "Applies" was unbounded in SCIRE v0.4 and is a back-end invariant in the proposal (TE-04) | F-6 fixes a one-hop default from the cited basis, which a front end may widen |
| D1-F4 | Re-review V4-12 (iii), de-attribution of a person from derived statements on request, and (iv), where an argument may stop, are carried by neither the proposal nor this text | Open: owner decision (candidate 6 §18.2) |
| D1-F5 | The re-review's D1 note on V3-10 asks which test or threshold a statistical disagreement uses | F-22 and §9: no disagreement without a declared model and rule; method is D2 |
| D1-F6 | The Codex review (SC-TE01) shows that exact judgment references alone do not make support current: an unchanged revision can lose effectiveness, a new adverse judgment supersedes nothing, and cyclic support has no defined evaluation | §6.1 well-foundedness; §6.5 dependency modes and currentness. Judgment on judgment stays open |
| D1-F7 | The Codex review (SC-TE04) shows that an absolute reading of D-36 would let anonymity shield an independently verified invalidity | F-8 narrow reading; owner decision |
| D1-F8 | The Codex review (TE-R12) shows channel assessment can proxy for a person or lab | F-41, F-41a |

---

## 15. Open challenges

1. **Judgment on judgment** (§6.5): proposed, open, left to review (proposal §15 item 6).
2. **De-attribution on request** (D1-F4): owner decision.
3. **Whether F-6's one-hop default is enough** for SCIRE's objection rule, or a front end should widen it by default: to be tested by E1 and E5.
4. **Whether E5's faithfulness criterion can be stated operationally** before data: the owner sets error and cost limits first.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the same model family and model as the proposal, candidates 4.1 and 5, the SCIRE v0.3 and v0.4 texts and the SCIRE v0.4 re-review. Shared blind spots are likely. A reviewer outside the Claude family is required before acceptance.
- **Read directly:** the proposal in full; candidate 5 §§1–18 in full (Appendix A by heading); SCIRE v0.4 §§2–7 in full; the SCIRE v0.4 re-review §§1–9 in full; the Codex review of the proposal in full, after the first draft.
- **Anchoring:** the Codex review was read after drafting; the repairs it prompted were fitted to an existing text, and their adequacy is for the reviewer to judge.
- **Not read:** SCIRE v0.4 §§8–17 (facilitation, orientation, interfaces, invariants, experiments), except as summarized by the proposal and the re-review; SSDS sources (reached only through the proposal's §10).
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated.
