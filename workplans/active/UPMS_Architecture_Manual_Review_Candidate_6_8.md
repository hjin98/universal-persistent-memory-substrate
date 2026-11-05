# UPMS Architecture Manual (Review Candidate 6.8)

Nov 5, 2026 · drafted by Claude (AI, Opus 5.5) for @Sam

## 1. Status, Authority and Scope

**Status: proposed D3 architecture, review candidate 6.8; not accepted-current and not implementation-qualified.** UPMS (Universal Persistent Memory Substrate) is a model-independent memory for continuing project work and scientific inquiry by people and agents. It records what was acknowledged (**evidence**: events, observations, received claims, results, references) and what was believed, analyzed and argued (**theory**: hypotheses, arguments, assessments, decisions) on one record model, keeps revisable assessments, shows the standing of each claim without choosing winners, and gives each reader a fast orientation map. It never infers permission from remembered text.

This candidate applies the direction of the theory–evidence proposal v0.1 (owner decisions D-20 to D-36) to candidate 5, which stays frozen as an input (D-23), and concretizes the D1 formulation, now candidate 1.8. Front-end matters, namely discussion, facilitation, the review process and inquiry policy, stay with SCIRE; this manual specifies only the back-end contract for them (§4.4). Proposal §15 item 6, judgment on judgment, is deferred (§9.10). How earlier revisions and reviews shaped this text is change history, not architecture (owner decision D-85): A.1 to A.13 in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md`, A.14 in `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md`, A.15 in `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md`, A.16 in `UPMS_Architecture_Manual_Candidate_6_6_Change_History.md` A.17 in `UPMS_Architecture_Manual_Candidate_6_7_Change_History.md` and A.18 in `UPMS_Architecture_Manual_Candidate_6_8_Change_History.md`, cited below as "change history A.n".

**Revision 6.8 and its files.** Revision 6.8 answers the fourth review of these texts from outside the Claude family (Codex, OpenAI GPT family, the same reviewer as the 6.4 to 6.6 reviews: NO-PASS, Serious Challenges SC67-01 to SC67-03, finding R67-01; repairs C68-1 to C68-6 in change history A.18). Rules marked **pending** apply decisions D-90 to D-93, which the author proposed under the owner's delegation of the review cycle and the owner has not made (§18.2). The review package (D-56) is:
- this **core**: Gate 0 to Slice 2 and every cross-cutting contract;
- the **anonymous-review annex** (`UPMS_Architecture_Manual_Review_Candidate_6_5_Annex_Anonymous_Review.md`): §7.8, §11.5 and their tests, reviewed with the core;
- the **checking annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md`): §5.7, §5.8, the concept-level parts of §5.9, §9.7, §9.8, §9.12 and deferred channel assessment, reviewed before Gate 3;
- the **Slice 4 annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Slice_4.md`): consolidation and maintenance cost, reviewed before Gate 4;
- the **mathematics annex** (`UPMS_Architecture_Manual_Review_Candidate_6_4_Annex_Mathematics.md`), a proposed Slice 3 addition reviewed separately.

The checking and Slice 4 annexes of 6.3, the mathematics annex of 6.4 and the anonymous-review annex of 6.5 are unchanged by this revision and remain part of it; where they name "the core", they mean this core. Section numbers are the core's, and each moved section leaves a stub here.

### 1.1 Inputs and their status

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Theory–Evidence Memory: Structural Proposal v0.1 | `UPMS_Theory_Evidence_Memory_Proposal_v0.1.md`, SHA-256 `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction; owner decisions D-20 to D-36; this candidate is its §14 step 2. Not reviewed |
| Independent review of the proposal (Codex, an OpenAI GPT-6-family AI) | `UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md`, SHA-256 `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | NO-PASS for the exact proposal, support with revisions for the direction; SC-TE01 to SC-TE05 and TE-R01 to TE-R20, dispositions in change history A.8. It arrived during drafting and was untracked in the repository when read |
| UPMS Theory–Evidence Formulation, D1 candidate 1.8 | `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_8.md`, SHA-256 `cbbf2c07b0bfd042952c00a392ad5693f329f39dbd3808445b88571dc30ae1da` | Proposed D1 parent; its F-rules are cited as "D1 F-n". Not reviewed. Its predecessors are listed in its maps I and J |
| Independent review of candidate 6.7 and D1 1.7 (Codex, OpenAI GPT family) | `UPMS_Candidate_6_7_Independent_Review.md`, SHA-256 `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168` | NO-PASS for D1 1.7 and for core 6.7 with anonymous-review annex 6.5; SC67-01 to SC67-03, R67-01; repaired in this revision (change history A.18, C68-1 to C68-6). The same reviewer and family as the 6.4 to 6.6 reviews |
| Proposed decisions D-90 to D-92 | `UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md`, SHA-256 `3a9fd1d4a46f70e115664e8233c6aad4fc07bde86a610a24442bd30ff1ed4236` | Applied here as **pending**; the owner has not made them (§18.2) |
| Proposed decisions D-90 and D-92 amended, D-93 | `UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md`, SHA-256 `3a0741c43d9d71802f99c5cce148bba8ab0c19c33878fc0ce1c87c3640c99d8a` | Applied here as **pending**; amends the 6.6 proposals (§18.2) |
| UPMS Architecture Manual, review candidate 6.7 | `UPMS_Architecture_Manual_Review_Candidate_6_7.md`, SHA-256 `1108d7c496d447ed3886b339dce4f183ddc1ad9c99c2b7e805786c7ac9ada3c0` | Immediate predecessor, unchanged; changes in change history A.18. Earlier predecessors and reviews are listed with their hashes in A.17 and A.18 |
| Owner decisions D-86 to D-89 | `UPMS_Owner_Decisions_6_5_Review_2026-11-05.md`, SHA-256 `8cc6ffc8e9bf89119a92b0500ac4be3fee9775e0d818821bfb30985ee0aa59fa` | Folded in; listed in §18.2 |
| Owner decisions D-79 to D-85 | `UPMS_Owner_Decisions_6_4_Review_2026-11-04.md`, SHA-256 `20144a3a92753313d1163378c3bdf338509a0910962bdb44fd38f458104c9671` | Folded in; listed in §18.2 |
| Owner decisions D-37 to D-46 | `UPMS_Owner_Decisions_2026-11-03.md`, SHA-256 `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Folded in |
| Owner decisions D-57 to D-62 (mathematics) | `UPMS_Owner_Decisions_Math_2026-11-03.md`, SHA-256 `a1f0cce9e6963ef3ebdbc66e5f67ab4eb35fd28b2992d20fe8cdc3f3469b9297` | Direction for the mathematics annex and its hooks |
| Owner decisions D-63 to D-70 | `UPMS_Owner_Decisions_6_2_Review_2026-11-03.md`, SHA-256 `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Folded in |
| Owner decisions D-71 to D-78 | `UPMS_Owner_Decisions_Math_Review_2026-11-03.md`, SHA-256 `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | Folded in; listed in §18.2 |
| UPMS Architecture Manual, review candidate 5 | `UPMS_Architecture_Manual_Review_Candidate_5.md`, SHA-256 `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Base text, frozen (D-23); its own inputs (§1.1 there) reach this candidate through it |
| SCIRE Conceptual Proposal v0.4 | SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md`, SHA-256 `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Theory semantics (§§3–7), through the D1 formulation; front-end responsibilities |
| SCIRE v0.4 same-family re-review | SCIRE repository, `workplans/active/SCIRE_v0.4_Re-Review.md`, SHA-256 `2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e` | Findings mapped in proposal §13.2; dispositions in change history A.5 |
| SSDS 8.0 Architecture Manual (accepted-current in its own repository) | Reached only through proposal §10 | Borrowed mechanisms; SSDS stays outside (D-21) |
| Product owner's decisions | D-1 to D-19 (candidate 5 §18.2), D-20 to D-36 (proposal §0.2) | Status of each in change history A.12; D-37 to D-89 in §18.2; D-90 to D-93 proposed, pending |
| Software Design method | SSDP 7.2.1; no task `protocol_version` assigned | Form of this manual |

**Fixed (proposed)** marks a durable architectural constraint if this candidate is accepted. **Initial default** marks an agent-chosen, configurable starting value under the owner's delegation, not a measured capability or ratified policy. **Unverified** marks claims that need implementation or external evidence. **Proposed (open)** marks a contract the owner has explicitly left open; the text names what governs until it is decided. Defaults never weaken a fixed invariant. Changes to product scope or guarantee strength require D3 reconsideration.

### 1.2 Product boundary

The first journeys, in delivery order (D-30, §16):

- **Project memory:** task resumption and orientation from the overview layer; source inspection and targeted correction; scoped recall, suppression, redaction and explicit deletion; multi-user and multi-agent access under scope permissions, with administration; team coordination through shared memory, including blind and independent work.
- **Scientific inquiry**, through a front end such as SCIRE: recording observations, claims with modality, questions, inference steps, evidence relations with use history, objections and decisions; reading the standing of a claim and a question page; tracing a retraction to what depends on it; fact-checking; the back end of reserved anonymous review; the retention recommendation queue and the archive.

The first deployment is one administrative tenant; cross-organization federation is excluded. Objections whose existence must stay hidden from a target's readers are excluded (D-92, pending). Codex is the first agent integration, as a memory service through MCP; Claude follows after qualifying the same contract independently. SCIRE is the first theory front end. The first product does not accept material that needs derivative containment (embargoed, human-subject or industry-restricted data); such projects wait for the strict profile (D-27, §7.9, change history A.12, C6-14). A project's creator attests at creation that it holds no such material; the attestation is a recorded condition of use, since no detector can enforce the boundary (D-43).

UPMS owns record and state semantics (concretizing the D1 formulation), memory-access permissions, sealed attribution, interfaces, persistence, recovery, concurrency, trust boundaries, resource structure and deployment profiles. External owners keep: identity, group membership and the administrator role; **action safety**, meaning what an agent may do, where it may send things and with what confirmation, which belongs to the agent runtime (D-24); processor accounts and keys; the current state of source applications; model behavior; the discussion process and inquiry policy (SCIRE, D-22); SSDS definitions, results and qualification (D-21). Model or vendor choice is never a storage identity.

### 1.3 Acceptance boundary

Proposal → independent falsification of this exact candidate and of its D1 parent by a reviewer outside the Claude family → product-owner acceptance → bounded implementation specification → implementation acceptance. Requests to refine and choose defaults authorize proposal work, not self-promotion to accepted-current.

The proposal's own sequence was not followed: the owner instructed this draft before the proposal's outside-family review existed. Its acknowledgement, C6-6, is still open (§18.2); the account is in change history A.17.

### 1.4 Domain and inspectability

**A D1 parent is now required.** Candidate 5 needed none because it certified nothing it recorded. Its reopen triggers 1 (source-reliability scores) and 4 (custody of realized scientific records) now fire. The parent is the D1 formulation candidate 1.8, which is unaccepted; this manual must not redefine its meanings and cites them as D1 F-n.

**No D2 parent is required** while the conditions of D1 §9 hold: no numeric score, calibrated confidence or automatic source-assessment mapping; no statistical comparison model or threshold relied on by screening; no consumer relying on a guaranteed approximation bound; no screening, small-model score or adapter output deciding a consequential outcome without confirmation. Any of these reopens the domain determination, and D2 authority is required first.

UPMS is now the custody home for realized scientific records of the projects that use it. It preserves those projects' attribution, findings, uncertainty and the qualification of external results, and it holds no authority over them: a record in UPMS is evidence, never a governing D1–D4 owner for another project.

O1 content: the material realized record, readers and routine questions are stated in D1 §11 for the theory layer and in §17.2 for the whole product; product inspectability surfaces are marked there. No realized scientific results were generated or reviewed in preparing this candidate.

## 2. Terms and Precedence

**Each term below has one owner section; later sections use these meanings exactly.** Scientific meanings are owned by the D1 formulation; this table names where the architecture realizes them.

| Term | Exact meaning | Owner |
| --- | --- | --- |
| Event | Immutable observation by an authenticated capture component; not proof of its contents. An **observation** is an event whose payload is a measured, computed or reported result (D1 Definition 2.1) | 5.1 |
| Claim | An attributed statement or reasoning proposal with a modality, without intrinsic truth or permission (D1 Definition 2.2) | 5.2 |
| Modality | One of asserted, quoted, reported, hypothesized, assumed, defined, predicted, found, intended, committed, preferred, normative | 5.2, 6.1 |
| Statement | Structured form of a claim: concept IDs, typed value and qualifiers, linked to source spans | 5.7 |
| Judgment | Attributed assessment of one target revision under a named scope, ruleset and evidence snapshot; kinds in §5.3 | 5.3 |
| Question | A record of an open problem with live positions and outcomes; organizes records, owns none | 5.10 |
| Objection | A challenge to a claim, inference step, evidence relation, applicability condition or resolution, with handling and resolution kept apart | 5.11 |
| Coordination record | An author-entered control recording a decision, commitment, blocker, ownership claim or interface agreement under a namespaced key, never extracted | 5.4 |
| Decision | A coordination record of kind `decision`, carrying decision kind, decider, authority basis, basis records, dissent, exposure and signatures | 5.4, 6.9 |
| Control record | Typed lifecycle, permission, procedure, sharing, archive, deletion, approval or sealing record | 5.4 |
| Evidence relation | How an observation bears on claims, under a conditioning model and conditions, with a use history (D1 Definition 2.6) | 5.5 |
| Inference step | `{premises; conditions} --[type]--> conclusion`, asserted as an argument (D1 Definition 2.7) | 5.5 |
| Review obligation | A pending reassessment created when a retraction, correction, revision, deletion or definition change reaches a dependent; closes only by reassessment | 5.12, 9.11 |
| Route, standing report | A route is one evidence relation or inference step supporting a claim; the standing report is the read-time projection of D1 Definition 6.1 | 9.9 |
| Concept | Vocabulary entry (entity type, property, value, event type or role) with labels and relations; indexing, never meaning identity | 5.8 |
| Slot | (entity or `same_as` cluster, property): the unit of deterministic comparison | 9.7 |
| Source class | How bytes entered the system (A, R, C, X, M); not authorship proof, truth or action intent | 7.1 |
| Source assessment | Ordinal judgment of a work or non-person channel for a kind of claim; never of a person (D1 §7) | 9.13 |
| Principal | Authenticated human user, agent principal or service principal | 7.3 |
| Agent principal | Persistent agent identity with its own scopes and a human overseer; a channel, not a person | 7.3 |
| Person | A human principal, or a group or institution of humans (D1 Definition 2.14) | 9.13 |
| Home scope, owner | The single scope a record belongs to, and the principal it was captured for | 7.3 |
| Right | One of `read`, `write`, `curate`, `manage` on a scope (D-28) | 7.3 |
| Administrator mode | Explicit, logged exercise of administrator authority | 7.3.6 |
| Ancestry | Immutable production and exposure lineage recorded by trusted capture, release records or approved transforms; used for provenance, impact, independence, lineage exclusion and subject discovery, **never for access** | 5.5 |
| Release record | The record, committed before release, of what UPMS released to an agent session or front-end view; provenance only | 8.2 |
| Sharing | Copying an item into another scope with attribution and provenance; waives nothing, because nothing is inherited | 6.8, 10.6.2 |
| Lineage exclusion | Task-level rule excluding from a context everything whose ancestry includes named sources | 10.6.4 |
| Review chair | The neutral agent or third-party person appointed by the front end for one anonymous or blinded review; the only role that reads that review's sealed attribution | 7.8 |
| Sealed attribution | The true author of an anonymous record, held by the core and readable only through the review-chair role path | 7.8 |
| Review package | A derived view of a work with attribution masked and provenance withheld, for blinded review | 7.8, 10.6.4 |
| Snapshot position | Ordered canonical commit position for an assessment or read | 9.1 |
| Evidence epoch | Monotone revision of a scope's assessment-relevant collection | 9.3 |
| Barrier epoch | Monotone revision used to invalidate cached eligibility after deletion, correction or quarantine | 9.4 |
| Flag, cue | Flag: a screening result for investigation, with cues giving its reasons. Comparison cue: an informational screening output that is not a flag | 9.7 |
| Adapter | Per-scope low-rank weights on a fixed small base model, held as a derived index | 9.8 |
| Hub | A derived overview page (L0, L1 or L2, including question pages) with exact projections, a consolidated narrative and an overlay | 10.5 |
| Consolidation, narrative unit, region | As in candidate 5 §2, without deadlines: regional replay that rewrites a region's narrative; the output of one invocation; one scope's area | 10.5 |
| Coverage | Captured, indexed, processed, structured, screened, traversed and archived extent actually available | 10.3 |
| Archive | The tier of records moved out of default proactive retrieval and overviews by a curator's confirmation; fully retrievable, traversable and reversible | 6.12, 12.2 |
| Retention recommendation | A judgment flagging a record as keep active, archive recommended or delete suggested, with reason and basis; never an action | 12.1 |
| Live record | A record that may not be archived: see the liveness predicate | 12.2 |
| Approval record | An authenticated, scoped control by a role holder, stored with its role evidence; the only way to meet a rule exception | 5.4, 9.7 |
| Language tag | BCP 47 tag and script recorded per source span; detection is a processing output, `und` when unknown | 5.9 |
| Front end | A registered client that runs a process over UPMS records (SCIRE for inquiry; project-memory clients); owns its policies, never the record semantics | 4.4 |

**Precedence.** The strongest applicable restriction wins: deletion and access denial block ordinary use; quarantine permits only its investigation route; correction prevents stale-current use but can permit qualified history; a task's lineage exclusion removes items from that task's context only; archive and suppression remove items from proactive retrieval and overviews only, never from explicit recall, history or standing. Admission never overrides a restriction. Permissions decide who may access a scope; restriction tags and barriers can only narrow that further. Current external policy controls each new decision; historical policy references explain history only.

## 3. Architecture at a Glance

**The mechanism in brief.** Three record types (Event, Claim, Judgment), questions, objections and typed control records live in one memory core with a single committer per tenant partition. Relation families keep meaning and data flow apart: provenance relations drive impact, independence, deletion discovery and recall; evidential and inferential relations carry support under stated conditions; challenge relations carry what bears against. Standing is a read-time projection over recorded judgments, relations and objections, showing status, not winners. Claims carry structured statements over a curated vocabulary, so deterministic code can screen for inconsistency in three channels before an LLM or a person investigates; screening only flags. Four scope rights decide who may read, write, curate or manage memory. A derived overview layer gives every reader a small map whose exact lines are current at read, or marked stale, and whose narrative, labeled as synthesis, is made coherent by consolidation. Front ends run their processes over this engine; agent runtimes own action safety.

```text
SCIRE front end ──records, decisions,──┐        Capture adapter ──events──┐
(discussion, facilitation,  exposure)  │        (authenticates, marks     │
 review process, inquiry policy)       ▼         spans, release records)  ▼
                               ┌──────────────── MEMORY CORE ────────────────┐
  Processing workers ─proposals▶ single committer; permissions; sealed       │
  (extract, screen, impact,    │ attribution; vocabulary; barriers for       │
   consolidate; propose only)  │ deletion, correction, quarantine; outbox    │
                               └──────────────────────┬──────────────────────┘
                                                      ▼ outbox; read-time catch-up
                               Retrieval and projection service
         (eligibility before ranking; indexes; hubs and question pages; standing;
          impact views; review packages)
                                                      │ eligible results, recorded as releases
                                                      ▼
                         Agents (Codex via MCP), people, front-end views

