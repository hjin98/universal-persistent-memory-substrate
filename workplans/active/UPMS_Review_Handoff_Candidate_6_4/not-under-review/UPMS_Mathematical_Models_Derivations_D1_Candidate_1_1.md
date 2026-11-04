# UPMS Mathematical Models and Derivations: D1 Formulation (Candidate 1.1)

**Kind:** Scientific Method Paper family (D1), first candidate, revision 1.1. It replaces candidate 1 for review, which stays unchanged; Appendix B maps the changes. It extends the UPMS Theory–Evidence Formulation, D1 candidate 1.4, and never redefines its meanings; rules there are cited as "TE F-n" and "TE Definition n".
**Date:** 3 November 2026
**Status:** PROPOSED D1 authority. Not reviewed, not accepted, not ratified. Its D3 realization is proposed in `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md` and in the hooks of core candidate 6.4; the front-end workflow is proposed in the SCIRE repository (`SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.2.md`).
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's direction (D-57 to D-62). No subagents were used. Revision 1.1 repairs the findings of a same-family review of the mathematics package (Claude Fable 5.1) and folds in owner decisions D-70 to D-78 ("Accept, draft it", 3 November 2026).
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer outside the Claude family, then ratification by the product owner (`AGENTS.md`).

---

## 0. Authority metadata

### 0.1 Inputs

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Theory–Evidence Formulation, D1 candidate 1.4 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_4.md`, SHA-256 `5e2b67f97b919d6612db6ed22bd6a3c7456b2be7141e4ef634bb3c2416afbb8f` | Parent meanings: claims, modality, inference steps and derivations (Definition 2.7: discharge and carried conditions), judgments, meaning links, standing, review obligations, the person guard |
| Owner decisions on mathematical support | `workplans/active/UPMS_Owner_Decisions_Math_2026-11-03.md`, SHA-256 `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | D-57 to D-62 |
| Owner decisions D-63 to D-70 | `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md`, SHA-256 `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | D-70 (discharged hypotheses; fidelity never in an inference basis) |
| Owner decisions D-71 to D-78 | `workplans/active/UPMS_Owner_Decisions_Math_Review_2026-11-03.md`, SHA-256 `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Folded in |
| Same-family review of the mathematics package (Claude Fable 5.1) | `workplans/active/UPMS_Mathematics_Package_Same_Family_Review.md`, SHA-256 `ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0` | NO-PASS; SM-1 to SM-4, FM-R01 to FM-R31; answered here and in the parent, core and annex |
| UPMS Mathematical Models and Derivations, D1 candidate 1 | `workplans/active/UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md`, SHA-256 `b50638641a506ae29861cec10fc76a647d6ed961d7345cff27dc0783168047a9` | Predecessor; changes in Appendix B |

Nothing here amends SSDS authority or the SCIRE proposals. No accepted D1 authority exists for UPMS, so there are no recorded tensions against accepted authority to carry.

### 0.2 What this document owns, and what it does not

| Owned here (D1) | Owned elsewhere |
| --- | --- |
| The meaning of mathematical expressions, symbols and their bindings, quantities and dimensions, mathematical models, mathematical statements, derivations and their assumptions, tool checks, formalization fidelity, inspection coverage, and the inspection brief | Records, storage, parsing, screening and projections: the UPMS mathematics annex (D3). The discussion, formalization workflow, tools and brief presentation: SCIRE. Executable models and their qualification: SSDS (D-21). What a numerical tolerance or error bound means: D2, when opened (§9) |
| | Theorems, formal proofs and Lean: the pure-mathematics package (D-57, D-58); this formulation prepares it (§8) |

---

## 1. Problem and intended use

### 1.1 The question

STEM projects reason with mathematical models: equations relating quantities, derived under assumptions and approximations, checked by hand, by computer algebra or numerically, and compared with observations. Today the memory holds such material as text. A reader cannot ask it reliably:
- which assumptions and approximations a result rests on;
- whether two papers' "ψ" or "T_c" denote the same thing;
- whether an equation is dimensionally consistent;
- which steps of a derivation have been checked, by what and by whom, and how far;
- what a retraction or correction of one step affects.

This formulation defines what the memory means by these things, so that a reader is not misled about the status of a mathematical result.

