# UPMS Theory–Evidence Memory: D1 Formulation (Candidate 1.3)

**Kind:** Scientific Method Paper family (D1), first candidate, revision 1.3. It replaces candidate 1.2 for review; candidates 1, 1.1 and 1.2 stay unchanged as its predecessors. Appendix B maps 1 → 1.1, Appendix D maps 1.1 → 1.2 and Appendix E maps 1.2 → 1.3.
**Date:** 3 November 2026
**Status:** PROPOSED D1 authority. Not reviewed, not accepted, not ratified. It is the D1 parent that UPMS architecture manual candidate 6.3 (`UPMS_Architecture_Manual_Review_Candidate_6_3.md`) concretizes. Neither file is accepted by being in the repository.
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request. No subagents were used. Revision 1.1 follows the author's re-reading of the Codex review against the operative text, at the product owner's request. Revision 1.2 repairs the findings of a same-family review of 1.1 and folds in the owner's decisions D-37 to D-46 and those of §16 here, at the owner's direction ("Draft on these", 3 November 2026). Revision 1.3 repairs the findings of a second same-family review, of 1.2, by Claude Fable 5.1, and folds in owner decisions D-63 to D-70 ("Proceed with your recommendation", 3 November 2026).
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
| UPMS Theory–Evidence Formulation, D1 candidate 1.2 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md`, SHA-256 `219a81bbfa061cf5914df1c144246416ce1b28ea15a6f5985c1a4151ecd01ed2` | Immediate predecessor; changes in Appendix E |
| UPMS Theory–Evidence Formulation, D1 candidate 1.1 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md`, SHA-256 `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | Predecessor; changes in Appendix D |
| Same-family review of candidate 1.1 and architecture candidate 6.1 (Claude Opus 5.5, fresh context) | `workplans/active/UPMS_Candidate_6_1_Same_Family_Review.md`, SHA-256 `f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592` | NO-PASS; SC-R1 to SC-R3, R-01 to R-20; same family, so not independent |
| Same-family review of candidate 1.2 and architecture candidate 6.2 (Claude Fable 5.1, fresh context) | `workplans/active/UPMS_Candidate_6_2_Same_Family_Review.md`, SHA-256 `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9` | NO-PASS; S62-1 to S62-3, F62-01 to F62-18; same family, so not independent |
| Owner decisions D-37 to D-46 | `workplans/active/UPMS_Owner_Decisions_2026-11-03.md`, SHA-256 `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Folded in here |
| Owner decisions D-63 to D-70 | `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md`, SHA-256 `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Folded in here |
| UPMS Theory–Evidence Formulation, D1 candidate 1 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md`, SHA-256 `65b736253c7bcb7e8a0f1d6dafc0251cc59adfb56dfd310cf336ad03766d30fc` | Predecessor; changes in Appendix B |
| UPMS Architecture Manual, review candidate 5 | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md`, SHA-256 `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen input (D-23): record types, modality, screening, the §1.4 reopen triggers |

No accepted D1 authority exists for UPMS. Candidate 5 §1.4 needed none; its triggers 1 (source-reliability scores) and 4 (custody of scientific records) now fire (proposal §2.3). Nothing here amends SSDS authority or the SCIRE proposals.

### 0.2 What this document owns, and what it does not

| Owned here (D1) | Owned elsewhere |
| --- | --- |
| The meaning of every theory–evidence record and relation: modality, objection state, evidential relation kinds, use history, independence, origin, qualification, usability, warrants, tension kinds, comparability, standing, review obligations, source assessment, meaning identity, historical reads | Storage, commits, permissions, retrieval, sealing, deletion mechanics: candidate 6.3 (D3) |
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

- **In regime:** qualitative and ordinal epistemic states; explicit typed statements; human and agent assessors; projects of the pilot scale of candidate 6.3 §14.2.
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

**Definition 2.5 — Objection.** An *objection* `O` has a target `tgt(O)` (a claim revision, an inference step, an evidence relation, an applicability condition or a resolution), a ground, an author, a *handling* `h(O) ∈ {open, acknowledged, deferred, answered}` and an optional *resolution* `r(O) ∈ {resolved-by-assessment, withdrawn}`, where `withdrawn` means withdrawn by the objection's own author. Nothing that happens to the target resolves `O`: a revision carries it (F-3a), and a withdrawal of the target leaves it unresolved (F-3b; owner decision D-63). The predicate

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

