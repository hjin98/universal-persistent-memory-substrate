# SCIRE v0.4 — Re-Review of the Changed Contracts (same-family)

**Date:** 2 November 2026
**Reviewer / asserter:** Claude (AI, Opus 5.5), in a Claude Code session started by the product owner with the instruction to continue the latest hand-off in `workplans/active/`. No subagents or external tools were used.
**Family label:** **SAME-FAMILY, and same model.** Both v0.4 texts name Claude Opus 5.5 as their author. This review can inform a revision. It does **not** count as the independent review that acceptance needs (`SCIRE_v0.4_Re-Review_Request.md`, header; `AGENTS.md`).
**Verdict:** **NO-PASS / SERIOUS CHALLENGE for acceptance of these exact v0.4 candidates, with SUPPORT WITH REVISIONS for their direction.** The repairs substantially close the three v0.3 Serious Challenges and most v0.3 findings. Three narrower Serious Challenges arise from the repairs themselves, and several block-level inconsistencies remain. Each has a bounded textual repair. None calls for redesign, a shared runtime or a reopening of D-A to D-J.
**Status:** Proposed review findings. Not owner acceptance, a scientific gate, an implementation mandate or qualification. Every finding stays open until a new bound revision is checked.
**Governing method:** No task or workplan names a `protocol_version`, so the repository default, SSDP 7.2.1, applies. The software-design (D3) skill was used. D1 points are marked as such and route to scientific formulation.

---

## 1. Serious Challenges and decision

1. **SC-41 — Resolution by assessment is a cheaper and less visible exit than an override.** Once an objection is "resolved by assessment", it stops travelling with decisions. If the objector disputes the resolution, the dispute is recorded as an objection to the assessment. That kind of target is not in the list of things through which an objection "applies" to a statement, so the dispute neither blocks nor travels. Nothing stops the person who wants to finalize from also being the one who resolves. The D-H protections (reason, consequences, visible dissent) can therefore be bypassed, and the dissent-loss failure that SCIRE exists to prevent returns (§4.1).
2. **SC-42 — A hidden applicable objection cannot be handled under both the objection rule and metadata protection.** Take a decider who lacks access to the restricted source behind an applicable objection. Blocking the decision reveals that the objection exists. Allowing it breaks SCIRE-03. Rule 5's fallback ("limit the decision where a safe view cannot be produced") fires only when the hidden item exists, so it is itself an existence oracle (§4.2).
3. **SC-43 — Unknown lineage has no consistent home.** A quarantine authorized by the *receiver's* or *project's* policy permits retaining content that may derive from a source whose *owner* forbids it, which contradicts D-I and repeats V3-01 under a new name. The trust boundary also gives no way to tell which part of a participant's or agent's contribution came from outside mediation. In the MCP deployment the adoption sequence names, every agent write would be unknown lineage. The floor then either quarantines every agent's memory or never operates (§4.3).

These are demonstrated textual contradictions or material ambiguities in the bound candidates. They are not observed implementation failures, and no frequency is claimed.

**What v0.4 gets right and must keep:**
- handling is separated from resolution, so acknowledgement and deferral no longer unblock anything;
- overrides are scoped, attributed and never count as resolution;
- availability is distinguished from eligibility, with exact execution outcomes;
- retention is checked before storing, restrictions are conjunctive, and a missing constraint declaration is never read as an empty set;
- use history has an inference-specific warrant;
- origin, qualification and usability are separate;
- comparability is relative to the target claim, and logical contradiction, statistical disagreement and failed prediction are distinct;
- adoption is separate from confirmation of intent;
- outcome decisions are separate from model finalization;
- authority is scoped for several PIs;
- decision exposure is recorded, and UPMS keeps custody.

These close the v0.3 trajectories as the v0.3 review posed them (§3). The new challenges concern edges that the repairs created.

**Acceptance boundary.**
1. Repair SC-41 to SC-43 and the block-level findings V4-04, V4-05 and V4-07 in new candidate files.
2. Have a reviewer **outside the Claude family** review the changed contracts.
3. The owner decides the items in §8.

E1 to E4 remain unexecuted.

---

## 2. Bound inputs, authority and independence

The repository was clean at intake, at commit `64a0068b79956332efa70403787f150217adf277`. Every hash below matches the request exactly. In this review, **S** is the SCIRE v0.4 proposal and **I** is the interoperability v0.4 proposal. Line numbers refer to the bound bytes.