### 1.2 Failure

Failure means a reader is misled about a mathematical result's status, for example:
- shown a derived result without the approximation it needs;
- shown a computer-checked step as if the derivation were verified;
- shown a formal rendering as if it were the informal claim;
- shown an agent's summary as if a person had inspected the work.

### 1.3 Validity regime

- **In regime:** symbolic models and derivations in physics, chemistry, engineering, biology and applied mathematics; equations, inequalities, approximations and asymptotic orders; units and dimensions; checks by computer algebra, by numerical exploration and by people; agent-produced derivations and structured renderings.
- **Out of regime for this candidate:**
  - formal proof as a mathematical guarantee, and pure-mathematics theorems with Lean (§8);
  - the meaning of a numerical tolerance or error bound (§9);
  - any automatic "true" or "false";
  - any judgment of a person by the system (TE F-39).

---

## 2. Definitions

**Definition M.1 — Mathematical expression.** An expression `x` is:
- its exact **LaTeX source** `src(x)` (D-59), which is the record;
- a derived **parse** `π(x)` under a named parser version and macro context, with `structure ∈ {full, partial, text_only}`;
- **bindings** `β(x)` from its symbol occurrences, each named by its exact source range, to symbol definitions (Definition M.2);
- its **symbol context** `ctx(x)`, whose conventions apply to it.

Notation is presentation: two expressions with identical source can mean different things, and two with different source can mean the same.

**Definition M.2 — Symbol, binding and symbol context.**
- A *symbol definition* is a claim with modality `defined` (TE Definition 2.2) that introduces a symbol within a *symbol context*: a document, a model, a derivation or a scope.
- A *binding* links one occurrence to one definition. An occurrence with no binding is **unbound**.
- A context also records its **notational conventions**: summation convention, index placement, sign conventions, units system, and similar.
- Two occurrences denote the same thing only through the same binding, or through a meaning link between their definitions (TE Definition 2.12), and only under the same conventions or a meaning link between the contexts' conventions.
- A binding is an attributed interpretation by whoever made it (TE Definition 2.3) and can be objected to (TE Definition 2.5).

**Definition M.3 — Quantity kind and dimension.**
- A symbol definition may give the symbol's *quantity kind* (for example energy or temperature) and its *dimension* in a named system (for example SI base dimensions), or declare it dimensionless or of unknown dimension.
- Natural or rescaled unit systems are recorded as conventions of the context.
- An expression's dimension is derived from its bindings under the context's conventions; with any unbound or unknown-dimension symbol, it is **unknown**.

**Definition M.4 — Mathematical statement.** A mathematical statement is a structured rendering of a claim (TE Definition 2.2). Its kind is one of:
- `equation`, `inequality`, `identity`;
- `definition` (of a symbol or object);
- `assumption`;
- `approximation`, with its order, error term or limit, and its validity condition;
- `conditional`: hypotheses `H` imply conclusion `K`;
- `conjecture`.

Each kind carries its expressions, its bindings and the claim's modality. The kind never changes the modality: an equation stated as a hypothesis is `hypothesized`. Kind `definition` requires modality `defined`, and kind `assumption` requires `assumed` or `hypothesized`; every other kind may carry any modality.

**Definition M.5 — Mathematical model.** A model `𝔐 = (V, Θ, R, D, A, ρ, purpose)` has:
- variables `V` and parameters `Θ`, each with symbol, quantity kind and dimension;
- relations `R` (equations, inequalities and definitions);
- a domain `D` of admissible values;
- the assumptions `A` it is built on;
- a stated regime `ρ`, where it is meant to apply;
- a purpose.

A model is recorded as a symbol context of kind `model`: a set of claims of modality `defined` (the model as defined), with a model identity, version and regime; its variables, parameters and domain are symbol definitions in that context. **Defining a model asserts nothing about nature.** Its adequacy for a purpose and regime is a separate claim, assessed separately (TE F-28 keeps model adequacy apart from inferential validity). A model may reference an SSDS model package as its executable counterpart; UPMS never copies that package (D-21).