**Definition 2.7 — Inference step.** An *inference step* `S = ({P₁…Pₙ}; c) --[t]--> C` asserts that premises `Pᵢ` (claim revisions) under conditions `c` support conclusion `C`, with type `t ∈ {deductive, computational, statistical, causal, abductive, analogical, heuristic}`. It exists only when someone asserts it as an argument. A *stated reason* (one claim given as the reason for another inside a speaker's words) is claim content and is never an inference step until someone asserts it as one. A *derivation* is a set of inference steps asserted together as one argument. A step of a derivation may **introduce** a hypothesis, a claim of modality `assumed` local to that derivation, and a later step of the same derivation may **discharge** it, so that the later step's conclusion no longer depends on it (for example by implication introduction, case analysis or reductio). A discharged hypothesis is not a premise of the conclusion it was discharged from (§6.1; owner decision D-70).

**Definition 2.8 — Judgment.** A *judgment* `J` is an attributed assessment of one target revision under a named scope `σ`, a ruleset `ρ` and an evidence snapshot `π`. Its kinds are: claim assessment, evidential assessment (of an evidence relation), inference assessment (of a step's validity under its conditions), comparability assessment (§5.7), objection resolution (§4.2), source assessment (§7), retention recommendation (candidate 6.3 §12). A child formulation may add kinds: the mathematics formulation adds `fidelity` (whether a rendering says what a claim says) and `inspection` (what a human inspected, and to what depth). Those are separate statuses; they never enter route status (§6.1) and are never cited in an inference assessment's basis (owner decision D-70). A claim assessment carries an epistemic status

```text
status(J) ∈ {supported, refuted, contested, unknown,
             supported-under(c), disfavored-under(c)}
```

where `c` is a stated condition set. Judgments in different `(σ, ρ)` coexist; none overrides another by recency. Every judgment has a validity interval, unbounded unless it states one. A judgment may **supersede** only an earlier judgment by the same assessor; a judgment by another assessor of the same target under the same `(σ, ρ)` is a concurrent head, never a replacement (same-family review F62-01). The assessor of a judgment is always named to its readers: anonymous-role sessions never submit judgments (F-8; owner decision D-64).

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

**F-3a — Revision carries objections** (same-family review SC-R1). When `tgt(O)` is revised to a successor revision, `O` is **carried** to the successor with the state "carried, pending re-examination". It stays unresolved, applies and travels exactly as before, until its author withdraws it, its author rebinds it to the successor (which only records that the author re-examined it), or a `resolution` decision under F-3 states that the successor no longer meets it. A reviser who thinks the revision answers `O` records that resolution, and F-5 labels it "self-resolved" where it applies. A revision never resolves anything by itself. A decision that cited the earlier revision keeps showing `O` in its current projections, whatever later happens to `O`'s target. **Steps and relations** (same-family review F62-05): an inference step or evidence relation that names an earlier one through `supersedes` is a revision of it for this rule when it keeps the same conclusion (a step) or the same observation and targets (a relation), and objections on the earlier one are carried.

**F-3b — Withdrawing a target does not resolve its objections** (owner decision D-63; same-family review S62-1). When `tgt(O)` is retracted, withdrawn or deleted by its author with no successor revision, `O` stays unresolved, with the state "target withdrawn, not re-examined". It stays live and is shown on the target's withdrawal or deletion marker and on the page of every question in which the target was a position, until its author withdraws it, its author rebinds it to another record (for example a new claim that restates the target), or a `resolution` decision under F-3 resolves it. A withdrawn record cannot be cited by a new decision, so `O` joins no new `A(D)` through it; a decision that cited the target keeps showing `O` (F-3a, F-7). Whoever withdraws or deletes a target is first shown its unresolved objections.

**F-4 — Disputed resolution.** If an objection `O'` targets the resolution of `O`, then `O'` applies wherever `O` applied, and every projection that would have shown `O` shows "resolved by assessment, disputed" with both records. A dispute is never absorbed into the resolution's own record.

**F-5 — Self-resolution.** If the principal who resolved `O` is also the decider of a decision `D` whose basis `O` targeted, every projection of `D` labels the resolution "self-resolved". Whether self-resolution is permitted is SCIRE policy.

**F-6 — Applicability.** For a decision `D` with cited basis records `B(D)` (its basis claims and every record its basis statement cites by identity: premises, inference steps, evidence relations, applicability conditions), the applicable set is

```text
A(D) = { O : tgt(O) ∈ B(D) ∪ basis-claims(D) } ∪ { O' : O' disputes the resolution of some O ∈ A(D) }
```

For every route `R ∈ B(D)` (evidence relation or inference step), `A(D)` also contains every objection whose target is an **endpoint** of `R`: for an evidence relation, its observation (the event and the observation claim), its conditioning model and condition, and every calibration, definition or model record it cites by identity; for an inference step, its premises and conditions (same-family review R-01). `A(D)` is one hop from the basis, following re-review V4-06: the basis statement sets the coverage boundary, and omitting a material premise is a visible defect of the basis, not a way to escape objections. A front end may widen `A(D)`; nothing narrows it. Objections further upstream are reported on request with their coverage, as "upstream", and are not part of `A(D)`.

**F-7 — Travel.** Every `O ∈ A(D)` with `unresolved(O)` or a disputed resolution, and every override covering `D`, is part of every projection of `D`, whatever `O`'s handling, mode (open, single-blind, double-blind) or archive placement.

**F-8 — Anonymous objections.** An anonymous objection has the same semantics as any objection (F-3 to F-7): it is unresolved until resolved, it travels, and it is judged on its argument. Anonymity neither adds nor removes argumentative weight. That it never **blocks** a decision (D-36) is part of SCIRE's objection rule, not of its meaning; the memory records whether an objection was anonymous at each time, so the rule can be applied and audited. **D-36 is read narrowly (owner decision D-37; Codex review SC-TE04):** an anonymous objection is never a procedural veto, but an attributed judgment that independently establishes what it pointed out (for example, that a relied-on inference step is invalid) changes the route's status (§6.1) like any judgment, whoever supplied the lead. **SCIRE's objection rule (D-38)** requires a consequential decision's basis statement to address every unresolved objection in `A(D)`, anonymous or signed, which gives no objection a veto. Neither the existence of an objection nor its arrival after a decision was evaluated is ever grounds for the memory to refuse the decision; it is recorded and travels (F-7). A critic who later signs makes it a signed objection from then on; the earlier interval stays anonymous in history. **An anonymous participant never submits a judgment** (owner decision D-64; same-family review F62-02): anonymous-role sessions submit objections, critiques, questions and claims that are not about a person, and route status changes only through attributed judgments (Definition 2.8, D-37).

**F-9 — Claims about people are never anonymous** (D-32, D-33). A claim whose subject is a person's reliability, competence, conduct or motive is a signed, attributed claim, linked to any reply by the person judged.

**F-9a — De-attribution of derived statements (owner decision D-44; re-review V4-12 (iii)).** A person may ask that derived statements stop naming them: summaries, overviews, narratives, translations and statements extracted from others' records then refer to them by role ("a participant", "an author"). What de-attribution never changes: who authored each record (attribution is a recorded fact, F-20 and TE-11), the content of a claim another human signed, and the identity relations used for independence and conflict checks. A person who wants their own contribution gone asks for deletion instead, which leaves a withdrawal marker where others relied on it (candidate 6.3 §12.3). Complete erasure and permanent true attribution cannot both be promised; this rule keeps attribution and limits repetition. **It is presentational:** anyone who may open the underlying record sees its author one step away, and the requester is told so. **Accountability renderings are exempt** (same-family review R-15): who decided, signed or resolved a decision, which curator deleted a record (the marker), which administrator read a scope in administrator mode, and which review chair blocked a message are always named, since F-1 and the dissent guarantees depend on them.

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

**F-17 — Uninstrumented observations.** If `ω(o) = uninstrumented`, `o` is carried with that label until *upgraded*: its material inputs, conditions and regime are recovered and its admissibility assessed. Re-entering the same number elsewhere is not an upgrade (re-review V4-12 (ii), restored). A finalization or outcome decision whose evidential routes, followed from its basis claims, all rest only on uninstrumented observations is **labeled** "sole uninstrumented backing" on every projection, however the routes are cited. Whether such a decision may proceed is SCIRE's finalization rule, which must not let it pass unlabeled; the memory labels and does not refuse (same-family review R-07).

**F-18 — Snapshots of external results.** A retained snapshot of an external result (for example from SSDS) is evidence of the value at the cited revision. Its qualification is "as of the snapshot; later changes unknown", and a claim relying on it states this (re-review V4-13).

### 5.4 Independence

**Definition 5.4.** An *independence claim* between two lines of evidence states the dimensions in which they are independent (data, method, instrument or code, model, analyst, model family, prompt, retrieved sources) and a coverage statement.

**F-19.** Missing provenance never establishes independence. Unknown authorship is never treated as independent (from SSDS). Copies of one source are one source. Several agents agreeing from shared inputs are one line of evidence for counting, though each argument stays inspectable.

**F-20 — Identity relations, not attributes.** Who did an analysis enters assessment **only** through identity relations: same principal or not, declared collaboration, declared conflict of interest, and, for conflict checks only, same sealed author. Using these to count independence, or to check a reviewer's conflict, is not judging a person. No attribute or aggregate of a person (§7.3) enters any assessment.

**F-20a — Nothing shown depends on a sealed identity** (Codex review TE-R13). For the analyst dimension of independence, two lines of evidence count as independent only when both are attributed to different principals, or both are anonymous under different pseudonyms in the same review. For every other pair, including an anonymous record and a signed one, or anonymous records in different reviews, analyst independence is **not established**, whatever the sealed truth. The rule is the same for every such pair, so applying it reveals nothing about who wrote what; its cost is that an anonymous critic's agreement never counts as independent of an attributed line. This is F-19 applied to authorship the reader may not know. An authenticated account is not proof of a unique human, so independence by principal or pseudonym is bounded by the identity provider's assurance.

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

**Definition 6.0 — Effective judgment** (same-family review SC-R2). A scientific judgment `J` of a target under `(σ, ρ)` is *effective* at position `p` if and only if
1. `J` is a head of its `(target, σ, ρ)` lineage at `p`; only `J`'s own assessor can supersede it, so heads by different assessors coexist (Definition 2.8);
2. `p` lies inside `J`'s validity interval, which is unbounded unless `J` states one;
3. the target revision `J` binds is current at `p` (otherwise the route is under review, F-21), and every evidence revision `J`'s basis cites is current and not retracted, corrected or deleted;
4. no review obligation is pending on the target;
5. `J`'s basis cites no flag, hub, narrative, projection, standing report, recommendation, source assessment or other judgment (D-39 defers judgment on judgment). Having been **shown** such a view is recorded as exposure and does not by itself make `J` ineffective;
6. `ρ` is a ruleset registered for the scope at `p`. `ρ` names a ruleset identity and version: a new version is a new `ρ`, unless its registration states that it continues the previous version, in which case judgments under the previous version stay effective (same-family review F62-06 b);
7. `J`'s assessor is attributed, not sealed (D-64).

No wall-clock age applies unless `ρ` states one, and activity elsewhere in the scope does not affect effectiveness. This is a definition for scientific standing only; the currentness rule for project-memory facts is the architecture's and is unchanged. A judgment that exists but is not effective is never ignored: the route shows it, with the condition that fails. Each judgment is also labeled with whether its assessor had been shown prior assessments or the standing of the same target (its recorded exposure), so a reader can see where an assessment may echo an earlier one (F62-06 c).

**Positive and negative** (same-family review S62-3). An inference assessment is positive when it finds the step valid under its conditions and negative when it finds it invalid. An evidential assessment is positive at `usable` or `usable-with-limits` (the limits are listed with the route), negative at `not-usable`, and neither at `under-review`, which puts the route under review. A claim assessment is positive at `supported` or `supported-under(c)`, negative at `refuted` or `disfavored-under(c)`, and neither at `contested` or `unknown`.

**Premises** (owner decisions D-69 and D-70; same-family review F62-03, F62-04). The premises of a step are its premise claims other than hypotheses discharged inside the same derivation (Definition 2.7). A premise is **established** for the route when it has an effective judgment with status `supported`, or `supported-under(c')` with `c'` **compatible** with the step's conditions. Compatibility is established only when `c'` and the step cite the same condition record by identity, or an effective comparability judgment (§5.7) states that `c'` covers the step's conditions; otherwise the premise shows "compatibility not established". A premise's judgment counts under the premise's home scope when that scope and the reader's scope register the same ruleset identity; otherwise the premise shows "assessed under another ruleset". The reader's scope is the claim's home scope unless the reader names another, and the report names the scope and ruleset under which each premise was judged.

| Route status | Condition |
| --- | --- |
| **unassessed** | no evidential or inference assessment of the route under the reader's `(σ, ρ)` |
| **assessed, not effective** | assessments exist, none is effective; each is listed with the condition of Definition 6.0 it fails |
| **under review** | a pending review obligation exists on the route, or the route binds an earlier revision of `κ` (F-21) |
| **challenged** | an objection targeting the route or one of its endpoints (F-6: for an evidence relation, its observation, conditioning model, condition and cited calibration, definition or model records; for an inference step, its premises and conditions) is unresolved or has a disputed resolution |
| **disputed** | effective positive and effective negative assessments of the route coexist; both are listed, and neither is chosen |
| **premises not established** | the route has an effective positive assessment and some premise is not established; each such premise is listed with its status, or "unassessed", "compatibility not established" or "assessed under another ruleset" |
| **broken** | every effective assessment of the route is negative (step invalid; observation not usable for this use); or a premise is retracted, superseded, or has an effective negative judgment that applies to the step's conditions; or the route is circular or rootless (F-25) |
| **assessed-sound** | some effective assessment of the route is positive and none is negative, every premise is established, no effective negative judgment applies to a premise, and none of the above holds |

Every route meets at least one condition. Several can hold; the report lists all of them, and the table order is used only to choose a one-word label.

**Well-foundedness** (Codex review SC-TE01, TE-R11). Route status depends on premises only through their own **effective judgments** (Definition 6.0), never through their projected standing, so it is computed in one pass with no fixed point. **Circularity is judged per derivation** (same-family review R-02): an inference step `S` with conclusion `κ` is **circular** when, for some premise `P` of `S`, every route that `P`'s effective supporting judgments cite reaches `κ` through inference steps. A premise with one cited route that avoids `κ` keeps `S` non-circular, so a third party's converse step cannot break a well-founded route. A circular route gives no positive warrant; a recursive definition (modality `defined`) or a proof by induction is not a support cycle. Negative information counts: an added adverse judgment or objection changes a route's status even when no cited revision changed. Ordinal statuses are never multiplied, averaged or voted on.

### 6.2 Standing report (normative)

**Definition 6.1.** The *standing* of `κ` for a reader at position `p` is the report

```text
standing(κ, p) = { judgments of κ per (σ, ρ), with status;
                   routes of κ, each with its status and its own standing one level down;
                   A(κ): objections targeting κ, its routes or a route endpoint (F-6), with state and mode;
                   review obligations on κ and its routes;
                   source assessments of the works κ rests on;
                   decisions that rely on κ, with dissent;
                   coverage: what the reader may not read, what is unprocessed,
                             and where traversal stopped }
```

computed over the exact revisions committed at `p` that the reader may read.

**F-28 — Status, not winners.** `standing` contains no aggregate verdict, score or ranking of alternatives. Two derived predicates are defined exactly, for front ends to use:

```text
has-sound-route(κ)      ⇔  some route of κ is assessed-sound and no O ∈ A(κ) is unresolved or disputed
has-open-challenge(κ)   ⇔  some O targeting κ, one of its routes or a route endpoint is unresolved or disputed
```

Standing never merges kinds of assessment that SCIRE v0.4 §5.4 keeps apart: qualitative plausibility, evidential bearing, inferential validity, model adequacy, quantitative probability, participant judgment and decision each stay in their own records and labels.

A position is shown as "current" only where a recorded decision makes it so (F-12).

**F-29 — Projection, not admission.** Propagating standing from premises to conclusions is computed at read time over exact revisions and is recomputed when an input changes. No stored judgment is created or changed by propagation.

**F-30 — Depth and coverage.** The report is exact to the depth it is computed. Where the traversal is bounded, the bound is part of `coverage`, and nothing beyond it is reported as sound or as absent.

### 6.3 History

**F-31.** Two reads are answerable and distinct:
- **as held then** at record position `t`: the records and standing as committed by `t`, evaluated under the rules and the projection version in force at `t` (from SSDS: historical decisions are never recomputed under newer rules; same-family review R-03);
- **as now assessed about then:** current assessments of records dated before `t`.

A later correction is never reported as what was held earlier. The memory never invents when somebody learned something. Where explicit deletion or a restore from backup removed records (candidate 6.3 §12), "as held then" is incomplete and says so, naming the interval a restore may have lost (re-review V4-20c; owner decision D-65).

### 6.4 Retraction and review obligations

**F-32 — Creation.** When a source is retracted or corrected, found inapplicable, or has a definition changed, or a claim is revised, a deterministic traversal of the provenance, evidential, inferential and meaning-link graphs within stated coverage creates a review obligation on each dependent route and claim, with an assignee.

**F-33 — Present eligibility.** While an obligation on a route is pending, the route is under review (§6.1) and cannot newly back a consequential use unless an explicit qualification is recorded. That qualification travels like an override (F-7).

**F-34 — Closure.** An obligation closes **only** through an attributed reassessment of the route's usability. Assigning, acknowledging, archiving or answering it does not close it (re-review V4-07).

**F-35 — No truth propagation.** Retraction, revision and definition change never make anything true or false. Past decisions are flagged, never undone.

### 6.5 Judgment on judgment (deferred, owner decision D-39)

A judgment whose basis cites another judgment is not effective (Definition 6.0, condition 5) and is shown as an assessment that is not effective. The proposed contract for admitting such judgments, with dependency modes and `current`-only reliance, is candidate 1.1 §6.5 (SHA-256 `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d`); it is to be revisited only if the Slice 2 demonstration shows assessors need it.

---

## 7. Source assessment

### 7.1 Meaning

**Definition 7.1.** A *source assessment* is a judgment about a **work** (or, once channel assessment is built under D-45, a non-person channel) as an evidence channel **for a kind of claim**. Its value is ordinal:

```text
established > generally-reliable > mixed > unreliable,  plus  unknown (unordered)
```

It is never a probability or a calibrated quantity. Its recorded basis is: provenance class and channel integrity; for non-person channels only, track record (Definition 7.2); retractions and corrections; declared conflicts of interest; known shared dependencies.

**Definition 7.2 — Track record** (non-person channels only; deferred with channel assessment, owner decision D-45): in Appendix C.

**F-36 — Assessment, not computation.** A source assessment is made by an attributed assessor, who states how the basis yields the ordinal value. No rule maps counts to a value automatically in this formulation. An automatic mapping, a numeric score or calibration reopens D2 (§9).

**F-37 — Limited use.** A source assessment may order retrieval and fact-checking work. It never sets a claim's standing alone and never hides a claim.

**Realization note.** Owner decision D-45 defers assessments of non-person channels and their track records to a later slice, built only if measured need justifies their proxy risk (candidate 6.3 §9.13). Their meanings are kept in Appendix C so they are not reviewed as current text; deferring them changes no meaning.

### 7.2 Guards

**F-38 — No reward for agreement.** Disagreeing with the prevailing theory is never a mark against a source; only outcomes assessed independently of the source and of the claim's own position count (Definition 7.2).

**F-39 — No person-level output** (D-32). For any person `π`, no score, rank, rating, track record, tendency, outcome count or label is computed, stored or shown. Authorship is never an input to a work's assessment, to a source assessment or to retrieval ranking. No view aggregates works by author to compare or characterize authors, and no view lists a person's works together with their assessment values; a work's assessment appears when that work is opened (same-family review R-17). A reader who opens a person's works one by one can still compile them; that residual is stated. A work never borrows standing, good or bad, from its author's other work. F-20's identity relations are the only use of authorship in assessment.

**F-40 — Humans judge people, accountably.** A judgment of a person exists only as a signed human claim (F-9), linked to the person's replies. It never feeds any assessment or ranking, is never surfaced proactively and is never repeated by an agent as its own view.

**F-41 — Proxies.** Institutions, groups and venues are persons for F-39. A channel must be a technical production or measurement mechanism with its own error behavior; a collection defined by authorship or affiliation (one researcher's papers, a lab's outputs, a venue's articles) is not a channel (Codex review TE-R12). An agent principal is a channel (a model family as a technical system), not a person; its assessment must not serve as a proxy for its human overseer.

**F-41a — Track-record coverage:** deferred with channel assessment, in Appendix C.

**F-42 — Conflicts of interest** are facts about the work they concern, never judgments of a person.

---

## 8. Assumptions, limitations and uncertainty

### 8.1 Assumptions

- **A-1:** Attribution is authentic within the deployment's trust boundary (candidate 6.3 §7). If attribution can be forged, every F-rule that names an author fails.
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
8. A narrative that drops the live alternative: the mandatory list still shows it; the omission flag is only a cue (candidate 6.3 §10.5.1, and §10.5.3 in its Slice 4 annex).
9. Retract a claim with an unresolved objection, restate it as a new claim, then finalize: the objection stays on the withdrawn target and on the question page (F-3b; S62-1).
10. A second assessor supersedes the first assessor's positive judgment to turn "disputed" into "broken": not possible; both stay heads (Definition 2.8; F62-01).
11. An anonymous participant records an invalidity judgment: refused (F-8; D-64).
12. A valid step on a premise nobody has assessed: "premises not established", never "assessed-sound" or "unassessed" (§6.1; S62-3).

---

## 11. Scientific inspectability (O1)

**Material realized record.** Events and observations with origin and qualification; claims with modality, conditions and acts; questions; evidence relations with use history; inference steps; objections with handling, resolution and mode; judgments, including comparability, source and retention-recommendation judgments; decisions with authority, exposure and dissent; review obligations; flags with cues; archive and deletion records; sealed attribution, blocks and appeals for anonymous review. **Destructive boundaries:** only explicit deletion (candidate 6.3 §12); archival is not destructive.

**Intended readers.** Researchers, PIs, reviewers and their agents; for project memory, the users, overseers, incident investigators and operators of candidate 5 §1.4.

**Routine questions.** What do we believe about X, why and how strongly? What bears against it? What changed since a given time? What was retracted, and what depends on it? Was this observation used to fit or to test? Which sources does this rest on, and how independent are they? What did we hold then? What is recommended for archive, and why?

**Product inspectability surfaces.** All are **beyond the requested deliverable** of this formulation and bind only after the owner accepts them: question pages and the understanding section; the standing report with its basis; fact-check results; the retraction impact view; the retention recommendation queue; masked review packages and the block-and-return flow; decision status (`reported`, `recorded`, `validated` awaiting signatures or complete) with its labels and late-objection delta; deletion and withdrawal markers; the participant-visible fields of anonymous-review records (same-family review R-19 m); the "target withdrawn, not re-examined" state on markers and question pages (D-63); and the restore coverage line (D-65). Candidate 6.3 §17.2 repeats this marking. Technical acceptance of this formulation does not accept them.

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

- **Concretized by:** UPMS candidate 6.3 (D3), which maps each F-rule to a record, check or projection and an acceptance test (its §15 and Appendix A).
- **Front-end dependents:** SCIRE's front-end specification (proposal §14 step 2) relies on F-3 to F-12 and must not narrow them.
- **Reopen triggers** in candidate 5 §1.4: triggers 1 and 4 are answered by this formulation; trigger 1 reopens again for any numeric score (§9). Triggers 2 and 3 are unchanged.
- **No accepted predecessor:** there are no recorded tensions against accepted D1 authority to carry, because none exists. Tensions recorded against the SCIRE v0.4 texts are carried as listed in §12.

---

## 14. Findings raised while drafting

These are the author's findings on the proposal's D1 content, recorded for the reviewer. None is a Serious Challenge to a D1 meaning; the D3-level challenges, including two Serious Challenges to the proposal's text, are in the change history of candidate 6.3 (A.12 and A.13).

| ID | Finding | Disposition here |
| --- | --- | --- |
| D1-F1 | The proposal says authorship is never an input to assessment (§6.4), and also counts independence by analyst (§5.4) and checks reviewer conflicts by identity (§7.1). Read literally, these conflict | F-20: identity relations only, never attributes or aggregates |
| D1-F2 | The proposal's decision kinds omit resolution by assessment, while SC-41's repair (carried with a back-end fix, proposal §13.2) needs resolution to carry decision fields | Definition 2.10 adds `resolution`; F-3 |
| D1-F3 | "Applies" was unbounded in SCIRE v0.4 and is a back-end invariant in the proposal (TE-04) | F-6 fixes a one-hop default from the cited basis, which a front end may widen |
| D1-F4 | Re-review V4-12 (iii), de-attribution of a person from derived statements on request, and (iv), where an argument may stop, are carried by neither the proposal nor this text | (iii): F-9a, proposed; owner decision. (iv): open (candidate 6.3 §18.2) |
| D1-F5 | The re-review's D1 note on V3-10 asks which test or threshold a statistical disagreement uses | F-22 and §9: no disagreement without a declared model and rule; method is D2 |
| D1-F6 | The Codex review (SC-TE01) shows that exact judgment references alone do not make support current: an unchanged revision can lose effectiveness, a new adverse judgment supersedes nothing, and cyclic support has no defined evaluation | §6.1 well-foundedness; §6.5 dependency modes and currentness. Judgment on judgment stays open |
| D1-F7 | The Codex review (SC-TE04) shows that an absolute reading of D-36 would let anonymity shield an independently verified invalidity | F-8 narrow reading; owner decision |
| D1-F8 | The Codex review (TE-R12) shows channel assessment can proxy for a person or lab | F-41, F-41a |
| D1-F9 | (Revision 1.1.) Candidate 1 let `content` judgment-basis entries count as epistemic dependencies while only `current` entries went stale, so a judgment could keep relying on an overturned judgment's content | §6.5: only `current` entries count |
| D1-F10 | (Revision 1.1.) Candidate 1's F-20 used same sealed author in independence counting. Between an anonymous and a signed record, any released result of that check reveals whether they share an author (the Codex review's TE-R13 trajectory), and candidate 6's count rule covered only critic counts | F-20 narrowed; F-20a |
| D1-F11 | (Revision 1.2; same-family review SC-R1.) Candidate 1.1 never said when `superseded` applies, and the architecture applied it to every revision, so a trivial edit resolved every objection | Definition 2.5 narrowed; F-3a carries objections |
| D1-F12 | (1.2; SC-R2.) "Effective" was undefined for scientific judgments; read as project-memory admission, no route was ever sound, and read otherwise, the admission rule kept by D-39 was bypassed | Definition 6.0; statuses "assessed, not effective" and "disputed" |
| D1-F13 | (1.2; R-01.) Objections to a cited route's observation, model, calibration or premises never reached the decision | F-6 endpoints; §6.1 "challenged" |
| D1-F14 | (1.2; R-02.) A converse step broke a well-founded route, and disagreement between assessors showed as "broken" | Per-derivation circularity; "disputed" |
| D1-F15 | (1.2; R-03, R-07, R-15, R-17.) History did not pin the projection version; F-17 made the memory refuse a front-end decision; de-attribution reached accountability renderings; author views could juxtapose assessments | F-31; F-17 as a label; F-9a exemptions; F-39 |
| D1-F16 | (Revision 1.3; same-family review S62-1.) Retracting or deleting a target resolved its objections as `superseded`, so restating the claim gave a clean position | `superseded` removed from resolutions; F-3b; D-63 |
| D1-F17 | (1.3; S62-3, F62-03, F62-04.) The route-status table had no status for a positive route on an unestablished premise; positive and negative, condition compatibility and cross-scope premises were undefined | "premises not established"; definitions in §6.1; D-69 |
| D1-F18 | (1.3; F62-01, F62-02, F62-05, F62-06.) Another assessor, or an anonymous session, could supersede or submit a judgment that broke a route; a step replaced through `supersedes` escaped F-3a; validity interval and ruleset version were undefined | Definition 2.8 supersession and attribution; F-3a steps and relations; Definition 6.0; D-64 |
| D1-F19 | (1.3; review §7.) A derivation with a discharged hypothesis could never be sound, because the hypothesis could never be `supported` | Definition 2.7 discharge; §6.1 premises; D-70 |

---

## 15. Open challenges

1. **Judgment on judgment** (§6.5): deferred by owner decision D-39.
2. **De-attribution on request** (D1-F4): decided (D-44, F-9a); V4-12 (iv), where an argument may stop, stays open.
3. **Whether F-6's one-hop default is enough** for SCIRE's objection rule, or a front end should widen it by default: to be tested by E1 and E5.
4. **Whether E5's faithfulness criterion can be stated operationally** before data: the owner sets error and cost limits first.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the same model family and model as the proposal, candidates 4.1 and 5, the SCIRE v0.3 and v0.4 texts and the SCIRE v0.4 re-review. Shared blind spots are likely. A reviewer outside the Claude family is required before acceptance.
- **Read directly:** the proposal in full; candidate 5 §§1–18 in full (Appendix A by heading); SCIRE v0.4 §§2–7 in full; the SCIRE v0.4 re-review §§1–9 in full; the Codex review of the proposal in full, after the first draft.
- **Anchoring:** the Codex review was read after drafting; the repairs it prompted were fitted to an existing text, and their adequacy is for the reviewer to judge. Revision 1.1 came from the same author re-reading that review against the operative text; it is a same-family check, not independent confirmation that the rest holds. Revision 1.2 answers a same-family review by a fresh Claude context; the author then wrote the repairs, so they too need an independent check. Revision 1.3 answers a second same-family review, by Claude Fable 5.1 in a fresh context; the same caveat applies.
- **Not read:** SCIRE v0.4 §§8–17 (facilitation, orientation, interfaces, invariants, experiments), except as summarized by the proposal and the re-review; SSDS sources (reached only through the proposal's §10).
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated.

---

## Appendix B. Change map, candidate 1 → candidate 1.1

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.1; candidate 1 added as predecessor input; references to the architecture now name candidate 6.2, whose section numbers are unchanged | Delivered as a new file (`AGENTS.md`) |
| F-8 | Author's recommendation added: confirm the narrow reading; SCIRE's basis statement addresses every unresolved applicable objection | Owner asked for recommendations |
| F-9a | New: de-attribution of derived statements, proposed | D1-F4, re-review V4-12 (iii); owner asked for recommendations |
| F-20, F-20a | Sealed authorship no longer enters independence; analyst independence across an anonymous and a signed record, or across reviews, is "not established" | D1-F10, Codex review TE-R13 |
| §6.5 | Only `current` entries are epistemic dependencies; author recommends deferral | D1-F9, Codex review SC-TE01 |
| §7.1 | Realization note: channel assessment deferred by candidate 6.2 | Simplicity; Codex review §7 |
| §14, §15, Appendix A | D1-F9, D1-F10 added; open items annotated; anchoring note extended | Record of this revision |

No other text changed.

---

## Appendix C. Deferred: channel assessment (owner decision D-45)

Kept so the meaning is ready when channel assessment is built; not current text.

**Definition 7.2 — Track record (non-person channels only).** For channel `ch` and claim kind `k`, the track record is the set of later judgments `J` on claims of kind `k` from `ch` such that `J`'s assessor is not among the authors of the assessed claim, and `J`'s basis consists of evidence independent of `ch` in the sense of Definition 5.4. A judgment whose basis is agreement with the prevailing position, rather than independent evidence, is excluded.

**F-41a — Track-record coverage.** A track record is reported with its denominator and coverage: the channel's claims of the kind, how many were later assessed, and how they came to be assessed. Preferential checking of disfavored sources biases an otherwise independent collection.

---

## Appendix D. Change map, candidate 1.1 → candidate 1.2

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.2; candidate 1.1, the same-family review and the owner decision record added as inputs; architecture references name candidate 6.2 | — |
| Definition 2.5, F-3a | `superseded` only for retraction or withdrawal with no successor; revision carries objections | SC-R1 |
| F-6, §6.1 "challenged" | Objections on route endpoints join `A(D)` and challenge the route | R-01 |
| F-8 | D-37 and D-38 folded in; no refusal for an objection's existence or late arrival | D-37, D-38, R-04 |
| F-9a | D-44; presentational; accountability renderings exempt | D-44, R-15 |
| F-17 | Label, not refusal; SCIRE's rule decides | R-07 |
| Definition 6.0, §6.1 table, well-foundedness | Effectiveness defined for scientific standing; "assessed, not effective" and "disputed"; per-derivation circularity | SC-R2, R-02 |
| F-28 | Open challenge includes route endpoints | R-01 |
| F-31 | Projection version pinned | R-03 |
| §6.5 | Replaced by a pointer to candidate 1.1 §6.5 | D-39, R-20 |
| §7, Appendix C | Definition 7.2 and F-41a moved to a deferred appendix; F-39 forbids listing a person's works with their assessments | D-45, R-17, R-20 |
| §10.3 case 8 | Mandatory list, not the flag | R-19 i |
| §11 | Decision status, markers and anonymous-review fields marked as surfaces beyond the deliverable | R-19 m |
| §14, §15, Appendix A | D1-F11 to D1-F15; open items updated | — |

No other text changed.

---

## Appendix E. Change map, candidate 1.2 → candidate 1.3

| Where | Change | Reason |
| --- | --- | --- |
| Title, metadata, §0.1 | Revision 1.3; candidate 1.2, the 6.2 same-family review and the D-63 to D-70 decision record added as inputs; architecture references name candidate 6.3 | — |
| Definition 2.5, F-3b | `superseded` is no longer a resolution; withdrawing or deleting a target leaves its objections unresolved and visible | S62-1, D-63 |
| Definition 2.7 | Derivations; introduced and discharged hypotheses | Review §7 (hook H3), D-70 |
| Definition 2.8 | Child kinds (`fidelity`, `inspection`) kept out of route status; validity interval; supersession only by the same assessor; no anonymous judgments | F62-01, F62-02, F62-06 a, D-64, D-70 |
| F-3a | Steps and relations replaced through `supersedes` are revisions | F62-05 |
| F-8 | Anonymous participants never submit judgments | F62-02, D-64 |
| Definition 6.0 | Same-assessor supersession; validity default; ruleset versions; condition 7; exposure label | F62-01, F62-06 a–c, D-64 |
| §6.1 | Positive and negative per kind; established premises, compatibility, cross-scope premises; new status "premises not established"; "broken" and "assessed-sound" restated; the table is total | S62-3, F62-03, F62-04, D-69, D-70 |
| Definition 6.1, F-28 | `A(κ)` includes route endpoints; misplaced sentence moved | F62-06 d, e |
| F-31 | A restore makes "as held then" incomplete and says so | F62-07, D-65 |
| §10.3 | Stress cases 9 to 12 | S62-1, S62-3, F62-01, F62-02 |
| §11 | New surfaces marked beyond the deliverable | D-63, D-65 |
| §14, Appendix A | D1-F16 to D1-F19; anchoring note | — |

No other text changed.
