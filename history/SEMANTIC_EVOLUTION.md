# UPMS Semantic Evolution History

This file preserves concise reasons for material semantic changes to UPMS that ordinary Git chronology cannot explain economically. It is historical context, not current authority. Current normative truth lives in the accepted owners; until an architecture manual is accepted, the records in `workplans/` carry the design lineage.

Each entry names the previous semantics, the replacement, the triggering evidence or rationale, the affected surfaces and the disposition.

---

## 2026-11-02 — Theory–evidence memory; SCIRE as front end (owner decisions D-20 to D-25; proposed)

- **Previous:**
  - UPMS held general context and logistics. Scientific argument belonged to a separate SCIRE system (SCIRE owner decisions D-A and D-D).
  - Candidate 5 certified none of what it recorded and needed no D1 parent.
  - Its security was sized for an operational environment, including instrumented-runtime information flow, release-segment access inheritance (D-6) and owner-confirmed publication.
  - Retention was time-based (for example, raw sources after 180 days).
- **Replacement (proposed):**
  - UPMS becomes one theory–evidence memory: evidence (what was acknowledged) and theory (what was believed, analyzed and argued) on one record model with three axes (provenance, content, standing).
  - SCIRE becomes the front end that runs the discussion process; UPMS is its memory engine.
  - SSDS stays outside, referenced only; its mechanisms may be borrowed.
  - Security is reduced to what open science needs: provenance, source classes, data-never-instructions, quarantine, attribution integrity and simple scopes, with an opt-in strict profile.
  - Retention follows importance and relevance: recommended-retention flags, an archive tier, and deletion only on explicit request.
- **Trigger:** the owner's conversation of 2 November 2026, answering the integration questions raised after the SCIRE v0.4 re-review.
- **Affected:**
  - `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md`;
  - the next manual candidate (candidate 5 §§1.4, 5, 7, 8, 10.5, 12, 14.2, 16 and 18.2, per the proposal's §13.3);
  - the SCIRE repository's proposals, which become inputs.
- **Disposition:**
  - D-20 to D-25 are owner decisions.
  - The proposal applying them is unreviewed and unaccepted.
  - Candidate 5 stays frozen as an input, and its independent review is not requested (D-23).