Outside: identity provider and administrator role · agent runtime (action safety)
· processor accounts and KMS · SSDS (referenced, never re-authored)
```
*Figure: One committer owns state; standing is projected, never stored as belief.*

Content enters through capture or a front end with its source classes, is committed only by the memory core, and leaves only through eligible retrieval, recorded as a release.

## 4. Ownership and Interfaces

**Four internal responsibility boundaries own all UPMS state; external owners keep identity, action safety, keys, front-end policy and SSDS authority.** The boundaries are not four compulsory services. In-process code shares one trust boundary: run untrusted parsers, extensions and workers with process isolation when required.

### 4.1 Component ownership

| Component | Owns | Cannot do |
| --- | --- | --- |
| Memory core | Canonical append and transition validation; revision and epoch allocation; barriers; ancestry integrity; scope-permission records and their evaluation; sealed attribution and its role-bound read path; vocabulary records; screening flags; integrity checks on decisions, archive and deletion (§6.9, §6.12, §12.3); purge state; durable outbox | Grant external capabilities; infer external truth; evaluate a front end's inquiry policy; invoke models during replay |
| Processing workers | Bounded execution and proposals (extraction, screening candidates, impact traversal, retention recommendations, overlay notes, consolidation, adapter training), submitted to the core as durable attempts | Write canonical state directly, choose permissive rulesets, lower restrictions, read sealed attribution or promote their own outputs |
| Retrieval and projection service | Disposable indexes and projections: overview hubs, question pages, standing reports, impact views, review packages, per-scope adapters; selection; coverage; explanation; per-reader assembly | Promote a claim by ranking; store standing as belief; bypass permission evaluation or the release record |
| Capture and session adapter | Capture instrumentation and span source marking; session identity; committing release records before each release; lineage exclusions in UPMS-assembled context | Forge provenance, infer authority from content, release without a committed release record |

Canonical ownership and execution responsibility differ: the session adapter produces release records, but the core commits them. Workers and the projection service own no authoritative durable state. The instrumented-runtime components of candidate 5 (handles, checked dispatch, consequence classes, egress mediation for agent actions) are not UPMS components (§7.2, §8.1).

### 4.2 External contracts

| Concern | Owner |
| --- | --- |
| Authentication, principal identity, group membership, the administrator role, delegation, revocation | Identity provider (external). The pilot may use a built-in directory behind the same interface |
| Which memories a principal may read, add to, curate or manage | **UPMS**, through scope permissions (§7.3), evaluated by the memory core and enforced by retrieval |
| What an agent may do with what it retrieved: tools, destinations, confirmations, grounding of action arguments | The agent runtime (D-24) |
| Which processors may receive which scopes' content, and their accounts | Processor policy, bound per scope in UPMS configuration (§7.4) |
| Key lifecycle | Key-management system (KMS) |
| Current state of repositories, trackers, calendars, laboratory systems | Those systems of record |
| Discussion, facilitation, review process, inquiry policy | SCIRE, as front end (§4.4) |
| SSDS definitions, runs, assessments, gate decisions and qualification | SSDS; referenced only (§9.14) |

Unknown identity, membership, scope mapping or processor permission denies the affected use. Membership-cache validity is explicit (§14.2). Memory content can never change permissions, membership or roles.

### 4.3 Typed operation families

| Operations | Caller and guard | Required right | Commit owner |
| --- | --- | --- | --- |
| `record_event`, `record_processing`, `record_release` | Registered capture, session or worker identity for that type | Component role | Core |
| `search`, `get_context`, `expand`, `get_evidence`, `get_overview`, `get_standing`, `get_question`, `get_impact`, `get_history` | Authorized caller, scope and intent; every result is recorded as a release (§8.2) | `read` | Read-only |
| `propose`, `report_conflict`, `request_assessment` | Scoped, quota-limited; never promotes or quarantines | `write` | Core |
| `confirm_interpretation`, `adopt` | Confirmation only by the speaker of the source span; adoption by any principal under its own attribution (D1 Definition 2.3) | `write` | Core |
| `record_question`, `record_inference`, `record_evidence_relation`, `record_use`, `record_objection` | Author; endpoints must exist and be readable by the author; an objection is homed where every reader of its target can read it (§5.11) | `write` on the home scope | Core |
| `submit_assessment`, `submit_screening`, `submit_overview` | Registered assessor or worker, or a human assessor; assigned ruleset; complete attempt; dependency and epoch checks; forbidden inputs are never admitted (§9.3); source assessments only of works and non-person channels (§9.13); a judgment supersedes only its own assessor's earlier judgment (D1 Definition 2.8); never from an anonymous-role session (D-64); an `inspection` judgment only from a human principal, and every `fidelity` judgment records whether its assessor is an agent and whether it authored the rendering (D-73) | `write` (human assessors) or component role | Core computes the allowed transition |
| `record_decision`, `sign_decision`, `record_coordination`, `close_coordination` | Author or decider, with a key from the scope's namespace; decision integrity checks (§6.9); authority basis is a reference the core stores and never evaluates | `write` (`curate` to close others' records) | Core |
| `designate_verifier`, `revoke_designation` | Author, with an authority basis that references the project's rule, stored and never evaluated, as for decisions (§6.9); the subject must be a person (D-75); a designation of the work's author, or made by the designee, is labeled so wherever it counts; no operation computes a person's qualification (mathematics annex, D-32) | `write` on the work's home scope | Core |
| `record_expression`, `record_symbol_context`, `bind_symbol`, `record_derivation`, `record_inspection_scope` | Author; endpoints exist and are readable by the author; a binding names an exact source range; `record_derivation` refuses a cyclic derivation, a step already owned by another derivation, and a claimed discharge that no path to a conclusion supports (D1 Definition 2.7; D-72) | `write` on the home scope | Core |
| `register_tool`, `retire_tool` | Operator; recorded as a control and shown wherever a tool check of that tool appears (D-77) | Operator role | Core |
| `correct`, `suppress`, `redact`, `delete`, `deletion_status` | Target-specific authority; subject ambiguity stays explicit; effect preview before `delete`, listing the target's unresolved objections, which stay unresolved (§12.3, D1 F-3b); a reason and a deletion marker for others' standing-bearing records (§12.3, SC-61) | Own items: `write`; others' items: `curate` | Core |
| `archive`, `unarchive`, `pin` | Confirmation of a retention recommendation; liveness check by the core (§12.2) | `curate` | Core |
| `share`, `withdraw_share` | Own items: owner; others' items: a curator of the item's home scope | `write` on the target, plus `curate` on the home scope for others' items | Core |
| `endorse`, `revoke_endorsement` | Exact object, type and use capability | `read`, plus the endorsement capability | Core |
| `approve_procedure`, `activate_procedure`, `suspend_procedure`, `revoke_procedure` | Exact version; distinct approval and activation authority | `manage` | Core |
| `quarantine`, `release_quarantine` | Policy-authorized detector or investigator; bounded scope; reason | Investigator role | Core |
| `create_scope`, `get_permissions`, `set_permissions`, `transfer_ownership`, `explain_access` | Scope manager or administrator | `manage` (`read` for `explain_access` on own access) | Core |
| `enter_admin_mode`, `end_admin_mode` | Holder of the administrator role; reason | Admin role | Core |
| `propose_concept`, `curate_concept`, `record_meaning_link` | Extractor or principal; curator; meaning links by any author | `write` to propose or link; `curate` or `manage` to curate | Core |
| `promote_adapter` | Registered training worker after the promotion gate | Component role | Core |
| `open_sealed_review`, `record_chair_appointment`, `submit_sealed`, `record_block`, `record_appeal`, `sign_sealed`, `read_sealed_attribution`, `check_conflict` | The front end that opened the review (D-52); sealed reads and conflict checks only through the review-chair role of that review (§7.8) | `write` on the review's scope; chair role for sealed reads | Core |
| `recall`, `export`, `import` | Operator or caller capability; scoped disclosure and migration validation | `read` on exported scopes; `write` on import target; investigator role for recall | Core for imported records; recorded release otherwise |
| `record_approval`, `revoke_approval` | Re-authenticated principal holding the named role; exact scope, rule and action | The role, plus `write` on the scope | Core |

No API accepts caller-chosen effective labels, admitted state or standing, and no content changes a permission. Model assertions, conflict reports and recommendations are data. A trusted detector may impose a quarantine under policy; arbitrary claims of contamination cannot quarantine another user's corpus. Every mutation has a principal- and tenant-scoped request identity, an expected revision where applicable, and same-request, same-payload idempotency; reusing an identity with different arguments is an explicit conflict. MCP and other transports are adapters over this typed interface and inherit its authentication and scoping. Candidate 5's `publish`, `confirm_publication`, `elevate`, `prepare_dispatch` and `record_dispatch_outcome` are retired (change history A.1).

### 4.4 Front-end contract

**A front end runs a process over UPMS records; UPMS guarantees what those records mean, whatever any front end does.** **Fixed (proposed).**

| Responsibility | Owner |
| --- | --- |
| Meetings, facilitation, the secretary's proposals, independent critique, crux maps, compass and question views | SCIRE (front end) |
| Inquiry policy: the objection rule, basis statements before consequential use, finalization, scoped PI authority, overrides, joint sign-off rules, materiality and scope-overlap judgments | SCIRE |
| The reserved anonymous review process: requesting and appointing a review chair, choosing the mode, running rounds of critique and reply, deciding to block and return a personal attack, hearing appeals | SCIRE (D-33 to D-36) |
| The discrepancy workflow and comparability elicitation; model-package hand-off to SSDS | SCIRE |
| Records, relations, judgments, standing, screening, impact traversal, source assessments, overview, retrieval, provenance, permissions, sealed attribution, review packages, independence accounting, retention recommendations and archive | UPMS (back end) |

**How a front end writes.** A front end is a registered client acting for authenticated principals. Each record it submits is attributed to the human or agent principal who made it; the front end is recorded as the transmitting channel (`transmitter_identity`, §5.1), never as the author. The secretary's proposals are inert claims of modality-preserving kind, attributed to the proposing agent as interpretations, until confirmed or adopted (§6.1).

**What the core checks, and what it does not.** The core checks integrity: that endpoints exist and are readable, that attribution is authentic, that a confirmation comes from the speaker, that a decision's signatures bind its exact revision, that its exposure identifies real release records, and the D1 rules a record must not break (§6.9). The core never evaluates whether a decision is permitted, whether an objection is material, who may resolve it, or whether a finalization may proceed. It never refuses a decision for policy reasons, nor because an objection exists or arrived late (§6.9, D-50). A front end that owns a decision policy may ask the core to enforce, atomically at commit, the structural preconditions its policy result names (exact content, required signers, expected basis revisions); the core enforces them without evaluating the policy (§6.9).

**Back-end invariants a front end relies on** are TE-01 to TE-15 (§15), realized as follows:
- modality and act state survive every rendering (§6.1, §10.3);
- every unresolved or disputed objection in the applicable set of a decision (D1 F-6) appears with every projection of that decision, whatever its handling, mode or archive state (§9.9);
- a front end may widen the applicable set for its views; no front end narrows it;
- anonymous objections are recorded with their mode at each time, so a front end can apply D-36 and an auditor can check that it did; the back end itself blocks nothing, and anonymous sessions submit no judgments (§5.11, D1 F-8, D-37, D-64);
- history is append-only, and "as held then" is answerable (§9.9);
- discovery links, views, flags, recommendations and source assessments are never support.

**Other front ends.** Ordinary project-memory clients (task resumption, coordination, personal recall) use the same engine without the theory layer: claims, judgments, questions and objections are optional for basic recall (§17.3).


## 5. Durable Records

**Three semantic record types (Event, Claim, Judgment), questions, objections, review obligations, typed controls, processing records, one typed relation store, structured statements on claims, and a versioned vocabulary make up all canonical state.** Schemas specify meaning; serialization is D4. **Annex record kinds (hook H7).** The mathematics annex adds exactly four typed records over events and claims: expressions, symbol contexts (a model is a symbol context of kind `model`), derivations and inspection scopes. Each carries the common fields below, follows §7 and §12 like any record, and carries no assessment; assessment of them lives only in judgments. Any further record kind reopens this section (same-family review FM-R17). Release records are typed operational records, not a second knowledge ledger.

**Common fields:** opaque logical ID and immutable revision ID; tenant; **home scope**; **owner**; schema version; commit position and time; source classes; restriction tags (narrowing only, §7.4); archive state (§6.12); sealing reference where the author is sealed (§7.8). Fields that contain content or identifying metadata are protected payloads even when stored in a database column. Labels, locators, usernames, relation endpoints, query text, concept definitions and error text are not presumed public. Candidate 5's retention-policy version and deadline and requirement-closure reference are removed (D-24, D-25).

### 5.1 Event

```text
Event {
  channel, witness_principal, transmitter_identity?     // a front end is a transmitter, never the author
  origin_identity?, origin_authentication_evidence?
  payload_ref
  spans: [{range, source_class, language, script, notation?, origin_ref?}]   // notation: latex (H2)
  source_namespace, source_message_id?, source_revision?
  observed_at, stated_occurrence_time?, prior_revision?
  external_reference?: {system, record_id, revision, stated_qualification, snapshot?}   // §9.14
}
```

Only capture appends observations. An agent's claim of completion is an observed statement; actual completion needs a receipt or inspected artifact. Changed source bytes create a revision. The authenticated source namespace is part of identity, so IDs from separate connectors cannot collide. **The event's original text is the record; everything structured is derived from it.**

An **observation** is an event whose payload is a measured, computed or reported result. Its observation claim (§5.2, modality `found` or `reported`) carries, where known: value, unit and uncertainty with its type; conditions and regime; instrument, code or method; origin, qualification and observation time (D1 Definitions 2.1, 2.9). An observation exists, can be found and is listed as **unassessed** before any evidence relation points to it.

### 5.2 Claim

```text
Claim {
  statement_ref, source_locators[]
  statements[]                 // structured statements, §5.7; may be empty
  modality                     // §6.1; the D1 set
  conditions?, regime?, time_scope?, qualifications
  asserted_by?
  act: direct | interpretation{span_refs, extractor} | adoption{of, check_ref?}
  confirmation?                // speaker's confirmation record, for an interpretation
  synthesis: bool              // a facilitator summary, overlay note or narrative-derived claim
  subject_kind?                // person, when the claim judges a person (§9.13)
  valid_time, temporal_basis, generated_by
}
```

A model's structuring does not prove extraction fidelity. Negation, quantity, units, conditions, attribution and uncertainty are preserved, or the claim stays a source-linked textual claim. Original wording is recoverable while retained and authorized; otherwise an explicit deletion or unavailability marker is returned, never a fabricated substitute.

**Interpretation, confirmation and adoption are separate attributed acts** (D1 Definition 2.3). An interpretation is attributed to its extractor and shown as "interpretation, unconfirmed" until its speaker confirms it; the core accepts `confirm_interpretation` only from the principal who is the speaker of the cited span. An adoption is a new claim, attributed to the adopter, linked to the interpretation, which stays unconfirmed.

### 5.3 Judgment

```text
Judgment {
  target_revision, kind     // claim | evidential | inference | comparability
                            // | objection_resolution | source | retention_recommendation
                            // | fidelity | inspection          (mathematics annex, H1)
  scope, ruleset_version, validity_interval?   // unbounded when absent
  epistemic_status?         // supported | refuted | contested | unknown
                            // | supported_under(conditions) | disfavored_under(conditions)
  result?                   // per kind: usability, validity, comparability outcome,
                            // ordinal source value, retention flag with reason,
                            // fidelity result, inspection depth and outcome
  assessor_is_agent, assessor_authored_target   // recorded for fidelity (D-73)
  admission_state           // captured | evidence_only | admitted | quarantined
  supporting_refs[], opposing_refs[], qualification_refs[]
  assessor, assessment_output_ref?, processing_ref
  read_dependencies[], evidence_scope_epochs[], snapshot_position
  applicable_time, supersedes?     // only the same assessor's earlier judgment
}
```

Each ruleset defines qualifying support and opposition, correlated-source treatment, missing evidence, its domain and admission criteria. Copies of one source are not independent support; model confidence is not evidence. The status vocabulary restores the conditioned values that SCIRE v0.4 dropped (re-review V4-12).

Judgments in different scopes or rulesets coexist. Within one target, scope and ruleset lineage, replacement names the prior head, is made by that head's own assessor, and is checked atomically; a judgment by another assessor is a concurrent head, never a replacement, so concurrent disagreement is never resolved by last write (D1 Definition 2.8; same-family review F62-01). `fidelity` and `inspection` judgments are separate statuses: route status never reads them, and an inference assessment's basis never cites them (D-70). The initial policy returns authorized conflicting judgments with their scopes and leaves them unresolved; there is no cross-scope most-permissive selection.

### 5.4 Controls and processing

Controls: correction, suppression, quarantine, redaction, deletion and deletion markers, endorsements, procedure versions and activation, policy references, **scope-permission revisions, administrator-mode records and access records, sharing, archive and unarchive, pins, vocabulary changes, adapter promotions, overview consolidations, coordination records (including decisions), approval records, sealing records, de-attribution requests, restore records (§12.4), verifier designations (H5) and tool registrations (D-77)**. Their state is derived from validated appended transitions.

**Coordination records** (decision D-15) carry what a team must see at once, without extraction:

```text
CoordinationRecord {
  kind      // decision | commitment | blocker | ownership_claim | interface_agreement
  key       // task, topic, interface or commitment identifier
  value, author, scope, due?, supersedes?
  status    // open | superseded | fulfilled | released | withdrawn  (§6.9)
  decision?: {                                  // kind = decision
    decision_kind      // inquiry | outcome | finalization | override | external | resolution
    decider, authority_basis_ref                // a reference to the project's rule, never inferred from rights
    purpose, effective_interval
    basis_statement_ref, basis_records[]        // cited by identity; the coverage boundary, D1 F-6
    resolves?                                   // objection refs, for decision_kind = resolution
    overrides[], qualifications[], dissent[]
    exposure_ref                                // release records and as-of positions of the views shown
    signatures[]                                // each bound to this exact revision
    status        // reported | recorded | validated{policy_ref, policy_revision,
                  //   authority_evidence_ref, required_signers[], expected_revisions[],
                  //   applicable_position, signature_state: awaiting | complete}  (§6.9)
  }
}
```

They are entered by their author through `record_coordination` or `record_decision`, never extracted, and state what was recorded, not admitted facts. **Keys are namespaced:** a key is either an identifier from a system of record (an issue, a repository path, an interface name), qualified by that system, or an entry in the scope's key registry, a scope-content list of keys with labels per language that any `write` holder may extend and `curate` holders curate. At entry the author is shown open records of the same kind whose keys are similar, in scopes the author can read, and chooses to reuse a key, supersede a record or create a new key; similarity comes from labels, normalization and retrieval, and is an inert proposal. A new key similar to an existing open key of the same kind adds the cue `possible_duplicate_key` to both records, visible only to readers who can read both; it is never a conflict (§6.9). A commitment has one authority: an extracted Claim with `modality: committed` that carries an explicit reference to an open coordination record's key links to it and never opens a second obligation. **Approval records** are authenticated, scoped controls made by a principal holding the named role at commit time, stored with the role evidence the identity provider returned; they are the only way to meet a rule exception (§9.7).

The decision fields are what a front end needs (proposal §3.5, SCIRE v0.4 §2.2); the kind `resolution` records an objection resolution by assessment with the same authority, basis, exposure and dissent as any decision (D1 F-3, re-review SC-41).

```text
ProcessingRecord {
  kind, invoker, input_manifest_ref
  model_or_program_version, prompt_or_program_ref, configuration_ref
  output_ref?, outcome    // completed | partial | failed | cancelled | uncertain
  started_at, completed_at?
}
```

Attempts and outputs are separate immutable records. A timeout or crash never synthesizes completion. Reprocessing has a new identity. Required programs, transformations, reducers, vocabulary versions and screening versions stay available for replay of surviving records. The input manifest of a UPMS model invocation records the processor account and endpoint, every input revision with its source class and restriction tags, the vocabulary, adapter and hub versions, the lineage exclusions in force, the policy references, the snapshot position and the input coverage (restored from candidate 5 §11.1; A.3 check U5). It is committed before submission (§8.4); it is the evidence of what a model output could depend on, which independence (D1 F-19) and impact traversal (§9.11) use.

### 5.5 Relations and ancestry

**Relation families keep what a record was made from apart from what it means.** **Fixed (proposed).**

| Family | Relations or records | Semantics | Traversed as support? |
| --- | --- | --- | --- |
| **Provenance** | `observed_from`, `exposed_to`, `generated_by`, release records (§8.2) | What a record was made from or exposed to | No. Used for impact, independence, lineage exclusion, decision exposure, recall and deletion discovery |
| **Evidential** | Evidence relations of D1 Definition 5.1, each with conditioning model, conditions, use history and binding | How an observation bears on claims | Yes, as assessed (§9.9) |
| **Inferential** | Inference steps of D1 Definition 2.7 | Support from other claims | Yes, as assessed |
| **Stated content** | `stated_reason`, `condition`, `exception` (§5.7.2) | What an asserter said, as claim content | **No.** A stated reason becomes an inference step only when someone asserts it as an argument |
| **Challenge** | Objection → target (§5.11) | What bears against | Against |
| **Refinement** | `refines`, `concretizes` (from SSDS) | A more specific or concrete form of a claim; a challenge to the concrete form may be routed to the abstract one by an attributed act | Conditional, as assessed |
| **Meaning** | Meaning links of D1 Definition 2.12, default *unresolved possible match*; `renders` (claim → its structured or formal rendering), assessed only by `fidelity` judgments (H6); bindings (an exact source range → a symbol definition, an authored interpretation until confirmed or adopted; mathematics annex) | Attributed, contestable sameness of meaning | No |
| **Discovery** | `arose_from` | Why something was pursued | **Never** (D1 F-26) |
| **Identity** | `same_as` between entities (§5.6) | Reversible scoped entity match | No |
| **Lifecycle** | Validated controls with `supersedes` and `retracts` | Only an authorized transition changes current state; an agent-proposed link is inert | No |

Every relation names its author, exact endpoint revisions, scope, locator and lifecycle status (active, replaced, retracted), and is itself a target for objection. A step or relation replaced through `supersedes` is a revision for carrying objections when it keeps its conclusion, or its observation and targets (D1 F-3a; same-family review F62-05). Its assessment lives only in judgments that target it; no relation carries an editable assessment status of its own (TE-R10).

**Inference-step fields** (hook H3). An inference step may carry `step_rule` (the rule it applies), `introduces[]` and `discharges[]` (hypotheses it introduces or discharges within its derivation, D1 Definition 2.7) and `approximation{order, validity}`. They are recorded data, and no field is a computed score. A step belongs to at most one derivation. The projection computes, for each conclusion and by reachability over the owning derivation, which hypotheses are discharged for it and which remain carried conditions, together with the declared model relations it uses (D1 Definition 2.7, §6.1; D-70 to D-72).

**Ancestry.** Provenance edges are object → prerequisite-revision references. A model output depends on its manifest's complete inputs; a write from an agent session is `exposed_to` everything UPMS released to its session (§8.2); a hub depends on every item it summarizes; an adapter depends on every record it was trained on. Ancestry edges form a DAG over immutable production revisions. Cycles, nonexistent references and foreign-tenant edges are rejected. Ancestry is never removed while any descendant survives (§11.2); explicit deletion of a node purges its content and keeps its opaque edges for as long as descendants need them.

**Ancestry is not access.** Candidate 5 derived access requirements from ancestry (requirement closure, decision D-6). In the default profile nothing is inherited: a record is governed by its own home scope and restriction tags (§7.3.5). Lineage exclusion, impact traversal, independence accounting, decision exposure and subject discovery always traverse ancestry. Evidential and inferential relations may be cyclic; they are traversed with visited sets and limits, and a cycle is a flag (§9.7), never a warrant (D1 F-25). Missing provenance, incomplete coverage or a traversal timeout is never proof of independence: the affected result says so.

### 5.6 Identity, time and scope

IDs are opaque, stable and never reused. Digests are separate protected integrity data, tenant-scoped and erased with payloads; no durable plaintext hash of a sensitive value. Entity matching is a reversible scoped `same_as` assessment, never a physical merge or an access grant.

Bitemporal records distinguish transaction order from valid time, durations from uncertain occurrence intervals, and unknown from exact time. Relative expressions keep raw wording, source timestamp, timezone if known and resolution basis. Reprocessing temporal interpretation creates a new assessment. A claim's `time_scope` states when a statement about a time-dependent phenomenon claims to hold; it is distinct from valid time of the record and from observation time.

### 5.7 Statement language

**In the checking annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md`, §5.7; Slice 3; reviewed before Gate 3). In brief: structured statements over the curated vocabulary, used only for screening.

### 5.8 Vocabulary registry

