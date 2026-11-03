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

## 2026-11-03 — Works ranked, persons never; scope of the first product (owner decisions D-26 to D-30)

- **Previous:** the theory–evidence proposal left five questions to the owner. It would have shown a person's assessed claims on request as a per-person track record.
- **Replacement:**
  - D-26: source assessment ranks works, never persons, because ranking people introduces politics. No score, ordering or track record is computed over a person's works taken together.
  - D-27: no strict profile in the first product.
  - D-28: four access rights (read, write, curate, manage).
  - D-29: any curator of a scope confirms archival.
  - D-30: project memory first, the theory layer second.
- **Trigger:** the owner's answers in conversation on 3 November 2026.
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.2, §6.4, §8, §9.1, §12 (TE-13), §14, §15 and §17. The proposal was edited in place before any review bound it.
- **Disposition:** owner decisions; the proposal stays unreviewed.

## 2026-11-03 — A person's track record, conservatively (owner decision D-31, superseding D-26)

- **Previous:** D-26 banned ranking persons. Only works were assessed, and nothing was computed over a person's works together.
- **Replacement:**
  - Works and precise arguments are still assessed one by one.
  - A person's track record may be built from those assessments, as a record of past tendency that can change with subject, context, time and incentives. It is not a ranking of the person.
  - The proposal makes it conditional (per subject, context and period, with declared incentives), never a single score, "insufficient record" when evidence is thin, on request rather than proactive, disputable by the person, and never a source of standing for a new work.
- **Trigger:** the owner reconsidered on 3 November 2026. A person's acts are more complicated than a score, but a record built from their works is useful. "Do this conservatively, and don't over-claim on someone who you don't know well."
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.2, §6.4, §12 (TE-13), §15 and §17. Candidate 5's non-goal "no person reputation" is narrowed to "no single person score".
- **Disposition:** owner decision; D-26 stays in the record as superseded; the proposal stays unreviewed.