**Definition M.6 — Derivation step.** A derivation step is an inference step (TE Definition 2.7) of type `deductive` or `computational`. It carries:
- a **step rule** from a curated set, for example substitution, algebraic rearrangement, differentiation, integration, series expansion, limit, change of variables, applying an identity, applying an imported result, or approximation;
- the assumptions it **introduces**, such as a case split, a local hypothesis or a choice of branch;
- the assumptions it **discharges**, using a discharging rule: `implication_introduction`, `case_analysis` (all cases closed), `reductio`, `induction` or `existential_elimination`, each with the form its assessor checks (for `existential_elimination` and induction, that the eigenvariable does not occur free in the conclusion or open hypotheses);
- for an approximation, its order or error term and its validity condition.

**Definition M.7 — Derivation.** A derivation `Δ` is a finite, acyclic set of derivation steps from **premises** to a **result**; a step belongs to one derivation only (TE Definition 2.7). Its inputs are model relations and assumptions, introduced hypotheses, previously derived results and imported results. For a conclusion `κ` of `Δ`, the **carried conditions** are

```text
cond(Δ, κ) = hypotheses not discharged for κ (on every path to κ; D-72)
           ∪ approximation conditions on the paths to κ
           ∪ {model identity, version and regime} for each declared model used (D-71)
```

Only previously derived and imported results, and other asserted or found claims, are premises that need effective judgments (TE §6.1). The result is supported, at most, **under** `cond(Δ, κ)`. Its modality is the asserter's choice (`asserted`, `predicted` or `hypothesized`); "within model 𝔐" is a condition, so a derivation never asserts the model about nature (MP7).

**Definition M.8 — Tool check.** A tool check is an observation (TE Definition 2.1) whose payload is a tool's output on stated inputs. It records:
- the tool, its version and environment;
- the exact inputs, as translated for the tool;
- the outcome: `passed`, `failed`, `inconclusive` or `incomplete`;
- what the tool did **not** check (unchecked side conditions, timeouts, numerical spot values only).

Its origin is `external-system run` when the tool is a governed external system, and otherwise `project-recorded` (TE Definition 2.9). A tool is registered by an operator act, shown on every check (D-77). Kinds of check:
- **symbolic:** computer algebra checks a step or identity;
- **numerical exploration:** evaluation at sample points;
- **formal:** a proof assistant checks a formalization; this kind belongs to the pure-mathematics package (§8).

**Definition M.9 — Formalization and fidelity.**
- A *rendering* of a claim is any structured, symbolic or tool-input form of it: a mathematical statement, a computer-algebra input, or a formal statement.
- A *formalization link* is a meaning link (TE Definition 2.12) from the claim to its rendering.
- A *fidelity judgment* is an attributed judgment of that link, with result `faithful`, `diverges(at, how)` or `unknown`.
- A rendering bears on the claim only through a fidelity judgment that is effective under TE Definition 6.0.
- A fidelity judgment by an agent principal, or by the rendering's author, is labeled as such. It counts as a judgment, but it never takes the rendering out of the brief's mandatory category of renderings without an independent human fidelity judgment (D-73).

**Definition M.10 — Inspection.** An *inspection judgment* is an attributed act by a human inspector, and only by a human: the memory refuses one from an agent principal (D-73). It records:
- the **scope** inspected: which steps, statements, renderings or tool checks;
- the **depth**: `spot`, `step-by-step` or `full` (every member of the scope examined step by step; a label that decides status only in FM-17);
- the **outcome**: `no defect found`, `defects found` (each a linked objection) or `inconclusive`.

Being shown work, or a summary of it, is **exposure**, not inspection (TE Definition 2.10; core §8.2).

**Definition M.11 — Designated verifier.** A *designated verifier* for a piece of work is a person named as such by an attributed act under the project's rule (an authority basis, as for decisions; TE Definition 2.10). A designation names its subject (a person, never an agent principal; D-75), the work or scope it covers and its effective interval. A designation of the work's own author, or one the designee made, is labeled. **The memory records the designation; it never computes, ranks or infers anyone's qualification** (TE F-20, F-39, D-32).

**Definition M.12 — Inspection brief.** An inspection brief is a derived view prepared for a human inspector, over one derivation revision, or over one result claim revision and every derivation to it. It consists of:
- a **mandatory part**, a projection over exact records (§6);
- an optional **ranked synthesis**: what matters most, what changed, and where the producer is uncertain and why.