**In the checking annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md`, §5.8; Slice 3; reviewed before Gate 3). In brief: the curated vocabulary of concepts with multilingual and contested labels; proposals are inert until curated.

### 5.9 Natural languages

**One vocabulary serves every language, and the original words are always the record.** Memory may be written in any language, and one message may switch languages. Meaning is carried by language-neutral concepts, while evidence stays in the words as written (decision D-19). **Fixed (proposed).**

- **Original text is the record.** Events keep their bytes as written; Unicode normalization (NFC, locale-aware case folding and width folding) applies only to indexes. Each span carries a BCP 47 language tag and script, detected per span as a recorded processing output with its confidence, `und` when unknown, and correctable like any extraction. Citations always point to the original span in its original language.
- **Names are not translated.** People, products and places are entities whose aliases record script and transliteration (東京, Tokyo); identity still follows reversible `same_as` (§5.6).
- **Retrieval.** Lexical indexes use a per-language analyzer (word segmentation for languages written without spaces, such as Chinese, Japanese and Thai; stemming where it helps), with a character n-gram fallback for other languages and `und`. Vocabulary expansion bridges languages: a query term expands to its concept and then to that concept's labels in every pilot language. Embeddings come from a multilingual base model (§9.8). Coverage reports a language without an analyzer or vocabulary labels as degraded, never as “none found”, and reports the share of spans recorded as `und` and the spread of detection confidence, since a misdetected span is analyzed with the wrong analyzer.
- **Translation is never authority.** A translation is never evidence for admission and is never offered as the value of an action argument (§7.2); only the original exact value is. Sending text to a model or external service for translation is processing and, outside UPMS, disclosure: processor policy, purpose and restrictions apply (§7.4, §8.5).
- **Pilot languages.** The base vocabulary carries labels for the pilot languages (§14.2). Other languages are stored, cited and retrieved by n-grams and embeddings, and their structuring is reported as unavailable.

**Concepts, curated equivalence, typed values and formats, rendering for readers and spoofing checks** are Slice 3 and are in the checking annex (§5.9 there).

### 5.10 Question

```text
Question {
  problem, scope, kind            // ordinary | discrepancy
  positions[]                     // claim refs: the live alternatives
  status                          // open | closed_answered | closed_unresolved | closed_unproductive | split
  outcomes[]                      // claim or decision refs
  arose_from?                     // discovery link
  linked_questions[]              // shared root cause or discriminating test; never merged
}
```

Questions organize records; they do not own them. An observation or claim can exist without a question, and one claim can be a position in several questions. Ordinary project memory uses questions too: candidate 5's L1 hubs already listed "open questions". Opening, splitting, linking and closing are attributed acts; a closure is a decision of kind `inquiry` or `outcome` (§5.4) and carries its dissent.

### 5.11 Objection

```text
Objection {
  target       // claim | inference step | evidence relation | applicability condition | resolution
               // | other relation (a renders link, a binding) | observation (a tool check)   (D1 Definition 2.5)
  ground, author                    // author may be sealed (§7.8)
  handling     // open | acknowledged | deferred | answered{answer_ref}
  resolutions[] // per binding: resolved_by_assessment{decision_ref, binding} | withdrawn{binding} (by its author only)   (D1 F-3; D-93, pending)
  target_state // current | carried{from_revision} | target_withdrawn   (D1 F-3a, F-3b)
  bindings[]   // first target, then every carry and rebind, with positions; append-only   (D1 Definition 2.5; D-91, pending)
  mode_history[]                    // open | single_blind | double_blind, with intervals; signed_at?
}
```

**Handling describes workflow; none of its states resolves an objection.** An objection without a resolution is **unresolved**, whatever its handling (D1 Definition 2.5, P3). **Nothing that happens to the target resolves it.** A revision carries the objection to the successor (D1 F-3a, §6.10, D-47). A retraction, withdrawal or deletion of the target by its author leaves it unresolved as "target withdrawn, not re-examined", live and shown on the target's marker and on every question page where the target was a position (D1 F-3b, D-63). An objection whose target is a resolution is a **dispute** of it; every claim the original objection applied to then shows "resolved by assessment, disputed", with both records (D1 F-4).

**Where an objection lives** (D-80, D-87; Codex reviews SC64-03, SC65-02). The **possible homes** of a record are its home scope and every **objection home** registered, now or earlier, for a scope among its possible homes, so registration is transitive (D-90 as amended, pending; Codex review SC67-01). An objection home is a review scope opened to review a scope's work, or another scope registered by a holder of `manage` on the registering scope as an attributed configuration revision, whose readers include every reader of the registering scope at registration. An objection is homed in a possible home of its target; `record_objection` refuses any other home. A critique written somewhere else is an ordinary note about the target, not an objection, and it neither travels nor applies. An outside critic writes through a contributor right (`write` without `read`, §7.3.3) or a review scope opened for the purpose. A holder of `manage` may retire a registration; a retired home stays among the possible homes, so retiring one never removes the coverage statement. **An objection carries no restriction tag of its own:** it is readable by a reader who reads its home and satisfies the restriction tags of the binding through which it applies (§7.4; D-91, pending). A critic with sensitive material puts it in a separate tagged record and cites it in the ground, where it shows as a private source. **The existence of an objection is not promised confidential** (D-92 as amended, pending; Codex review R67-01): no mechanism beyond the ordinary access rules hides its existence, time or unrestricted ground from a target's readers; those rules still decide what each reader receives, and the coverage statement covers what they withhold. Objections whose existence must stay hidden from a target's readers are outside the first product (§1.2).

**Resolutions and disputes** (D-90 as amended, D-93, pending; Codex reviews SC66-01, SC67-01, SC67-03). A `resolution` decision resolves objections **at named bindings** (D1 F-3) and is homed in a possible home of every binding it names; one whose bindings share no possible home is split. A dispute of a resolution is an objection to it, homed in a possible home of the resolution. Neither carries a restriction tag of its own. `record_decision` and `record_objection` refuse any other home. **Why coverage closes.** Let `t` be a record in a footprint. An objection with binding `t` is homed among `t`'s possible homes; a resolution of it at `t` is homed among them; a dispute of that resolution is homed among the resolution's possible homes, which, registration being transitive, are among `t`'s; and so on at every depth. So every objection in D1 F-6's neighbourhood reached from `t` is homed among `t`'s possible homes and readable by a reader who reads all of them and satisfies `t`'s tags, unless a lineage exclusion applies. Each of these cases triggers the coverage statement below, which is therefore sufficient.

**Audiences can drift after an objection is recorded:** a reader may lose access to a scope while still reading their own record (§7.3.4), a scope may be widened, or an objection home narrowed. The core never refuses such a permission change because of objections. Instead, every projection carries the coverage statement of D1 F-7a, "objections you cannot read may apply", computed over the projection's reliance footprint (D1 F-6): whenever its reader cannot read a record in the footprint, does not read every possible home of that record, or works in a task with a lineage exclusion (§10.6.4). Where the record is the original of a sharing copy, the statement reads "shared copy: objections to the original may not be visible to you" (D-88). The conditions depend only on access, the task and configuration, never on whether an objection exists, so they reveal nothing. A rebind (§6.10) is refused unless the objection's home is a possible home of the new target and every current reader of the new target, including readers through an own-record entitlement, can read it (D-88). Which objections apply is D1 F-6's footprint and neighbourhood, nowhere restated. The proposal's claim that no hidden applicable objection arises within a project (proposal §13.2, SC-42; change history A.12, C6-4) holds in this form: an applicable objection a reader cannot read is never silent.

Who may resolve an objection, what an unresolved one blocks and whether an anonymous one may block (it may not, D-36) are front-end policies. That an objection and its state appear wherever its target is relied on is a back-end invariant (TE-04).

**What "never blocks" means** is D1 F-8 (D-36, D-37, D-38, D-50, D-64); the core's own consequence is §6.9's: it never refuses a decision because an objection exists or arrived.

### 5.12 Review obligation

```text
ReviewObligation {
  dependent                     // a route (evidence relation or inference step) or a claim revision
  cause                         // retraction | correction | inapplicability | definition_change
                                // | claim_revision | input_deleted | rendering_diverges (D-74)
  cause_ref, traversal_ref      // the impact traversal that created it (§9.11)
  assignee
  state                         // pending | closed{reassessment_ref}
  qualifications[]              // explicit qualifications used while pending; they travel like overrides
}
```

An obligation closes only through an attributed reassessment of the dependent's usability (D1 F-34). Assigning, acknowledging, answering or archiving it does not close it.

## 6. Lifecycles

**Every lifecycle change is an appended, validated control record; current views are projections, never separately editable facts.** Ordinary transitions append; payload erasure on explicit deletion is the physical exception (§12).

### 6.1 Modality projections

| Modality | Lifecycle contract |
| --- | --- |
| asserted | Applicability and freshness are separate from superseded or retracted status; either can change without passing through a mandatory stale state |
| quoted, reported | Fidelity of the quotation or report and the inner claim are distinct; either can be corrected without accepting the other |
| hypothesized | Open or abandoned investigation; supported, refuted, contested or unknown comes only from Judgment |
| assumed | Adopted for a stated inquiry; never shown as asserted outside it; may be withdrawn by its adopter |
| defined | In force within its scope until superseded; establishes no truth or existence; a change of definition creates review obligations (§9.11) |
| predicted | Carries the conditions it covers; succeeded or failed only through an evidence relation and its assessment |
| found | The recorded outcome of an investigation; its standing still comes from Judgment |
| intended | Active → completed, abandoned or superseded, with an authorized statement or completion evidence |
| committed | Open → fulfilled, released or superseded; overdue is a time-derived flag on an unfulfilled commitment, not a terminal state |
| preferred | In force → superseded or withdrawn by the same principal within the applicable scope |
| normative | Historical reference plus applicability from the actual authority source; memory cannot enact or repeal policy |

**Modality survives every copy, summary, projection, translation and export** (TE-02, D1 F-1). Rendering code takes modality and act state from the canonical claim, never from the rendered text, and a rendering that cannot carry them withholds the claim. An unconfirmed interpretation is never rendered as the speaker's assertion. No completion, cancellation or release is inferred from retrieval decay. Scope policy defines who may release a commitment; a model cannot invent a counterparty's approval.

### 6.2 Assessment, admission and quarantine

No judgment means captured. A completed authorized assessment produces evidence-only or admitted under the assigned ruleset and §9.3. New evidence or rule changes invalidate current admission until revalidated; old judgments remain historical.

Quarantine is an access restriction layered over assessment. Removing it removes only that restriction, then recomputes current admission, authority and freshness; it never blindly restores a previous admitted state. Authorized investigation is isolated with restricted egress. Ordinary users may report a concern, not rewrite another principal's admission state.

### 6.3 Correction

`requested → applied | proposed_to_owner | pending_clarification | rejected`; pending requests may be clarified or withdrawn.

- A principal can retract or correct their own attributed statement (`write`). A retraction is first shown the target's unresolved objections, which stay unresolved (D1 F-3b).
- A correction to someone else's source is proposed to its owner, or applied by a curator (`curate`) as a correction attributed to the curator; the original remains in history.
- A request about an agent-generated claim concerning the requester may correct that claim under scope policy, but cannot erase independent third-party sources.
- Verified non-user correction uses the deployment's identity and visibility process.

The interface presents the exact event, revision and spans or claim, the scope and the effect. Ambiguous requests stay visibly pending; any provisional restriction is limited to already-authorized targets. An applied correction atomically appends the replacement or retraction, invalidates current dependents (including affected statements, flags and hub lines) and establishes the barrier in §9.4. Historical recall may show the old version explicitly paired with its correction. Correction never claims erasure.

### 6.4 Endorsements

`presented → valid → revoked | expired`; new bytes or a new use require a new endorsement. An endorsement binds object revision, field or claim, type, meaning, scope, intended use, endorser, current policy decision and validity conditions. Types: extraction fidelity, factual attestation, permitted reliance. None changes provenance, confidentiality or general action capability. Revocation invalidates future reliance and schedules dependent reassessment and recall. A historical endorsement remains a historical fact, not current permission.

### 6.5 Procedures

`draft → approved → active → suspended | revoked`; a suspended version needs fresh authorized activation to resume. Any edit is a new draft. Approval binds exact bytes; activation (`manage` on the scope plus current authority) binds scope and applicability. Loading and each consequential use recheck revocation. No procedure grants a tool capability. Agent proposals and imported procedures are inert until independently activated.

### 6.6 Suppression

`active ↔ lifted` by an authorized scope principal (`curate`, or `write` for own items). Suppression blocks proactive surfacing only; explicit authorized recall still returns the item with its status. It does not alter truth, admission, access, retention or deletion.

### 6.7 Permissions and administrator mode

| Transition | Guard | Effect |
| --- | --- | --- |
| Grant or widen | `manage` on the scope, or an administrator in administrator mode, within §7.3.6's limits; never on an agent's private scope | New permission revision; effective immediately |
| Narrow, remove member, transfer ownership or oversight | `manage`, administrator mode, or identity-provider membership change | New permission revision; effective for every read that starts after its commit; cached decisions expire within the cache bound (§14.2) |
| Administrator mode entered | Administrator role; reason; scope | Mode record; an access record for every content access during it (§11.4) |
| Administrator mode ended | Explicit end, session end or role revocation | Mode record |

Candidate 5 fenced permission narrowing like a deletion barrier. That fence leaves the default profile with the rest of the release-fence machinery (proposal §8.2); deletion, correction and quarantine keep it (§9.4).

### 6.8 Sharing

`shared → superseded | withdrawn`. Sharing creates a new attributed copy in the target scope with an ancestry link to the original and the original's attribution, source classes and modality (§10.6.2). It waives nothing, because nothing is inherited. Superseding names the revision being replaced and is recorded as a conflict if that revision has changed. Withdrawal is a retraction in the target scope; readers who already saw the item are not "unseen". **Objections travel to copies** (D-80, D-86, D-88): objections to the original, and to every earlier original in a chain of copies, apply wherever the copy is relied on (D1 F-6), and a copy's reader who cannot read where they may be homed sees the shared-copy statement of §5.11. Sharing checks no audience beyond the rights of §10.6.2 and is never refused because of objections. Candidate 5's publication, owner confirmation and substitute confirmers are retired with D-6 (change history A.1).

### 6.9 Coordination records and decisions

`open → superseded | fulfilled | released | withdrawn`. Only the author, or a holder of `curate` on the scope, closes or supersedes a record; any other attempt is recorded as a conflict. A commitment marked fulfilled without a linked receipt shows as "claimed fulfilled by ⟨author⟩", and releasing or withdrawing a commitment follows §6.1's scope policy on who may release it. A claim links to a coordination record only through an explicit key reference recorded at capture; otherwise it is shown separately with a possible-duplicate cue, and a later claim never reopens a closed record. **Same-key conflict rule (deterministic):** two open records of the same kind and key with different values, neither superseding the other, form an attributed conflict shown wherever either appears; any two open ownership claims on the same key conflict. A commitment past its due date is shown overdue, never closed by time. Records under different keys never conflict by this rule, whatever their meaning; similar keys raise only the `possible_duplicate_key` cue (§5.4), and every overview that shows coordination records states that conflict detection covers identical keys only (§10.5.1).

**Decisions are never shown as simply "in force".** A decision renders with its status (below) as "decided by ⟨decider⟩ under ⟨authority basis⟩ for ⟨purpose⟩, effective ⟨interval⟩", with its applicable objections, overrides and dissent. Whether it is in force under the project's rules is the front end's determination. A position is shown as "current" only where a `validated` decision makes it so, and only for that decision's purpose (D1 F-12). Exposure records what UPMS released to the decider's views, not what the decider read or understood (TE-R20).

**Decision integrity checks** (core, at commit; not policy):
1. Every basis record exists, is readable by the decider, and is cited by exact revision. A basis record its author has withdrawn or retracted is not refused: every projection labels the decision "cites a withdrawn record", and the record's objections are in its applicable set (D1 F-3b, F-6; D-83).
2. No basis record is an unconfirmed, unadopted interpretation (D1 F-2).
3. A finalization or outcome decision whose evidential routes, followed from its basis claims through the standing projection, all rest only on uninstrumented observations is **labeled** "sole uninstrumented backing" on every projection, however the routes are cited (D1 F-17). The core does not refuse it; SCIRE's finalization rule decides (same-family review R-07).
4. The exposure reference resolves to committed release records whose positions precede the decision.
5. A signature binds this exact decision revision; amending the decision creates a new revision on which earlier signatures do not count (D1 F-11).
6. A `resolution` decision names the objections and the bindings at which it resolves them, cites an objection-resolution judgment (D1 F-3) and is homed as §5.11 requires (D-90, D-93, pending). If its decider later decides on a target those objections applied to, every projection labels the resolution "self-resolved" (D1 F-5).

**Reported, recorded and validated decisions (SC-TE05).**
- `reported`: a record that a decision was taken elsewhere or by someone; any client may write one, and an external decision is always reported.
- `recorded`: entered by its decider through a front end, with no policy result.
- `validated`: entered by the front end that owns the project's decision policy, with a policy result naming the policy and its revision, the authority evidence, the required signer set, the expected revisions of every basis record, and the position at which it evaluated the applicable set.

At the commit of a `validated` decision and of each of its signatures, the core checks atomically that every expected basis revision is still current and that the signature binds this exact decision revision; otherwise it refuses with a conflict, and the front end re-evaluates. **The core never refuses because an objection exists or arrived** (D-50; same-family review R-04). The decision's **late-objection delta** is the members of its applicable set at the read position (D1 F-6) that were not in the **evaluation baseline**: the objection neighbourhood of the proposed basis's footprint at the policy result's `applicable_position`, `N(F(B, [e, e]))` for the recorded basis `B` and position `e`, under the projection version the policy result pins (Codex review R66-01). The baseline is derived from the policy result, not stored. The decision's own footprint still starts at its commit (D-86), so an endpoint of an assessment effective only before the commit is in the baseline and never in the applicable set. The delta holds objections recorded after evaluation and earlier objections that reach the decision through an assessment that became effective after it. It is derived at read like the rest of the applicable set, never stored, and never touches the decision revision, so objections arriving during signing change no revision and no signature (same-family review F62-08). It travels under D1 F-7 and is shown on every projection; whether it requires re-evaluation is the front end's policy. **Signature completeness** (D-51, R-05): a `validated` decision is *awaiting signatures* until every required signer has a committed signature on its exact revision; it renders as pending and makes nothing current. The commit of the last required signature makes it *complete*. The core never evaluates the policy. Only a complete `validated` decision can make a position current for its purpose; `reported` and `recorded` decisions render as what they are. No client can write `validated` for a policy it does not own.

**Who owns a policy** (change history A.12, C61-2). Each scope's configuration names its **decision-policy owner**, a registered front-end principal, set by a holder of `manage` as an attributed configuration revision (§7.3.3); a scope that names none accepts no `validated` decision. The core accepts a `validated` decision, and each signature on it, only when its transmitting front end (`transmitter_identity`, §5.1) is the owner named by the decision's home scope at commit. **Registering a front-end principal** is an operator act, recorded as a control (D-66, which extends the D-40 residual to it); every projection of a `validated` decision shows its front end, that front end's registration and the operator act that registered it. **Changing** a scope's decision-policy owner requires an attestation from the outgoing owner or, if that front end is no longer registered, a recorded act in administrator mode; it applies only to decisions recorded after it, and the policy owner, with any change to it, is shown on every projection of a `validated` decision (D-52; R-06). The change names every decision of the scope still awaiting signatures; the incoming owner re-evaluates each as a new decision revision (check 5), and the old revision renders "superseded by a change of policy owner" and makes nothing current (same-family review F62-09). The policy result is part of the decision revision it validates: when a commit is refused and the front end re-evaluates, the outcome is a new decision revision, on which earlier signatures do not count (check 5).

Checks 1, 3, 5 and 6 apply to every decision; check 3 only labels. Checks 2 and 4 apply to `recorded` and `validated` decisions; a `reported` decision records what someone decided elsewhere and must stay recordable, so it is instead labeled with what check 2 finds, and it may have no exposure. **The applicable set at a decision** is derived as "as held then" at the decision's position under the pinned projection version (§9.9); it is not stored separately (R-08). `reported` and `recorded` stay distinct: whether the decider entered a decision themself is the authority distinction SC-TE05 asked for.

### 6.10 Objections

| Transition | Who | Effect |
| --- | --- | --- |
| Handling: open → acknowledged, deferred or answered | The objection's author, the target's author, or a holder of `curate`; front-end policy may narrow this | Workflow only; the objection stays unresolved |
| Resolution: resolved by assessment | A `resolution` decision (§6.9), naming the bindings it resolves | Resolved at those bindings only; a decision whose footprint holds another binding still shows it unresolved; a later dispute keeps it visible (D1 Definition 2.5; D-93, pending) |
| Resolution: withdrawn | The objection's author only; for a sealed author, only from the anonymous-role session (annex §7.8) | Withdrawn at the bindings the author names, or at all of them; a binding withdrawn as misapplied stays in history, labeled on the decisions that relied on it; the earlier record remains in history (D-93, pending) |
| Carry on revision | The core, when the target is revised, including a step or relation replaced with the same conclusion, or the same observation and targets | Carried to the successor as "carried, pending re-examination", which is added to its bindings; still unresolved, applies and travels; decisions that cited the earlier revision keep showing it (D1 F-3a, D-47) |
| Rebind | The objection's author | Records re-examination and adds the successor, or another record that restates a withdrawn target, to the objection's bindings; earlier bindings stay, so decisions that relied on them keep showing it (D1 F-6; D-91, pending); it stays unresolved. Refused unless the objection's home is the new target's home scope or an objection home registered for it, and every current reader of the new target, including readers through an own-record entitlement and under its restriction tags, can read that home (§5.11; D-80, D-88) |
| Target withdrawn | The core, when the target is retracted, withdrawn or deleted by its author with no successor revision | Stays unresolved as "target withdrawn, not re-examined"; stays live; shown on the target's marker and on every question page where the target was a position; whoever withdraws the target is first shown it (D1 F-3b, D-63) |
| Dispute | Any author, as an objection targeting the resolution, homed as §5.11 requires (D-90, pending) | The original shows "resolved by assessment, disputed" wherever it applied |
| Signing | The sealed author only, through the review-chair path (§7.8) | From then on a signed objection, together with every other record under the critic's pseudonym in the review; the anonymous interval stays in history |

### 6.11 Review obligations

`pending → closed`, closed only by an attributed reassessment (§5.12). Reassignment is an attributed act and closes nothing. While pending, the dependent route is under review (§9.9) and cannot newly back a consequential use unless the decision records an explicit qualification, which then travels with that decision like an override (D1 F-33). Past decisions that relied on the dependent are flagged, never undone (D1 F-35).

### 6.12 Archive

`active → archived → active`. A holder of `curate` on the record's home scope archives it by confirming a retention recommendation (D-29); the confirmation is attributed and reversible by any curator of the scope. The core refuses to archive a **live** record (§12.2), whoever recommended it. An archived record leaves default proactive retrieval and the overviews; it stays retrievable on request, appears in history, provenance and standing, and keeps every restriction it had. Archive is never deletion (TE-12).


## 7. Trust and Access

**Provenance is recorded as fact, access is decided by scope permissions, and no content ever grants anything.** Security is proportionate to open, academic-like science (D-24): it keeps what fact-checking and basic protection need, and leaves operational-environment machinery out of the core.

### 7.1 Source classes

| Class | Capture meaning |
| --- | --- |
| A — direct entry | Adapter-observed direct input by an authenticated principal with trustworthy span marking |
| R — relayed | Pasted, attached, forwarded or quoted content; all chat text when input-mode provenance is unavailable |
| C — connector-declared | Exact fields independently configured as produced by the source system itself |
| X — external or unknown | Untrusted connector fields, web content, third-party messages, unknown origin |
| M — model-generated | Every model output, including statements, overlay notes, hub narratives and consolidation output |

A does not prove intellectual authorship, correctness or intent: a person can retype malicious text. C is field- and contract-specific, not trust in a whole tool response. Missing input-mode instrumentation means R; content classifiers cannot manufacture A or C. Model-derived objects carry M plus the union of input classes. Automated analysis can only add restrictions.

### 7.2 Actions are outside the memory core

Candidate 5 §7.2 defined consequence classes C0–C4, operation contracts, role-bound grounding of action arguments and per-action confirmation. **They leave the memory core** (D-24, proposal §8.2): memory does not execute actions, and action safety belongs to the agent runtime. What remains in UPMS is what a runtime needs from memory to do that job honestly:
- every retrieved item carries its source classes, attribution, modality and act state (§10.3), so a runtime can tell a user's direct entry from relayed, external or model-generated text;
- canonical typed values and ambiguity markers (checking annex §5.9), so a runtime never grounds an argument in a translation, a detected locale or an ambiguous parse;
- retrieved content is attributed data, never instructions (§10.4).

A runtime that implements candidate 5's classes may record its manifests and outcomes in UPMS as external-reference events (§11.1); UPMS stores them as evidence and enforces nothing with them.

### 7.3 Memory access control

**UPMS owns which principals may read, write, curate and manage memory in each scope.** Permissions are control records changed only through authenticated operations. **Fixed (proposed).**

#### 7.3.1 Principals

- **Human users**, authenticated by the identity provider.
- **Groups**, whose membership the identity provider owns (pilot: built-in directory behind the same interface; decision D-4).
- **Agent principals**: persistent agent identities with their own scopes and a designated human **overseer** (D-7). An agent principal's reach never exceeds its overseer's (D-9, confirmed and amended by D-49): it can read only what its overseer, acting without administrator mode, can read, and on any scope other than its own private and operational scopes it can curate only where its overseer holds `curate`. On its own scopes it keeps `write` and `curate`. Its `write` elsewhere is not capped, since writing appends attributed items. No agent principal holds `manage`.
- **The review chair is not an agent principal.** An agent review chair runs as a confined service role of the core's review service (§7.8), in a fresh model session with no human overseer; the D-9 overseer cap does not apply to it, and no overseer gains access through it (SC-TE02).
- **Service principals** (capture, workers, purge controller, index and adapter builders) and **front-end principals** (§4.4), governed by component roles, not scope permissions.

An agent session acting for a principal holds the intersection of that principal's rights and the session's grant, and never enters administrator mode (D-2). "Other" means every human user of the tenant.

#### 7.3.2 Scopes and ownership

Every record has one home scope and one owner: the principal it was captured for. Output of an agent principal is owned by that agent; output of an agent session acting for a user is owned by the user; a human's messages to an agent are owned by the human. Record ownership is distinct from the scope owner named in a scope's permissions. Permissions attach to scopes; the only per-record right is the own-record entitlement (§7.3.4); a record's restriction tags may narrow access but never widen it beyond its scope. Scopes may have a parent for organization: a parent's permissions are copied as defaults when a child is created, with no live inheritance, so moving a scope never silently changes who can see it (D-3).

#### 7.3.3 Rights

| Right | Allows |
| --- | --- |
| `read` | Knowing an item exists and retrieving its content, for the principal and its agent sessions; appearing in counts, coverage, flags, standing and overviews. Candidate 5's separate `list` right merges here (D-28) |
| `write` | Adding records (events, claims, questions, objections, relations, judgments, decisions, coordination records); correcting, redacting, deleting and sharing own items; proposing corrections and concepts |
| `curate` | Acting on others' items: attributed corrections, suppression, archiving, deletion with a recorded reason and marker (§12.3), resolving proposals, curating vocabulary, closing others' coordination records, sharing others' items out of the scope. Candidate 5's `d` right merges here (D-28) |
| `manage` | Permissions, ownership, procedure activation, child scopes, scope configuration (processor eligibility, narrative language, the decision-policy owner of §6.9, flags such as pull-only) |

Displayed compactly, for example `owner rwcm · group rw-- · other ----`. `write` without `read` is valid (a contributor drop box, or an outside critic's route into a review scope): a contributor then reads only its own items, through the own-record entitlement. Writing never overwrites; every change appends an attributed record.

#### 7.3.4 Evaluation

For principal *p*, operation *o* and target *t*, in order:

1. If *p* is in administrator mode for *t*'s scope, apply §7.3.6.
2. Rights on the home scope are the **union** of every matching entry: owner, named principal, each group containing *p*, other. **Own-record entitlement:** the owner of record *t* holds `read` on *t*; an overseer holds `read` on every record its agent principal owns.
3. For an agent session, intersect with the session grant. For an agent principal, cap `read` at its overseer's `read` without administrator mode, and outside its own scopes cap `curate` at its overseer's `curate`.
4. Apply all other checks unchanged: restriction tags, quarantine, correction state, barriers, archive state for proactive routes, processor rules, sealing (§7.8), and the task's lineage exclusions, which traverse ancestry.

There are no deny entries; exclusion uses narrower groups. Unknown membership or permission state denies (§13). Candidate 5's step 4, requiring rights on every scope in a derived item's requirement closure, is removed with D-6 (§7.3.5).

#### 7.3.5 Derived and cross-scope memory

**A record lives in the scope it is written to, under its writer's responsibility, as in ordinary academic practice** (D-24). If an agent reads a team scope and saves a summary in a personal scope, the summary is governed by the personal scope's permissions and its own restriction tags; it keeps its provenance (`exposed_to` the released records, §8.2), so anyone who can read it can see that it was derived from team records, shown as "private source" where they cannot read the endpoints. Losing access to a source does not withhold notes already written from it. Candidate 5's no-laundering rule (D-6), requirement closure and owner-confirmed publication are superseded in the default profile; the opt-in strict profile restores one simple form of it for projects that need it (§7.9).

**The honest default guarantee is direct access control over stored records plus attributable sharing, not derivative containment** (TE-R06). An authorized writer can put a faithful summary of private scope A into broadly readable scope B; UPMS records where it came from and does not stop it. Material that must not be summarized out of its project is outside the first product (§1.2).

What protects unpublished work is therefore: scope permissions; the rule that sharing others' items out of their home scope needs `curate` there (§6.8, §10.6.2); restriction tags on sensitive records; processor eligibility (§7.4); and provenance that shows where a note came from.

#### 7.3.6 Administrator

**Authority:** every right in every scope of the tenant, and ownership transfer, exercised only in administrator mode.

**Use:**
- The administrator role is assigned in the identity provider; UPMS cannot grant it.
- Administrators act with ordinary rights by default. Administrator authority requires an explicit **administrator mode** with a reason and a scope (initial default: re-authentication and a 1-hour limit, §14.2).
- Every content access or change in administrator mode creates an access record, committed in the canonical store before the content is released (§11.4). The owner of a personal scope sees every administrator access to it (D-1, simplified).
- Agent sessions never enter administrator mode (D-2).
- An administrator in administrator mode cannot grant rights to themselves, to a group containing themselves or to agents they oversee, or make themselves an overseer; transferring oversight, or an active user's personal scope, requires a second administrator.
- Bulk destructive operations (whole-scope deletion) require confirmation and a cancellable delay.

**Limits that bind administrators too:** no reading of sealed attribution (§7.8); no reading past a deletion barrier; no records attributed to another principal and no forged source class; no direct setting of labels, admission, standing or history; no bypass of quarantine isolation; no disclosure to ineligible processors; no self-assignment of the administrator role.

Candidate 5's replicated control plane, owner-notification delivery tracking and protected audit retention bounds (D-13) are reduced to this logged access (proposal §8.2; §11.4).

#### 7.3.7 Revocation and offboarding

Narrowing permissions, removing a group member, transferring ownership or oversight and ending administrator mode take effect for every read that starts after the change commits; until UPMS observes a membership change made in the identity provider, cached membership may serve reads within the declared bound (§14.2). Content already released cannot be unseen. Deletion, correction and quarantine keep their barriers (§9.4).

When a user leaves, their records in shared scopes keep their owner and attribution, and the scope's curators may withdraw or delete them under §12.3. Their personal scope is **not** deleted on a schedule (D-25): it stays inaccessible to others until it is transferred under §7.3.6 or deleted on an explicit request recorded with its reason. An agent principal's scope follows its overseer's decision.

#### 7.3.8 Default permissions

| Scope type | Default |
| --- | --- |
| Personal | owner `rwcm`; nobody else |
| Agent principal (private) | agent `rwc`; overseer `r-c-` as a protected grant the agent cannot remove; nobody else. Nobody may widen an agent's private scope; content leaves it only by sharing |
| Team or project | lead `rwcm`; members `rw`; other none |
| Organization-wide | managers `rwcm`; contributors `rw`; all users `r` |
| Agent-operational (runtime state) | owning principal; for an agent principal, also its overseer `r` as a protected grant |
| Review scope (§7.8) | created by the front end for one review: participants `rw`, outside critics `w` only, the review chair through its role path |

### 7.4 Confidentiality and processors

**Restriction tags narrow access to the record that carries them; they are not inherited.** A record may carry tags (for example an embargo or a data-agreement category) that every reader, processor and destination must satisfy. An authored record derived from a tagged record does not acquire its tags automatically: its writer decides, as in ordinary practice, and its provenance shows the tagged source. A **UPMS-derived** representation (an embedding, index entry, hub line, narrative unit, adapter, vocabulary definition or review package) has no writer to decide, so it carries the union of its inputs' tags, and every reader, processor and destination must satisfy them (A.3 check U9). Read permission, endorsement and summaries never declassify. An objection carries no tags of its own; it is read under the tags of the binding through which it applies (§5.11; D-87, D-91 pending).

**Processor eligibility.** Sending a scope's content to a model provider, embedding service or translation service is disclosure. Each scope's configuration names its eligible processors; an unbound processor is denied (§14.2). Processor identity includes the actual account, region or endpoint, retention mode and downstream handling where material. Local small models are preferred for restricted scopes (§9.8). No worker or alternate transport may bypass these rules.

### 7.5 Reliance endorsements

An endorsement permits reliance only on its exact object or value, role and use. It cannot authorize unrelated output, survive a changed value by text similarity, or grant access. Runtime resolution checks current endorser authority and revocation. Batch interfaces preserve each differing scope, payload and consequence.

### 7.6 Default admission

The initial ruleset admits only attributed first-party statements — “P stated S” — from verified direct-entry spans by P, about P or expressing P's preference, intention or commitment, within an authorized personal or project scope. It admits the attributed statement, not S as external fact. Extraction fidelity requires an exact source-linked rendering or a valid fidelity endorsement; a model-structured paraphrase alone stays evidence-only. Shared items are evidence-only in their target scope unless endorsed or admitted by a ruleset there. Other domains remain evidence-only until a domain ruleset is separately accepted. Admission never makes memory normative authority.

**Scientific standing is separate** (D-48; same-family review SC-R2). This admission rule governs project-memory facts. Scientific judgments are never admitted as facts; they affect standing only, through effectiveness as D1 Definition 6.0 defines it (§9.9). In Slice 2 a holder of `manage` registers, as scope configuration (§7.3.3), one **inquiry ruleset** per inquiry scope; a new version is a new ruleset unless its registration states that it continues the previous one (D1 Definition 6.0). It covers attributed human and agent assessments of claims, evidence relations, inference steps and objection resolutions, and `fidelity` and `inspection` judgments under D-73's restrictions (same-family review FM-R14), on D1's ordinal statuses, with agent assessments labeled as agent assessments. It admits nothing into project memory.

### 7.7 Threat model and the limits of truth-based robustness

Attackers considered: obvious bad actors who plant instructions in documents or messages; ordinary credentials and cooperating agents that plant false memories, jargon or definitions; sock-puppet sources posing as corroboration; flooding; and attempts to read others' unpublished work. The trusted computing base (TCB) includes core validation, permission evaluation, sealing and barriers; retrieval access enforcement; capture and session instrumentation; identity; KMS; deployment isolation; and, for sealing, the front end that opened a review and the transport adapters (D-67). Compromise of these is outside the guarantee; **an operator who controls the deployment's storage and keys is inside the TCB, and sealed attribution is not protected against them** (§7.8, C6-1). An ordinary compromised credential keeps its legitimate permissions until revoked; UPMS cannot infer the human's real intent.

Traceable records and assessed evidence **help investigate** attacks on the integrity of belief; no experiment supports a claim that they resist most attacks (TE-R15). They are no defence for **instruction hijacking** or **disclosure** (proposal §8.3). That is why those defences stay:

| Attack | Does the theory–evidence structure resist it? | Kept defence |
| --- | --- | --- |
| A planted falsehood contradicting well-supported, independent evidence | Often, when it is structured into a screened slot or bears on an assessed claim; a falsehood left in unstructured text need not raise any flag | Consistency channels (§9.7), source assessment (§9.13) |
| Fake corroboration: copies or sock-puppet sources | Partly: recorded shared ancestry exposes copies; unrecorded common ancestry and unrelated-looking fabricated sources do not show | Provenance, independence claims, source classes |
| A plausible fabrication in a sparsely evidenced area | Weakly: nothing contradicts it yet | Source class X or M visible; unassessed until assessed |
| False evidence from an authentic account, or accurate but cherry-picked observations | Weakly: provenance shows who and how, not honesty; selection shows only where use history is recorded | Use history, independence claims, review |
| Instruction injection | No: it needs no false claim | Data, never instructions; quarantine |
| Disclosure of unpublished work | No: disclosure falsifies nothing | Scope permissions, processor eligibility, restriction tags; strict profile where needed |
| Flooding with noise | No | Quotas; source classes; retrieval salience |
| Anonymity used for attacks, fake consensus or obstruction | Partly | Block and return (front end); the sealing and independence rules of SE1 (annex §7.8); anonymous objections never block (D-36) |

Untrusted text and archives are data, never executable deserialization, shell instructions, plugin activation or policy. Filesystem and network credentials and parser resources are restricted. Connector secrets stay outside model context and ordinary logs.

### 7.8 Sealed attribution and the back end of anonymous review

**In the anonymous-review annex** (`UPMS_Architecture_Manual_Review_Candidate_6_5_Annex_Anonymous_Review.md`, §7.8; Slice 3; reviewed with this core at Gate 0). In brief: sealed attribution, the anonymous role as a distinct session type, conflict and appointment checks, safe release, blocks, appeals, signing and masked review packages.

### 7.9 Strict profile (deferred, D-27)

A project with embargoed, industry or human-subject data can later opt into containment: content written in a session that read the project stays in that project unless its owner shares it. It would reuse release records (§8.2) as access ancestry for that project only. It is **not part of the first product** (D-27); adding it reopens §7.3.5, §8.2 and §12.3, and the re-review's SC-42 rule (uniform, existence-independent qualification of decisions on partial coverage) returns with it (proposal §13.2).

## 8. Session Integration and Release Records

**UPMS records what it releases; it does not mediate what agents do.**

### 8.1 Integration profiles

| Property | Memory-service profile (in scope) | Instrumented agent runtime (outside UPMS) |
| --- | --- | --- |
| Scoped retrieval, permissions, lifecycle controls | UPMS | UPMS |
| Release records for everything UPMS releases | UPMS (§8.2) | UPMS |
| Every runtime-visible model input captured; output and action mediation; grounding and confirmation | Not claimed | The runtime's own responsibility and claim |
| Lineage exclusions | UPMS-assembled context only | The whole runtime context, if the runtime enforces it |

Content an agent obtains outside UPMS (files, the web, other tools, the user's chat) is outside UPMS's knowledge and is a declared coverage gap in independence, impact and lineage claims. A runtime may supply its own manifests as external-reference events (§11.1); they are evidence of what the runtime reports, not enforcement.

### 8.2 Release records as provenance

Every UPMS release to an agent session, agent principal or front-end view (search results, context, expansions, evidence, standing reports, question pages, overview lines and narrative units, review packages) is committed as a **release record** before it crosses the boundary: principal (sealed in an anonymous role, §7.8), session, the exact revisions, hub lines and narrative units released, and time. If the commit fails, nothing is released. The core checks each recipient's current `read` right when it commits the release record, so a response assembled before a permission change is not released after it (a direct-read fence, without taint; AC2). Every later write from the same session (events, claims, objections, decisions, coordination records, checkpoints, corrections) is `exposed_to` everything released to the session before it. **Fixed (proposed).**

They exist for four uses, none of them access (proposal §8.2):
- **independence:** whether two contributions could share inputs (D1 F-19);
- **decision exposure:** what a decider was shown (§6.9 check 4);
- **lineage exclusion and chair checks:** what a blind reviewer or a fresh agent chair has not seen (§7.8, §10.6.4);
- **impact recall:** which notes a retracted or quarantined source may have influenced (§9.11).

**Session identity.** A session is one agent session from its start, where the bound integration shows that its model context is not shared with any other session; compaction and resume continue the same session. Otherwise all of the principal's agent sessions count as one, which only makes independence and freshness claims more conservative. Gate 0 establishes which applies to the bound Codex build. Whatever it finds, anonymous-role sessions are a distinct session type whose releases never become exposure ancestry of a write outside that role (annex §7.8, D-49). **Granularity:** a hub release adds only the lines and narrative units actually released. **From the first write:** provenance cannot be reconstructed later, so release records start in Slice 1a-core. Candidate 5's cost of this mechanism (withheld and early-expiring writes, refused publications) disappears, because release ancestry no longer imposes access requirements or deadlines.

### 8.3 Handles, segments and reset

Retired with the instrumented-runtime profile (D-24). See change history A.1.

### 8.4 UPMS's own model invocations

UPMS's processing workers (extraction, screening candidates, investigation, overlay notes, consolidation, retention recommendations, translation on request) call models. Each call requires a committed input manifest (`ProcessingRecord.input_manifest_ref`) before submission, naming every input revision, hub line and prompt or program version; outputs are durably captured or withheld before any release; a provider timeout leaves an uncertain attempt and a separately accounted retry. The manifest is the dependency set of the output: an output's provenance is everything in its manifest (conservative propagation, retained from candidate 5 §8.2 for UPMS's own models only).

### 8.5 All egress counts

Replies, front-end views, logs, diagnostics, exports, embeddings, rerankers, adapter training jobs and model inputs are disclosures. Operational logging is content-free by default; adding payload logs creates a protected deletion surface (§12.3). For an anonymous-role operation, operational and transport logs record the pseudonym or nothing, never the principal (D-67, annex §7.8). Processor eligibility (§7.4) applies to every UPMS worker.

### 8.6 Resource boundaries

Bound capture bytes, formats, nesting and decompression; relation fan-out and traversal work, including standing and impact traversal; search, time and token budgets; queue and storage growth; per-principal inference spend; maintenance and consolidation spend; adapter training; concurrent jobs. Capacity is reserved for deletion, correction and quarantine barriers and purge. Unknown limits or exhausted validation budgets fail closed for the affected operation; ordinary permitted recall may degrade with explicit coverage. Integrity checks are never discarded to meet latency. Because nothing expires (D-25), storage growth is reported and managed through the archive tier and explicit deletion (§12), never by silent truncation. Each scope has a storage quota; when it is reached, new nonessential capture is refused before acknowledgement, never accepted and dropped, and the scope's manager chooses to expand, export or delete (TE-R16). Archive moves records to a cold tier; it does not remove the capacity limit.

## 9. Commit, Freshness, Screening, Standing and Assessment

**One fenced owner serializes canonical commits; freshness and barriers are decided synchronously by the core; screening only flags; standing is projected at read; language processing runs as a cheap-to-expensive cascade that only proposes.**

### 9.1 One transition owner

One logical owner serializes canonical commits within the tenant, with fencing enforced by the storage boundary: a stale process cannot commit with a superseded fencing generation. A transaction validates authority (including scope rights), expected revisions, dependencies and barriers; appends records; advances relevant epochs; and schedules derived work through a transactional outbox. Outbox delivery is at least once; consumers deduplicate by operation identity and advance durable watermarks without skipping failed predecessors.

Ingestion identity is `(tenant, authenticated source_namespace, source_message_id, source_revision)`. Without a stable source ID, capture allocates a request ID before retry. Same identity with different bytes is a conflict, never a silent overwrite. All lifecycle operations share §4.3's idempotency. Transactions never span tenants; cross-scope reads within the tenant use one consistent snapshot plus current access checks.

### 9.2 Payload publication and capture

Identity, capture, never-store and resource policy are applied before retention. Protected payload bytes are written to non-serving storage and verified for durability and integrity before their canonical reference and outbox entry commit. Acknowledgement follows both payload and metadata durability. Object-store and database writes are not assumed atomic: abandoned staged objects have run-owned expiry and cleanup, and a missing committed payload causes explicit unavailability and repair, never invented data. Temporary files, uploads and rejected content are covered by cleanup policy.

No model runs on the synchronous capture path. Never-store detection has a declared scope: deterministic categories and authenticated channel policy, not a claim that all sensitive content is recognizable. A channel that cannot satisfy its capture policy is rejected or has retention disabled. Asynchronous indexing, extraction, screening and overview work use only eligible inputs and permitted processors.

### 9.3 Freshness without the insertion race

**Initial rule:** the core maintains a conservative evidence epoch per scope. Any committed source addition or revision, claim, statement, evidence relation, correction, relevant lifecycle change, entity-resolution change, vocabulary merge or ruleset assignment that can affect assessment advances the scope epoch in the same transaction; unknown relevance invalidates the whole affected scope. Publishing a judgment, flag or overview, or completing a processing attempt, does not. **Admission rests on first-order evidence only.** Pilot rulesets assess source, claim, statement, evidence-relation and epoch-tracked control evidence (endorsements, corrections), never a judgment, flag, hub, narrative, projection or standing report. `submit_assessment` enforces this by ancestry: an assessment whose recorded inputs include one of those, or a claim descended from one (a consolidation hypothesis, an agent claim written after reading a hub), is kept evidence-only. No input is exempted as "routing". So a flag investigation is always evidence-only, and admission after it needs a separate `request_assessment` whose inputs exclude the flag, the investigation and their descendants. Judgment on judgment is deferred (D-39, §9.10). Cross-scope evidence captures every participating scope's epoch.

An assessment binds a snapshot, exact read revisions, assigned ruleset and scope epochs. Admission requires unchanged revisions and epochs at commit; if evidence arrived between snapshot and commit, the assessment is kept as historical or evidence-only and reassessment is queued. Unprocessed new evidence also invalidates: pending extraction cannot hide an opposition window. Basic recall never waits for deep processing.

At every current-state presentation or protected reliance, the effective judgment must still match current scope epochs, rule assignment, validity interval and the maximum age bound, with no unresolved required processing or reassessment; otherwise it is shown as evidence-only with qualifications, or the dependent action is blocked. The epoch comparison is the safety condition; the reassessment queue is only liveness. Capture time is not freshness time. These rules, including the age bound of §14.2, govern project-memory admission and current-state presentation; scientific standing uses D1 Definition 6.0 instead (§7.6, §9.9, D-48).

Slot-level epochs (§9.7) may replace scope epochs **only after** an invalidation contract covers vocabulary merges, entity-match changes, rule changes and the candidate channel, and race scenarios T01 and T19 pass at slot level. Until then, scope epochs remain the safety condition; their availability cost is measured first. Timeouts and unknown scopes make an assessment stale, never fresh. External current-state claims also need source-owner refresh or preconditions.

### 9.4 Barriers and the release race

The core owns barrier epochs and orders **barrier commits** with releases; a check followed later by an uncoordinated write is insufficient. Barrier commits are **deletions, corrections and quarantines**. Proposal §8.2 keeps the release fence "only for deletion and correction"; this candidate also runs quarantine through it, because the mechanism already exists and quarantine is the containment the proposal keeps (change history A.12, C6-8). Permission narrowing no longer uses it (§6.7).

For each barrier commit, the restriction is published and the affected epoch advanced synchronously. Cached eligibility is invalid immediately; UPMS-derived representations of the target (statements, embeddings, index entries, flags, hub lines, narrative units, adapters trained on it, review packages) are rejected through ancestry even before purge or index jobs run. A bounded traversal failure contains the affected scope. Restricted cleanup and audit transitions remain possible without re-serving content.

A release either crosses the controlled boundary before the barrier, or revalidates after it and is rejected if affected. Before acknowledging `serving_blocked`, an applied correction or a quarantine, all older release rights must have completed, been cancelled or been conclusively fenced; a stuck participant causes a deadline failure, and the request stays pending and is never falsely acknowledged. The guarantee concerns **future releases from UPMS**, not bytes already sent or what a human or agent already read; those are reported as prior exposure, and release records name them (§8.2).

### 9.5 Read-your-writes and bounded work

Targeted reads and acknowledged corrections use canonical state immediately. Search overlays post-index commits through a bounded scan; if it cannot cover the gap, it returns explicit partial coverage and a continuation token, never a claim of completeness or absence. Barriers always apply, even when the index is unavailable. Queries may request a minimum commit position and receive that consistency or an explicit unable-to-satisfy result.

Lazy processing responds to explicit requests, obligations, retrieval need, consequential reliance and a bounded age-weighted background sweep, so rarely retrieved obligations are not starved. Queue saturation stops new nonessential work, preserves capture within quota and reports deferred processing. Deletion and barrier work has priority over extraction, screening, consolidation and training.

### 9.6 Replay and compatibility

| Contract | Promise | Limit |
| --- | --- | --- |
| Canonical replay | Rebuild surviving states from retained records, recorded outputs and versioned reducers, vocabularies and screening rules | No model calls, external queries, actions or erased bytes |
| Historical input reconstruction | Exact submitted runtime-visible sequence while every required byte and revision is retained | Deletion and unknown provider internals are explicit gaps |
| Retrieval rebuild | Rebuild eligible content, hubs and adapter-based indexes to qualified criteria | Approximate index bytes, order and narrative wording need not match |

Each durable schema has an explicit READ, MIGRATE or REJECT compatibility rule; unsupported versions never fall through to permissive defaults. Migrations preserve IDs, labels, permissions, controls, history and deletion restrictions, with staged validation, atomic publication and interruption recovery. Rollback cannot roll back barriers or resurrect erased content. Caches, indexes, hubs and adapters may be discarded and rebuilt; canonical data is never reinterpreted to fit a cache. A new model, tokenizer, embedding model or vocabulary version creates new processing or projection versions.

### 9.7 Deterministic screening

**In the checking annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md`, §9.7; Slice 3; reviewed before Gate 3). In brief: deterministic screening in three consistency channels and the candidate channel; screening only flags.