| File | SHA-256 | Use |
| --- | --- | --- |
| `SCIRE_Conceptual_Proposal_v0.4.md` | `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Primary; read in full |
| `Memory_and_Domain_Interoperability_Proposal_v0.4.md` | `d901deb5e7bc6f749c4770eb7aef3d75325fee472ef00b5981ee7861666d09e3` | Primary; read in full |
| `SCIRE_v0.4_Re-Review_Request.md` | `2fc5c10225204b1e287408cba47c206ccd8fd33273c7ebe59c2ec5c28495464f` | The request; read in full |
| `SCIRE_v0.3_Independent_Concept_Review.md` | `60dae8f585390ccb6636aa4513aa6155ac0c1b378ea4299ef4656d0078435021` | Findings being answered; read in full |
| `SCIRE_v0.3_Independent_Concept_Review_Handoff.md` | `15fb9211c87e1133bbf125431dc14a16b66321b83e10402928fcf21bbc4ac780` | Earlier questions; read in full |
| `SCIRE_Conceptual_Proposal_v0.3.md` | `02c5ece20beccb93021ce0fe156d170d3ae7dfecffbf5768aef1f4a05c211459` | Predecessor; §§2, 4, 6–10 compared directly, other sections by heading |
| `Memory_and_Domain_Interoperability_Proposal_v0.3.md` | `b4a594ae1b4369cf064565c7a25d8ff0b402d1fbaaa5f2b2c38464ce2c64c916` | Predecessor; §§3.2–4, 6–7 compared directly, other sections by heading |

`history/SEMANTIC_EVOLUTION.md` and `workplans/README.md` were also read. The owner decisions D-A to D-J are taken from the recorded headers and history entry. The owner conversation itself was not accessed.

**Independence limits.** This reviewer is the same model as the author of v0.4, of v0.3 and of the v0.2 review. Shared blind spots are therefore likely, and this review supplies **no family separation**. This session has no memory of writing v0.4, but that does not make the review independent. The v0.3 review was read *before* the v0.4 texts, and the change maps sit inside the files under review, so the analysis is anchored on both. Closure judgments below rest on the v0.4 body text, as the request requires, and never on the change maps alone.

---

## 3. Closure of SC-31 to SC-33 and V3-01 to V3-13

"Closed" means the v0.3 review's trajectory no longer succeeds against the v0.4 body text. It does not mean the area is now defect-free.

| ID | Verdict | Basis in v0.4 text | Residual |
| --- | --- | --- | --- |
| **SC-31 / V3-01** confidentiality | **Partly closed** | S §9.2 rules 1–7 and the trust-boundary and revocation paragraphs (L469–493); I §7.1–7.4 (L203–237). The writer-scope retention trajectory fails, because rule 1 needs retention permission before storing. Existence signalling is replaced by rule 5. Carried constraints need trusted producers, and a missing declaration means unknown lineage. Revocation works through grants with expiry or revalidation, and caches are covered by I rule 8. | SC-43 (quarantine authority, undetectable declared gap, MCP deployment); SC-42 (metadata against the objection rule); V4-08 (an empty set from a context that is not input-closed); V4-09 (over-restriction uncontrolled) |
| **SC-32 / V3-02** objection disposition | **Partly closed** | S §4.4 (L221–237): handling statuses resolve nothing; the resolutions are listed; unresolved objections and overrides travel; the rule applies through dependencies. §6.6 (L371–378): links under review cannot newly support a decision. The acknowledge-and-defer-then-finalize trajectory now fails (scenario G). | SC-41 (resolution by assessment); V4-06 (applicability set by how much was recorded); V4-07 (review obligations still close by an undefined "disposed of") |
| **SC-33 / V3-03** availability and evidence | **Closed**, with a minor residual | S §2.6 (L141–148), SCIRE-15; I §4 (L129–136), §8.7 (L271–278); outcome states in I §6.2 (L187). The broad-publication trajectory now yields "refused or qualified", and "not performed" needs a known precondition. | V4-13 (a snapshot cannot show later requalification; wording of I §5.3 and INT-06); V4-15 (outcome enumerations differ between S and I) |
| **V3-04** basis | **Partly closed** | S §4.5 (L239–248) requires a basis statement, including the hypotheses of imported results and whether they hold, and says a finalization cannot substitute for it | V4-04: SCIRE-11 (L582) lets "an explicit record that they were not done" stand in for the basis statement, contradicting §4.5. V4-05: the requirement covers every decision |
| **V3-05** use history | **Closed** | P5 (L162); §6.2 (L335–345): non-exclusive history, an inference-specific warrant, proofs marked not applicable, a narrow independent-confirmation label | None material |
| **V3-06** finalization scope | **Closed**, with residuals | §2.2 (L95–121): five decision kinds, scoped finalization, outcome decisions; §2.3 (L123–125); SCIRE-16; scenarios R and S; I §3.3 | V4-14 (who judges scope overlap); V4-20 (what a joint signature binds); §8 item 8 (escalation when PIs conflict) |
| **V3-07** capture | **Partly closed** | §8.7 (L442–453): triggers fire before reliance, plus bounded source review; §9.1 (L459–467): capture coverage; "pays nothing" removed | V4-10 ("reviewed for extraction" is not complete extraction); V4-11 ("fires before" cannot be enforced for informal decisions) |
| **V3-08** observation and qualification | **Closed** for custody and qualification; **regression** elsewhere | §4.2 (L203–205): observations are source records and can be unassessed; investigation outcomes. §6.4 (L351–361): origin, qualification and usability are separate; upgrade criterion | V4-12: the v0.3 rule that uninstrumented evidence cannot back a finalization without upgrade was dropped, so upgrading now has no consequence; the change map does not record this |
| **V3-09** adoption | **Closed** | §4.3 (L213–219), SCIRE-04, scenario I | None material |
| **V3-10** comparability | **Closed** | §5.3 (L276–304): relative to the target; logical, statistical and failed-prediction kinds; regime as the test; the subgroup example; units errors kept in history. Scenarios E and F | None material. D1 note: "more than a stated model makes plausible" should name the test or threshold used (low) |
| **V3-11** custody and exposure | **Closed** | §4.1 (L186–188), §7.1 (L388–400): decision exposure, occurrence time, time scope. §10.3 (L527–529) and I §3.2 (L102–108): UPMS keeps custody | SCIRE-09 exposure and "as SCIRE held then" are limited by permitted deletion (§7.3); say so (V4-20) |
| **V3-12** warrants | **Closed** | §6.5 (L365–369), SCIRE-07 | None |
| **V3-13** experiments | **Partly closed** | §15 (L649–668): matched comparators, owner-set limits, development and evaluation split, variant disclosure, expanded E3 and E4 cases, order | V4-09: E3 rejects only leaks, so a deny-all floor wins; v0.3 I §7.4's "leak *or block too much*" criterion was dropped. V4-19: nothing measures the cost of the new mechanisms |

**Re-run of the v0.3 review's §4 and §6 trajectories.**
- **§4.1:** retention in the writer's scope now fails. The trust-model trajectory (agent context, note, UPMS, "no SCIRE reads" declaration) fails only if the declaring context is input-closed (V4-08).
- **§4.2:** acknowledge, then finalize, now fails. Resolve, then dispute, then finalize succeeds (SC-41). The retraction trajectory fails while the obligation is pending, but can succeed after an undefined "disposal" (V4-07).
- **§4.3:** fails as intended.
- **T1, T2 and T3** (§6): all fail as intended under §5.3.

---

## 4. Serious Challenge trajectories and bounded repairs

### 4.1 SC-41 — Resolution by assessment

**Text.** An objection is resolved by "an attributed assessment, by someone with authority for the scope". If the objector disputes it, "the dispute is kept as a further objection or as dissent" (S L227). An objection *applies* to a statement when it targets "the statement itself or a material dependency within stated coverage: a premise, an inference step, an applicability condition, or an evidence link the statement relies on" (L235). Only "every unresolved objection that applies, and every override, travels with the decision" (L237). Who may resolve is left to the project (§8.3; open question 9).

**Trajectory.**
1. Dr Q objects to C ("mechanism M explains the effect throughout regime R") on the ground that M fails in part of R.
2. The PI, who holds authority for the scope, records an assessment that a linked answer meets Q's ground. O is now *resolved*.
3. Q disputes the assessment. The dispute is recorded as O′, whose target is the assessment.
4. An assessment is not a premise, an inference step, an applicability condition or an evidence link, so O′ does not *apply* to C.
5. The PI finalizes C. No applicable unresolved objection exists, so no override is needed. The package (§10.1) carries neither O nor O′. If Q's disagreement went in as "dissent", it was attached to the resolution, not to the finalization.

**Consequence.** The decision-facing record no longer shows a live scientific dispute. The resolver may be the same person who benefits. D-H's requirements (reason, accepted consequences, use limits, visible dissent) apply only to overrides, so a decider who would otherwise need an override has a cheaper exit with less to record. This is v0.3's SC-32 in a narrower form: an act with administrative effect removes unresolved scientific force from the view where the decision is taken.

**Strongest opposing reading.** A project may forbid self-resolution, and "dissent" may be meant to travel. Neither is stated, and the default leaves the route open.

**Bounded repair.**
- Make resolution by assessment a **decision kind**, or a sub-kind of one, so that it carries authority basis, scope, basis statement, exposure and dissent like any other decision.
- A **disputed resolution travels.** An objection to a resolution applies to every statement the original objection applied to, and any decision relying on those statements shows "resolved by assessment (disputed)" with both records.
- When the resolver is also the decider relying on the target, the decision shows **"self-resolved"**. Whether that is permitted is an owner decision (§8 item 1). Requiring the objector's assent is not part of this repair: it would create the veto that §4.4 rightly avoids.

No voting or scoring machinery is needed.

### 4.2 SC-42 — Hidden applicable objections against metadata protection

**Text.**
- An applicable material unresolved objection blocks a decision unless overridden. It then travels "on every view of that decision and in any model package" (S L235–237).
- Rule 5: the existence of a restricted source and its lineage are restricted. A view "never reveals whether a particular hidden item exists". "Where a safe and adequate view cannot be produced, the view or the decision that depends on it is limited instead" (L485).
- I rule 5 (L230) protects existence in refusals and coverage statements.

**Trajectory.**
1. Project P has PIs A and B with overlapping scopes (§2.3).
2. A has access to an industrial collaborator's restricted dataset X; B does not.
3. A records objection O to C, derived from X: "X shows C fails above 200 K". O inherits X's restrictions, including on its existence (rule 5).
4. B, acting within scope, moves to finalize C. One of three things happens:
   - **The finalization is blocked** because O applies. B learns that a hidden applicable objection exists, which breaks rule 5. Repeated attempts over different subsets of C locate it.
   - **It proceeds**, because B cannot see O. SCIRE-03 is broken, and the package goes to SSDS without O.
   - **The rule 5 fallback applies.** It is conditioned on "a safe and adequate view cannot be produced", which is true only because O exists. Limiting the decision under that condition is the same existence oracle.
5. The transfer to SSDS raises the same problem when SSDS is not cleared for X.

**Consequence.** For any decider or receiver with less than full access, SCIRE's central dissent guarantee and its metadata guarantee cannot both hold. Partial access is ordinary in multi-PI and industry-collaboration projects. A coverage statement such as "this view covers only records you may see" stays honest, but it is not enough for a decision, and making it enough for a decision leaks.

**Bounded repair: make every limitation independent of whether hidden items exist.**
- A consequential decision records the **decider's access coverage** relative to scopes that the project's policy declares may bear on the target. The determination uses scope configuration, never item existence.
- If any such scope lies outside the decider's coverage, the decision is **uniformly** marked "decided on partial coverage". It then needs either a co-signer cleared for those scopes (joint sign-off under D-G) or a cleared review. Whatever the co-signer or reviewer may tell the decider is released under the source owner's policy.
- The package carries the same existence-neutral qualification.

What a cleared reviewer may reveal, and whether partial-coverage decisions are allowed at all, are owner decisions (§8 item 2).

### 4.3 SC-43 — Unknown lineage, quarantine and the trust boundary

**Text.**
- S rule 1 (L481): unknown-lineage content is stored only in "an authorized quarantine scope, if the project's policy defines one".
- I rule 1 (L222): "a scope the receiver's policy authorizes for unknown-lineage content".
- D-I (S L35): retention "belong[s] to the source owners".
- S trust boundary (L489) and I §7.4 (L237): content "a participant or an external agent brings from outside … mediation" is unknown lineage, and the participant "remains responsible".
- I rule 3 (L224–228): constraints are accepted only from trusted producers (a system's own mediated contexts or designated adapters), and a missing declaration is unknown lineage.
- I §12 step 3 (L337): first operations "through MCP servers or equivalent".

**Trajectory (a): who authorizes quarantine.** Source A's owner permits reading but forbids retention outside A's environment. An agent reads A and writes a paraphrase into UPMS without a trusted declaration. UPMS's policy defines a quarantine, so the paraphrase is retained there. A's owner never authorized that retention: the receiver did. That is the V3-01 conflict under a new name. If the writer can read its quarantine, the result also matches v0.3's "narrowest scope the writer may use".

**Trajectory (b): undetectable declared gap.**
- In a SCIRE meeting, a scientist mentions a result she heard in a confidential talk. The utterance is output from a context SCIRE runs, so its lineage is taken to be the meeting's release set (rule 3). But part of it came from outside.
- SCIRE cannot tell which part, so the rule "treat it as unknown lineage" cannot be applied to anything in particular. Applied to every participant contribution, it would quarantine and withhold the meeting record itself (rules 1 and 6). Applied to none, it never operates.
- The same holds for "conservative bound": the release set is an upper bound on what an output may derive from only for contexts that nothing outside can reach.

**Trajectory (c): the named deployment.** With MCP servers, agents run in their own runtimes. Neither SCIRE nor UPMS mediates their contexts, and neither has designated them as trusted adapters. Under I rule 3, every agent write to UPMS ("Record context", I §6.2) and every agent contribution to SCIRE is unknown lineage. UPMS's core function becomes quarantine-or-refuse for all agent memory, unless the agent runtime is designated a trusted producer. That designation would require the runtime to know every restriction on what it read (see V4-08).

**Consequence.** As written, the floor either contradicts D-I or is unimplementable or unusable in the deployment the proposal names. The benign reading ("participants are responsible, as in ordinary confidentiality") is the right model, but the text gives it no mechanism. It labels the content unknown instead.

**Bounded repair.**
- **Accountable declaration.** A person, or the operator accountable for an agent runtime, may declare the restrictions on content they contribute, under their own attribution and responsibility. This is the ordinary-confidentiality model the text already invokes. It is not a trusted-producer empty set: it is an auditable claim with a named asserter. A declaration can be wrong, and that responsibility is the declarer's.
- **Unknown lineage** then means content with **no accountable declarer** (automated imports, undesignated agents). Such content is refused. Alternatively it may be held in a quarantine whose retention terms the **source owners** authorized, for example through a standing grant covering what the writer could have read. A receiver's policy alone is not enough. Quarantined content is not available for ordinary use.
- State that rule 3's release set is a conservative bound only for input-closed contexts (V4-08).
- Open question 5 becomes an owner decision (§8 item 3).

---

## 5. New findings

Priority: **Block** means repair before accepting the affected contract. **Revision** and **Clarification** do not block acceptance of the direction. Confidence concerns the textual or logical finding, not how often it would occur.

| ID / priority | Section | Claim under test | Counterexample or reasoning | Consequence / owner | Disposition | Confidence |
| --- | --- | --- | --- | --- | --- | --- |
| **V4-01 / Block (SC-41)** | S §4.4, §8.3, SCIRE-03 | Only resolution or an override changes what may rely on a target, and dissent travels | §4.1 | Dissent loss returns; D-H can be bypassed. D1 meaning, D3 enforcement | §4.1 repair; owner decision §8 item 1 | High |
| **V4-02 / Block (SC-42)** | S §4.4, §9.2 rule 5, §10.1; I §7.3 rule 5 | SCIRE-03 and metadata protection both hold | §4.2 | Leak or hidden dissent for deciders with partial access. D3 security | §4.2 repair; owner decision §8 item 2 | High |
| **V4-03 / Block (SC-43)** | S §9.2 rules 1, 3, 6 and trust boundary; I §7.3 rules 1, 3, §7.4, §12 | The unknown-lineage floor respects D-I and works | §4.3 | Contradicts D-I or does not operate. D3 security and interoperability | §4.3 repair; owner decision §8 item 3 | High |
| **V4-04 / Block** | S SCIRE-11 (L582) against §4.5 (L241, L248) and §8.7 (L451) | A basis statement is required before consequential use | SCIRE-11 allows "a basis statement and a bounded source review, **or an explicit record that they were not done**". §4.5 makes the basis statement mandatory; §8.7 allows the not-done record only for the source review. An implementer following the invariant can finalize without a basis | Reopens V3-04 through the normative summary. D1 | Change SCIRE-11 to "requires a basis statement, and a bounded source review or a record that it was not done" | High |
| **V4-05 / Block** | S §4.4 rule (L235), §4.5 (L241), §2.2 | Objection and basis rules apply to consequential uses | Both say "a decision" without qualification. **Inquiry decisions** ("work under H for now"), recorded **external decisions** and **overrides** are all decisions. In v0.4, a hypothesis with an acknowledged objection needs an override, a basis statement and a source review before anyone may explore it. In v0.3, acknowledging was enough. An override is a decision whose basis is the objected statement, so on a literal reading it needs an override itself (a regress) | Bureaucracy, or literal unrealizability, in everyday inquiry. D1 meaning of consequential use | Define a **closed list** of consequential uses: outcome decisions, finalization, publication, transfer and resolution decisions (SC-41). Inquiry decisions rely on statements in the existing "assumed (for an inquiry)" modality, which the rule does not block. Overrides and external-decision records are exempt by definition | High |
| **V4-06 / Revision** | S §4.4 "within stated coverage" (L235), §4.5 | Applicability through material dependencies is workable and cannot be bypassed | (a) **Bypass:** C's basis is a paragraph mentioning premise P, which is a record elsewhere with unresolved objection O. No dependency link C→P is recorded, so O does not apply to C. Less structure means fewer applicable objections. (b) **Workability:** whether applicability is transitive is unstated; transitively, any upstream objection blocks. (c) Who states the coverage is unstated | The rule's strength depends on the relier's choice of structure. D1/D3 | Make the **basis statement the coverage boundary**: it cites by identity the records for the premises and evidence it names. Applicability covers objections to the statement and to those cited records (one hop), stated on the decision. Bounded source review covers the rest. This makes the rule both bounded and hard to bypass, because omitting a material premise is a visible defect of the basis | Medium-high |
| **V4-07 / Block** | S §6.6 (L373, L378), SCIRE-08 | A retraction prevents new unqualified reliance | A review obligation "appears in the compass until **disposed of**". Disposal is undefined: the assignee could acknowledge it and close it, after which the link stops being under review. The SC-32 split between handling and resolution was applied to objections but not to review obligations. The "or a qualified claim" exit (L378) has no requirement that the qualification travel | Retraction trajectory 6 can succeed again. D1/D3 | A review obligation closes only through an attributed reassessment of the link's usability, by someone with authority. Assigning or acknowledging it does not close it. A qualification used instead of an override travels like an override | High |
| **V4-08 / Revision** | I §7.3 rule 3 (L226), §7.2; S rule 3 (L483) | A trusted producer's affirmative empty set is sound | A context SCIRE hosts can also call UPMS or other tools. SCIRE knows only what *it* released, so "its mediated context held no restricted content" is unjustified. I §7.2 itself says no system sees what an agent read elsewhere | Restricted content is laundered as declared-clean. D3 security | A trusted producer's declaration covers only its own releases, unless the context is **input-closed** (every input passes through the producer). Otherwise the declaration is partial, and the rest is unknown lineage or rests on an accountable declaration (SC-43) | Medium-high |
| **V4-09 / Revision** | S §9.2 rules 2, 3, 6, §15 E3 (L663); I §7.5; v0.3 I §7.4 | Over-restriction is controlled | One restricted slide shown in a meeting taints everything produced afterwards. A reset requires "verifiably" removing derived content, which humans cannot do. Conjunctive restrictions accumulate. The listed controls only label or reduce the problem: audience-scoped generation leaves existing taint, grants need owner work, and "awaiting clearance" is a state. E3 "reject[s] any floor that permits a forbidden action; choose[s] the cheapest", so a deny-all floor passes. v0.3's trigger, "leak **or block too much**", was dropped without a change-map entry | Over-restriction becomes the stable failure, and the experiment cannot detect it. D3, experiment design | Make E3's decision rule two-sided. Measure the fraction of records withheld or quarantined, clearance latency, and decisions delayed by clearance, against limits the owner sets beforehand. Allow taint to be scoped to the agent context separately from human transcript spans, which are under the participant-declaration model (SC-43) | Medium-high |
| **V4-10 / Clarification** | S §9.1 (L463), SCIRE-13 | Capture coverage prevents false reassurance | "Which source intervals have been reviewed for extraction" lets a reader infer completeness inside reviewed intervals. A reviewed interval can still hold a missed qualifier (the quiet caveat of V3-07) | False reassurance moves from "captured records" to "reviewed intervals". D3 views | Each reviewed interval shows its reviewer (person, or agent with model and version) and that review recall is not established until E4 measures it | Medium |
| **V4-11 / Clarification** | S §8.7 (L451) | Triggers 2 and 3 fire before consequential reliance | SCIRE cannot detect that people are "about to rely" on an informal decision. The next sentence concedes capture "at that point", after people have started acting on it | An unenforceable promise. D3 | Enforce at SCIRE-mediated consequential acts (finalization, outcome recording, transfer). Informal reliance captured late is recorded with its occurrence time (§7.1) and flagged "acted on before capture" | Medium |
| **V4-12 / Revision** | S §4.4, §6.4, §7.3, §10.1, §4.5 against v0.3 L181, L193–195, L281, L318, L397 | v0.4 drops nothing material without disclosure | Removed with no change-map entry: (i) the statement status vocabulary (open, challenged, supported- or disfavored-under-conditions, withdrawn, superseded), although SCIRE-02 and P2 still refer to "status" and §7.2 asks "why was H rejected"; (ii) "uninstrumented … cannot back a finalized model without upgrade" and the matching package exclusion, so the new upgrade criterion has no consequence; (iii) "a person who asks for removal is de-attributed from derived statements"; (iv) where an argument may stop (assumptions, imported results, declared gap), "the type sets what counts as checking it", and "not forced onto statistical or exploratory reasoning" | Undefined status values; a lost evidence rule; a lost privacy property. The change map does not show the revision is lossless. D1/D3 | Restore each item, or record its removal and the reason in the change map. Suggested: restore a minimal status set or derive status from decisions; restore (ii) as "carried with its label, and not the sole backing of a finalization or published outcome without upgrade"; ask the owner about (iii) | High that the removals happened; medium on their consequence |
| **V4-13 / Clarification** | S §2.6 (L148); I §4 (L132), §5.3 (L154), INT-06 | Eligibility and consequential dereferencing are consistent | An authorized snapshot can satisfy a new use (§4), but I §5.3 and INT-06 require "the owning system's current, applicable record" for publication and interpretation. A snapshot of SSDS result r cannot show that SSDS later downgraded r to *failed* | A publication may cite a since-downgraded result. D3 interoperability | Say which property must be current: the immutable value at revision r can come from a snapshot, but qualification is "as of snapshot time; later changes unknown" and must appear in the claim. Align I §5.3 and INT-06 with the snapshot route | Medium |
| **V4-14 / Clarification** | S §4.4 "material"; §2.3 "overlapping scopes" | Judgments that let a decision through are attributed | Nobody is named as deciding whether an objection is *material*. Calling it immaterial lifts the block without an override (though it still travels, L237). Nobody is named as deciding whether two PIs' scopes *overlap*, so non-overlap can be asserted to avoid scenario S | Unrecorded gatekeeping. D1/D3 | Record materiality and scope-overlap judgments as attributed acts on the decision. A contested overlap is treated as overlapping until resolved | Medium |
| **V4-15 / Clarification** | S §4.2 (L205), §6.4 (L358), §10.2 (L521–522); I §6.2 (L187) | The small exchange contracts agree on meaning | Execution outcomes: S §10.2 has 4 values; I has 5 (adds "known not performed"); S §4.2 mixes a scientific outcome ("null") into execution states. Qualification: S §10.2 has 4; S §6.4 and I have 5 (with "unknown") | The two documents already disagree on what INT-05 says must be agreed | One enumeration, owned by I and cited by S. Keep "null" as a scientific outcome on the investigation, separate from execution outcome | High |
| **V4-16 / Revision (simplicity)** | S §9.2 against I §7.3; S §6.4 against §6.6 | Each rule has one owner | The confidentiality rules are restated in both documents and have drifted: the quarantine authorizer is "project's policy" in S and "receiver's policy" in I, and S has no rule for accepting incoming carried constraints. Usability "under review" (§6.4) duplicates present eligibility (§6.6) | Divergence risk, already realized; extra length. D3 | S §9.2 keeps SCIRE-internal predicates and cites I §7 for cross-system rules. Present eligibility lives only in §6.6 | High |
| **V4-17 / Clarification** | I review boundary (L33), §7.2 (L217), §6.2 package restrictions | The proposal does not amend UPMS or SSDS | "UPMS and SCIRE each adopt this floor", and SSDS is expected to honor constraints carried in packages, while the proposal disclaims amending either system | Cross-system guarantees silently depend on other owners. D3 interoperability | State that guarantees involving UPMS or SSDS hold only after those owners accept the floor. Until then, flows into them are declared gaps | Medium |
| **V4-18 / Editorial** | S §11.1 (L556) | Every proposed surface is defined | "The source-owner manifest for disclosure review (§9.2)": §9.2 defines no manifest | A dangling product surface | Define it in §9.2 (the list of restricted sources and owners in a release set) or remove it | High |
| **V4-19 / Revision (experiments)** | S §15, §11 | The experiments cover the new mechanisms | No study measures the cost of the v0.4 additions: overrides per decision, blocked decisions, disputed resolutions, basis-statement effort, partial-coverage decisions. The D-J prototype (§11) omits §9.2, but nothing says whether the first real inquiry may contain restricted sources | Repairs may be accepted without evidence that they are usable. D3, experiment design | E4 counts blocked decisions, overrides, disputed resolutions and basis effort. The owner states whether the D-J inquiry excludes restricted material; if it does not, §9.2 joins the prototype | Medium |
| **V4-20 / Clarification (minor)** | S §2.3, §7.3, SCIRE-09 | Small gaps | (a) A joint signature should bind the exact decision content, and any change voids earlier signatures. (b) Whether revoking *retention* permission requires deleting or restricting stored derivatives is unstated. (c) An append-only store with permitted deletion means "as SCIRE held then" and decision exposure may be incomplete; SCIRE-09 should say so | Low | State each in one sentence | Medium |

---

## 6. Answers to the request's specific questions

**Objection rule (request §3.2a).**
- "Applies through material dependencies within stated coverage" can be bypassed by recording less structure, and is open-ended if read as transitive (V4-06).
- The larger workability problem is that the rule reaches *every* decision, including inquiry decisions and overrides (V4-05).
- "Resolved by assessment" is an objector-silencing loophole as written (SC-41).
- One repair addresses all three: the basis statement sets coverage, consequential uses are a closed list, and disputed resolutions travel.

**Basis statement and bounded source review (§3.2b).** Proportionate *once* it is limited to the closed list of V4-05 and SCIRE-11 is corrected (V4-04). A paragraph with cited record identities is enough. The source-review escape hatch is honest, because its absence is recorded, and it is cheap. With those two fixes, this adds no new bureaucracy.

**Retention, quarantine and carried constraints (§3.2c).**
- Retention-before-storing is implementable within a system.
- The quarantine contradicts D-I unless source owners authorize it (SC-43).
- Carried constraints are honest about the trust boundary in I §7.4. However, the affirmative empty set overclaims for contexts that are not input-closed (V4-08), and the MCP deployment has no trusted producers at all (SC-43c).
- Over-restriction is labeled, not controlled, and E3 cannot detect it (V4-09).

**Metadata protection (§3.2d).** Yes: honest coverage becomes impossible in one important case. When the coverage gap matters to a *decision*, a generic "covers only what you may see" is honest but not enough to decide on, and any decision-specific limit leaks (SC-42). The repair is existence-independent qualification plus cleared co-signing.

**Availability against eligibility (§3.2e).** No remaining contradiction of substance. The snapshot route needs the currency qualification of V4-13, and I §5.3 and INT-06 should name it.

**Decision kinds and several PIs (§3.2f).** Coherent but not enough. Several acts with decision force sit outside the five kinds: resolution by assessment (SC-41), materiality and scope-overlap judgments (V4-14), and review-obligation closure (V4-07). Making resolution a decision kind and recording the two judgments covers them. Joint signatures need binding to exact content (V4-20a). Conflict between PIs needs a declared escalation authority, or it stays open indefinitely (§8 item 8). Staying open is acceptable, but it should be chosen deliberately.

**Simplicity (§3.3).** S grew from about 7,900 to 10,900 words, and I from about 5,300 to 5,800. Most of the growth maps to findings and is justified: the decision kinds, the tension kinds in §5.3, the three predicates, use history and the time table. What adds cost without closing a finding:
- the duplicated confidentiality rules (V4-16);
- usability's "under review", which duplicates §6.6 (V4-16);
- the objection and basis rules' reach into inquiry decisions (V4-05). This is the largest *operational* cost added, and narrowing it removes cost.

Nothing else is recommended for removal. In one place v0.4 is smaller than it should be: the dropped v0.3 properties (V4-12).

**Experiments (§3.4).** E1, E2 and E4 are decision-relevant as designed: each names the design choice its result would change. E3 is not, because its rule is one-sided (V4-09). None measures the cost of the new objection and authority machinery (V4-19). Stage 0a, tracing the paper counterexamples, is partly done by this review, though only at same-family strength.

---

## 7. Inherited stress cases against v0.4

| Case (v0.3 review §7) | v0.4 behavior | Assessment |
| --- | --- | --- |
| 1. False contradiction | §5.3 kinds and target-relative comparability | Closed |
| 2. Hidden dissent | Acknowledge and defer no longer unblock; capture coverage and source review exist | Residual: SC-41, V4-10 |
| 3. Mistaken secretary | Interpretation, confirmation and adoption | Closed |
| 4. Shared ancestry | §6.3 | Survives |
| 5. Unexpected discovery | Unassessed observations; "arose from" | Closed |
| 6. Scientific retraction | Under-review state blocks new reliance | Residual: V4-07 |
| 7. Private-source derivative | Three predicates, conjunctive restrictions, inheritance, metadata, grants | Residual: SC-42, SC-43, V4-08, V4-09 |
| 8. Temporal ambiguity | Occurrence time, exposure | Closed |
| 9. Broken connector | Availability against eligibility; outcome states | Closed (V4-13 minor) |
| 10. Complexity inversion | Triggers before reliance | New cost: V4-05; unmeasured: V4-19 |
| Publication | Outcome decisions; no renaming as a model | Closed. Whether unresolved objections and overrides must be disclosed *in the external publication* is a human decision (§8 item 5) |
| Multi-year turnover, urgent re-evaluation, shared laboratory evidence, contradictory memories, cross-project discovery | As in the v0.3 review, now with custody kept and adoption | Survive; cross-project discovery inherits SC-42 when access is asymmetric |

---

## 8. Decisions needing human authority

| # | Decision | Why technical reasoning cannot settle it | Recommended framing |
| --- | --- | --- | --- |
| 1 | Who may resolve objections by assessment; whether a decider may resolve objections to a statement they rely on (SC-41) | It allocates scientific authority and accountability | Allow it, but label it "self-resolved"; disputed resolutions always travel |
| 2 | Whether decisions on partial coverage are allowed, and what a cleared co-signer or reviewer may reveal (SC-42) | It trades source owners' confidentiality against decision liveness | Allow with uniform qualification and a cleared co-signer; reveal only what the owner's policy permits |
| 3 | Unknown-lineage policy: refuse, or owner-authorized quarantine; accountable declaration by participants and agent operators (SC-43; S open question 5) | Retention belongs to source owners (D-I) | Accountable declaration as the normal path; refuse undeclared content unless owners grant a quarantine |
| 4 | Over-restriction tolerance for E3 and E4 (V4-09) | It is a cost-benefit limit (D-J) | Set before E3, alongside the leak criterion |
| 5 | Whether unresolved objections and overrides must be disclosed in external publications | Scientific-integrity policy, bounded by confidentiality | Disclose at least their existence where permitted; otherwise qualify the claim |
| 6 | Restore or drop the v0.3 properties in V4-12, especially de-attribution on request | Privacy and evidence policy | Restore (ii) and (iii) unless there is a stated reason |
| 7 | Whether UPMS and SSDS adopt the retention and carried-constraint floors (V4-17) | Those systems' owners decide | Ask through I open questions 1 and 2 |
| 8 | Escalation authority for conflicts between PIs (§2.3) | Project governance | Each project declares one, or chooses explicitly to leave conflicts open |

D-A to D-J stand. No challenge to an owner decision is raised: each Serious Challenge above is a defect in the text that applies a decision, not in the decision. SC-43's repair is the mechanism D-I itself implies (the source owner, including a participant as owner of their own contribution, controls retention).

---

## 9. Revision recommendations

**SCIRE proposal.**
- §4.4 and §2.2: resolution as a decision kind; disputed resolutions travel; self-resolution labeled (SC-41).
- §4.4, §4.5 and SCIRE-03, -11: a closed list of consequential uses; inquiry decisions under "assumed for an inquiry"; the basis statement sets coverage; correct SCIRE-11 (V4-04, V4-05, V4-06).
- §6.6: review obligations close only by reassessment (V4-07).
- §9.2: an accountable declaration path; owner-authorized quarantine; partial-coverage decisions; input-closed contexts; cite I §7 for cross-system rules (SC-42, SC-43, V4-08, V4-16).
- §9.1 and §8.7: reviewer identity on capture coverage; enforcement at mediated acts (V4-10, V4-11).
- Restore or disclose the V4-12 removals; define or remove the manifest (V4-18).
- §15: a two-sided E3; cost measures in E4; whether the D-J inquiry includes restricted material (V4-09, V4-19).

**Interoperability proposal.**
- §7.3 rules 1 and 3, §7.4: owner-authorized quarantine, accountable declarations, partial trusted-producer declarations, and the MCP deployment case (SC-43, V4-08).
- §6.2: the single owned enumerations (V4-15).
- §5.3 and INT-06: the snapshot currency qualification (V4-13).
- §7.2 and the review boundary: state the dependency on UPMS and SSDS acceptance (V4-17).
- §7.5: restore "or block too much" as a criterion (V4-09).

Deliver the revision as new files with their own hashes and change maps. The v0.4 files and this review stay frozen.

---

## 10. Coverage, evidence and limits

**Executed evidence.**
- Full reading of both v0.4 texts, the request, the v0.3 review and the v0.3 hand-off.
- SHA-256 verification of every bound input.
- Direct comparison with the stated v0.3 sections and heading-level comparison elsewhere.
- Targeted greps for dropped or inconsistent terms.
- Constructed textual trajectories.

Nothing was implemented, run, measured or studied. The trajectories are thought experiments, not empirical results. No realized scientific results or gate evidence exist for these proposals, and none were examined.

**Not covered.**
- Full re-reading of the v0.2 texts. Only v0.3 losses were checked, not v0.2 losses beyond what the v0.3 review listed.
- The UPMS and SSDS repositories.
- Legal or policy review.
- Discipline coverage.
- Any user behavior.

The v0.2 interop cache-revocation property (v0.2 §10.4) was checked only through the v0.3 review's description and I rule 8.

**Independence.** This is a same-model review (§2). Its findings may share the author's blind spots, and it may also overcorrect. A reviewer outside the Claude family should treat it as a list of hypotheses to test, not as settled findings.

**Scientific reporting.**
- *Findings:* all material findings are SC-41 to SC-43 and V4-04 to V4-20 (with V4-01 to V4-03 restating the challenges). This review launched no tools or agents beyond file reading and search.
- *Realized results:* none examined; none exist.
- *Variants:* no analysis, model or parameter variants were evaluated or selected. Trajectories were constructed adaptively to challenge the text; they are not pre-specified tests or an exhaustive adversary space.
- *Tensions:* no accepted D1 or D2 authority exists for SCIRE, so no tension search against accepted authority applies. The v0.3 review and the history file were read as candidate evidence.

**Persistence.** These findings are recorded in this file, and `workplans/README.md` indexes it. Nothing has been committed. No proposal, earlier review or history entry was changed.

**Revisit condition.** Re-check each finding against a newly bound revision's body text. Do not close a finding because a change map mentions it.