---

## 3. Principles (normative)

- **MP1 — Notation is not meaning.** Identity of meaning comes from bindings and meaning links, never from matching notation.
- **MP2 — Conditions travel with results.** A derived result is never shown without its conditions: undischarged assumptions, approximations with their order and validity, and model regimes.
- **MP3 — Checks are relative and partial.** Every tool check is relative to its tool, version, inputs and what it did not check. No tool check is a verdict.
- **MP4 — Three statuses, never merged.** The mechanical check, fidelity and inspection coverage are separate, and none implies another.
- **MP5 — Agents propose; people inspect.** Agent-produced derivations and renderings are attributed proposals. Their standing comes only through judgments, including fidelity and inspection judgments (D-61). Only humans inspect, and an agent's or author's own judgment of its work is always labeled (D-73).
- **MP6 — Attention is managed, not substituted.** A brief may rank and summarize; it never omits a mandatory item and never counts as inspection.
- **MP7 — Model adequacy is not derivation validity.** A valid derivation from an inadequate model is still inadequate for its purpose, and an adequate model does not make a derivation valid.

---

## 4. Expressions, symbols and dimensions

**FM-1 — Binding before comparison.** Two expressions are compared as mathematics only through their bindings. An unbound occurrence makes any comparison involving it **unknown**, never "same" or "different". Similar notation across contexts yields at most an unresolved possible match (TE Definition 2.12). Expressions in contexts with different conventions, and no meaning link between those conventions, raise the cue "conventions differ".

**FM-2 — Partial structure is honest.** When LaTeX cannot be parsed unambiguously (an overloaded macro, a juxtaposition that could be multiplication or application, an implicit index convention), the parse is `partial`, and the ambiguous part keeps its source text. A guessed reading is an interpretation by its parser (TE Definition 2.3), not a fact.

**FM-3 — Dimensional consistency is a cue.** If, under its bindings and conventions, an equation's sides, a sum's terms, or a function's argument (for example of `exp` or `log`) have dimensions that differ or are not dimensionless where required, the memory raises a **dimensional inconsistency** cue. It does not refute the claim: the binding, the convention or the claim may be wrong. With unknown dimensions, the check reports "not covered".

**FM-4 — Conventions are part of the context.** A change of convention, such as a sign, a unit system or index placement, is a definition change (TE F-27, F-32). It creates review obligations on the expressions, derivations and results that used the context, followed through each expression's context (Definition M.1).

---

## 5. Derivations

**FM-5 — Conditions propagate.** For a derivation `Δ` with result `κ`, any route to `κ` through `Δ` is at most `supported-under(cond(Δ, κ))` (Definition M.7; TE §6.1 carried conditions). A later route that uses `κ` as a premise inherits `cond(Δ)`, subject to TE §6.1's compatibility rule. Dropping a condition is a fidelity defect in the rendering that dropped it.

**FM-6 — Approximations keep their order.** An approximation step records its order or error term (for example `O(ε²)`) and its validity condition (for example `ε ≪ 1`, `T ≪ T_F`). A result derived through it is never shown without them. Combining approximations of different orders states the combined order, or "order unknown".

**FM-7 — Imported results bring their hypotheses.** Applying an imported result, whether a textbook identity, a theorem or a previously derived result, is a step whose premises include that result's hypotheses or conditions. A hypothesis not shown to hold in the step's context is a carried condition.

**FM-8 — Steps are assessed one by one.** A derivation's validity is the validity of its steps, each assessed as an inference step (TE Definition 2.8). A derivation is not assessed-sound unless every step on the route to its result is assessed-sound, with TE §6.1's statuses applying per step. An objection or a negative assessment on one step challenges or breaks every route that passes through it.

**FM-9 — Errors propagate as obligations.** A correction or retraction of a step, premise, model relation, binding or convention creates review obligations on every dependent derivation and result (TE F-32). Nothing becomes true or false automatically.

**FM-10 — Equivalent models and definitions are meaning links.** Two models, or two definitions of one object, are equivalent only under an attributed meaning link `equivalent-under(c)`, which is itself assessable and open to objection. Equivalence never follows from shared names.

