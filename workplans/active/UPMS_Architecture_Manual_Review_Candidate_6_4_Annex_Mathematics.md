# UPMS Architecture Manual, Review Candidate 6.4: Mathematics Annex (proposed addition)

3 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** proposed D3 architecture; not accepted-current. **A proposed Slice 3 addition to candidate 6.4, reviewed separately from its Gate 0 package** (D-56). The 6.4 core (`UPMS_Architecture_Manual_Review_Candidate_6_4.md`, SHA-256 `3c9844db1c2b99094c882f3f2bcb4e6d8cdbf9f7f9df6ab02f68f962729b2e09`) lists this annex and carries its hooks (§M.0). It replaces the 6.3 mathematics annex, which stays unchanged, and repairs the findings of a same-family review of the mathematics package (Claude Fable 5.1; `UPMS_Mathematics_Package_Same_Family_Review.md`) under owner decisions D-71 to D-78; the changes are mapped in the 6.4 change history (A.14). Section numbers like "§9.9" are the core's.

**D1 parents:** UPMS Mathematical Models and Derivations, D1 candidate 1.1 (`UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md`, SHA-256 `d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e`), cited as "M Definition M.n" and "M FM-n"; and the Theory–Evidence Formulation 1.4 (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1_4.md`, SHA-256 `5e2b67f97b919d6612db6ed22bd6a3c7456b2be7141e4ef634bb3c2416afbb8f`), cited as "TE". **Owner decisions:** D-57 to D-62, D-70, D-71 to D-78. **Front end:** SCIRE, through `SCIRE_Mathematics_and_Tools_Extension_Proposal_v0.2.md` in the SCIRE repository.

**Mathematics is recorded and related here; it is checked and computed elsewhere.** UPMS stores expressions, symbol contexts, bindings, derivations, tool checks, fidelity and inspection, and computes their standing and the brief's mandatory part. Tools run in the front end's environment (D-60). **Fixed (proposed).**

---

## M.0 Hooks in the core

| Hook | Where in core 6.4 | What it does |
| --- | --- | --- |
| H1 | §5.3 Judgment `kind`; §7.6 | `fidelity` (target: a `renders` link) and `inspection` (target: an inspection scope). Separate statuses: route status never reads them and an inference assessment's basis never cites them (D-70). The inquiry ruleset covers both; only humans inspect, and every fidelity judgment records whether its assessor is an agent and whether it authored the rendering (D-73) |
| H2 | §5.1 Event `spans` | Optional `notation: latex` per span, with the exact source range (D-59) |
| H3 | §5.5 inference-step fields; §4.3 `record_derivation` | `step_rule`, `introduces[]`, `discharges[]`, `approximation{order, validity}`. A step belongs to one derivation; discharge is path-scoped and checked at commit; undischarged hypotheses and declared model relations are carried conditions (TE Definition 2.7, §6.1; D-70 to D-72) |
| H4 | Checking annex §5.7.1 Statement `kind` | `equation`, `inequality`, `identity`, `definition`, `assumption`, `approximation`, `conditional`, `conjecture`, with `expressions[]` (M Definition M.4) |
| H5 | §5.4 Controls; §4.3 `designate_verifier` | Verifier designations, with subject (a person, D-75), covered work or scope and interval; self-designation labeled |
| H6 | §5.5 Meaning family | `renders` (claim → rendering), assessed only by `fidelity` judgments; an objection on it challenges routes that cite its tool checks (TE §6.1) |
| H7 | §5 opening; §4.3 | Exactly four record kinds: expressions, symbol contexts (a model is a context of kind `model`), derivations, inspection scopes; with their operations. Any further kind reopens core §5 |

Also in the core for this annex: objections may target `renders` links, bindings and tool checks (§5.11, TE Definition 2.5); `rendering_diverges` is a review-obligation cause (§5.12, §9.11, D-74); `register_tool` is an operator act (§4.3, D-77); parses and screening cues are UPMS-derived representations (§12.3).

---

## M.1 Records

```text
MathExpression {
  span_ref                        // exact LaTeX source in an event (H2); the record
  context_ref                     // its symbol context; conventions apply through it
  macro_context_ref?              // the document's macro definitions, as captured
  parse_ref?, parser_version?, structure: full | partial | text_only   // parsing: later slice (D-76)
}

SymbolContext {
  kind: document | model | derivation | scope
  conventions: {units_system, signs, index_placement, summation, ...}   // each a defined claim
  parent_context?
  model?: {model_id, version, defining_claims[], regime, purpose, ssds_package_ref?}   // kind = model
}

SymbolDefinition = Claim (modality defined) with {
  symbol_latex, context_ref, quantity_kind?, dimension? | dimensionless | unknown
}

Binding = Meaning relation (§5.5) {
  source_range                    // the exact occurrence in a span; no parse needed
  symbol_definition_ref
  author, state: interpretation | confirmed | adopted   // TE Definition 2.3
}

Derivation {
  derivation_id, result_claim_ref, steps[]      // inference steps with H3 fields; each step owned by one derivation
  inputs[]                                      // results and imports needing judgments; model contexts; hypotheses
  // carried conditions and discharges are derived per conclusion (§M.5), never stored
}

ToolCheck = Event (observation) with {
  tool_ref                                      // registry entry, with the operator act that registered it (D-77)
  tool_version, environment_identity            // image digest or lockfile hash; else "description only"
  input_ref, rendering_link_ref?                // exact tool input; the renders link it realizes
  output_ref, outcome: passed | failed | inconclusive | incomplete
  unchecked[]                                   // side conditions, timeouts, sample-only coverage
  kind: symbolic | numerical_exploration | formal     // formal: pure-mathematics package
}

InspectionScope { members[]: exact revisions of steps, renderings, tool checks, statements }
// Inspection = Judgment kind inspection (H1) on an InspectionScope, by a human only (D-73), with
//   depth: spot | step_by_step | full, outcome, objection_refs[]
// Fidelity   = Judgment kind fidelity  (H1) on a renders link, with
//   result: faithful | diverges{at, how} | unknown; assessor_is_agent; assessor_authored_target
```

All of these are ordinary records, with home scope, owner, attribution, restriction tags and lifecycle as in §5 and §7. An agent's binding, rendering or derivation is an interpretation or attributed proposal (TE Definition 2.3) until it is confirmed, adopted or assessed. A binding, a `renders` link and a tool check can each be objected to (§5.11).

---

## M.2 Parsing (later slice, D-76)

A parser worker, one of the core's processing workers, derives `parse_ref` from the exact source under a named parser version and the captured macro context. It writes a processing record (§5.4), and its output is replayable. Parsing is not needed for bindings, which name source ranges.

What stays `partial`, with the ambiguous part kept as source text (M FM-2):
- overloaded macros;
- juxtaposition that could be multiplication or application;
- implicit index conventions;
- notation the parser does not know.

A parse never changes the source. Re-parsing under a new parser version is a new derivation of the parse, and comparisons cite the parse version they used.

---

## M.3 Bindings, conventions and impact

- **Bindings** are Meaning relations with authors. An agent's proposed binding is an interpretation until confirmed or adopted. Comparisons use only effective bindings, and only within one context or across contexts whose conventions are linked; otherwise the cue "conventions differ" (M FM-1).
- **A change to a symbol definition, a binding or a convention** is a definition change. It advances the scope epoch and runs impact traversal (§9.11), which follows bindings, each expression's `context_ref`, `renders` links and derivation inputs. It creates review obligations on dependent expressions, steps, derivations, renderings and results (M FM-4, FM-9).
- **Two contexts' symbols** are the same only through a meaning link of kind `identical` or `equivalent_under(c)` (TE Definition 2.12, M FM-10).

---

## M.4 Dimensional screening (later slice, D-76)

A deterministic screening channel, added to the checking annex's §9.7, evaluates dimensions under effective bindings and the context's conventions. It needs a parse (§M.2). It raises:
- **dimensional inconsistency:** the sides of an equation, the terms of a sum, or the argument of a transcendental function disagree;
- **not covered:** some dimension is unknown or unbound.

It is a cue, never a refutation, and the absence of a cue certifies nothing (§9.7). It is replayable at a pinned vocabulary and convention version.

---

## M.5 Standing of derivations

The standing projection (§9.9) is extended, computed at read like the rest of the report.

**Per step:** route status, as for any inference step (TE §6.1; M FM-8). An inference assessment whose assessor authored the step is labeled "self-assessed", and one by an agent "agent-assessed".

**For each derivation `Δ` and conclusion `κ`:**
- **Carried conditions:** `cond(Δ, κ)` computed by reachability over the owning derivation: hypotheses not discharged for `κ` on every path, approximation conditions with their orders on the paths to `κ`, and each declared model's identity, version and regime (M Definition M.7; D-71, D-72). Routes to `κ` through `Δ` are at most `supported_under(cond(Δ, κ))`.
- **Discharges:** each discharged hypothesis with the step and discharging rule that discharged it.
- **Coverage:** for each step, rendering and cited tool check on the route to the result, one of:
  - inspected, at its depth;
  - tool-checked only;
  - neither (M FM-16).
- **Verified in full:** true only if every member of that route lies within one or more effective `full` inspections, outcome `no defect found`, by people designated for that work or scope at the time, and no unresolved objection applies (M FM-17). It reads "derivation verified in full; premises: ⟨status⟩; conditions: ⟨cond(Δ, κ)⟩". Otherwise the report shows the parts.

**For each rendering:** its effective fidelity judgments, labeled "agent-judged" or "author-judged" where they are, or "fidelity not assessed" (M FM-14).

**For each tool check:** its outcome, what it left unchecked, the operator act that registered its tool, and, if its `renders` link has no effective fidelity judgment, "checked: rendering fidelity not assessed".

**For the models used:** adequacy claims and their assessments, shown apart from derivation validity (M MP7).

Caching and history follow §9.9: positions, ruleset and projection versions are pinned, and negative information invalidates caches.

---

## M.6 Tools and tool checks

- **Registry.** A tool is registered by an operator act (`register_tool`, D-77), recorded as a control with name, version and environment description, and shown wherever a check of that tool appears. A tool reference names a registry entry.
- **Recording path.** Tool checks reach UPMS only through the front end's attributed recording path. The invoker is recorded, with the tool as the method (§5.1). A tool never writes to UPMS directly.
- **Tags.** A tool check's input, output and artifacts carry the union of their inputs' restriction tags, because no writer chose them (§7.4). Sending content to a tool that runs outside the deployment is processing and egress (§8.5): processor eligibility applies. Tools on local hardware are inside the deployment boundary when the deployment profile says so.
- **Evidence semantics.**
  - A symbolic `passed` enters an inference assessment of the checked step as a record cited in that judgment's `supporting_refs`, with the `renders` link cited beside it. No evidence relation is created (M FM-11).
  - An effective `diverges` fidelity judgment on that `renders` link makes the check inapplicable for the step: the impact traversal follows the link to its tool checks and to the judgments citing them, and creates review obligations with cause `rendering_diverges` (§9.11, D-74).
  - Numerical exploration is recorded as an evidence relation of kind `consistent-with` or `bears-on, unassessed`, with its actual use (normally `model-check`); a disagreement is "values differ" with both values (M FM-12).
  - `incomplete` lists what it left unchecked (M FM-13).
  - A check made by an agent of the same model family as the derivation's author is labeled same-family (D-78).

---

## M.7 The inspection brief

- **Subject.** One derivation revision, or one result claim revision and every derivation to it (M Definition M.12).
- **Mandatory part.** A projection over exact records: the M FM-19 list, which includes carried conditions and discharges, renderings without an independent human fidelity judgment, and steps whose only effective assessment is self-assessed or agent-assessed, paginated with exact counts and a coverage line. It is built by the projection service like a hub, and its lines are current at read or marked stale (§10.5).
- **Ranked synthesis.** Supplied by the front end or an agent and labeled as synthesis (§5.2 `synthesis`). Uncertainty statements are claims attributed to their producer, with modality `asserted`; the order is the producer's claim, and no confidence value is stored (M FM-20).
- **Exposure, not inspection.** Release of a brief creates release records, which are exposure (§8.2). It never creates an inspection judgment (M FM-21).
- **Ordering.** The front end may order the synthesis as it likes. The mandatory part's membership is fixed by the projection, and a front end may add items to it but never remove them (§4.4: widen, never narrow).

---

## M.8 Deletion and retention

- **Parses, dimensional cues, coverage computations and brief projections** are UPMS-derived representations. They are purged or regenerated when an input is deleted (§12.3 names parses and cues).
- **Bindings, renderings, derivation steps, fidelity and inspection judgments and designations** are authored records. They follow §12.3 for authored descendants, and deleting a step or rendering that others relied on leaves a marker (SC-61).
- **Tool artifacts** are records like any other. They are retained by importance, never by time (D-25).

---

## M.9 Invariants and tests

**Invariants**

| ID | Invariant | Slice |
| --- | --- | --- |
| MA1 | Mathematical comparison uses only effective bindings under one context or linked conventions; unbound occurrences make a comparison unknown | 3 |
| MA2 | A derived result's carried conditions and discharges are always shown with it; its routes through a derivation are at most supported under those conditions | 3 |
| MA3 | A tool check is evidence about its inputs only, cited in a judgment's basis; without an effective fidelity judgment on its `renders` link it is shown as "rendering fidelity not assessed"; a divergence triggers review; numerical exploration never confirms; incomplete checks list what they left unchecked | 3 |
| MA4 | Check, fidelity and inspection coverage are separate lines; "verified in full" holds only under M FM-17 and names premises and conditions | 3 |
| MA5 | A brief's mandatory part is an exact projection that no front end narrows; showing a brief is exposure, never inspection | 3 |
| MA6 | Verifier designation is an attributed control under the project's rule, naming a person; no API computes a person's qualification | 3 |
| MA7 | Only humans record inspection judgments; agent-judged, author-judged and self-assessed work is labeled and never leaves the mandatory part on that judgment alone | 3 |

**Tests**

| Case | Trajectory and required discriminator |
| --- | --- |
| TM01 | `ψ` bound to a wave function in one context and a stream function in another: no comparison; an unbound third occurrence gives "unknown"; two contexts with different sign conventions and no link raise "conventions differ" |
| TM02 | (Later slice.) An equation adds an energy to a temperature: a dimensional cue, the claim not refuted; with one unbound symbol, "not covered" |
| TM03 | A result derived under `ε ≪ 1` at `O(ε²)` is cited later: the condition and order appear in the citing claim's standing; a rendering that drops them is marked diverging once a fidelity judgment records it |
| TM04 | A case split introduces `x > 0` and never discharges it: the result is shown sound under the carried condition `x > 0`; a split with every case closed discharges it |
| TM05 | A computer-algebra check passes on an input with the opposite sign: shown as "checked: rendering fidelity not assessed"; a human's `diverges` judgment then puts the step's route under review with cause `rendering_diverges`, and a decision citing the route shows the obligation |
| TM06 | Agreement at ten sample points: recorded as `consistent-with` with use `model-check`, never confirming; one disagreeing point is recorded as "values differ", and becomes an objection only when someone asserts it |
| TM07 | A check times out on branch cuts: `incomplete`, listing the branch cuts |
| TM08 | A sign-convention change between drafts: impact traversal creates review obligations on every expression and derivation using the context |
| TM09 | A brief whose synthesis omits an unchecked step: the mandatory part still lists it with its count; a front end that tries to drop it from the mandatory part is refused |
| TM10 | A person is released a brief and records nothing: exposure only; coverage unchanged |
| TM11 | Full verification: a derivation with one step inspected step-by-step by a non-designated person and the rest at depth `full` by a designated verifier is not verified in full; after a designated `full` inspection of the remaining step with no open objection, it is, and the line names its premises and conditions; an inspection made before the designation's interval does not count |
| TM12 | A request for a person's "verification record" or any per-person aggregate of inspections: refused; designations are shown only as attributed controls on the work |
| TM13 | A derivation from a model's defining relations with one open assumption: sound under the model and the assumption, both listed as carried conditions (D-71) |
| TM14 | A hypothesis used on a side branch that bypasses the step that discharges it: still a carried condition of the result (D-72) |
| TM15 | `record_derivation` with a step that discharges a hypothesis introduced in another derivation, or with a cycle: refused |
| TM16 | An agent judges its own renderings faithful: they stay in the mandatory part as "fidelity: agent-judged only"; an agent's inspection judgment is refused (D-73) |
| TM17 | The derivation agent assesses its own steps with its own tool checks: each assessment is labeled self-assessed and agent-assessed, and the steps stay in the mandatory part |
| TM18 | A tool check shows the operator act that registered its tool; a check by a same-family agent is labeled same-family (D-77, D-78) |

---

## M.10 Slices

| Slice | Deliverable |
| --- | --- |
| 1a-core (already) | LaTeX source captured as span content, cited exactly (H2's source range); nothing structured |
| 3, first part | The H1 to H7 hooks, in the core; symbol contexts, definitions and bindings by source range; mathematical statements; models as contexts and derivations; tool registry and tool-check recording; `renders` links, fidelity and inspection judgments; designations; derivation standing; the brief's mandatory part; MA1 and MA3 to MA7; TM01, TM03 to TM18 |
| 3, later part (D-76) | Parsing (§M.2) and dimensional screening (§M.4); MA1 over parses; TM02 |
| Later (pure-mathematics package, D-57, D-58) | Theorems, lemmas and formal statements; formal tool checks against Lean with toolchain, mathlib commit, axioms and `sorry` coverage |

This annex is reviewed with the checking annex, before Gate 3, unless the owner moves models and derivations earlier.

---

## M.11 Open items

1. **Does a computer-algebra system need a qualification record?** If so, a passed symbolic check would be offered as evidence only for a qualified tool version (M §14 item 3). A first answer is needed before Slice 3.
2. **The step-rule set:** it is curated, including the discharging rules, but its first contents and how it grows are unspecified. It should probably be a vocabulary (checking annex §5.8).
3. **Deployment-boundary classification of local tools** (§M.6), in the deployment profile (§14).
4. **The scale of a brief's mandatory part** for long derivations, which pagination alone may not solve (M §14 item 4).
5. **Impact closure of the hooks** on core §5, §9.9, §9.11 and the checking annex is for the reviewer to check.

---

## Coverage and independence

Written by Claude (AI, Opus 5.5), the same model family as every text it extends; a reviewer outside the Claude family is required. Revision 6.4 was rewritten from the 6.3 annex against core 6.4 and the mathematics D1 1.1, in answer to a same-family review by Claude Fable 5.1; the repairs are unreviewed. No realized results were produced or reviewed. Choices of record fields, depths, outcomes, labels and slice placement are the author's proposed defaults, except where D-71 to D-78 fix them.
