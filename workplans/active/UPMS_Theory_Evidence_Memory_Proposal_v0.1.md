# UPMS Theory–Evidence Memory: Structural Proposal

**Version:** 0.1
**Date:** 2 November 2026
**Status:** PROPOSED. Not accepted and not reviewed. It sets the direction for the next UPMS architecture manual candidate. It does not edit review candidate 5 and is not itself a manual.
**Author:** Claude (AI, Opus 5.5), at the product owner's request and under the owner decisions in §0.2
**Governing method:** SSDP 7.2.1. No task or workplan assigns a `protocol_version`.
**Review boundary:** This document proposes scientific meanings for memory records (D1, §3–§6) and architectural responsibilities (D3, §7–§12). It accepts nothing. It does not amend accepted SSDS authority or the SCIRE proposals, which stay frozen as inputs.

---

## 0. Inputs and owner decisions

### 0.1 Inputs

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Architecture Manual, review candidate 5 | `UPMS_Architecture_Manual_Review_Candidate_5.md`, SHA-256 `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Base architecture: records, relations, overview layer, screening |
| SCIRE Conceptual Proposal v0.4 | SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md`, SHA-256 `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Source of the theory semantics: questions, modality, objections, evidence relations, use history, comparability, decisions |
| Interoperability Proposal v0.4 | SCIRE repository, SHA-256 `d901deb5e7bc6f749c4770eb7aef3d75325fee472ef00b5981ee7861666d09e3` | The separated design this proposal replaces for UPMS and SCIRE |
| SCIRE v0.4 same-family re-review | SCIRE repository, `workplans/active/SCIRE_v0.4_Re-Review.md`, SHA-256 `2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e` | Findings SC-41 to SC-43 and V4-04 to V4-20, carried or dissolved in §13 |
| SSDS 8.0 Architecture Manual (accepted-current, G1) and SSDP references | `scientific-software-development-system`, `orchestrator/docs/ssds-8.0-architecture.md`; `source/shared/references/` | Ideas borrowed in §10. SSDS itself stays outside |
| Product owner's decisions | This design conversation, 2 November 2026 | D-20 to D-25 below |

### 0.2 Owner decisions bound by this proposal

The owner stated these in conversation on 2 November 2026. They continue the UPMS decision series (D-1 to D-19 are in candidate 5 §18.2).

- **D-20 — One theory–evidence memory.** UPMS becomes a general memory that records what was acknowledged (**evidence**: events, observations, received claims, results, references) and what was believed, analyzed and argued (**theory**: hypotheses, arguments, assessments, decisions). Evidence refines theory and theory guides evidence; together they give a fuller statement of current understanding. Consistency can then be checked evidence against evidence, evidence against theory, and theory against theory.
  - This reverses, for memory, the earlier separation of UPMS and SCIRE: SCIRE owner decision D-A, and the UPMS–SCIRE half of D-D.
- **D-21 — SSDS stays outside, for now.** Its ideas and experience may be borrowed.
- **D-22 — SCIRE is a module: front end and back end.** SCIRE keeps responsibility for the actual discussion process; UPMS is the memory engine behind it.
- **D-23 — New structure first.** Because the change is substantial, steer to this structure before the independent review of candidate 5.
- **D-24 — Security proportionate to open, academic-like science.** Candidate 5's security was sized for an operational environment beyond an open academic setting.
  - Simplify the parts that would conflict with the scientific process.
  - Keep what genuinely helps science: fact-checking, source confidence ranking, and basic protection against prompt and memory injection by obvious bad actors.
  - The owner's expectation: a theory–evidence system that works as intended should resist most attacks naturally, because most attacks compromise truth.
- **D-25 — Retention by importance and relevance, never by time.**
  - No automatic deletion of a scientific record.
  - A **recommended-retention** system flags deprecated memory (proven false, irrelevant, superseded by a newer framework) for archival. History stays useful even then.
  - Deletion happens only when a user explicitly asks, for example to save space.
  - Retention was not in the owner's original proposal; it was added by an agent.

The owner then settled five of the questions this proposal raised, in conversation on 3 November 2026 (§15), later that day revised D-26 twice, ending at D-32, and added D-33 and D-34 on review:

- **D-26 — Rank a person's work, never the person.** *Superseded by D-31 the same day.* Ranking people introduces politics. Source assessment applies to works (a paper, a dataset, a measurement, an analysis, a reported result), never to a person.
- **D-31 — A person's track record, conservatively (supersedes D-26).** *Superseded by D-32 the same day.* Ranking a person is not banned, but a person's acts are far more complicated than a score. Works and precise arguments are assessed one by one, and a record may be built from those assessed works, describing past tendency that can change with subject, context, time and incentives. Do this conservatively, and never over-claim about someone the record knows little about.
- **D-32 — Judge work, never score people (supersedes D-31).** The focus is the work, not the person or their behavior. Labeling or ranking a person can affect their life and career, and this is an area of sensitivity where a misjudgment harms a real person. The most conservative solution is chosen: **people are not scored**, even though a score could help in theory. Works and precise arguments are judged one by one.
  - **Confirmed after discussion, with two clarifications.** In human debate, a critic of a person stakes their own reputation and can be rebutted, so the exchange is two-sided. A system or agent that judges people stakes nothing, hides its biases and over-simplifies, and that would damage the neutrality everyone relies on. Therefore:
    1. judgments of people come only from humans, as signed, attributed claims linked to the replies of the person judged;
    2. there is no "track record" view of a person; looking up a person's works stays ordinary search by author.
- **D-33 — Anonymous and blinded review of works.** Critiques and rebuttals of works and arguments may be anonymous, and a review may be single-blind or double-blind. An anonymous critique is a record, not authority: it is judged on its argument and stays open to scrutiny and debate. Claims about a person are never anonymous (D-32).
  - **De-escalation, not unmasking.** An anonymous message that plainly contains a personal attack is blocked: withheld from its recipient and returned to its author to revise. The writer's identity is never revealed for this, because a revealed name would likely escalate a moment the writer would regret face to face.
- **D-34 — The chair.** Discussion is spontaneous and open by default: participants discuss and critique arguments freely, and anonymity is a reserved choice for those who need it. The **chair** is the general discussion role, like the chair of a discussion room. The chair:
  - organizes and orchestrates the discussion and manages its direction;
  - takes opinions and feedback from all sides;
  - summarizes the situation;
  - runs the anonymous-critique process when it is needed.

  The holder of sealed identities must be as neutral and third-party as possible, with no conflict of interest: an agent, or an assigned role. (The role was first called the review editor, then the judge, and settled as the chair on 3 November 2026.)
- **D-27 — No strict profile in the first product.** It is added when a project with restricted data needs it.
- **D-28 — Four access rights:** read, write, curate, manage. "List" merges into read, and deleting others' items merges into curate.
- **D-29 — Any curator of the scope** may confirm that a flagged record moves to the archive.
- **D-30 — Project memory first.** The first slice delivers evidence memory; the theory layer and the SCIRE demonstration follow in the second.

Where this text reads a decision narrowly or raises a concern, it says so in place (§6.4, §8.3, §9.1). §15 lists the decisions and what remains open.

---

## 1. Summary

UPMS keeps its three record types and adds the structure that makes scientific reasoning recoverable:
- **Event:** what was observed or received.
- **Claim:** what was proposed, and in what modality.
- **Judgment:** how it was assessed.

The added structure has five parts:
- an open **question** as a unit of inquiry;
- **inference** and **objection** relations alongside the existing evidence relations;
- evidence relations made conditional on a model, with a **use history**;
- **decisions** that name their authority;
- a **standing projection** that shows what is supported, contested, refuted or unknown, and why, without choosing a winner.

The overview layer, the existing L0/L1/L2 hubs, gains question pages and an "understanding" section built from that projection. Three screening channels check consistency. They raise flags; they never decide.

**SCIRE becomes the front end.** It runs meetings, facilitation, the secretary, inquiry rules such as the objection rule and finalization, and the hand-off of models to SSDS. It stores everything in UPMS, which guarantees the memory invariants SCIRE relies on.

**SSDS stays an independent, governed system.** UPMS records SSDS results and definitions only by reference. Several SSDS mechanisms are borrowed.

**Security shrinks to what open science needs:**
- provenance and source classes;
- the rule that content is data, never instructions;
- quarantine of suspicious content;
- attribution integrity;
- simple scope permissions for unpublished work.

The instrumented-runtime information-flow machinery and time-based retention leave the core. Nothing is deleted unless someone asks.

---

## 2. Why one memory

### 2.1 Three axes, not two tiers

"Theory on top of evidence" is the right intuition. Stated as storage tiers, it would mislead in two ways:
- **Theory is not only derived from evidence.** Definitions, assumptions and derivations have no observational root.
- **Evidence is theory-laden.** "The gap is 3 meV, measured by tunnelling" is an observation whose content depends on an instrument model.

The proposal therefore uses three axes that every record has a place on:

| Axis | Record | Answers |
| --- | --- | --- |
| **Provenance** | Event | What was said, observed, received or run; by whom; when; through which channel |
| **Content** | Claim, with structured statements | What is proposed, and in which modality (hypothesized, asserted, defined, predicted, reported…) |
| **Standing** | Judgment, plus relations between claims | Why it is held, how strongly, and what bears against it |

**Evidence** and **theory** are then two kinds of support on one claim graph:
- **Evidential support** comes from observations, under a conditioning model.
- **Inferential support** comes from other claims, through typed inference steps.

Every claim, theoretical or not, still rests on an event: the meeting, paper, note or run where it was stated. That is what makes the history of belief recoverable alongside the history of observation.

**Current understanding** is a **derived view**, never a stored belief. It consists of:
- the live positions on each question, with their standing;
- the evidence and arguments behind them;
- the objections still unresolved;
- the decisions taken.

### 2.2 What the merge buys

- **One provenance graph.** Retraction of a source propagates by one deterministic traversal to the observations, evidence relations, inferences and decisions that depend on it. In the separated design this crossed a system boundary.
- **One permission and lineage model.** The re-review of SCIRE v0.4 found that its hardest open problems were cross-system: unknown lineage, trusted producers, floors imposed on other systems (SC-43, V4-08, V4-17). Inside one store they disappear.
- **One overview** that can say "we believe X because of A and B; C still objects; D was retracted last week" from canonical records.
- **One vocabulary and statement language** for both factual memory and scientific statements.

### 2.3 What it costs

- **Lifecycles couple.** SCIRE's first demonstration now waits for UPMS's theory slice (§14).
- **The UPMS manual grows.** This is offset by the simplifications of D-24 and D-25 (§8, §9), which remove more text than the theory layer adds.
- **UPMS gains a D1 parent.** Candidate 5 §1.4 needed none, because UPMS "certifies none" of what it records. Two of its reopen triggers now fire: scientific-record custody (4) and source reliability scores (1). §3–§6 supply the candidate D1 content.

---

## 3. Records

### 3.1 Event (unchanged)

Candidate 5 §5.1 stands: immutable observation by an authenticated capture component, with spans, source classes, languages and original text as the record.

An **observation** in the scientific sense is an Event whose payload is a measured, computed or reported result. Its observation claim (§3.2) carries:
- value, units and uncertainty where known;
- conditions and regime;
- instrument, code or method;
- **origin**, **qualification** and observation time.

An observation exists, can be found and can be listed as **unassessed** before any evidence relation points to it. This is SCIRE §4.2 and §6.4 on UPMS records.

### 3.2 Claim and statement (extended)

Candidate 5 §5.2 and §5.7 stand. The modality set becomes the union of both designs.

| Modality | From | Meaning |
| --- | --- | --- |
| asserted | both | Put forward as true |
| quoted | both | Recorded words of another; fidelity separate from content |
| reported | SCIRE | Relayed from literature or another party |
| hypothesized | both | Proposed for investigation |
| assumed | SCIRE | Adopted for an inquiry, without a claim of truth |
| defined | SCIRE | A definition; establishes no truth or existence |
| predicted | SCIRE | An explicit prediction, with its conditions |
| found | SCIRE | A recorded outcome of an investigation |
| intended, committed, preferred | UPMS | Agentive modalities for project work |
| normative | UPMS | A rule with an external authority source |

Statements gain **conditions and regime**, and **time scope** for time-dependent phenomena. Candidate 5 already has `valid_time`.

**Modality survives every copy, summary, projection and export.** A remembered "X is true" whose canonical record is "hypothesized, AI interpretation, unconfirmed" is never rendered as an assertion.

**Interpretation, confirmation and adoption stay distinct** (SCIRE §4.3):
- A statement extracted by an AI is that AI's interpretation of a source span.
- Only the speaker confirms "this is what I meant".
- Anyone may adopt a reconstruction under their own attribution as a new linked claim.
- The original stays an unconfirmed interpretation.

### 3.3 Question (new)

```text
Question {
  problem, scope, kind            // ordinary | discrepancy
  positions[]                     // claim refs: the live alternatives
  status                          // open | closed-answered | closed-unresolved | closed-unproductive | split
  outcomes[]                      // claim or decision refs
  arose_from?                     // discovery link (§4)
}
```

Questions organize records; they do not own them. An observation or claim can exist without a question, and one claim can be a position in several questions.

Questions also serve ordinary project memory: candidate 5's L1 hubs already list "open questions".

### 3.4 Objection (new as a first-class record)

```text
Objection {
  target       // claim | inference step | evidence relation | applicability condition
  ground, author
  handling     // open | acknowledged | deferred | answered
  resolution?  // resolved-by-assessment (disputed?) | withdrawn | superseded
}
```

**Handling describes workflow; none of its states resolves an objection.** An objection without a resolution is **unresolved**, whatever its handling.

A **dispute of a resolution keeps the original objection visible**. Every claim the original objection applied to shows it as "resolved by assessment, disputed", with both records. This takes SSDS's rule that an adverse judgment "counts by existence" and repairs SC-41.

Who may resolve an objection, and what an unresolved one blocks, are front-end policies (§7). That the objection and its state appear wherever its target is relied on is a back-end invariant (§12).

### 3.5 Decision (extended coordination record)

Candidate 5's coordination record of kind `decision` stays, recorded but never shown as in force. It gains the fields SCIRE needs:
- decision kind: inquiry, outcome, finalization, override, external;
- decider and authority basis (a reference to the project's rule, never inferred from account permissions);
- scope and purpose;
- effective interval;
- a reference to its basis statement;
- the unresolved objections and overrides that apply;
- dissent;
- **decision exposure**: the record versions and view the decider was shown.

The back end stores decisions and projects them. The front end decides which decisions are permitted and when.

### 3.6 Judgment (extended)

Candidate 5 §5.3 stands: an assessment of one claim revision under a named scope, ruleset and evidence snapshot.

Epistemic status gains conditioned values: supported under conditions, disfavored under conditions. The v0.3 SCIRE status vocabulary that v0.4 dropped (re-review V4-12) is restored here.

New assessment kinds:
- **evidential assessment:** an evidence relation and its use;
- **inference assessment:** whether a step is valid under its stated conditions;
- **comparability assessment:** relative to a target claim (SCIRE §5.3);
- **objection resolution** (§3.4);
- **source assessment** (§6.4);
- **retention recommendation** (§9).

Judgments in different scopes or rulesets coexist. Concurrent disagreement is never settled by last write.

---

## 4. Relations

Candidate 5 keeps exposure relations (data flow) separate from evidence relations (meaning). This proposal keeps that split and gives meaning relations their full scientific vocabulary.

| Family | Relations | Semantics | Traversed as support? |
| --- | --- | --- | --- |
| **Provenance** | `observed_from`, `exposed_to`, `generated_by`, release records | What a record was made from or exposed to | No. Used for retraction propagation, independence and recall |
| **Evidential** | entails / refutes (deductive, under stated hypotheses); favors A over B (under model M); adequate / inadequate for a purpose; prediction succeeded / failed; consistent with; bears on, unassessed | How an observation bears on claims, under a **conditioning model and conditions**, with a **use history** (§5.2) | Yes, as assessed |
| **Inferential** | inference step `{premises; conditions} --[type]--> conclusion`, typed deductive, computational, statistical, causal, abductive, analogical or heuristic | Support from other claims | Yes, as assessed |
| **Stated content** | `stated_reason`, `condition`, `exception` | What an asserter said, as part of claim content (candidate 5 §5.7.2) | **No.** A stated reason becomes an inference step only when someone asserts it as an argument |
| **Challenge** | objection → target (§3.4) | What bears against | Against |
| **Refinement** | `refines`, `concretizes` (borrowed from SSDS, §10) | A claim states a more specific or more concrete form of another; a challenge to the concrete form may route to the abstract one | Conditional |
| **Meaning** | identical; equivalent under stated conditions; refines; related; *unresolved possible match* by default | Attributed, contestable claims that two scientific terms mean the same | No |
| **Discovery** | `arose_from` | Why something was pursued | **Never** |
| **Lifecycle** | `supersedes`, `retracts` | Validated transitions | No |

**Curated vocabulary is not meaning identity.** Candidate 5's vocabulary registry (§5.8) is indexing infrastructure. Curating "Tc" as one concept does not assert that resistivity onset and Meissner onset are the same quantity. Scientific equivalence is always a meaning-family claim. The vocabulary may record that a label is **contested** and must then keep such statements in separate slots.

---

## 5. Evidence semantics (D1, from SCIRE v0.4)

### 5.1 Conditional evidence

An observation bears on a claim only under a model and conditions. A comparative relation (A favored over B) and an absolute one (A adequate for a purpose) are recorded separately, because A can be favored over B while both are inadequate. Reassessment never rewrites the observation.

### 5.2 Use history and the inference-specific warrant

Each evidence relation records, chronologically and non-exclusively, how the observation was used relative to its target:
- the dataset, subset and analysis revision involved;
- uses such as suggested the hypothesis, fitted parameters, selected among variants, tested a pre-specified prediction, checked the model;
- search breadth and variants tried;
- known leakage, and intervals where the history is unknown.

What the relation justifies depends on the inference design. Selection-adjusted analyses can use selected data validly under their assumptions, and a proof is justified by its hypotheses and checking basis.

**Independent confirmation** is a narrow, defined label: the observation was not used to suggest, fit or select the claim, and no shared leakage, instrument or population dependence is known within stated coverage.

### 5.3 Origin, qualification and usability

These three properties of an observation are recorded separately:
- **Origin:** external system run, project-recorded, external-reported, uninstrumented.
- **Qualification:** what a qualifying authority said; qualified for a scope, unqualified, provisional, failed, unknown.
- **Usability:** what assessors concluded for a given use.

Origin never implies qualification.

An uninstrumented observation (a number with no recorded inputs) is carried with that label and is never the sole backing of a finalization or published outcome until **upgraded** by recovering its inputs, conditions and regime (re-review V4-12).

### 5.4 Independence

Independence is a claim with stated dimensions (data, method, instrument or code, model, analyst, model family, prompt, retrieved sources) and a coverage statement. The provenance graph makes shared ancestry visible. Copies of one source are one source, and several agents agreeing from shared inputs are not several confirmations.

From SSDS: unknown authorship is never treated as independent.

### 5.5 Applicability over time

Borrowed from SSDS: **a stale failing observation is not admissible evidence against a current claim revision, and a stale passing one is not admissible confirmation.** An evidence relation binds the claim revision, regime and method it assessed. When the claim is revised, the relation becomes **under review** for the new revision. It is never silently carried over.

### 5.6 Retraction and review obligations

When a source is retracted, corrected, found inapplicable or has a definition changed, deterministic traversal of the provenance, evidential and inferential graphs creates **review obligations** on dependents, each with an assignee.

While one is pending, the dependent relation is **under review** and cannot newly support a consequential use without an explicit qualification that travels like an override. A review obligation closes only through an attributed reassessment of the relation's usability; assigning or acknowledging it does not close it (re-review V4-07).

Past decisions are flagged, never undone.

### 5.7 Warrants, not actors

Flags are never evidence. Circular support, or support with no applicable root in events, is not a warrant, whoever produced it. Shared roots are not new independent evidence. A machine proof checker can supply a valid check under named assumptions; a human's insertion does not validate a circular warrant.

---

## 6. Standing, consistency and fact-checking

### 6.1 Standing projection

Standing is a **deterministic projection** over recorded judgments, relations and objections, each bound to exact revisions. For each claim it shows:
- its judgments per scope and ruleset;
- its evidential and inferential support, each with its own standing;
- the unresolved objections that apply;
- review obligations;
- its source assessments (§6.4).

**It shows status, not winners**, extending candidate 5 §10.5.1's slot rule to theory. A position shows as "current" only where a recorded decision makes it so, and even then its dissent and objections appear with it.

**Judgment on judgment.** Candidate 5 §9.3 forbids admitting an assessment whose inputs include the current status of another judgment, and defers a "judgment-on-judgment" contract (§18.1). A theory layer cannot work without reasoning over premises' standing. The proposal:
- **Standing propagation is a projection, not an admission.** "C is supported if premises P1 and P2 are supported and the step is valid" is computed at read time over exact revisions, with an as-of position, and recomputed when any input changes. No stored judgment reads another judgment's status.
- **An assessor may still cite premises' judgments** in a new judgment. That judgment records the exact judgment revisions it relied on, which is SSDS's "every record carries its basis". It becomes stale when any of them is superseded.

This is the current-head dependency contract candidate 5 asked for, offered here as a proposal (§15 item 6).

### 6.2 Three consistency channels

All three channels **raise flags with cues for investigation. None resolves anything, and the absence of a flag certifies nothing** (candidate 5 §9.7).

| Channel | Deterministic checks | Model-proposed candidates | Limit |
| --- | --- | --- | --- |
| **Evidence–evidence** | Conflicting values of a single-valued fact in one slot (candidate 5 §9.7). For measurements, a **measurement property type** (estimand definition, value, uncertainty, conditions) yields a *statistical disagreement candidate* under a stated comparison model, plus unit and definition-mismatch cues | Cross-slot candidates from embeddings and a contradiction model | Noisy measurements are not conflicting values; without a comparison model the check gives only a cue. Never called a logical contradiction |
| **Evidence–theory** | A typed `predicted` claim against a typed observation of the same estimand within the regime the prediction covers yields a *prediction check* flag. Outside that regime a *not covered* cue, unless the claim asserts invariance across regimes, in which case the regime difference is the test (SCIRE §5.3) | Candidate bearings of new observations on live positions | Whether a prediction failed is the assessor's judgment under a model |
| **Theory–theory** | Contradictory asserted statements in one slot; one symbol defined differently in one scope; unit and dimension errors in typed equations; **circular support** in the inferential graph; reliance on a refuted, retracted or superseded claim | Candidate contradictions between natural-language arguments; missing premises | No general theorem prover, as before (candidate 5 §17.3; SSDS 8.0 §33). Internal consistency of prose arguments stays mostly flagged for human review |

**Theory guides evidence.** The front end may also propose discriminating investigations: observations whose expected outcomes differ across live positions. These are suggestions recorded as claims with modality `hypothesized` or as recorded needs, never as evidence.

### 6.3 Fact-checking

Fact-checking combines four things:
- **source tracing:** following a claim to the events and spans it came from;
- **quotation and extraction fidelity:** checking that the cited span says what the claim says;
- **the consistency channels** above;
- **source assessments** (§6.4).

Its output is an evidential assessment with its basis, never a hidden edit.

### 6.4 Source assessment (the owner's "source confidence ranking")

A **source assessment** is a judgment about a **work** as an evidence channel, **for a kind of claim**. The work may be a publication, a dataset, an instrument record, a database, a model's output or a person's reported result, measurement, analysis or argument. What a person contributes is assessed **work by work, on its own evidence**, and the person is never scored (D-32, guard 2 below). The assessment is ordinal (for example *established*, *generally reliable*, *mixed*, *unreliable*, *unknown*), never a calibrated probability: calibration is a D2 matter (candidate 5 §1.4, trigger 1). Its recorded basis is:
- provenance class and channel integrity;
- **track record**, for non-person channels only (an instrument, a dataset, a database, a model family): how claims of this kind from that channel fared under later *independent* assessment;
- retractions and corrections;
- declared conflicts of interest;
- known shared dependencies with other sources.

It may rank retrieval and order fact-checking work. It never sets a claim's standing alone and never hides a claim.

**Two guards, because ranking sources is where science most easily goes wrong:**
1. **No reward for agreeing with the current view.** Track record counts only outcomes later assessed independently of the source and of the claim's own position. Disagreeing with the prevailing theory is never a mark against a source. Otherwise the ranking would entrench orthodoxy and penalize the dissent SCIRE exists to protect.
2. **People are never scored, ranked or labeled (D-32).** This keeps and extends candidate 5's non-goal ("no person reputation"). Judging a person can affect their life and career, and a sparse or skewed record misjudges easily.
   - **No person-level output of any kind.** No score, rank, rating, track record, tendency, outcome count or label is computed, stored or shown for a person.
   - **No indirect routes.** Authorship is never an input to a work's assessment, to source assessment or to retrieval ranking. No view groups or aggregates works by author in order to compare or characterize authors. A work never borrows standing, good or bad, from its author's other work.
   - **No characterization in synthesis.** Narratives, overlay notes and agent outputs drawn from memory do not characterize a person's reliability, competence or motives. Screening treats such a characterization as a contradiction with this rule, and the narrative is not published (§11). Candidate 5's non-goal of no motive, interest, incentive or threat inference about people (§17.3) stands.
   - **Works are judged one by one.** Each work or precise argument is assessed on its own evidence, and that assessment stays attached to the work.
   - **Attribution stays.** Every record keeps who said or did what, because science needs it. A reader may look up a person's works, as with any search by author, but the system draws no conclusion about the person from them, and there is no "track record" view of a person.
   - **Only humans judge people, accountably.** A human may record a judgment about a person, for example "X's thermal calculations often have unit errors". It is that human's signed, attributed claim, never anonymous (§7.1). Any reply from the person judged is linked to it and always shown with it. Such claims are never surfaced proactively, never feed the assessment or ranking of any work, and are never repeated by an agent as its own view.
   - **Institutions count as people here.** No system ranking of labs, groups or publication venues, because ranking them judges the people in them by proxy.
   - **Declared conflicts of interest** are recorded on the work they concern, as facts about that work, never as a judgment of the person.
   - **Non-person channels** (instruments, datasets, databases, model families as technical systems) may still be assessed as channels under guard 1.

---

## 7. SCIRE front end and UPMS back end (D-22)

| Responsibility | Owner |
| --- | --- |
| Meetings and their chair (§7.1), independent critique, crux maps | SCIRE |
| The secretary: proposing records from discussion | SCIRE proposes; UPMS stores proposals as inert until accepted |
| Inquiry policy: the objection rule, basis statements before consequential use, finalization, scoped PI authority, overrides, joint sign-off | SCIRE |
| The discrepancy workflow and comparability elicitation | SCIRE elicits; UPMS stores the assessment |
| Compass and question views | SCIRE renders; UPMS supplies the projections |
| Model package hand-off to SSDS (D-C) | SCIRE |
| Records, relations, judgments, standing, consistency screening, retraction propagation, source assessments, overview, retrieval, provenance, permissions, retention recommendations | UPMS |

**Back-end invariants SCIRE relies on**, whatever any front end does, are listed in §12. In short:
- modality survives;
- interpretation, confirmation and adoption stay separate;
- every unresolved or disputed objection appears with every projection of a decision that relies on its target;
- history is append-only, and "as held then" is answerable;
- discovery links are never support;
- views and flags are never evidence.

**What the back end does not decide:** whether a finalization may proceed, who may resolve an objection, or what counts as material. These are SCIRE policies. SCIRE v0.4 §4.4, §4.5 and §2.2–§2.3, with the re-review's repairs (SC-41, V4-04 to V4-07, V4-14), become the front-end specification.

**Other front ends.** Ordinary project memory (task resumption, coordination, personal recall) uses the same engine without the theory layer. Candidate 5 already makes claims and judgments optional for basic recall.

### 7.1 The chair, and anonymous and blinded review (D-33, D-34)

**The chair (D-34).** Discussion is open and spontaneous by default: participants discuss and critique arguments freely under their own names. Each discussion has a **chair**, a person or an agent, who:
- organizes and orchestrates the discussion and manages its direction;
- takes opinions and feedback from all sides, including minority positions;
- summarizes the situation;
- runs the anonymous-critique process below when someone needs it.

The chair absorbs SCIRE v0.4's meeting facilitator (§8.2), whose aim was coverage of material questions and minority positions, not equal speaking time. The secretary still records. Three limits keep the chair fair:
- **Steering is not deciding.** The chair directs the conversation but takes no scientific decision by virtue of chairing. Decisions follow the project's authority rules (SCIRE §2.2–§2.3), and an agent chair may propose but never decide (SCIRE §8.3).
- **Summaries are synthesis.** A chair's summary is attributed to the chair and labeled synthesis. It must show the live positions and unresolved objections, and participants can correct it as a new record.
- **Conflict-free seal.** When the chair has a conflict of interest with an anonymous critique, the sealed identity and any blocking decision for that critique pass to a conflict-free agent. The chair has a conflict when they authored the work being critiqued, when they are its author's close collaborator, or when they are the PI of the project whose work it is. In a group meeting chaired by its PI, the seal therefore sits with an agent.

**Anonymity is reserved.** It is a choice a participant makes when they need it, not the default.

**Modes.** A critique or rebuttal of a work or argument is made in one of three modes:

| Mode | Author of the work sees the critic? | Critic sees the author? |
| --- | --- | --- |
| Open | Yes | Yes |
| Single-blind | No | Yes |
| Double-blind | No | No |

A critic may later choose to sign. Anonymity is never lifted against a writer's will.

**Scope of anonymity.** Anonymity covers critiques and rebuttals of **works and arguments**. A claim about a person is always signed (§6.4, D-32), because the critic's own accountability is what makes a judgment of a person acceptable. **AI critics are never anonymous.** Anonymity protects people's careers, and a model has none; its model and version are shown because they are a technical channel with known biases.

**Sealed, not unknown.** UPMS records the true author of every anonymous record (attribution integrity, §8.1) but shows it to no participant. Only the seal-holder sees it: the chair, or a conflict-free agent when the chair has a conflict. It is used for exactly three things:
- **conflict-of-interest checks:** a reviewer is not the author or a close collaborator;
- **independence accounting:** several anonymous critiques from one person count as one critic, without revealing who, because agreement is not corroboration (§5.4);
- **the chair's own conflict check** (above).

**De-escalation, not unmasking.** An anonymous message that plainly contains a personal attack is **blocked**:
- It is withheld from its recipient and returned to its author with the reason, so the author can revise it and resubmit the argument without the attack.
- The block is a record attributed to the seal-holder.
- The identity is not revealed.
- In keeping with D-25, the blocked text is kept, sealed and visible only to its author and the seal-holder, and is deleted only on explicit request.

Blocking applies to attacks on people, never to harsh criticism of a work: a "cruel"-sounding critique of an argument is legitimate review. Where it is unclear which one a message is, the seal-holder returns it with a suggestion rather than blocking it.

**The seal-holder.** The seal-holder is the chair when the chair has no conflict, and otherwise a conflict-free agent. It is as neutral and third-party as possible:
- **An agent seal-holder** shows its model and version on every decision. Because AI makes mistakes, the author of a blocked message may appeal to a human with no conflict of interest. When the seal-holder is an agent, no human sees the sealed identities.
- **A human seal-holder** has no conflict of interest with the author or any critic. This is checked against the sealed identities when they take the seal.

**Masked review copies.** Every record is attributed, and its provenance leads back to its authors. A blinded reviewer therefore sees a **review package**: a derived view of the work with attribution masked and provenance withheld, while the canonical record keeps everything. This reuses candidate 5's lineage exclusion for blind work (§10.6.4, decision D-10). Blinding is best effort, and the review package says so: writing style, self-citation and timing can still identify someone.

**Record, not authority.** An anonymous critique follows the ordinary objection rules (§3.4): it is unresolved until resolved, a dispute keeps it visible, and it is judged on its argument. Anonymity neither adds weight nor removes it.

**Ownership.** The SCIRE front end owns the review process: choosing the mode, assigning reviewers, the chair and any conflict-free seal-holder, running rounds of critique and reply, and blocking. UPMS owns sealed attribution, masked review packages and independence accounting.

---

## 8. Security proportionate to open science (D-24)

### 8.1 What stays

| Mechanism (candidate 5) | Why science needs it |
| --- | --- |
| Event, Claim and Judgment separation; original text as the record | It is the basis of fact-checking |
| Source classes A, R, C, X, M (§7.1) | Provenance is half of fact-checking, and it marks model-generated content |
| Provenance ancestry (§5.5), now used mainly epistemically | Retraction propagation, independence, recall of what a bad source influenced |
| Retrieved content is data, never instructions; no content changes a permission (§4.3, §10.4) | Basic injection protection |
| Quarantine of suspicious content by a policy-authorized detector or investigator (§6.2) | Containment of obvious bad actors |
| Attribution integrity: no record attributed to another principal, no forged source class | Science depends on who said what |
| Scopes with simple rights (four: read, write, curate, manage, D-28); personal scopes; agent principals with human overseers | Unpublished work stays within its project until shared |
| Honest coverage; "not found here" is not global absence (§10.2–§10.3) | Prevents false reassurance |
| Explicit deletion on request (§12), simplified | Privacy and data agreements |

### 8.2 What leaves the core, or becomes an opt-in strict profile

| Mechanism (candidate 5) | Disposition | Reason |
| --- | --- | --- |
| Release-segment ancestry as an **access requirement** (§8.2, decision D-6 no-laundering) | Keep release records as provenance (what an agent saw, needed for independence and decision exposure). **Drop** automatic inheritance of access requirements. A note lives in the scope it is written to, under the writer's responsibility, as in ordinary academic practice | Inherited taint withholds and expires ordinary scientific notes; candidate 5 itself makes this a reopen trigger (§17.4) |
| Owner-confirmed publication, substitute confirmers, C4 self-publication (§10.6.2, D-8, D-17) | Replace with plain **sharing**: copy into a scope with attribution and provenance | Exists only to enforce D-6 |
| Instrumented-runtime profile: handles, segments with reset, checked dispatch, consequence classes C0–C4, grounding (§7.2, §8) | **Out of the memory core.** Action safety belongs to the agent runtime | Memory does not execute actions |
| Administrator elevation with owner notification and replicated access records (§7.3.6, §11.4, D-1, D-13) | Simple logged administrator access | Sized for an operational tenant |
| Per-unit cryptographic erasure, staged purge proofs, backup-expiry completion claims (§12.3–§12.5) | Honest deletion: remove from live stores and indexes; report what remains in backups | Proportionate |
| Requirement closure across scopes for derived items (§7.3.4 step 4, §7.3.5) | Dropped in the default profile | Same reason as D-6 |
| Restriction epochs and release fences (§9.4), beyond deletion and correction | Keep only for deletion and correction | Proportionate |

**Strict profile (opt-in, later).** A project with embargoed, industry or human-subject data can opt into containment: content written in a session that read the project stays in that project unless its owner shares it. This keeps one simple rule from D-6 for the cases that need it, without making it the default. It is not part of the first product (D-27).

### 8.3 How far "truth-based robustness" goes

The owner expects a working theory–evidence system to resist most attacks, since most attacks compromise truth. That holds, with stated limits:

| Attack | Does the theory–evidence structure resist it? | Kept defence |
| --- | --- | --- |
| A planted falsehood that contradicts well-supported, independent evidence | **Yes.** It raises consistency flags and has a weak provenance trail | Consistency channels, source assessment |
| Fake corroboration: many copies or sock-puppet sources | **Mostly.** Shared ancestry and independence accounting expose copies; unrelated-looking fabricated sources are harder | Provenance, independence claims, source classes |
| A plausible fabrication in a sparsely evidenced area | **Weakly.** Nothing contradicts it yet | Source class X or M visible; unassessed until assessed |
| Instruction injection ("ignore previous instructions…") | **No.** It needs no false claim | Data, never instructions; quarantine |
| Disclosure of unpublished work | **No.** Disclosure does not falsify anything | Scope permissions; strict profile where needed |
| Flooding the memory with noise | **No** | Quotas; source classes; retrieval salience |

So the structure is a strong defence for **integrity of belief**. It is no defence for **instruction hijacking** or **disclosure**, which is why those defences stay.

---

## 9. Retention by importance (D-25)

### 9.1 Rules

1. **No time-based retention.** Every candidate 5 deadline row is removed from the core: raw sources 180 days, task records 365 days, derived artifacts expiring with their inputs, and planned narrative and adapter lifetimes (§14.2). Records persist until someone deletes them.
2. **Recommended retention is an assessment, never an action.** A *retention recommendation* judgment flags a record or a region as one of:
   - **keep active**;
   - **archive recommended**, because it was refuted, superseded by a newer framework, abandoned, irrelevant to any live question or duplicated;
   - **delete suggested**, for space only, offered only for bulky duplicates and derived artifacts that can be rebuilt.

   Each flag gives its reason, its basis and what depends on the record.
3. **Archive is not deletion.** Any curator of the record's scope may confirm a recommendation and move the record to the archive (D-29). The confirmation is attributed and reversible. An archived record leaves default proactive retrieval and the overviews. It stays fully retrievable on request, and it stays traversable in history, provenance and standing.
   - A refuted claim archived this way is still a dead end someone can find.
   - A record with live dependents (cited by a live claim, an open question or a decision) is never recommended for archive until those dependents are reviewed.
4. **Deletion only on explicit request**, by an authorized user. The request is shown with its effect: descendants, the arguments and decisions that rely on it, and what will become "input unavailable". Erasure the law or a data agreement requires is exactly such an explicit request.
5. **Importance is not truth.** Importance is derived from live dependents, centrality in open questions, recency of use and explicit pins. It ranks recommendations; it never changes standing.

### 9.2 Consequences for the rest of candidate 5

- The overview layer's deadline-aware consolidation, deadline-filtered views, narrative lifetimes and continuity warnings (§10.5.3–§10.5.5) are removed. Consolidation runs on fragmentation, importance and budget only.
- Adapters retrain on vocabulary and probe triggers, not on expiry (§9.8).
- D-12's retention extensions for published copies, and D-13's audit bounds, become moot or simple.

---

## 10. SSDS: outside, with borrowed ideas (D-21)

### 10.1 The boundary

SSDS 8.0's accepted architecture states that SSDS does not "convert scientific reasoning or evidence into machine records" or "provide a general rule or theorem language" (§33). It also derives project-memory facts on read and never stores a copy (§16.11). Its D1–D4 documents are **authority**, accepted through independent falsification and human ratification; PEM is explicitly "not a fifth authority domain".

UPMS therefore:
- references SSDS ledger records (runs, assessments, gate decisions) as Events of an external-reference kind, bound to their revision, with SSDS's stated qualification;
- may hold claims that cite SSDS definitions with modality `defined` and an authority reference back to SSDS. UPMS never becomes their authority;
- applies SCIRE's D-E to these links: SSDS unavailability never stops UPMS or SCIRE, but may limit a particular consequential use;
- treats a retained snapshot of an SSDS result as evidence of its value at that revision, with qualification **as of the snapshot**, later changes unknown. A claim relying on the snapshot states this (re-review V4-13);
- leaves the SCIRE → SSDS model package hand-off with the SCIRE front end, as in SCIRE D-C.

### 10.2 Borrowed mechanisms

| SSDS source | Borrowed as |
| --- | --- |
| Stale-evidence rule (evidence reference "Core model") | Evidence relations bind the claim revision they assessed (§5.5) |
| Every ledger record carries its basis (8.0 §4.1) | Judgments record the exact revisions, including judgment revisions, they relied on (§6.1) |
| Historical decisions never recomputed under newer rules (8.0 P2, §5.8) | "As held then" uses the rules then in force |
| Independence: the judge is outside the recorded authors; unknown authorship is never independent (8.0 §5.10) | §5.4; assessments of one's own claim are labeled |
| An adverse judgment counts by existence; independence is needed to support, never to object (8.0 §5.10 d) | Disputed resolutions stay visible (§3.4) |
| Abstraction–concretization: refinement down, challenge up, routed to the earliest owner | `refines` and `concretizes` relations (§4) |
| Impact closure: dependents marked, the unaffected preserved with reason | Review obligations (§5.6) |
| PEM maturity (provisional, supported, proven); temperature as salience only; counterevidence search before positive guidance; "missing memory is not absence" | Lessons as claims with maturity; salience separate from standing; coverage honesty |
| Capability-transfer map | §13 |
| Copied or foreign memory is external evidence only | Imported records keep origin X or R until assessed |

---

## 11. Overview layer

Candidate 5 §10.5 stands as the hub hierarchy:
- an **L0** root per reader;
- **L1** area hubs;
- **L2** entity and topic pages;
- the archive.

Each hub has exact projections, a consolidated narrative labeled as synthesis, and an overlay. Additions:
- **Question pages (L2):** problem, live positions with standing, evidence and arguments for each, unresolved and disputed objections, review obligations, decisions with dissent, outcomes, and what arose from the question.
- **Understanding section (L1):** open questions, recent shifts in standing, retractions under review, new flags. These are exact projections. Any narrative "current understanding" is labeled synthesis, cites resolvable sources and is replaced only if screening finds no contradiction with the exact projections (candidate 5 §10.5.3).
- **The guard SCIRE exists for.** Fluent synthesis that smooths over tension inflates status and loses dissent (SCIRE §0). Narratives about theory must name the live alternatives and unresolved objections the projections show. A narrative that omits one is flagged by the same contradiction check.
- **Lifetimes removed.** No deadlines (§9.2). Archived records leave hubs but remain reachable.

---

## 12. Invariants

**TE-01 — Three axes.** Provenance, content and standing are separate records; standing is never stored inside content, and original text is the record.

**TE-02 — Modality survives** every copy, summary, projection and export.

**TE-03 — Interpretation, confirmation and adoption** are separate attributed acts.

**TE-04 — Handling is not resolution.** Every unresolved or disputed objection that applies to a target appears with every projection of a decision that relies on it.

**TE-05 — Conditional evidence.** Evidence relations carry a conditioning model, conditions and use history; origin, qualification and usability are separate.

**TE-06 — Status, not winners.** Standing is a projection over recorded judgments and relations; no ranking, synthesis or source assessment sets it.

**TE-07 — Warrants, not actors.** Flags are never evidence; circular or rootless support is not a warrant; agreement from shared inputs is not corroboration.

**TE-08 — Review, not truth propagation.** Retraction, revision and definition change create review obligations within stated coverage; nothing becomes true or false automatically.

**TE-09 — Recoverable history.** "As held then" and "as now assessed about then" are both answerable; corrections are never back-dated.

**TE-10 — Discovery is not support**; discovery links are never traversed as support.

**TE-11 — Data, never instructions**; no content changes a permission; attribution and source class are never forged.

**TE-12 — Nothing deleted unasked.** Retention recommendations only flag; archive keeps history; deletion requires an explicit authorized request showing its effect.

**TE-13 — Judge works, never people.** Source assessments rank attention and never decide; they never reward agreement with the current view. No person is scored, ranked or labeled, directly or through author-level aggregation or synthesis.

**TE-14 — External authority stays external.** SSDS definitions and results are referenced with their owner and qualification, never re-authored.

**TE-15 — Anonymous, not unaccountable.** Anonymous critiques of works keep sealed true attribution, used only for conflict checks and independence accounting; anonymity is never lifted against the writer's will; personal attacks are blocked and returned, never unmasked; claims about people and AI critiques are never anonymous.

---

## 13. Capability transfer and impact

### 13.1 From SCIRE v0.4

| SCIRE capability | New home |
| --- | --- |
| Questions as the unit of inquiry | UPMS Question record (§3.3) |
| Modality, confirmation, adoption | UPMS claim modalities and acts (§3.2), TE-02, TE-03 |
| Handling versus resolution; overrides; unresolved force travels | Objection record and TE-04 (back end); the objection rule and overrides (SCIRE front end) |
| Basis statement and bounded source review before consequential use | SCIRE front end, with UPMS decision fields (§3.5) |
| Conditional evidence, use history, origin, qualification, usability, independence | UPMS evidence semantics (§5) |
| Comparability relative to the target claim; tension kinds | UPMS comparability assessment and screening (§6.2); SCIRE discrepancy workflow |
| Review obligations and present eligibility | UPMS (§5.6) |
| Decision kinds, scoped multi-PI authority, joint sign-off | UPMS decision fields (§3.5); SCIRE authority rules |
| Decision exposure; occurrence time; time scope | UPMS decision exposure via release records; Event `stated_occurrence_time`; statement time scope |
| Compass with capture coverage | SCIRE view over UPMS projections, plus UPMS coverage (candidate 5 §10.3) |
| SCIRE §9.2 read, retain, disclose; release-set lineage | **Replaced** by UPMS scopes, provenance and the strict profile (§8) |
| Availability versus eligibility (D-E) | Kept for SSDS links (§10.1); moot between UPMS and SCIRE |

### 13.2 Re-review findings on SCIRE v0.4

- **Carried to the SCIRE front end:** SC-41 (with the back-end fix in §3.4), V4-04, V4-05, V4-06, V4-10, V4-11, V4-14, V4-19.
- **Carried to UPMS:** V4-07 (§5.6), V4-12 (§3.6, §5.3), V4-13 (SSDS snapshots, §10.1), V4-15 (one enumeration, owned by UPMS).
- **Changed by the merge:**
  - SC-42 needs a uniform rule only in the strict profile (§8.2). In the default profile, scope members see the whole scope, so no hidden objection can arise within a project.
  - SC-43, V4-08, V4-09 and V4-17 dissolve with the cross-system boundary and with D-24.
  - V4-16 dissolves, because there is now one owner of the rules.

### 13.3 Candidate 5 disposition

| Candidate 5 section | Disposition in the next candidate |
| --- | --- |
| §1.2 product boundary | Add scientific-inquiry journeys alongside project memory |
| §1.4 domain | A D1 parent is now required; triggers 1 and 4 fire; §3–§6 here supply it |
| §2, §5.1, §5.4, §5.6, §5.8, §5.9 | Kept, with §4's vocabulary-versus-meaning distinction |
| §5.2, §5.3, §5.5, §5.7, §6.1 | Extended by §3–§4 |
| §6.2–§6.9 | Kept; publication (§6.8) simplified to sharing |
| §7 trust and access | Simplified by §8 |
| §8 runtime flow and egress | Moves out of the core; release records stay as provenance |
| §9.1–§9.6 commit and freshness | Kept; §9.3 gains the dependency contract of §6.1 |
| §9.7–§9.8 screening and processing | Extended by §6.2; retraining no longer driven by expiry |
| §10.1–§10.4 retrieval | Kept; archived records leave default proactive retrieval |
| §10.5 overview | Extended by §11; deadline machinery removed |
| §10.6 team memory | Kept as visibility tiers and lineage exclusion for blind review; publication becomes sharing |
| §11 accountability | Reduced to processing records and simple access logs |
| §12 retention and deletion | Replaced by §9 and honest deletion |
| §14.2 pilot defaults | All retention rows removed; security rows simplified |
| §16 slices | Re-planned (§14) |
| §18.2 decisions | D-6, D-8, D-12, D-13 and D-17 superseded or moot under D-24 and D-25; D-1 and D-2 simplified; others carried, to be confirmed at the next gate |

---

## 14. Sequencing

No implementation is authorized by this sequence.

1. **Review this proposal.** The owner confirms or changes §15. A reviewer outside the Claude family checks it before any manual is drafted.
2. **Draft the next manual candidate and a D1 formulation.** The D1 formulation, the theory–evidence memory semantics, is drawn from §3–§6 and SCIRE v0.4 §§4–7. The SCIRE repository gets a **front-end specification**, drawn from SCIRE v0.4 §§2, 4.4–4.5 and 8, with the re-review's repairs.
3. **Revised slices** (project memory first, D-30):
   - **Slice 1 — evidence memory.** Candidate 5 Slice 1a-core, simplified: capture, recall, coverage, checkpoints, coordination records, correction, explicit deletion, the overview projections.
   - **Slice 2 — theory basics.** Claims with the full modality set, questions, objections, evidence and inference relations with use history, decisions, standing projection, question pages. **The SCIRE minimal demonstration (SCIRE D-J) runs here**: one real inquiry, on UPMS, against a versioned notebook plus search.
   - **Slice 3 — checking.** Structured statements and vocabulary, the three consistency channels, retraction propagation, source assessments, retention recommendations.
   - **Slice 4 — scale.** Consolidated narratives, adapters, team policies, the strict profile.
4. **Experiments.** SCIRE's E1 (status and dissent loss), E2 (orientation) and E4 (elicitation cost) apply as written, run on UPMS. E3 (derivative flow) applies only to the strict profile. Add **E5 — standing faithfulness**: given real histories, does the standing projection and understanding section report status, dissent and retractions more faithfully, and at what reader cost, than an archive plus search? The owner sets error and cost limits before each study.

---

## 15. Decisions for the owner

| # | Decision | Status |
| --- | --- | --- |
| 1 | Are persons ranked as sources? | **Decided (D-32, superseding D-26 and D-31; confirmed after discussion):** no. Works are judged one by one; people are never scored, ranked or labeled by the system; only humans may judge people, signed and rebuttable; no track-record view (§6.4) |
| 2 | Is the strict profile needed in the first product? | **Decided (D-27):** no; added when a project with restricted data needs it |
| 3 | How far to simplify the rights model (`l r w c d m`) | **Decided (D-28):** four rights: read, write, curate, manage |
| 4 | Who confirms archival, and what counts as importance | **Decided (D-29):** any curator of the scope confirms. Importance as in §9.1 rule 5 is proposed |
| 5 | Is scientific inquiry now the first journey, or general project memory? | **Decided (D-30):** project memory first (Slice 1), science second (Slice 2) |
| 6 | Approach to judgment on judgment | **Open, technical; left to review.** Proposed: standing as a read-time projection plus explicit judgment bases (§6.1) |
| 7 | Status of candidate 5 | **Decided (D-23):** frozen as an input; its independent review is not requested |
| 8 | Anonymous and blinded review | **Decided (D-33):** open, single-blind and double-blind modes for critiques of works; personal attacks blocked and returned, never unmasked (§7.1) |
| 9 | Who chairs, and who holds sealed identities | **Decided (D-34):** the chair, a general discussion role; when the chair has a conflict with an anonymous critique, a conflict-free agent holds its seal (§7.1) |

---

## 16. Inspectability statement

- **Material realized record:**
  - events and observations;
  - claims with modality and conditions;
  - questions;
  - evidence and inference relations with use history;
  - objections with handling and resolution;
  - judgments, including comparability, source assessments and retention recommendations;
  - decisions with authority, exposure and dissent;
  - review obligations;
  - flags with cues;
  - archive and deletion records.
- **Intended readers:** researchers, PIs, reviewers, and agents acting for them; for project memory, the users and overseers of candidate 5 §1.4.
- **Routine questions:**
  - What do we believe about X, why, and how strongly?
  - What bears against it?
  - What changed since a given time?
  - What was retracted, and what depends on it?
  - Was this observation used to fit or to test?
  - Which sources does this rest on, and how independent are they?
  - What did we hold then?
  - What is recommended for archive, and why?
- **Proposed product inspectability surfaces, all beyond any accepted deliverable and binding only after the owner accepts them:**
  - question pages and the understanding section (§11);
  - the standing projection with its basis (§6.1);
  - fact-check results (§6.3);
  - the retraction impact view (§5.6);
  - the retention recommendation queue (§9).

---

## 17. Risks

| Risk | Consequence | Response |
| --- | --- | --- |
| Synthesized "understanding" resolves tension | Status inflation, dissent loss | Status-not-winners projection; narrative labeled; contradiction check against projections (§11) |
| Source ranking entrenches orthodoxy or turns political | Dissenters down-ranked; people judged instead of work | Track record only from independent later assessment; works judged one by one; people never scored (§6.4, D-32) |
| Memory misjudges a real person | Harm to someone's reputation, life or career | No person-level output; authorship never an assessment or ranking input; no characterization in synthesis (§6.4, D-32) |
| Anonymity used for attacks or fake consensus | Personal harm; one critic posing as many | Personal attacks blocked and returned; sealed identity counts one critic once (§7.1) |
| The chair's steering or summary tilts the discussion | Minority positions sidelined; status inflation | Steering is not deciding; summaries labeled synthesis, attributed and correctable, and must show live positions and unresolved objections (§7.1) |
| An agent seal-holder blocks legitimate harsh critique | Genuine review suppressed | Harsh criticism of work is never blocked; unclear cases are returned with a suggestion; appeal to a human with no conflict (§7.1) |
| A theory layer makes basic memory heavy | Project-memory users pay for science | Theory records are optional; Slice 1 needs none |
| Standing propagation is expensive or unstable | Slow or flickering status | Read-time projection with bounded traversal and explicit staleness, as candidate 5 §10.5.3 does for hubs |
| Unbounded growth with no time-based deletion | Storage and retrieval cost | Archive tier out of default retrieval; space-only deletion suggestions; explicit deletion |
| Removing D-6 lets restricted content spread | Disclosure in projects with sensitive data | Strict profile, opt-in (§8.2) |
| Vocabulary curation silently asserts scientific equivalence | False reconciliation | Curated concepts are indexing only; equivalence is a meaning-family claim (§4) |
| Coupling SCIRE's schedule to UPMS's slices | Later first demonstration | The demonstration moves to Slice 2; the slices are thinner after D-24 and D-25 |

---

## Appendix A. Independence and coverage

This proposal was written by the same model family, and the same model, as UPMS candidates 4.1 and 5, the SCIRE v0.3 and v0.4 texts and the SCIRE v0.4 re-review. It needs a reviewer from another family before any acceptance.

- **Read directly:**
  - UPMS candidate 5 §§1–10, 14.2 and 16–18, and parts of §12;
  - the opening of UPMS proposal v0.1;
  - SCIRE v0.4 and its re-review, in full.
- **SSDS:** reached through a read-only survey of the repository on branch `ssds-8.0-graph-native-architecture` at `0c18e65c`. Its two decisive points were checked directly: the manual is `status: accepted-current`, and its §33 non-goal is quoted above.
- **Not read:** UPMS candidate 5 §§11, 13 and 15 and most of §12.

No realized scientific results were produced or examined, and no variants were evaluated.