---

## 6. Checks, fidelity, inspection and the brief

### 6.1 Tool checks

**FM-11 — A tool check is evidence about a step, not a judgment.** A passed symbolic check is evidence bearing on an inference assessment of the step it checked. The assessment stays an attributed act. A tool check is about its **inputs**: if the tool input renders the step unfaithfully, the check says nothing about the step (FM-14). An effective `diverges` fidelity judgment on the tool input's rendering makes the check inapplicable as evidence for the step and creates review obligations on every assessment that cited it (TE F-32; D-74). The divergence is never cited in an assessment's basis (D-70).

**FM-12 — Numerical exploration suggests.** Agreement at sample points, plots and quick simulations on local hardware (D-60) are observations. An agreement is recorded as an evidence relation of kind `consistent-with(T)` or `bears-on(T), unassessed` (TE Definition 5.1), with a use-history entry describing its actual use, normally `model-check` or `not-applicable`. Until D2 is accepted (§9), no numerical check takes the use `tested-pre-specified` or the kinds `entails` or `prediction-succeeded`, so it never confirms a symbolic result. A disagreement is recorded as "values differ", with both raw values and the environment. Whether it is a counterexample is the claim of whoever asserts it as an objection.

**FM-13 — Incomplete is not passed.** A check with timeouts, unchecked side conditions (branch cuts, division by possibly-zero terms, convergence, interchange of limits) or partial coverage is `incomplete`, and lists what it left out.

### 6.2 Fidelity

**FM-14 — Renderings need fidelity.** A mathematical statement, tool input or formal statement bears on the claim it renders only through an effective fidelity judgment (Definition M.9). An agent's rendering without one is an interpretation, unconfirmed (TE Definition 2.3). A tool check of an unassessed rendering is shown as "checked: rendering fidelity not assessed". A rendering judged only by an agent, or only by its author, is shown as "fidelity: agent-judged only" or "fidelity: author-judged only" (D-73).

**FM-15 — Divergence is located.** A `diverges` fidelity result names where (a symbol, a hypothesis, a quantifier, a condition, a sign) and how. Each divergence is an objection to the rendering, so it travels (TE F-7), and it challenges every route whose effective assessment cites a tool check of that rendering (TE §6.1).

### 6.3 Inspection

**FM-16 — Coverage is explicit.** Inspection is recorded with its scope and depth. A result's standing report shows, separately:
- which steps and renderings were inspected, and to what depth;
- which were checked only by tools;
- which were neither.

"Inspected" without a scope is not recordable.

**FM-17 — Full verification of a derivation.** A derivation is shown as **verified in full** only when every step on the route to its result, every rendering it relies on and every tool check it cites lies within one or more **effective** inspection judgments of depth `full`, outcome `no defect found`, by people holding a designation for that work or its scope whose interval covers the inspection, and no objection to any of them is unresolved. Every other combination is shown as its parts, never rounded up. It is a property of the derivation, not of the result: it always reads "derivation verified in full; premises: ⟨their status⟩; conditions: ⟨cond(Δ, κ)⟩". A revoked designation changes nothing "as held then", and removes the status from current reads unless the project's rule says otherwise; the report says which applies.

**FM-18 — The verifier is designated, not assessed.** Whether a person counts as a designated verifier comes only from an attributed designation under the project's rule. The memory never infers it from track record, authorship or any attribute of the person (TE F-39, F-41).

### 6.4 The inspection brief

**FM-19 — Mandatory part.** Every brief contains, as an exact projection paginated with counts:
- steps not assessed-sound, and steps checked only by tools;
- renderings without an effective fidelity judgment by a human other than their author (agent-judged and author-judged ones are listed as such), and every located divergence;
- carried conditions: hypotheses not discharged for the result and declared model relations; every discharged hypothesis with the step that discharged it; and approximations with their order and validity;
- failed, inconclusive and incomplete tool checks, with what they left out;
- unbound symbols and dimensional cues;
- unresolved objections in the work's applicable set (TE F-6);
- same-family checks, labeled as such (D-78);
- a coverage line, for example "inspected: 7 of 23 steps step-by-step; 12 tool-checked only; 4 neither".

