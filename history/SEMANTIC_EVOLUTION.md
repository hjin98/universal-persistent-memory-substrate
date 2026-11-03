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

## 2026-11-03 — Judge work, never score people (owner decision D-32, superseding D-31)

- **Previous:** D-31 allowed a conditional, conservative per-person track record (counts of outcomes per subject and period, shown on request).
- **Replacement:**
  - People are never scored, ranked or labeled. There is no person-level output of any kind: no score, rank, rating, track record, tendency, outcome count or label.
  - Authorship is never an input to a work's assessment, source assessment or retrieval ranking.
  - No view aggregates works by author to compare or characterize authors, and synthesis must not characterize a person's reliability, competence or motives.
  - Works and precise arguments are judged one by one, attribution stays on every record, and non-person channels may still be assessed.
- **Trigger:** the owner's clarification on 3 November 2026. The focus is the work, not the person. Reputations can be consequential to a person's life and career, and this is an area of sensitivity: "The most conservative solution is simply don't score them… We are dealing with real people here."
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.2, §6.4, §12 (TE-13), §15 and §17. Candidate 5's non-goal "no person reputation" is restored and extended.
- **Disposition:** owner decision; D-26 and D-31 stay in the record as superseded; the proposal stays unreviewed.

## 2026-11-03 — D-32 confirmed; anonymous and blinded review with a neutral judge (owner decisions D-33, D-34)

- **Previous:**
  - D-32 had been recorded but not yet confirmed.
  - The proposal had no review modes. Every critique was attributed openly, and no one was named to hold anonymous identities.
- **Replacement:**
  - **D-32 confirmed, with two clarifications.** The owner's reasoning: in human debate, a critic of a person stakes their own reputation and can be rebutted, while a system or agent stakes nothing and over-simplifies, which damages its neutrality. So only humans judge people, as signed, attributed claims linked to replies, and there is no track-record view.
  - **D-33.** Critiques and rebuttals of works may be open, single-blind or double-blind. An anonymous critique is a record, not authority, and is judged on its argument. Claims about people and AI critiques are never anonymous. Identity is sealed, not unknown: it is used for conflict checks and independence accounting. Anonymous personal attacks are blocked and returned to their writer for revision (de-escalation), never unmasked.
  - **D-34.** A neutral judge holds the sealed identities: an agent, or an assigned role with no conflict of interest. It was first called the review editor and renamed at the owner's request, because this is not a journal.
- **Trigger:** the owner's discussion on 3 November 2026, drawing on peer-review practice. On abuse: "the correct action is de-escalation instead… a revealed name there would likely cause personal escalation."
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.2, §6.4, new §7.1, §12 (TE-15), §15 and §17.
- **Disposition:** owner decisions; the proposal stays unreviewed.

## 2026-11-03 — The chair as the general discussion role (owner decision D-34, revised)

- **Previous:**
  - D-34 named a review editor, then a judge, as a neutral role existing only for anonymous review.
  - SCIRE v0.4 had a separate meeting facilitator.
- **Replacement:**
  - Discussion is open and spontaneous by default, and anonymity is a reserved choice.
  - The **chair** is the general discussion role: it organizes and orchestrates the discussion, manages its direction, takes views from all sides, summarizes, and runs anonymous critique when needed. It absorbs the facilitator.
  - Steering is not deciding, and the chair's summaries are attributed, labeled synthesis.
  - When the chair has a conflict with an anonymous critique (author, close collaborator, or PI of the work), the seal and any blocking for that critique pass to a conflict-free agent. This preserves D-34's requirement of a neutral, conflict-free holder of identities.
- **Trigger:** the owner's request on 3 November 2026 for a more appropriate name than "judge", and the clarification that the role is "basically like a chair in the discussion room".
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.2, §7, §7.1, §15 and §17.
- **Disposition:** owner decision; the proposal stays unreviewed. The SCIRE front-end specification will define the chair in full.

## 2026-11-03 — Reserved review chair, separate from facilitation (owner decision D-34, revised again)

