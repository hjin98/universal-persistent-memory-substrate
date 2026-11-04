# UPMS Architecture Manual, Review Candidate 6.3: Mathematics Annex (proposed addition)

3 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** proposed D3 architecture; not accepted-current. **A proposed Slice 3 addition to candidate 6.3, reviewed separately from its Gate 0 package** (D-56). The 6.3 core (`UPMS_Architecture_Manual_Review_Candidate_6_3.md`, SHA-256 `e6c02b0a60eead112b2a0ef78b07ff849e0006c71df25e60aeefa24686590a44`) lists this annex and absorbs its hooks (§M.0). It replaces the 6.2 mathematics annex, which stays unchanged; only the title, this status, the D1 parent, §M.0, the slice row, open item 5 and the coverage note changed. Section numbers like "§9.9" are the core's.

**D1 parent:** UPMS Mathematical Models and Derivations, D1 candidate 1 (`UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md`), cited as "M Definition M.n" and "M FM-n"; with the Theory–Evidence Formulation as its parent, now candidate 1.3 (whose Definition 2.7 and §6.1 carry D-70's rule for discharged hypotheses). The mathematics D1 text still names 1.2 and is to be updated at its next revision; no meaning it relies on changed. **Owner decisions:** D-57 to D-62 (`UPMS_Owner_Decisions_Math_2026-11-03.md`). **Front end:** SCIRE, through `SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.1.md` in the SCIRE repository.

**Mathematics is recorded and related here; it is checked and computed elsewhere.** UPMS stores expressions, symbols, models, derivations, tool checks, fidelity and inspection, and computes their standing and the brief's mandatory part. Tools run in the front end's environment (D-60). **Fixed (proposed).**

---

## M.0 Hooks in the core

Core 6.3 absorbs every hook. The same-family review of 6.2 checked H1 to H6 against the core (its §7): H1, H2, H5 and H6 were additive; H3 needed a D1 rule, which owner decision D-70 supplied; and the author then found H7.

| Hook | Where in core 6.3 | What it does |
| --- | --- | --- |
| H1 | §5.3 Judgment `kind` | Adds `fidelity` (target: a `renders` link, M Definition M.9) and `inspection` (target: an inspection scope record). Both are separate statuses: route status never reads them, and an inference assessment's basis never cites them (D-70), so TE Definition 6.0 condition 5 is unchanged |
| H2 | §5.1 Event `spans` | Optional `notation: latex` per span, with the exact source range (D-59) |
| H3 | §5.5 inference-step fields | Optional `step_rule`, `introduces[]`, `discharges[]`, `approximation{order, validity}` (M Definition M.6). A hypothesis discharged within a derivation is not a premise of the conclusion, so a derivation that discharges its hypotheses can be sound (TE Definition 2.7, §6.1; D-70) |
| H4 | Checking annex §5.7.1 Statement `kind` | Adds `equation`, `inequality`, `identity`, `definition`, `assumption`, `approximation`, `conditional`, `conjecture`, with `expressions[]` (M Definition M.4) |
| H5 | §5.4 Controls; §4.3 `designate_verifier` | Verifier designations: an attributed control with an authority basis that references the project's rule, stored and never evaluated (M Definition M.11, D-32) |
| H6 | §5.5 Meaning family | The relation `renders` (claim → rendering), assessed only by `fidelity` judgments |
| H7 | §5 opening | The records of §M.1 (expressions, symbol contexts, models, derivations, inspection scopes) are canonical record kinds with the common fields and no assessment. The 6.2 core's §5 listed every kind of canonical state and did not allow them; the author found this while absorbing the hooks |

---

## M.1 Records

```text
MathExpression {
  span_ref                        // exact LaTeX source in an event (H2); the record
  macro_context_ref?              // the document's macro definitions, as captured
  parse_ref?, parser_version, structure: full | partial | text_only
  bindings[]: {occurrence, symbol_definition_ref | unbound}
}

SymbolContext {
  kind: document | model | derivation | scope
  conventions: {units_system, signs, index_placement, summation, ...}   // each a defined claim
  parent_context?
}

SymbolDefinition = Claim (modality defined) with {
  symbol_latex, context_ref, quantity_kind?, dimension? | dimensionless | unknown
}

Model {
  model_id, version, defining_claims[]          // modality defined (M Definition M.5)
  variables[], parameters[], relations[], domain, assumptions[], regime, purpose
  ssds_package_ref?                             // reference only (D-21)
}

Derivation {
  derivation_id, result_claim_ref, steps[]      // inference steps with H3 fields
  premises[]                                    // model relations, assumptions, results, imports
  // cond(Δ) is derived (§M.5), never stored
}

ToolCheck = Event (observation) with {
  tool_ref                                      // registered tool (§M.6)
  tool_version, environment_identity            // hash of the environment description
  input_ref, rendering_link_ref?                // exact tool input; the renders link it realizes
  output_ref, outcome: passed | failed | inconclusive | incomplete
  unchecked[]                                   // side conditions, timeouts, sample-only coverage
  kind: symbolic | numerical_exploration | formal     // formal: pure-mathematics package
}

InspectionScope { members[]: exact revisions of steps, renderings, tool checks, statements }
// Inspection = Judgment kind inspection (H1) on an InspectionScope, with
//   depth: spot | step_by_step | end_to_end, outcome, objection_refs[]
// Fidelity   = Judgment kind fidelity  (H1) on a renders link, with
//   result: faithful | faithful_under(c) | diverges{at, how} | unknown
```

All of these are ordinary records, with home scope, owner, attribution, restriction tags and lifecycle as in §5 and §7. An agent's binding, rendering or derivation is an interpretation or attributed proposal (D1 TE Definition 2.3) until it is confirmed, adopted or assessed.

---

## M.2 Parsing

A parser worker, one of the core's processing workers, derives `parse_ref` from the exact source under a named parser version and the captured macro context. It writes a processing record (§5.4), and its output is replayable.

What stays `partial`, with the ambiguous part kept as source text (M FM-2):
- overloaded macros;
- juxtaposition that could be multiplication or application;
- implicit index conventions;
- notation the parser does not know.

A parse never changes the source. Re-parsing under a new parser version is a new derivation of the parse, and comparisons cite the parse version they used.

---

## M.3 Bindings, conventions and impact

- **Bindings** are records with authors. An agent's proposed binding is an interpretation until confirmed or adopted. Comparisons use only effective bindings (M FM-1).
- **A change to a symbol definition, a binding or a convention** is a definition change. It advances the scope epoch and runs impact traversal (§9.11), which follows bindings, `renders` links and derivation premises. It creates review obligations on dependent steps, derivations, renderings and results (M FM-4, FM-9).
- **Two contexts' symbols** are the same only through a meaning link of kind `identical` or `equivalent_under(c)` (D1 TE Definition 2.12, M FM-10).

---

## M.4 Dimensional screening

A deterministic screening channel, added to the checking annex's §9.7, evaluates dimensions under effective bindings and the context's conventions. It raises:
- **dimensional inconsistency:** the sides of an equation, the terms of a sum, or the argument of a transcendental function disagree;
- **not covered:** some dimension is unknown or unbound.

It is a cue, never a refutation, and the absence of a cue certifies nothing (§9.7). It is replayable at a pinned vocabulary and convention version.

---

## M.5 Standing of derivations

The standing projection (§9.9) is extended, computed at read like the rest of the report.

**Per step:** route status, as for any inference step (D1 TE §6.1; M FM-8).

**For each derivation `Δ`:**
- **Conditions:** `cond(Δ)` derived from undischarged assumptions, approximation conditions with their orders, and the regimes of the models used (M Definition M.7). The result's routes through `Δ` are at most `supported_under(cond(Δ))`.
- **Coverage:** for each step, rendering and cited tool check on the route to the result, one of:
  - inspected, at its depth;
  - tool-checked only;
  - neither (M FM-16).
- **Verified end-to-end:** true only if every member of that route lies within one or more `end_to_end` inspections by designated verifiers, with outcome `no defect found`, and no unresolved objection applies (M FM-17). Otherwise the report shows the parts.

**For each rendering:** its effective fidelity judgment, or "fidelity not assessed" (M FM-14).

**For each tool check:** its outcome, what it left unchecked, and, if its `renders` link has no effective fidelity judgment, "checked: rendering fidelity not assessed".

**For the models used:** adequacy claims and their assessments, shown apart from derivation validity (M MP7).

Caching and history follow §9.9: positions, ruleset and projection versions are pinned, and negative information invalidates caches.

---

## M.6 Tools and tool checks

- **Registry.** Tools are registered by an operator act (D-52) with name, version and environment description. A tool reference names a registry entry.
- **Recording path.** Tool checks reach UPMS only through the front end's attributed recording path. The invoker is recorded, with the tool as the method (§5.1). A tool never writes to UPMS directly.
- **Tags.** A tool check's input, output and artifacts carry the union of their inputs' restriction tags, because no writer chose them (§7.4). Sending content to a tool that runs outside the deployment is processing and egress (§8.5): processor eligibility applies. Tools on local hardware are inside the deployment boundary when the deployment profile says so.
- **Evidence semantics.**
  - A symbolic `passed` is evidence bearing on an inference assessment of the checked step, through an evidence relation whose conditioning model is the `renders` link (M FM-11).
  - Numerical exploration records use `suggested` (M FM-12).
  - `incomplete` lists what it left unchecked (M FM-13).

---

## M.7 The inspection brief

- **Mandatory part.** A projection over exact records: the M FM-19 list, paginated with exact counts and a coverage line. It is built by the projection service like a hub, and its lines are current at read or marked stale (§10.5).
- **Ranked synthesis.** Supplied by the front end or an agent and labeled as synthesis (§5.2 `synthesis`). Uncertainty statements are claims attributed to their producer, with modality `asserted` (M FM-20).
- **Exposure, not inspection.** Release of a brief creates release records, which are exposure (§8.2). It never creates an inspection judgment (M FM-21).
- **Ordering.** The front end may order the synthesis as it likes. The mandatory part's membership is fixed by the projection, and a front end may add items to it but never remove them (§4.4: widen, never narrow).

---

## M.8 Deletion and retention

- **Parses, dimensional cues, coverage computations and brief projections** are UPMS-derived representations. They are purged or regenerated when an input is deleted (§12.3).
- **Bindings, renderings, derivation steps, fidelity and inspection judgments and designations** are authored records. They follow §12.3 for authored descendants, and deleting a step or rendering that others relied on leaves a marker (SC-61).
- **Tool artifacts** are records like any other. They are retained by importance, never by time (D-25).

---

## M.9 Invariants and tests

**Invariants**

| ID | Invariant | Slice |
| --- | --- | --- |
| MA1 | Mathematical comparison uses only effective bindings; unbound occurrences make a comparison unknown | 3 |
| MA2 | A derived result's conditions are always shown with it; the result's routes through a derivation are at most supported under those conditions | 3 |
| MA3 | A tool check is evidence about its inputs only; without an effective fidelity judgment on its `renders` link it is shown as "rendering fidelity not assessed"; numerical exploration never confirms; incomplete checks list what they left unchecked | 3 |
| MA4 | Check, fidelity and inspection coverage are separate lines; "verified end-to-end" holds only under M FM-17 | 3 |
| MA5 | A brief's mandatory part is an exact projection that no front end narrows; showing a brief is exposure, never inspection | 3 |
| MA6 | Verifier designation is an attributed control under the project's rule; no API computes a person's qualification | 3 |

**Tests**

| Case | Trajectory and required discriminator |
| --- | --- |
| TM01 | `ψ` bound to a wave function in one context and a stream function in another: no comparison; an unbound third occurrence gives "unknown" |
| TM02 | An equation adds an energy to a temperature: a dimensional cue, the claim not refuted; with one unbound symbol, "not covered" |
| TM03 | A result derived under `ε ≪ 1` at `O(ε²)` is cited later: the condition and order appear in the citing claim's standing; a rendering that drops them is marked diverging once a fidelity judgment records it |
| TM04 | A case split introduces `x > 0` and never discharges it: the result is shown `supported_under(x > 0)` |
| TM05 | A computer-algebra check passes on an input with the opposite sign: shown as "checked: rendering fidelity not assessed" until a fidelity judgment locates the divergence; the divergence then travels as an objection |
| TM06 | Agreement at ten sample points: recorded with use `suggested`, never offered as confirming; one disagreeing point produces a counterexample cue |
| TM07 | A check times out on branch cuts: `incomplete`, listing the branch cuts |
| TM08 | A sign-convention change between drafts: impact traversal creates review obligations on every derivation using the context |
| TM09 | A brief whose synthesis omits an unchecked step: the mandatory part still lists it with its count; a front end that tries to drop it from the mandatory part is refused |
| TM10 | A person is released a brief and records nothing: exposure only; coverage unchanged |
| TM11 | End-to-end: a derivation with one step inspected step-by-step by a non-designated person and the rest end-to-end by a designated verifier is not shown as verified end-to-end; after a designated end-to-end inspection of the remaining step with no open objection, it is |
| TM12 | A request for a person's "verification record" or any per-person aggregate of inspections: refused; designations are shown only as attributed controls on the work |

---

## M.10 Slices

| Slice | Deliverable |
| --- | --- |
| 1a-core (already) | LaTeX source captured as span content, cited exactly (H2's source range); nothing structured |
| 3, with checking | The H1 to H7 hooks, in the core; parsing; symbol contexts, definitions and bindings; mathematical statements; models and derivations; dimensional screening; tool registry and tool-check recording; `renders` links, fidelity and inspection judgments; designations; derivation standing; the brief's mandatory part; MA1 to MA6; TM01 to TM12 |
| Later (pure-mathematics package, D-57, D-58) | Theorems, lemmas and formal statements; formal tool checks against Lean with toolchain, mathlib commit, axioms and `sorry` coverage |

This annex is reviewed with the checking annex, before Gate 3, unless the owner moves models and derivations earlier.

---

## M.11 Open items

1. **Does a computer-algebra system need a qualification record?** If so, a passed symbolic check would be offered as evidence only for a qualified tool version (M §14 item 3). A first answer is needed before Slice 3.
2. **The step-rule set:** it is curated, but its first contents and how it grows are unspecified. It should probably be a vocabulary (checking annex §5.8).
3. **Deployment-boundary classification of local tools** (§M.6), in the deployment profile (§14).
4. **The scale of a brief's mandatory part** for long derivations, which pagination alone may not solve (M §14 item 4).
5. **Hooks absorbed** in core 6.3 (§M.0); whether impact closure on §5, §9.9, §9.11 and the checking annex is complete is for the reviewer.

---

## Coverage and independence

Written by Claude (AI, Opus 5.5), the same model family as every text it extends; a reviewer outside the Claude family is required. It was written from the 6.2 core §§5.1–5.5, §7.4, §8.2, §9.9, §9.11, §9.14 and §12.3, and from the D1 mathematics formulation. Revision 6.3 rewrote only the front matter, §M.0, the slice row and open item 5, against core 6.3. No realized results were produced or reviewed. Choices of record fields, depths, outcomes and slice placement are the author's proposed defaults.