**FM-20 — Objective signals lead.** The ranked synthesis orders items by recorded, checkable signals first (the categories of FM-19), then by the producer's stated uncertainty. The order is itself the producer's claim, labeled synthesis; no ordinal or numeric confidence is stored on any record. A producer's uncertainty is a claim with modality `asserted`, attributed to its producer and given with its reasons. It is never a calibrated probability (TE §1.3) and never evidence (core §5.3: model confidence is not evidence).

**FM-21 — Rank, never omit.** The synthesis may put items first and summarize the rest, but every mandatory item stays reachable from the brief with its count. Showing a brief records exposure to it. Only an inspection judgment (Definition M.10) records inspection.

---

## 7. Standing

The standing report of a claim with a mathematical rendering or derivation (TE Definition 6.1) adds:
- its carried conditions and discharges (FM-5, FM-6; TE §6.1);
- the status of each derivation route, per step (FM-8);
- tool checks, with outcome and coverage (FM-11 to FM-13);
- fidelity of each rendering (FM-14, FM-15);
- inspection coverage, and whether each derivation is verified in full (FM-16, FM-17);
- model adequacy claims and their assessments, kept apart from derivation validity (MP7).

No line merges two of these, and none sets another (MP4).

---

## 8. Preparing the pure-mathematics package

This formulation does not cover theorems, formal proofs or Lean (D-57, D-58). The package that will:
- reuses Definitions M.8 to M.12 and FM-11 to FM-21 unchanged;
- adds a `formal` tool check: a check relative to the Lean toolchain version, the mathlib commit and the axioms used, in which any unfinished `sorry` makes the check `incomplete`;
- adds proof statuses as further coverage, never as truth;
- adds formal statements as renderings whose fidelity is judged as in FM-14.

A formal check is relative to its system, version, library and axioms. It is never "true".

---

## 9. D1 → D2 hand-off

D2 is not opened. Two items are handed over:

| Item | D1 constraint handed to D2 | Until D2 is accepted |
| --- | --- | --- |
| Numerical agreement as evidence (FM-12) | A stated tolerance needs its error model: floating-point, discretization and sampling error, and the regime | Numerical exploration records `suggested` only; no numerical check is offered as confirming |
| Numerical disagreement as a counterexample (FM-12) | A "values differ" record is a counterexample only under a stated tolerance and error model | Both raw values and the environment are recorded; the asserter's objection carries the claim |
| Numerical error bounds of approximations (FM-6) | A numeric bound, as opposed to an asymptotic order, needs its derivation and assumptions | Orders are recorded symbolically; numeric bounds stay text with `structure: partial` |

---

## 10. Hooks in the architecture

Core candidate 6.4 carries all seven hooks the mathematics annex lists (its §M.0): judgment kinds `fidelity` and `inspection` (H1); a notation field on spans (H2); step rules, introduced and discharged hypotheses and approximations on inference steps (H3); mathematical statement kinds, in the checking annex (H4); verifier designations (H5); the `renders` link (H6); and the annex's four record kinds (H7). The parent formulation carries the rules this text needs: discharge and carried conditions (TE Definition 2.7, §6.1), objections on renderings, bindings and tool checks (TE Definition 2.5), and divergence as a cause of review (TE F-32).

---

## 11. External adequacy and falsification

### 11.1 What would show this formulation adequate