- **Previous:** one "chair" both ran discussions and held the sealed identities for anonymous critique. When it had a conflict, the seal passed to an agent.
- **Replacement:**
  - Ordinary discussion is open, decentralized cross-review in which the PI's arguments are reviewed like anyone's, with no central reviewer and no anonymity.
  - An optional **facilitator** (SCIRE's existing role) organizes, steers and summarizes, holds no seal and decides nothing.
  - A **review chair** is appointed only when anonymity or blinded review is needed. It is a neutral agent, or a third-party person, who has not participated in the discussion and has no stake in it, and it holds the sealed identities for that review.
  - The conflict hand-off rule is no longer needed, because the review chair has no stake by definition.
- **Trigger:** the owner's observation on 3 November 2026 that the PI's arguments need review too, so a discussion chair cannot be the neutral party. "Let's just reserve this function only when it is needed."
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.2, §7, §7.1, §15 and §17.
- **Disposition:** owner decision; the proposal stays unreviewed.

## 2026-11-03 — Review-chair appointment; anonymous objections never block (owner decisions D-35, D-36)

- **Previous:**
  - The proposal said a review chair is appointed when someone needs anonymity, but not by whom.
  - An anonymous objection was subject to SCIRE's ordinary objection rule, so it could block a decision.
- **Replacement:**
  - **D-35.** Any participant may ask for a review chair, and posting anonymously counts as asking. By default the system appoints a fresh agent. A person serves only by explicit assignment from a participant with the manage right on the discussion's scope.
  - **D-36.** Anonymous objections inform but never block a decision, finalization or publication. They are shown with everything they apply to. A critic who later signs makes the objection an ordinary one from then on.
- **Trigger:** the owner's answers on 3 November 2026. A fresh agent is always available; a human chair needs explicit assignment by someone with administrator permission; an anonymous critic likely has little or no stake, so should not block progress.
- **Affected:** `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` §0.1, §0.2, §7.1, §12 (TE-15), §15 and §17. The objection rule itself is SCIRE front-end policy, and its specification must reflect D-36.
- **Disposition:** owner decisions; the proposal stays unreviewed. It keeps the label v0.1 and is frozen at its current hash for review.

## 2026-11-03 — Candidate 6 and the D1 theory–evidence formulation (proposed)

- **Previous:** candidate 5 had no D1 parent. Deletion propagated along inherited access requirements (D-6). The proposal left candidate 5 §§11, 12, 13 and 15 unreconciled and judgment on judgment open.
- **Replacement (proposed, unreviewed):**
  - A D1 formulation (`UPMS_Theory_Evidence_Formulation_D1_Candidate_1.md`) defines the meaning of the theory–evidence records, standing as a read-time report with no aggregate verdict, and a one-hop applicable set of objections from a decision's cited basis.
  - Candidate 6 (`UPMS_Architecture_Manual_Review_Candidate_6.md`) applies D-20 to D-36 to candidate 5. Deleting a source purges UPMS-derived representations but not records people wrote from it, which get review obligations; an erasure creates deletion obligations for their owners instead of deleting them.
  - Two repairs of the proposal's text: a curator's deletion of another's objection, judgment or dissent leaves an attributed marker (SC-61); everything an anonymous-role session causes is sealed, so release records cannot unmask a critic (SC-62).
  - After Codex's outside-family review of the proposal (NO-PASS) arrived during drafting: standing reads premises only through their effective judgments, so support needs no fixed point; decisions are reported, recorded or validated, and only validated ones make a position current; dissent is kept visible by deterministic mandatory lists, not by screening; an anonymous objection is read as never a procedural veto, though an independently verified invalidity still counts; anonymity is unavailable until its contract is qualified.
  - Judgment on judgment stays open as a proposed contract; candidate 5's rule governs until the owner decides.
- **Trigger:** the owner's request on 3 November 2026 to draft candidate 6 and the D1 formulation (proposal §14 step 2), and the Codex review of the proposal that arrived during drafting.
- **Affected:** the two new files; the review request `UPMS_Review_Request_Candidate_6.md`; `workplans/README.md`, which now also indexes the Codex review.
- **Disposition:** proposals only. The repairs and the deletion semantics need the owner's confirmation and a reviewer outside the Claude family. Candidate 5 and the proposal are unchanged.

## 2026-11-03 — Candidate 6.1 and D1 formulation 1.1 (proposed)

- **Previous:** candidate 6 counted independence between anonymous and signed records from sealed attribution, returned a failed conflict check's reason class, masked critic counts that per-critic pseudonyms already revealed, let `content` judgment-basis entries count without going stale, and named no owner for a scope's decision policy.
- **Replacement (proposed, unreviewed):**
  - Nothing a reader sees depends on sealed attribution: analyst independence between an anonymous and an attributed record, or across reviews, is "not established", and a conflict on sealed grounds shows as an ordinary decline.
  - Signing attributes every record under the critic's pseudonym in the review. Only the critic's own agent, or a temporary review-service session, may assist an anonymous critic.
  - A scope names its decision-policy owner, and only that front end can write `validated` decisions there.
  - Only `current` judgment-basis entries count. Assessments of channels and their track records move to a later slice.
  - De-attribution of derived statements is proposed. The author's recommendation is recorded on every open owner decision.
- **Trigger:** the owner's request to re-read the Codex review against candidate 6's body text, and then to add recommendations before drafting.
- **Affected:** the two new files; the review request `UPMS_Review_Request_Candidate_6_1.md`, which supersedes the unsent one for candidate 6; `workplans/README.md`. Candidate 6's word count was also corrected (about 40,600 words, not 37,900).
- **Disposition:** proposals only. The recommendations decide nothing; the owner decides, and a reviewer outside the Claude family reviews. Candidate 6 and D1 candidate 1 are unchanged.

## 2026-11-03 — Owner decisions D-37 to D-46

- **Previous:** D-36's reading, operator custody, erasure propagation, when anonymous review arrives, the first-product boundary, de-attribution, channel assessment and judgment on judgment were open or proposed, with the author's recommendations in candidate 6.1 §18.2 and §18.3.
- **Replacement:**
  - **D-37:** D-36 is read narrowly: no veto, but an independently established invalidity changes standing.
  - **D-38:** SCIRE's basis statement addresses every unresolved applicable objection.
  - **D-39:** judgment on judgment is deferred.
  - **D-40:** the operator-custody residual is accepted and disclosed to contributors.
  - **D-41:** erasure creates obligations, with an administrator fallback.
  - **D-42:** anonymous review arrives in Slice 3.
  - **D-43:** restricted material is excluded, with the creator's attestation.
  - **D-44:** de-attribution applies to derived representations.
  - **D-45:** channel assessment is deferred.
  - **D-46:** the SC-61 and SC-62 repairs are the chosen direction.
  - Confirmed: D-1, D-4, D-8, D-9, D-16, D-18, D-19 and the recency rule.
- **Trigger:** the owner accepted the recommendations ("Yes I accept the recommendations, proceed.").
- **Affected:** `workplans/active/UPMS_Owner_Decisions_2026-11-03.md`, bound to candidate 6.1 and D1 candidate 1.1 by hash. The texts fold the decisions in at their next revision.
- **Disposition:** owner decisions. Neither text is accepted. A same-family review was requested because the outside-family reviewer is unavailable for now; it cannot substitute for the independent review Gate 0 needs.

## 2026-11-03 — Candidate 6.2 and D1 formulation 1.2 (proposed)

- **Previous:** a same-family review found that, in candidate 6.1:
  - revising a claim resolved every objection to it;
  - "assessed-sound" depended on candidate 5's project-memory freshness, so no route could ever be sound;
  - sealing could leak through sessions, placement, edges, assignment and lifecycle acts;
  - any objector could block a joint decision at commit;
  - restore could lose revocations, access records and deletion markers.

  A same-family check found that the candidate 5 reconciliation (A.3) had dropped or misdescribed several candidate 5 properties still needed.
- **Replacement (proposed, unreviewed):**
  - Objections are carried to a revised target and stay unresolved.
  - Scientific standing uses its own effectiveness: latest in its line, in its validity interval, on a current target, with no wall-clock bound. Disagreement shows as "disputed".
  - The anonymous role is a distinct session type, and only a temporary review-service session may assist a critic.
  - The core never refuses a decision because an objection exists; late objections travel as a delta. A validated decision is current only once every required signature is in.
  - A recovery log holds every restrictive and sealing control, and restore applies it before serving.
  - Records that outlive deletion carry no payload. UPMS-derived representations carry their inputs' restriction tags.
  - The manual is split into a core, an anonymous-review annex, a checking annex and a change history.
  - Owner decisions D-47 to D-56 (the owner's "Draft on these", 3 November 2026) are folded in. D-49 amends D-9 as confirmed; D-48 bounds D-39's reach to judgments citing judgments.
- **Trigger:** the same-family review of 6.1 and the reconciliation check, run because the outside-family reviewer is unavailable for now.
- **Affected:** the six new files; `workplans/README.md`.
- **Disposition:** proposals only. Neither check is independent, and the repairs are unreviewed. Candidate 6.1 and D1 1.1 are unchanged.

## 2026-11-03 — Mathematical support: owner decisions D-57 to D-62 and first drafts (proposed)

- **Previous:** mathematics was text. D1 1.2 excluded general theorem proving and had no meaning for models, derivations, symbols or checks.
- **Replacement (proposed, unreviewed):**
  - **Owner decisions:**
    - D-57: models and derivations first, pure mathematics later;
    - D-58: Lean as the default formal system, in the pure-mathematics package;
    - D-59: LaTeX;
    - D-60: checking and computation run as tools of an extended SCIRE, not in the memory;
    - D-61: agents formalize and humans inspect, with briefs that direct attention, and end-to-end inspection by a designated verifier as the robust route.
  - **D1 formulation for models and derivations:**
    - notation is not meaning, so bindings are required;
    - dimensional checks are cues;
    - conditions and approximation orders travel with results;
    - tool checks are relative evidence, and numerical exploration only suggests;
    - check, fidelity and inspection coverage are separate;
    - verifiers are designated by project rule, never assessed (D-32);
    - a brief ranks but never omits, and showing it is exposure, not inspection.
  - **D3 mathematics annex**, with six core hooks to absorb at the next core revision.
  - **SCIRE extension proposal**, in the SCIRE repository.
- **Trigger:** the owner's request for native mathematical support and their answers on 3 November 2026.
- **Affected:** the four new files; the 6.2 review request (a note that the annex is not under review); `workplans/README.md`.
- **Disposition:** proposals and owner decisions. The 6.2 core is unchanged; the hooks wait for its next revision.