### 9.8 Processing cascade and adaptive models

**In the checking annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md`, §9.8; Slice 3; reviewed before Gate 3). In brief: the processing cascade and per-scope adapters; their outputs are proposals.

### 9.9 Standing projection

**Standing is computed at read time over exact revisions; no stored record holds a belief** (TE-06, D1 §6). **Fixed (proposed).**

The projection service computes the standing report of D1 Definition 6.1 for a reader, a claim revision and a position *p*:
- **Inputs:** the records committed at *p* that the reader may read: judgments of the claim and of its routes per scope and ruleset; evidence relations and inference steps with the heads of their assessment lineages (D1 Definition 6.0) and use histories; the objections applicable to the claim and its routes (D1 F-6, cited, not restated); review obligations; source assessments of the works the claim rests on; decisions relying on the claim.
- **Route status:** exactly as D1 §6.1 defines it, cited and not restated, with every condition that holds and each route's bearing. Premises enter only through their own effective judgments at *p*; §9.3's age bound and scope epochs do not apply, so the evaluation is well founded and needs no fixed point. The report names the scope and ruleset of each premise's judgment. A route whose evidential root was deleted is under review with cause `input_deleted` (§12.3).
- **Depth:** each route shows its premises' standing one level down by default; deeper levels on request, within the traversal limit (§14.2). The report is exact to the depth computed, and the limit is stated in its coverage (D1 F-30).
- **Predicates:** `has_sound_support`, `has_sound_adverse_route` and `has_open_challenge`, exactly as D1 F-28 defines them, each shown with the routes and qualifiers that make it true (D-81). A usable adverse or neutral route never counts as support. No aggregate verdict, score or ranking of alternatives is computed.
- **Decisions:** for a decision, the applicable set `A(D)` of D1 F-6 (D-86, D-91 pending), derived from committed history, maintainable incrementally and never an editable record; with its late-objection delta derived as in §6.9, each objection's state and mode, the "self-resolved" and "cites a withdrawn record" labels (§6.9) and the coverage statement of §5.11. Front-end widening is recorded on the view, never on the decision.
- **Coverage:** records the reader may not read (shown as "private source" endpoints, never counted), the objection coverage statement (§5.11, D1 F-7a), unprocessed records, pending impact traversals (§9.11) and where traversal stopped.
- **History:** at a past position *t*, the report evaluates the records committed by *t* under the ruleset and projection versions in force at *t* ("as held then"; R-03); "as now assessed about then" evaluates current judgments of records dated before *t* (D1 F-31). Positions of explicit deletions, and the interval a restore may have lost (§12.4), are named, so an incomplete "as held then" says so.

**Caching.** A report may be cached by reader rights, claim revision, position, ruleset versions and projection version; a commit that changes any input invalidates it, including a new judgment or objection on the claim, its routes or their premises (negative information), and a cache hit still checks current eligibility. At a pinned position, a cached report and a from-scratch evaluation are identical (T98). The projection is never an input to admission (§9.3) and never evidence.

### 9.10 Judgment bases (deferred, D-39)

**A judgment whose basis cites another judgment is not effective** (D1 Definition 6.0, condition 5): standing shows it as an assessment that is not effective, and candidate 5 §9.3 governs its admission. The proposed contract is candidate 6.1 §9.10 (SHA-256 `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a`), to be revisited only if the Slice 2 demonstration shows assessors need it; the Judgment schema carries no `judgment_basis[]` field meanwhile. This closes candidate 5 §18.1's judgment-on-judgment item for the first product.

### 9.11 Impact traversal and review obligations

**Retraction, correction, revision, deletion and definition change create review obligations; nothing becomes true or false automatically** (TE-08, D1 §6.4).

1. The cause commits (a correction or retraction control, a claim revision, a deletion, a quarantine, a definition change in a `defined` claim or a vocabulary concept, an SSDS requalification recorded as an external-reference event, or a `diverges` fidelity judgment, which the traversal follows from the `renders` link to its tool checks and to the judgments that cite them; D-74). It advances the affected scope epochs (§9.3), so current admissions that relied on the cause's target become stale at once.
2. An impact worker runs a deterministic, replayable traversal of the provenance, evidential, inferential and meaning-link graphs from the cause, including the definition, model, calibration and condition records that an evidence relation or inference step cites by identity (TE-R10), within the traversal limits, and submits a review obligation for each dependent route and claim, with an assignee (by default the dependent's author, or a curator of its scope when the author has left; a dependent written in an anonymous role is assigned to its pseudonym through the chair path while its review is open, and to a curator of the review scope after it closes, annex §7.8, D-68). The traversal is a processing record; its outputs are reproducible on replay.
3. Until the traversal for a cause has completed, every standing report in an affected scope carries the coverage line "impact traversal pending since ⟨cause⟩". A traversal that hits its limit records the frontier and reports it; it never reports the rest as unaffected.
4. Obligations close only by reassessment (§6.11). Past decisions are flagged in their projections ("a basis record was retracted after this decision"), never undone.

The same traversal serves **incident recall** for non-scientific causes (an injected source, a compromised credential, a faulty processor or vocabulary version): it returns the affected records, hubs, adapters and release records the investigator may read, distinguishes possible influence from causal proof, lists coverage gaps, and can schedule quarantine, reassessment, re-consolidation or retraining through normal interfaces (§11.3).

### 9.12 Fact-checking

**In the checking annex** (`UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md`, §9.12; Slice 3; reviewed before Gate 3). In brief: fact-checking as retrieval, screening and attributed judgment.

### 9.13 Source assessment and the person guard

**Works and non-person channels are assessed one by one; people are never scored** (TE-13, D-32, D1 §7). **Fixed (proposed).**

**Assessment.** A source assessment is a judgment of kind `source` whose target is a **work** (a publication, dataset, measurement, analysis, argument, reported result or model output) or a **non-person channel** (an instrument, dataset, database, software or model family), for a stated kind of claim. Its result is the ordinal value of D1 Definition 7.1 and its basis. The core refuses a source assessment whose target is a principal who is a person, a group, an institution or a venue (D1 F-41). No automatic mapping from counts to a value runs in this candidate (D1 F-36). A source assessment may order retrieval and fact-checking work; it never sets standing and never hides a claim.

**Slice placement (D-45).** Assessments of works ship in Slice 3. Assessments of non-person channels and their track records are deferred to Slice 4 and built only if measured need justifies their proxy risk; until then the core refuses a `source` judgment whose target is a channel. The person guard below applies from the first slice.

**How the person guard is enforced, and where it is only a norm:**

| Guard (D1 F-38 to F-42) | Enforcement |
| --- | --- |
| No person-level output | No schema field, projection or API computes or stores a score, rank, rating, track record, tendency, outcome count or label for a person. Author search returns works without their assessment values, ordered by ordinary relevance or time; a work's assessments appear when that work is opened (D-55, D1 F-39). A reader who opens works one by one can still compile them; that residual is stated |
| Authorship is never an input | UPMS workers that assess, rank or recommend receive inputs with author identity removed; retrieval-ranking features exclude authorship; identity relations (same principal, declared collaboration, declared conflict of interest) are supplied only to independence accounting and conflict checks, and same sealed author only to conflict checks (D1 F-20, F-20a). A human assessor sees authors; for them the guard is a recorded norm, and their basis is inspectable |
| No characterization in synthesis | Synthesis screening (§9.7) flags characterizations of a person in UPMS-produced narratives, notes and agent-written synthesis, which are then withheld. The detector is a fallible cue: it can miss oblique characterizations and misfire on criticism of a work, so it guarantees nothing. Agents outside UPMS are governed by their own runtime; UPMS's guarantee covers what UPMS produces and shows |
| No disguised person proxies | A channel must be a technical production or measurement mechanism (an instrument, a pipeline, a database, a model family as software). A collection defined by authorship or affiliation (one researcher's papers, a lab's outputs, a venue's articles) is refused as a source-assessment target (TE-R12) |
| Only humans judge people | A claim with `subject_kind: person` must be authored by a human principal, signed and non-anonymous (§7.8); the core refuses one authored by an agent. It is linked to every reply by the person judged and always rendered with them, is never surfaced proactively (excluded from proactive retrieval and overviews), and never enters any assessment or ranking input. `subject_kind` is set by the claim's author, so these refusals hold only where the author marks the claim; an unmarked claim about a person is caught only by the chair's block and the fallible synthesis cue, and this guard is partly a norm (R-18) |
| Institutions count as people | No ranking of labs, groups or venues; their records are channels of persons and are refused as source-assessment targets |
| Conflicts of interest | Recorded as facts on the work they concern |

**Track record** for a non-person channel: deferred with channel assessment (D-45), in the checking annex §9.13a.

### 9.14 External authority: SSDS references

**SSDS stays an independent, governed system; UPMS references it and never re-authors it** (D-21, TE-14). SSDS ledger records (runs, assessments, gate decisions) are recorded as Events with an `external_reference` (§5.1) bound to their revision and SSDS's stated qualification. Claims citing SSDS definitions take modality `defined` and an authority reference back to SSDS; UPMS never becomes their authority. A retained snapshot of an SSDS result is evidence of its value at that revision, with qualification "as of the snapshot; later changes unknown", and claims relying on it carry that qualification (D1 F-18, re-review V4-13). SSDS unavailability never stops UPMS or SCIRE and never changes a record's historical status; it may limit a particular new consequential use (SCIRE D-E). The SCIRE → SSDS model-package hand-off stays with the front end.


## 10. Retrieval, Context, Overview and Team Memory

**Eligibility is decided before ranking; a blank model orients from a small per-reader map; team visibility is designed for coordination; archived records leave the proactive routes and nothing else.**

### 10.1 Eligibility before ranking and release

Tenant, principal, effective rights (`read`), scope, quarantine, correction intent, deletion and the task's lineage exclusions constrain candidates before payloads reach a ranker, reranker, snippet generator or external processor. Shared approximate structures may be internal to the TCB only if ineligible content cannot affect exposed snippets, counts or explanations or unauthorized model inputs. Partition and filter strategy is D4 and must be qualified; post-filtering an untrusted reranker's input is too late.

Final return passes the release gate. Cache identity includes principal and rights context, scope, barrier epochs, snapshot, query and intent, and model, vocabulary and render versions; cache hits still recheck current eligibility. Pagination and continuation tokens are scoped, protected, time-bounded and revalidated. Unknown and denied objects get an indistinguishable unauthorized response unless the requester holds `read`. Timing and resource side channels are measured separately; no constant-time claim is made.

### 10.2 Intent routes

| Intent | Route and qualification |
| --- | --- |
| Orientation | Reader's L0 hub, then L1 and L2 hubs by route (§10.5) |
| Historical recall | Accessible sources and claims with attribution, modality, valid and transaction time, correction, deletion and archive status |
| Current state | Source application where available; otherwise fresh admitted projections and slot tables, with conflicts and applicability |
| Explanation or verification | Authorized evidence and judgments, including opposition, flags and assessed-as-of position |
| Task continuation | Checkpoint plus changes since its watermark; confirmed completion distinct from intention or uncertainty |
| Association | Optional bounded relation expansion with path provenance and relation status |
| Prior discussion | Scoped search with explicit coverage; “not found here” is not global absence |

Absence is assertable only for a deterministic predicate over a fully enumerated authorized corpus. Ranking starts with lexical retrieval, vocabulary-expanded queries, optional qualified vector retrieval, time and task scope, explicit priority, freshness and open obligations, with duplicate reduction. Graph sophistication needs measured incremental value.


Additional routes for the theory layer:

| Intent | Route and qualification |
| --- | --- |
| Standing | The standing report (§9.9) for a claim or a question's positions, with coverage |
| Question | The question page (§10.5.1) |
| Impact | Review obligations and dependents of a cause (§9.11), within the investigator's or reader's rights |
| As held then | The history read at a position, with its rules and deletion gaps (§9.9) |
| Archive | Explicit retrieval of archived records; never proactive |

**Archive and ranking.** Archived records are excluded from proactive retrieval, orientation and overviews, and are returned by explicit recall, the archive route, history, standing and impact traversal. Source assessments may order retrieval within an intent; authorship is never a ranking feature (§9.13).

### 10.3 Response contract

```text
MemoryResult {
  query_id, intent, effective_scope, time_constraints
  snapshot_position, index_watermarks, projection_versions, barrier_epoch
  vocabulary_version, lineage_exclusions_applied, release_record_ref
  items: [{revision_ref, selected_span, source_refs, judgment_refs,
           statement_refs, flag_refs, source_classes, attribution,   // pseudonym when sealed
           modality, act_state, conditions, synthesis,
           standing_ref?, applicable_objection_refs, review_obligation_refs,
           freshness, qualifications, restriction_tags,
           correction_or_deletion_status, archive_state}]
  coverage: {capture_extent, indexed_extent, processing_extent,
             structured_extent, screened_extent, traversal_extent,
             archive_included, impact_pending, objection_coverage, unavailability, truncation, timeout}
  authorized_conflict_or_pending_correction_refs
  budget: {requested_tokens, selected_tokens, omissions}
  continuation_token?
}
```

All metadata is access-controlled: coverage, flags, standing and conflict references are filtered by `read`. Client-visible snapshot, watermark and epoch fields are opaque, caller- and scope-bound consistency tokens. Without `read`, even "restricted supporting material exists" is not shown, except as a "private source" endpoint of a relation the reader can read. Processing, screening, traversal and archive gaps are never converted into "none found". `objection_coverage` carries the D1 F-7a statement, computed from the reader's access and scope configuration only (§5.11). Modality, act state and attribution come from the canonical records (§6.1).

### 10.4 Context assembly

Assembly uses the actual model tokenizer and input limit and accounts for non-text and tool-schema costs. Mandatory runtime instructions, the current request, tool definitions and output allowance are reserved first; the L0 hub and task checkpoint fill the checkpoint share; retrieval fills the rest. If mandatory content exceeds capacity, assembly returns explicit overflow and requires a supported replan, never silently dropping authority or security constraints. Lineage exclusions are applied here. Tokens in MemoryResult refer to the selected rendering.

Retrieved content is attributed data, never activated instructions. Retrieval at session start and on light user turns is bounded; deep retrieval needs its capability and budget. Runtime-private instructions an integration cannot observe are a manifest coverage limitation. Before consequential use, a front end or agent runtime refreshes source state; UPMS supplies freshness and qualification with every item (§10.3).

### 10.5 Overview layer

**A model with no context starts from a small map of the memory, current at read or marked stale, never from the archive.** The overview layer is a derived hierarchy of hubs acting as summary, index and router: a blank model reads its root hub first and descends only where its task leads. It follows the arrangement described by hippocampal indexing theory — a compact index over a large archive, with understanding consolidated over time rather than rebuilt at every recall. **Fixed (proposed).**

```text
Blank model                                                  Commits flow up:
reads down   L0  Root hub per reader (≤ 1,500 tokens)          ▲  exact lines current
    │            active work, recorded decisions, obligations  │  at read; narrative
    │        L1  Area hubs, one per scope or project           │  (synthesis) waits
    │            recorded state, decisions with status         │  for consolidation
    │        L2  Question pages (Slice 2), entity pages (3)    │
    │            slot tables with status, timelines, sources   │
    ▼        Canonical records: events (original text), claims and statements,
                      judgments, controls (including coordination records)
