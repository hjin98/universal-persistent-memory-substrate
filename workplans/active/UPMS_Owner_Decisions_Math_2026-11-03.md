# UPMS Owner Decisions on Mathematical Support, 3 November 2026 (D-57 to D-62)

3 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

The owner set the direction for native mathematical support in UPMS, after a discussion in a Claude Code session. Their words are quoted or closely paraphrased below. Claude wrote this record and cannot widen the decisions: where this record and the owner's words differ, the owner's words govern.

## 1. Decisions

| ID | Decision | Owner's words (abridged) |
| --- | --- | --- |
| **D-57** | **Models and derivations first; pure mathematics later.** The first mathematical package serves mathematical models, equations and derivations in STEM work. Definitions, theorems and formal proofs of pure mathematics follow as a separate package | "Models and derivations first, Pure math support later." |
| **D-58** | **Lean is the default formal system** for formal verification. It belongs to the pure-mathematics package | "Go with lean as the default for formal verification. It goes with the 'pure math' support package." |
| **D-59** | **LaTeX is the canonical mathematical notation** | "Use LaTeX." |
| **D-60** | **Checking and computation run outside the memory, as tools of the front-end environment.** Rather than a second front end, SCIRE is extended to support discussion of pure-mathematics subjects. Machine checking becomes one tool of that environment, alongside others that assist verification, such as a light computational environment on local hardware used as a proof-of-concept assist | "The actual machine checking … belongs to an external environment, not the memory itself … extend SCIRE to include external support and discussion capability for 'pure math' subjects, then the machine-check support will become a 'tool' for the environment, along other tools …" |
| **D-61** | **Agents formalize; humans inspect.** Agent formalization is a major route. Human verification and inspection run as a parallel mechanism: agents do the heavy lifting, humans inspect and correct, as in SSDP and SSDS. Agents present their work to maximize the efficiency of the human's attention: what is important, where the model is not confident, summaries. Full end-to-end inspection by a qualified human verifier remains the robust route, though it costs significant time and effort | "the agents do the heavy-lifting work, while human will inspect and correct … present it to human in a way that maximize efficiency of the user's attention … Full end-to-end inspection from qualified human verifier remains the robust route" |
| **D-62** | **The author's sequence proceeds**, resolving problems as they arise: check the 6.2 core for hooks, then a D1 paper on models and derivations, a SCIRE extension proposal, and a UPMS mathematics annex. The pure-mathematics package follows | "Proceed with your preferred sequence. We will resolve problems as we proceed." |

## 2. Design constraints the author proposed, not yet decided

The author proposed these in the same discussion. The owner did not object, but they are **proposals carried into the drafts**, not decisions:
- Tool results are evidence, never verdicts. A formal check is relative to the system, version, library and axioms. Numerical exploration only suggests.
- Three statuses are kept separate and never merged:
  - the mechanical check;
  - formalization fidelity (does the formal or structured rendering say what the informal claim says);
  - human inspection coverage.
- The inspection brief:
  - leads with objective signals before an agent's self-reported uncertainty;
  - prioritizes but never omits, and carries the mandatory lists and a coverage line;
  - when shown to someone, records exposure, not inspection.
- UPMS references SSDS model packages and never copies them (D-21).

## 3. What this record does not decide

It accepts no text. The drafts it directs need independent review outside the Claude family before acceptance (`AGENTS.md`). It does not commit a date or a slice; slice placement is proposed in the drafts.