On realistic project histories (a derivation in a paper draft, a model revised over months, an agent's re-derivation), readers using the memory answer the routine questions of §12 correctly and faster than with notebooks and search, and are not misled by any trajectory in §11.2. The cheapest first evidence is the deterministic stress cases, run on two or three real derivations from a project draft, before any seeded-error study. This is to be measured, with owner-set limits, in the SCIRE evaluation (E1, E5).

### 11.2 Stress cases that must not mislead

1. The same `ψ` means a wave function in one paper and a stream function in another: no comparison is made without bindings.
2. An equation adds an energy to a temperature: a dimensional cue, not a refutation.
3. A result derived under `ε ≪ 1` is cited later without the condition: the condition is still shown, and the citing rendering's fidelity is marked as diverging.
4. A case split introduces `x > 0`, and it is never discharged: the result shows `supported-under(x > 0)`. A case split whose cases are all closed discharges it.
5. A computer-algebra check passes on an input that has the wrong sign relative to the paper: shown as "checked: rendering fidelity not assessed" until a fidelity judgment finds the divergence, after which the step's route goes under review (FM-11).
6. Agreement at ten random points is presented as confirmation: recorded as `suggested`.
7. A timeout leaves branch cuts unchecked: `incomplete`, with the branch cuts listed.
8. An agent's brief puts a minor step first and summarizes the unchecked sign-convention change: the mandatory part still lists the change, with its count.
9. A person opens the brief and approves: exposure is recorded, and no inspection judgment exists until they record one with its scope.
10. A respected senior author's derivation is shown as verified because of who wrote it: impossible. Only designated full inspection with no open objection gives that status (FM-17, FM-18).
11. A model is valid but used outside its regime: adequacy is shown apart from derivation validity, with the regime.
12. An agent judges its own renderings faithful: the brief still lists them as "fidelity: agent-judged only" (D-73).
13. An agent records an inspection judgment: refused (D-73).
14. A result derived from a model's relations under one open assumption: sound under "within the model, assuming h", with both listed (D-71).

### 11.3 Assumptions and limitations

- **A-M1:** inspection and fidelity judgments are honest reports of what their authors examined. The memory records them; it cannot verify them.
- **A-M2:** the project's designation rule, not the memory, carries a verifier's qualification (D-32, FM-18).
- **Limitation:** full inspection by a designated verifier (D-61's robust route) is only as robust as that person's work. The status says who inspected what, not that the work is correct.

### 11.4 What would falsify or reopen it

- A trajectory in which a reader, following FM-1 to FM-21, is misled as in §1.2.
- Evidence that inspection or fidelity judgments are routinely not honest reports (A-M1).
- A need to state numerical tolerance as evidence (reopens §9 into D2).
- A front-end workflow that cannot present the mandatory part at the scale real derivations reach: this would reopen FM-19, not justify omission.

---

## 12. Scientific inspectability (O1)

**Material realized record:**
- expressions with source, parse and bindings;
- symbol contexts and conventions;
- models and their versions;
- derivation steps with rules, assumptions and approximations;
- tool checks with inputs, environment and coverage;
- fidelity and inspection judgments;
- designations of verifiers;
- briefs shown, as exposure.

**Intended readers:** project members, reviewers and designated verifiers; agents working on the project.

**Routine questions:**
- What does this symbol mean here?
- Under what assumptions and approximations does this result hold?
- Which steps were checked by a tool, which by a person, how far, and which by neither?
- Does this rendering say what the claim says?
- What does a correction of this step affect?
- Is this derivation verified in full, and if not, what is missing?

**Product inspectability surfaces**, all **beyond the requested deliverable** and binding only after the owner accepts them:
- the derivation view, with conditions, per-step status and coverage;
- the symbol view;
- the inspection brief;
- the coverage view of a result.

Technical acceptance of this formulation does not accept them. No realized scientific results were produced or reviewed in preparing it.

---

## 13. Findings raised while drafting

| ID | Finding | Disposition here |
| --- | --- | --- |
| M-F1 | D-61's "qualified human verifier" could be read as the memory judging a person's qualification, which D-32 forbids | Definition M.11 and FM-18: designation by an attributed act under the project's rule; the memory never assesses a person |
| M-F2 | An agent's stated confidence, presented to direct attention (D-61), could become an implicit calibrated probability or be treated as evidence | FM-20: an attributed claim with reasons, ranked after objective signals; never evidence |
| M-F3 | A brief that summarizes for efficiency could omit the one item that matters, and showing it could be mistaken for inspection | FM-19, FM-21 |
| M-F4 | Candidate 6.2 lacks judgment kinds for fidelity and inspection, a notation field on spans, step rules and assumptions, and math statement kinds | §10; the mathematics annex lists them for the next core revision |
| M-F5 | TE Definition 2.7's step type `computational` covers both a computer-algebra step and a numerical computation; their warrants differ (FM-11, FM-12) | Distinguished here by the tool-check kind; TE Definition 2.7 is unchanged |
| M-F6 | (Revision 1.1; review SM-1 to SM-4.) A divergent rendering left a route sound; no derivation from a model could be sound; discharge was not path-scoped; agents could inspect or clear their own fidelity | FM-11, Definition M.7, M.6, M.9, M.10, FM-19; parent rules; D-71 to D-74 |
| M-F7 | (1.1; FM-R01 to FM-R11.) `suggested` misused and a test escape; designation scope and effectiveness; result versus derivation; conventions; disagreement; assumptions; hook list; `faithful_under`; kinds and modality; brief subject; stored confidence | FM-12, FM-17, M.11, M.1, M.2, FM-1, §9, §11.3, §10, M.9, M.4, M.12, FM-20 |

---

## 14. Open challenges

1. Whether the curated step-rule set (Definition M.6) can be kept small and still cover real derivations: to be tested on project histories.
2. How far dimensional analysis can go with natural or rescaled units (Definition M.3): conventions may make many checks "not covered".
3. Whether computer-algebra tools need a qualification record of their own, as SSDS results have, before a passed check is offered as evidence.
4. The scale at which the brief's mandatory part stays usable (§11.3).

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the same model family and model as every UPMS and SCIRE text it extends. A reviewer outside the Claude family is required before acceptance.
- **Read directly:** UPMS D1 candidate 1.2 §§2–7 and 9 (1.4 for revision 1.1); candidate 6.2 core §§5.1–5.5 and 9.14 (6.4 hooks for revision 1.1); the owner's decisions D-57 to D-62; SSDS's derivation module header (to confirm that SSDS's "derivation" means derived state, not mathematical derivation).
- **Not read:** SCIRE v0.4 beyond what the UPMS texts carry; SSDS model-package definitions; any external literature on proof assistants, computer algebra or formalization.
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated.
- **Choices:** the step-rule examples and the discharging rules, the depth levels (`spot`, `step-by-step`, `full`), the tool-check outcomes and the brief's mandatory categories are the author's proposed defaults. D-73 fixes who may inspect; nothing else here is fixed by owner decision.
- **Revision 1.1:** written by the same author in answer to a same-family review by Claude Fable 5.1; the repairs are unreviewed. The natural-deduction conditions on discharging rules follow standard logic texts from the author's and reviewer's knowledge, uncited.

---

## Appendix B. Change map, candidate 1 → candidate 1.1

| Where | Change | Reason |
| --- | --- | --- |
| Front matter, §0.1 | Revision 1.1; parent 1.4 with its hash; decision records and the review as inputs; 6.2 core row removed | FM-R07 |
| M.1, M.2, FM-1, FM-4 | Bindings by source range; symbol context on every expression; conventions in comparison and impact; bindings as objectionable interpretations | FM-R04, FM-R19, FM-R13 |
| M.4 | Kinds `definition` and `assumption` restricted by modality | FM-R09 |
| M.5 | A model is a symbol context of kind `model` | Simplicity |
| M.6 | Discharging rules with their side conditions | SM-3 |
| M.7, FM-5, FM-7 | Carried conditions per conclusion; premises that need judgments; result modality | SM-2, SM-3; D-71, D-72 |
| M.8 | Tool registration | D-77 |
| M.9, M.10, MP5, FM-14 | `faithful_under` dropped; agent and author fidelity labeled; only humans inspect; depth `full` | SM-4; D-73; simplicity |
| M.11 | Designation subject, scope, interval and labels | FM-R02; D-75 |
| M.12 | The brief's subject | FM-R10 |
| FM-11, FM-15 | Divergence makes the check inapplicable and challenges the route | SM-1; D-74 |
| FM-12, §9 | Numerical exploration as `consistent-with` or `bears-on`; no test escape; "values differ" | FM-R01, FM-R05 |
| FM-17 | Effective, designated, full inspection; a property of the derivation; revocation | FM-R02, FM-R03 |
| FM-19, FM-20 | Discharges and carried conditions listed; agent and author fidelity listed; same-family checks labeled; no stored confidence | SM-3, SM-4, FM-R11; D-78 |
| §7, §10, §11 | Standing items; all seven hooks; assumptions and limitations; stress cases 12 to 14; cheapest first evidence | FM-R06, FM-R07 |

No other text changed.
