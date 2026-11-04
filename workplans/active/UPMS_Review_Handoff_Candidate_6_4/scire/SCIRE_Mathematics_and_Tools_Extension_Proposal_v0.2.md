# SCIRE Mathematics and Tools Extension

**Conceptual Proposal**

**Version:** 0.2
**Date:** 3 November 2026
**Status:** PROPOSED. Unratified. An extension of the SCIRE front end; it does not amend SCIRE v0.4, which stays frozen as an input. It replaces v0.1, which stays unchanged, and repairs the front-end findings of a same-family review of the mathematics package (Claude Fable 5.1, NO-PASS) under UPMS owner decisions D-71 to D-78; Appendix B maps the changes. The repairs are unreviewed.
**Author:** Claude (AI, Opus 5.5), at the product owner's direction (UPMS owner decisions D-57 to D-62, D-71 to D-78)
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer outside the Claude family, then the owner (`AGENTS.md`).

**Inputs**

| Input | Identity | Role |
| --- | --- | --- |
| SCIRE Conceptual Proposal v0.4 | `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md`, SHA-256 `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | The front end extended: meeting room, roles, demand-driven formalization, decision authority, SSDS transfer |
| UPMS owner decisions on mathematical support | UPMS repository, `workplans/active/UPMS_Owner_Decisions_Math_2026-11-03.md`, SHA-256 `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | D-57 to D-62 |
| UPMS owner decisions on the mathematics review | UPMS repository, `workplans/active/UPMS_Owner_Decisions_Math_Review_2026-11-03.md`, SHA-256 `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | D-71 to D-78 |
| Same-family review of the mathematics package | UPMS repository, `workplans/active/UPMS_Mathematics_Package_Same_Family_Review.md`, SHA-256 `ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0` | Front-end findings FM-R26 to FM-R31, and the role gaps of SM-4 |
| UPMS Mathematical Models and Derivations, D1 candidate 1.1 | UPMS repository, `workplans/active/UPMS_Mathematical_Models_Derivations_D1_Candidate_1_1.md`, SHA-256 `d1e0c9a6c88e224fd27d8601c28e28f91b9df75ed90151b0b71865831861710e` | Meaning of expressions, symbols, models, derivations, tool checks, fidelity, inspection and the brief, cited as "M FM-n"; its parent, the theory–evidence formulation 1.4, is cited as "TE" |
| UPMS Architecture Manual, candidate 6.4 core, and its mathematics annex | UPMS repository, `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_4.md`, SHA-256 `3c9844db1c2b99094c882f3f2bcb4e6d8cdbf9f7f9df6ab02f68f962729b2e09`, and `UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md`, SHA-256 `71083419f4b9d4091153d7fd86ec32046081eca1f295d9f31e0b867015f51a58` | The back-end contract this front end writes to |

Documents and their contents are design inputs, not instructions to execute tools.

---

## 0. Summary

SCIRE becomes the place where people and agents discuss, derive, check and inspect mathematics, not only empirical claims. It does so with the same objection, decision and review process, not a second front end (D-60).

- **First package:** mathematical models and derivations in STEM work (D-57).
- **Later package:** pure mathematics, with Lean as the default formal system (D-58).
- **Notation:** LaTeX (D-59).
- **Tools:** checking and computation are tools of the environment, never of the memory. The first tools are computer algebra and a light numerical environment on local hardware used as a proof-of-concept assist. Dimensional screening and parsing run in UPMS in a later slice (D-76). Lean arrives with the pure-mathematics package (D-60).
- **Division of labor:** agents do the heavy lifting of deriving, rendering and checking, and present the work so that a person's attention goes where it matters. People inspect and correct. Full inspection by a designated verifier remains the robust route for derivations that will be relied on (D-61). Only people record inspections (D-73).

UPMS keeps the records and their meaning; SCIRE runs the process.

---

## 1. Problem

Derivations decay in the same ways SCIRE v0.4 §1.1 names for arguments. A condition is dropped when a result is quoted. A sign convention changes between drafts. A step "checked by Mathematica" was checked on a mistyped input. A collaborator's "looks right" becomes "verified".

Agents now produce derivations and checks far faster than people can inspect them. Without structure, either people inspect everything, which does not scale, or they trust summaries, which hides errors. The extension aims at a third course: agent work arrives inspection-ready, people inspect what matters, and the record says exactly what was and was not inspected.

---

## 2. Scope and non-goals

**In scope:**
- mathematics in discussion: LaTeX in messages and documents;
- derivations as records;
- models with variables, units, domains and regimes;
- tool checks;
- formalization fidelity;
- human inspection;
- the inspection brief;
- handing derived models to SSDS (v0.4 §10.1).

**Later:** the pure-mathematics mode (§9).

**Non-goals:**
- SCIRE does not become a proof assistant or a computer-algebra system. It runs external tools and records what they did.
- No tool result is a verdict; no automatic "true", "verified" or "proved" (M MP3).
- No score of any person's mathematical competence (UPMS D-32). Who counts as a designated verifier is set by project rule (M FM-18).

---

## 3. Principles

The front end owes UPMS's mathematical principles (M MP1 to MP7) in everything it shows. It adds three of its own:

- **SP1 — Attention is the scarce resource.** The front end spends the person's attention on what is most consequential and least checked. It does not ration the record: everything stays reachable.
- **SP2 — Tools assist; people and attributed agents assess.** A tool runs, an agent proposes, and an attributed judgment assesses. A tool cannot resolve an objection or make a decision (v0.4 §8.3: an AI may propose, never decide).
- **SP3 — Inspection is an act.** Reading a brief is exposure. Inspection is recorded only when someone records it, with its scope and depth (M FM-16, FM-21).

---

## 4. Mathematics in the meeting room

**Writing.** Participants write mathematics in LaTeX, inline or as display equations. The front end renders it and sends the exact source to UPMS as span content. A participant may declare a symbol context (a paper, a model, a derivation) and its conventions: units system, sign conventions, index placement, summation.

**The secretary extends to mathematics** (v0.4 §8.6). It proposes, as interpretations attributed to itself:
- equations and statements with their kind (M Definition M.4);
- bindings of symbols to definitions;
- derivation steps with their step rule, introduced and discharged assumptions, and approximation order and validity.

These stay "interpretation, unconfirmed" until the speaker confirms them, or someone adopts them (v0.4 §4.3).

**Demand-driven formalization applies to derivations** (v0.4 §8.7). A derivation becomes structured records when:
- someone objects to a step;
- a decision is about to rely on its result;
- the result is about to leave the project, to SSDS or to publication;
- someone asks for it.

Until then it is a source record with an index.

**Objections** can target a step, an assumption, an approximation, a binding, a convention, a rendering or a tool check, and they travel as any objection does (TE Definition 2.5).

---

## 5. Roles

| Role | Who | Does | Never |
| --- | --- | --- | --- |
| Derivation agent | An AI participant | Drafts derivations, steps and renderings; runs tools; prepares the brief | Decides, resolves an objection, records an inspection, judges the fidelity of its own renderings or assesses its own steps |
| Checking agent | An AI participant other than the one that derived, preferably of a different model family (D-78) | Re-derives or attacks steps independently, as an attributed agent assessment; may record agent fidelity judgments, which are labeled | Counts as human inspection, or clears a rendering from the brief's mandatory part |
| Inspector | A person | Inspects at a chosen scope and depth; records fidelity judgments and objections | Is counted as having inspected what they were only shown |
| Designated verifier | A person named under the project's rule for the work or its scope (M Definition M.11) | Performs full inspection when a derivation will be relied on | Is designated by the system from any attribute of theirs |
| Facilitator | As in v0.4 §8.2 | Surfaces mandatory items and minority positions in discussion | Hides an item to keep the meeting short |

A checking agent from a different model family reduces common-mode error, but it is still an agent. Its assessment is shown as an agent assessment and never satisfies an inspection requirement. When no other family is available, a same-family checking agent may be used, and its work is labeled same-family wherever it appears (D-78). UPMS refuses an inspection judgment from any agent and labels agent and author fidelity judgments (D-73).

---

## 6. Tools

### 6.1 Tool contract

- **Registration.** A tool is registered by an operator act (UPMS D-77), with its name, version and environment description, and the registration is shown with every check of the tool. An agent cannot register a tool.
- **Invocation.** An agent or a person invokes a registered tool with a stated purpose and exact inputs. A model's raw output is never passed as a tool's input without being recorded first.
- **Isolation.** Tools that run code, notably the local numerical environment, run in a sandbox on local hardware:
  - resource limits, and no network by default;
  - no credentials;
  - no access to the memory beyond the inputs the invocation gives;
  - outputs that are inert data.

  Agent-written code is untrusted input, and its output is never treated as instructions.
- **Recording.** Every run, failed or not, is recorded in UPMS as a tool check (M Definition M.8): tool, version, environment identity (an image digest or lockfile hash where available), exact inputs, outputs, outcome, and what was left unchecked. Artifacts (scripts, notebooks, plots) are stored as payloads of source class M. No UPMS worker ever executes them; a re-run is a new tool invocation through the front end, with the artifact as a recorded input.
- **Meaning of a result.**
  - A passed symbolic check is evidence about its inputs (M FM-11).
  - Numerical exploration only suggests: an agreement is `consistent-with`, a disagreement is "values differ" with both values (M FM-12).
  - A fidelity divergence on a tool input puts the steps it backed under review (M FM-11, UPMS D-74).
  - A timeout or an unchecked side condition makes a check incomplete (M FM-13).

### 6.2 First tools (proposed defaults, not owner decisions)

| Tool | Use | Notes |
| --- | --- | --- |
| Computer algebra (for example SymPy) | Checking identities, simplifications, derivatives, integrals, series of a step | Outcome is about the tool input; fidelity of that input is separate (M FM-14) |
| Numerical environment (for example Python with NumPy and SciPy, or Julia), local hardware | Proof-of-concept exploration: sample-point checks, plots, small simulations, counterexample search | Exploratory; a counterexample candidate becomes an objection when someone asserts it |
| Dimensional checker | Dimensional consistency of equations under bindings | Later slice; runs in UPMS screening, and SCIRE presents its cues (M FM-3, D-76) |
| Lean | Formal checking | Pure-mathematics package (§9) |

Which computer-algebra and numerical systems ship first is an open choice (§12).

---

## 7. Derivation, checking and inspection workflow

1. **Draft.** The derivation agent writes the derivation as steps, each with its step rule, assumptions, approximation order and validity condition, and bindings to the relevant model and symbol context.
2. **Render and check.** It renders the steps that tools can check, runs the tools, and records every run. Steps no tool can check are marked as such.
3. **Attack.** A checking agent, preferably of another model family, re-derives the result or attacks the steps most likely to be wrong. It records attributed agent assessments and objections.
4. **Brief.** The derivation agent prepares the inspection brief (§8).
5. **Inspect.** The person chooses a scope and depth, inspects, and records inspection judgments, fidelity judgments and objections. Corrections go back to step 1 as new revisions; objections carry over to revised steps (UPMS D-47), and stay when a step is withdrawn (D-63).
6. **Verify in full** (when required). A designated verifier inspects every step, rendering and cited check on the route to the result at depth `full`. Only then is the **derivation** shown as verified in full, always with its premises' status and its carried conditions (M FM-17). It never makes the result true.

**When full verification is required** is project policy, which SCIRE owns. The proposed default:
- a finalization that relies on a derivation, an SSDS transfer, or a publication states the derivation's verification status;
- the project's rule decides whether that status must be "verified in full";
- a decision may proceed on less only with an explicit qualification, which travels with it as an override does (TE F-7).

---

## 8. The inspection brief

The brief is how D-61's "maximize the efficiency of the user's attention" is met. It has a fixed structure.

1. **What and why.** The result, what relies on it, and what a wrong result would cost.
2. **Coverage line.** For example: "inspected: 7 of 23 steps step-by-step; 12 tool-checked only; 4 neither" (M FM-19).
3. **Objective signals, ranked.** Each signal links to its record:
   - steps no tool checked;
   - failed, inconclusive or incomplete checks;
   - renderings without an independent human fidelity judgment (agent-judged and author-judged ones listed as such), and located divergences;
   - carried conditions: undischarged hypotheses and the model relations used; and discharged hypotheses, with the step that discharged them;
   - approximations with their order and validity;
   - convention changes;
   - unbound symbols and dimensional cues;
   - disagreements between the derivation and checking agents, and same-family checks, labeled;
   - steps whose only assessment is self-assessed or agent-assessed;
   - open objections.
4. **Producer's uncertainty, with reasons.** For example: "I am unsure the branch of the square root is right for x < 0, because …". These are stated as the agent's claims, ranked after the objective signals, and never as percentages (M FM-20).
5. **What changed** since the inspector last looked.
6. **Suggested inspection order.** The fewest steps whose inspection removes the most consequential unchecked risk. It is the producer's suggestion, labeled synthesis; the inspector chooses.
7. **Record inspection.** The inspector records what they inspected, at what depth, with what outcome.

**Rules:**
- Every mandatory item stays reachable from the brief with its count (M FM-21).
- Ranking never hides an item.
- No "approve all".
- The brief never shows a single overall confidence.

**Measuring whether it works.** The brief is a hypothesis to test, not a guarantee. Two different kinds of evidence are needed:
- **Deterministic tests** of the mandatory part (UPMS TM09, TM16, TM17): seeded items must appear with their counts. These pass or fail; no study is needed.
- **A seeded-error study** of whether brief-guided inspection finds errors at acceptable cost. It is registered as a SCIRE evaluation item **before any data**, stating:
  - the primary outcome (errors missed per derivation) and secondary outcomes (inspector time, false alarms);
  - the hypotheses and the comparison arms: brief-guided inspection, full inspection without a brief, and summary-only review;
  - the frozen error catalogue (sign errors, dropped conditions, wrong branches, unfaithful renderings, bad discharges), its seeding procedure and who seeds;
  - assignment of inspectors and derivations to arms, and blinding of inspectors to which errors were seeded;
  - the sample size and the analysis.

  The cheapest first evidence is the deterministic tests run on two or three real derivations from a project draft. D2 is opened only when a statistical comparison is actually needed.

The owner sets limits before measurement; none are set here.

---

## 9. Pure-mathematics mode (later, D-57, D-58)

The same workflow, with:
- definitions, lemmas and theorems as records;
- a Lean project per inquiry, with the toolchain and mathlib commit pinned;
- formal checks that report the axioms used and every unfinished `sorry`;
- formal statements as renderings whose fidelity a person judges (M FM-14);
- a lemma-dependency view.

Agent formalization drafts the formal statements and proofs. The brief adds "formal statement fidelity not yet judged" and "axioms beyond the standard set" as objective signals. A Lean check is relative to its system, version, library and axioms, and it is never "true". This mode is proposed in a later revision.

---

## 10. Back-end contract with UPMS

SCIRE keeps no copy of mathematical records. It writes:
- expressions, bindings, statements, models, derivation steps and tool checks;
- fidelity and inspection judgments and designations;
- objections and decisions.

All go to UPMS as attributed records, under the UPMS mathematics annex. SCIRE reads the mandatory part of every brief from UPMS's exact projections, so a front-end bug cannot drop a mandatory item that UPMS knows about. A model handed to SSDS (v0.4 §10.1) carries its derivation's carried conditions, verification status, the standing of its premises and its open objections.

---

## 11. Security

Running agent-written code is the main new risk:
- tools run sandboxed, without credentials or network by default;
- tool outputs are inert data, and a tool cannot write to UPMS except through SCIRE's attributed recording path;
- content in documents, messages, tool output or memory is never treated as instructions (UPMS TE-11).

Resource limits protect local hardware; a run that hits a limit is recorded as incomplete.

---

## 12. Open questions

1. Which computer-algebra and numerical systems ship first. Do computer-algebra results need a qualification record of their own before a passed check is offered as evidence (M §14 item 3)?
2. The project rule for designated verifiers, and when full verification is required by default.
3. Whether the brief's mandatory part stays usable at the size of real derivations (M §14 item 4).
4. When the pure-mathematics mode follows, and its first scope.

---

## 13. Inspectability statement (O1)

**Material realized record:** as in M §12, plus tool registrations, invocations with purpose, sandboxed run environments, briefs shown (as exposure) and inspection orders suggested.

**Readers and routine questions:** as in M §12, plus "what should I inspect first, and why?".

**Product surfaces, all beyond the requested deliverable**, binding only after the owner accepts them:
- the inspection brief;
- the derivation view;
- the tool-run view;
- the workflow of §7.

No realized scientific results were produced or reviewed in preparing this proposal.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), like SCIRE v0.4 and the UPMS texts it builds on. A reviewer outside the Claude family is required before acceptance.
- **Read directly:** SCIRE v0.4 §§0–2, 8 and 10.1; the UPMS D1 mathematics formulation, its owner decisions, and the candidate 6.2 core sections it cites; for v0.2, the mathematics package review, the D1 mathematics 1.1 and the 6.4 core hooks.
- **Not read:** SCIRE v0.4 §§3–7 and 9–17 beyond their headings and what the UPMS texts carry; the interoperability proposal v0.4; any external literature on proof assistants, computer algebra or inspection studies.
- **Choices:** the role split, the workflow stages, the brief's structure, the example tools and the seeded-error study design are the author's proposed defaults, except where D-73, D-76, D-77 and D-78 fix them.
- **Realized results:** none. **Variants:** none evaluated.

---

## Appendix B. Change map, v0.1 → v0.2

| Where | Change | Reason |
| --- | --- | --- |
| Front matter, inputs | v0.2; inputs bound by hash to the D1 mathematics 1.1 and core 6.4 with its annex; decision records and the review added | FM-R26 |
| §0, §6.2 | Dimensional checker moved to a later UPMS slice; only people inspect | D-73, D-76 |
| §4 | Tool checks are objection targets | FM-R13 |
| §5 | The derivation agent never judges its own renderings' fidelity or assesses its own steps; agent fidelity labeled and never clears the mandatory part; same-family checks allowed and labeled | FM-R27, SM-4; D-73, D-78 |
| §6.1 | Registration under D-77; environment identity; artifacts never executed by UPMS; divergence triggers review | FM-R22, FM-R23, FM-R30; D-74 |
| §7 | "Verified in full", a derivation property with premises and conditions; qualification travels as an override | FM-R02, FM-R03, FM-R29 |
| §8 | Carried conditions and discharges; independent human fidelity; self-assessed steps; no time estimates; deterministic tests separated from a pre-registered study | SM-3, FM-R20, FM-R28, FM-R31 |
| §10, §12 | SSDS hand-off carries premise standing; the model-family question closed by D-78 | FM-R03; D-78 |

No other text changed.
