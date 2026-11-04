# UPMS Owner Decisions on the Mathematics Package Review, 3 November 2026 (D-71 to D-78)

3 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**The product owner accepted the author's recommendations on the owner questions raised by the same-family review of the mathematics package,** together with the simplicity changes the author recommended. The author put them to the owner in a Claude Code session, and the owner answered: "Accept, draft it". This record states those recommendations as decided and binds them to the review they answer. Claude wrote this record and cannot widen the decisions: where this record and the recommendations as put to the owner differ, the recommendations govern.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Mathematics_Package_Same_Family_Review.md` | `ea064acf1bba18b9b86d3eff0d36332def2284b7794716aa4c43d8f1a5f569c0` | The review whose §5 owner questions and §6 simplicity suggestions these decisions answer |

## 2. Decisions

| ID | Decision | Answers |
| --- | --- | --- |
| **D-71** | **Open assumptions and model relations are conditions, not premises.** A hypothesis a derivation introduces and does not discharge, and the defining relations and assumptions of a declared model a step uses, need no `supported` judgment for a route to be sound. They become conditions of the conclusion and travel with it ("valid under these assumptions"). A route that rests on them can be at most supported under those conditions | SM-2 |
| **D-72** | **Discharge is path-scoped.** A hypothesis counts as discharged for a conclusion only where every path from the hypothesis to that conclusion passes through a step that discharges it. The core checks the claimed discharges when a step is recorded and refuses one that no path supports. Discharges are listed in the standing report and in the brief's mandatory part | SM-3 |
| **D-73** | **Only humans inspect, and self-assessed fidelity never clears the list.** The core refuses an `inspection` judgment from any agent principal. A `fidelity` judgment by an agent, or by the rendering's author, is labeled as such and never removes the rendering from the mandatory "fidelity not assessed by an independent human" category | SM-4, FM-R20, FM-R27 |
| **D-74** | **A fidelity divergence triggers review.** A `diverges` fidelity judgment on a rendering is a cause of inapplicability: it creates review obligations on every assessment that cited a tool check of that rendering, and on the routes they back. The divergence is never cited in an assessment's basis, so D-70 holds | SM-1 |
| **D-75** | **Designation guards.** The core refuses a designation whose subject is not a person. A designation of the work's own author, or made by the designee, is allowed and labeled | FM-R15 |
| **D-76** | **Parsing and dimensional screening may run inside UPMS, later.** They are deterministic derived processing, like screening, not the external checking of D-60. Both move to a later slice. The first mathematics slice is: records, bindings by source range, derivations, tool checks, fidelity, inspection and the brief | FM-R24, review §5 item 9, §6 item 1 |
| **D-77** | **Registering a tool is an operator act,** recorded as a control and shown wherever a tool check appears, as D-66 does for front ends | FM-R23 |
| **D-78** | **A checking agent of another model family is preferred, not required.** A same-family check is labeled as such wherever it appears | Review §5 item 8 |

**Simplicity changes accepted** (review §6): `Model` is folded into a symbol context of kind `model`; `faithful_under(c)` is dropped; the brief's per-step time estimates are dropped; the inspection depth `end_to_end` is renamed `full`, and the depth levels stay as labels.

## 3. What this record does not decide

- **It accepts no text.** The revisions that apply these decisions stay proposed until a reviewer outside the Claude family has falsified them and the owner accepts them (`AGENTS.md`).
- **The review's other findings need no owner decision** and are the author's to repair.
- **D-71 and D-72 change the parent D1 formulation,** so they are applied there and in the core, not only in the mathematics texts.
