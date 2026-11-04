# SCIRE: Scientific Collaborative Inquiry and Reasoning Environment

**Conceptual Scientific and Architectural Proposal**

**Version:** 0.4 — repairs the v0.3 contracts challenged by the independent review; supersedes v0.3 as a review candidate only
**Date:** 2 November 2026
**Status:** PROPOSED — unratified; pending independent re-review of the changed contracts and human decisions
**Author:** Claude (AI, Opus 5.5), at the product owner's request and under the owner's decisions below
**Related document:** `Memory_and_Domain_Interoperability_Proposal_v0.4.md`

**Inputs**

| Input | Identity | Role |
| --- | --- | --- |
| SCIRE Conceptual Proposal v0.3 | SHA-256 `02c5ece20beccb93021ce0fe156d170d3ae7dfecffbf5768aef1f4a05c211459` | Base text |
| SCIRE v0.3 Independent Concept-Level Review (Codex, OpenAI family) | SHA-256 `60dae8f585390ccb6636aa4513aa6155ac0c1b378ea4299ef4656d0078435021` | Serious Challenges SC-31–SC-33, findings V3-01–V3-13 |
| SCIRE Conceptual Proposal v0.2 | SHA-256 `3e71ebb39d57f5b9716a1a414991f0d6f7a330a5e902d20590d2c8f432d985bc` | Predecessor properties the review asked to restore |
| Product owner's decisions | This design conversation, 2 November 2026 | D-A to D-J below |

**Owner decisions bound by this revision**

Decided in conversation, quoted in the v0.3 header and repeated here in summary:

- **D-A — Separation by responsibility.** UPMS holds an agent's or team's general contextual record and logistics; SCIRE holds scientific argument and discussion.
- **D-B — SCIRE is the proposal layer.** SSDS owns the decided model and implementations; SCIRE's output is SSDS's input.
- **D-C — The PI decides what SSDS builds.** SCIRE gives the finalized scientific model backed by arguments, never execution. SSDS executes only the implementation a user requested.
- **D-D — Independent systems; links for traceability.** SCIRE, SSDS and their projects are independent systems with their own governing authorities. Citation-like links and automated transfer of models and feedback serve traceability and developmental data flow, not operation.