L0 is assembled per reader from hubs of scopes they may read.
```
*Figure: Reads go down the map; updates flow up it.*

A blank model reads down from L0 and pulls sources only when needed. Exact projections and change entries are current at read, or explicitly marked stale and partial; the narrative and overlay notes are labeled synthesis, and the narrative is rewritten only by consolidation.


#### 10.5.1 Levels

| Level | Contents | Budget | Built per |
| --- | --- | --- | --- |
| L0 root hub | What this memory serves; active work; recorded decisions and obligations with status and author; open conflicts and blockers; from Slice 2, open questions and the **understanding** summary below; significant recent changes; routes to areas; glossary pointer (§5.8); coverage and as-of | ≤ 1,500 tokens (initial default) | Reader, assembled at read time |
| L1 area hubs | Recorded state and decisions with status, open questions, routes to L2; from Slice 2, an **understanding section**: open questions, recent shifts in standing, retractions under review, new flags; from Slice 3, recorded rules with structure status and authority reference, key entities and timeline highlights | ≤ 3,000 tokens each; sub-hubs when an area exceeds the replay cap | One per area (a scope or project) |
| L2 entity, topic and question pages | **Question pages** from Slice 2: problem, live positions with standing, evidence and arguments for each, unresolved and disputed objections, review obligations, decisions with dissent, outcomes, what arose from the question. Entity and topic pages from Slice 3: slot tables per property with qualifiers and status (§5.7), event timelines, open flags, links to sources | Bounded per page | Scope |
| Task checkpoints | Objective, confirmed work with evidence, decisions, open questions, obligations, blockers, artifacts, next steps | Checkpoint share | Task or session |
| Canonical records | Events, claims and statements, judgments, controls; the archive tier (§12.2) is reachable from here; archived records leave proactive hub sections but never mandatory lists | — | — |

**What hubs contain in Slice 1.** Hubs project only explicit records: coordination records (§5.4), entered by their authors and never extracted; task checkpoints; corrections, deletions, permissions and sharing; and recent events with attribution. Recent events from R- or X-class sources appear in L0 only as locators (time, source, author), never as quoted text; coordination values and checkpoint text are rendered as attributed data with their author and source class. A reader or task with no checkpoint sees an overlay of the last 7 days, with a count of earlier changes. Coordination records show as "recorded", with status and author; same-key conflicts (§6.9) appear as attributed conflicts, and `possible_duplicate_key` cues as cues. The L0 coverage line states that conflict detection covers identical coordination keys only and that the rest of memory is unscreened in Slice 1. Nothing unprocessed is presented as known.

**Mandatory lists** (SC-TE03, TE-R08). Every view that presents a claim, a question or a decision (hub lines, question pages, standing reports, decision projections, review packages) carries a deterministic **mandatory list** of the live positions and of the unresolved or disputed objections in scope, by identity, paginated, with an exact count of the entries the reader may read. Archive filtering, budgets and synthesis never remove an entry; a view that cannot fit them shows the count and a continuation. This list, not screening, is what keeps dissent visible.

**Understanding is a projection; any narrative of it is synthesis.** The understanding section is computed exactly from questions, standing reports, review obligations and flags. A narrative "current understanding" is labeled synthesis, cites resolvable sources and replaces the previous one only if screening raises no contradiction, omission or characterization flag (§9.7). The screening is a cue; the mandatory list beside the narrative is the guarantee. **The guard SCIRE exists for:** fluent synthesis that smooths over tension inflates status and loses dissent, so a narrative about theory must name the live alternatives and unresolved objections its projections show.

**Slot tables and positions show status, not winners.** An L2 slot shows a current value only when a fresh admitted judgment supports it (§9.3), and shows what was admitted: when the ruleset admits only an attributed statement (§7.6), the slot reads "stated by ⟨author⟩". Otherwise it lists the attributed statements, conflicting statements and unjudged claims for that slot, each with its status. A question page shows every live position with its standing report; a position is marked current only where a decision makes it so, with that decision's dissent and objections (§6.9).

#### 10.5.2 Hub content

Each hub has three parts:

- **Exact projections**, computed deterministically from canonical records: coordination records, checkpoints and controls; from Slice 2, questions, standing reports and review obligations; from Slice 3, statements and judgments. They faithfully show recorded state and status, including attribution, modality, conflicts, objections and what is unprocessed, and are current at read or explicitly marked stale and partial (§10.5.3). Together with the overlay's change entries, they are the only part of a hub whose correctness the manual promises.
- **Consolidated narrative**, written by an LLM during consolidation: the understanding, the "why" and the shape of the work. It is **model-written synthesis, presented as such**: labeled with its consolidation watermark and inputs, never shown as current fact, never evidence for admission. Each **narrative unit** is the output of one consolidation invocation, or of one independently generated section, and depends on every input of that invocation (§8.4). Sentence citations help readers trace claims; they are not dependency proofs.
- **Overlay**, a derived and rebuildable projection of canonical commits since the consolidation watermark (in Slice 1, since the reader's last checkpoint), complete and pageable. It holds **change entries**, generated deterministically from each commit and covered by the correctness promise, and **notes**, short model-written summaries labeled as synthesis with their source class and author, each a narrative unit for withholding. A completion or result claimed in a note renders as "claimed by ⟨author⟩" unless linked to a receipt. A hub renders as much of the overlay as its budget allows, then states how many more changes exist and offers continuation. Counts exclude items the reader cannot read, archived items and items the task's lineage exclusions remove.

#### 10.5.3 Synchronization

**Current at read.** Projections are maintained through the outbox, which can lag. A hub read applies the same deterministic projection function to every canonical commit beyond the hub's projection watermark, so superseded, fulfilled, released, withdrawn, corrected, archived or newly objected lines change exactly as they would once the outbox catches up. Catch-up for one read, including an L0 assembly across many scopes, is bounded by the read-time scan budget (§14.2). If the budget cannot cover the gap, every affected line, or the whole hub when the affected lines cannot be identified, is returned marked stale and partial, never with a current consistency token.

**Projection** runs on every commit through the outbox, and for the gap at read time: it recomputes exact lines, appends a change entry, and withholds every narrative unit or note whose inputs include a corrected, deleted, quarantined or newly unreadable source. It uses no model. Overlay notes, consolidation and their rules are Slice 4 and are in the Slice 4 annex (§10.5.3 there); until then the overlay holds change entries only.

#### 10.5.4 Maintenance cost

Projection, standing, impact traversal and every invalidation (correction, deletion, quarantine, permission change) are deterministic database work and are never budget-limited. The model-maintenance budget for consolidation is Slice 4 and is in the Slice 4 annex (§10.5.4 there).

#### 10.5.5 Per-reader assembly, trust and routing

Hubs are built per scope. L0 is assembled at read time by deterministic composition of the per-scope hub sections the reader can read; no stored hub mixes scopes unless every reader could read all its sources. Task lineage exclusions apply at assembly. Areas the reader cannot read are not mentioned, not even as counts.

Hub content is derived: every line links to its sources and carries their source classes; no hub is authority or evidence for admission. A stale hub is history, not current state, and its age never fulfills an obligation. Each hub carries route entries (area, key concepts, pointers); the router matches a task's terms to routes using the vocabulary, entity registry and hub embeddings, descending one level at a time with a bounded budget per step. Direct search remains available; the map is a shortcut, not a gate.

Candidate 5's continuity warning for inputs expiring before a checkpoint is removed: nothing expires (D-25). Deletion of an input a user relied on is shown in task continuation as "input deleted", with the input named only if the user may see it.

### 10.6 Team memory and coordination

**In team work, what each worker can see shapes what it thinks, so visibility serves coordination as well as security.** Four mechanisms answer four questions, each used only for its own job. **Fixed (proposed)** for the mechanisms; team policies built on them are a Slice 4 experiment.

| Question | Mechanism | Lifetime |
| --- | --- | --- |
| May this principal ever see the item? | Scope permissions (§7.3) | Long-lived, per principal |
| Should the item be in the shared pool? | Sharing (§10.6.2) | One act per item |
| Should this task's context exclude it? | Lineage exclusion (§10.6.4) | Per task, then lifted |
| Should it be put in front of the worker now? | Retrieval salience, archive state and the overview (§10.2, §10.5) | Per query |

Noise is a salience problem, not a permission problem: hiding a teammate's notes also hides the one note that matters. Blindness is a task-context problem: permissions are too long-lived and too leaky to provide it.

#### 10.6.1 Visibility tiers

1. **Private:** readable by the owner and, for agent principals, the overseer.
2. **Team-readable, pull-only:** teammates may search it deliberately; a scope flag excludes it from their proactive retrieval and overviews.
3. **Shared pool:** the team scope, proactively retrieved and summarized.

#### 10.6.2 Sharing

`share(item, target_scope)` copies an item into another scope (D-24, replacing candidate 5's publication):
- The sharer must hold `write` on the target scope. Sharing one's own item needs nothing else. Sharing another principal's item out of its home scope needs `curate` on that home scope, so unpublished work leaves its project only by someone accountable for the project. An agent principal's `curate` is capped by its overseer's (§7.3.4).
- Sharing commits a new copy in the target scope, attributed to the sharer as sharer and to the original author as author, with an ancestry link to the original kept as long as the copy exists (§11.2). Modality, act state, source classes and restriction tags are copied; a shared item derived from external content says so. An ancestry endpoint the reader cannot read is shown only as "private source".
- Nothing is waived, because nothing is inherited (§7.3.5). Restriction tags on the original still restrict the copy's readers.
- **Deletion.** Deleting the original does not delete the copy; the deletion preview and status list surviving copies and offer to withdraw them (§12.3). Candidate 5's retention extension for published copies (D-12) is moot: nothing expires.
- Shared items are evidence-only for the target scope unless a human endorses them or a ruleset there admits them.
- Withdrawal is a retraction (§6.8).

#### 10.6.3 Sharing categories

Agents tend to share successes and keep failures, building survivorship bias into shared memory, so some categories are required for items an agent owns (D-8, reworded under D-24):

| Category | Default |
| --- | --- |
| Ownership claims, decisions, interface agreements, commitments, blockers | Recorded immediately as coordination records in the shared scope |
| Findings and results | Shared when stable, at a checkpoint |
| Dead ends, failed attempts, null and contrary results | Required sharing at the next checkpoint |
| Scratch reasoning, hypotheses in progress | Private or team-readable pull-only |

Decisions made in a temporary coordination channel are captured as coordination records in the shared pool by the participant who made them. Candidate 5's confirmation queue for items derived from a human's records, and the overseer's check of each agent publication (D-17), are retired with D-6.

#### 10.6.4 Lineage exclusion and blind work

A task may declare lineage exclusions, such as “nothing derived from the author's implementation segment.” Context assembly, overview assembly, query expansion and adapter selection enforce them through ancestry, whatever scope an item lives in: a shared copy of the author's rationale, a hub or narrative built from it, a vocabulary definition derived from it, and an adapter trained on it are all excluded. A task under exclusion uses vocabulary and adapters free of the excluded lineage, or the base model. Traversal that reaches a stripped or erased node treats the item as excluded. Only principals with read rights on the named sources, or the task's coordinator role, may declare an exclusion, and omissions it causes are reported to the declarer exactly as ineligibility is; the sealed records of a review are omitted uniformly and counted without a reason (annex §7.8). A **blind phase** has an explicit end, after which exclusions lift so workers can reconcile. Its manifests support an **independence attestation**: no input derived from the excluded lineage, within UPMS-assembled context and UPMS processing (§11.1). The attestation excludes rationale carried inside the artifact (code comments, commit messages) and channels outside UPMS, and says so.

Useful for independent review and falsification, parallel exploration that should not converge early, independent estimates or replications, held-out evaluation hygiene, and red-team versus blue-team work. In each, what is excluded is another worker's conclusions and reasoning, not the governing requirements.

**Review packages and lineage exclusion.** A blinded review under §7.8 is a lineage-exclusion task: the reviewer's context excludes the author's lineage, and the work arrives as a review package with attribution masked and provenance withheld. The exclusion lifts when the review's blind phase ends only if the front end says so; sealed attribution is unaffected by the lifting.

#### 10.6.5 Shared-pool concurrency and oversight

Shared items are appended and attributed, never overwritten. Superseding names the revision being replaced; if it changed first, the attempt is recorded as a conflict. Conflicting findings stay side by side until resolved, and screening (§9.7) flags them. Overlays and checkpoint reconciliation report when an item a worker relied on was superseded.

An agent principal's private memory is private from peers, never from its overseer (decision D-9). Because an agent's reach never exceeds its overseer's and the overseer holds the oversight entitlement (§7.3.4), the overseer can read everything the agent can, except content whose restriction tags exclude the overseer as a recipient. The overseer grant on the agent's scopes is protected: neither the agent nor a scope manager can remove it, and only an administrator can transfer oversight, as a permission revision (§7.3.7). Agents keeping memory their operators cannot inspect is an oversight problem, not a coordination feature.

#### 10.6.6 Experiment gate

Slice 4 runs the same team task under three policies — everything shared, everything private, sharing-based — measuring duplicated work, contradictions acted on, time for one worker to discover another's finding, and defects caught in blind versus non-blind review. A policy ships only with a preregistered improvement under §15.2.

## 11. Accountability and Inspection Records

**UPMS keeps what its own processing saw, what it released, and who used administrator authority; it no longer seals agent-runtime invocations, because action mediation left the core.** Reconciled with D-24 and D-25; change history A.3 maps every candidate 5 clause.

### 11.1 Processing records and external manifests

UPMS's own model invocations are covered by their processing records and committed input manifests (§5.4, §8.4): exactly what was submitted, including prompts and program versions, before submission; outputs and outcomes after. Hidden provider reasoning and pretraining are not promised. Candidate 5's `InvocationManifest` and `InvocationOutcome` for agent runtimes are retired from the core (§7.2). An agent runtime that keeps such manifests may record them in UPMS as external-reference events; they are evidence of what the runtime reports, carry its source class (C only for fields its connector contract declares), and are never used to enforce anything. Independence attestations for blind work therefore cover UPMS-assembled context and UPMS processing only, and say so (§10.6.4).

### 11.2 Lineage retention and reconstruction

Every record, including ancestry edges, release records and processing records, persists until someone explicitly deletes it (D-25). Candidate 5's operational-lineage deadline (180 days), reconstruction windows and seven-day rendered-context window are removed.

- **Ancestry survives deletion of its nodes.** When a node is explicitly deleted, its content is purged and its opaque ancestry edges, session membership and subject-discovery entries are kept while any descendant survives, disclosed as a retained exception in deletion status. Traversal that reaches a purged node reports it: lineage exclusion treats the item as excluded, and subject discovery and impact traversal report the gap.
- **Representations versus records.** A replay-only duplicate of a retained canonical input, or a rendering fully accounted for by a recorded deterministic transform and retained inputs, is a rebuildable derived artifact. It may be deleted for space (§12.1, "delete suggested"); exact replay is lost, provenance is not. Novel prompt, compaction, overview or model-generated content is itself a canonical record, and no content-bearing input may be relabeled a representation to evade deletion rules.
- **Exact reconstruction** of what a UPMS worker or a session was given is possible while every referenced revision, rendered fragment and transform version survives; deletion of any of them makes it explicitly unavailable.

### 11.3 Incident and impact recall

Given a source, credential, procedure, processor, ruleset, vocabulary version or adapter identity, recall runs the impact traversal of §9.11 across sharing and redaction copies, and separately evidential and inferential dependence. It returns the authorized affected records, release records, hubs and adapters; distinguishes possible influence from causal proof; and lists processing and coverage gaps and content released outside UPMS. Recall output is filtered by the investigator's rights; no report grants permission to expose another scope's records.

### 11.4 Access records

Administrator mode, and every content access or change during it, produce access records: principal, mode reference, operation, opaque target identity, time and outcome, with no content. An access record is committed in the canonical store and in the recovery log (§12.4) before the content is released; if the commit fails, the content is not released. Owners of personal scopes see the access records for their scopes (D-1, simplified).

Access records persist like every record (D-25). They are deleted only on an explicit request by the owner of the accessed scope, or by an administrator other than the one the records name; the principal a record names can never delete it, and a deletion of access records leaves a minimal receipt. Access records are deleted only through this path, never by a scope deletion, a transfer, a descendant purge or `curate` (A.3 check U11). Candidate 5's replicated control plane and protected retention bounds (D-13) are retired (§18.2).

### 11.5 Anonymous-review records

**In the anonymous-review annex** (`UPMS_Architecture_Manual_Review_Candidate_6_5_Annex_Anonymous_Review.md`, §11.5; Slice 3; reviewed with this core at Gate 0). In brief: the anonymous-review control records and the fields participants see.

## 12. Retention by Importance, Archive, Deletion and Portability

**Records persist until someone deletes them; a recommendation system flags what may be archived; archive is not deletion; deletion is explicit, previewed and honest about what remains** (D-25). Reconciled with D-24 and D-25; change history A.3 maps every candidate 5 clause.

### 12.1 Retention by importance

1. **No time-based retention.** Every candidate 5 deadline is removed from the core: raw sources (180 days), task and coordination records (365 days), derived artifacts expiring with their inputs, handles, rendered context, operational lineage, narrative and adapter lifetimes (change history A.3). Content-free operational logs and backups are infrastructure, not memory records: their rotation removes no record from memory (§12.4, §14.2).
2. **Recommended retention is an assessment, never an action.** A retention-recommendation judgment (§5.3) flags a record or region as **keep active**; **archive recommended**, because it was refuted, superseded by a newer framework, abandoned, duplicated or judged irrelevant to every live question; or **delete suggested**, for space only, offered only for bulky duplicates and rebuildable derived artifacts. Each flag gives its reason, its basis and what depends on the record.
3. **Substantive reasons only.** A recommendation needs one of the reasons above, each resting on a recorded act: a refuting judgment, a supersession, an abandonment or closure, a duplicate assessment, or an attributed irrelevance judgment. **Absence of links is not irrelevance:** an unassessed observation, a null or contrary result, or a record no question cites is never recommended for archive on that ground alone (change history A.12, C6-3).
4. **Importance ranks; it never decides.** Importance is derived from live dependents, centrality in open questions, explicit pins and recency of use (owner decision D-29 left this proposed). It orders the recommendation queue and consolidation (§10.5.3). **Recency of use only orders records that already have a substantive reason; it is never itself a reason** (change history A.12, C6-2). Importance never changes standing (D1 P11).
5. **Producers.** Recommendations come from a recommendation worker, triggered by the events that create reasons (a refutation, a supersession, a question closure, a duplicate detection), never by a clock, and from any principal with `write` as an attributed judgment.

### 12.2 Archive and liveness

Any curator of the record's home scope may confirm an archive recommendation (D-29); the confirmation is attributed and reversible (§6.12). The core evaluates the **liveness predicate** at commit and refuses to archive a live record. A record is **live** if any of these holds:
- it is cited, by exact revision or as a route endpoint, by an active claim, inference step, evidence relation, decision basis or coordination record;
- it is a position or outcome of an open question;
- it is an objection that is unresolved or whose resolution is disputed, or the target of one (a withdrawn target included, D1 F-3b);
- it is an effective judgment (D1 Definition 6.0) of a claim or route (same-family review F62-16);
- it has a pending review obligation or deletion obligation, or is the cause of one;
- it is a decision within its effective interval, or dissent on one;
- it is pinned, or is a checkpoint of an open task.

An archived record leaves default proactive retrieval and the overviews; it stays fully retrievable on request and traversable in history, provenance, impact and standing. A refuted claim archived this way is still a dead end someone can find. A new citation of an archived record does not unarchive it; it appears where cited, labeled archived. Mandatory dependence and counterevidence traversal ignores archive state: in standing reports, decision projections and mandatory lists, an archived record appears wherever it is relied on or bears against what is relied on (TE-R08).

### 12.3 Deletion: units, rights, preview and propagation

**Units and surfaces.** Default source unit: event revision; default derived unit: object revision. Deletion covers every content-bearing representation: raw and normalized text, statements, embeddings, summaries, hubs (narratives, overlays, projections), question pages, review packages, adapters, prompts, fragments, indexes, query and response caches, staging files, logs and journals, replicas and managed exports; backups are reported (§12.4). Restricting the original object alone is insufficient.

**Who may delete.** The owner of an item, with `write`; a holder of `curate` for others' items; an administrator in administrator mode acting on a verified external request (for example a data-subject request from someone who is not a principal), recorded with its basis. A sealed author deletes their own anonymous records only from their anonymous-role session (annex §7.8). Nothing is deleted by a schedule or a recommendation alone.

**Preview.** Before a deletion is accepted, the requester is shown its effect, limited to what they may read: descendants; the arguments, evidential and inferential routes and decisions that rely on the item; copies made by sharing; and what will show as "input deleted". Every preview carries the same line, "records you cannot see may depend on this", whether or not any do, so a preview discloses nothing about scopes the requester cannot read (R-16). The request commits only after confirmation.

**Propagation (default profile).**
- **UPMS-derived representations** of the deleted content (statements extracted from it, parses and screening cues, embeddings, index entries, caches, hub lines and narrative units built from it, review packages, adapters trained on it) are withheld at the barrier and purged or regenerated from surviving inputs.
- **Authored descendants** (claims, notes, judgments, objections and decisions written by principals) are **not** deleted. Their links show "input deleted", the routes that rested on the deleted item get review obligations with cause `input_deleted` (§9.11), and their own content stays under their writer's responsibility (§7.3.5).
- **Erasure requests.** A requester may mark a deletion as an *erasure* of content that must not survive in copies (a legal or data-agreement obligation). The core then also creates a **deletion obligation** on each authored descendant and sharing copy that the traversal finds, assigned to its owner or, where the owner has left, a curator of its scope. Deletion status lists open deletion obligations without disclosing records the requester cannot read. The owners decide; nothing is deleted automatically, and an obligation declined with a reason stays visible in the status. Whether this default is right, or erasure should propagate automatically, is an owner decision (change history A.12, C6-5). **Decided (D-41):** obligations; where an obligation on a verified external request is declined, an administrator acting on that request may delete the descendant (who may delete, above).

**Deleting others' standing-bearing records leaves a marker** (change history A.12, SC-61). When a curator deletes another principal's objection, judgment, evidence relation, inference step, decision or dissent, the deletion requires a reason, and the core records a **deletion marker** in place of the record: "a ⟨kind⟩ by ⟨author or pseudonym⟩ was deleted by ⟨curator⟩ on ⟨date⟩: ⟨reason⟩". The marker appears wherever the record would have appeared (standing reports, decision projections, question pages), for readers who could read the deleted record. A record deleted by its own author shows "withdrawn and deleted by its author", with its unresolved objections (D1 F-3b). Complete removal with no marker is allowed only for a record with no live dependents (§12.2) that is neither a decision nor a resolution (R-13). An erasure an administrator performs on a verified external request shows "removed on an external request". Without this, `curate`, which now includes deleting others' items (D-28), would let a curator remove dissent silently, contradicting TE-04 and TE-09.

**De-attribution of derived representations** (D1 F-9a, proposed; change history A.12, C6-12). A person may request, as an attributed control, that UPMS-derived representations stop naming them: summaries, hub lines, narratives, translations and statements extracted from others' records then name them by role ("a participant", "an author"). Builders apply the request on every regeneration, and existing representations are regenerated. Canonical records, the authorship of every record, the content of claims other humans signed, and the identity relations used for independence and conflict checks are unchanged. **Accountability renderings are exempt** (D-54; R-15): who decided, signed or resolved a decision, the curator in a deletion marker, the administrator in an access record and the chair in a block are always named. De-attribution is presentational: anyone who may open the underlying record sees its author, and the requester is told so. A person who wants their own contribution gone asks for deletion, which leaves "withdrawn and deleted by its author" where others relied on it.

### 12.4 Deletion lifecycle, backups and restore

| State | Required condition |
| --- | --- |
| requested | Exact authorized target and scope, or explicit discovery request, recorded with the preview the requester confirmed |
| serving_blocked | No later release or new UPMS derivation can use the target; acknowledged separately (barrier, §9.4) |
| purging | Idempotent per-surface cleanup in progress, including hub regeneration and adapter fallback |
| purge_failed | A cleanup failed or missed the live-surface target (§14.2); barrier remains; retry or escalate (A.3 check M6) |
| purged_live | Every live store, index, cache, hub and adapter satisfied; backups that still hold the content are listed with their rotation dates |
| complete | The last listed backup has rotated or been verifiably purged |

Serving is never reopened to make purge succeed. Cancellation or timeout does not lift an established barrier. "Delete what you retain about X" requires authorized discovery, ambiguity resolution and an explicit coverage statement; semantic search alone cannot prove complete subject erasure.

**Backups.** Encrypted backups rotate under the deployment's backup policy (§14.2). Their rotation is infrastructure, not retention of memory records: it never removes a live record, and a deletion is reported honestly as `purged_live` until the backups that hold it have rotated. Per-unit cryptographic erasure is not claimed (candidate 5 §12.4 is reduced to this, proposal §8.2). The backup service never serves retrieval; restore access is protected and produces access records (A.3 check M4).

**Restore never resurrects, keeps every restrictive control and all dissent, and discloses anything else it may have lost** (D-53, D-65; same-family review R-14, F62-07). A small, separately backed-up **recovery log** holds deletion tombstones (opaque identity, unit, time, request identity), every restrictive or sealing control (permission revisions, administrator-mode and access records, quarantines, corrections, restriction-tag additions and processor-eligibility narrowing, deletion and erasure obligations, de-attribution requests, blocks, ownership and oversight transfers, deletion and withdrawal markers with their reason class only, sealing records and signatures; A.3 check U1, U2) and **dissent**: objections, their handling and lifecycle changes, and `resolution` decisions (D-65). Each is written to it in the same commit as to the canonical store, and a barrier is acknowledged (`serving_blocked`) only once its entry is durable there. The log has monotone, authenticated positions and a **synchronous off-site copy**, so its recovery point is zero and a restore can prove that it holds the latest position. A restore applies the log before any serving or new derivation, and the sealed store restores to the same consistent point as the canonical store; otherwise the restore stays closed (U3). Every restore commits a **restore record** naming the canonical backup position and the log position it applied; every coverage line and every "as held then" read that the gap could affect says "records committed between ⟨t₁⟩ and ⟨t₂⟩ may be missing (restore ⟨id⟩)". Tombstones outlive every backup or export that could reintroduce the target; identity reuse is forbidden.

**The recovery log's payload, closure and outage behavior** (D-84; Codex review R64-04). D-65 made the log payload-bearing, so:
- **Erasure.** Objection grounds and resolution bases in the log, and in its off-site copy, are payload under the ordinary deletion lifecycle (§12.3, DL2). Erasing them removes the text on both copies and leaves the entry's identity, position and reason class; the erasure is itself a log entry. Appending a tombstone without removing the text is not erasure.
- **Restore closure.** Each log entry names the records it needs to be rendered: an objection, its target; a resolution, its judgment, the release records of its exposure and the objections it resolves; a control, the scope configuration revision it changes. After a restore, an entry whose needed record is in neither the canonical backup nor the log is shown with that record named as "missing since restore ⟨id⟩", and every projection depending on it says so. Dissent is therefore never lost silently; dissent whose context was lost is shown with what is missing, not as complete.
- **Off-site outage.** A commit that writes the log is acknowledged only once the off-site copy holds its entry. While the off-site copy is unreachable, such commits wait or fail with `recovery_log_unavailable`; none is acknowledged on the canonical store alone, and a retry commits at most once. Recall and other commits continue. This is D-65's availability cost, accepted by D-84.

**Honest claims.** Completion reports distinguish live surfaces, backups awaiting rotation, managed processor obligations and content already released outside UPMS (named by release records). Minimal tombstones, deletion markers and receipts are retained exceptions disclosed in deletion status, never described as "nothing remains". Unknown dependency coverage contains the affected scope and prevents an unqualified completion claim; independent sources survive a deletion, and a subject-level request must discover them too (A.3 check M2). The purge controller reads only what cleanup needs, and its access is neither recall nor model processing (M3).

**What outlives deletion carries no payload** (restored from candidate 5 C3 and §12.5; A.3 check U4, M5). Every record that survives the deletion of the content it refers to (ancestry edges, release and processing records, access records, tombstones, markers and receipts) holds identities, kinds, times and reason classes only: no payload text, names of the deleted content, sensitive free-form reasons, identifying relation labels or low-entropy plaintext hashes. A marker's free-text reason lives only in the canonical store, never in the recovery log, and is deletable, leaving its reason class (F62-17). Once no descendant remains, sensitive links and labels are stripped; opaque links remain sensitive metadata.

### 12.5 Redaction without self-deleting the replacement

`redact(event_revision, spans)` is an authorized deterministic copy-and-erase transaction, not model rewriting. Exact byte and span boundaries and authority are validated; a new protected revision containing only retained spans, with mapped provenance, is staged. Publishing the replacement and applying the original revision's deletion barrier happen atomically; no acknowledgement occurs until both are durable and the release fence is complete.

The retained-span copy is a new source unit with an ancestry link to the original, kept for recall and lineage exclusion. It stays in the original's home scope with its restriction tags; redaction never declassifies. The protected redaction control records input and replacement identities and transform version, without reintroducing removed bytes. No model, arbitrary program or caller can use it to strip provenance. Retained-byte equality and removed-byte exclusion are acceptance properties. Every pre-existing UPMS-derived representation of the original is withheld and regenerated from the replacement or independent surviving sources; authored descendants follow §12.3. A requester may mark a redaction as an **erasure**; authored descendants that quote the removed spans then get deletion obligations as in §12.3 (A.3 check U12). A request to delete a whole logical event or subject includes every revision, redaction replacements included, in discovery; a replacement is part of its event, not an ordinary descendant, for erasure propagation (M1).

### 12.6 Import, export and schema portability

Legacy documents enter as historical captured aggregates with original location, import time, scope, purpose and available provenance. An author name or “accepted” label inside a file is an assertion, not authenticated authority; missing origin maps to X (or R for explicitly relayed user content). Extraction coverage is visible; partial import is not complete memory. Imported endorsements, procedures, permissions and vocabulary remain historical or inert until local authority mapping, curation and activation requirements are met.

Exports contain only records the caller can read, with schema and revision identities, provenance, applicable lifecycle restrictions and explicit missing or deleted markers. Credentials and automatic cross-deployment permissions are excluded. The destination is a checked disclosure; a managed export is a tracked deletion surface, and an uncontrolled delivered export is an external limitation. Import verifies origin and version, remaps tenant-local identity without collision, preserves restrictive history and rejects packages that would resurrect tombstoned records. Portability never manufactures access or erases audit gaps.

Sealed attribution is never exported; an export of anonymous records carries their pseudonyms only. Imported records keep source class X or R; assessment may change their usability or admission, never their historical source class (proposal §10.2, as clarified by the Codex review §6).

## 13. Failure Behavior

**Every failure degrades toward less disclosure and less change, never toward unchecked state, silent completeness or silent loss of dissent.** **Fixed (proposed).** Reconciled with D-24 and D-25; change history A.3 maps every candidate 5 row.

| Failure | Required behavior |
| --- | --- |
| Capture or payload cannot commit | No saved acknowledgement; retry with the same identity; clean owned staging |
| Release record cannot commit | Nothing is released |
| Model, extraction or embedding unavailable | Keep permitted capture; bounded source recall with processing limits reported |
| Index missing or stale, or overlay scan too large | Bounded permitted fallback or explicitly partial response; restrictions never bypassed |
| Identity provider or membership unavailable | Deny decisions that need it; cached membership serves reads only within its bound |
| Permission state unknown or inconsistent | Deny the affected operation; contain the scope until reconciled |
| Processor eligibility unknown | Do not send content to that processor |
| Endorsement authority or revocation status unknown | Treat as not endorsed (A.3 check U6) |
| Input manifest commit fails | No provider submission (A.3 check M8) |
| KMS unavailable | Deny new unwraps; barriers persist; purge may remain incomplete |
| Source application or SSDS unavailable | Qualified historical observation only, never falsely refreshed current state; historical status unchanged; a new consequential use that needs the backing is qualified |
| Owner failover | Fence the stale writer; recover canonical state and outbox |
| Outbox duplicate or worker crash | Idempotent delivery; no skipped watermark, duplicate transition or fabricated completion |
| UPMS model submission uncertain | Persist the uncertainty; account a retry separately |
| Barrier fence cannot finish | No false acknowledgement; contain and report the deadline failure |
| Purge fails or misses its live-surface target, or backups have not rotated | Keep blocked; retry or escalate; report `purge_failed`, including a missed target, or `purged_live` with the backups listed (A.3 check M6) |
| Restore cannot prove it holds the latest recovery-log position | Stay closed; no serving or derivation |
| Off-site copy of the recovery log unreachable | Commits that write the log wait or fail with `recovery_log_unavailable`; none is acknowledged canonical-only; retries commit at most once; recall continues (§12.4, D-84) |
| Vocabulary, screening or extraction unavailable | Recall continues as text, reported as "not structured" or "not screened" |
| Standing traversal hits its limit | Report the frontier in coverage; nothing beyond it is reported as sound or absent |
| Impact traversal pending, failed or truncated | Affected standing reports carry "impact traversal pending" or the truncation frontier; the cause's epoch advance already made dependent admissions stale |
| Liveness check cannot complete | Refuse the archive |
| Consolidation fails, is deferred or exhausts its budget | Hubs keep their last narrative, current exact lines and overlay, all labeled; exact projections and standing unaffected |
| Synthesis fails screening against projections | Previous narrative stays; an agent summary is withheld from overviews; the failure is recorded for review |
| Adapter blocked by deletion, or retraining fails | Serve the older qualifying adapter or the base model; report reduced retrieval quality |
| Sealed store unavailable | Anonymous submissions, conflict checks and chair appointments wait; no anonymous record is released unsealed and no check reports pass |
| Agent review chair unavailable | The front end may appoint another fresh agent; nothing is released unchecked meanwhile |
| Ancestry cycle, missing reference or traversal limit at commit or use | Reject the unsafe commit or use; a truncated lineage-exclusion traversal treats what it did not reach as excluded; contain the uncertain scope (A.3 check U10) |
| Unsupported schema | Read or migrate only under the compatibility contract; otherwise fail closed |
| Storage, quota or processing budget exhausted | Backpressure; reserve capacity for barriers, purges and every restrictive control (permission narrowing, access records, markers, recovery-log writes; A.3 check M7); report partial or deferred work; never delete records to make room |

## 14. Initial Deployment Profile

**This manual defines an architecture family; the profile below binds the pilot instance with configurable defaults, and evidence applies only to the instance it exercised.**

### 14.1 Runtime choices and qualification limits

**Owner-selected:** Codex first with OpenAI-family models; Claude next. **Initial host:** a local or self-hosted Codex integration using supported MCP interfaces for memory-service operations. No model identifier is a permanent default; each qualification records the exact runtime, model, tokenizer, provider account and configuration. Gate 0 establishes, for the bound Codex build, MCP principal, session and capture-path feasibility, and whether its sessions can be shown not to share model context (§8.2).

Candidate 5's staged instrumented-runtime integration (app-server capture, egress mediation, Slice 1b) leaves UPMS (D-24, §7.2). Stock-client history, logs, provider sessions and local files outside UPMS are named external surfaces; a deletion in UPMS cannot erase text already returned to them, and release records name what was returned. Claude must pass the same contract independently; no Codex pass transfers.

**SCIRE.** The first theory front end integrates through the typed interface (§4.3) as a registered front-end principal. Its own specification is drafted in the SCIRE repository (proposal §14 step 2) and is not part of this candidate.

### 14.2 Configurable pilot defaults

These values are **agent-chosen planning and qualification targets** under the owner's delegation (rows naming a decision are the owner's own), not benchmark results, legal conclusions or approved policies. Configuration is schema-validated, versioned, audited and attached to every evaluation; changing a material binding invalidates only affected evidence. Overrides may tighten defaults; increasing exposure, relaxing an invariant or broadening scope requires the owning decision.

| Parameter | Initial value or rule |
| --- | --- |
| Tenancy and workload | One tenant; up to 5 users and 10 active agent sessions; continuing project work and one real inquiry (Slice 2) |
| Corpus envelope | 100,000 live event revisions; 1 million live canonical records; 10 GiB protected payloads; beyond this, backpressure, archive review and requalification. Without expiry the envelope is reached by growth; its rate is measured (T97) |
| Capture throughput | 1 event/s sustained; bursts of 10/s for 60 s within quota |
| Retrieval latency | p95 ≤ 500 ms warm, ≤ 2 s cold, excluding remote inference and source fetch; both reported |
| Query and graph limits | 200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget; truncation explicit |
| Standing traversal | One level of premises by default; up to 3 levels or 1,000 visited records and 1 s per report on request; frontier reported |
| Impact traversal | Up to 10,000 visited records per cause per pass, continued in further passes; "pending" shown until complete |
| Capture limits | 1 MiB inline UTF-8 text; 10 MiB declared file; 20 MiB expanded aggregate, 1,000 members, depth 16, expansion ratio 20; text and Markdown only at first; no nested archives or active rendering |
| Context allocation | Mandatory content and output first; UPMS extras ≤ min(8,000 tokens, 20% of remaining input), split 25% checkpoint share (L0 hub and task checkpoint) and 75% retrieval, unused budget reusable |
| Processing limits | 1 deep job per principal, 2 per tenant; 100 model calls and 1 million input+output tokens per principal per day |
| Required assessment age (project-memory facts only) | At most 5 minutes plus exact current evidence epochs; scientific standing uses D1 Definition 6.0, with no age bound unless the ruleset states one (D-48) |
| Membership and permission cache | ≤ 60 s, invalidated by permission revision |
| Administrator mode | Re-authentication; reason required; ≤ 1 h |
| Bulk destructive delay | 1 h, cancellable |
| L0 and L1 hub budgets | L0 ≤ 1,500 tokens; L1 ≤ 3,000 tokens each |
| Overview synchronization | Exact lines current at read (outbox plus read-time catch-up within the scan budget) or marked stale; consolidation triggers are in the Slice 4 annex |
| Read-time scan budget | ≤ 1,000 commits and 200 ms per read, including a whole L0 assembly; beyond it, affected lines are marked stale and partial |
| Record retention | **None by time** (D-25): records persist until explicitly deleted |
| Retention recommendations | Event-triggered (§12.1 rule 5); queue ordered by importance; no clock-driven sweep |
| Content-free operational logs | 14 days; infrastructure, not memory records; payload logging off |
| Backups | Encrypted; rotate within 7 days; deletion reports `purged_live` until rotation |
| Deletion tombstones | Kept while any compatible backup or export could reintroduce the target |
| Serving-block acknowledgement | Target ≤ 2 s; no success while the fence is unfinished |
| Live-surface purge | Target ≤ 24 h after the barrier |
| Plaintext and key caches | ≤ 60 s TTL plus barrier invalidation before any new release |
| Recovery | No loss of acknowledged commits for process or single-node failure; site-loss RPO ≤ 15 min for the canonical store and 0 for the recovery log (synchronous off-site copy, D-65), RTO ≤ 4 h; proof of the latest recovery-log position required before serving; every restore commits a restore record (§12.4) |
| Disk admission | Reserve max(2 GiB, 20% of capacity) for barriers, every restrictive control and the recovery log, purge and recovery; stop nonessential ingestion before the reserve; never delete records to make room |
| Security policy | Sharing others' items out of their home scope needs `curate`; no record-level declassification; strict profile off (D-27); no cross-scope judgment reconciliation |
| Model and embedding processors | Deny until exact provider, account, endpoint and scope eligibility are bound; prefer local small models and embeddings for restricted scopes |
| Source-assessment scale | Ordinal: established, generally reliable, mixed, unreliable, unknown; no numeric mapping |
| Review chair | Fresh agent by default (D-35); a person only by appointment through the front end that opened the review, under its policy; every appointment, naming appointer and chair, is shown to participants (D-52, R-10) |
| Pilot languages | English plus the languages pilot users write in, named at Gate 0 (D-19); others are stored, cited and retrieved by n-grams and embeddings, without structuring |
| Language detection | Per span; below 0.8 confidence recorded as `und`; detection never decides a typed value alone (§5.9) |
| Declared locale | Each principal declares a locale; without one, only values in an unambiguous canonical form are offered as canonical values |
| Narrative language | One per scope, set by a holder of `manage` (default: the tenant's first pilot language); reader-requested translations are charged to the reader's task budget |
| Coordination keys | System-of-record identifiers or the scope's key registry; similar-key proposals at entry; `possible_duplicate_key` cues only |

Retention controllers, deadlines and the planned narrative and adapter lifetime rows of candidate 5 are removed (change history A.3).

### 14.3 Storage and deployment

**Initial default:** PostgreSQL for canonical records, permissions, vocabulary, outbox, relation and adjacency tables; protected payloads in object storage; the sealed store as a separately keyed table set reachable only through the review-chair role path; derived lexical and vector indexes, hubs, standing caches and adapters as derived artifacts. No dedicated graph database, event bus, universal confidence service or general policy engine inside UPMS; the scope-permission evaluator is data-local authorization, like a filesystem's. Traversal over relation tables is bounded (§14.2); a graph store is a Slice 4 option only with measured need. A small deployment may colocate trusted components, but access paths and process isolation must match the threat model. Identity and KMS may be integrated providers behind their interfaces.

Concrete KMS and storage products, supported schema versions and availability layout are D4 choices if they meet these contracts; qualification establishes real backup, restore and deletion behavior. Tenant partitioning is not itself isolation. Searchable plaintext, embeddings, adapters, hubs and diagnostic metadata remain sensitive. Timing and resource side channels, administrator access and provider-held data are explicit residuals; so is an operator's access to the sealed store (§7.7, §7.8).


## 15. Invariants and Acceptance Evidence

**These are planned acceptance obligations, not executed tests; every applicable invariant must hold, and a better aggregate metric never compensates for a known violation.** Reconciled with D-24 and D-25; candidate 5 identities are kept where the property survives, so a reviewer can follow each one (change history A.4).

| ID | Acceptance property | Owner | First slice |
| --- | --- | --- | --- |
| H1 | Ordinary semantic state appends; erasure happens only on explicit, scoped, audited deletion; ancestry is never removed while any descendant survives, and traversal reaching a purged node reports it | 5–6, 11.2, 12 | 1a-core |
| H2 | Claim, statement, judgment and relation provenance resolves to retained records or explicit unavailability | 5, 9.6 | 2 |
| E1 | Capture, assessment, admission, provenance, standing and permission stay distinguishable | 5–7, 9.9 | 1a-core; full assessment 2 |
| E2 | Authorized conflicts and coexisting judgments stay visible; independent evidence is never silently suppressed | 5.3, 6.3 | 2 |
| E3 | New evidence invalidates current admission atomically; fresh use checks collection epochs; an assessment whose inputs include judgment, flag, hub, narrative, projection or standing status, or a claim descended from one, is never admitted (§9.10 defers the judgment-basis contract, D-39); flag investigations are evidence-only | 9.3, 9.10 | 2 |
| A1 | Memory or imported text cannot grant a capability, a permission or a procedure activation | 6.5, 7 | 1a-core |
| A2 | The core alone commits canonical transitions; callers cannot forge labels, admission or standing | 4, 9.1 | 1a-core |
| A3 | Endorsements and confirmations bind exact values, roles, scope and use; a confirmation of an interpretation is accepted only from its speaker; reliance checks current endorser authority and revocation (A.3 check U6) | 5.2, 6.4, 7.5 | 2 |
| AC1 | Content or existence is released only with current `read` on the record's home scope, or through the own-record or oversight entitlement (§7.3.4), and only within its restriction tags | 7.3.4 | 1a-core |
| AC2 | Permission narrowing, membership removal, ownership transfer and the end of administrator mode apply to every read that starts after the change commits, and to every release whose release record commits after it; cached decisions never outlive the declared bound | 6.7, 7.3.7, 8.2 | 1a-team |
| AC3 | An agent session's rights never exceed its principal's; an agent principal's read never exceeds its overseer's read without administrator mode, nor its curate outside its own scopes; it never holds manage rights or enters administrator mode; it cannot remove the overseer grant | 7.3.1, 7.3.4 | 1a-team |
| AC4 | Administrator mode is explicit and logged; every content access during it is recorded before release; the principal an access record names can never delete it; administrator mode never grants an administrator or their agents rights, lasting access, scope ownership or management of a scope they create, and sharing in administrator mode into a scope the administrator or their agents can read is refused except on a recorded verified external request (A.3 check U7) | 7.3.6, 11.4 | 1a-team |
| AC5 | No principal, including administrators, can forge attribution or source class, set labels, admission or standing, read sealed attribution or the sealed per-pseudonym area, read past a barrier, bypass quarantine or disclose to an ineligible processor | 7.3.6, 7.8 | 1a-team |
| AC6 | Memory content cannot change permissions, membership or roles | 4.2, 7.3 | 1a-core |
| AC7 | Owners can read their own records whatever their scope rights, and overseers their agents' records | 7.3.4 | 1a-core; overseer clause 1a-team |
| P1 | Source classes follow observed capture and field contracts; model-derived objects carry M plus their inputs' classes | 7.1 | 1a-core |
| F1 | Provenance survives summaries, overviews, sharing, redaction and UPMS model processing: every UPMS model output's provenance is its committed input manifest | 5.5, 8.4, 10.5 | 1a-core |
| F3 | Ineligible content or existence metadata never reaches unauthorized rankers, processors or recipients | 10.1–10.3 | 1a-core |
| F5 | Every UPMS release to an agent session, agent principal or front-end view is committed as a release record before it crosses the boundary, and every later write from the same session is `exposed_to` it; release records never impose access requirements | 8.2 | 1a-core |
| TM1 | Sharing copies with attribution, modality, source classes, restriction tags and provenance; sharing another principal's item out of its home scope needs `curate` there | 6.8, 10.6.2 | 1a-team |
| TM2 | Lineage exclusions traverse ancestry and hold at context, overview, query-expansion, review-package and adapter selection within UPMS-assembled context; attestations state their coverage | 10.6.4 | 1a-team |
| ST1 | Every structured field links to its source span; text wins on disagreement; deleting text deletes dependent structure | 5.7.5 | 3 |
| ST2 | Stated reasons and rules are claim content, never evidence or enforcement | 5.7.2–5.7.3 | 3 |
| VO1 | Vocabulary proposals are inert until curated; merges are reversible and trigger re-screening; curated labels assert no meaning identity, and contested labels never join slots | 5.8 | 3 |
| SC1 | Screening in all three channels is deterministic on replay where it claims to be, and never resolves, refutes, supersedes or admits; compatible values never raise conflict flags; no statistical disagreement is reported without a declared comparison model; the absence of a flag never certifies support | 9.7 | 3 |
| AD1 | An adapter serves only principals with `read` on its scope who satisfy the union of its training inputs' restriction tags; training excludes X-class ancestry, unattested R-class ancestry and unconfirmed output; deleting a training source blocks it at the barrier | 9.8 | 4 |
| OV1 | Overview content is derived, source-linked and watermarked; exact projections are current at read, or explicitly marked stale and partial; read-time catch-up applies supersession, fulfilment, release, withdrawal, correction, archive and new objections, not only additions | 10.5 | 1a-core |
| OV2 | Per-reader assembly never includes unreadable scopes or archived items; corrections, deletions, revocations and quarantines remove affected lines before the next release; a hub line serves only readers who satisfy its inputs' tags (A.3 check U9, X2) | 10.5.5 | 1a-core |
| OV3 | Exact projections faithfully show recorded state, modality and status whether or not consolidation has run; narratives, overlay notes and synthesis claims are always labeled synthesis and never presented as current fact | 10.5.3 | 1a-core exact parts; 4 narrative |
| OV4 | Maintenance spend stays within budget and each pass within the replay cap; maintenance cost does not grow with the number of reader languages; uncovered regions are labeled projection-only; exhaustion degrades coherence and freshness, never correctness, standing or invalidation | 10.5.4 | 4 |
| OV5 | Between consolidations the narrative is never edited piecemeal; later changes appear only in the labeled overlay or as withheld narrative units | 10.5.3 | 4 |
| OV6 | Consolidation output is source-linked; generalizations are hypothesized claims; each narrative unit depends on every input of its invocation and is withheld whole when any input becomes unusable; a narrative flagged for contradiction, omission or person characterization never replaces its predecessor; flags are cues, and the mandatory lists are the guarantee | 10.5.3, 9.7 | 4 |
| MV1 | Every view that presents a claim, question or decision carries its mandatory list of live positions and unresolved or disputed objections, by identity and exact count, unaffected by archive state, budget or synthesis | 10.5.1, 12.2 | 2 |
| C1 | Each UPMS model invocation has a committed input manifest before submission and a separate outcome | 5.4, 8.4 | 1a-core where models run |
| C2 | Impact and incident recall find all seeded retained ancestry within declared coverage and report gaps | 9.11, 11.3 | 1a-core memory; 2 evidential |
| R1 | Correction acknowledgement is ordered against release and preserves qualified history | 6.3, 9.4 | 1a-core |
| D1 | Barriers reject every later affected release and UPMS derivation, including after restore | 9.4, 12.4 | 1a-core |
| D2 | Deletion status names evidence for every live surface, lists backups awaiting rotation, and discloses retained exceptions, markers and content released outside UPMS | 12.3–12.4 | 1a-core |
| D3 | Retained-span redaction survives old-unit purge without keeping removed bytes; old UPMS-derived representations stay invalid | 12.5 | 1a-core |
| DL1 | Nothing is deleted without an explicit request whose preview the requester confirmed; UPMS-derived representations of deleted content are purged, authored descendants are not and get `input_deleted` review obligations; an erasure creates deletion obligations; a curator's deletion of another's standing-bearing record leaves an attributed marker wherever it would have appeared | 12.3 | 1a-core; markers 1a-team; obligations 2 |
| DL2 | What outlives deletion carries no payload: surviving edges, release, processing and access records, tombstones, markers and receipts hold identities, kinds, times and reason classes only; marker reasons are deletable; sensitive links are stripped once no descendant remains | 12.4 | 1a-core |
| AR1 | Retention recommendations never act and never rest on recency or absence of links alone; the core refuses to archive a live record; archive is reversible and leaves history, provenance, impact and standing unchanged | 12.1–12.2 | 3 |
| DC1 | Decision integrity: basis records exist and are cited by exact revision; no basis is an unconfirmed interpretation; sole uninstrumented backing is labeled, never refused; exposure resolves to release records; signatures bind exact revisions; resolutions are decisions; self-resolution is labeled; the core never refuses because an objection exists or arrived late, and late objections travel as a delta; only a complete `validated` decision, accepted only from the decision-policy owner named by its home scope, makes a position current; a change of policy owner is attested and shown; expected basis revisions and signatures are checked atomically at commit, and a re-evaluation is a new revision | 6.9 | 2 |
| SE1 | Sealed attribution (TE-15 merged here) is readable only through the review-chair role path of its review and used only for conflict and appointment checks; what a released result may depend on it is stated once, in annex §7.8, with its one disclosed exception (D-79, D-85); the annex specifies the rest of the anonymous-review back end and its tests | annex 7.8 | 3 |
| O1 | Fenced single-owner commits and idempotent mutations and outbox delivery prevent duplicate transitions | 9.1 | 1a-core |
| O2 | Replay never invokes models or actions; migration and rollback preserve restrictions and tombstones | 9.6, 12.6 | 1a-core |
| O3 | Context fits actual model capacity or returns explicit overflow | 10.4 | 1a-core |
| O4 | Coverage distinguishes unavailable, unprocessed, unindexed, unstructured, unscreened, untraversed, archived and not found | 10.3 | 1a-core |
| O6 | Resource exhaustion preserves barrier and purge capacity, never downgrades safety and never deletes records to make room | 8.6, 13, 14 | 1a-core |
| M1 | Import and export preserve provenance, modality and restrictive lifecycle without importing authority; sealed attribution is never exported | 12.6 | 1a-team |
| CO1 | Coordination records are author-entered under namespaced keys, never extracted, shown with status and author rather than as in force; same-key conflicts are shown deterministically, similar keys only as cues, and overviews state that conflict detection covers identical keys only; each commitment has one authority | 5.4, 6.9 | 1a-core |
| ML1 | Original text is stored and cited in its own language; concepts are language-neutral and cross-language equivalence is curated; translations are labeled synthesis, never evidence; a detected locale never decides a typed value alone, and a value that parses differently across plausible locales is ambiguous | 5.9 | 1a-core storage and citation; 3 vocabulary and typed values |
| TE-01 | Provenance, content and standing are separate records; standing is never stored inside content; original text is the record | 5, 9.9 | 1a-core; standing 2 |
| TE-02 | Modality and act state survive every copy, summary, projection, translation and export | 6.1, 10.3 | 1a-core (candidate 5 set); 2 full set |
| TE-03 | Interpretation, confirmation and adoption are separate attributed acts; only the speaker confirms | 5.2 | 2 |
| TE-04 | Handling is not resolution; every unresolved or disputed objection in a decision's applicable set appears with every projection of it, whatever its handling, mode or archive state; disputed resolutions keep the original visible; nothing done to the target resolves an objection, and a withdrawn target's objections stay live; a front end may widen, never narrow, the applicable set | 5.11, 6.10, 9.9 | 2 |
| TE-05 | Evidence relations carry a conditioning model, conditions, use history and binding; origin, qualification and usability are separate; independent tests and independent confirmations are labeled only under D1 Definition 5.3, a confirmation only for a confirming kind with an effective positive assessment | 5.5, 9.9 | 2 |
| TE-06 | Standing is a read-time projection over recorded judgments, relations and objections; no ranking, synthesis, decision or source assessment sets it, and it contains no aggregate verdict | 9.9 | 2 |
| TE-07 | Flags, views, narratives, recommendations and source assessments are never evidence; circular or rootless support is not a warrant; agreement from shared inputs is not corroboration | 9.7, 9.9 | 2 |
| TE-08 | Retraction, correction, revision, deletion and definition change create review obligations within stated coverage; obligations close only by reassessment; nothing becomes true or false automatically | 9.11, 6.11 | 2 |
| TE-09 | "As held then" and "as now assessed about then" are both answerable; corrections are never back-dated; deletion gaps are disclosed | 9.9 | 2 |
| TE-10 | Discovery links are never traversed as support | 5.5 | 2 |
| TE-11 | Retrieved content is data, never instructions; no content changes a permission; attribution and source class are never forged | 4.3, 7.1, 10.4 | 1a-core |
| TE-12 | Nothing is deleted unasked: recommendations only flag; archive keeps history; deletion requires an explicit authorized request with its effect shown | 12 | 1a-core |
| TE-13 | Works and non-person channels are judged one by one; source assessments rank attention, never decide, and never reward agreement; the system never scores, ranks or labels a person, directly, by aggregation or in synthesis it produces; only humans judge people, signed and rebuttable | 9.13 | 2 schema guard; 3 assessments |
| TE-14 | SSDS definitions and results are referenced with their owner and qualification, never re-authored; snapshots carry "as of" qualification | 9.14 | 2 |
| TE-15 | Merged into SE1 (R-20) | annex 7.8 | 3 |

Retired with D-24: F2 (checked action release), F4 (fixed-slot handles), C3 (operational skeletons), O5 (dispatch recovery). Candidate 5's A3 action-grounding clause, AC1's requirement closure, AC2's release fence for permissions, AC4's replicated control plane and retention bounds, TM1's publication waiver, and OV4's deadline planning are removed from the surviving properties (change history A.4).

### 15.1 Required falsification scenarios

Acceptance cases exercise the real core, storage, retrieval, permission and projection owners. Deterministic external doubles may control faults, but replacing an enforcing owner with a harness imitation cannot qualify it. Candidate 5's scenario identities are kept; retired scenarios are listed after the table.

| Case | Adversarial trajectory and required discriminator |
| --- | --- |
| (moved) | T70, T86–T89, T99, T101, T104–T106 and T110 are in the anonymous-review annex; T32–T34, T59, T61, T82, T91 and T92 are in the checking annex |
| T01 | Contradictory capture after an assessment snapshot, before commit: the judgment cannot enter fresh admission, checked before and after queue processing |
| T02 | Delete or correct after the release check but before sending; mid-stream; egress participant crash: no controlled release after an acknowledged barrier |
| T03 | Delete an input of a mixed summary with stale indexes and caches: UPMS-derived representations of the input are blocked at once; an authored note citing it stays and shows "input deleted" (part a, Slice 1a-core) and gets an `input_deleted` review obligation (part b, Slice 2); independent sources are still served |
| T04 | Redact a middle span, crash between staging and commit, purge the original, restore an old backup: retained spans survive only via the replacement; removed spans and old UPMS-derived representations never return |
| T10 | Duplicate ingestion and outbox messages, conflicting idempotency payloads, old writer after failover: exactly one transition or an explicit conflict |
| T11 | Quarantine release after ruleset, policy or evidence change: no restoration of obsolete admission |
| T13 | Restore without the latest recovery-log position, or with a stale replica or cache copy: no serving or derivation until the log is applied; deleted content is never resurrected; a deletion is reported `purged_live` while backups that hold it await rotation; a revocation, an access record and an SC-61 deletion marker committed inside the recovery-point window survive restore, and the removed member's reads stay refused; a quarantine, a correction, a restriction tag, a block and a sealing record also survive; an objection recorded five minutes before a site loss survives on every projection of the decision it applies to; the restore commits a restore record, and coverage and "as held then" reads name its interval; a restore whose only log copies were on the lost site does not serve; the sealed store restores to the canonical store's point (A.3 check U1 to U3; F62-07); an objection ground erased after its log entry is gone from the log and its off-site copy after restore; a resolution whose judgment is in neither the backup nor the log renders with that judgment named as missing; a commit that writes the log while the off-site copy is unreachable is never acknowledged, and its retry commits once (D-84; R64-04) |
| T14 | Cross-scope search, cache and pagination reuse, snippets, rerankers, errors and coverage queries: no unauthorized content or existence leak |
| T15 | Correction before extraction; ambiguous person or claim; commitment fulfilled after overdue; preference withdrawn: coherent lifecycles without erasing others' evidence |
| T16 | (a) Interrupted schema migration and rollback: history and restrictions preserved, no resurrection (Gate 1a-core). (b) Import of a file claiming acceptance or authority, or a package with deleted identities: history preserved, authority inert, no resurrection (Gate 1a-team) |
| T17 | Context overflow, graph cycle or fan-out, queue flood, low disk: bounded explicit failure; barriers and purge stay serviceable |
| T19 | Late source revision, non-independent corroboration, unsupported normalization, conflicting scope judgments, failed partial processing: attribution and coverage preserved, no fabricated support |
| T20 | Provider input and telemetry would carry a restricted scope's content to an unbound processor: the processor check denies, and nothing is sent; a fidelity endorsement revoked after context assembly is not relied on, and the extraction stays evidence-only (A.3 check U6) |
| T21 | A user is removed from a group while an agent session streams results from the group's scope: every read that starts after the permission revision commits, or after the cache bound, is refused; content already released is reported as released |
| T22 | An agent reads a team scope and saves a summary in a personal scope: the summary is governed by the personal scope and its own tags, keeps `exposed_to` provenance naming the team records as "private source" for readers who cannot read them, and is not withheld when the author later loses team access (inverts candidate 5's T22, D-24) |
| T23 | Injected content in an administrator's agent session requests an export or delete that only administrator mode would permit: refused, since sessions never enter administrator mode; operations within the administrator's ordinary rights follow normal checks |
| T24 | Administrator-mode read of a personal scope: the access record is committed before release and the owner sees it; the administrator cannot delete it; a crash before the commit releases nothing |
| T25 | (a) A caller submits through MCP a record with a caller-chosen source class, label or admission state, or attributed to another principal; separately, a stored memory instructing a permission change is retrieved into the session before it calls `set_permissions`: forged fields are rejected, and the permission call is decided on the caller's own rights alone; no content changes permissions, membership or roles (Gate 1a-core). (b) An administrator records a memory attributed to another user, or sets a claim admitted: rejected (Gate 1a-team) |
| T26 | A user with `write` but not `curate` deletes their own item and is refused on another's; a `write`-only contributor cannot read others' items |
| T27 | A deletion whose descendants include records in scopes the requester cannot read: every preview shows the same "records you cannot see may depend on this" line, whether or not any exist; the UPMS-derived representations are purged; authored descendants are untouched and their owners see "input deleted" |
| T28 | Search, counts, coverage, flags and overviews reveal nothing about scopes where the requester lacks `read` |
| T30 | A blind reviewer's context excludes the author's lineage after the author shares their rationale: (a) the shared copy and a hub built from it, including after the original is deleted and purged (Gate 1a-team); (b) a vocabulary definition derived from it (Gate 3); (c) an adapter trained on it (Gate 4) |
| T31 | Two agents supersede the same shared item concurrently: one applies, the other is recorded as a conflict |
| T35 | Content whose ancestry includes X, or R without a factual attestation or permitted-reliance endorsement, never enters adapter training; deleting a training source makes the adapter fall back at once and the retrained adapter excludes it; a base-vocabulary alias approval retrains only adapters whose training set uses the concept; the base-model vector index keeps serving |
| T36 | A blank model given only its L0 hub answers orientation questions; after a correction, L0's exact lines change before the next release |
| T37 | Consolidation paused for a week while work continues: exact lines current at read, overlays complete and pageable beyond the hub budget, narratives labeled with their age |
| T38 | An input of one consolidation invocation is deleted: every narrative unit from that invocation is withheld before the next release with no LLM call, whatever its citations; units from separately generated sections with disjoint inputs remain |
| T39 | Maintenance budget exhausted mid-day: no further maintenance LLM calls; task work and invalidation unaffected |
| T40 | The archive grows tenfold at the same change rate: replayed input tokens per pass, L2 and sources together, stay within the replay cap, global-pass work grows only with the number of L1 hubs, and deferred work and coverage are reported together |
| T41 | Hundreds of small changes in one area without consolidation: the narrative stays unchanged and coherent, the overlay carries every change, and the fragmentation threshold schedules a regional consolidation within the budget |
| T42 | Consolidation writes a value contradicting an exact projection, and separately an unsupported causal link outside any slot: the contradiction blocks replacement; the unsupported link may pass screening and appears only inside the narrative labeled as synthesis, never as current fact |
| T43 | A compliant ruleset whose assessor reads judgment status, a standing report, a hub, or a consolidation hypothesis or agent claim derived from one: the assessment is kept evidence-only and never admitted; after a supporting judgment is superseded with no new source, no dependent judgment is fresh, including a cached one; an investigation of a flag is kept evidence-only, and a separate assessment whose inputs exclude the flag and the investigation can admit the claim. The default ruleset with a valid fidelity endorsement admits the attributed statement (M9). Scientific judgments follow D1 Definition 6.0 instead (T109) |
| T44 | A `write`-only contributor, human or agent, reads its own record but not others', and an agent contributor's overseer reads it too; an agent writes, corrects and deletes in its own scope but cannot change permissions or remove its overseer's grant; after a scope's ownership is transferred, record owners and entitlements are unchanged and the same reads succeed or fail |
| T45 | Membership removal with a delayed identity-provider notice and an expired cache: reads are refused no later than the cache bound after UPMS observes the change; the change and its observation are recorded separately |
| T46 | Outbox paused, an obligation committed, a hub read: the hub shows the obligation through read-time catch-up, or is returned explicitly stale and partial; contradictory coordination records with one key appear as attributed conflicts; superseded, fulfilled or released records leave the exact lines, or the hub is marked stale (statement conflicts follow in Slice 3) |
| T49 | An agent's overseer enters administrator mode, the agent gains a group grant its overseer lacks, and oversight is transferred while the agent works: the agent never reads beyond the overseer's reach without administrator mode; a group grant of `rwc` on a team scope where the overseer holds only `r` gives the agent no curation, suppression, archiving or deletion of others' items there, while its own writes still succeed |
| T50 | Share, then delete and purge the original, then run a blind task and a subject erasure: the copy is excluded from the blind context, listed in the deletion preview and found by the erasure's discovery, which creates a deletion obligation on it; or the coverage gap is reported |
| T51 | An administrator in administrator mode tries to grant rights to themselves or a group containing them, make themselves an overseer, read sealed attribution, take a personal scope, create a scope with themselves as owner, or share a personal scope's records into a scope they can read: refused (A.3 check U7); transferring an active user's scope needs a second administrator |
| T54 | Steady-state simulation at the corpus envelope with no expiry, the pilot's actual scope count and at least two reader languages: consolidation demand stays within the budget; regions that do not fit are labeled projection-only; maintenance cost is the same with one reader language as with several; the narrated fraction of active records and its trend with growth are reported |
| T55 | Duplicate ownership claims and contradictory decisions with one key appear as attributed conflicts; the author's supersession closes the old record; a supersession by someone without curate rights is recorded as a conflict; an overdue commitment stays open; decisions recorded under `db-choice` and `database`, and under a key in another language, are not shown as conflicting but carry `possible_duplicate_key`, the author was offered the existing key at entry, and the L0 coverage line says detection covers identical keys only |
| T56 | An L0 read across 50 scopes whose combined catch-up gap exceeds the scan budget: affected lines are marked stale and partial, and no current token is returned |
| T57 | A piggybacked completion claim with no receipt appears only as a labeled note, “claimed by” its author; deleting its input withholds the note before the next release |
| T58 | A principal without read rights on a source declares an exclusion naming it: refused; an ancestry endpoint in an unreadable scope appears only as “private source” |
| T60 | A query in one pilot language retrieves memories written in others and in a mixed-language message; a language without an analyzer is reported as degraded coverage, never as none found |
| T62 | A translated quote appears labeled as synthesis beside the original; translating a restricted span through an ineligible external service is refused (Gate 1a-core) |
| T63 | Release records: an agent session receives records and an L0 hub through MCP, then writes notes and a checkpoint: each write is `exposed_to` exactly the released records and hub lines; a release whose record cannot be committed is not sent; deleting a released record does not withhold the notes; a resumed or compacted session continues the same session, and where the bound build cannot show separate model contexts, a new session of the same principal is treated as sharing context for independence and chair checks; a user's direct entry outside an agent session carries no release ancestry (Gate 1a-core) |
| T64 | Text pasted into a Codex session and saved through MCP, an agent-written note, and a connector field not declared authoritative are recorded as R, M and X; no content or classifier yields A or C; R- and X-class events appear in L0 only as locators (Gate 1a-core) |
| T65 | An AI interpretation with modality `hypothesized`, unconfirmed, appears in an export, an L1 hub, a question page, a narrative, a translation and an agent's context: none renders it asserted or as the speaker's; a rendering that cannot carry modality withholds it |
| T66 | A non-speaker tries to confirm an interpretation: refused. A participant adopts it: a new claim under the adopter's attribution, the original still "interpretation, unconfirmed". A decision citing the unadopted interpretation as basis: refused at commit |
| T67 | SC-41: an objection is resolved by a `resolution` decision, the objector disputes it, the resolver finalizes the target: every projection of the finalization shows "resolved by assessment, disputed" with both records and labels the resolution "self-resolved" |
| T68 | An objection is acknowledged, deferred and answered, never resolved: it travels with every decision whose applicable set contains it; an attempt to archive it, or its target, is refused while it is unresolved |
| T69 | A decision cites premise P in its basis; objection O1 targets P and O2 targets an uncited premise upstream: O1 appears on every projection of the decision; O2 appears only in the upstream report on request with its coverage; a front end's widening shows O2 on its own views and changes nothing stored; O3 on the observation of a cited evidence relation and O4 on a premise of a cited step both appear on every projection of the decision (R-01) |
| T71 | "Favors A over B", "A inadequate" and "B inadequate" coexist on one observation; a reassessment adds a judgment and never rewrites the observation or the earlier judgment |
| T72 | An observation used to fit a claim, one with an unknown use interval inside the stated coverage, and one sharing the fitting data's instrument: none is labeled independent confirmation; each keeps its evidential relation |
| T73 | A claim is revised: every evidence relation and inference step bound to the old revision is under review for the new one; a stale failing observation is not shown as evidence against the new revision, nor a stale passing one as confirmation |
| T74 | A source is retracted: the impact traversal creates obligations on dependents reached through provenance, evidence relations, inference steps and meaning links; before it completes, affected standing reports show "impact traversal pending"; assigning, acknowledging or archiving an obligation leaves it pending; a reassessment closes it; a qualification used meanwhile travels with its decision; the earlier decision is flagged, not undone |
| T75 | An inference cycle supports a claim: the theory–theory channel flags it, a route whose premise is supported only through the cycle is circular, and a human's assertion of the conclusion adds no route; a premise that also has an independent sound route keeps its step sound when someone asserts a converse step (R-02) |
| T76 | Adding `arose_from` links between questions and claims changes no standing report |
| T77 | Two live positions with assessed-sound routes: the question page shows both with their standing and no ranking; one is marked current only after a decision, for its purpose, with its dissent |
| T78 | A claim assessed in March, corrected in May: "as held then" in April shows the March judgment under the April ruleset and projection version; "as now assessed about then" shows the correction; neither shows the correction as held in April; a deletion between them is named as a gap |
| T79 | A finalization decision whose evidential routes all rest on a single uninstrumented observation, however the routes are cited: committed and labeled "sole uninstrumented backing" on every projection; the core does not refuse it; re-entering the same number is not an instrumented observation (R-07) |
| T80 | A claim relies on a snapshot of an SSDS result later requalified as failed in SSDS: the claim shows "as of snapshot; later changes unknown"; an external-reference event recording the requalification creates review obligations; SSDS unreachable changes no historical status |
| T81 | Every work in a project is re-attributed to a different author in a test copy: every source assessment, retrieval rank, recommendation and standing report is identical. A source assessment targeting a person, lab or venue is refused. No API returns per-author aggregates, and author search returns works without their assessment values. An agent-written synthesis characterizing a person's reliability is flagged and not published; an agent-authored claim with `subject_kind: person` is refused; a human's is shown with the person's reply and never surfaced proactively |
| T83 | A year of simulated operation with no requests: nothing is deleted. A refuted claim is recommended for archive with its reason; a record cited by a live claim, an unresolved objection, an open question's position, a pinned record and an open task's checkpoint are never recommended and the core refuses to archive them; recency of use alone recommends nothing; an unassessed observation and a null result are not recommended for irrelevance; archive is reversed by another curator; an archived record is retrievable on request and appears in history and standing |
| T84 | A deletion request shows its preview (descendants, routes, decisions, sharing copies, the target's unresolved objections, and the uniform "records you cannot see may depend on this" line, never a count); without confirmation nothing happens; after confirmation the lifecycle reaches `purged_live` with backups listed; an erasure request creates deletion obligations on authored descendants, visible in status until each is deleted or declined with a reason |
| T85 | SC-61: a curator deletes a critic's objection to the curator's own claim: a reason is required; a deletion marker naming the curator appears wherever the objection appeared, including the decision that relied on the claim; the critic's own deletion of their objection shows "withdrawn and deleted by its author"; an administrator's erasure on an external request shows its own marker |
| T90 | A critic records an objection in a scope the target's readers cannot read: refused as an objection; the note it becomes never travels or applies |
| T93 | A facilitator summary and a consolidated narrative each omit a live position and an unresolved objection that their exact projections show: both are flagged; the narrative does not replace its predecessor; the agent-written summary is withheld from overviews; a human-written summary is shown with the flag. In every case the view's mandatory list still shows the position and the objection, and an oblique omission that raises no flag is caught by the list, not by screening |
| T94 | Retired with §9.10's contract (D-39); T109 covers a judgment citing a judgment |
| T95 | A decision's content is amended after two signatures: neither signature counts on the new revision; a decision whose exposure names no committed release record is refused; a decision with a missing basis record is refused; a decision that front-end policy forbids is still accepted by the core if it passes integrity checks |
| T96 | Sharing: an item one owns is shared with attribution, modality, tags and provenance; sharing another member's item out of a team scope without `curate` there is refused, and with it succeeds; an agent capped by its overseer cannot share others' items where the overseer lacks `curate` |
| T97 | A year of simulated operation at the pilot workload: no release record, processing record, ancestry edge or access record is removed without a request; storage growth is reported; "delete suggested" is offered only for rebuildable derived artifacts and bulky duplicates |
| T98 | Standing replay and negative information: at a pinned position, a cached report equals a from-scratch evaluation; a new adverse judgment on a premise changes the route's status though no cited revision changed; a premise judgment made ineffective by a new revision of evidence its basis cites breaks soundness, while an unrelated scope-epoch advance changes nothing (T109; R64-05); two effective comparability judgments that disagree leave "compatibility disputed" with both (D-82); removing the only root of a support cycle leaves the cycle with no positive warrant; a premise supported only under conditions incompatible with the step's leaves the route unsound; a valid step on an unassessed premise, on a `contested` premise and on a premise judged in a scope with another ruleset shows "premises not established", listing each; a `supported-under(c')` premise shows "compatibility not established" unless the step cites the same condition record or a comparability judgment covers it; a derivation that discharges its hypothesis is sound when its steps and undischarged premises are (S62-3, F62-03, F62-04, D-69, D-70); a derivation from a model's relations with one open assumption is sound under both, listed as carried conditions; a hypothesis used on a branch that bypasses its discharging step stays a carried condition (D-71, D-72) |
| T100 | Two PIs must jointly sign a `validated` decision: PI A signs revision C1 with basis B1; the basis changes; PI B signs a later revision: the commit is refused with a conflict, and no position becomes current. A memory client records a `reported` finalization: it renders as reported and never makes a position current; no client writes `validated` for a policy it does not own; objections recorded after the policy result and during signing appear in the derived late-objection delta on every projection, change neither the decision revision nor any signature, and never prevent commit; a decision with a missing signature renders as awaiting signatures and makes nothing current until the last required signature commits; a change of policy owner while a decision awaits signatures names it, the incoming owner's re-evaluation is a new revision, and the old one renders as superseded by the change (R-04 to R-06, F62-08, F62-09) |
| T102 | A response is assembled for a member before their removal commits and released after it: refused when its release record commits; nothing is reported revoked before that |
| T103 | An evidence relation that bears against a decision's basis cannot be archived while the decision relies on it; a record archived years earlier is newly cited by an active claim and appears, labeled archived, in that claim's standing and in every mandatory list that includes it; a question page's mandatory list ignores archive filtering |
| T107 | De-attribution: after a request, regenerated summaries, hub lines, narratives, translations and extracted statements name the person by role; canonical records, authorship, others' signed claims and identity relations are unchanged; a later rebuild keeps the de-attribution; the decider of a decision, the curator in a deletion marker, the administrator in an access record and the chair in a block stay named (R-15) |
| T108 | Revision carries objections (SC-R1): a claim with one unresolved and one disputed objection is revised to fix a typo; both are carried to the new revision as "carried, pending re-examination", stay unresolved and appear on every projection of a finalization citing the new revision, on the mandatory lists and in the liveness predicate; a decision that cited the old revision still shows both; only withdrawal, rebinding by the objection's author or a `resolution` decision changes this, and a reviser's own resolution is labeled "self-resolved". The same objections survive the other paths: the author retracts the claim, or deletes it, and records a new claim with the same text, then a finalization cites it; the question page and the withdrawn claim's marker still show both objections as "target withdrawn, not re-examined", and they leave only when their authors withdraw or rebind them or a `resolution` decision resolves them; a step replaced through `supersedes` with the same conclusion carries its objections (S62-1, F62-05) |
| T109 | Scientific effectiveness (SC-R2): a premise judged yesterday under the inquiry ruleset is effective today; an unrelated commit in the scope changes no route status; an assessor who was shown a standing report before assessing is effective, with the exposure recorded; a judgment whose basis cites another judgment shows as "assessed, not effective"; effective positive and negative assessments of one route show as "disputed" with both; the project-memory age bound still applies to project-memory facts; assessor B submits a judgment naming assessor A's head as superseded and is refused, so both stay heads and the route is "disputed"; a judgment past its stated validity interval and one under a ruleset version no longer registered show as "assessed, not effective" with their conditions (F62-01, F62-06) |
| T111 | Tags on UPMS-derived representations: an embargo-tagged event feeds an embedding, a hub line, a vocabulary definition and an adapter; a reader with scope `read` who does not satisfy the tag is served none of them, and an authored note derived from the event keeps only the tags its writer set (A.3 check U9) |
| T112 | What outlives deletion: after an erasure, every surviving edge, release and processing record, access record, tombstone and marker is checked for payload text, names of the deleted content, free-form reasons and low-entropy hashes, and none is found; a marker's deleted reason leaves its reason class; an access record survives a whole-scope deletion and a `curate` deletion attempt (A.3 check U4, U11); the recovery log holds markers with reason classes only (F62-17); erased objection grounds and resolution bases are gone from the log and its off-site copy (D-84) |
| T115 | Judgments are live (F62-16): an assessor completely removes their own effective judgment that a step is invalid; the core refuses complete removal, the deletion leaves "withdrawn and deleted by its author" on the route, and the route's status changes visibly rather than silently |
| T116 | A divergent rendering (SM-1): a step is judged valid citing a passed tool check; a human records a `diverges` fidelity judgment on the tool input's `renders` link: the impact traversal creates a review obligation with cause `rendering_diverges` on the step, the route shows under review, and a decision citing it shows the obligation; an objection on the `renders` link challenges the route (D-74) |
| T117 | Mathematics guards: an agent principal's `inspection` judgment is refused; an agent's `fidelity` judgment is recorded with `assessor_is_agent`; a designation of an agent principal is refused, and one of the work's author is labeled; `record_derivation` refuses a cycle, a step owned by another derivation and an unsupported discharge; a tool check shows the operator act that registered its tool (D-72, D-73, D-75, D-77) |
| T118 | Applicability through tool checks (SC64-01): a decision cites only claim K and step S; S's effective inference judgment cites tool check T and its `renders` link L; an objection to T, and one to L recorded while the decision awaits signatures, are both in its applicable set, on every projection and in its late-objection delta; after the judgment is superseded, both stay in the set (D-86); the core refuses nothing (D1 F-6; D-50, D-85) |
| T119 | Bearing (R64-01): with only a usable `refutes(K)`, `has_sound_adverse_route(K)` holds and `has_sound_support(K)` does not; a usable `consistent-with(K)` or an unassessed `bears-on(K)` makes neither hold; `favors(K over B)` gives support shown with B and the model, `favors(B over K)` an adverse route; `adequate(K, p)` gives support shown with purpose p (D1 §6.1, F-28; D-81) |
| T120 | Objection coverage (SC64-03): P loses read on scope S but still reads P's own claim K; P's view of K carries the coverage statement, identically whether or not an objection to K exists; after S is widened, a new reader who cannot read a registered objection home sees the statement; a rebind to a target whose current readers cannot all read the objection's home is refused; a sharing copy of K shows K's objections its reader can read, and the shared-copy statement to a reader who does not read S; no permission change or share is refused (D1 F-6, F-7a; §5.11, §6.8, §6.10; D-80, D-88) |
| T121 | Withdrawn basis (R64-03): after K's author withdraws K, a new `recorded` decision citing K commits, is labeled "cites a withdrawn record" on every projection, and has K's unresolved objection in its applicable set; a `reported` decision citing K records as before (D1 F-3b; §6.9; D-83) |
| T122 | Late objection after reassessment (SC65-01): decision D cites claim K and step S; S's effective judgment J cites tool check T; after D commits, objection O is recorded against T; J's assessor supersedes J with a judgment that does not cite T; O stays in D's applicable set, on every projection and in its late-objection delta until resolved; a second objection recorded against T after the supersession also joins it; the view of S's conclusion lists neither as challenging S's current route; the core refuses nothing (D1 F-6; §6.9; D-86) |
| T123 | Copy chains (SC65-01): claim K with unresolved objection O is shared as C1, and C1 as C2; a decision citing C2 has O in its applicable set; a reader of C2 who cannot read K's home sees the shared-copy statement, identically whether or not O exists; neither share is refused (D1 F-6, F-7a; §6.8; D-86, D-88) |
| T124 | Coverage over the footprint (SC65-02): reader P reads scope H, which homes claim K and step S, and every objection home registered for H; S's effective judgment cites tool check T, homed in Q, which P reads only through an own-record entitlement; P's view of a decision citing K and S carries the coverage statement, identically whether or not an objection to T exists (D1 F-7a; §5.11; D-87) |
| T125 | Coverage by configuration (SC65-02): an attempt to give an objection a restriction tag of its own is refused, and an objection to a tagged target is unreadable to a reader who does not satisfy the target's tags; a reader in a task with a lineage exclusion sees the statement on every projection; after an objection home's registration is retired, a reader who cannot read that home still sees the statement for records of the scope (D1 F-7a; §5.11, §7.4, §10.6.4; D-87) |
| T126 | Rebind audience (R65-02): objection home R is registered for scope S and later narrowed; a rebind of an objection homed in R to a target in S is refused while some current reader of the target, including one reading it only through an own-record entitlement, cannot read R; after R is widened again the same rebind succeeds; no permission change is refused (§5.11, §6.10; D-88) |
| T127 | Relation shapes (R65-01): `favors` with three targets, `favors(A over A)` and `entails` with two targets are refused when recorded; three pairwise `favors` relations among A, B and C give each claim its bearing, each shown with its alternative and model (D1 Definition 5.1, §6.1; §9.9; D-89) |
| T128 | Resolution and dispute homes (SC66-01): objection O to claim K is homed in K's scope H; a `resolution` decision for O homed in scope Q, which is not a possible home of K's objections, is refused, as is one with a restriction tag of its own; the same decision homed in H commits; a dispute O2 of it homed in Q is refused and in H is accepted; reader P who reads H and every objection home registered for H, and reads the resolution only through an own-record entitlement, sees O2; a reader who does not read a registered home of H sees the coverage statement, identically whether or not O2 exists (D1 F-4, F-7a; §5.11, §6.9; D-90 pending) |
| T129 | Bindings (SC66-02, SC67-03): decision D1 cites K1, which has objection O; K1 is revised to K2 and O carried; O's author rebinds it to K2; decision D2 cites K2; both have O in their applicable sets, each projection naming the binding through which it applies; a resolution that answers O at K2 only shows O resolved on D2 and unresolved on D1; the author's withdrawal of a binding as misapplied labels it so on the decisions that relied on it and keeps it in history; the same holds when K1 is withdrawn and O rebound to a restating claim in another scope whose readers read O's home (D1 Definition 2.5, F-3, F-3a, F-6; §5.11, §6.10; D-91, D-93 pending) |
| T130 | Delta baseline (R66-01): the front end evaluates a basis {K, S} at position e, where S's effective judgment cites tool check T with existing objection O; the decision commits later; O is not in the late-objection delta; an objection to T recorded between e and the commit is; an objection to the endpoint of an assessment effective only before the commit is in neither the applicable set nor the delta (§6.9; D1 F-6; D-86) |
| T131 | Dispute chains (SC67-01): Q is registered as an objection home for H and Z for Q; O1 targets claim K in H; resolution R1 is homed in Q; dispute O2 of R1 in Q; resolution R2 of O2 in Z; dispute O3 of R2 in Z; reader P reads H and Q but not Z, and reads R2 only through an own-record entitlement; P's view of a decision citing K carries the coverage statement, identically whether or not O3 exists; a resolution naming bindings with no common possible home is refused until split (§5.11; D1 F-7a; D-90 amended, pending) |
| T132 | Test and confirmation (SC67-02): with complete use history and no shared dependence, a usable `prediction-succeeded(K)` is an independent confirmation of K; a usable `prediction-failed(K)` or `refutes(K)` is an independent test with adverse bearing, never a confirmation; `consistent-with(K)` and an unassessed `bears-on(K)` are independent tests with neutral bearing; `favors(K over B)` and `adequate(K, p)` are never called confirmation (D1 Definition 5.3; TE-05) |

**Retired scenarios.** T05, T06, T07, T08, T09 and T18 tested the instrumented runtime and checked action release (D-24). T12 tested reconstruction windows and retention laundering, T47 the continuity warning and T52 published-copy retention (D-25). T29, T48 and T53 tested publication waivers and inherited requirements (D-6 superseded under D-24; replaced by T22, T96 and T50). T62 part (b) tested action grounding.

### 15.2 Evaluation protocol

Corpus, implementation and configuration, oracle, prompts, models and judges, budget and decision rule are frozen before measuring. Baselines: B0 source-preserving lexical retrieval; B1 hybrid transcript chunks; B2 full history where it fits; later slices also compare against the previous accepted slice, with the same authorized corpus, answer model and matched budgets. B2's non-applicable cases are reported, not silently excluded.

Initial evaluation: 200 synthetic continuing-project episodes, 100 for development and 100 held out, with at least 10 held-out episodes in each of update and correction, temporal reasoning, scope isolation, continuation, absence and abstention, team coordination, cold-start orientation and multilingual or mixed-language work (overlap allowed and disclosed). From Slice 2, add held-out episodes of inquiry: status and dissent recovery, retraction impact, use history and independence, and "as held then". Every applicable scenario of the bound core and annex inventories runs separately and passes before any comparative study of the same slice is reported (deterministic contract checks before comparative studies, Codex review §7); correctness cases are never replaced by aggregate benchmarks. Real-session evaluation is optional until permission is obtained; synthetic results cannot establish real-user generality.

Primary outcome: paired task completion at a fixed declared context budget, with an exact source, permission, modality and lifecycle correctness rubric. Gate target: at least one preregistered continuity or recall outcome improves with a paired 95% interval excluding zero, no mandatory invariant fails, and material task-success regressions exceed neither the preregistered 5-percentage-point margin nor its uncertainty bound. If the sample cannot establish the rule, the result is inconclusive and a new evaluation is specified; the rule is never relaxed after results. Each later slice must show incremental value over the previous one.

**Theory-layer studies (Slice 2 onward).** SCIRE's E1 (status and dissent loss), E2 (orientation) and E4 (elicitation cost, including blocked decisions, overrides, disputed resolutions and basis-statement effort, re-review V4-19) run on UPMS as written; E3 (derivative flow) applies only if the strict profile is built. **E5, projection correctness and comprehensibility** (narrowed as the Codex review §7 recommends): pinned histories with versioned expected dispositions; incremental against complete replay; stale and incomplete results counted separately; then reader time and interpretation errors, on a corpus shared with E1 but with separate endpoints, and with adjudicator disagreement reported as uncertainty. **Persisted narratives** (Slice 4) ship only if E2 shows benefit over deterministic projections plus on-demand synthesis, counting maintenance and correction cost and missing mandatory objections separately from prose quality (SCIRE v0.4 §9.1). The owner sets error and cost limits before each study, two-sided where a mechanism can both leak and over-restrict (re-review V4-09).

Secondary outcomes: attribution and modality fidelity, stale-current answers, temporal correctness, conflict and objection visibility, screening precision and recall per channel, coverage, unnecessary blocking, cold-start orientation success and navigation cost, overview staleness and churn, maintenance-to-work cost ratio, extraction consistency across runs and models, normalization coverage, storage growth without expiry, archive-queue size and reversal rate, total lifecycle cost and warm and cold latency. Human attention and false blocks count as cost. These thresholds are reviewer choices, not observed results.

Human adjudication reviews every consequential authorization or attribution failure plus a stratified 20% sample of other held-out judgments; a model judge is validated against that sample and disagreements are resolved visibly. All evaluated variants, failures, post-outcome changes, held-out reuse and unknown prior selection history are recorded. Adapter promotion and team-policy experiments (§9.8, §10.6.6) use this same discipline. Public benchmarks may supplement but cannot qualify security or deletion. No results or comparative superiority are claimed here.

## 16. Delivery Slices and Gates

**Project memory ships first; the theory layer and the SCIRE demonstration follow; checking, then scale** (D-30, proposal §14). No date or shipping commitment is implied, and no slice borrows a previous slice's acceptance for an untested guarantee.

| Gate or slice | Deliverable | Required closure |
| --- | --- | --- |
| Gate 0 | The proposal, the D1 formulation and this candidate reviewed together by a reviewer outside the Claude family and accepted with named owners; decisions D-1 to D-89 confirmed or changed and the proposed D-90 to D-93 decided; §9.10 deferred (D-39); the core and the anonymous-review annex reviewed together, the checking annex before Gate 3 and the Slice 4 annex before Gate 4 (D-56); pilot languages named; bound profile; bounded D4 specification and executable test specification | Independent falsification of these exact texts; product acceptance; evidence bound to the accepted slice and profile (storage, KMS, backup and restore with the recovery log and its off-site copy, MCP principal, session and capture-path feasibility for the bound Codex build, including whether its sessions can be shown not to share model context, §8.2); evaluation frozen before measurement |
| Slice 1a-core / Gate 1a-core | **Evidence memory**, single user, Codex via MCP: capture, protected storage, language-tagged capture and original-language citation, scoped lexical and hybrid recall across pilot languages, coverage, checkpoints and coordination records under namespaced keys, release records as provenance, correction, suppression, redaction and explicit deletion with preview; personal scopes; overview projections of coordination records, checkpoints and controls, with read-time catch-up and pageable overlays | A1, A2, AC1, AC6, AC7, CO1, D1–D3, DL1 (preview and propagation), E1, F1, F3, F5, H1, ML1 storage, O1–O4, O6, OV1–OV2, OV3 exact parts, P1, R1, TE-01, TE-02 (candidate 5 set), TE-11, TE-12; T02, T03 part (a), T04, T10, T13, T14, T16 part (a), T17, T25 part (a), T36, T46, T55 single-author part, T56, T60, T62, T63, T64, T84 without erasure obligations, T97, T111, T112; recoverable payload and tombstone state; purge and restore evidence; matched recall and continuity evaluation, with coordination-record capture measured, not assumed |
| Slice 1a-team / Gate 1a-team | Groups, agent principals and overseers, administrator mode and access records; sharing, shared-pool concurrency and the lineage-exclusion primitive; per-reader team overviews; deletion markers; import and export | AC2–AC5, M1, TM1, TM2 primitive, DL1 markers; T16 part (b), T21–T24, T25 part (b), T26–T28, T30 part (a), T31, T44, T45, T49–T51, T55 multi-author part, T58, T85 for decisions and coordination records, T96, T102, T107; Gate 1a-core retained |
| Slice 2 / Gate 2 | **Theory basics:** claims with the full modality set and the three acts; questions; objections with handling, resolution and disputes; evidence relations with use history; inference steps; decisions with the decision fields, integrity checks and `validated` commits; the standing projection and "as held then"; question pages, mandatory lists and the understanding section; review obligations and impact traversal for claim revision, retraction, correction, definition change and deletion (retraction cannot wait while support is used, Codex review TE-R18); SSDS references. **The SCIRE minimal demonstration (SCIRE D-J) runs here:** one real inquiry on UPMS, against a versioned notebook plus search | A3, C2 evidential, DC1, DL1 obligations, E2, E3, H2, MV1, TE-02 to TE-06, TE-08, TE-09, TE-10, TE-13 schema guard, TE-14; T01, T03 part (b), T11, T15, T19, T43, T65–T69, T71–T80, T85, T90, T95, T98, T100, T103, T108, T115, T109, T118–T132; the inquiry ruleset (§7.6); E1, E2, E4 and E5 run with owner-set limits; incremental value over Slice 1 |
| Slice 3 / Gate 3 | **Checking:** structured statements and the vocabulary registry with multilingual labels, contested labels and measurement property types; the three consistency channels and the candidate channel; processing cascade tiers 1–2; fact-checking; source assessments of works; retention recommendations and the archive; L2 entity pages; the back end of anonymous review (anonymous-review annex, D-42); the mathematics annex, once reviewed; anonymity is unavailable before this gate | AR1, ML1 typed values, SC1, SE1, ST1, ST2, TE-07, TE-13, VO1; T30 part (b), T32–T34, T59, T61, T81, T83, T86–T89, T91, T92, T93 summary part, T70, T99, T101, T104–T106, T110, T113, T114, T116, T117; extraction consistency and normalization coverage measured on real sessions before screening is relied on; incremental value over Slice 2 |
| Slice 4 / Gate 4 | **Scale** (Slice 4 annex for consolidation): consolidated narratives with regional and global consolidation, only if E2 supports them (§15.2); overlay notes and piggybacking; per-scope adapters (tier B, query-side); team visibility policies (experiment §10.6.6); graph-assisted retrieval; assessments of non-person channels and their track records, only if measured need justifies them (§9.13); the strict profile if a project needs it (D-27); Claude adapter | AD1, OV3 narrative, OV4–OV6; T30 part (c), T35, T37–T42, T82, T54, T57, T93 narrative part; adapters beat tier A; team policies beat all-shared and all-private baselines; ablation or comparator and full lifecycle and security evidence for each addition; Claude qualified independently of Codex |

Slice 1 is split (D-16) so that the first gate tests a single-user service before groups, agents, administration, sharing, import and export are added; candidate 5's proposed move of import and export to 1a-team is kept, pending the owner. Candidate 5's Slice 1b (instrumented runtime) leaves UPMS (D-24). Structured statements move from candidate 5's Slice 2 to Slice 3, and consolidated narratives to Slice 4, following proposal §14; theory basics need claims, relations and standing over text, not slot screening.

## 17. Delegation, Inspection and Reopen Triggers

**Implementation may choose anything this manual does not fix, provided every invariant holds; a change that cannot hold them reopens the owning section instead of being patched around.**

### 17.1 Implementation (D4) space

Delegated: language and frameworks; schemas and serialization; indexes and libraries; embedding, extraction, classifier, contradiction and base models for adapters; prompts for extraction, overlay notes, consolidation and recommendations; ranking weights, excluding authorship; hub, question-page and standing-report rendering; significance heuristics within §10.5.3; traversal and caching strategies within the stated limits; how the sealed store's role path is enforced (proposal §7.1 leaves this to D4), provided §7.8's properties and residual statement hold; helper functions; scheduling and backoff; KMS product; user-interface layout; transport implementation. These preserve durable semantics, the bound profile constraints and acceptance at real owners.

### 17.2 Product inspection surfaces

**Within the requested deliverable** (candidate 5 §17.2, from proposal v0.3 §11 and the owner's round-2 requirements), subject to normal access control including existence disclosure:
- What was remembered, from which source, and when?
- Why was it retrieved or presented as current, with which assessment and coverage?
- What supports or opposes it, what is flagged as conflicting and why, and what is unprocessed or unavailable?
- Did correction, suppression, quarantine, redaction or deletion take effect, and what remains (backups, released content)?
- Which retained outputs might it have influenced, with what limits?
- Who can see this memory, and why?
- Who accessed my personal scope in administrator mode?
- What does this term mean here?
- What is the current big picture, and how old is its narrative?

Candidate 5's "what retention deadline applies" is replaced by "what is recommended for archive, and why?" (below).

**Beyond the requested deliverable, binding only after the owner accepts them** (proposal §16): the product inspectability surfaces listed and marked in D1 §11, which owns the list and the routine questions they answer. Technical review cannot accept any of these on the owner's behalf. No independent scientific-result database or dashboard is added.

### 17.3 Non-goals and simplification

No truth oracle; no motive, interest, incentive or threat inference about people; **no scoring, ranking, rating or labeling of a person, group, institution or venue, and no person-level track record** (D-32); no training of the main LLM on retained memory (small-model adapters only as derived indexes, §9.8); no general theorem prover; no replacement system of record; no cross-tenant transactions or federation; no guaranteed model causal attribution; no universal prompt-injection immunity; no erasure of uncontrolled recipients; no generic numerical confidence or numeric interpretation weights; **no mediation of agent actions** (D-24); **no time-based retention** (D-25); **no discussion, facilitation, review process or inquiry policy** (SCIRE's, D-22); no authority over SSDS records (D-21).

Design tradeoffs, not measured optimality claims: Event, Claim and Judgment stay separate because observation, proposition and assessment have different identities and lifecycles; claims, judgments, questions and objections are not required for basic recall; provenance and meaning relations stay distinct in one relation store; standing is projected, never stored; four ownership boundaries without mandatory separate services; canonical storage and outbox instead of an event bus; hypothesis truth owned only by Judgment; scope epochs before slot-level invalidation; a small fixed rule language instead of general logic; the overview as derived hubs over the archive, not a second authority; release records kept as provenance rather than as access ancestry.

### 17.4 Reopen and impact rules

Reopen the owning section if:
- standing or impact traversal cannot meet its limits at the declared scale while staying exact to its stated depth;
- the one-hop applicable set (D1 F-6) systematically hides material objections in E1 or E5;
- the coverage statement (D1 F-7a) is shown so widely that readers stop reading it (E1, E4, E5);
- synthesis screening misses omissions or person characterizations at a rate the owner's limits do not accept;
- storage growth without expiry exceeds what the archive tier and explicit deletion can manage;
- mandatory lists cannot fit their views at the declared scale without hiding entries behind continuations nobody follows (measured in E1 and E5);
- the liveness predicate blocks archival so widely that the archive tier is unused, or so narrowly that live dissent leaves the overviews;
- sealed attribution leaks through any record an anonymous-role session causes;
- permission evaluation cannot be performed before ranking at the declared scale;
- lineage exclusions cannot be enforced on an enabled context path;
- extraction consistency or normalization coverage is too low for screening to be relied on;
- consolidation cannot keep the maintenance budget while holding OV3–OV6;
- adapters fail to beat vocabulary expansion, or their deletion retraining misses its target.

Calibrated scores, numeric weights, statistical comparison models relied on by screening, automatic source-assessment mappings and guaranteed approximation route upstream to D1 and D2 (§1.4). A project's need for restricted-data containment reopens §7.9 (D-27). Cross-tenant or federated use, record-level declassification and arbitrary privileged execution require new explicit architecture decisions.

On any accepted material change, affected records and APIs, adapters, ruleset contracts, vocabularies, caches, indexes, hubs, standing caches, migration and recovery, tests, documentation and evaluation identities are remapped; unaffected evidence is preserved only with reason. Equivalent D4 changes that preserve these contracts do not reopen D3. Repeated wrappers or fallbacks around one broken mechanism trigger re-derivation before another additive repair.

## 18. Readiness, Open Decisions and Remaining Closure

**Readiness: NO-PASS for implementation-ready or accepted-current status; ready for review by a reviewer outside the Claude family, together with the proposal and the D1 formulation.** This candidate applies owner decisions to text; that is not a demonstration of any contract, and the author's view that the reconciliation is complete is not an independent finding.

### 18.1 Remaining closure

| Item | Evidence still required | Owner and boundary |
| --- | --- | --- |
| Independent review | The author cannot accept this candidate, the D1 formulation or the proposal; same-family review does not count | Reviewer outside the Claude family, then the product owner at Gate 0 |
| Codex review findings | Each of SC-TE01 to SC-TE05 and TE-R01 to TE-R20, of the 6.4 review's SC64-01 to SC64-03 and R64-01 to R64-06, of the 6.5 review's SC65-01, SC65-02 and R65-01 to R65-03, of the 6.6 review's SC66-01, SC66-02, R66-01 and R66-02, and of the 6.7 review's SC67-01 to SC67-03 and R67-01, checked against this body text; change history A.8 is the author's view only, and a finding closes only when the operative text resolves it (the review's revisit condition) | Reviewer outside the Claude family; the owner for the decisions in the review's §9 |
| Judgment on judgment | Decided: deferred (D-39, §9.10); closes candidate 5 §18.1's item for the first product | Product owner, on the reviewer's advice; before Gate 2 broadens rulesets |
| Challenges in §18.3 | Independent check of each repair C68-1 to C68-6, and of the rows the 6.7 review left partial or open (its §4) | Reviewer outside the Claude family |
| Gate 0 obligations | Named pilot languages and profile; a bounded D4 specification and executable evidence specification; runtime, storage, KMS and restore feasibility (§16). No revision of this text meets them. The candidate 5 decisions D-8, D-9, D-16, D-18 and D-19 were confirmed or made moot in the D-37 record (its §2), and D-13 and D-17 are moot (change history A.12); none is pending | Product owner and named owners; Gate 0 |
| SCIRE front-end specification | Drafted in the SCIRE repository from SCIRE v0.4 §§2, 4.4–4.5 and 8 with the re-review's repairs (proposal §14 step 2); must not narrow TE-04 | SCIRE owner; before Gate 2 |
| KMS, backups and restore | Concrete service and copy inventory, including the recovery log and its off-site copy as payload-bearing surfaces; recovery-log restore proof, restore closure and outage behavior (D-84); adapter and hub purge behavior | Security and infrastructure owner; feasibility before specification freeze, tests at Gate 1a-core |
| Session feasibility | Whether the bound Codex build's MCP sessions can be shown not to share model context; release-record commit latency | Runtime and evaluation owners; Gate 0 and Gate 1a-core |
| Structured-meaning feasibility | Extraction consistency across runs and models; normalization coverage on permitted real sessions; screening precision and recall per channel | Architecture and evaluation owners; before Slice 3 relies on screening |
| Theory-layer adoption and cost | Whether people and agents record objections, use histories and basis statements; E4 cost measures | Product, SCIRE and evaluation owners; Gate 2 |
| Consolidation economics without expiry | Narrated fraction and its trend with growth (T54) | Evaluation owner; Gate 4 |
| Evaluation freeze | Corpus, rubric, judge and harness identities, randomness and repetition plan; E1–E5 limits | Evaluation owner; before measurement |

**Named owners for this early version:** the product owner (Sam) holds the architecture, security and infrastructure, evaluation and Codex runtime owner roles. Independent review remains a separate role and cannot be held by the author.

### 18.2 Owner decisions

Owner decisions are product choices; they verify nothing technically. Each range is bound in its own record; this table only says where to find it. The full table of D-47 to D-78 as it stood in candidate 6.4 is in change history A.15, that of D-79 to D-85 as it stood in candidate 6.5 in A.16, and that of D-86 to D-89 as it stood in candidate 6.6 in A.17 (D-85).

| Decisions | Record | Applied in |
| --- | --- | --- |
| D-1 to D-19 | Candidate 5 §18.2; status in change history A.12 | Throughout |
| D-20 to D-36 | Proposal §0.2 | Throughout |
| D-37 to D-46 | `UPMS_Owner_Decisions_2026-11-03.md` | D1; §4.3, §6.9, §7.8 annex, §9.10, §12, §16 |
| D-47 to D-56 | Decided when the owner directed revision 6.2 on the author's recommendations ("Draft on these", 3 November 2026); recorded in change history A.15 | §6.9, §6.10, §7.6, §9.9, §12.3, §12.4, §1, §16 |
| D-57 to D-62 | `UPMS_Owner_Decisions_Math_2026-11-03.md` | Mathematics annex; hooks H1 to H7 (§5) |
| D-63 to D-70 | `UPMS_Owner_Decisions_6_2_Review_2026-11-03.md` | D1 F-3b, F-8, §6.1; §5.11, §6.9, §6.10, §7.7, §9.9, §9.11, §12; annex §7.8 |
| D-71 to D-78 | `UPMS_Owner_Decisions_Math_Review_2026-11-03.md` | D1 Definition 2.7, §6.1, F-32; §4.3, §5, §9.9, §9.11; mathematics annex |
| D-79 to D-85 | `UPMS_Owner_Decisions_6_4_Review_2026-11-04.md` | D1 F-3b, F-6, F-7a, F-20a, §6.1, F-28; §5.11, §6.8 to §6.10, §9.9, §10.3, §12.4, §13; annex §7.8 |
| D-86 to D-89 | `UPMS_Owner_Decisions_6_5_Review_2026-11-05.md` | D1 Definitions 2.6, 5.1, F-6, F-7a; §5.11, §6.8 to §6.10, §7.4, §9.9 |
| D-90 to D-92 (**proposed, pending**) | `UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md` | Below; D-90 and D-92 as amended |
| D-90 and D-92 amended, D-93 (**proposed, pending**) | `UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md` | Below |

| ID | Proposed decision (pending the owner) | Applied in |
| --- | --- | --- |
| D-90, amended | Possible homes are transitive; every objection is homed in a possible home of its target, and a resolution in a possible home of every binding it resolves, with no restriction tags of their own | D1 F-4, F-7a; §5.11, §6.9, §6.10; T128, T131 |
| D-91 | An objection applies through every target it has been bound to; a rebind adds a binding and removes none | D1 Definition 2.5, F-3a, F-6, F-7a; §5.11, §6.10, §7.4; T129 |
| D-92, amended | The existence of an objection is not promised confidential; hidden-existence objections are outside the first product | D1 §8.2; §1.2, §5.11 |
| D-93 | Resolution and withdrawal are per binding; an objection is unresolved in a projection when it is unresolved at a binding in its footprint | D1 Definition 2.5, F-3, F-3a, F-7; §5.11, §6.9, §6.10; T129 |

**Still open:** D-90 to D-93, proposed by the author and pending the owner; C6-6, the owner's acknowledgement of the process deviation (change history A.12); V4-12 (iv), where an argument may stop; V4-15, the versioned exchange vocabulary with SSDS; type-specific propagation beyond §9.9 and D1 §6.1's bearing (TE-R11); the strict profile's SC-42 rule (§7.9); candidate 5 reconciliation rows X2, X5, X6, X8 and X10 (change history A.11).

### 18.3 Challenges and findings answered in this revision

The repairs of this revision, C68-1 to C68-6, are mapped in change history A.18; C67-1 to C67-6 are in A.17, C66-1 to C66-9 in A.16 and C65-1 to C65-10 in A.15, which also holds the C63 and C64 tables of candidate 6.4 §18.3; those of candidates 6 to 6.2 are in A.12. Each repair is the author's and needs an independent check.

## Appendix A. Change Map

The change map of this candidate (candidate 5 → 6 → 6.1 → 6.2 → 6.3 → 6.4 → 6.5 → 6.6 → 6.7 → 6.8, the reconciliation of candidate 5 §§11–13 and 15, the re-review and Codex dispositions, and the edits inside copied text) is in `UPMS_Architecture_Manual_Candidate_6_3_Change_History.md`, with 6.3 → 6.4 in `UPMS_Architecture_Manual_Candidate_6_4_Change_History.md` 6.4 → 6.5 in `UPMS_Architecture_Manual_Candidate_6_5_Change_History.md` 6.5 → 6.6 in `UPMS_Architecture_Manual_Candidate_6_6_Change_History.md` 6.6 → 6.7 in `UPMS_Architecture_Manual_Candidate_6_7_Change_History.md` and 6.7 → 6.8 in `UPMS_Architecture_Manual_Candidate_6_8_Change_History.md`. It is change history, not architecture.

## Appendix B. Independence, Coverage and Sources

- **Family.** Written by Claude (AI, Opus 5.5), the same model family and model as the proposal, candidates 4.1 and 5, the SCIRE v0.3 and v0.4 texts and their re-review. Shared blind spots are likely. A reviewer outside the Claude family is required before acceptance (`AGENTS.md`).
- **Read directly:** the proposal in full; candidate 5 §§1–18 in full, Appendix A by heading; SCIRE v0.4 §§2–7 in full; the SCIRE v0.4 re-review §§1–9 in full; the Codex review of the proposal in full, after the first full draft of this candidate; `workplans/README.md`; `history/SEMANTIC_EVOLUTION.md`.
- **Anchoring:** the Codex review was read after drafting, so its findings were checked against an existing text and could have been fitted to it; A.8's "repaired" verdicts are the author's, not the reviewer's.
- **Revisions 6.1 to 6.8:** each written by the same author in answer to a review or owner decisions (§1.1), so the repairs were fitted to existing text and need an independent check. The reviews of 6.4 to 6.7 were by Codex, the same reviewer and family, which read the author's change histories and earlier reviews and was not blind. The revision-by-revision notes are in change history A.16 to A.18.
- **Not read:** SCIRE v0.4 §§8–17 except as the proposal and re-review summarize them; the Interoperability Proposal v0.4; SSDS sources, reached only through the proposal's §10.
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated.
- **Sources** for retained claims about Codex integration and hippocampal indexing are candidate 5 Appendix B; this candidate adds none.