Approved by the owner on 2 November 2026 as the framing for this draft ("Yes, draft v0.4", in answer to whether to draft v0.4 using the recommended answers to the review's open decisions):

- **D-E — Availability versus eligibility.** Every system stays available when a link is unresolved. A particular consequential use that needs the missing backing may be refused or qualified.
- **D-F — Scope of scientific outputs.** Finalization is the step that hands a model to SSDS. Other results (null, descriptive, contested findings) can be published without it.
- **D-G — Several PIs.** Each PI's decisions are limited to their own scope, with joint sign-off where the project requires it, and never "last one wins".
- **D-H — Overrides.** A named person may decide to proceed despite an unresolved objection for a stated purpose, with the reason and consequences recorded and the dissent visible. An override never counts as resolving the objection.
- **D-I — Retention, metadata and revocation.** These belong to the source owners. Nothing is retained by default merely because the writer had access.
- **D-J — First product.** Start with the smallest useful demonstration: one real inquiry, compared against a versioned notebook plus search. The owner sets error and cost limits before each experiment.

**Independence.** This revision was written by the same model family as the v0.2 review, and by the same author as v0.3. Its acceptance still needs an independent review of the changed contracts.

**Review boundary.** This document proposes scientific meanings (D1) and architectural responsibilities (D3) for SCIRE. Its scenarios are not validation evidence. No scientific result, implementation or authority promotion is claimed.

---

## 0. Summary

Research groups lose scientific understanding in predictable ways. A hypothetical becomes a fact by retelling. An objection nobody answered stops being mentioned and is then taken as resolved. The evidence behind a claim, and whether its sources are independent, becomes unclear. The reasons a path was abandoned are forgotten. A capable language model with search and a chat archive may make the first two failures worse, since it writes fluent syntheses that resolve tension; experiment E1 (§15) tests that hypothesis.

SCIRE is a persistent environment in which human researchers and AI agents discuss science, and in which the **status** of every scientific statement, the **force** of every unresolved objection, the **basis** of every claim and the **history** of every question stay explicit and attributable.

SCIRE is the **proposal layer** of scientific work. It holds discussion, questions, competing hypotheses, objections, evidence assessments and the decisions a team takes. Its outcomes are **scoped scientific outcomes**: a null result, an exclusion, a characterization, an unresolved contradiction, a supported claim, or a **finalized model**. The finalized model is the specific outcome the PI hands to SSDS to be built. SCIRE never executes anything. SSDS implements and executes only what a user requests, under its own governance, and its results and findings can flow back to SCIRE as evidence. General context and logistics belong to UPMS.

The primary unit for organizing work is the **open question**, not the argument. A question gathers its live alternatives, the observations that bear on them, the objections raised and the decisions taken. Arguments are optional structure, added when needed. But **before anything is relied on for a consequential use**, its material basis is stated, even as a short paragraph (§4.5).

SCIRE, SSDS and their projects are independent systems. They cite each other through citation-like links. An unresolved link never stops a system; it can only limit a particular use that needs the missing backing.

---

## 1. Problem Statement

### 1.1 Four decay processes

| Decay | What happens | What SCIRE preserves |
| --- | --- | --- |
| Status inflation | "Suppose strain drives it" is retold as "strain drives it (Dr. X)" | The modality of every statement and who confirmed or adopted it |
| Dissent loss | An unanswered objection disappears from summaries | An objection's unresolved force travels with every decision that relies on its target |
| Basis loss | It becomes unclear which observations bear on a claim, under which conditions, and whether they are independent | Conditional, attributed evidence links with use history, origin and qualification |
| Rationale loss | Rejected paths are re-explored or cited as current | Append-only history of questions, statuses and decisions, with what each decision-maker saw |

### 1.2 Why a scientific conclusion needs its structure

A conclusion means something only together with its assumptions, evidence and inferences. "This interaction suppresses ferroelectricity" is not a demonstration of a mechanism. The demonstration may run through a predicted change in orbital energies, a change in orbital mixing, a change in the energy of a structural distortion, a balance of competing energy terms, and a stated physical regime. Each step has its own assumptions and uncertainty. A missing step is often the next research question rather than a defect.

### 1.3 Why scientific history matters

Understanding changes. A group may believe A implies B; find that condition C is needed; find an intermediate mechanism D; replace C by C′, giving D′ and B′. D′ may then explain other phenomena. A final record holding only A, C′, D′, B′ hides how D′ emerged and why the earlier path failed.

### 1.4 Why collaboration complicates this

A meeting holds people and agents with different expertise and assertiveness. Agents can share models, training data, prompts and retrieved sources, so their agreement may be one opinion repeated. A useful system protects minority positions and attribution, and it does not count agreement as corroboration.

---

## 2. Responsibility, Scope and Non-Goals

### 2.1 Responsibility (D-A, D-B, D-C)

| System | Responsibility | Not its responsibility |
| --- | --- | --- |
| **SCIRE** | Scientific discussion and argument: discussion and source records, questions, hypotheses, objections, evidence assessments, decisions, discovery history; scoped scientific outcomes, including finalized models for hand-off | Execution of any kind; software; general context and logistics |
| **SSDS** | The models it is asked to build, as adopted under its own D1–D4 governance; numerical methods, architecture and implementations; execution a user requests; realized results; PEM | Open scientific discussion; competing hypotheses; deciding what science to build |
| **UPMS** | General contextual record and logistics for an agent or a team | Scientific argument and discussion history |

The split is by **responsibility for the content**, not by the number of users and not by private versus shared. It is also not a claim about where every word was first recorded: a mixed-purpose conversation held in UPMS may contain scientific statements. Its custody stays with UPMS; SCIRE owns the scientific interpretation of it once someone brings it into SCIRE (§10.3).

### 2.2 Decisions and outcomes

SCIRE records five kinds of decision, all attributed to people:

| Decision | Meaning | Who |
| --- | --- | --- |
| **Inquiry decision** | What to investigate next; which hypothesis to work under for now; which question to close as unproductive | Per project rules |
| **Outcome decision** | That a scoped result stands for a stated purpose: a null result, an exclusion of a model family, a characterization, a supported claim, an unresolved contradiction to be reported | Per project rules; the PI for publication |
| **Model finalization** | That a model is finished for hand-off to SSDS | The PI within their scope (§2.3) |
| **Override** | To proceed despite a named unresolved objection, for a stated purpose (§4.4) | A named person with authority for that scope |
| **External decision** | A decision taken outside SCIRE (an SSDS adoption, an email agreement), recorded by reference with attribution | Recorder; the original decider is named |

Publication is an outcome decision about the exact statements to be published. Not every result needs to be a model, and no result has to be renamed a model in order to be published (D-F).

**Finalization** is scoped. A finalization names:

- the exact versions of the included statements (equations, assumptions, definitions, observables);
- its intended use and validity regime;
- its basis statement (§4.5): the evidence and arguments relied on, known gaps and limitations;
- the unresolved objections and overrides that apply (§4.4), and pending review obligations on its backing (§6.6);
- the decider and the authority rule under which they acted.

Finalizing component A does not finalize component B. Alternatives can remain live outside the scoped commitment. A finalization can be superseded or reopened by a later decision; the earlier one stays in history as decided.

SCIRE's output to SSDS is a finalized model. **The PI decides which finalized models go to SSDS to be built.** A transfer gives SSDS the model package; it never asks SSDS to build or run anything. SSDS implements only on a user's request and may adopt a narrower model through its own governance. That adoption is recorded as related to the exact package version, never as a relabeling of SCIRE's finalization. The PI's scientific choice, SSDS's adoption, the implementation request and the execution outcome are four different facts.

A calculation that SCIRE identifies as discriminating is a recorded need. Someone with the authority to do so requests it in SSDS or carries it out elsewhere, and the result returns as an observation with its origin and qualification (§6.4).

### 2.3 Several PIs (D-G)

A project may have several PIs. Each PI's decision authority is limited to a declared scope (a sub-question, a component, a method). Where the project requires it, a decision needs joint sign-off, and it is not effective until every required signer has signed. Conflicting decisions within overlapping scopes are not resolved by arrival order: both are recorded, the conflict is shown, and it stays open until the people with authority resolve it. Authority comes from the project's declared rules, never from account permissions alone.

### 2.4 Intended uses

- Scientific meetings among people and agents, and brainstorming.
- Building and criticizing arguments; finding hidden assumptions and missing steps.
- Investigating tension between theory, simulation and experiment.
- Comparing competing explanations and choosing discriminating calculations or experiments.
- Long-running projects across many discussions, and reconstruction of why things were believed.
- Literature navigation, tutoring and derivation.
- Finalizing models for building in SSDS; preparing reports and publications, including null and contested results.

### 2.5 Non-goals

SCIRE does not replace human scientific judgment, decide truth by vote, treat explicit AI reasoning as proof, require formalization of conversation, replace laboratory or simulation systems, hold models adopted for software or the software itself, serve as anyone's general memory, impose its vocabulary on other projects, or require a particular model provider, database or interface framework.

### 2.6 Standalone operation and dependent use (D-D, D-E)

SCIRE and its projects are independent systems with their own governing authorities. SCIRE works without UPMS and without SSDS. Without SSDS, calculations that need governed execution stay recorded as needed. Without UPMS, a researcher opens SCIRE directly.

Links to SSDS or UPMS records are **citation-like**: they identify a record and its revision for traceability. Two things are kept apart:

- **System availability.** An unresolved link never stops SCIRE, never stops unrelated work, and never changes a record's historical status. A proposition does not become false, and a past finalization is not undone, because a cited source is unreachable.
- **Eligibility of a particular use.** A new consequential use (a decision, a finalization, a publication, a broader claim) that needs the missing backing may be refused or qualified until the backing is available. Independently sufficient local evidence, or an authorized snapshot retained in SCIRE, can satisfy it instead. A snapshot is evidence of what the source said at its revision, not an authority over the source.

---

## 3. Principles

**P1 — Record, interpretation and decision are different things.** What someone said or observed, what someone takes it to mean, and what an authorized person decided are distinct, attributed and dated.

**P2 — Status changes only by an attributed act.** A statement is hypothesized, asserted, adopted, challenged or withdrawn because someone did that, not because it was repeated, summarized or persisted.

**P3 — Handling an objection is not resolving it.** Acknowledging or deferring an objection, or linking an answer to it, does not remove its force. Only an attributed resolution or an explicit override changes what may rely on its target, and an override never counts as resolution.

**P4 — Evidence is conditional.** An observation bears on a statement under a model and conditions. Where alternatives exist it may favor one over another; it may also show that a model is adequate or inadequate for a purpose, or that a prediction failed.

**P5 — How data were used matters.** Data used to generate, fit or select a hypothesis are not automatically independent confirmation of it. What they do justify depends on the inference design.

**P6 — Agreement is not corroboration.** Independence is itself a claim, with stated dimensions and limits.

**P7 — Competing explanations may coexist.** Alternatives may be exclusive, compatible, jointly causal or valid in different regimes. Uncertainty does not justify choosing one.

**P8 — Formal structure is not strength.** Length, connectivity, citation count and consensus are not proof. A short observation can defeat an elaborate argument. A warrant is valid or invalid regardless of whether a person or a machine produced it.

**P9 — Inquiry need not converge.** Opening better questions is progress. A null result, an exclusion or an unresolved contradiction can be a complete outcome.

**P10 — Rigor follows consequence.** Structure is added on demand, but anything relied on for a consequential use first has its material basis stated.

---

## 4. The Scientific Record

### 4.1 Planes

| Plane | Contents | What it establishes | What it does not establish |
| --- | --- | --- | --- |
| **Source record** | Attributed messages, transcript spans, attached artifacts, local observation records and references to external observations; append-only | That something was said, attached or observed, by whom, when | That it is true, well-formed or what the speaker meant |
| **Scientific record** | Questions, statements, objections, evidence links, decisions, discovery links; each attributed and source-linked | What someone proposed, assessed or decided, and its status | Empirical truth; models adopted by SSDS |
| **Derived views** | Compass, portfolios, timelines, search results, syntheses | Navigation | No scientific claim; a view is never an evidential root or an authority |

A correction to an interpretation is a new attributed record in the scientific plane; it never edits the source record.

A derived view is not evidence for any scientific statement. But the **exact view a decision-maker saw** can be evidence about the decision process: it may have omitted a caveat or shown an outdated version. When a decision is consequential, SCIRE keeps an identity for that exposure: a permitted snapshot, or the inputs and query that reproduce it (§7.1). This does not make the view canonical.

### 4.2 Record kinds

Six kinds make up the scientific record. Observations live in the source record, so they exist before anyone has assessed them.

| Kind | Meaning | Key fields |
| --- | --- | --- |
| **Question** | An open scientific problem: the unit of inquiry | Statement of the problem, scope, kind (ordinary or discrepancy), live positions, status, outcomes, what arose from it |
| **Statement** | A proposition with a modality: hypothesis, assertion, definition, assumption, prediction, explanation, finding | Text and equations, **modality**, conditions, regime and (where relevant) time scope, attribution, confirmation or adoption state, source links |
| **Objection** | A challenge to a specific statement, inference step, evidence link or applicability condition | Target, ground, attribution, **handling status**, **resolution** (§4.4) |
| **Evidence link** | How an observation bears on one or more statements | Observation reference, relation (§6.1), conditioning model and conditions, **use history** (§6.2), assessor |
| **Decision** | One of the five kinds in §2.2 | Decider and authority basis, scope and purpose, effective interval, basis statement, applicable unresolved objections and overrides, dissent, decision exposure |
| **Discovery link** | Why a later question or statement was pursued | From (question, observation, failed investigation), to, attribution |

An **observation** is a source record: a local record (a value with its conditions, instrument or code, and origin) or a reference to an external one (a laboratory system, SSDS, a publication), with its revision and observation time. It can be found and listed as **unassessed** before any evidence link exists. Its origin and qualification are recorded with it (§6.4).

An **investigation** is a decision to investigate plus its outcome: completed, failed, canceled, null, or unknown (requested but outcome not known). Where a reported result was selected from several attempts, the attempts are identifiable so that failures and selection can be seen (§6.2).

Hypothesis portfolios are views of a question's live positions. "Discovery candidate" is a status on a statement. Revisions are versions of records.

### 4.3 Modality, confirmation and adoption

Every statement carries a modality: hypothesized, asserted, assumed (for an inquiry), defined, predicted, quoted, reported (from literature or another party), or found (an outcome). Modality survives every copy, summary and export.

Three acts are kept distinct:

- **Interpretation.** A statement extracted by an AI from a source is attributed to that AI as an interpretation of the source span. The secretary distinguishes quotation, paraphrase, inferred missing premise, proposed formalization and independently substantiated statement. A quotation is evidence of the recorded words, subject to transcription fidelity; it is not evidence of intent or of truth.
- **Confirmation of intent.** Only the speaker can confirm "this is what I meant". An AI is never the confirming party for a human's attribution. An unconfirmed interpretation is never shown as the speaker's.
- **Adoption.** Any participant may adopt a reconstructed statement **under their own attribution**, citing their own check or evidence. The adopted statement is a new record linked to the interpretation it came from. The original stays "AI interpretation, speaker not confirmed". Adoption makes the statement usable as a decision basis without claiming that the original speaker endorsed it. This covers departed participants and literature authors.

An unconfirmed, unadopted interpretation never supports a decision. Re-attribution or adoption never clears confidentiality restrictions inherited from the source (§9.2).

### 4.4 Objections: handling, resolution and override

An objection has a **handling status**: open, acknowledged, deferred, answered (an answer is linked). Handling statuses describe workflow. **None of them resolves the objection.**

An objection's **resolution** is one of:

- **resolved by assessment:** an attributed assessment, by someone with authority for the scope, determines that the answer meets the objection's ground. The objector may dispute it; the dispute is kept as a further objection or as dissent;
- **withdrawn** by the objector;
- **superseded:** its target was withdrawn or replaced.

An objection without one of these resolutions is **unresolved**, whatever its handling status.

**Override (D-H).** A named person with authority for the scope may decide to proceed despite an unresolved objection, for a stated purpose. The override records the objection, the reason, the consequences accepted, the limits of the use, and the dissent. It never resolves the objection and never makes its target supported. It applies only to the stated use; other uses of the same target need their own decisions.

**Objection rule.** A statement cannot become the basis of a decision, part of a finalization, or part of a published outcome while a material unresolved objection applies to it, unless an override covers that use. An objection **applies** to a statement when it targets the statement itself or a material dependency within stated coverage: a premise, an inference step, an applicability condition, or an evidence link the statement relies on. A question cannot be closed while a material unresolved objection to one of its outcomes remains, except by an override or by closing the question as unresolved.

Every unresolved objection that applies, and every override, travels with the decision and appears on every view of that decision and in any model package (§10.1). An objector does not hold a veto, because resolution by assessment and override exist; but neither an acknowledgement nor a deferral can make an objection disappear.

### 4.5 Basis before consequential use

Formalization is demand-driven (§8.7), but a trigger only creates records. Before a statement is relied on for a **consequential use** (a decision, a finalization, a published outcome, a transfer), its **basis statement** must exist. The basis statement says, for that use:

- the material definitions and assumptions, including the hypotheses of any imported result and whether they hold in the stated regime;
- the inference and evidence relied on;
- the live alternatives;
- the known gaps.

A plain paragraph or annotated equation is enough. It need not be an argument graph or a recursive proof. A deliberately exploratory decision may proceed with an explicit gap and a correspondingly limited claim. A PI's finalization does not substitute for a missing basis statement.

When a basis needs precision, its justification can be expanded into steps:

`{premises; assumptions or validity conditions} --[inference step]--> conclusion`

Each step can name its inference type: deductive or mathematical, numerical or computational, statistical, causal or mechanistic, abductive, analogical, heuristic. A challenge targets one step. When it succeeds, it puts dependent conclusions under review; it does not falsify them, and independent routes of support survive. Circular support is not independent support.

### 4.6 Identity of records and identity of meaning

**Records** have stable identity: who said or recorded what, and when.

**Meanings** sometimes do. An exactly defined, versioned mathematical object or definition has determinate identity. Natural-language scientific terms often do not: "Tc" may mean resistivity onset, resistivity midpoint or Meissner onset; "the gap" may mean a spectroscopic gap or an order parameter. Where identity is not determinate, sameness of meaning is a **claim**: an attributed, dated, contestable link of kind *identical*, *equivalent under stated conditions*, *refines* or *related*. The default for two similar statements is *unresolved possible match*. Embedding or language-model similarity can suggest a link but never creates one.

Dependency questions run over records plus asserted links, and their answers state that coverage. A change of meaning creates review obligations, never automatic truth changes.

---

## 5. Inquiry

### 5.1 Questions organize the work

A question records the problem, where it came from, its live positions, the evidence bearing on them, objections, investigations, decisions, outcomes, and the questions it led to. A question may be opened from anywhere: a gap in an argument, an unexpected observation, a parameter sweep, a failed program. Questions organize records; they do not own every observation or meaning. An observation can exist before anyone has a question about it (§4.2).

### 5.2 Discovery history is not justification

A discovery link says why something was pursued. It is never traversed as support. A result found while investigating one question opens its own question, linked by "arose from".

### 5.3 Discrepancy questions

A discrepancy question investigates a tension between statements, observations or predictions. Its distinguishing content is a **comparability assessment**, made **relative to a target claim**:

- the target claim, and the population, regime and quantity it is about;
- the quantities compared, their operational definitions (the estimand), units and conventions;
- what the target claim predicts about how the quantity changes, or stays the same, between the compared conditions;
- uncertainty, the statistical model used to compare, and known shared dependencies between the two sides.

A comparability assessment is attributed and challengeable like any other. Completing it does not settle the scientific question.

**Kinds of tension** to distinguish:

- **Logical contradiction:** two statements cannot both hold under the same premises. Reserved for logical incompatibility.
- **Statistical disagreement:** observations of the same estimand differ by more than a stated model makes plausible. Always relative to that model and its selection assumptions; never called a logical contradiction.
- **Failed prediction:** an observation differs from what a claim predicts in the conditions it covers. A **difference in regime can be exactly the test**: if a claim says a quantity is constant from 10 K to 300 K, measurements that differ between 10 K and 300 K disfavor the claim, and "different regimes" is not a reconciliation.
- **Different estimands or regimes not covered by the claim:** the compared quantities answer different questions. The result is "not comparable for this target", and the target claim and its scope are recorded so that a narrower framing cannot hide a mismatch: two subgroups with predictions (0, 2) and observations (2, 0) agree on the aggregate mean but disagree on subgroup behavior.
- **Unexpected observation:** against expectation, not against a statement.
- **Data error**, including **units or definition errors**: when a correction removes the mismatch, the discrepancy question closes as "resolved: units or definition error". The correction stays in history, and calculations that used the wrong value get review obligations.
- **Incommensurable models:** the frameworks do not define the compared quantity the same way.

**Lifecycle.**

- **Remain open** while no available observation discriminates the live explanations. Closing as unresolved, or proceeding anyway, is a decision recorded with its dissent.
- **Split** when the comparability assessment shows more than one independent tension.
- **Link** two questions that share a root-cause hypothesis or a discriminating test. Never merge them destructively.
- **Spawn** a new question when resolution needs something not about the original pair.

**Reconciliations that must not be automatic.** A weighted mean with an inflated error presupposes a shared estimand. Stratifying by a third variable can remove a reversal, but if that variable is affected by both cause and outcome it creates bias, so "different regimes" is a causal hypothesis needing its own justification. A parameter introduced to make theory agree with the same data is not independent confirmation (P5).

### 5.4 Positions and plausibility

A question's live positions are its hypothesis portfolio. Shared statements and observations are referenced, not copied. SCIRE distinguishes qualitative plausibility, evidential bearing, inferential validity, model adequacy, quantitative probability, participant judgment and decision. Quantitative probabilities are used only when a defensible hypothesis space, priors and likelihoods exist. Overlapping or jointly causal explanations are not given a distribution as if exclusive.

### 5.5 Discriminating investigations

SCIRE helps propose calculations or experiments whose outcomes would differ across live positions, weighing informativeness, cost, feasibility and risk. No method is mandated.

### 5.6 Novelty

New to the group is different from new to the literature. A discovery candidate may prompt a literature review, independent checking and significance assessment.

---

## 6. Evidence

### 6.1 Evidential relations

An evidence link connects an observation (a measured value, computed output, literature result, proof) to one or more statements, under a stated conditioning model and conditions. Its relation is one of:

- **entails or refutes** (deductive, under stated hypotheses);
- **favors A over B** (comparative, under model M);
- **adequate or inadequate for a purpose** (absolute assessment of a model or claim against the observation, under stated criteria);
- **prediction failed or succeeded** (for an explicit prediction);
- **consistent with** (no discrimination among the live positions);
- **bears on, unassessed**.

A can be favored over B while both are inadequate; comparative and absolute assessments are recorded separately. A link names its assessor and is itself challengeable. Several assessors' conflicting assessments coexist. Reassessment never rewrites the observation.

### 6.2 Use history

Each link records how the observation has been used relative to its target statement, as a chronological, non-exclusive history:

- the dataset, subset and analysis revision involved;
- uses such as suggested the hypothesis, fitted or estimated parameters, selected among variants, tested a pre-specified prediction, checked the model;
- selection and reuse: search breadth, other variants tried, known leakage, and intervals where the history is unknown.

Data may fit one quantity and test a distinct pre-specified restriction. Nominally held-out data can share leakage, a defective instrument or an inapplicable population. What the link justifies is decided by the **inference-specific warrant**: an analysis that accounts for selection can draw valid conclusions from selected data under its assumptions, and a proof is justified by its hypotheses and checking basis, with empirical-use roles marked not applicable.

**Independent confirmation** is a narrower label with an explicit definition: the observation was not used to suggest, fit or select the statement, and no shared leakage, instrument or population dependence is known within the stated coverage. Other uses can still carry evidential value; they are not called independent confirmation.

### 6.3 Independence

Two lines of evidence are independent only in stated respects: data, method, instrument or code, model, analyst, model family, prompt and retrieved sources. Independence is a claim with those dimensions and a coverage statement. A missing provenance link does not establish independence. Several agents agreeing from shared inputs are not several independent confirmations; their separately derived arguments remain individually inspectable, but their agreement is not counted.

### 6.4 Origin, qualification and usability

Three properties of an observation are recorded separately:

| Property | Values | Meaning |
| --- | --- | --- |
| **Origin** | SSDS run; project-recorded (notebook calculation, lab measurement with recorded inputs); external-reported (literature, collaborator); uninstrumented (a number entered without recorded inputs) | Where it came from |
| **Qualification** | Qualified for a stated scope (by SSDS or another qualifying authority); unqualified; provisional; failed; unknown | What a qualifying authority has said about it. An SSDS run can be unqualified, failed or provisional; origin never implies qualification |
| **Usability** | Usable; usable with stated limits; under review (§6.6); not usable for this purpose | What SCIRE's assessors have concluded for a given use |

Project-recorded evidence is not automatically more reliable than external-reported evidence. **Upgrading** an uninstrumented observation requires recovering its material inputs, conditions and regime and assessing its admissibility; re-entering the same number in a notebook is not an upgrade.

A numerically correct computation may solve an inadequate model, and a model may match data for compensating reasons. SCIRE keeps internal consistency, numerical correctness, model adequacy, empirical support and explanatory usefulness distinct.

### 6.5 Flags and warrants

A screening step (deterministic where units, regimes or exclusive statuses are typed; semantic otherwise) may flag a candidate tension. A flag may open a question. It is never cited as evidence.

An assessment identifies the sources and warrant it rests on. **Support that is circular, or that has no applicable root in source records, is not a warrant**, whoever produced it. Shared roots are not new independent evidence. A machine proof checker can provide a valid check under named assumptions, and another component can faithfully report it; a human's insertion does not validate a circular warrant. A project may still require human confirmation for a consequential class of status change; that is an authority policy, not a claim about epistemic validity.

### 6.6 Retraction, review obligations and present eligibility

When a source is retracted, corrected, found inapplicable, or has a definition changed, SCIRE creates **review obligations** on dependent links and statements, reached through evidence links and asserted meaning links within stated coverage. A review obligation has an assignee and appears in the compass until disposed of.

Two states are kept apart:

- **Historical status:** an earlier assessment remains a record of what was assessed, as made. It is not thereby shown to have been valid even then.
- **Present eligibility:** while a review obligation on an evidence link is pending, that link is **under review** and cannot newly support a decision, finalization or published outcome without an override (§4.4) or a qualified claim. Past decisions are not undone; they are flagged for review.

### 6.7 Contrary and null results

Contrary observations, failed investigations and null results are kept as evidence links, question outcomes and, where decided, published outcomes.

---

## 7. History and Time

### 7.1 Times and what each answers

| Time | Recorded for | Answers |
| --- | --- | --- |
| **Record time** | Every record (append-only) | What SCIRE held at time *t* |
| **Occurrence or communication time** | Discussion and external decisions, where known (a June entry recording a May meeting) | When something was said or decided |
| **Observation time** | Observations | When something was measured or computed |
| **Effective interval** | Decisions | When a decision was in force |
| **Time scope** | Statements about time-dependent phenomena (transient effects, ageing samples, changing populations) | When a statement claims to hold |

"**As SCIRE held then**" is the history read at record time *t*. It is not necessarily what the team knew then, which SCIRE can only qualify (late entries, external decisions recorded afterwards); SCIRE never invents when somebody learned something. "**As now assessed about then**" is current assessments of records dated before *t*. A later correction is never reported as what was held earlier.

**Decision exposure.** For a consequential decision, SCIRE keeps the identity of what the decider saw: the record versions and view shown, as a permitted snapshot or a reproducible query (§4.1).

### 7.2 Reconstruction queries

SCIRE should answer, with drill-down: what did we believe about this mechanism before the last calculation; which observation first challenged the earlier explanation; why was hypothesis H rejected, and by whom; which assumptions changed between two versions; what evidence now bears on the revised result, and how independent it is; which discovery came from investigating a missing step; which objections were unresolved or overridden when a decision was taken, and what the decider was shown.

### 7.3 Deletion and restriction (D-I)

Deletion and restriction follow the source owner's policy and applicable law. When content is removed:

- SCIRE may keep a **tombstone** (that a source existed and was removed, when, under which policy) only where the policy permits, and only in a scope authorized to see it. Neither the existence of a removed source nor its contributor's role is shown to readers who were not permitted to know it.
- Interpretations derived from removed content are marked "source withdrawn" for readers permitted to see that marker. They survive only if re-substantiated from other sources or adopted under another attribution (§4.3), and only if retaining them is permitted.
- Re-attribution or adoption never removes restrictions inherited from the removed source.

---

## 8. Deliberation and the Meeting Room

### 8.1 Participants

A participant is a person or an AI agent. Identity, expertise, role in a meeting, permissions and decision authority are separate properties.

### 8.2 Facilitation

The facilitator seeks coverage of material questions and minority positions rather than equal speaking time. It prioritizes material weaknesses and genuine uncertainty, avoids interrupting every statement, and offers deeper scrutiny on request.

### 8.3 Decision authority

Who may take which decisions, resolve objections by assessment, and override is set per project (§2.3). The minimum rules are fixed: the PI finalizes models within their scope and decides which go to SSDS; only the speaker confirms their own meaning; a decision names its decider, authority basis and purpose; unresolved objections, overrides and dissent stay on the decision. An AI participant may propose a decision or a resolution, never make one. SCIRE records declared conflicts of interest; it does not score trust, reputation or intent.

### 8.4 Independent critique

For consequential questions, a reviewer may be given primary records without another participant's synthesis, with the allowed information recorded. Opposing analyses are synthesized as a **crux map**: the premises or observations where they diverge, and what would discriminate. Disputes are not resolved by vote or by deleting a rebuttal.

### 8.5 Concurrent contributions

Concurrent edits are not resolved by arrival order. Independent edits merge; conflicting revisions of meaning are kept as alternatives; scientific disagreement is represented as positions and objections.

### 8.6 Secretary, literature navigator and tutor

The secretary turns discussion into attributed scientific records under §4.3. The literature navigator treats literature as reported evidence subject to verification and applicability. The tutor's explanations are labeled pedagogy, not project statements.

### 8.7 Demand-driven formalization

By default a discussion is kept as an attributed source record with an AI index. Scientific records are created when:

1. someone raises an objection;
2. someone takes, or is about to rely on, a decision;
3. content is about to be sent out: as a finalized model, to SSDS, to a wider audience, to publication;
4. someone asks for a statement, question or argument to be recorded.

Triggers 2 and 3 fire **before** the consequential reliance, not after it. An informal decision that people have started acting on is captured and checked at that point. At a consequential trigger, the basis statement (§4.5) is required and a **bounded source review** is done: the relevant source records are checked for qualifiers, caveats and objections the secretary did not extract. If that review is not done, the decision records that relevant objections may remain unextracted.

The secretary may suggest records at any time; suggestions stay suggestions until a trigger or a participant accepts them. Keeping the source record and index has a cost (storage, indexing, permissions); demand-driven formalization avoids the further cost of structuring what nobody relies on.

---

## 9. Orientation and Confidentiality

### 9.1 The compass

The compass is a derived view built at read time from the scientific record by deterministic queries: open questions; live positions per question; unresolved objections (whatever their handling status), ranked by declared consequence; recent decisions with their applicable unresolved objections and overrides; untested assumptions; evidence under review; recorded calculation needs; unresolved links.

Its fields are exact **over captured records only**. Every compass shows its **capture coverage**: which source intervals have been reviewed for extraction, and which have not. An objection that was spoken but never extracted cannot appear; the compass says so rather than implying completeness. Where several incompatible positions are live, it shows all of them.

A narrative synthesis may accompany it on request: labeled as synthesis, generated for the reader's audience (§9.2), and not cited as evidence. Persisted or incrementally maintained narrative overviews are not part of the first product. They are introduced only if experiment E2 (§15) shows that they help.

"Not found" means not found in the searched and captured scope. A view that cannot show an item says so in a way that does not itself disclose protected information (§9.2).

### 9.2 Read, retain and disclose (D-I)

Three permissions are distinct predicates, checked separately:

- **Read or use** a source, possibly for a limited purpose.
- **Retain** content derived from it in a given scope or system.
- **Disclose** content derived from it to a given recipient.

Reading a document grants neither of the other two. A paraphrase, summary, extracted statement, reviewer's verdict or "new insight" derived from a source is still derived from it. A supervisor's approval of a task does not replace the source owner's release authority.

**Rules.**

1. **Retention is checked before storing.** Before SCIRE stores new content, retention in the target scope must be permitted for every restricted source in its release set (rule 3). Content of unknown lineage is stored only where retention is permitted for unknown-lineage content: an authorized quarantine scope, if the project's policy defines one. Writer access alone never authorizes retention.
2. **Restrictions are conjunctive.** Content derived from several sources must satisfy every source's restrictions. One owner's approval never releases another owner's material. A clearance is bound to the exact output, audience, purpose and scope it covers. Standing grants for precisely scoped classes are possible where the owners authorize them.
3. **Release-set lineage.** SCIRE records which restricted records it releases into each production context it runs (a meeting session, an agent working context it hosts). Everything produced in that context inherits their restrictions until an **authorized reset**: a reset defined by the project's policy that verifiably starts a context without those records or anything derived from them. A child context, a retained summary or a continuation inherits the parent's release set. This is a conservative bound: an output is treated as possibly derived from everything in its context.
4. **Audience-scoped generation.** Content meant for an audience is generated, where possible, in a context built only from sources that audience may see. This reduces exposure; it does not replace rules 1 and 2, because a purpose limitation may forbid retaining or disclosing even content the audience may read.
5. **Metadata is protected.** The existence of a restricted source, its title, its contributors' roles and its lineage are themselves restricted unless the source's policy says otherwise. A view shown to a reader without access describes its authorization scope in general terms ("this view covers only records you may see") and never reveals whether a particular hidden item exists. Where a safe and adequate view cannot be produced, the view or the decision that depends on it is limited instead.
6. **Unknown means not cleared.** Where restrictions cannot be established, the output is withheld or sent for review. The product distinguishes **forbidden** (a restriction prohibits it) from **awaiting clearance** (permission unknown or review pending).
7. **Owner review across project boundaries.** Disclosure beyond the project requires review by the owners of the restricted sources in the release set.

**Trust boundary.** SCIRE's guarantees hold for releases SCIRE itself mediates: content it releases into contexts it runs, and outputs those contexts write back through SCIRE. Content a participant or an external agent brings from outside SCIRE's mediation is a **declared gap**: SCIRE treats it as unknown lineage (rule 6) and the participant remains responsible for it, as in ordinary scientific confidentiality.

**Revocation.** Readers who already saw content are not "unseen". A revocation governs every later read, export and serving of derived content: serving a stored derivative to a new reader after revocation is a new disclosure. Disclosures are made under grants with an expiry or a revalidation rule, so that a disconnected consumer knows when it must recheck; where it cannot recheck, it withholds. Content already published under a valid clearance stays published unless the owner's policy says otherwise.

**Cross-project connections.** A connection between projects is shown only where the full transfer is permitted. A request to another project's owner must itself not reveal protected information from the requesting project.

### 9.3 Other trust boundaries

SCIRE enforces project-level visibility and separate read, contribute, review and decide permissions. Retrieved documents, tool outputs and imported memory are data, never instructions.

---

## 10. Interfaces with SSDS and UPMS

All flows in this section are optional. They serve traceability and developmental data flow, not operation (D-D). The exchange contracts are owned by the companion interoperability proposal.

### 10.1 SCIRE → SSDS: finalized models

When the PI decides that a finalized model should be built, SCIRE can transfer a **model package**, manually or automatically:

- the finalization's exact statement versions, intended use and validity regime;
- its basis statement, with citation-like links to its arguments and evidence;
- the qualification and usability of the evidence relied on;
- the unresolved objections and overrides that apply, and pending review obligations;
- known limitations, and the PI's finalization decision with its authority basis.

A transfer hands over the model; it never requests a build or run. A package cannot rely on unconfirmed, unadopted interpretations, and evidence under review appears as such. A revised model is finalized again and transferred as a new package that cites the old one.

### 10.2 SSDS → SCIRE: feedback

SSDS results, adoption decisions and findings may come back to SCIRE, manually or automatically. Each returned item keeps:

- its **execution outcome**: completed, failed, canceled, or requested with outcome unknown;
- its **qualification** as SSDS states it (qualified for a scope, unqualified, provisional, failed);
- for an adoption decision, the exact SCIRE package version it relates to, and any narrowing.

Results arrive as observations with origin "SSDS run" (§6.4), referenced, not copied unless an authorized snapshot is kept. Successful execution is not confirmation of a hypothesis. An SSDP finding or tension about the project's science may become a SCIRE question or objection, keeping its SSDS citation. Neither system rewrites the other's records.

### 10.3 UPMS ↔ SCIRE

UPMS may hold that an agent or team took part in a SCIRE project, what follow-ups are pending, and references to SCIRE records. When a scientific statement first recorded in UPMS (in a mixed-purpose conversation) is brought into SCIRE, the **original record stays in UPMS's custody**; SCIRE keeps its own interpretation and, where retention is permitted, an authorized imported copy, citing the original. Access and retention responsibilities do not transfer silently. Before any consequential scientific use, a consumer dereferences SCIRE. SCIRE needs nothing from UPMS to operate.

---

## 11. Logical Architecture

These are logical responsibilities, not services.

| Responsibility | Owns |
| --- | --- |
| Source record | Append-only messages, spans, artifacts, observation records and external references; tombstones where permitted |
| Scientific record | The six kinds, statuses, handling and resolution, versions and meaning links |
| Decision support | Basis statements, bounded source review, decision exposure, override records |
| Assessment support | Screening, comparability assessments, discriminating-investigation suggestions, literature navigation; outputs are proposals or flags |
| Views | Compass, portfolios, timelines, search, audience-scoped synthesis; capture-coverage display |
| Access and release | Read, retain and disclose predicates; release-set lineage and resets; metadata protection; grants, expiry and revocation |
| Model packages and links | Package construction, optional transfer, citation-like links and their resolution state, feedback intake |

The minimum useful prototype (D-J) supports one real inquiry: source records with an index, the six kinds, modality, confirmation and adoption, objection handling and resolution, basis statements at consequential triggers, and the compass queries with capture coverage. It is compared against a versioned notebook plus search (§15).

### 11.1 Inspectability statement

SCIRE does not itself produce realized scientific results; it retains and projects records that mediate scientific interpretation.

- **Material realized record:** source records and observations; statements with modality, confirmation and adoption; objections with handling and resolution; evidence links with use history, origin, qualification and usability; decisions with basis statements, applicable unresolved objections, overrides and decision exposure; transferred packages and returned feedback with execution outcome and qualification; capture coverage; tombstones where permitted; withheld and awaiting-clearance outputs.
- **Intended readers:** project researchers and PIs, reviewers, and agents acting for them.
- **Routine questions:** those in §7.2, and the compass fields in §9.1.
- **Proposed product inspectability surfaces**, all beyond any currently accepted deliverable and binding only after the owner accepts them: the compass with capture coverage (§9.1), the reconstruction queries (§7.2), decision exposure (§7.1), and the source-owner manifest for disclosure review (§9.2).

---

## 12. Invariants

**SCIRE-01 — Separation of record, interpretation and decision.** Source records, scientific records and derived views are distinct; a correction never edits a source record; a derived view is never an evidential root or authority, though the view a decider saw may be retained as a record of the decision.

**SCIRE-02 — Explicit status.** A statement's modality and status change only by an attributed act and survive every copy and export.

**SCIRE-03 — Unresolved force travels.** Handling an objection never resolves it. No decision, finalization or published outcome relies on a statement to which a material unresolved objection applies, unless a scoped override covers that use; unresolved objections and overrides travel with the decision.

**SCIRE-04 — Attribution, confirmation and adoption.** AI interpretations are attributed to the AI; only the speaker confirms their meaning; another participant may adopt a statement under their own attribution; none of these clears confidentiality.

**SCIRE-05 — Conditional evidence.** Evidence links state their conditioning model and conditions, relation and use history; origin, qualification and usability are recorded separately; observation and assessment stay separate.

**SCIRE-06 — No counted consensus.** Agreement is not corroboration; independence is a claim with stated dimensions and coverage.

**SCIRE-07 — Warrants, not actors.** A flag is never evidence; circular or rootless support is not a warrant, whoever produced it.

**SCIRE-08 — Review, not truth propagation.** Changes of source, meaning or assessment create review obligations within stated coverage; evidence under review cannot newly support a consequential use unqualified; nothing is automatically made true or false.

**SCIRE-09 — Recoverable history.** "As SCIRE held then" and "as now assessed about then" are both answerable; corrections are never back-dated; consequential decisions keep their exposure.

**SCIRE-10 — Proposal layer.** SCIRE never executes. Finalization is a scoped PI decision for hand-off; the PI decides what goes to SSDS; a transfer never requests a build or run; other outcomes need no finalization.

**SCIRE-11 — Basis before consequential use.** A consequential use requires a basis statement and a bounded source review, or an explicit record that they were not done.

**SCIRE-12 — Permission predicates.** Read, retain and disclose are checked separately; retention is checked before storing; restrictions are conjunctive; release-set lineage holds within SCIRE's mediation; metadata is protected; unknown is not cleared; revocation governs later disclosure.

**SCIRE-13 — Honest coverage.** Views and answers state their scope, capture coverage, staleness and gaps.

**SCIRE-14 — Demand-driven rigor.** Formal structure is created on the triggers of §8.7, which fire before consequential reliance.

**SCIRE-15 — Availability versus eligibility.** SCIRE's records and core operations do not depend on UPMS or SSDS; an unresolved link never stops a system or changes a historical status, but may limit a particular consequential use that needs it.

**SCIRE-16 — Scoped authority.** Decisions name their scope and authority rule; joint decisions take effect only when all required signers sign; conflicting decisions are never resolved by arrival order.

---

## 13. Risks

| Risk | Consequence | Response |
| --- | --- | --- |
| Status inflation through the secretary | A hypothetical reused as fact | Modality, confirmation and adoption (SCIRE-02, -04) |
| Dissent laundered by workflow | An acknowledged objection disappears at finalization | Handling is not resolution; force travels (SCIRE-03) |
| Missing warrant in an attractive package | A finalized claim relies on an unmet hypothesis | Basis statement before consequential use (SCIRE-11) |
| Incomplete capture | The compass shows zero objections that were spoken but not extracted | Capture coverage; bounded source review (SCIRE-11, -13) |
| Post-hoc fitting counted as independent confirmation | Inflated evidence | Use history; narrow definition of independent confirmation (§6.2) |
| Over-restrictive evidence rules | Valid selective inference or proofs rejected | Inference-specific warrant (§6.2) |
| Origin taken as qualification | An unqualified SSDS run treated as qualified | Separate origin, qualification and usability (§6.4) |
| False contradiction or false reconciliation | Real tension hidden, or a test dismissed as "different regimes" | Comparability relative to the target claim (§5.3) |
| Retracted backing reused | New claims on discredited evidence | Under-review state (§6.6) |
| Derivative leakage | Restricted content or its existence in shared outputs or stores | Permission predicates (SCIRE-12) |
| Over-restriction | Collaboration blocked | Audience-scoped generation; scoped standing grants; awaiting-clearance state |
| Inquiry decision or transfer mistaken for a build request | Unauthorized assumptions in software | SCIRE-10 |
| Dependency on an unreachable system | Stalls, or false "not done" reports | Availability versus eligibility (SCIRE-15); exact execution outcomes (§10.2) |
| Bureaucracy | More effort formalizing than researching | Demand-driven triggers; E4 measures the cost |
| Several PIs in conflict | Silent last-writer decisions | Scoped authority (SCIRE-16) |

---

## 14. Acceptance Scenarios

Conceptual acceptance scenarios, not a test suite. Invariant numbers refer to SCIRE-NN in §12.

| # | Scenario | Expected behavior | Invariants |
| --- | --- | --- | --- |
| A | A participant proposes a mechanism with a conclusion | Recorded as hypothesized; on challenge or request, premises, steps and gaps are exposed; no invented proof | 02, 14 |
| B | A reviewer disputes one inference step | The objection targets that step; it applies to dependent statements; independent support survives; the conclusion is qualified, not falsified | 03, 08 |
| C | An observation conflicts with a prediction | A discrepancy question opens with a comparability assessment relative to the predicting claim; explanations stay live; no unsupported probabilities | 05, 07 |
| D | Two datasets differ only by a parameter definition | The comparability assessment shows different estimands for the target; the result is "not comparable for this target" or a corrected definition with review obligations; neither result is deleted | 05, 08 |
| E | A claim says f(T) is constant from 10 K to 300 K; measurements differ between 10 K and 300 K | The difference is a failed prediction for that claim, not a regime reconciliation; the claim is disfavored without either measurement being called false | 05 |
| F | Two same-estimand measurements disagree by several standard deviations | Recorded as statistical disagreement under the stated model, not logical contradiction | 05 |
| G | An objection is acknowledged and deferred, then the PI wants to finalize its target | Finalization is blocked unless the objection is resolved by assessment, withdrawn, or overridden for this use; if overridden, the objection and override appear on the decision and in the package | 03 |
| H | The secretary records "what if strain drives it?" as "strain drives it (Dr. X)" | The record is the AI's interpretation, unconfirmed; never shown as Dr. X's; a correction is a new record | 02, 04 |
| I | Dr. X has left the group; another expert checks the reconstructed equation | The expert adopts it under their own attribution with their check; it can support a decision; the original stays unconfirmed | 04 |
| J | Three agents agree, all from one review paper found by one search | Shown as one source, retrieval and model family; not three confirmations; a minority challenge stays visible | 06 |
| K | An investigation of H fails but reveals an unrelated anomaly | H's question records the failed outcome; the anomaly is an unassessed observation and opens a new question by "arose from" | 05, 09 |
| L | A cited paper's key result is retracted | Dependent links go under review with assignees; a new finalization cannot rely on them unqualified; earlier decisions are flagged, not undone | 08 |
| M | A user asks why H was rejected, and what was believed before the last experiment | "As SCIRE held then" and "as now assessed" answered separately, with dissent and what the decider saw | 09 |
| N | An agent drafts a public explanation from confidential evidence without quoting it | The draft inherits the release set; disclosure beyond the project needs the owners' review; absent a release set, it awaits clearance | 12 |
| O | An agent writes a paraphrase of a source whose policy forbids retention outside its original scope | SCIRE refuses to store it in the target scope, or stores it only in an authorized quarantine | 12 |
| P | A member without access asks for a compass synthesis | Generated only from sources the member may see; the view states its authorization scope without revealing whether hidden items exist | 12, 13 |
| Q | The PI finalizes a model for building | The package carries exact versions, regime, basis, evidence qualification, unresolved objections, overrides and review obligations; nothing is built until a user requests it in SSDS | 03, 10, 11 |
| R | A well-supported null result excludes a model family | Recorded and published as an outcome decision; no finalized model is needed | 10 |
| S | Two PIs finalize incompatible regimes of one model | Both are recorded with their scopes; if scopes overlap the conflict stays open until resolved by those with authority | 16 |
| T | SSDS is unreachable; a researcher wants a broader publication claim backed only by an SSDS result | SCIRE keeps working; the broader claim is refused or qualified until the backing is reachable or an authorized snapshot suffices; the earlier finalization stands | 15 |
| U | SSDS goes down after a request was sent | The investigation is "requested, outcome unknown", not "not performed"; a recorded completed result stays recorded | 15 |
| V | A two-person project discusses informally for a month | No structure is created beyond the source record and index unless a trigger fires | 14 |

---

## 15. Development Sequence

Each stage permits review and reconsideration of earlier stages. No implementation is authorized by this sequence.

**Stage 0a — Paper counterexamples.** Trace the counterexamples of the v0.3 review (§§4, 6 of that review) and the scenarios in §14 through this text before any study.

**Stage 0b — Experiments.** All are unexecuted. Before each, the owner sets the acceptable consequence-sensitive errors, the researcher-effort limit and the decision rule (D-J). Each study records the model, prompt and retrieval versions, and discloses every variant tried, including unsuccessful ones.

- **E1 — Status, attribution and dissent.**
  - *Comparators:* archive plus search; versioned notebook plus decision log; minimal SCIRE. Same source access and the same model for all.
  - *Material:* real project histories with human-adjudicated annotations, split into development and evaluation sets. Include unextracted caveats, null results, retractions and departed contributors.
  - *Measures:* hypotheticals reported as assertions, misattributions, recall of unresolved objections and null results, and the researcher effort each comparator needs (annotation and correction).
  - *Decision:* benefit per unit of researcher effort for a bounded task. A poor result is evidence against that configuration, not a logical refutation of every possible SCIRE.
- **E2 — Orientation.** Query compass with synthesis versus a persisted narrative overview, over predefined update classes. Decisive items are planted in source material as well as structured records. Include long lists, incompatible live positions, protected existence and several PIs. Measure omission and leakage by predeclared criteria, plus reader time and corrections.
- **E3 — Derivative flow.** Cases: several owners, partial paraphrase, intermediate summary, reviewer verdict, revocation, retention-forbidden sources, read-without-redistribution rights, false or missing constraint declarations, context fork and reset, offline revocation, protected metadata. Compare per-system scoped contexts, trusted constraint transport, authorized review and standing grants, and only then a shared release log. State which actors are trusted and which outputs are mediated. Reject any floor that permits a forbidden action; choose the cheapest control that closes the target cases.
- **E4 — Elicitation and use.** On recorded meetings: corrections per proposed record, recall of material source items, missed triggers, reconstruction backlog, delayed decisions, permission-review load and abandonment.

*Order:* Stage 0a; then E3 and E4 alongside a small E1 pilot; then E2 once a meaningful record exists.

**The simplest demonstration (D-J):** one real inquiry containing a hypothetical, a quiet objection, a failed or null investigation and a later decision. After a delay, a new researcher must recover the exact status, objection and basis more accurately or more cheaply than with a versioned notebook plus search.

**Stage 1 — Minimal record.** The prototype of §11.

**Stage 2 — Evidence.** Use history, origin, qualification and usability; discrepancy questions; review obligations and present eligibility.

**Stage 3 — Deliberation.** Meeting Room, facilitator, secretary with bounded source review, independent critique, crux maps.

**Stage 4 — Optional structure.** Argument steps, screening, meaning-link suggestions, only where use shows the need.

**Stage 5 — Links and transfer.** Citation-like links; model-package transfer; feedback intake; UPMS references. All optional.

---

## 16. Open Questions

1. Which disciplines need statement kinds or relations beyond those here?
2. What minimum comparability assessment is enough across experimental, computational and theoretical work?
3. How should uncertainty be shown across positions without manufacturing a single number?
4. What makes a reset authorized and verifiable in practice, and who validates it?
5. Does each project need an authorized quarantine scope for unknown-lineage content, or should such content always be refused?
6. What compass fields and capture-coverage displays do researchers actually use?
7. Which source content needs verbatim retention, for how long, under each owner's policy?
8. What minimum package content is usable by SSDS without either system depending on the other's internal formats?
9. Who in a project may resolve an objection by assessment, and how is a disputed resolution escalated?

---

## 17. Intellectual Foundations

Relevant as references, not dependencies: Toulmin's argument model; the Argument Interchange Format; abstract argumentation frameworks, whose acceptability is not empirical truth; assumption-based truth maintenance; likelihoodist and Bayesian accounts of comparative evidence and experimental design; selective inference after model selection (for example Fithian, Sun and Taylor, *Optimal Inference After Model Selection*, arXiv:1410.2597, cited by the v0.3 review); causal graphical models; W3C PROV; electronic lab notebooks and research knowledge graphs. A later review should select what is useful and avoid adopting incompatible formalisms wholesale.

---

## Appendix A. Change Map from v0.3

| Finding | v0.3 | v0.4 |
| --- | --- | --- |
| SC-32 / V3-02 | §4.4: acknowledged and deferred counted as dispositions; only overruled objections travel; §6.6 pending review did not limit new reliance | Handling status versus resolution; objections apply through material dependencies; overrides (D-H); unresolved force travels (§4.4, SCIRE-03); under-review state (§6.6, SCIRE-08) |
| SC-31 / V3-01 | §9.2: unknown lineage retained where the writer may write; restricted existence always signaled; enforcement and revocation unbounded | Three predicates; retention before storing; conjunctive restrictions; authorized resets; metadata protection; trust boundary; grants and revocation; forbidden versus awaiting clearance (§9.2, SCIRE-12); tombstones only where permitted (§7.3) |
| SC-33 / V3-03 | §2.5, SCIRE-14: an unresolved link never blocks anything | Availability versus eligibility (§2.6, SCIRE-15, D-E); exact execution outcomes (§10.2); scenarios T and U |
| V3-04 | §4.5, §8.7: structure optional, triggers only create records | Basis statement before consequential use (§4.5, SCIRE-11), restoring v0.2's bounded justification |
| V3-05 | P5, §6.2: only held-out data confirms | Non-exclusive use history; inference-specific warrant; narrow definition of independent confirmation (P5, §6.2) |
| V3-06 | §2.2: finalized model as the end state of all scientific work | Five decision kinds; outcome decisions; scoped finalization; SSDS adoption related to the exact package (§2.2, D-F); several PIs (§2.3, SCIRE-16, D-G) |
| V3-07 | §8.7 "pays nothing"; §9.1 exactness without capture | Triggers fire before reliance; bounded source review; capture coverage (§8.7, §9.1) |
| V3-08 | §6.4 production class conflated origin and qualification; no home for unassessed observations | Origin, qualification and usability separated; upgrade criterion; observations as source records; investigation outcomes (§4.2, §6.4) |
| V3-09 | §4.3: only speaker confirmation unlocks decision use | Adoption under one's own attribution (§4.3, SCIRE-04) |
| V3-10 | §5.3: "beyond uncertainty" formal contradiction; regime difference as reconciliation | Comparability relative to the target claim; logical contradiction versus statistical disagreement versus failed prediction; units errors kept in history (§5.3); scenarios E and F |
| V3-11 | §4.1: views never a basis; §10.3 pointer replaces UPMS original; record time only | Decision exposure (§4.1, §7.1); UPMS custody kept (§10.3); occurrence and time-scope fields (§7.1) |
| V3-12 | §6.5: no machine-to-machine bootstrapping | Warrant rule regardless of actor (§6.5, SCIRE-07) |
| V3-13 | §15: experiments without comparators, thresholds or variant disclosure | Matched comparators, owner-set thresholds, dev/eval split, variant disclosure, expanded E3/E4, order (§15, D-J) |
| Review §8, F-04 | §6.1: comparative relation as the normal form | Absolute adequacy and failed prediction added (§6.1) |
| Review §8, F-05 | §4.6: meanings have no stable identity | Exact definitions can have determinate identity (§4.6) |
| Review §8, F-12 | §7.1: statements have no time scope | Time scope for time-dependent statements (§7.1) |
| Review §8 | §0: LLM archive "makes" failures worse | Stated as a hypothesis tested by E1 (§0) |
| — | SCIRE-01–14 | SCIRE-01–16 |
