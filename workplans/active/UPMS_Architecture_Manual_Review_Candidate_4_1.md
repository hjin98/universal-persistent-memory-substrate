# UPMS Architecture Manual (Review Candidate 4)

Oct 31, 2026 · @Sam

## 1. Status, Authority and Scope

**Status: proposed D3 architecture, review candidate 4; not accepted-current and not implementation-qualified.** UPMS (Universal Persistent Memory Substrate) is a model-independent memory service for continuing project work by people and agents. It preserves observations, keeps revisable assessments, gives each reader a fast orientation map, and supplies an instrumented runtime with what it needs to enforce permitted use. It never infers permission from remembered text.

This candidate repairs review candidate 3 against an interim review by three same-family AI reviewers on 31 October 2026 (M-01–M-26; NO-PASS with two Serious Challenges), applying each repair in its owning section together with the owner's decisions (§18.2). Candidate 3 had repaired candidate 2 against Codex's cross-review (CR01–CR10); candidate 2 had consolidated review candidate 1 (Codex's refined manual) with the round-2 amendments A1–A7. Appendix A.5 maps every interim finding to the sections and tests that changed, built from a section-level comparison of candidates 3 and 4. It also adds multi-language support at the owner's request (§5.9, Appendix A.6). The interim review was not independent; the independent falsification required before promotion is still outstanding.

### 1.1 Inputs and their status

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Architecture Manual — Refined Candidate (review candidate 1) | SHA-256 `0ffc2740b4ec9088511754c1d2593262feff74d8bac6a1e39c4f37ab55ab4443` | Base text; its repairs F01–F18 are retained |
| UPMS Architecture Review (Codex) | SHA-256 `b0617a925916a130d47187917e54acd009ba3f367da29015c916ff94e8854f50` | Findings F01–F18 and their dispositions |
| UPMS Architecture Manual: Round 2 Amendments | Claude Docs artifact, 30 October 2026 | Amendments A1–A7; change rationale |
| Earlier architecture review of proposal v0.3 (R1–R7) | Appendix A | Closes the base text's “review not supplied” item |
| Product owner's instructions | This design conversation | Codex with OpenAI-family models first, Claude second; configurable retention; delegated initial defaults; decisions D-1 to D-19 (§18.2) |
| Software Design method | SSDP 7.2.1; no task `protocol_version` assigned | Form of this manual |
| UPMS Architecture Manual (Review Candidate 2), Markdown export | SHA-256 16fee00e43899a7cfd34c3e4fc4e67c3deee4bd3c32e982546f942783a14266f | The reviewed text, frozen in that file and in this doc's history; this candidate edits it |
| UPMS Candidate 2 Cross-Review (Codex) | SHA-256 d7ef16e8cba2214d8d394e592978380ba63a25974c15f8c6682a1b818c0ce6d5 | Findings CR01–CR10, question answers and decision dispositions repaired here |
| UPMS Architecture Manual (Review Candidate 3), Markdown export | SHA-256 dcf61fc1e7a6c87e1ce8ec033edbb0b50d2fa6e09b1d6b27dc359a1d80fc2a97 | The reviewed text, frozen in that file and in this doc's history; this candidate edits it |
| UPMS Candidate 3 Interim Review (Claude subagents, consolidated) | SHA-256 d462621194357cd1276306bb47bb7d0885af701a51c3ccbe6e5e73d8e6c69834 | Findings M-01–M-26 and owner questions Q1–Q5 repaired here; same-family, not independent |

**Fixed (proposed)** marks a durable architectural constraint if this candidate is accepted. **Initial default** marks an agent-chosen, configurable starting value under the owner's delegation, not a measured capability or ratified policy. **Unverified** marks claims that need implementation or external evidence. Defaults never weaken a fixed invariant. Changes to product scope or guarantee strength require D3 reconsideration.

### 1.2 Product boundary

The first journeys are:

- task resumption and orientation from the overview layer;
- source inspection and targeted correction;
- scoped recall, suppression, redaction and deletion;
- multi-user and multi-agent access under scope permissions, with administration;
- team coordination through shared memory, including blind and independent work.

The first deployment is one administrative tenant; cross-organization federation is excluded. Codex is the first integration target; Claude follows after qualifying the same adapter contract independently.

UPMS owns record and state semantics, memory-access permissions, interfaces, persistence, recovery, concurrency, trust boundaries, resource structure and deployment profiles. External owners keep identity, group membership and the admin role; action, destination and processor policy; keys; source-application current state; model behavior; and external effects. Model or vendor choice is never a storage identity.

### 1.3 Acceptance boundary

Proposal → independent falsification of this exact candidate → product-owner acceptance → bounded implementation specification → implementation acceptance. Requests to refine and choose defaults authorize proposal work, not self-promotion to accepted-current. Section 18 separates unresolved evidence from choices provisionally bound.

### 1.4 Domain and inspectability

No scientific (D1) or numerical-method (D2) parent is required: UPMS records attributed statements and references and certifies none of them. Assessment categories, structured-statement screening, approximate retrieval and adapted small models are engineering mechanisms that only propose; screening never resolves a conflict, and adapters are promoted only through an evaluation gate.

This determination reopens, and D1/D2 authority is required first, when:

1. source-reliability scores, calibrated confidence or numeric interpretation weights are introduced;
2. a consumer relies on a guaranteed approximation bound;
3. screening, a small-model score or an adapter output decides a consequential outcome without confirmation;
4. UPMS becomes the retention home for realized scientific records, in which case it must preserve those projects' authority, findings, uncertainty and retention requirements.

No realized scientific results were generated or reviewed in preparing this candidate. Material operational records are sources, assessments, corrections, access and lifecycle decisions, invocation inputs and outcomes, failed or incomplete processing, retrieval coverage, overview state and deletion evidence. Readers are users, overseers, incident investigators and operators; their routine questions are in §17.2.

## 2. Terms and Precedence

**Each term below has one owner section; later sections use these meanings exactly.**

| Term | Exact meaning | Owner |
| --- | --- | --- |
| Event | Immutable observation by an authenticated capture component; not proof of its contents | 5.1 |
| Claim | An attributed statement or reasoning proposal, without intrinsic truth or permission | 5.2 |
| Statement | Structured form of a claim: concept IDs, typed value and qualifiers, linked to source spans | 5.7 |
| Judgment | Assessment of one claim revision under a named scope, ruleset and evidence snapshot | 5.3 |
| Control record | Typed lifecycle, permission, authorization-reference, procedure, publication, dispatch or receipt record | 5.4 |
| Concept | Vocabulary entry (entity type, property, value, event type or role) with labels and relations | 5.8 |
| Slot | (entity or `same_as` cluster, property): the unit of deterministic comparison | 9.7 |
| Source class | How bytes entered the system; not authorship proof, truth or action intent | 7.1 |
| Principal | Authenticated human user, agent principal or service principal | 7.3 |
| Agent principal | Persistent agent identity with its own scopes and a human overseer | 7.3 |
| Home scope, owner | The single scope a record belongs to, and the principal it was captured for | 7.3 |
| Right | One of `l r w c d m` on a scope | 7.3 |
| Elevation | Explicit, time-bounded, audited exercise of administrator authority | 7.3 |
| Dependency | Restrictive requirement derived from ancestry: who may access an object and what deletion propagates to it. The requirement closure is the union over all ancestors, less requirements waived by publication. Only owner publication waives one; certified redaction (12.2) and the tested contracts of 8.2–8.3 limit which ancestry a new object acquires. Elsewhere, “dependency” means a requirement or the ancestry edge it comes from; named contracts (read\_dependencies, dependency contracts) keep their names | 5.5, 8.2 |
| Evidence relation | An attributed assessment of support, opposition or identity; never a permission edge | 5.5 |
| Publication | Owner's act of copying an item into a target scope, waiving a scope's access requirement only for ancestors the owner owns; ancestry is kept | 10.6 |
| Lineage exclusion | Task-level rule excluding from a context everything whose ancestry includes named sources | 10.6 |
| Snapshot position | Ordered canonical commit position for an assessment or read | 9.1 |
| Evidence epoch | Monotone revision of a scope's assessment-relevant collection | 9.3 |
| Restriction epoch | Monotone revision used to invalidate cached security eligibility | 9.4 |
| Handle | Principal- and scope-bound reference to a protected value; not an access capability | 8.3 |
| Release | Bytes or a command crossing the last UPMS-controlled boundary | 8.4 |
| Barrier | Durable restriction serialized with releases and descendant commits | 9.4, 12.3 |
| Flag, cue | Flag: a screening result for investigation, with cues giving its reasons. Comparison cue: a recorded, informational screening output that is not a flag | 9.7 |
| Adapter | Per-scope low-rank weights on a fixed small base model, held as a derived index | 9.8 |
| Hub | A derived overview page (L0, L1 or L2) with exact projections, a consolidated narrative and an overlay | 10.5 |
| Consolidation | Regional replay that rewrites a region's narrative as one coherent piece, plus the per-scope global pass over L1 hubs | 10.5 |
| Coverage | Captured, indexed, processed, structured, screened, retained and instrumented extent actually available | 10.3 |
| Ancestry | Immutable production and exposure lineage recorded by trusted capture, runtime or approved transforms; never removed while any descendant survives; traversed by lineage exclusion, incident recall and subject discovery | 5.5 |
| Coordination record | A control recording a decision, commitment, blocker, ownership claim or interface agreement, entered by its author and never extracted; same-key conflicts are shown deterministically (5.4, 6.9) | 10.5 |
| Narrative unit | The output of one consolidation invocation, or of one independently generated section; the unit of invalidation | 10.5 |
| Own-record entitlement | A record owner's right to list and read a record built only from records the same principal owns; the oversight entitlement extends it to the agent's overseer | 7.3 |
| Region | One scope's area, consolidated as a unit; divided at consolidation into sub-regions by entity, then by time window, when its input exceeds the replay cap | 10.5.4 |
| Approval record | An authenticated, scoped control by a role holder, stored with its role evidence; the only way to meet a rule exception | 5.4, 9.7 |
| Language tag | BCP 47 tag and script recorded per source span; detection is a processing output, und when unknown | 5.9 |

**Precedence.** The strongest applicable restriction wins: deletion and access denial block ordinary use; quarantine permits only its investigation route; correction prevents stale-current use but can permit qualified history; a task's lineage exclusion removes items from that task's context only; suppression affects proactive retrieval only. Admission never overrides a restriction. Permissions decide who may access a scope; restriction tags, purpose and barriers can only narrow that further. Current external policy controls each new decision; historical policy references explain history only.

## 3. Architecture at a Glance

**The mechanism in brief.** Three record types (Event, Claim, Judgment) and typed control records live in one memory core with a single committer per tenant partition. Two relation families keep meaning and data flow apart: evidence relations explain beliefs; exposure relations drive security, deletion and recall. Claims carry structured statements over a curated vocabulary, so deterministic code can screen for conflicts before an LLM investigates. Scope permissions decide who may list, read, write, curate, delete or manage memory. A derived overview layer gives every reader a small map whose exact lines are current at read, or marked stale, and whose narrative, labeled as synthesis, is made coherent by consolidation. Two integration profiles bound what can be claimed: a memory service guarantees scoped retrieval, correction and deletion; only an instrumented runtime can claim end-to-end information-flow properties. Permission to act always comes from external policy.

```text
Capture adapter ──events──▶  MEMORY CORE  ◀──proposals── Processing workers
(authenticates,             (single committer,           (extract, screen,
 marks spans)                barriers, permissions,       consolidate; propose
                             vocabulary)                  only, never commit)
                                  │ outbox: projections, hubs; read-time catch-up
                                  ▼
                          Retrieval service
            (eligibility before ranking; indexes, hubs, adapters)
                                  │ eligible context, L0 map
                                  ▼
                          Runtime adapter ──checked release──▶ Models, tools, people
          (manifests, handles, segments;                      (reached only by release;
           checks every release)                               processors need approval)
           manifests and outcomes are committed back through the memory core

External owners: identity provider and policy, KMS — membership, admin role,
capabilities and keys, consulted by core, retrieval and runtime
```
*Figure: One committer owns state; every release is checked.*

Content enters through capture with its source classes, is committed only by the memory core, and leaves only through eligible retrieval and a checked release; all canonical writes, including runtime records, go through the core.

## 4. Ownership and Interfaces

**Four internal responsibility boundaries own all UPMS state; external owners keep identity, policy, keys and effects.** The boundaries are not four compulsory services. In-process code shares one trust boundary, and separate credentials alone do not isolate hostile code in one process: run untrusted parsers, extensions and workers with process and capability isolation when required.

### 4.1 Component ownership

| Component | Owns | Cannot do |
| --- | --- | --- |
| Memory core | Canonical append and transition validation; revision and epoch allocation; barriers; dependency integrity; scope-permission records and their evaluation; vocabulary records; screening flags; purge state; durable outbox | Grant external capabilities; infer external truth; invoke models or actions during replay |
| Processing workers | Bounded execution and proposals (extraction, screening candidates, overlay notes, consolidation, adapter training), submitted to the core as durable attempts | Write canonical state directly, choose permissive rulesets, lower restrictions or promote their own outputs |
| Retrieval service | Disposable indexes and projections, including overview hubs and per-scope adapters; selection; coverage; explanation; per-reader overview assembly | Promote a claim by ranking; bypass permission evaluation or final release checks |
| Runtime adapter | Capture instrumentation and span source marking; segment and handle execution; complete submitted-context capture; propagation; lineage exclusions in context; mediated egress | Forge provenance, infer authority from content, release without current checks |

Canonical ownership and execution responsibility differ: the runtime produces manifests, handles and outcomes, but the core commits their durable records. In-memory handles vanish at restart unless their protected backing and bindings were committed. Workers own no authoritative durable state.

### 4.2 External contracts

| Concern | Owner |
| --- | --- |
| Authentication, principal identity, group membership, the administrator role, delegation, revocation | Identity provider (external). The pilot may use a built-in directory behind the same interface |
| Which memories a principal may list, read, add to, curate, delete or manage | **UPMS**, through scope permissions (§7.3), evaluated by the memory core and enforced by retrieval and egress |
| Action capabilities, destinations, processors, authenticated purpose compatibility | External policy |
| Key lifecycle | Key-management system (KMS) |
| Current state of repositories, trackers, calendars | Those systems of record |
| Effects and retry semantics | Each tool |

Providers are processors, not implicitly authorized destinations. Policy decisions bind principal, tenant, authenticated purpose, operation, exact resource or destination, policy revision, validity and revocation conditions. A caller-supplied purpose string cannot widen scope. Unknown identity, membership, scope mapping or processor permission denies the affected use. Policy- and membership-cache validity and revocation delay are explicit; consequential releases use online decisions in the initial profile. Memory content can never change permissions, membership or roles.

### 4.3 Typed operation families

| Operations | Caller and guard | Required right | Commit owner |
| --- | --- | --- | --- |
| `record_event`, `record_manifest`, `record_outcome`, `record_processing` | Registered capture, runtime or worker identity for that type | Component role | Core |
| `search`, `get_context`, `expand`, `get_evidence`, `get_overview` | Authorized caller, purpose, scope and intent | `r` (`l` for existence only) | Read-only; release checked |
| `propose`, `report_conflict`, `request_assessment` | Scoped, quota-limited; never promotes or quarantines | `w` | Core |
| `submit_assessment`, `submit_screening`, `submit_overview` | Registered assessor or worker, assigned ruleset or schedule, complete attempt, dependency and epoch checks; assessments with forbidden inputs are never admitted (§9.3) | Component role | Core computes the allowed transition |
| `correct`, `suppress`, `redact`, `delete`, `deletion_status` | Target-specific authority; subject ambiguity stays explicit | Own items: `w`; others' items: `c` (correct, suppress) or `d` (redact, delete) | Core |
| `publish`, `withdraw_publication` | Item owner | Ownership, plus `w` on the target scope | Core |
| `endorse`, `revoke_endorsement` | Exact object, type and use capability | `r`, plus the endorsement capability | Core |
| `approve_procedure`, `activate_procedure`, `suspend_procedure`, `revoke_procedure` | Exact version; distinct approval and activation authority | `m` | Core |
| `quarantine`, `release_quarantine` | Policy-authorized detector or investigator; bounded scope; reason | Investigator role | Core |
| `prepare_dispatch`, `record_dispatch_outcome` | Trusted egress adapter; exact action and idempotency binding | Component role | Core |
| `create_scope`, `get_permissions`, `set_permissions`, `transfer_ownership`, `explain_access` | Scope manager or administrator | `m` (`l` for `explain_access` on own access) | Core |
| `elevate`, `end_elevation` | Holder of the administrator role, re-authenticated | Admin role | Core |
| `propose_concept`, `curate_concept` | Extractor or principal; curator | `w` to propose; `c` or `m` to curate | Core |
| `promote_adapter` | Registered training worker after the promotion gate | Component role | Core |
| `recall`, `export`, `import` | Operator or caller capability; scoped disclosure and migration validation | `r` on exported scopes; `w` on import target; investigator role for recall | Core for imported records; checked output otherwise |
| `record_coordination, close_coordination` | Author; supersession, fulfilment, release or withdrawal by the author or a curator (§6.9) | w (c for others' records) | Core |
| `record_approval, revoke_approval` | Re-authenticated principal holding the named role; exact scope, rule and action | The role, plus w on the scope | Core |
| `confirm_publication, revoke_confirmation` | Owner of an ancestor record whose requirement the publication would waive; exact item and target; C4 confirmation | Ownership of the ancestor | Core |

No API accepts caller-chosen effective labels or admitted state, and no content changes a permission. Model assertions and conflict reports are data. A trusted detector may impose a restriction under policy; arbitrary claims of contamination cannot quarantine another user's corpus. Every mutation has a principal- and tenant-scoped request identity, an expected revision where applicable, and same-request, same-payload idempotency; reusing an identity with different arguments is an explicit conflict. MCP and other transports are adapters over this typed interface and inherit its authentication and scoping.

## 5. Durable Records

**Three semantic record types (Event, Claim, Judgment), typed controls, processing records, one typed relation store, structured statements on claims, and a versioned vocabulary make up all canonical state.** Manifests and dispatches are typed operational records, not a second knowledge ledger. Schemas specify meaning; serialization is D4.

**Common fields:** opaque logical ID and immutable revision ID; tenant; **home scope**; **owner**; authenticated capture or use purpose; schema version; commit position and time; retention-policy version and deadline; source classes; confidentiality restrictions; requirement-closure reference. Fields that contain content or identifying metadata are protected payloads even when stored in a database column. Labels, locators, usernames, relation endpoints, policy references, query text, concept definitions and error text are not presumed public.

### 5.1 Event

```text
Event {
  channel, witness_principal, transmitter_identity?
  origin_identity?, origin_authentication_evidence?
  payload_ref
  spans: [{range, source_class, language, script, origin_ref?}]
  source_namespace, source_message_id?, source_revision?
  observed_at, stated_occurrence_time?, prior_revision?
}
```

Only capture appends observations. An agent's claim of completion is an observed statement; actual completion needs a receipt or inspected artifact. Changed source bytes create a revision. The authenticated source namespace is part of identity, so IDs from separate connectors cannot collide. **The event's original text is the record; everything structured is derived from it.**

### 5.2 Claim

```text
Claim {
  statement_ref, source_locators[]
  statements[]            // structured statements, §5.7; may be empty
  modality, qualifications, asserted_by?
  valid_time, temporal_basis, generated_by
}
```

Modalities: asserted, quoted, hypothesized, intended, committed, preferred, normative. A model's structuring does not prove extraction fidelity. Negation, quantity, units, conditions, attribution and uncertainty are preserved, or the claim stays a source-linked textual claim. Original wording is recoverable while retained and authorized; otherwise an explicit deletion, expiry or unavailability marker is returned, never a fabricated substitute.

### 5.3 Judgment

```text
Judgment {
  claim_revision, scope, ruleset_version
  epistemic_status        // supported | refuted | contested | unknown
  admission_state         // captured | evidence_only | admitted | quarantined
  supporting_refs[], opposing_refs[], qualification_refs[]
  assessor, assessment_output_ref?, processing_ref
  read_dependencies[], evidence_scope_epochs[], snapshot_position
  applicable_time, supersedes?
}
```

Each ruleset defines qualifying support and opposition, correlated-source treatment, missing evidence, its domain and admission criteria. Copies of one source are not independent support; model confidence is not evidence. Restrictive exposure and evidential sufficiency stay separate: an independent basis can support a conclusion without a disputed derivation, but an artifact exposed to a deleted or private source keeps its restrictions.

Judgments in different scopes or rulesets coexist. Within one claim, scope and ruleset lineage, replacement names the prior head and checks it atomically; concurrent disagreement is never resolved by last write. The initial policy returns authorized conflicting judgments with their scopes and leaves them unresolved; there is no cross-scope most-permissive selection.

### 5.4 Controls and processing

Controls: correction, suppression, quarantine, redaction, deletion, endorsements, procedure versions and activation, policy references, dispatch intents and receipts, **scope-permission revisions, elevations and access records, publications, vocabulary changes, adapter promotions, overview consolidations, coordination records and approval records**. Their state is derived from validated appended transitions.

**Coordination records** (decision D-15) carry what a team must see at once, without extraction:

```text
CoordinationRecord {
  kind      // decision | commitment | blocker | ownership_claim | interface_agreement
  key       // task, topic, interface or commitment identifier
  value, author, scope, due?, supersedes?
  status    // open | superseded | fulfilled | released | withdrawn  (§6.9)
}
```

They are entered by their author through `record_coordination`, never extracted, and state what was recorded, not admitted facts. A commitment has one authority: an extracted Claim with `modality: committed` that carries an explicit reference to an open coordination record's key links to it and never opens a second obligation. **Approval records** are authenticated, scoped controls made by a principal holding the named role at commit time, stored with the role evidence the identity provider returned; they are the only way to meet a rule exception (§9.7).

```text
ProcessingRecord {
  kind, invoker, input_manifest_ref
  model_or_program_version, prompt_or_program_ref, configuration_ref
  output_ref?, outcome    // completed | partial | failed | cancelled | uncertain
  started_at, completed_at?
}
```

Attempts and outputs are separate immutable records. A timeout or crash never synthesizes completion. Reprocessing has a new identity. Required programs, transformations, reducers, vocabulary versions and screening versions stay available for replay of surviving records.

### 5.5 Relations, ancestry and requirement closure

| Kind | Relations or records | Semantics |
| --- | --- | --- |
| Exposure and production | `observed_from`, `exposed_to`, `generated_by` | Trusted observations; source → invocation → output traversal supports forward recall |
| Evidence | `supports`, `opposes`, `same_as` | Assessor, exact endpoints, scope, locator, status and qualification |
| Statement content | `stated_reason`, `condition`, `exception` | What an asserter said; part of claim content (§5.7.2), never evidence |
| Lifecycle | Validated controls with `supersedes` and `retracts` links | Only an authorized transition changes current state; an agent-proposed link is inert |

Ancestry edges are object → prerequisite-revision references. A model output depends on its manifest's complete inputs; a dispatch depends on its arguments and the context that selected it; an adapter depends on every record it was trained on; a hub depends on every item it summarizes. Reverse traversal finds descendants. Pre-existing sources do not become descendants merely by sharing a manifest. Operational records and relations receive the restrictions of the information they expose.

Ancestry edges form a DAG over immutable production revisions. Cycles, nonexistent references, foreign-tenant edges and unvalidated narrowing are rejected. Ancestry and requirements are distinct. Exposure and production relations form an immutable ancestry that is never removed while any descendant survives (§11.2); restrictive requirements (who may access an object, and what deletion propagates to it) are derived from that ancestry. Only owner publication (§10.6.2) waives a requirement on existing ancestry; certified redaction copies (§12.2) and the tested contracts of §8.2–§8.3 limit which ancestry a new object acquires. None removes ancestry. Lineage exclusion, incident recall and subject discovery always traverse ancestry, never only the requirement closure. Evidence relations may be cyclic and are traversed with visited sets and limits. Closure indexes are derived accelerators. Missing closure, incomplete runtime coverage or a traversal timeout is not proof of independence: the affected use or scope is contained. Dependency validation and barrier checks are synchronous at commit and release; background graph expansion is not the safety mechanism.

### 5.6 Identity, time and scope

IDs are opaque, stable and never reused. Digests are separate protected integrity data, tenant-scoped and erased with payloads; no durable plaintext hash of a sensitive value. Entity matching is a reversible scoped `same_as` assessment, never a physical merge or an access grant.

Bitemporal records distinguish transaction order from valid time, durations from uncertain occurrence intervals, and unknown from exact time. Relative expressions keep raw wording, source timestamp, timezone if known and resolution basis. Reprocessing temporal interpretation creates a new assessment. Cross-scope derived artifacts inherit all restrictions; membership alone never broadens an item's readership or permitted purpose (§7.3.5).

### 5.7 Statement language

**A claim may carry structured statements: canonical concept IDs plus explicit qualifiers, derived from the source text and linked to the exact words they came from.** They let deterministic code query and compare before an LLM interprets. **Fixed (proposed).**

#### 5.7.1 Statement

```text
Statement {
  statement_id, claim_ref, kind     // state | event | generic | rule
  subject:   entity_ref | ambiguous{candidate entity_refs}
  property:  concept_ref            // state statements
  event:     {event_type concept_ref, roles {agent, object, recipient,
              instrument, ...: entity_ref | literal}}   // event statements
  value:     concept_ref | number{value, unit} | text_literal | interval
             | ambiguous{candidate values}
  qualifiers: {
    valid_time:  instant | interval | imprecise range | unknown
    place:       place_ref | unknown
    polarity:    positive | negative
    modality:    asserted | quoted | hypothesized | intended | committed
                 | preferred | normative
    aspect:      ongoing | completed | habitual | none
    attribution: {asserted_by, quoted_from?}
  }
  span_refs[], extraction_ref, vocabulary_version
  structure_status: full | partial | text_only
}
```

- **Events and states are declared by the vocabulary, not by grammar.** “It is raining,” “the sky rains” and “rain fell” all become a rain event; grammatical subject is not semantic role.
- **Aspect and genericity are kept.** “It rains a lot in Seattle” is a `generic` statement; “it is raining in Seattle” is an ongoing event. They neither merge nor conflict.
- **Defaults come from the source.** Unspecified time defaults to the source event's observed time with `temporal_basis: utterance`; unspecified place stays `unknown`. A default is recorded as a default, never as a stated fact.

#### 5.7.2 Links between statements

Rationales, conditions and exceptions are statements joined by typed links, not text appended to another statement. One rationale may justify several statements, and each link has its own attribution and can be disputed separately. Any “appendix” grouping a reader sees is a presentation view.

| Link | Meaning | Layer |
| --- | --- | --- |
| `stated_reason` | The asserter gave B as the reason for A | Claim content |
| `condition` | A is asserted to hold when B holds | Claim content |
| `exception` | A rule does not apply when B holds | Claim content |
| `supports`, `opposes` | An assessor judges B to be evidence for or against A | Judgment layer (§5.5) |

A stated reason is never evidence; keeping `stated_reason` out of the judgment layer prevents someone's rationale from silently becoming proof.

#### 5.7.3 Rules

```text
Rule {
  deontic:     prohibited    // pilot; required and permitted stay partial text
  pattern:     event_type | (entity_type, property)
  constraints: conjunction of comparisons on properties and qualifiers
               (=, ≠, <, >, ∈, weekday, interval relations)
  exceptions:  patterns met only by authenticated approval records (§9.7)
  scope, authority_ref        // the actual authority source
}
```

The operator set is fixed and small, and the pilot structures only prohibitions; required and permitted rules stay source-linked text with structure\_status: partial until their semantics are specified. Nested quantifiers, defaults such as “usually,” counterfactuals and vague thresholds are not structured; such a rule stays source-linked text with `structure_status: partial`. A rule in memory never enforces anything: matching produces flags only (§9.7), and the governing policy stays with its authority.

#### 5.7.4 Ambiguity

When the extractor cannot choose, the field holds `ambiguous{…}` with an unordered set of candidates. Screening treats it as “could match any candidate” and raises a cue, never a verdict. No numeric weights are stored: model-stated percentages are not calibrated probabilities, and calibrated confidence is a D1/D2 reopen trigger (§1.4). Fuzzy similarity belongs to retrieval indexes, not canonical storage.

#### 5.7.5 Text first

- Every structured field links to the span it came from.
- If text and structure disagree, the text wins and the structure is re-extracted under a new processing identity.
- Deleting or redacting the text deletes the dependent structure (§12).
- Agents receive both: text for meaning, structure for cues.

Memory that does not normalize stays available as text. Coverage reports structured, partial and text-only extents separately (§10.3).

### 5.8 Vocabulary registry

**Statements store concept IDs; synonyms, relations and comparison rules live once in a versioned vocabulary.** Adding a synonym changes the vocabulary, not every record, and query expansion through it is deterministic. **Fixed (proposed).**

```text
Concept {
  concept_id, kind       // entity_type | property | value | event_type | role
  labels: {language → preferred, aliases[]}, definitions: {language → text}
  relations: exact_match[], close_match[], broader[], narrower[], related[], replaced_by?
  status: active | deprecated
  home_scope, vocabulary_version
}
```

Relations follow the SKOS pattern and do more work than synonyms: hue and lightness are narrower dimensions of color, so “blue” and “dark” may both hold; azure is narrower than blue, so it refines rather than contradicts.

**Property schemas.** Every property concept declares what deterministic comparison needs:

| Field | Purpose |
| --- | --- |
| `value_type`, `unit_dimension` | Which values are well formed; unit conversion |
| `cardinality` | `single` (one value at a time) or `multi`; only single-valued properties can conflict by value |
| `varies_with` | Whether values depend on time, place or both |
| `value_space` | Allowed concepts or numeric range |
| `compatibility` | Refinement through `broader`; separate dimensions never conflict; optional numeric tolerance |
| `default_qualifiers` | For example, time defaults to the source's observed time |

Event types declare their roles and whether two events of the type can coexist at one time and place.

**Scope.** The tenant has a base vocabulary readable by all users. Each scope may extend it; a scope's concepts and definitions are scope content under §7.3, because a definition can disclose information. Curation is a derivation, never a waiver: a curated concept keeps the ancestry and requirements of the proposals and examples it came from and is visible only to principals with rights on its whole requirement closure; a candidate whose closure exceeds the target scope is refused, and the base vocabulary accepts only concepts with no requirement beyond what all users can read. Statements record the vocabulary version they were extracted with.

**Governance.**

- Proposals are inert. When extraction meets an unknown term, it proposes a new concept or a mapping to the nearest existing one; the proposal takes effect only after curation by a holder of `c` or `m` on the vocabulary's scope, or by an accepted deterministic rule.
- Merges and splits are reversible, like entity `same_as`. Every merge re-screens the slots it joins (§9.7).
- Deprecation keeps recognition: a deprecated term remains an alias mapped through `replaced_by`, so old memories stay retrievable and comparable, while extraction and display prefer the current label. A term is removed only when no retained memory uses it.
- Every change produces a new vocabulary version; derived indexes record the version they were built with and rebuild when it changes.

**Initial vocabulary.** Project-work concepts only: tasks, decisions, components, configuration values, deadlines, people and roles, and events such as release, deploy and review. It grows by curated additions, not by agents minting properties freely.

**Expansion (adaptation tier A).** Indexes and queries expand terms with preferred labels and definitions, in every pilot language (§5.9): “HAS” is embedded as “HAS (Historical Applicability Set).” Off-the-shelf retrieval models then understand domain jargon immediately, deterministically and without training.

### 5.9 Natural languages

**One vocabulary serves every language, and the original words are always the record.** Memory may be written in any language, and one message may switch languages. Meaning is carried by language-neutral concepts, while evidence stays in the words as written (decision D-19). **Fixed (proposed).**

- **Original text is the record.** Events keep their bytes as written; Unicode normalization (NFC, locale-aware case folding and width folding) applies only to indexes. Each span carries a BCP 47 language tag and script, detected per span as a recorded processing output with its confidence, `und` when unknown, and correctable like any extraction. Citations always point to the original span in its original language.
- **Concepts are language-neutral.** A concept has labels and definitions per language. Words that mean the same thing in different languages are labels of one concept, so statements, slots, rules, screening and hubs work across languages with no translation step: “production deploy” and “本番デプロイ” resolve to one event-type concept, and a no-Friday-deploy prohibition written in English screens an event recorded in German.
- **Equivalence is curated, not assumed.** Languages divide meaning differently: a word in one language may cover two concepts in another. A label joins a concept only through curation; model-proposed translations are inert proposals like any other (§5.8). Where meanings only overlap, the concepts stay separate and are linked by `close_match`, which never joins slots: a comparison across a close match gives at most a possible flag with the cue `cross_language_mapping`.
- **Names are not translated.** People, products and places are entities whose aliases record script and transliteration (東京, Tokyo); identity still follows reversible `same_as` (§5.6).
- **Values and formats.** Numbers, dates, times, units and currencies are parsed with the span's locale into typed values before comparison; a parse failure leaves the statement text-only.
- **Retrieval.** Lexical indexes use a per-language analyzer (word segmentation for languages written without spaces, such as Chinese, Japanese and Thai; stemming where it helps), with a character n-gram fallback for other languages and `und`. Vocabulary expansion bridges languages: a query term expands to its concept and then to that concept's labels in every pilot language. Embeddings come from a multilingual base model (§9.8). Coverage reports a language without an analyzer or vocabulary labels as degraded, never as “none found”.
- **Rendering for readers.** Exact projections render concept labels in the reader's preferred language deterministically, falling back to another label with its language marked. Quotes are always shown in the original language; a translation may accompany a quote only as labeled synthesis (source class M) with its own ancestry. A narrative is generated in the readers' preferred language, and a translated narrative is another narrative unit with the same inputs.
- **Translation is never authority.** A translation is never evidence for admission and never grounds an action argument (§7.2); only the original exact value can. Sending text to a model or external service for translation is processing and, outside UPMS, disclosure: processor policy, purpose and restrictions apply (§7.4, §8.5).
- **Spoofing.** Labels, aliases and entity names are checked for confusable and mixed-script strings (Unicode UTS #39); a proposal that collides with an existing label across scripts is flagged to the curator, so a look-alike cannot capture a concept.
- **Pilot languages.** The base vocabulary carries labels for the pilot languages (§14.2). Other languages are stored, cited and retrieved by n-grams and embeddings, and their structuring is reported as unavailable.

## 6. Lifecycles

**Every lifecycle change is an appended, validated control record; current views are projections, never separately editable facts.** Ordinary transitions append; payload and metadata erasure is the explicit physical exception (§12).

### 6.1 Modality projections

| Modality | Lifecycle contract |
| --- | --- |
| asserted | Applicability and freshness are separate from superseded or retracted status; either can change without passing through a mandatory stale state |
| quoted | Quotation fidelity and the inner claim are distinct; a quotation can be corrected without accepting its contents |
| hypothesized | Open or abandoned investigation; supported, refuted, contested or unknown comes only from Judgment |
| intended | Active → completed, abandoned or superseded, with an authorized statement or completion evidence |
| committed | Open → fulfilled, released or superseded; overdue is a time-derived flag on an unfulfilled commitment, not a terminal state |
| preferred | In force → superseded or withdrawn by the same principal within the applicable scope |
| normative | Historical reference plus applicability from the actual authority source; memory cannot enact or repeal policy |

No completion, cancellation or release is inferred from retrieval decay. Scope policy defines who may release a commitment, including explicit delegation; a model cannot invent a counterparty's approval.

### 6.2 Assessment, admission and quarantine

No judgment means captured. A completed authorized assessment produces evidence-only or admitted under the assigned ruleset and §9.3. New evidence or rule changes invalidate current admission until revalidated; old judgments remain historical.

Quarantine is an access restriction layered over assessment. Removing it removes only that restriction, then recomputes current admission, authority and freshness; it never blindly restores a previous admitted state. Authorized investigation is isolated with restricted egress. Ordinary users may report a concern, not rewrite another principal's admission state.

### 6.3 Correction

`requested → applied | proposed_to_owner | pending_clarification | rejected`; pending requests may be clarified or withdrawn.

- A principal can retract or correct their own attributed statement (`w`).
- A correction to someone else's source is proposed to its owner, or applied by a curator (`c`) as a correction attributed to the curator; the original remains in history.
- A request about an agent-generated claim concerning the requester may correct that claim under scope policy, but cannot erase independent third-party sources.
- Verified non-user correction uses the deployment's identity and visibility process.

The interface presents the exact event, revision and spans or claim, the scope and the effect. Ambiguous requests stay visibly pending; any provisional restriction is limited to already-authorized targets. An applied correction atomically appends the replacement or retraction, invalidates current dependents (including affected statements, flags and hub lines) and establishes the barrier in §9.4. Historical recall may show the old version explicitly paired with its correction. Correction never claims erasure.

### 6.4 Endorsements

`presented → valid → revoked | expired`; new bytes or a new use require a new endorsement. An endorsement binds object revision, field or claim, type, meaning, scope, intended use, endorser, current policy decision and validity conditions. Types: extraction fidelity, factual attestation, permitted reliance. None changes provenance, confidentiality or general action capability. Revocation invalidates future reliance and schedules dependent reassessment and recall. A historical endorsement remains a historical fact, not current permission.

### 6.5 Procedures

`draft → approved → active → suspended | revoked`; a suspended version needs fresh authorized activation to resume. Any edit is a new draft. Approval binds exact bytes; activation (`m` on the scope plus current authority) binds scope and applicability. Loading and each consequential use recheck revocation. No procedure grants a tool capability. Agent proposals and imported procedures are inert until independently activated.

### 6.6 Suppression

`active ↔ lifted` by an authorized scope principal (`c`, or `w` for own items). Suppression blocks proactive surfacing only; explicit authorized recall still returns the item with its status. It does not alter truth, admission, access, retention or deletion.

### 6.7 Permissions and elevation

| Transition | Guard | Effect |
| --- | --- | --- |
| Grant or widen | `m` on the scope, or elevated administrator, within §7.3.6's limits; never on an agent's private scope | New permission revision; effective immediately |
| Narrow, remove member, transfer ownership or oversight | `m`, elevated administrator, or identity-provider membership change | Restriction commit under §9.4; acknowledged only after the release fence |
| Elevation opened | Administrator role; re-authentication; reason; scope; duration ≤ profile limit | Elevation record; access records for every content access during it |
| Elevation ended | Expiry, explicit end, or role revocation | Restriction commit; pending releases relying on it are withheld |

### 6.8 Publication

`published → superseded | withdrawn`. Publication creates a new attributed copy in the target scope (§10.6.2). Superseding names the revision being replaced and is recorded as a conflict if that revision has changed. Withdrawal is a retraction in the target scope; readers who already saw the item are not “unseen.”

### 6.9 Coordination records

`open → superseded | fulfilled | released | withdrawn`. Only the author, or a holder of `c` on the scope, closes or supersedes a record; any other attempt is recorded as a conflict. A commitment marked fulfilled without a linked receipt shows as “claimed fulfilled by ⟨author⟩”, and releasing or withdrawing a commitment follows §6.1's scope policy on who may release it. A claim links to a coordination record only through an explicit key reference recorded at capture; otherwise it is shown separately with a possible-duplicate cue, and a later claim never reopens a closed record. **Same-key conflict rule (deterministic):** two open records of the same kind and key with different values, neither superseding the other, form an attributed conflict shown wherever either appears; any two open ownership claims on the same key conflict. A commitment past its due date is shown overdue, never closed by time.

## 7. Trust, Access and Action Policy

**Provenance is recorded as fact, access is decided by scope permissions, and actions are checked against operation contracts; none of these is ever granted by memory content.**

### 7.1 Source classes

| Class | Capture meaning |
| --- | --- |
| A — direct entry | Adapter-observed direct input by an authenticated principal with trustworthy span marking |
| R — relayed | Pasted, attached, forwarded or quoted content; all chat text when input-mode provenance is unavailable |
| C — connector-declared | Exact fields independently configured as produced by the source system itself |
| X — external or unknown | Untrusted connector fields, web content, third-party messages, unknown origin |
| M — model-generated | Every model output, including statements, overlay notes, hub narratives and consolidation output |

A does not prove intellectual authorship, correctness or intent: a person can retype malicious text. C is field- and contract-specific, not trust in a whole tool response. Missing input-mode instrumentation means R; content classifiers cannot manufacture A or C. Model-derived objects carry M plus the union of input classes. Automated analysis can only add restrictions.

### 7.2 Consequence classes and grounding

Every operation has a trusted registered contract defining effects, target-binding arguments, payload and disclosure fields, normalization, execution identity, resource limits, conditions and idempotency behavior. Recipient, host, path, account, amount, permission subject, query string, headers and attachments cannot escape checks by a convenient field name. An unknown or inadequately characterized operation is **blocked** until contracted; a generic confirmation cannot make unknown effects reviewable.

Grounding means an exact, canonically resolved value is authorized **for this argument role and operation**, through a trusted task-intent binding, a connector field declared authoritative for that role, a valid exact-use reliance endorsement, or explicit dispatch confirmation. Mere occurrence of the same string in an A or C span is insufficient, and a translation never grounds an argument (§5.9). Relative paths resolve against a bound root, symbolic links at use, recipients and accounts against their actual identity, URLs through the controlled network path. Ambiguous resolution blocks the action. The runtime enforces this; the model only proposes.

| Class | Examples | Initial integrity rule (capability, confidentiality and barrier checks always apply) |
| --- | --- | --- |
| C0 | Scoped memory read | Authorized scope, rights and purpose; bounded read |
| C1 | Reply to the requesting principal | Recipient may receive every restriction; retrieved material rendered as attributed data |
| C2 | Memory proposal or isolated draft | Restricted artifact in authorized storage; an arbitrary filesystem write is not automatically C2 |
| C3 | External disclosure, fetch, message, contracted tool write | Role-bound grounding; policy permits influencing sources; X-influenced outgoing payload requires exact-payload confirmation by default |
| C4 | Irreversible, financial or permission-changing operation | C3 requirements plus per-action confirmation by the authorized principal; from Slice 1b, an agent's self-publication under §10.6.2 is the one pre-authorized class (decision D-17) |

Confirmation shows normalized operation, effective target, payload, consequences and qualifications. It is nonce-bound, single-dispatch, time-bounded and invalid after any argument or revision change. Capability is separate from task intent. Conservative provenance plus grounding does not guarantee semantic obedience; end-to-end action quality remains an evaluated limitation.

**Public-reader exception.** A registered, explicitly enabled public browsing operation may waive target grounding and X-payload confirmation for an isolated public reader with no private inputs, credentials, cookies, authorization headers, local files, internal-network reachability or persistent privileged provider state. All bytes and observable request choices must be eligible for public disclosure. The broker allows only contracted public HTTP(S) reads, bounds redirects, size and time, and revalidates destination addresses at connection time and on every redirect; DNS rebinding, loopback, link-local, metadata services and private destinations are denied. Public GET is not assumed effect-free. **Disabled in the initial pilot until qualified.**

### 7.3 Memory access control

**UPMS owns which principals may list, read, add to, curate, delete and manage memory in each scope.** Permissions are control records changed only through authenticated operations. **Fixed (proposed).**

#### 7.3.1 Principals

- **Human users**, authenticated by the identity provider.
- **Groups**, whose membership the identity provider owns (pilot: built-in directory behind the same interface; *decision D-4*).
- **Agent principals**: persistent agent identities with their own scopes and a designated human **overseer**. An agent principal's reach never exceeds its overseer's (decision D-9): it can list or read only what its overseer, acting without elevation, can list or read. Its write, curate and delete rights on its own scopes are not bounded this way, and no agent principal holds `m`.
- **Service principals** (capture, workers, purge controller, index and adapter builders), governed by component roles (§4.3), not scope permissions.

An agent session acting for a principal holds the intersection of that principal's rights and the session's grant, and never elevates. “Other” means every human user of the tenant.

#### 7.3.2 Scopes and ownership

Every record has one home scope and one owner: the principal it was captured for. Output of an agent principal is owned by that agent; output of an agent session acting for a user is owned by the user; a human's messages to an agent are owned by the human. Record ownership is distinct from the scope owner named in a scope's permissions. Permissions attach to scopes; the only per-record rights are the own-record and oversight entitlements (7.3.4); a record's restriction tags may narrow access but never widen it beyond its scope. Scopes may have a parent for organization: a parent's permissions are copied as defaults when a child is created, with no live inheritance, so moving a scope never silently changes who can see it (*decision D-3*).

#### 7.3.3 Rights

| Right | Linux analog | Allows |
| --- | --- | --- |
| `l` list | directory read | Knowing an item exists; non-content metadata; appearing in counts, coverage, flags and overviews |
| `r` read | file read | Retrieving content, for the principal and its agent sessions; implies `l` |
| `w` write | file write | Adding memories; correcting, redacting or deleting own items; proposing corrections and concepts; publishing own items |
| `c` curate | — | Acting on others' items: attributed corrections, scope suppression, resolving proposals, curating vocabulary |
| `d` delete | write on parent, sticky bit off | Deleting others' items |
| `m` manage | `chmod`, `chown` | Permissions, ownership, scope retention, procedure activation, child scopes |

Displayed Linux-style, for example `owner lrwcdm · group lrw--- · other ------`. `w` without `r` is valid (a drop box): a contributor then reads only its own items, through the own-record entitlement (7.3.4). Writing never overwrites; every change appends an attributed record.

#### 7.3.4 Evaluation

For principal *p*, operation *o* and target *t*, in order:

1. If *p* is an elevated administrator for *t*'s scope, apply 7.3.6.
2. Rights on the home scope are the **union** of every matching entry: owner, named principal, each group containing *p*, other. **Own-record entitlement:** the owner of record *t* also holds `l` and `r` on *t* when every input record in *t*'s ancestry is owned by that same principal; a record built from others' records gets no entitlement and is checked under step 4. **Oversight entitlement:** an overseer holds the same `l` and `r` on every record its agent principal owns that is built only from that agent's records; others are checked under step 4.
3. For an agent session, intersect with the session grant. For an agent principal, cap `l` and `r` at its overseer's non-elevated `l` and `r`, recomputed for every scope checked in step 4; on its own private and operational scopes the agent keeps `w`, `c` and `d`, and it never holds `m`.
4. For a derived item, require the needed right (`r` or `l`) on **every** scope in its requirement closure, against current permissions (7.3.5), applying steps 2 and 3 to each scope.
5. Apply all other checks unchanged: restriction tags, authenticated purpose, quarantine, correction state, barriers, processor rules, and the task's lineage exclusions, which traverse ancestry.

There are no deny entries; exclusion uses narrower groups. Linux's owner-precedence rule is deliberately not copied. Unknown membership or permission state denies (§13).

#### 7.3.5 Derived and cross-scope memory

A derived item is readable only by principals who can read all of its sources. If an agent reads a team scope and saves a summary in a personal scope, a teammate without access to the personal scope cannot read it, and the owner loses it upon leaving the team (*decision D-6*). The same holds for a summary of others' records saved in the same team scope once its author's rights there are narrowed. A fresh restatement by the user is a new memory with no inherited requirement. Owner publication (§10.6.2) is the only operation that waives an access requirement; it waives a scope's requirement only for ancestors the publisher owns, and never removes ancestry. Vocabulary curation and adapter training are derivations, never waivers (§5.8, §9.8).

#### 7.3.6 Administrator

**Authority:** every right in every scope of the tenant, ownership transfer, and retention within tenant limits.

**Use:**

- The administrator role is assigned in the identity provider; UPMS cannot grant it.
- Administrators act with ordinary rights by default; admin power requires an explicit **elevation** with a reason and scope, lasting at most the profile limit, after re-authentication.
- Every content access or change during elevation creates an access record, which is durably committed to the replicated control plane (§12.4) before the content is released and is governed by the protected audit retention of §11.4.
- Reading a personal scope while elevated notifies its owner (decision D-1); a failed notice is recorded and shown, never treated as delivered.
- An elevated administrator cannot grant rights to themselves, to a group containing themselves or to agents they oversee, take ownership of any scope, or make themselves an overseer; transferring oversight, or an active user's personal scope, requires a second administrator and notifies the previous overseer or owner.
- Agent sessions never inherit elevation (*decision D-2*).
- Bulk destructive operations (whole-scope deletion, tenant-wide retention cuts) require confirmation and a cancellable delay.

**Limits that bind administrators too:** no reading past a deletion barrier; no records attributed to another principal and no forged source class; no direct setting of labels, admission or history; no bypass of quarantine isolation; no disclosure to restricted processors; no granting of tool capabilities; no self-assignment of the administrator role.

#### 7.3.7 Revocation and offboarding

Narrowing permissions, removing a group member, transferring ownership or oversight, narrowing an overseer's rights (for every agent it oversees) and ending an elevation are restriction commits under §9.4: the restriction epoch advances, acknowledgement waits for the release fence, and pending outputs that relied on the revoked access are withheld. Content already released cannot be unseen. Every narrowing passes four named stages: request received (for a change that starts in the identity provider, its observation is the request); change observed by UPMS; UPMS restriction commit, in the same transaction as the observation; fence complete. Only the last is acknowledged as revoked, and an identity-provider acceptance alone never certifies it. Until UPMS observes a membership change, cached membership may serve reads within the declared bound (§14.2).

When a user leaves, their records in shared scopes keep their owner and attribution, and the scope's `d` holders may withdraw or delete them; their personal scope is deleted at the end of its retention period unless transferred under §7.3.6. An agent principal's scope follows its overseer's decision.

#### 7.3.8 Default permissions

| Scope type | Default |
| --- | --- |
| Personal | owner `lrwcdm`; nobody else |
| Agent principal (private) | agent `lrwcd`; overseer `lrd` as a protected grant the agent cannot remove; nobody else. These permissions are fixed: nobody may widen an agent's private scope, and content leaves it only by publication |
| Team or project | lead `lrwcdm`; members `lrw`; other none |
| Organization-wide | managers `lrwcdm`; contributors `lrw`; all users `lr` |
| Agent-operational (runtime state) | owning principal; for an agent principal, also its overseer `lr` as a protected grant |

### 7.4 Confidentiality and purpose

Restrictions are conjunctive: every tag must permit the recipient, processor, destination and authenticated purpose. Derived data inherits the union. A result spanning several scopes may therefore be unusable; isolate the work instead of dropping tags. Read permission, factual endorsement and summaries never declassify. **Declassification is disabled in the pilot, except owner publication, which waives a scope's access requirement only for ancestors the publisher owns and keeps ancestry (§10.6.2).** Processor identity includes the actual account, region or endpoint, retention mode and downstream handling where material, not just a vendor name.

### 7.5 Reliance endorsements

An endorsement permits reliance only on its exact object or value, role and use. It cannot authorize unrelated output, survive a changed value by text similarity, or grant access. Runtime resolution checks current endorser authority and revocation. Batch interfaces preserve each differing scope, payload and consequence.

### 7.6 Default admission

The initial ruleset admits only attributed first-party statements — “P stated S” — from verified direct-entry spans by P, about P or expressing P's preference, intention or commitment, within an authorized personal or project scope. It admits the attributed statement, not S as external fact. Extraction fidelity requires an exact source-linked rendering or a valid fidelity endorsement; a model-structured paraphrase alone stays evidence-only. Published team items are evidence-only for the team unless endorsed. Other domains remain evidence-only until a domain ruleset is separately accepted. Admission never makes memory normative authority.

### 7.7 Threat model and isolation

Attackers may control documents, ordinary credentials, untrusted fields and cooperating agents; inject delayed instructions; plant jargon or definitions to steer vocabulary, screening or adapters; mislead endorsers; and attempt cross-scope disclosure, false memory, unauthorized effects and resource exhaustion. The trusted computing base (TCB) includes core validation, permission evaluation and barriers; retrieval access enforcement; egress; capture and manifest instrumentation; identity and policy; KMS; and deployment isolation. Compromise of these is outside the guarantee. An ordinary compromised credential keeps its legitimate permissions until revoked; UPMS cannot infer the human's real intent.

Untrusted text and archives are data, never executable deserialization, shell instructions, plugin activation or policy. Filesystem and network credentials and parser resources are restricted. Connector secrets stay outside model context and ordinary logs. A privileged arbitrary shell or uncontrolled outbound route is incompatible with a claimed fully mediated instrumented profile.

## 8. Runtime Flow and Egress

**End-to-end information-flow claims exist only in the instrumented profile, where the runtime records every input, propagates dependencies, keeps untrusted values behind handles and checks every release.**

### 8.1 Two integration profiles

| Property | Memory-service profile | Instrumented-runtime profile |
| --- | --- | --- |
| Eligible scoped retrieval, permissions and UPMS lifecycle controls | Required | Required |
| Every runtime-visible model input captured | Not claimed | Required within declared modality and runtime coverage |
| Output dependency propagation and dispatch checks | Only UPMS-owned workers and releases | All enabled paths in the qualified adapter |
| Task lineage exclusions | Applied to UPMS-assembled context only | Applied to the whole runtime context; independence attestation available |
| Downstream recall and deletion containment | UPMS-controlled surfaces | Also recorded runtime outputs and actions within retained coverage |

A missing egress path cannot be advertised as instrumented merely by listing a gap: disable it, narrow the claim to the memory-service profile, or repair and qualify the adapter. Provider-internal pretrained state is outside the runtime boundary; undisclosed persistent session state that may contain prior inputs is not harmless and must be disabled or conservatively tracked.

### 8.2 Conservative propagation

Every opaque model invocation's outputs inherit all runtime-visible inputs: instructions, messages, retrieval, overview hubs, tool results, images and files, procedures, summaries and compaction, prior session state, and model-visible handle metadata. A segment's dependency set grows monotonically until a validated reset. A deterministic non-model transformation may limit the ancestry an output acquires only through a specified and tested contract; citations, schema validation and model judgments cannot.

Restrictions follow control dependence too: choosing a public URL, a branch, a result count or which handle to return based on private content discloses information without copying text. No complete timing or resource noninterference is claimed; semantic metadata leakage is forbidden, and residual timing and resource channels are assessed per profile (§14).

### 8.3 Segments, handles and reset

A handle binds tenant, permitted principal and segment, scope and purpose, exact value revision, type, expiry and dependencies. IDs are unguessable references, not bearer permission. Labels and origins stay in the trusted store unless their disclosure is permitted. Cross-principal passing, guessing, stale revisions, replay after expiry and post-barrier resolution fail ordinary checks.

Two transfer contracts are valid:

1. **Opaque fixed slot.** The trusted runtime allocates a handle slot of fixed type and shape before an untrusted reader runs. The planner sees no result-dependent value, status, count, label or identifier. This tested deterministic interface may keep hidden-value dependencies out of the planner; resolution at dispatch still imports them into the action.
2. **Result-dependent transfer.** Any returned metadata, chosen handle, success bit, variable count, text or unwrap imports full dependencies and restrictions into the planner. This is the default when independence is unproven.

A secret-reading segment cannot use a public success or error channel to avoid confidentiality. A reset starts from a trusted context-selection contract and retained eligible records; model-written summaries keep all old dependencies. If the selected records, objective, query or reset decision came from tainted context, those dependencies remain unless a tested deterministic boundary proves the narrower transfer. Reset also discards provider-side conversation state or carries its dependencies forward. A handle lives no longer than its backing object's eligibility and retention.

### 8.4 Checked dispatch and release

Before any provider submission, tool call, reply or export:

1. Resolve the registered contract and the effective effects, values, destinations and argument roles.
2. Include invocation, control and resolved-handle dependencies; check target and payload confidentiality, recipients' scope rights, purpose and processor eligibility.
3. Obtain current capability and task-intent decisions and apply §7.2, including current endorsements and confirmations.
4. Check fresh required judgments, corrections, barriers, revocations, lineage exclusions and external preconditions.
5. Commit a dispatch intent before any effect can escape, binding exact protected arguments, operation and version, caller, dependencies, policy and restriction epochs, nonce, expiry and an external idempotency key where supported.
6. At the final controlled boundary, revalidate and serialize release with barriers (§9.4); consume the release authorization once; use an external conditional-write precondition where available.
7. Append a completed, blocked, failed, cancelled or uncertain outcome with receipt and actual destination. A crash after sending and before receipt is uncertain, not failed.

An uncertain consequential action is never blindly retried: reconcile by external receipt or status, or by the same supported idempotency key; otherwise keep the uncertainty and require an explicit authorized recovery decision. There is no exactly-once claim across an uncontrolled external service.

Model invocations also require a committed input manifest before submission. Outputs are durably captured or withheld before release; a provider timeout can leave an uncertain submission and a separately accounted retry. Streaming uses checked bounded chunks; nothing already released can be retracted by a later barrier. The initial adapter buffers externally visible model output until dependencies and the release decision are recorded.

### 8.5 All egress counts

Replies, inter-agent traffic, tools, URL, query and header fields, logs, diagnostics, exports, embeddings, rerankers, adapter training jobs and model inputs are disclosures. This applies to UPMS processing workers in both profiles. Operational logging is content-free by default; adding payload logs creates a protected deletion surface. No worker or alternate transport may bypass processor restrictions.

### 8.6 Resource boundaries

Bound capture bytes, formats, nesting and decompression; relation fan-out and traversal work; search, time and token budgets; queue and storage growth; per-principal inference spend; maintenance and consolidation spend; adapter training; concurrent jobs. Capacity is reserved for restriction commits and deletion remediation. Unknown limits or exhausted validation budgets fail closed for the affected action; ordinary permitted recall may degrade with explicit coverage. Lineage and safety checks are never discarded to meet latency.

## 9. Commit, Freshness, Screening and Processing

**One fenced owner serializes canonical commits; freshness, barriers and screening are decided synchronously by the core; language processing runs as a cheap-to-expensive cascade that only proposes.**

### 9.1 One transition owner

One logical owner serializes canonical commits within the tenant, with fencing enforced by the storage boundary: a stale process cannot commit with a superseded fencing generation. A transaction validates authority (including scope rights), expected revisions, dependencies and barriers; appends records; advances relevant epochs; and schedules derived work through a transactional outbox. Outbox delivery is at least once; consumers deduplicate by operation identity and advance durable watermarks without skipping failed predecessors.

Ingestion identity is `(tenant, authenticated source_namespace, source_message_id, source_revision)`. Without a stable source ID, capture allocates a request ID before retry. Same identity with different bytes is a conflict, never a silent overwrite. All lifecycle operations share §4.3's idempotency. Transactions never span tenants; cross-scope reads within the tenant use one consistent snapshot plus current access checks.

### 9.2 Payload publication and capture

Identity, capture, never-store and resource policy are applied before retention. Protected payload bytes are written to non-serving storage and verified for durability and integrity before their canonical reference and outbox entry commit. Acknowledgement follows both payload and metadata durability. Object-store and database writes are not assumed atomic: abandoned staged objects have run-owned expiry and cleanup, and a missing committed payload causes explicit unavailability and repair, never invented data. Temporary files, uploads and rejected content are covered by cleanup policy.

No model runs on the synchronous capture path. Never-store detection has a declared scope: deterministic categories and authenticated channel policy, not a claim that all sensitive content is recognizable. A channel that cannot satisfy its capture policy is rejected or has retention disabled. Asynchronous indexing, extraction, screening and overview work use only eligible inputs and permitted processors.

### 9.3 Freshness without the insertion race

**Initial rule:** the core maintains a conservative evidence epoch per scope. Any committed source addition or revision, claim, statement, evidence relation, correction, relevant lifecycle change, entity-resolution change, vocabulary merge or ruleset assignment that can affect assessment advances the scope epoch in the same transaction. Unknown relevance invalidates the whole affected scope. Publishing a judgment, a flag or an overview, or completing a processing attempt, does not advance it. Correspondingly, pilot rulesets assess only source, claim, statement, evidence-relation and epoch-tracked control evidence (endorsements, corrections), never the current status of a judgment, flag, hub, narrative or projection. The core enforces this at `submit_assessment` by ancestry: an assessment whose recorded inputs include a judgment, flag, hub, narrative or projection, or a claim descended from one (a consolidation hypothesis, or an agent claim written after reading a hub), is kept as evidence-only and never admitted. Model-written claims are pointers to their cited sources, which the assessor reads directly. Judgment-on-judgment assessment requires a separately accepted current-head dependency contract. Cross-scope evidence captures every participating scope's epoch.

An assessment binds a snapshot, exact read revisions, assigned ruleset and scope epochs. Admission requires unchanged revisions and epochs at commit; if evidence arrived between snapshot and commit, the assessment is kept as historical or evidence-only and reassessment is queued. Unprocessed new evidence also invalidates: pending extraction cannot hide an opposition window. Basic recall never waits for deep processing.

At every current-state presentation or protected reliance, the effective judgment must still match current scope epochs, rule assignment, validity interval and the maximum age bound, with no unresolved required processing or reassessment; otherwise it is shown as evidence-only with qualifications, or the dependent action is blocked. The epoch comparison is the safety condition; the reassessment queue is only liveness. Capture time is not freshness time.

Slot-level epochs (§9.7) may replace scope epochs **only after** an invalidation contract covers vocabulary merges, entity-match changes, rule changes and the candidate channel, and race scenarios T01 and T19 pass at slot level. Until then, scope epochs remain the safety condition; their availability cost is measured first. Timeouts and unknown scopes make an assessment stale, never fresh. External current-state claims also need source-owner refresh or preconditions.

### 9.4 Barriers and the release race

The core owns restriction epochs and orders restriction commits with final controlled releases; a check followed later by an uncoordinated socket or file write is insufficient. **Restriction commits** include corrections, deletions, permission narrowing, group-membership removal, ownership or oversight transfer, narrowing of an overseer's rights and the end of an elevation.

For each, the target restriction is published and the affected epoch advanced synchronously. Cached eligibility is invalid immediately; derived descendants (statements, flags, hub lines, adapters) are rejected through validated requirement closure even before purge or index jobs run. A bounded closure failure contains the affected scope. No new ordinary descendant of a deletion-blocked input may commit; restricted cleanup and audit transitions remain possible without re-serving content.

Release and barrier activation use a core-coordinated gate: a release either crosses the controlled boundary before the barrier, or revalidates after it and is rejected if affected. Remote egress processes participate in the fence; an offline cached permit is insufficient. Before acknowledging `serving_blocked`, an applied correction or a revocation, all older release rights must have completed, been cancelled or been conclusively fenced. A stuck participant causes a deadline failure; the request stays pending and is never falsely acknowledged. No lock waits on an uncontrolled recipient's receipt.

The guarantee concerns **future releases from controlled surfaces**, not bytes already sent, human knowledge, or external actions already dispatched; those are reported as prior or uncertain exposure. An old-context invocation's pending output is withheld and, if needed, regenerated from a new eligible context. External policy revocation is enforced within its declared propagation bound; strict post-acknowledgement revocation requires the policy integration to join this fence. Pilot consequential decisions are online, single-use and fail closed on uncertainty.

### 9.5 Read-your-writes and bounded work

Targeted reads and acknowledged corrections use canonical state immediately. Search overlays post-index commits through a bounded scan; if it cannot cover the gap, it returns explicit partial coverage and a continuation token, never a claim of completeness or absence. Barriers always apply, even when the index is unavailable. Queries may request a minimum commit position and receive that consistency or an explicit unable-to-satisfy result.

Lazy processing responds to explicit requests, obligations, retrieval need, consequential reliance and a bounded age-weighted background sweep, so rarely retrieved obligations are not starved. Queue saturation stops new nonessential work, preserves capture within quota and reports deferred processing. Deletion and barrier work has priority over extraction, screening, consolidation and training.

### 9.6 Replay and compatibility

| Contract | Promise | Limit |
| --- | --- | --- |
| Canonical replay | Rebuild surviving states from retained records, recorded outputs and versioned reducers, vocabularies and screening rules | No model calls, external queries, actions or erased bytes |
| Historical input reconstruction | Exact submitted runtime-visible sequence while every required byte and revision is retained | Deletion, expiry and unknown provider internals are explicit gaps |
| Retrieval rebuild | Rebuild eligible content, hubs and adapter-based indexes to qualified criteria | Approximate index bytes, order and narrative wording need not match |

Each durable schema has an explicit READ, MIGRATE or REJECT compatibility rule; unsupported versions never fall through to permissive defaults. Migrations preserve IDs, labels, permissions, controls, history and deletion restrictions, with staged validation, atomic publication and interruption recovery. Rollback cannot roll back barriers or resurrect erased content. Caches, indexes, hubs and adapters may be discarded and rebuilt; canonical data is never reinterpreted to fit a cache. A new model, tokenizer, embedding model or vocabulary version creates new processing or projection versions.

### 9.7 Deterministic screening

**Deterministic code compares structured statements and raises conflict flags with reconciliation cues; an LLM or human investigates; screening never resolves anything.** Given recorded extractions, a vocabulary version and a rule set, screening produces the same flags on replay. **Fixed (proposed).**

**Slot conflicts.** Statements are indexed by slot: (entity or `same_as` cluster, property). A pair in one slot is flagged when (1) the subjects are the same entity or a `same_as` candidate; (2) the property is single-valued; (3) valid time and place overlap or are unknown; (4) the values are incompatible under the property schema; and (5) polarity and modality are comparable — both asserted, or a negation against an assertion; a quotation is not compared with an assertion. Compatible values (refinements, or different dimensions such as hue and lightness) never raise a conflict flag; they may produce an informational comparison cue, which is not a flag. Event statements are compared likewise when their type declares that two events cannot coexist.

**Rule matching.** Every intended, committed or recorded event is matched against active rules in its scope (§5.7.3), including through `broader` relations: a release matches a rule about deploys if release is narrower than deploy. Only prohibitions are screened in the pilot, using one table: an event whose qualifiers all match the prohibition's pattern and validity interval gives a definite flag; one with a needed qualifier unknown gives a possible flag; a mismatch, a negated event (“we did not deploy on Friday”) or a quoted or hypothesized event gives none. A flag is suppressed only by an approval record (§5.4) whose scope, rule and action match; its role evidence was recorded at commit, so replay reads that evidence, never the identity provider's current state. Any other claim of approval, including a statement attributed to the role holder, leaves the flag and adds the cue `unverified_exception`.

```text
Flag {
  statements[] | (statement, rule), severity  // definite | possible | adjacent
  cues[]:  missing_qualifier(time | place) | entity_match_uncertain
           | value_adjacent
           | modality_or_attribution_differs | recent_vocabulary_merge | cross_language_mapping
           | missing_exception_evidence | unverified_exception | source_class_differs
  screening_version, vocabulary_version, inputs_watermark
}
```

Severity is ordinal and rule-based, not a probability: definite when every condition holds with all qualifiers known; possible when a qualifier or entity match is unknown; adjacent when values are close in the value space. Cues tell the investigator where to look. Two “sky” statements, blue and green, with overlapping times and no place raise a possible flag with `missing_qualifier(place)` and `entity_match_uncertain`; blue against dark raises no flag, only an informational `different_dimension` comparison cue.

**Comparison cues** are recorded as `ComparisonCue {statements[], kind, screening_version, vocabulary_versions}` processing outputs, separate from flags, replay-deterministic, and visible only to principals who can read both statements. A value concept narrower than two dimensions (“dark green” against “blue”) is compared on each dimension it declares and is incompatible if any declared dimension is. Comparisons across scopes, or between a published copy and its target scope, use each statement's own recorded vocabulary version, mapped through merges both readers can see. Flags and cues are never required processing under §9.3.

**Candidate channel.** Slot comparison is high-precision and low-recall. A probabilistic channel proposes cross-slot candidates using embedding similarity and a small contradiction model (§9.8); its outputs are recorded processing records shown as candidate flags, separate from deterministic flags.

**Resolution and visibility.** Screening never resolves, refutes, supersedes or admits a claim, and the absence of a flag never certifies support, fidelity or currency. Every flag goes to investigation, whose result is a Judgment (§5.3, §6.2). A flag is visible only to principals who can read both flagged items. Text-only statements are not slot-screened, and coverage says so. Required actions are not screened in the pilot, so an unfulfilled obligation is reported as unscreened coverage, never as “no flag”. Reversing a vocabulary merge restores the prior comparisons and retires flags that depended on the merge.

### 9.8 Processing cascade and adaptive models

**Language processing runs deterministic code first, small local models second and the LLM last, only where needed.** Small models may be adapted to a scope's jargon through adapters held as derived, deletable, permission-bound indexes. Domain adaptation is in scope by owner decision D-11.

| Tier | Runs | Jobs |
| --- | --- | --- |
| 1. Deterministic | Rule-based NLP and normalizers | Base word forms, dates and times, units, exact vocabulary lookup, schema validation |
| 2. Small local models | Multilingual sentence-embedding model, entity tagger, small classifiers, small contradiction model | Retrieval embeddings; candidate concepts for unknown terms; entity mentions; sentence routing (fact, rule, rationale, chit-chat); negation and hedging; cross-slot candidates; significance proposals for overview updates |
| 3. LLM | Extraction, investigation and consolidation model | Full structured extraction; ambiguity resolution; flag investigation; overlay notes and consolidation |

**Fixed (proposed):**

- Lower tiers propose and route; outputs are processing records with model version and inputs. They may add restrictions and never grant anything.
- A router's decision to skip extraction never drops text; the item is reported as not structured.
- Tier 2 runs locally by default, so restricted memory need not reach an external processor.
- A tier-2 score that gates a consequential outcome without tier-3 or human confirmation needs measured error rates first (a D2 reopen trigger, §1.4).
- Tier 2 starts with embeddings and one contradiction model; other classifiers are added only when evaluation shows the LLM extractor is too slow, costly or inconsistent.

**Two adaptation tiers.** Tier A is vocabulary expansion (§5.8): immediate, deterministic, no training. Tier B is per-scope low-rank adapters (LoRA or similar) on a fixed base model, for domain sense expansion cannot capture; it ships only if it beats tier A on the scope's probe set.

**Adapters as derived indexes.** An adapter is versioned, records its training snapshot, and has ancestry edges, and so requirements, on every record it was trained on. **Fixed (proposed):**

- **Per scope.** An adapter is a lossy compressed copy of its training text; only principals with `r` on every scope in its requirement closure may use it, and a scope's adapter trains only on records whose closure lies within that scope. Cross-scope search queries each scope's index with its own adapter and merges ranked lists, never raw scores.
- **Training data** comes only from the curated vocabulary (aliases as positives, related-but-different concepts as hard negatives), user corrections and endorsements, and validated or confirmed extractions. Excluded: anything whose ancestry includes X-class content, or R-class content without a factual attestation or permitted-reliance endorsement (§6.4; a fidelity confirmation is not enough); unconfirmed model output; retrieval feedback; quarantined items; other scopes. This keeps known external lineage out of training. It cannot stop a misled curator from approving a planted term, which is why curation is attributed and reversible.
- **Retrain from scratch on trigger:** a change to a vocabulary concept in the adapter's training set, a threshold of newly approved aliases for concepts in its training set, a probe-accuracy drop, or a training-source deletion. Global consolidation (§10.5) retrains only adapters whose training inputs changed. Training uses pinned seed and versions.
- **Promotion gate.** Promote only if the adapter beats both the current adapter and the base model on the scope's probe set and a general regression set, with no regression beyond the preregistered margin; variants tried are recorded (§15.2).
- **Re-embedding.** Adaptation is query-side only in the pilot: document vectors come from the base embedding model and carry no adapter ancestry, so deleting an adapter's training source never blocks the vector index. Document-side adaptation needs its own dependency contract and a base-vector fallback index.
- **Deletion.** Deleting a training source blocks every adapter trained on it at the barrier. Serving falls back to the newest adapter whose snapshot predates the deleted record, or the base model, and a retrain from surviving data is queued (§14.2). Retention expiry is planned instead: training takes only inputs at least the adapter's planned lifetime from their deadline, the adapter records its own deadline, and it is retrained before that deadline, so routine expiry never forces a fallback.
- **Evolving jargon.** Deprecated terms stay in training data as aliases of their replacements, so old memories remain understandable; only extraction output prefers current terms.

## 10. Retrieval, Context, Overview and Team Memory

**Eligibility is decided before ranking; a blank model orients from a small per-reader map; team visibility is designed for coordination as well as security.**

### 10.1 Eligibility before ranking and release

Tenant, principal, effective rights (`r` for content, `l` for existence), purpose, scope, quarantine, correction intent, deletion and the task's lineage exclusions constrain candidates before payloads reach a ranker, reranker, snippet generator or external processor. Shared approximate structures may be internal to the TCB only if ineligible content cannot affect exposed snippets, counts or explanations or unauthorized model inputs. Partition and filter strategy is D4 and must be qualified; post-filtering an untrusted reranker's input is too late.

Final return passes the release gate. Cache identity includes principal and rights context, purpose, scope, restriction epochs, snapshot, query and intent, and model, vocabulary and render versions; cache hits still recheck current eligibility. Pagination and continuation tokens are scoped, protected, time-bounded and revalidated. Unknown and denied objects get an indistinguishable unauthorized response unless the requester holds `l`. Timing and resource side channels are measured separately; no constant-time claim is made.

### 10.2 Intent routes

| Intent | Route and qualification |
| --- | --- |
| Orientation | Reader's L0 hub, then L1 and L2 hubs by route (§10.5) |
| Historical recall | Accessible sources and claims with attribution, valid and transaction time, correction and retention status |
| Current state | Source application where available; otherwise fresh admitted projections and slot tables, with conflicts and applicability |
| Explanation or verification | Authorized evidence and judgments, including opposition, flags and assessed-as-of position |
| Task continuation | Checkpoint plus changes since its watermark; confirmed completion distinct from intention or uncertainty |
| Association | Optional bounded relation expansion with path provenance and relation status |
| Prior discussion | Scoped search with explicit coverage; “not found here” is not global absence |

Absence is assertable only for a deterministic predicate over a fully enumerated authorized corpus. Ranking starts with lexical retrieval, vocabulary-expanded queries, optional qualified vector retrieval, time and task scope, explicit priority, freshness and open obligations, with duplicate reduction. Graph sophistication needs measured incremental value.

### 10.3 Response contract

```text
MemoryResult {
  query_id, intent, effective_scope, authenticated_purpose, time_constraints
  snapshot_position, index_watermarks, projection_versions, restriction_epoch
  vocabulary_version, lineage_exclusions_applied
  items: [{revision_ref, selected_span, source_refs, judgment_refs,
           statement_refs, flag_refs, source_classes, attribution,
           freshness, qualifications, confidentiality_tags,
           correction_or_retention_status}]
  coverage: {capture_extent, indexed_extent, processing_extent,
             structured_extent, screened_extent, retained_extent,
             unavailability, truncation, timeout}
  authorized_conflict_or_pending_correction_refs
  budget: {requested_tokens, selected_tokens, omissions}
  continuation_token?
}
```

All metadata is access-controlled: coverage, flags and conflict references are filtered by `l`. Client-visible snapshot, watermark and epoch fields are opaque, caller- and scope-bound consistency tokens, not raw tenant-wide counters. Without `l`, even “restricted supporting material exists” is not shown; the response says current support or coverage is insufficient without implying a hidden object. Retention, processing and screening gaps are never converted into “none found.”

### 10.4 Context assembly

Assembly uses the actual model tokenizer and input limit and accounts for non-text and tool-schema costs. Mandatory runtime instructions, the current request, tool definitions and output allowance are reserved first; the L0 hub and task checkpoint fill the checkpoint share; retrieval fills the rest. If mandatory content exceeds capacity, assembly returns explicit overflow and requires a supported replan, never silently dropping authority or security constraints. Lineage exclusions are applied here. Tokens in MemoryResult refer to the selected rendering.

Retrieved content is attributed data, never activated instructions. Retrieval at session start and on light user turns is bounded; deep retrieval needs its capability and budget. Runtime-private instructions an integration cannot observe are a manifest coverage limitation. Before consequential use, source state and permission are refreshed under §8.4.

### 10.5 Overview layer

**A model with no context starts from a small map of the memory, current at read or marked stale, never from the archive.** The overview layer is a derived hierarchy of hubs acting as summary, index and router: a blank model reads its root hub first and descends only where its task leads. It follows the arrangement described by hippocampal indexing theory — a compact index over a large archive, with understanding consolidated over time rather than rebuilt at every recall. **Fixed (proposed).**

```text
Blank model                                                  Commits flow up:
reads down   L0  Root hub per reader (≤ 1,500 tokens)          ▲  exact lines current
    │            active work, recorded decisions, obligations  │  at read; narrative
    │        L1  Area hubs, one per scope or project           │  (synthesis) waits
    │            recorded state, decisions with status         │  for consolidation
    │        L2  Entity and topic pages, from Slice 2          │
    │            slot tables with status, timelines, sources   │
    ▼        Archive: events (original text), claims and statements,
                      judgments, controls (including coordination records)
L0 is assembled per reader from hubs of scopes they may read.
```
*Figure: Reads go down the map; updates flow up it.*

A blank model reads down from L0 and pulls sources only when needed. Exact projections and change entries are current at read, or explicitly marked stale and partial; the narrative and overlay notes are labeled synthesis, and the narrative is rewritten only by consolidation.

#### 10.5.1 Levels

| Level | Contents | Budget | Built per |
| --- | --- | --- | --- |
| L0 root hub | What this memory serves; active work; recorded decisions and obligations with status and author; open conflicts and blockers; significant recent changes; routes to areas; glossary pointer (§5.8); coverage and as-of | ≤ 1,500 tokens (initial default) | Reader, assembled at read time |
| L1 area hubs | Recorded state and decisions with status, open questions, routes to L2; from Slice 2, recorded rules with structure status and authority reference, key entities and timeline highlights | ≤ 3,000 tokens each; sub-hubs when an area exceeds the replay cap | One per area (a scope or project) |
| L2 entity and topic pages | From Slice 2: slot table per property with qualifiers and status (§5.7); event timeline; open flags (§9.7); links to sources | Bounded per page | Scope |
| Task checkpoints | Objective, confirmed work with evidence, decisions, open questions, obligations, blockers, artifacts, next steps | Checkpoint share | Task or session |
| Archive | Events, claims and statements, judgments, controls (including coordination records) | — | — |

**What hubs contain in Slice 1a.** Hubs project only explicit records: coordination records (§5.4: decision, commitment, blocker, ownership claim, interface agreement), entered by their authors through `record_coordination` and never extracted; task checkpoints; corrections, deletions, permissions and publications; and recent events with attribution. Recent events from R- or X-class sources appear in L0 only as locators (time, source, author), never as quoted text; coordination values and checkpoint text are rendered as attributed data with their author and source class. A reader or task with no checkpoint sees an overlay of the last 7 days, with a count of earlier changes. Coordination records show as “recorded”, with status and author, never as “in force”; same-key conflicts (§6.9) appear as attributed conflicts. With no consolidation yet, the 1a overlay is measured from the reader's or task's last checkpoint. Nothing unprocessed is presented as known. Slot tables, rules and other statement-based content arrive with Slice 2.

**Slot tables show status, not winners.** An L2 slot shows a current value only when a fresh admitted judgment supports it (§9.3), and shows what was admitted: when the ruleset admits only an attributed statement (§7.6), the slot reads “stated by ⟨author⟩”. Otherwise it lists the attributed statements, conflicting statements and unjudged claims for that slot, each with its status. Deterministic selection never turns a statement into a current fact.

#### 10.5.2 Hub content

Each hub has three parts:

- **Exact projections**, computed deterministically from canonical records: coordination records, checkpoints and controls, and from Slice 2 statements and judgments. They faithfully show recorded state and status, including attribution, conflicts and what is unprocessed, and are current at read or explicitly marked stale and partial (10.5.3). Together with the overlay's change entries, they are the only part of a hub whose correctness the manual promises.
- **Consolidated narrative**, written by an LLM during consolidation: the understanding, the “why” and the shape of the work. It is **model-written synthesis, presented as such**: labeled with its consolidation watermark and inputs, never shown as current fact, never evidence for admission. Each **narrative unit** is the output of one consolidation invocation, or of one independently generated section, depends on every input of that invocation (§8.2), and records its own deadline, the earliest retention deadline among those inputs. Sentence citations help readers trace claims; they are not dependency proofs.
- **Overlay**, a derived and rebuildable projection of canonical commits since the consolidation watermark (in Slice 1a, since the reader's last checkpoint), complete and pageable. It holds two kinds of entry: **change entries**, generated deterministically from each commit and covered by the correctness promise; and **notes**, short model-written summaries labeled as synthesis with their source class and author, each a narrative unit for withholding. A completion or result claimed in a note renders as “claimed by ⟨author⟩” unless linked to a receipt. A hub renders as much of the overlay as its budget allows, then states how many more changes exist and offers continuation; it never implies the inline part is complete. Counts exclude items the reader cannot list or that the task's lineage exclusions remove.

#### 10.5.3 Synchronization and consolidation

**Exact projections are current at read or explicitly marked stale; the narrative becomes coherent through consolidation and is always labeled as synthesis.** Fast updates never edit the narrative piecemeal, because many local edits fragment it; they accumulate in the overlay, and consolidation — a regional replay that rewrites a region's narrative as one coherent piece — absorbs them. This mirrors the complementary roles of fast and slow memory, with consolidation as the sleep phase.

**Current at read.** Projections are maintained through the outbox, which can lag. A hub read therefore applies the same deterministic projection function to every canonical commit beyond the hub's projection watermark, so superseded, fulfilled, released, withdrawn or corrected lines change exactly as they would once the outbox catches up. Catch-up for one read, including an L0 assembly across many scopes, is bounded by the read-time scan budget (§14.2). If the budget cannot cover the gap, every affected line, or the whole hub when the affected lines cannot be identified, is returned marked stale and partial, never with a current consistency token.

| Mode | When | What it does | LLM? |
| --- | --- | --- | --- |
| Projection | Every commit through the outbox, and for the gap at read time | Recomputes exact lines; appends a change entry to the overlay; withholds every narrative unit or note whose inputs include a corrected, deleted, expired or newly unreadable source | No |
| Overlay note | When a significant change reaches a hub about to be read, or at the end of a task | Adds a short source-linked note, labeled synthesis; never edits the narrative | Optional, bounded |
| Regional consolidation | Before the region's earliest narrative deadline (first priority); otherwise when its fragmentation crosses its threshold and budget remains; at idle time | Replays the region's L2 pages and the sources selected under the deadline rule, within the replay cap; rewrites its narrative units; absorbs the overlay | Yes, batched |
| Global consolidation | Weekly, only when at least one region changed and the estimated work fits the budget; otherwise deferred | Rewrites each scope's L0 section from that scope's consolidated L1, one invocation per scope; schedules retraining only of adapters whose training inputs changed. Cross-area analysis is a separately budgeted optional step, with outputs homed where every reader can read all their inputs | Yes, batched |

- **Overlay, not edits.** Between consolidations the narrative does not change; readers see it with its watermark, followed by the overlay. The narrative stays coherent and the overlay stays honest about what is new.
- **Fragmentation drives consolidation, not only the clock.** Each hub tracks overlay size, withheld narrative units, age, and contradiction flags between its narrative and its exact projections, found by screening statements extracted from the narrative (§9.7). Crossing a threshold schedules regional consolidation when the estimated work fits the budget.
- **Deadline-aware replay.** Retention expiry is scheduled, unlike deletion, so consolidation plans for it. Every narrative input, including L2 lines and statements, is read through a deadline-filtered view that keeps only material whose effective retention deadline is at least the planned narrative lifetime away (§14.2). Older material is not narrated; it stays reachable through exact projections and retrieval while retained. A region with no eligible material says its narrative is empty. Each unit records its deadline, and the region is re-consolidated before that deadline. Expiry therefore retires material on a schedule instead of withholding narratives by surprise. Because every narrated region must be re-consolidated within each lifetime, demand grows with the volume narrated, so the budget fixes coverage: deadline passes come first, ordered by retrieval demand and explicit priority; fragmentation passes use only what remains; regions that do not fit are projection-only and labeled so.
- **Full replay, interleaved.** Within that window, consolidation re-reads old and new material together, not only the delta; replaying only the new would overweight recent events.
- **Bottom-up order.** Regions consolidate from L2 to L1; global passes then rewrite each scope's L0 section from its consolidated L1, so upper levels are never rebuilt from stale lower ones.
- **Significance.** Decisions, rule changes, obligations, commitments, conflicts and flags, corrections, deletions and publications always propagate upward; routine items stay at L2 (in Slice 1a, in the overlay) unless retrieval demand or explicit priority raises them. A small classifier may propose significance; deterministic rules decide.
- **Understanding as an output.** Consolidation also proposes what deserves to be learned: recurring patterns, lessons from dead ends, cross-area dependencies, emerging rules, vocabulary changes. Each is a `hypothesized` claim attributed to the consolidation run, linked to its supporting instances, and evidence-only until judged or endorsed. Such claims are pointers, never support: an assessment must read the cited sources directly (§9.3).
- **Guarding against consolidation errors.** Consolidation compresses and reorganizes, and human sleep shows the risk: gist strengthens while schema-consistent false memories appear. So the archive stays verbatim; generalizations are labeled hypotheses; citations must resolve to sources readable by the narrative's readers; a new narrative replaces the old one only if screening finds no contradiction with exact projections; and the diff from the previous consolidation is recorded. **Passing these checks does not certify that the narrative is supported or faithful** — an unsupported causal link outside any slot can pass them — which is why the narrative is always labeled synthesis.
- **Deletion, revocation and expiry.** When an input of a narrative unit or note is deleted, corrected or expires, the whole unit is withheld; when an input becomes unreadable to a reader, the unit is withheld from that reader. The hub then falls back to exact projections and the overlay until the region is re-consolidated from surviving inputs. Hubs that need finer granularity generate sections in separate invocations with disjoint inputs.
- **Stability.** Structure and wording are kept where facts have not changed, by aligning the new narrative with the previous one after generation; the previous narrative is never an input to its replacement. Churn is measured.
- **Fast and slow learning.** The archive and overlays play the fast, episodic role; consolidated hubs and per-scope adapters play the slow role.
- **Piggybacking.** At the end of a task, the working agent's checkpoint becomes overlay notes for its area at little extra cost, labeled as synthesis; consolidation checks them against sources.

#### 10.5.4 Maintenance cost

**Maintenance work is bounded per pass and has its own budget, so it never competes with the work it supports.** Work per pass is capped and total work is capped by the budget; what grows with the archive is the share of it left projection-only (10.5.3). It is not independent of archive size: global passes read every scope's L1 hubs.

- Projection is database work and overlay notes are small; consolidation is the main LLM cost.
- **Regions.** A region is one scope's area; a project spanning scopes has one region per scope. When a region's deadline-filtered input exceeds the replay cap, consolidation divides it into sub-regions with their own L1 sub-hubs, by entity and then by time window; divisions are recomputed only at consolidation, and regions never merge across scopes.
- **Replay cap.** A regional pass reads at most the replay cap of input tokens, L2 pages and sources together (§14.2), whatever the archive's size.
- **Global passes** read one scope's consolidated L1 hubs per invocation, capped at the replay cap; a scope whose L1 hubs exceed it is rolled up hierarchically, sub-hubs into their L1 hub first. The number of L1 hubs grows with archive size divided by the cap. Global passes are budget-gated like regional passes.
- **Benefit-conditioned.** Consolidation runs when a deadline approaches or fragmentation crosses its threshold, and the estimated work fits the budget; otherwise it is deferred and the hub stays labeled stale with its overlay.
- **No per-reader LLM cost.** L0 is composed per reader deterministically from per-scope sections, so the LLM writes each scope's section once, not once per reader.
- **Cheapest adequate model per job:** deterministic code for projections, small models for significance, a smaller LLM for overlay notes, the strongest model at batch rates for consolidation.
- **Budget.** Maintenance has its own quota below task work: the larger of a share of recent task-model tokens, where the integration profile can measure them, and a fixed bootstrap budget, never above a daily cap (§14.2). Unused budget accrues up to a bounded reserve, so one capped regional pass always fits in the consolidation share. At least half is reserved for consolidation. Correction, deletion and permission invalidation is deterministic and never budget-limited.
- **Planning estimate (Unverified).** With the pilot defaults, the bootstrap consolidation share of 50,000 tokens a day sustains about 20 capped regional passes per 30-day lifetime, after outputs and weekly global passes, so about 1.2 million tokens of narrated material; the rest of a large archive is projection-only. T54 measures the narrated fraction and availability by simulation at the corpus envelope.
- **Graceful exhaustion.** When the budget is spent, the narrative ages and the overlay grows, both labeled. Coherence and freshness degrade; exact projections and invalidation do not.
- **Measured:** maintenance-to-work cost ratio, replayed input tokens per pass (L2 and sources), deferred work, narrative availability per region, overlay size and withheld units at read time, narrative-versus-projection contradictions, churn, and cold-start success (§15.2).

#### 10.5.5 Per-reader assembly, trust and routing

Hubs are built per scope. L0 is assembled at read time by deterministic composition of the per-scope hub sections the reader can read; no stored hub mixes scopes unless every reader could read all its sources. Task lineage exclusions apply at assembly. Areas the reader cannot list are not mentioned, not even as counts.

Hub content is derived: every line links to its sources and carries their source classes; no hub is authority or evidence for admission. A stale hub is history, not current state, and its expiry never fulfills an obligation. Each hub carries route entries (area, key concepts, pointers); the router matches a task's terms to routes using the vocabulary, entity registry and hub embeddings, descending one level at a time with a bounded budget per step. Direct search remains available; the map is a shortcut, not a gate.

**Continuity warning.** When a checkpoint or item under an explicit retention extension (§14.2) a user relies on has an input that expires sooner, task continuation and the retention inspection surfaces show the effective loss deadline, naming the input only if the user may see it. Hub narratives are excluded, because their deadlines are planned (10.5.3). Inputs are never retained beyond policy to avoid the warning.

### 10.6 Team memory and coordination

**In team work, what each worker can see shapes what it thinks, so visibility serves coordination as well as security.** Four mechanisms answer four questions, each used only for its own job. **Fixed (proposed)** for the mechanisms; team policies built on them are a Slice 3 experiment.

| Question | Mechanism | Lifetime |
| --- | --- | --- |
| May this principal ever see the item? | Scope permissions (§7.3) | Long-lived, per principal |
| Has the owner declared it fit for the team? | Publication (10.6.2) | One act per item |
| Should this task's context exclude it? | Lineage exclusion (10.6.4) | Per task, then lifted |
| Should it be put in front of the worker now? | Retrieval salience and the overview (§10.2, §10.5) | Per query |

Noise is a salience problem, not a permission problem: hiding a teammate's notes also hides the one note that matters. Blindness is a task-context problem: permissions are too long-lived and too leaky to provide it.

#### 10.6.1 Visibility tiers

1. **Private:** readable by the owner and, for agent principals, the overseer.
2. **Team-readable, pull-only:** teammates may search it deliberately; a scope flag excludes it from their proactive retrieval and overviews.
3. **Shared pool:** the team scope, proactively retrieved and summarized.

#### 10.6.2 Publication

`publish(item, target_scope)` copies private work into the shared pool:

- The publisher must own the item and hold `w` on the target scope.
- Publication commits a new attributed copy in the target scope, with an ancestry link to the original that is kept as long as the copy exists (§11.2).
- It waives a scope's access requirement **only for ancestors the publisher owns**: the waiver applies to a scope only when it is the publisher's own personal or private scope or the publisher holds manage rights on it, and every ancestor record from that scope in the item's ancestry closure is owned by the publisher or its owner has confirmed this exact publication (confirm\_publication). Revoking that confirmation restores the requirement and withholds the copy. Requirements from anything else (a confidential client document the publisher read, a teammate's records, a human's messages to an agent) stay attached and still restrict readers. This is the one exception to “no declassification in the pilot” (§7.4).
- **Deletion and retention (decision D-12):** deleting or redacting the publisher's private original does not delete the published copy; that deletion or redaction status lists the publisher's surviving copies and offers to withdraw them. For ancestors the publisher owns, a human's publication records a retention extension, and the copy follows the stricter of the target scope's and the category's retention; an agent's self-publication never extends retention. Deletion, correction or retention expiry of any other ancestor still propagates to the copy. A request to erase everything about a subject finds published copies through ancestry, which is kept for that purpose (§11.2).
- Source classes and provenance survive; a published item derived from external content says so. An ancestry endpoint in a scope the reader cannot list is shown only as “private source”.
- Published items are evidence-only for the team unless a human endorses them.
- Withdrawal is a retraction (§6.8); readers who already saw the item are not “unseen.”
- **Agents publish only what they own (decision D-8).** An agent principal may publish, without per-item confirmation, an item whose waivable ancestry it owns entirely; this self-publication is a pre-authorized C4 class (§7.2). Anything derived from records owned by a human, including that human's messages to the agent, keeps that human's requirement unless that human confirms this exact publication (C4); an ancestor owned by another agent needs that agent's overseer, and one owned by a departed user needs the scope's manage-rights holder. An X-influenced item keeps C3's exact-payload confirmation. In the memory-service profile UPMS cannot see what an agent read before writing, so this rule binds only ancestry UPMS recorded; the full rule needs the instrumented runtime (Slice 1b). Until then, in Slice 1a-team, the overseer confirms each agent publication and each agent coordination record in a shared scope (decision D-17). A human may delegate publication of their own records to an agent only under §7.2's per-action C4 confirmation.

#### 10.6.3 Publication categories

Agents tend to share successes and keep failures, building survivorship bias into shared memory, so some categories are required (*decision D-8, for items the agent owns*):

| Category | Default |
| --- | --- |
| Ownership claims, decisions, interface agreements, commitments, blockers | Recorded immediately as coordination records in the shared scope |
| Findings and results | Published when stable, at a checkpoint |
| Dead ends and failed attempts | Required publication at the next checkpoint |
| Scratch reasoning, hypotheses in progress | Private or team-readable pull-only |

Decisions made in a temporary coordination channel are captured as coordination records (§5.4) in the shared pool by the participant who made them. Required categories apply only to items whose waivable ancestry (the ancestors in scopes whose requirement publication would waive) the agent owns entirely; an item derived from a human's records is queued for that human's confirmation at the next checkpoint instead. The queue shows each candidate to the human whose records it derives from, released for confirmation only and only if that human can read all its other ancestors; otherwise it cannot be confirmed. An agent's coordination records in a shared scope pass the same test as its publications.

#### 10.6.4 Lineage exclusion and blind work

A task may declare lineage exclusions, such as “nothing derived from the author's implementation segment.” Context assembly, overview assembly, query expansion and adapter selection enforce them through ancestry, never through the access-requirement closure alone, whatever scope an item lives in: a published copy of the author's rationale, a hub or narrative built from it, a vocabulary definition derived from it, and an adapter trained on it are all excluded. A task under exclusion uses vocabulary and adapters free of the excluded lineage, or the base model. Traversal that reaches a stripped or erased node treats the item as excluded. Only principals with list rights on the named sources, or the task's coordinator role, may declare an exclusion, and omissions it causes are reported to the declarer exactly as ineligibility is. A **blind phase** has an explicit end, after which exclusions lift so workers can reconcile. Its manifests support an **independence attestation**: no input derived from the excluded lineage, within instrumented coverage. The attestation excludes rationale carried inside the artifact (code comments, commit messages) and channels outside UPMS, and says so.

Useful for independent review and falsification, parallel exploration that should not converge early, independent estimates or replications, held-out evaluation hygiene, and red-team versus blue-team work. In each, what is excluded is another worker's conclusions and reasoning, not the governing requirements.

#### 10.6.5 Shared-pool concurrency and oversight

Shared items are appended and attributed, never overwritten. Superseding names the revision being replaced; if it changed first, the attempt is recorded as a conflict. Conflicting findings stay side by side until resolved, and screening (§9.7) flags them. Overlays and checkpoint reconciliation report when an item a worker relied on was superseded.

An agent principal's private memory is private from peers, never from its overseer (decision D-9). Because an agent's reach never exceeds its overseer's and the overseer holds the oversight entitlement (§7.3.4), the overseer can read everything the agent can, except content whose restriction tags exclude the overseer as a recipient. The overseer grant on the agent's scopes is protected: neither the agent nor a scope manager can remove it, and only an administrator can transfer oversight, as a restriction commit (§7.3.7). Agents keeping memory their operators cannot inspect is an oversight problem, not a coordination feature.

#### 10.6.6 Experiment gate

Slice 3 runs the same team task under three policies — everything shared, everything private, publication-based — measuring duplicated work, contradictions acted on, time for one worker to discover another's finding, and defects caught in blind versus non-blind review. A policy ships only with a preregistered improvement under §15.2.

## 11. Accountability and Inspection Records

**The instrumented runtime seals what every invocation saw before dispatch, keeps lineage while survivors need it, and can trace a compromised source forward to what it may have influenced.**

### 11.1 Invocation records

```text
InvocationManifest {
  invocation_id, segment_id, principal, tenant, runtime_version
  provider_account_endpoint, model_identifier, configuration_ref
  ordered_inputs: [{immutable_revision_ref, span_or_transform_ref,
                    role, rendered_fragment_ref, source_classes,
                    confidentiality_tags}]
  handles_in_scope[], procedure_versions, tool_schema_versions
  compaction_template_tokenizer_versions, prior_provider_state_ref?
  overview_hub_versions, vocabulary_version, adapter_versions
  lineage_exclusions_in_force, elevation_ref?
  policy_decision_refs, snapshot_position
  aggregate_classes_and_tags, input_coverage, committed_at
}

InvocationOutcome {
  invocation_id, output_refs, proposed_action_refs, dispatch_refs
  provider_receipt?, status, completed_at?
}
```

The manifest covers exactly what is submitted, including middleware transformations, attachments and prior state within the claim boundary. It is committed before provider dispatch; outputs and outcomes follow. A transcript or post-hoc summary is not a pre-dispatch manifest. Hidden provider reasoning and pretraining are not promised. If instrumentation cannot observe some runtime-generated prompts or compaction, the full instrumented profile stays unqualified. Manifests are the evidence for independence attestations (§10.6.4).

### 11.2 Retention and reconstruction

The operational record splits into a protected reference skeleton and protected rendered fragments. The skeleton holds opaque links, classes, tags, policy and dispatch references and outcomes, never free-form payload text; opaque links remain sensitive metadata with a retention policy.

Exact reconstruction requires **all** referenced original revisions, rendered fragments, media bytes and transform or template versions, not just newly generated fragments. The effective reconstruction deadline is the earliest among them. A reconstruction window may pin copies only within applicable retention permission; deletion and access revocation override it. If policy forbids keeping a required item, the shorter effective window is recorded at capture.

**Representation expiry differs from semantic-object expiry.** A replay-only duplicate of a retained canonical input, or a rendering fully accounted for by a recorded deterministic transform and retained inputs, may expire without deleting the source or its semantic descendants; exact replay is lost, restrictive lineage is not. Novel prompt, compaction, overview or model-generated content is itself a canonical protected input with its own retention, compatible with its descendants. Expiry or deletion of a canonical input invokes deletion and descendant invalidation, and no content-bearing input may be relabeled a temporary representation to evade that. This keeps a seven-day replay window from imposing seven-day retention on all otherwise lawful memories.

The minimum restrictive lineage is kept while surviving objects require it; removing links for space never makes a live descendant independent. Ancestry is kept while any descendant survives, including a published copy that is not a deletion descendant: a purged node keeps its opaque ancestry edges, segment membership and subject-discovery entries, as a disclosed retained exception, until no descendant remains. Only then are sensitive source links and labels stripped from audit skeletons, keeping only permitted minimal receipts. Traversal that reaches a stripped node fails closed: lineage exclusion treats the item as excluded, and subject discovery reports the coverage gap. Recall coverage ends with retained lineage.

### 11.3 Incident recall

Given a source, credential, procedure, processor, ruleset, vocabulary version or adapter identity, recall traverses ancestry, including across publications and redaction copies, and, separately, evidential dependence. It returns authorized affected records, manifests, outputs, dispatches, outcomes, procedures, hubs and adapters; distinguishes possible influence from causal proof; and lists processing, instrumentation and retention gaps, uncertain effects and destinations outside local control. No report grants permission to expose another scope's records (recall output is filtered by the investigator's rights) or to undo an external action. Recall can schedule authorized reassessment, quarantine, re-consolidation or adapter retraining through normal interfaces.

### 11.4 Access records

Elevations, and every content access or change during them, produce access records: principal, elevation reference, operation, opaque target identity, time and outcome, with no content. An access record is durably committed to the replicated control plane (§12.4) before the content is released; if the commit fails, the content is not released. Owners of personal scopes can see access records for their scopes and receive a notice for elevated reads (decision D-1); a failed notice is recorded and shown.

**Protected audit retention (decision D-13).** Access records have their own retention binding, separate from scope, category and tenant retention, with a minimum of one year. They are excluded from scope and category retention cuts, scope deletion or transfer, and descendant purge, and are disclosed as a retained exception in deletion status. The period can be lengthened; a reduction applies only to records created after it takes effect, so no administrator can shorten the retention of existing records, their own included. Restores re-apply this binding before serving.

## 12. Retention, Redaction, Deletion and Portability

**Deletion is a staged lifecycle: a durable serving barrier takes effect at acknowledgement, purge follows across every surface, and completion is reported only for what was actually satisfied.**

### 12.1 Deletion units, surfaces and rights

Default source unit: event revision; default derived unit: object revision. Unusually large or mixed-policy inputs are split into declared units at capture. Every content-bearing representation is covered: raw and normalized text, statements, embeddings, summaries, overview hubs (narratives, overlays, projections), adapters, prompts, fragments, handles, indexes, query and response caches, staging files, logs, journals and WAL, replicas, backups and managed exports. Restricting the original object alone is insufficient.

**Who may delete:** own items with `w`; others' items with `d`; administrators while elevated; retention policy. A deletion propagates along restrictive requirements to descendants, including in scopes the requester cannot see, without disclosing them; their owners see only “an input is unavailable.” A published copy is not a deletion descendant of its publisher's private original (§10.6.2), but remains one, including for retention expiry, for every ancestor the publisher does not own. Access records are excluded (§11.4).

Retention is versioned policy per tenant, scope and category with effective deadlines and a deletion plan. More restrictive applicable deadlines win. Reads never renew retention silently. Longer retention requires an authorized explicit change before expiry; nothing resurrects erased bytes. A retention change cannot silently purge an unexpectedly broad corpus: it shows scope, counts the actor may see, affected continuity and effective date, then applies the authorized transition, with a cancellable delay for tenant-wide cuts (§7.3.6). Retention expiry uses the same barrier and purge evidence as explicit deletion. Access records follow their protected retention (§11.4), not scope or category cuts.

### 12.2 Redaction without self-deleting the replacement

`redact(event_revision, spans)` is an authorized deterministic copy-and-erase transaction, not model rewriting. Exact byte and span boundaries and authority are validated; a new protected revision containing only retained spans, with mapped provenance, is staged. Publishing the replacement and applying the original revision's deletion barrier happen atomically; no acknowledgement occurs until both are durable and the release fence is complete.

The certified retained-span copy is an explicit, narrow requirement exception: a new source unit, not an ordinary descendant of the whole original for erasure propagation. Its ancestry link to the original is kept for recall and lineage exclusion. It keeps the original's confidentiality and purpose restrictions; redaction never declassifies. The protected redaction control records input and replacement identities and transform version for audit, without reintroducing removed bytes. No model, arbitrary program or caller can use it to strip dependencies. Retained-byte equality and removed-byte exclusion are acceptance properties. Every pre-existing descendant of the original (statements, flags, hub lines, adapters) is still withheld or purged and regenerated from the replacement or independent surviving sources.

This preserves unrelated spans, not uninterrupted availability of every old summary. A request to delete the whole logical event or subject includes all revisions and replacements in discovery.

### 12.3 Deletion lifecycle

| State | Required condition |
| --- | --- |
| requested | Exact authorized target and scope, or explicit discovery request, recorded |
| authorized / restricting | Target restriction committed; old release rights being drained or fenced |
| serving\_blocked | No later controlled release or ordinary descendant commit can use the target or its descendants; acknowledged separately |
| purging | Idempotent per-surface cleanup and key and copy reconciliation in progress, including hub regeneration and adapter fallback and retraining |
| purge\_failed | A cleanup failed or a deadline was missed; barrier remains; retry or escalate |
| complete\_within\_scope | Every named controlled surface and required key and copy condition satisfied; evidence and external limits listed |

Serving is never reopened to make purge succeed. Cancellation or timeout does not lift an established barrier. Unknown dependency coverage contains the affected scope and prevents an unqualified completion claim. “Delete what you retain about X” requires authorized discovery, ambiguity resolution and an explicit coverage statement; semantic search alone cannot prove complete subject erasure. Independent sources survive an occurrence deletion when permitted; a subject-level request must discover them too.

The purge controller accesses only the payloads and metadata needed for authorized cleanup; these internal operations are not ordinary recall or new model processing. Running model or worker results touched by a barrier are withheld and purged. Content already released outside control is listed as such.

### 12.4 Keys and backups

Standard authenticated encryption uses independently addressable data keys for payload units and protected content or metadata. Deleting a database wrapper is not cryptographic erasure if a backup restores it while the wrapping key survives. A chosen KMS satisfies per-unit irreversible destruction only if all recovery, wrapper and key caches are covered; otherwise completion waits for physical copy or backup expiry.

**Initial design choice:** encrypted backups with short bounded expiry, not an unverified claim of immediate per-unit cryptographic erasure. Live stores, indexes, hubs, adapters and caches purge promptly; `complete_within_scope` waits for every relevant backup, WAL, replica and staging copy to expire or be verifiably purged. The recovery-only backup service never exposes content to retrieval; administrative restore access is protected and audited. Cached plaintext and keys have bounded lifetimes and explicit invalidation.

Deletion, revocation and permission-narrowing control history, together with elevation and access records (§11.4), lives in a separately durable recovery control plane under the same logical core authority, outside ordinary data-backup rollback, with authenticated checkpoints, monotone positions and redundant copies. A restore must prove it has the latest applicable control and audit state and enforce it **before** any serving or new derivation; otherwise it stays closed. Data restore alone cannot resurrect access. Tombstones outlive every compatible backup, export or replica that could reintroduce the target; identity reuse is forbidden.

### 12.5 Audit and erasure claims

Minimal audit keeps an authorized pseudonymous actor, policy reference, opaque target and request identity, state, surface evidence and counts. Names, payloads, sensitive free-form reasons, identifying relation labels and low-entropy plaintext hashes are stripped. Minimal tombstones and receipts are an explicit retained exception disclosed in deletion status, never described as “nothing remains.” Richer retained lineage is protected data and blocks claiming its erasure.

External recipients and ungoverned exports cannot be erased by local key destruction. Contracted provider retention and deletion evidence is tracked separately. A processor whose retention conditions violate a category's policy cannot receive that category at all. Completion reports distinguish local controlled surfaces, managed processor obligations and uncontrolled historical disclosures.

### 12.6 Import, export and schema portability

Legacy documents enter as historical captured aggregates with original location, import time, scope, purpose and available provenance. An author name or “accepted” label inside a file is an assertion, not authenticated authority; missing origin maps to X (or R for explicitly relayed user content). Extraction coverage is visible; partial import is not complete memory. Imported endorsements, procedures, permissions and vocabulary remain historical or inert until local authority mapping, curation and activation requirements are met.

Exports contain only records the caller can read, with schema and revision identities, provenance, applicable lifecycle restrictions and explicit missing or deleted markers. Credentials and automatic cross-deployment permissions are excluded. The destination is a checked disclosure; a managed export is a tracked deletion surface, and an uncontrolled delivered export is an external limitation. Import verifies origin and version, remaps tenant-local identity without collision, preserves restrictive history and rejects packages that would resurrect tombstoned records. Portability never manufactures access or erases audit gaps.

## 13. Failure Behavior

**Every failure degrades toward less disclosure and less action, never toward unchecked state or silent completeness.** **Fixed (proposed).**

| Failure | Required behavior |
| --- | --- |
| Capture or payload cannot commit | No saved acknowledgement; retry with the same identity; clean owned staging |
| Model, extraction or embedding unavailable | Keep permitted capture; bounded source recall with processing limits reported |
| Index missing or stale, or overlay scan too large | Bounded permitted fallback or explicitly partial response; restrictions never bypassed |
| Identity provider or membership unavailable | Deny decisions that need it; cached membership serves reads only within its bound; no consequential release |
| Permission state unknown or inconsistent | Deny the affected operation; contain the scope until reconciled |
| Policy decision or revocation status unknown | Deny the affected release or action; no silent stale authorization |
| KMS unavailable | Deny new unwraps; barriers persist; purge may remain incomplete |
| Source application unavailable | Qualified historical observation only, never falsely refreshed current state |
| Owner failover | Fence the stale writer and egress rights; recover canonical state and outbox |
| Outbox duplicate or worker crash | Idempotent delivery; no skipped watermark, duplicate transition or fabricated completion |
| Manifest or dispatch journal commit fails | No provider submission or external effect |
| Tool or provider result uncertain | Persist the uncertainty; reconcile before any consequential retry |
| Restriction fence cannot finish | No false acknowledgement; contain and report the deadline failure |
| Purge or backup expiry fails | Keep blocked; retry or escalate; report incomplete and the deadline miss |
| Vocabulary, screening or extraction unavailable | Recall continues as text, reported as “not structured” or “not screened” |
| Consolidation fails, is deferred or exhausts its budget | Hubs keep their last narrative, current exact lines and overlay, all labeled; exact projections unaffected |
| Consolidation output fails screening against projections | Previous narrative stays; the failure is recorded for review |
| Adapter blocked by deletion, or retraining fails | Serve the older qualifying adapter or the base model; report reduced retrieval quality |
| Ancestry cycle, missing reference or traversal limit | Reject the unsafe commit or use; contain the uncertain scope |
| Unsupported schema or stale restore controls | Read or migrate only under the compatibility contract; otherwise fail closed |
| Storage, quota or processing budget exhausted | Backpressure; reserve control and purge capacity; report partial or deferred work |

## 14. Initial Deployment Profile

**This manual defines an architecture family; the profile below binds the pilot instance with configurable defaults, and evidence applies only to the instance it exercised.**

### 14.1 Runtime choices and qualification limits

**Owner-selected:** Codex first with OpenAI-family models; Claude next. **Initial host:** a local or self-hosted Codex integration using supported MCP interfaces for memory-service operations, with a controlled app-server integration evaluated for deeper instrumentation. This is an implementation target, not evidence that stock Codex exposes every hook UPMS needs. No model identifier is a permanent default; each qualification records the exact runtime, model, tokenizer, provider account and configuration.

Codex's official documentation describes MCP connections and app-server thread, turn, event and approval interfaces. Tool hooks cover many local calls but exclude hosted tools and some specialized paths, and continuing an existing exec session does not repeat its pre-tool hook. **MCP plus hooks alone is therefore insufficient evidence of the instrumented profile.** The staged integration is a design inference from these documented facts.

Before Slice 1b, demonstrate exact pre-provider context capture (including compaction and resume), output interception before display, procedure and handle enforcement, nested agents, shell, network and processor coverage, current policy, release fencing and lineage-exclusion enforcement. Uncovered paths are disabled in the qualified instance. If supported APIs cannot supply these boundaries, Slice 1a's memory-service claim stands and the adapter design is reopened; a shadow transcript is never called complete instrumentation. A runtime fork or new enforcing host is a separate design decision.

Stock-client history, logs, provider sessions and local files outside UPMS are named external surfaces; a memory-service deletion cannot erase text already returned to them. Capturing or importing them needs explicit scope and capture permission. Claude must pass the same contract independently; no Codex pass transfers.

### 14.2 Configurable pilot defaults

These values are **agent-chosen planning and qualification targets** under the owner's delegation (rows naming a decision are the owner's own), not benchmark results, legal conclusions or approved policies. Configuration is schema-validated, versioned, audited and attached to every evaluation; changing a material binding invalidates only affected evidence. Overrides may tighten defaults; increasing exposure, relaxing an invariant or broadening scope requires the owning decision.

| Parameter | Initial value or rule |
| --- | --- |
| Tenancy and workload | One tenant; up to 5 users and 10 active agent sessions; continuing project work |
| Corpus envelope | 100,000 live event revisions; 1 million live canonical records; 10 GiB protected payloads; beyond this, backpressure and requalification |
| Capture throughput | 1 event/s sustained; bursts of 10/s for 60 s within quota |
| Retrieval latency | p95 ≤ 500 ms warm, ≤ 2 s cold, excluding remote inference and source fetch; both reported |
| Query and graph limits | 200 candidates, 30 returned items, 3 hops or 1,000 visited nodes, 2 s work budget; truncation explicit |
| Capture limits | 1 MiB inline UTF-8 text; 10 MiB declared file; 20 MiB expanded aggregate, 1,000 members, depth 16, expansion ratio 20; text and Markdown only at first; no nested archives or active rendering |
| Context allocation | Mandatory content and output first; UPMS extras ≤ min(8,000 tokens, 20% of remaining input), split 25% checkpoint share (L0 hub and task checkpoint) and 75% retrieval, unused budget reusable |
| Processing limits | 1 deep job per principal, 2 per tenant; 100 model calls and 1 million input+output tokens per principal per day |
| Required assessment age | At most 5 minutes plus exact current evidence epochs |
| Membership and permission cache | ≤ 60 s, invalidated by restriction epoch; consequential releases check online |
| Elevation | ≤ 1 h; re-authentication; reason required |
| Bulk destructive delay | 1 h, cancellable |
| L0 and L1 hub budgets | L0 ≤ 1,500 tokens; L1 ≤ 3,000 tokens each |
| Overview synchronization | Exact lines current at read (outbox plus read-time catch-up within the scan budget) or marked stale; regional consolidation before a narrative deadline first, then, with remaining budget, when a hub's overlay exceeds 20% of its token budget, a narrative unit is withheld or a narrative-projection contradiction is flagged; global consolidation weekly when a region changed, subject to the budget |
| Maintenance budget | min(500,000, max(100,000, 15% of the tenant's measured daily task-model tokens over a rolling 7 days)) tokens per day; 100,000 where task usage is unmeasured; unused budget accrues up to 7 days' allowance; at least half reserved for consolidation; deadline passes before fragmentation passes; invalidation exempt |
| Adapter retraining after training-source deletion | Within 24 h; older qualifying adapter or base model serves meanwhile |
| Raw source retention | 180 days from capture; an explicit authorized pin may extend |
| Durable user-approved task records | 365 days or a shorter scope policy; dependencies must also be lawfully retained, or the record becomes unavailable |
| Derived artifacts and handles | No later than the earliest required input deadline; handles ≤ 1 h and current segment eligibility |
| Rendered context window | Replay-only copies up to 7 days, shortened by any input's policy or deletion; novel canonical inputs keep their own deadline |
| Operational lineage | 180 days, and as long as a surviving dependent requires it within policy |
| Access records | At least one year, protected (decision D-13); may be lengthened; a reduction applies only to records created after it (§11.4) |
| Content-free operational logs | 14 days; payload logging off |
| Minimal deletion receipts | 1 year; tombstones longer only until every compatible resurrection source retires |
| Serving-block acknowledgement | Target ≤ 2 s; no success while the fence is unfinished |
| Live-surface purge | Target ≤ 24 h after the barrier |
| Backup expiry and complete purge | Backups expire ≤ 7 days; complete-within-scope target ≤ 8 days after the barrier |
| Plaintext and key caches | ≤ 60 s TTL plus barrier invalidation before any new release |
| Recovery | No loss of acknowledged commits for process or single-node failure; site-loss RPO ≤ 15 min, RTO ≤ 4 h; latest control state required before serving |
| Disk admission | Reserve max(2 GiB, 20% of capacity) for control, purge and recovery; stop nonessential ingestion before the reserve |
| Security policy | Declassification off except owner publication; public-reader exception off; no uncontracted tool; no cross-scope judgment reconciliation |
| Model and embedding processors | Deny until exact provider, account, endpoint and category permission are bound; prefer local small models and embeddings for restricted data |
| Overview replay cap | Replay cap: ≤ 60,000 input tokens per regional pass, L2 pages and sources together; an area above it is divided into sub-hubs by entity, then by time window (§10.5.4) |
| Planned narrative and adapter lifetime | 30 days, or half the scope's raw retention if shorter; consolidation and adapter training read only inputs at least this far from their retention deadline, through a deadline-filtered view, and re-run before the output's own deadline |
| Read-time scan budget | ≤ 1,000 commits and 200 ms per read, including a whole L0 assembly; beyond it, affected lines are marked stale and partial |
| Coordination records | As durable user-approved task records: 365 days or a shorter scope policy |
| Pilot languages | English plus the languages pilot users write in, named at Gate 0 (decision D-19); others are stored, cited and retrieved by n-grams and embeddings, without structuring |
| Language detection | Per span; below 0.8 confidence recorded as und |

No one-year task record silently extends a source's 180-day retention: either an explicit permitted extension covers its inputs, or the derived record expires or becomes unavailable. A user's fresh independent statement can be a new source event; presenting old model text for endorsement does not erase its dependencies. Retention controllers use server-recorded capture time and trusted current time; clock uncertainty never prolongs a security lease or falsely certifies expiry.

### 14.3 Storage and deployment

**Initial default:** PostgreSQL for canonical records, permissions, vocabulary, outbox and adjacency tables; protected payloads in object storage; derived lexical and vector indexes, hubs and adapters as derived artifacts. No dedicated graph database, event bus, universal confidence service or general policy engine inside UPMS; the scope-permission evaluator is data-local authorization, like a filesystem's. A small deployment may colocate trusted components, but access paths and process isolation must match the threat model. Identity, policy and KMS may be integrated providers behind their interfaces.

Per-object data-key envelopes and encrypted backup expiry follow §12.4. Concrete KMS and storage products, supported schema versions and availability layout are D4 choices if they meet these contracts; qualification establishes real key caching, backup, restore and deletion behavior. Tenant partitioning is not itself isolation. Searchable plaintext, embeddings, adapters, hubs and diagnostic metadata remain sensitive.

Timing and resource side channels, administrator access and provider-held data are explicit residuals. Before multi-user release, semantic isolation is tested and cross-scope timing leakage measured under the chosen index, cache and adapter design. A stronger noninterference promise needs an accepted stronger profile and evidence.

## 15. Invariants and Acceptance Evidence

**These are planned acceptance obligations, not executed tests; every applicable invariant must hold, and a better aggregate metric never compensates for a known violation.**

| ID | Acceptance property | Owner | First slice |
| --- | --- | --- | --- |
| H1 | Ordinary semantic state appends; erasure is explicit, scoped and audited; ancestry is never removed while any descendant survives, and traversal reaching a stripped node fails closed | 5–6, 12 | 1a |
| H2 | Claim, statement and judgment provenance resolves to retained records or explicit unavailability | 5, 9.6 | 2 |
| E1 | Capture, assessment, admission, provenance and permission stay distinguishable | 5–7 | 1a; full assessment 2 |
| E2 | Authorized conflicts stay visible; independent evidence is never silently suppressed | 5.3, 6.3 | 2 |
| E3 | New evidence invalidates current admission atomically; fresh use checks collection epochs; an assessment whose inputs include judgment, flag, hub, narrative or projection status, or a claim descended from one, is never admitted | 9.3 | 2 |
| A1 | Memory or imported text cannot grant a capability, a permission or a procedure activation | 6.5, 7 | 1a |
| A2 | The core alone commits canonical transitions; callers cannot forge labels or admission | 4, 9.1 | 1a |
| A3 | Endorsement and confirmation bind exact values, roles, scope, use and current authority | 6.4, 7.2, 7.5 | 1b; judgment endorsements 2 |
| AC1 | Content or existence is released only with current `r` or `l` on the home scope (or through an own-record or oversight entitlement) and on every scope in the item's requirement closure | 7.3.4–7.3.5 | 1a |
| AC2 | Permission narrowing, membership removal, ownership transfer and end of elevation are fenced like barriers | 7.3.7, 9.4 | 1a |
| AC3 | An agent session's rights never exceed its principal's; an agent principal's list and read reach never exceeds its overseer's non-elevated reach, and it never holds manage rights; the agent cannot remove the overseer grant; oversight transfer is fenced; sessions never elevate | 7.3.1, 7.3.6 | 1a |
| AC4 | Elevation is explicit, time-bounded and re-authenticated; every access during it is durably recorded before release, in the replicated control plane; the retention of existing access records can never be shortened; elevation never grants an administrator or their agents lasting rights or scope ownership | 7.3.6, 11.4 | 1a |
| AC5 | No principal, including administrators, can forge attribution or source class, set labels or admission, read past a barrier, bypass quarantine or disclose to a restricted processor | 7.3.6 | 1a |
| AC6 | Memory content cannot change permissions, membership or roles | 4.2, 7.3 | 1a |
| P1 | Source classes follow observed capture and field contracts and conservative propagation | 7.1 | 1a; runtime propagation 1b |
| F1 | Model and control dependencies and restrictions survive summaries, overviews, reset and transfer | 8.2–8.3, 10.5 | 1b; UPMS workers 1a |
| F2 | Every release or action passes its complete contract and current checks; only the qualified public-reader exception waives grounding | 7.2, 8.4 | 1b; UPMS releases 1a |
| F3 | Ineligible content or existence metadata never reaches unauthorized rankers or recipients | 10.1–10.3 | 1a |
| F4 | Only a tested fixed-slot interface avoids hidden-value taint; result-dependent handle metadata propagates restrictions | 8.3 | 1b |
| TM1 | Publication waives a scope's access requirement only for ancestors the publisher owns, and an agent needs the owner's confirmation for anything derived from a human's records (in Slice 1a-team through overseer confirmation of every agent publication; from Slice 1b through runtime lineage); ancestry, provenance and source classes survive | 10.6.2 | 1a |
| TM2 | Lineage exclusions traverse ancestry and hold at context, overview, query-expansion and adapter selection within instrumented coverage; attestations state their coverage | 10.6.4 | 1a primitive; 1b runtime |
| ST1 | Every structured field links to its source span; text wins on disagreement; deleting text deletes dependent structure | 5.7.5 | 2 |
| ST2 | Stated reasons and rules are claim content, never evidence or enforcement | 5.7.2–5.7.3 | 2 |
| VO1 | Vocabulary proposals are inert until curated; merges are reversible and trigger re-screening | 5.8 | 2 |
| SC1 | Screening is deterministic on replay and never resolves, refutes, supersedes or admits; compatible values never raise conflict flags; the absence of a flag never certifies support | 9.7 | 2 |
| AD1 | An adapter serves only principals with `r` on every scope in its requirement closure; training excludes X-class ancestry, unattested R-class ancestry and unconfirmed output; deleting a training source blocks it at the barrier | 9.8 | 3 |
| OV1 | Overview content is derived, source-linked and watermarked; exact projections are current at read, or explicitly marked stale and partial; read-time catch-up applies supersession, fulfilment, release, withdrawal and correction, not only additions | 10.5 | 1a |
| OV2 | Per-reader assembly never includes unreadable scopes; corrections, deletions and revocations remove affected lines before the next release | 10.5.5 | 1a |
| OV3 | Exact projections faithfully show recorded state and status whether or not consolidation has run; the narrative and overlay notes are always labeled synthesis and never presented as current fact | 10.5.3 | 1a exact parts; 2 narrative |
| OV4 | Maintenance spend stays within budget and each pass within the replay cap; scheduled expiry is planned for, not met by withholding; the budget bounds narrative coverage, and uncovered regions are labeled projection-only; exhaustion degrades coherence and freshness, never correctness or invalidation | 10.5.4 | 2 |
| OV5 | Between consolidations the narrative is never edited piecemeal; later changes appear only in the labeled overlay or as withheld narrative units | 10.5.3 | 2 |
| OV6 | Consolidation output is source-linked; generalizations are hypothesized claims; each narrative unit depends on every input of its invocation and is withheld whole when any input becomes unusable | 10.5.3 | 2 |
| C1 | Each instrumented invocation has a pre-dispatch manifest and a separate outcome | 11.1 | 1b; UPMS model workers when enabled |
| C2 | Recall finds all seeded retained ancestry within declared coverage and reports gaps | 11.3 | 1a memory; 1b downstream |
| C3 | Skeletons hold no payload; reconstruction windows cover every required item or report exceptions | 11.2 | 1b |
| R1 | Correction acknowledgement is ordered against release and preserves qualified history | 6.3, 9.4 | 1a UPMS; 1b downstream |
| D1 | Barriers reject every later affected controlled release and descendant commit, including after restore | 9.4, 12 | 1a |
| D2 | Completion names evidence for every controlled surface, key and backup and discloses retained exceptions | 12.3–12.5 | 1a |
| D3 | Retained-span redaction survives old-unit purge without keeping removed bytes; old descendants stay invalid | 12.2 | 1a |
| O1 | Fenced single-owner commits and idempotent mutations and outbox delivery prevent duplicate transitions | 9.1 | 1a |
| O2 | Replay never invokes models or actions; migration and rollback preserve restrictions | 9.6, 12.6 | 1a |
| O3 | Context fits actual model capacity or returns explicit overflow | 10.4 | 1a |
| O4 | Coverage distinguishes unavailable, unprocessed, unindexed, unstructured, unscreened and not found | 10.3 | 1a |
| O5 | Pre-effect intent plus uncertain-outcome recovery prevents blind consequential retries | 8.4 | 1b; UPMS dispatch when enabled |
| O6 | Resource exhaustion preserves restriction and purge capacity and never downgrades safety | 8.6, 13, 14 | 1a |
| M1 | Import and export preserve provenance and restrictive lifecycle without importing authority | 12.6 | 1a |
| AC7 | Owners can list and read records built only from their own records whatever their scope rights, and overseers can do the same for their agents' records; a record with others' inputs needs rights on its whole requirement closure | 7.3.4 | 1a |
| CO1 | Coordination records are author-entered, never extracted, shown with status and author rather than as in force; same-key conflicts are shown deterministically; each commitment has one authority | 5.4, 6.9 | 1a |
| ML1 | Original text is stored and cited in its own language; concepts are language-neutral and cross-language equivalence is curated; translations are labeled synthesis, never evidence and never action grounding | 5.9 | 1a storage, citation and grounding; 2 vocabulary |

### 15.1 Required falsification scenarios

Acceptance cases exercise the real core, storage, retrieval, permission and egress owners. Deterministic external doubles may control faults, but replacing an enforcing owner with a harness imitation cannot qualify it.

| Case | Adversarial trajectory and required discriminator |
| --- | --- |
| T01 | Contradictory capture after an assessment snapshot, before commit: the judgment cannot enter fresh admission, checked before and after queue processing |
| T02 | Delete or correct after the release check but before sending; mid-stream; egress participant crash: no controlled release after an acknowledged barrier |
| T03 | Delete an input of a mixed summary with stale indexes and closure cache: descendants blocked at once; independent sources still permitted |
| T04 | Redact a middle span, crash between staging and commit, purge the original, restore an old backup: retained spans survive only via the certified replacement; removed spans and old descendants never return |
| T05 | A reader encodes a secret in handle count, type, status, selection or a reset-selected objective: the planner or action inherits restrictions, or transfer is blocked |
| T06 | The same literal address appears in an unrelated user statement and an injected source chooses it: no role-bound intent, so dispatch fails |
| T07 | Public fetch redirects or rebinds to a local or metadata address, carries cookies, or chooses a query from private context: exception denied |
| T08 | Invalid, foreign, stale or revoked handle and mismatched confirmation nonce: no capability or revision bypass |
| T09 | Crash before or after an external send and before receipt: durable intent exists, uncertainty preserved, no blind duplicate |
| T10 | Duplicate ingestion and outbox messages, conflicting idempotency payloads, old writer after failover: exactly one transition or an explicit conflict |
| T11 | Quarantine release after ruleset, policy or evidence change: no restoration of obsolete admission |
| T12 | Original revision expires before manifest fragments, or a source is deleted during reconstruction: exact reconstruction explicitly unavailable; derived copies cannot launder retention |
| T13 | Restore without latest control history, with a stale KMS wrapper, WAL, replica or cache copy, or an expired backup awaiting cleanup: no premature serving or erasure certification |
| T14 | Cross-scope search, cache and pagination reuse, snippets, rerankers, errors and coverage queries: no unauthorized content or existence leak |
| T15 | Correction before extraction; ambiguous person or claim; commitment fulfilled after overdue; preference withdrawn: coherent lifecycles without erasing others' evidence |
| T16 | Import of a file claiming acceptance or authority, or a package with deleted identities; interrupted migration and rollback: history preserved, authority inert, no resurrection |
| T17 | Context overflow, graph cycle or fan-out, queue flood, low disk: bounded explicit failure; barriers and purge stay serviceable |
| T18 | Codex compaction and resume, hosted tool, continued exec, subagent, hidden prompt injection, output stream: each enabled path captured and enforced, or the instrumented claim fails |
| T19 | Late source revision, non-independent corroboration, unsupported normalization, conflicting scope judgments, failed partial processing: attribution and coverage preserved, no fabricated support |
| T20 | Policy or endorsement revoked after context assembly; provider input and telemetry carry private data: current destination and purpose checks deny |
| T21 | A user is removed from a group while an agent session streams output that used the group's scope: no release that begins revalidation after the UPMS restriction commit uses the removed access, and nothing is reported revoked before fence-complete |
| T22 | An agent saves a team-scope summary into a personal scope: a teammate without personal access cannot read it; the owner loses it after leaving the team |
| T23 | Injected content in an administrator's agent session requests an export or delete that only elevation would permit: refused, since sessions never elevate; operations within the administrator's ordinary rights follow normal checks |
| T24 | Elevated read of a personal scope: access record committed before release and owner notified; deleting the record, shortening scope, category or tenant retention, deleting or transferring the scope, or crashing before the audit commit never removes it or releases content unaudited; an old-backup restore re-applies the binding; reducing access-record retention affects only records created afterward |
| T25 | An administrator records a memory attributed to another user, or sets a claim admitted: rejected |
| T26 | A user with `w` but not `d` deletes their own item and is refused on another's; a `w`-only drop-box contributor cannot read others' items |
| T27 | A deletion cascades into scopes the requester cannot see without disclosing them; descendant owners see only “an input is unavailable” |
| T28 | Search, counts, coverage, flags and overviews reveal nothing about scopes where the requester lacks `l` |
| T29 | A published note derived from a private note and a confidential document: the private-scope requirement is waived, the confidential one still restricts readers, ancestry is kept, and deleting the private original leaves the published copy |
| T30 | A blind reviewer's context excludes the author's lineage after the author publishes their rationale: (a) the published copy and a hub built from it, including after the original is deleted and purged (1a-team); (b) a vocabulary definition derived from it (Gate 2); (c) an adapter trained on it (Gate 3) |
| T31 | Two agents supersede the same shared item concurrently: one applies, the other is recorded as a conflict |
| T32 | “Sky is blue” and “sky is green” at overlapping times without places: a possible flag with `missing_qualifier(place)` and `entity_match_uncertain`; “blue” against “dark” raises no conflict flag, only a recorded `ComparisonCue` of kind `different_dimension` |
| T33 | A Friday release intention against a no-Friday-deploy prohibition: flagged without approval; not flagged with an authenticated in-scope approval record; still flagged, with `unverified_exception`, when approval is only claimed in text or is forged, expired, out of scope or only a statement attributed to the role holder; replay after the role is revoked gives identical flags |
| T34 | A deprecated term still retrieves and screens memories that use it; new extractions use the current label |
| T35 | Content whose ancestry includes X, or R without a factual attestation or permitted-reliance endorsement, never enters adapter training; deleting a training source makes the adapter fall back at once and the retrained adapter excludes it; rolling expiry never forces a fallback; a base-vocabulary alias approval retrains only adapters whose training set uses the concept; the base-model vector index keeps serving |
| T36 | A blank model given only its L0 hub answers orientation questions; after a correction, L0's exact lines change before the next release |
| T37 | Consolidation paused for a week while work continues: exact lines current at read, overlays complete and pageable beyond the hub budget, narratives labeled with their age |
| T38 | An input of one consolidation invocation is deleted: every narrative unit from that invocation is withheld before the next release with no LLM call, whatever its citations; units from separately generated sections with disjoint inputs remain |
| T39 | Maintenance budget exhausted mid-day: no further maintenance LLM calls; task work and invalidation unaffected |
| T40 | The archive grows tenfold at the same change rate: replayed input tokens per pass, L2 and sources together, stay within the replay cap, global-pass work grows only with the number of L1 hubs, and deferred work and coverage are reported together |
| T41 | Hundreds of small changes in one area without consolidation: the narrative stays unchanged and coherent, the overlay carries every change, and the fragmentation threshold schedules a regional consolidation within the budget |
| T42 | Consolidation writes a value contradicting an exact projection, and separately an unsupported causal link outside any slot: the contradiction blocks replacement; the unsupported link may pass screening and appears only inside the narrative labeled as synthesis, never as current fact |
| T43 | A compliant ruleset whose assessor reads judgment status, a hub, or a consolidation hypothesis or agent claim derived from one: the assessment is kept evidence-only and never admitted; after a supporting judgment is superseded with no new source, no dependent judgment is fresh, including a cached one; the default ruleset with fidelity endorsements is accepted |
| T44 | A w-only contributor, human or agent, reads its own record but not others', and an agent contributor's overseer reads it too; an owned summary of others' records stays unreadable once the owner's rights are narrowed, in another scope or the same one; an agent writes, corrects and deletes in its own scope but cannot change permissions or remove its overseer's grant; after a scope's ownership is transferred, record owners and entitlements are unchanged and the same reads succeed or fail |
| T45 | Membership removal with delayed or dropped identity-provider notices, an expired cache and a paused egress participant: the four stages are reported separately, and only fence-complete is acknowledged as revoked |
| T46 | Outbox paused, an obligation committed, a hub read: the hub shows the obligation through read-time catch-up, or is returned explicitly stale and partial; contradictory coordination records with one key appear as attributed conflicts; superseded, fulfilled or released records leave the exact lines, or the hub is marked stale (statement conflicts follow in Slice 2) |
| T47 | A checkpoint outlives a required input: the user sees the effective loss deadline in task continuation and retention inspection, with the input named only if they may see it |
| T48 | An agent derives an item from a human's messages in its own scope and publishes it: the human's requirement stays and the item is queued for the human's confirmation; an item derived only from the agent's own notes publishes without confirmation; a team lead's summary of members' records keeps their requirements; a human's confirmation for one target scope does not waive the requirement for another; an agent cannot waive a team scope's requirement on which it lacks manage rights; revoking a confirmation withholds the copy; in Slice 1a-team, an agent publication or shared coordination record without its overseer's confirmation is refused |
| T49 | An agent's overseer elevates, the agent gains a group grant its overseer lacks, and oversight is transferred while the agent streams: the agent never reads beyond the overseer's non-elevated reach, and the transfer is fenced |
| T50 | Publish, delete and purge the original, then run a blind task and a subject erasure: the copy is excluded from the blind context and found by erasure, or the coverage gap is reported |
| T51 | An elevated administrator tries to grant rights to themselves or to a group containing them, take a personal scope, or make themselves an overseer: refused; transferring an active user's scope needs a second administrator and notifies the owner; the primary site is lost just after an elevated release, and the access record survives |
| T52 | A published copy whose owned ancestor reaches its retention deadline survives under the target scope's policy; when a foreign ancestor expires or is deleted, the copy is withheld; the owner's deletion status lists surviving copies |
| T53 | A concept curated from a published copy carrying a foreign requirement, and an adapter trained on one: a reader without the foreign right sees neither, and the base vocabulary refuses the concept |
| T54 | Steady-state simulation at the corpus envelope with 180-day rolling expiry: consolidation demand stays within the budget; deadline passes are never starved by fragmentation passes; no narrative input, including L2 lines, is within the planned lifetime of its deadline; narrated regions meet the preregistered availability floor; the narrated fraction is reported and projection-only regions are labeled |
| T55 | Duplicate ownership claims and contradictory decisions with one key appear as attributed conflicts; the author's supersession closes the old record; a supersession by someone without curate rights is recorded as a conflict; an overdue commitment stays open |
| T56 | An L0 read across 50 scopes whose combined catch-up gap exceeds the scan budget: affected lines are marked stale and partial, and no current token is returned |
| T57 | A piggybacked completion claim with no receipt appears only as a labeled note, “claimed by” its author; deleting its input withholds the note before the next release |
| T58 | A principal without list rights on a source declares an exclusion naming it: refused; an ancestry endpoint in an unlistable scope appears only as “private source” |
| T59 | The same decision recorded in English and Japanese resolves to one concept and one slot; a contradicting value recorded in German raises a flag; each citation shows its original language |
| T60 | A query in one pilot language retrieves memories written in others and in a mixed-language message; a language without an analyzer is reported as degraded coverage, never as none found |
| T61 | Two concepts linked only by close\_match never share a slot, and comparing them gives at most a possible flag with cross\_language\_mapping; a model-proposed translation stays inert until curated; a look-alike label in another script is flagged at proposal |
| T62 | A translated quote appears labeled as synthesis beside the original; an action argument present only in translation fails grounding; translating a restricted span through an unapproved external service is refused |

### 15.2 Evaluation protocol

Corpus, implementation and configuration, oracle, prompts, models and judges, budget and decision rule are frozen before measuring. Baselines: B0 source-preserving lexical retrieval; B1 hybrid transcript chunks; B2 full history where it fits; later slices also compare against the previous accepted slice, with the same authorized corpus, answer model and matched budgets. B2's non-applicable cases are reported, not silently excluded.

Initial evaluation: 200 synthetic continuing-project episodes, 100 for development and 100 held out, with at least 10 held-out episodes in each of update and correction, temporal reasoning, scope isolation, continuation, absence and abstention, team coordination, cold-start orientation and multilingual or mixed-language work (overlap allowed and disclosed). Every applicable T01–T62 scenario runs separately; correctness cases are never replaced by aggregate benchmarks. Real-session evaluation is optional until permission is obtained; synthetic results cannot establish real-user generality.

Primary outcome: paired task completion at a fixed declared context budget, with an exact source, permission and lifecycle correctness rubric. Gate target: at least one preregistered continuity or recall outcome improves with a paired 95% interval excluding zero, no mandatory invariant fails, and material task-success regressions exceed neither the preregistered 5-percentage-point margin nor its uncertainty bound. If the sample cannot establish the rule, the result is inconclusive and a new evaluation is specified; the rule is never relaxed after results. Slice 1b may justify equivalent task success with materially better measured enforcement under a preregistered cost tradeoff. Each later slice must show incremental value over the previous one.

Secondary outcomes: attribution fidelity, stale-current answers, temporal correctness, conflict visibility and screening precision and recall, coverage, unnecessary blocking, confirmation prompts, cold-start orientation success and navigation cost, overview staleness and churn, maintenance-to-work cost ratio, extraction consistency across runs and models, normalization coverage, total lifecycle cost and warm and cold latency. Initial confirmation usability threshold: median ≤ 1 integrity confirmation per completed task and p95 ≤ 3 on the ordinary workload; C4-heavy tasks reported separately and never exempted from their confirmation rule, apart from §7.2's pre-authorized self-publication class, reported separately. Human attention and false blocks count as cost. These thresholds are reviewer choices, not observed results.

Human adjudication reviews every consequential authorization or attribution failure plus a stratified 20% sample of other held-out judgments; a model judge is validated against that sample and disagreements are resolved visibly. All evaluated variants, failures, post-outcome changes, held-out reuse and unknown prior selection history are recorded. Adapter promotion and team-policy experiments (§9.8, §10.6.6) use this same discipline. Public benchmarks may supplement but cannot qualify security or deletion. No results or comparative superiority are claimed here.

## 16. Delivery Slices and Gates

**Useful, permission-aware recall with a deterministic overview ships first; end-to-end runtime instrumentation, structured meaning and consolidation follow as separately gated slices; team policies and adapters are experiments on top.** No date or shipping commitment is implied, and no slice borrows a previous slice's acceptance for an untested guarantee.

| Gate or slice | Deliverable | Required closure |
| --- | --- | --- |
| Gate 0 | This candidate accepted with named owners; decisions D-1 to D-19 confirmed or changed; pilot languages named; bound profile; bounded D4 specification and executable test specification | Independent falsification of this exact text; product acceptance; evidence bound to the accepted slice and profile (storage, KMS, backup, replicated audit, and MCP principal, session and capture-path feasibility for the bound Codex build, for Slices 1a-core and 1a-team; Codex instrumentation feasibility only when Slice 1b is inside the accepted boundary); evaluation frozen before measurement |
| Slice 1a-core / Gate 1a-core | Codex-facing single-user memory service via MCP: capture, protected storage, language-tagged capture and original-language citation, scoped lexical and hybrid recall across pilot languages, coverage, checkpoints and coordination records, correction, suppression, redaction and deletion, import and export; personal scopes with own-record rights; overview projections of coordination records, checkpoints and controls, with read-time catch-up and pageable overlays (no slot tables) | 1a invariants on real boundaries (including AC1, AC6, AC7, CO1, OV1–OV2, OV3 exact parts); T02–T04, T10, T12–T17, T36, T46, T47, T55 single-author part, T56, T60, T62; recoverable payload and control state; purge and restore evidence; inspection journeys; matched recall and continuity evaluation, with coordination-record capture measured, not assumed; no claim about unmediated Codex actions |
| Slice 1a-team / Gate 1a-team | Groups, agent principals and overseers, administrator elevation and protected access records; publication, shared-pool concurrency and the lineage-exclusion primitive; per-reader team overviews | AC2–AC5, TM1, TM2 primitive; T21–T29, T30 part (a), T31, T44, T45, T48 overseer-confirmation part, T49–T52, T55 multi-author part, T58; Gate 1a-core retained |
| Slice 1b / Gate 1b | One qualified Codex instrumented adapter: manifests, segments, handles, current policy, controlled egress, dispatch recovery, runtime lineage exclusions and independence attestation | T18 coverage demonstrated; F1, F2, F4, C1, C3, O5, TM2 in the runtime; T05–T09, T20, T30 part (a) through the runtime, T48; adversarial races; confirmation-burden threshold; no enabled bypass |
| Slice 2 / Gate 2 | Lazy claims and structured statements; vocabulary registry with multilingual labels and expansion; deterministic screening and candidate channel; processing cascade tiers 1–2; judgments, temporal and conflict projections; reversible identity matching; limited endorsements; L2 pages; consolidated narratives with deadline-aware regional and per-scope global consolidation | H2, E2, E3, ST1–ST2, VO1, SC1, OV3–OV6; T01, T11, T19, T30 part (b), T32–T34, T37–T43, T53 vocabulary part, T59, T61, T54 with a preregistered availability floor, T57; extraction consistency and normalization coverage measured on real sessions before screening is relied on; incremental value over 1a; 1b guarantees retained where enabled |
| Slice 3 / Gate 3 | Team visibility policies (experiment §10.6.6); per-scope adapters (tier B, query-side); graph-assisted retrieval; Claude adapter; broader collaboration | AD1; T30 part (c), T35, T53 adapter part; adapters beat tier A; team policies beat all-shared and all-private baselines; ablation or comparator and full lifecycle and security evidence for each addition; explicit cost tradeoff; Claude qualified independently of Codex |

The structured foundation (Slice 2) precedes team policies because conflict screening between workers needs comparable statements; basic recall, publication and pull-only notebooks work on text alone. A memory-service release is not the final first-runtime instrumented deliverable.

Slice 1a is split (decision D-16) so that the first gate tests a single-user service before groups, agents, administration and publication are added. In §15, a first slice of “1a” means Slice 1a-core, except AC2–AC5, TM1, TM2, AC7's overseer clause, CO1's multi-author clause, and the publication and lineage paths of H1 and C2, which first apply in Slice 1a-team; TM1's derivation clause is fully tested only in Slice 1b.

## 17. Delegation, Inspection and Reopen Triggers

**Implementation may choose anything this manual does not fix, provided every invariant holds; a change that cannot hold them reopens the owning section instead of being patched around.**

### 17.1 Implementation (D4) space

Delegated: language and frameworks; schemas and serialization; indexes and libraries; embedding, extraction, classifier, contradiction and base models for adapters; prompts for extraction, overlay notes and consolidation; ranking weights; hub rendering and templates; significance heuristics within §10.5.3; helper functions; scheduling and backoff; cache representation; KMS product; user-interface layout; transport implementation. These preserve durable semantics, the bound profile constraints and acceptance at real owners. Components are not multiplied to imitate a missing runtime hook: the enforcing boundary is fixed, or the claim is narrowed honestly.

### 17.2 Product inspection surfaces

Within the requested deliverable (proposal v0.3 §11, extended by the owner's round-2 requirements), subject to normal access control including existence disclosure:

- What was remembered, from which source, and when?
- Why was it retrieved or presented as current, with which assessment and coverage?
- What supports or opposes it, what is flagged as conflicting and why, and what is unprocessed or unavailable?
- Did correction, suppression, quarantine, redaction, revocation or deletion take effect, and what remains pending?
- Which retained outputs or actions might it have influenced, with what outcomes and limits?
- What retention deadline applies, and which controlled and external surfaces remain after deletion?
- Who can see this memory, and why?
- Who accessed my personal scope while elevated?
- What does this term mean here?
- What is the current big picture, and how old is its narrative?

No independent scientific-result database or dashboard is added. Technical review cannot accept a product surface beyond the requested deliverable on the owner's behalf.

### 17.3 Non-goals and simplification

No truth oracle; no motive, interest, incentive or threat inference about people; no person reputation; no training of the main LLM on retained memory (small-model adapters only as derived indexes, §9.8); no general theorem prover; no replacement system of record; no cross-tenant transactions or federation; no guaranteed model causal attribution; no universal prompt-injection immunity; no erasure of uncontrolled recipients; no generic numerical confidence or numeric interpretation weights.

Design tradeoffs, not measured optimality claims: Event, Claim and Judgment stay separate because observation, proposition and assessment have different identities and lifecycles; claims, statements and judgments are not required for basic recall; evidence and exposure stay distinct in one relation store; four ownership boundaries without mandatory separate services; canonical storage and outbox instead of an event bus; hypothesis truth owned only by Judgment; scope epochs before slot-level invalidation; a small fixed rule language instead of general logic; the overview as derived hubs over the archive, not a second authority.

### 17.4 Reopen and impact rules

Reopen the owning section if:

- runtime capture or mediation cannot enforce it, or hidden state prevents reset;
- conservative invalidation destroys usable availability;
- purge deadlines exceed feasible key and backup behavior;
- confirmation burden exceeds the declared threshold;
- a new processor changes the confidentiality boundary;
- permission evaluation cannot be performed before ranking at the declared scale;
- lineage exclusions cannot be enforced on an enabled context path;
- extraction consistency or normalization coverage is too low for screening to be relied on;
- consolidation cannot keep the maintenance budget while holding OV3–OV6;
- adapters fail to beat vocabulary expansion, or their deletion retraining misses its target.

Scientific-record custody, calibrated scores, numeric weights or guaranteed approximation route upstream (§1.4). Cross-tenant or federated use, declassification beyond owner publication, and arbitrary privileged execution require new explicit architecture decisions.

On any accepted material change, affected records and APIs, adapters, operation and ruleset contracts, vocabularies, caches, indexes, hubs, migration and recovery, tests, documentation and evaluation identities are remapped; unaffected evidence is preserved only with reason. Equivalent D4 changes that preserve these contracts do not reopen D3. Repeated wrappers or fallbacks around one broken mechanism trigger re-derivation before another additive repair.

## 18. Readiness, Open Decisions and Remaining Closure

**Readiness: NO-PASS for unconditional implementation-ready or accepted-current status; ready for independent D3 review.** This candidate applies the repairs from the cross-review of candidate 2 and the interim review of candidate 3 to the integrated text and binds pilot defaults under delegation. That is not a demonstration of the runtime, storage or evaluation contracts.

### 18.1 Remaining closure

| Item | Evidence still required | Owner and boundary |
| --- | --- | --- |
| Independent review | The author of this candidate cannot independently accept it | Independent reviewer of this exact text, then the product owner at Gate 0 |
| Codex instrumented feasibility | Documented MCP, hooks and app-server features do not establish exact context capture, complete egress control or runtime lineage exclusion | Runtime and architecture owner; before accepting Slice 1b |
| KMS, backups and recovery | Concrete service and copy inventory; restored-control and audit-state proof; replicated audit-commit latency before release; adapter and hub purge behavior | Security and infrastructure owner; feasibility before specification freeze, full tests at Gates 1a-core and 1a-team |
| Structured-meaning feasibility | Extraction consistency across runs and models; normalization coverage on permitted real sessions; screening precision and recall | Architecture and evaluation owners; before Slice 2 relies on screening |
| Consolidation economics | Maintenance-to-work ratio, coherence, and narrative availability under rolling expiry (T54) at pilot scale | Evaluation owner; Gate 2 |
| Evaluation freeze | Corpus, rubric, judge and harness identities, randomness and repetition plan | Evaluation owner; before measurement |
| Source reconciliation | The cross-review of candidate 2 (CR01–CR10, Appendix A.4) and the interim same-family review of candidate 3 (M-01–M-26, Appendix A.5) are addressed here; this exact text needs independent re-review; no acceptance record exists for any version | Product owner confirmed on 31 October 2026 that no other governing record exists |
| Coordination-record adoption | Whether people and agents actually enter coordination records through MCP is unmeasured; Slice 1a-core evaluation measures capture on permitted real sessions rather than assuming it in a synthetic corpus | Product and evaluation owners; Gate 1a-core |
| Judgment-on-judgment assessment | A separately accepted current-head dependency contract before any ruleset may use judgment status (§9.3) | Architecture owner; before Gate 2 broadens rulesets |

**Named owners for this early version:** the product owner (Sam) holds the architecture, security and infrastructure, evaluation, and Codex runtime owner roles named above. Independent review remains a separate role and cannot be held by the author.

### 18.2 Owner decisions

The product owner kept the proposed defaults D-1 to D-10 and decided D-11 for the round-2 review; accepted the recommended outcomes D-1 to D-14 after the cross-review of candidate 2; and on 31 October 2026, after the interim review of candidate 3, accepted the revised D-8, D-9, D-12 and D-13 and the new D-15 and D-16. The author then reworded D-1, D-5, D-6 and D-8 to D-12 as consequences of D3 repairs, including a same-family check of the draft; the owner confirmed those outcomes and decided D-17 and D-18 on 31 October 2026, then added multi-language support (D-19). All decisions are for this early version and may change if a later review challenges them. Each may still be revisited at Gate 0.

| ID | Decision | Outcome | Main alternative |
| --- | --- | --- | --- |
| D-1 | Administrator reads of personal scopes | Elevated, recorded in the replicated control plane before release, owner notified; failed notices shown | Logged only; or silent, as root |
| D-2 | Administrator power through agent sessions | Never: sessions do not elevate | Allowed with per-action confirmation |
| D-3 | Scope nesting | Defaults copied at creation; no live inheritance | Live inheritance |
| D-4 | Source of groups | Identity-provider interface, built-in directory for the pilot; four named revocation stages (§7.3.7) | Groups native to UPMS |
| D-5 | Rights granularity | Six rights `l r w c d m`, plus own-record and oversight entitlements (§7.3.4) | Strict `r w x` |
| D-6 | Derived memories when access to a source is lost | Lost (no-laundering), including summaries saved in the same scope; owner publication of owned ancestry is the only waiver | Re-statement prompt before access ends |
| D-7 | Agents as persistent principals | Yes, each with a human overseer | Sessions acting only for humans |
| D-8 | Who decides publication | Agents publish without per-item confirmation only from their own private scope or scopes they manage, and only items whose ancestors there they own; anything derived from a human's records needs that human's confirmation of the exact publication; fully enforceable only with runtime lineage (see D-17) | Per-item human confirmation for all agent publication |
| D-9 | Oversight | An agent's list and read reach never exceeds its overseer's non-elevated reach; agents never hold `m`; the overseer holds a protected lrd grant; agent private scopes cannot be widened; oversight transfer needs a second administrator and is fenced | Configurable oversight |
| D-10 | Blind review in the pilot | Lineage-exclusion primitive in Slice 1a-team, traversing ancestry; team policy in Slice 3 | Required in 1a |
| D-11 | Domain adaptation of small models | In scope, as gated per-scope adapters, query-side only in the pilot (§9.8) | Out of scope |
| D-12 | Published copy when its private original is deleted or expires | Survives under the stricter of the target scope's and category retention for ancestors the publisher owns, when a human published it (an agent's self-publication never extends retention); other ancestors still propagate; subject erasure finds it through ancestry | Copy deleted or expired with its original |
| D-13 | Audit retention | At least one year; may be lengthened; a reduction applies only to later records; no shortening path | Shortening with a second administrator's approval |
| D-14 | Rule screening in the pilot | Prohibitions only; required and permitted rules stay text | Full deontic screening |
| D-15 | Source of the Slice 1a overview | Author-entered coordination records with a deterministic same-key conflict rule (§5.4, §6.9) | Checkpoints, controls and attributed events only |
| D-16 | Slice 1a boundary | Split into 1a-core (single-user service) and 1a-team, each with its own gate | One Slice 1a gate |
| D-17 | Agent publication before runtime lineage | In Slice 1a-team the overseer confirms each agent publication and each agent coordination record in a shared scope; lifted at Slice 1b, where runtime lineage enforces D-8 | Accept and disclose the gap |
| D-18 | Narrative coverage | Default maintenance budget; the narrated fraction is measured in the pilot (T54) and the rest is labeled projection-only | Raise the maintenance budget |
| D-19 | Multi-language support | In scope (owner requirement, 31 October 2026): language-neutral concepts, curated cross-language equivalence, original-language citation (§5.9); pilot languages named at Gate 0 | One working language; translate at capture |

Default values are not missing decisions merely because they are configurable; missing enforcing capabilities and required evidence remain missing. Gate 0 may narrow a workplan to an accepted Slice 1a boundary without claiming later closure, but cannot silently discard the full Codex integration objective.

## Appendix A. Review Lineage

**Five review rounds shaped this text; each item below names where its result now lives.** Assertions in this appendix are by the AI authors named, not by an independent reviewer.

### A.1 Review of proposal v0.3 (R1–R7)

Asserter: Claude (AI), 30 October 2026. No acceptance decision was made on it. The first architecture manual's “R” tags refer to these items; review candidate 1 recorded this review as not supplied.

| ID | Finding on v0.3 | Repair | Current location |
| --- | --- | --- | --- |
| R1 | Integrity was a placeholder with no default policy | Source classes as provenance facts plus a consequence-class policy | §7.1–§7.2 (strengthened by F02–F04) |
| R2 | Whole-invocation taint accumulates until sessions become unusable | Segments and handles | §8.3 (strengthened by F05) |
| R3 | Authenticating the sender collapses “first-party” when text is pasted | Span marking as adapter conformance | §7.1 |
| R4 | Slice 1 was most of the system | Split along integration profiles | §16 |
| R5 | Manifests were the most sensitive records with no retention policy | Long skeleton, short rendered fragments | §11.2 (strengthened by F08–F09) |
| R6 | Phantom-read validation for judgments was expensive and underspecified | Snapshot validity with a staleness bound | §9.3 (mechanism superseded by F01's evidence epochs) |
| R7 | Deleting one fact from a message required deleting the whole turn | Span redaction | §12.2 (corrected by F07) |

### A.2 Review of the first manual (F01–F18)

Asserter: Codex (AI), 30 October 2026; record SHA-256 `b0617a925916a130d47187917e54acd009ba3f367da29015c916ff94e8854f50`. All eighteen repairs are retained: insertion-race freshness (F01, §9.3); role-bound grounding (F02, §7.2); the public-reader exception (F03, §7.2); blocking uncontracted tools (F04); handle metadata channels (F05, §8.3); the release fence (F06, §9.4); redaction self-deletion (F07, §12.2); reconstruction windows and representation expiry (F08, §11.2); lineage metadata and restore controls (F09, §11.2, §12.4); guarded submission paths (F10, §4.3, §6.2); lifecycle coherence (F11, §6.1); judgment heads and attributed admission (F12, §5.3, §7.6); payload publication and idempotency (F13, §9.1–§9.2); durable dispatch intent (F14, §8.4); import, export and schema compatibility (F15, §9.6, §12.6); purpose, non-users and opaque consistency tokens (F16, §4.2, §10.3); missing figures and delivery plan (F17, §3, §16); Codex feasibility (F18, §14.1).

### A.3 Round-2 amendments (A1–A7)

Asserter: Claude (AI), drafting for the product owner, 30–31 October 2026; requirements from the owner.

| ID | Amendment | Current location |
| --- | --- | --- |
| A1 | Memory access control: users, groups, agents, rights per scope, administrator | §4.2, §4.3, §6.7, §7.3, §11.4, §12.1 |
| A2 | Team memory and coordination: tiers, publication, blind work | §6.8, §7.4, §10.6 |
| A3 | Statement language | §5.2, §5.7 |
| A4 | Vocabulary registry | §5.8 |
| A5 | Deterministic screening | §9.7 |
| A6 | Processing cascade and adaptive models | §9.8, §17.3 |
| A7 | Overview layer, synchronization and consolidation | §10.5 |

### A.4 Cross-review of candidate 2 (CR01–CR10)

Reviewer: Codex (AI), 31 October 2026; record SHA-256 `d7ef16e8cba2214d8d394e592978380ba63a25974c15f8c6682a1b818c0ce6d5`; disposition NO-PASS. The repairs below are asserted by Claude (AI) for the product owner, who accepted the recommended outcomes for D-1 to D-14. They have not been re-reviewed.

| ID | Finding on candidate 2 | Repair | Sections | Tests |
| --- | --- | --- | --- | --- |
| CR01 | Publication “released” dependencies, so lineage exclusion, deletion and erasure lost track of published copies | Ancestry (always kept) separated from restrictive requirements (waivable); publication makes a copy that waives only owned-scope access requirements; lineage exclusion and subject erasure traverse ancestry | §5.5, §7.3.5, §7.4, §10.6.2, §10.6.4, §11.3, §12.2; D-12 | T29, T30 |
| CR02 | Withholding single narrative sentences assumed citations capture everything a sentence depends on | The narrative unit is one invocation's output, withheld whole when any input is invalidated | §10.5.3 | T38 |
| CR03 | A completed screen cannot warrant the overview's correctness promise, yet narratives and slot tables were presented as correct current state | Correctness promised only for exact projections; narrative labeled as synthesis; slot tables show status and conflicts | §10.5, §10.5.1, §10.5.3 | T42, T46 |
| CR04 | The baseline's restriction of pilot rulesets to source and claim evidence was dropped, so a superseded supporting judgment could escape evidence epochs | Pilot rulesets may depend only on source, claim and statement evidence; rulesets using judgment status are rejected | §9.3 | T43 |
| CR05 | `w`-only contributors could not read their own records; an agent could legitimately hold access its overseer lacked, so “always on” oversight was false, and could remove the overseer's grant | Own-record entitlement; agent rights bounded by the overseer's; overseer grant protected | §7.3.1, §7.3.3, §7.3.4 | T44 |
| CR06 | Administrators could erase access records through retention settings | Protected audit retention with a one-year minimum; shortening needs a second administrator, never for their own access | §11.4, §12.1, §14.2; D-13 | T24 |
| CR07 | The screening contract specified incompatible outcomes and wrong deontic semantics: permitted actions were flagged and absent obligations could not be flagged | Informational cues separated from flags; prohibitions only in the pilot; only authenticated in-scope exception records suppress a flag | §5.7.3, §9.7; D-14 | T32, T33 |
| CR08 | Maintenance cost was not bounded as the archive grows | Region size cap; bounded-work contract; budget values; retrain only adapters whose sources changed | §9.8, §10.5.4, §14.2 | T37, T40, T41 |
| CR09 | Slice 1a's overview depended on statements and vocabulary from Slice 2; “current at every commit” conflicted with the asynchronous outbox; Gate 0 asked for Codex evidence outside the slice; revocation had one undefined “acknowledged” point | 1a overview built from typed coordination records with read-time catch-up; Gate 0 evidence bound to the accepted slice; four named revocation stages | §7.3.7, §10.5.1, §10.5.3, §14.2, §16 | T21, T45, T46 |
| CR10 | The continuity warning for checkpoints outliving their inputs was lost | Restored, with input names shown only to readers who may see them | §10.5.5 | T47 |

Also changed: agents may publish without confirmation only items they own, waiving only scopes they own (D-8, §10.6.2); T23 now states its oracle; content whose ancestry includes X, or R without a trust endorsement, is excluded from adapter training (§9.8, T35). On the reviewer's questions 5 and 7, T23 and T24 answer administrator erasure and session elevation, and the training exclusion answers planted external content.

*Correction (candidate 4, M-26).* As published in candidate 3, this table cited an unchanged section (§5.3) and unchanged tests (T26, T39), and paraphrased CR03, CR05, CR07 and CR09 inaccurately; the rows above are corrected. A section-level comparison of candidates 2 and 3 shows that the repairs also changed §2, §3, §5.7.3, §7.3.1–§7.3.8, §7.4, §9.7, §9.8, §10.5.2, §10.5.4, §10.5.5, §10.6.2–§10.6.5, §11.3, §11.4, §12.1, §12.2 and §14.2; invariants H1, E3, AC3, AC4, AC7, TM1, TM2, SC1, OV1, OV3, OV5 and OV6; and tests T21, T23, T24, T29, T30, T32, T33, T35, T37, T38, T40–T42, with T43–T47 added. The decision table also lost its alternatives column, restored in §18.2. The “Also changed” line's §10.6.3 citation is likewise corrected to §10.6.2.

### A.5 Interim review of candidate 3 (M-01–M-26)

Reviewers: three Claude (AI) subagents in fresh contexts, consolidated by Claude (AI), the manual's author, 31 October 2026; record SHA-256 `d462621194357cd1276306bb47bb7d0885af701a51c3ccbe6e5e73d8e6c69834`; disposition NO-PASS with two Serious Challenges. Same model family as the author, so not independent. The product owner accepted the recommended answers to Q1–Q5 (decisions D-8, D-9, D-12, D-13, D-15 and D-16). The repairs below are asserted by Claude (AI) and have not been re-reviewed; sections and tests were confirmed by a section-level comparison of candidates 3 and 4.

| ID | Finding on candidate 3 | Repair | Sections | Invariants and tests |
| --- | --- | --- | --- | --- |
| M-01 | The publication waiver was keyed on scope ownership, so an agent could publish a derivative of a human's records without the human; agent publication skipped C4 | Waiver only for ancestors the publisher owns or whose owner confirmed; required categories only for wholly self-owned ancestry; agent self-publication a pre-authorized C4 class | §2, §4.3, §6.8, §7.2, §7.4, §10.6.2, §10.6.3; D-8 | TM1; T48 |
| M-02 | The overseer bound made an agent's own scope read-only and excluded the overseer from operational state; the obvious patch granted `m` | Overseer bounds only list and read reach; agent keeps `w c d` on its own scopes, never `m`; overseer holds `m` and an oversight entitlement | §6.7, §7.3.1, §7.3.2, §7.3.4, §7.3.8, §10.6.5; D-9 | AC3, AC7; T44 |
| M-03 | Rolling expiry withheld narratives almost always; the cap did not bound replayed sources; budget and global pass ungated | Deadline-aware replay with a planned lifetime; replay cap on L2 and sources; fixed regions split by entity or time; per-scope, budget-gated global pass; budget base per profile with accrual | §2, §10.5.2–§10.5.4, §14.2 | OV4; T40, T54 |
| M-04 | “Ancestry never removed” contradicted purge stripping, so a surviving copy could escape lineage exclusion and erasure | Ancestry of purged nodes kept while any descendant survives; traversal reaching a stripped node fails closed | §2, §5.5, §10.6.2, §10.6.4, §11.2 | H1; T30, T50 |
| M-05 | An elevated self-grant or ownership transfer became unaudited access | Elevation cannot grant an administrator or their agents rights or ownership; active-user scope transfer needs a second administrator and notice | §7.3.6 | AC4; T51 |
| M-06 | Access records could be lost by restore | Committed to the replicated control plane before release; restores prove audit state | §7.3.6, §11.4, §12.4 | AC4; T51 |
| M-07 | The own-record entitlement laundered others' inputs in the same scope | Entitlement only for records built wholly from the owner's own records | §2, §7.3.4, §7.3.5 | AC1, AC7; T44 |
| M-08 | Curation and adapters were keyed on home scope, leaking foreign requirements | Curation and training are derivations; visibility needs the whole requirement closure; base vocabulary only tenant-readable concepts | §5.8, §7.3.5, §9.8 | AD1; T53 |
| M-09 | The bound leaked through overseer elevation and step 4; oversight transfer unfenced | Non-elevated reach, recomputed per scope; oversight transfer and overseer narrowing are restriction commits | §6.7, §7.3.4, §7.3.7, §9.4, §10.6.5 | AC3; T49 |
| M-10 | The 1a coordination record had no type, operation, lifecycle or conflict rule | Coordination control with `record_coordination`, §6.9 lifecycle and same-key conflict rule; one authority per commitment; “recorded”, never “in force” | §2, §4.3, §5.4, §6.9, §10.5.1, §10.6.3, §16; D-15 | CO1; T46, T55 |
| M-11 | Catch-up left superseded lines current; no scan bound; model notes shown as current | Catch-up applies the projection function to every gap commit or marks lines stale; scan budget; overlay split into change entries and labeled notes | §3, §10.5, §10.5.2, §10.5.3, §14.2 | OV1, OV3; T56, T57 |
| M-12 | Judgment status re-entered assessment through claims | Enforced at `submit_assessment` by ancestry; endorsements admitted explicitly; model claims are pointers | §4.3, §9.3, §10.5.3 | E3; T43 |
| M-13 | Role-holder statements could suppress flags; replay depended on live role state | Approval records only, with role evidence recorded at commit | §2, §4.3, §5.4, §9.7 | T33 |
| M-14 | Test-to-gate mapping broken; §15.2 omitted T43–T47 | T30 split by slice; T38 left to Gate 2; §15.2 covers T01–T58; tests added for D-8, D-12, D-13 paths | §15.1, §15.2, §16 | T30, T48–T58 |
| M-15 | Slice 1a was wider than in candidate 2 | Split into 1a-core and 1a-team, each gated | §16, §18.2; D-16 | — |
| M-16 | Adapters fell back at every expiry; vocabulary trigger retrained everything; vector dependency undefined | Deadline-aware training; concept-scoped triggers; query-side-only adaptation | §9.8, §14.2; D-11 | AD1; T35 |
| M-17 | Retention of published copies undefined | Copy follows target retention for owned ancestors; other ancestors' expiry propagates | §10.6.2, §12.1; D-12 | T52 |
| M-18 | “Dependency” used three ways; narrowing rule contradicted §8.2–§8.3; stale invariants | One vocabulary (ancestry edge, requirement, requirement closure); narrowing sentence restated; AC1 and C2 updated | §2, §5.5, §15 | AC1, C2 |
| M-19 | D-13 ambiguous on who is protected | No shortening path: reductions apply only to later records | §11.4, §14.2; D-13 | AC4; T24 |
| M-20 | Cue record, truth table, vocabulary pinning and required-processing status undefined | `ComparisonCue` record; prohibition truth table; per-statement vocabulary versions; flags never required processing; obligation absence reported as unscreened | §2, §9.7 | T32 |
| M-21 | Global consolidation mixed scopes | One invocation per scope; cross-area analysis homed by readability | §10.5.3 | — |
| M-22 | 1a overlay unbounded; raw R- and X-class text in L0 | 1a overlay from the last checkpoint; R and X events as locators only | §10.5.1, §10.5.2 | — |
| M-23 | Continuity warning noisy and missing from continuation | Checkpoints and items under a retention extension only; shown in task continuation | §10.5.5 | T47 |
| M-24 | Exclusion declarations and provenance revealed unlistable scopes | Declaration needs list rights or the coordinator role; opaque ancestry endpoints | §10.6.2, §10.6.4 | T58 |
| M-25 | Minor wording, figure, test and gate gaps | “Current at read” wording; overlay derived; slot attribution; T21 oracle; figures; decision rows marked in §14.2 (a full per-value origin column is not restored); deletion status lists copies; revocation-stage edges; Gate 0 MCP identity feasibility; C4-heavy tasks never exempted | §3, §7.3.7, §10.5.1, §13, §10.5.2, §10.6.2, §14.2, §15.2, §16 | T21 |
| M-26 | Change map and decision record inaccurate | A.4 corrected; alternatives column restored; decision history stated | §1, §18, §18.2, A.4 | — |

A same-family check of a draft of this candidate (findings K-01–K-20 and stale phrases S-1–S-20, by a Claude (AI) subagent) found further defects. Their repairs are folded into the rows above: deadline filtering of every narrative input, budget-bounded narrative coverage, deadline priority and the budget formula (M-03); scope-manager consent, target-bound confirmation, the `confirm_publication` operation, agent coordination records and fixed agent scopes (M-01, M-02); oversight self-transfer (M-05, M-09); commitment closure and explicit key linkage (M-10); slice exceptions and T48's move to Gate 1b (M-14); and the decision history in §18.2, where the owner then confirmed the reworded outcomes and decided D-17 and D-18 (M-26).

### A.6 Owner addition: multi-language support

Requirement from the product owner, 31 October 2026, after the interim review: memory may be written in any language; words with the same meaning share one language-neutral concept; the original words are always cited. Drafted by Claude (AI) and not yet reviewed by anyone. Changes: §5.9 (new), §5.1 (span language and script), §5.8 (per-language labels, `close_match`), §7.2 (no grounding from translation), §9.7 (`cross_language_mapping` cue), §9.8 (multilingual embeddings), §2 (language tag), §14.2 (pilot languages, detection), §15 (ML1), §15.1 (T59–T62), §15.2 (multilingual episodes), §16 (slice placement) and §18.2 (D-19).

## Appendix B. Related Work and Cited Sources

**Codex documentation cited by review candidate 1 (§14.1), not re-opened for this candidate:** [MCP](https://learn.chatgpt.com/docs/extend/mcp?surface=cli), [App server](https://learn.chatgpt.com/docs/app-server), [Hooks](https://learn.chatgpt.com/docs/hooks).

**Related work, named from the author's knowledge for reviewers to check; none was opened for this candidate, and none is evidence that UPMS achieves its results:**

| Work | Relevance |
| --- | --- |
| POSIX permissions and access control lists | Owner, group and other rights (§7.3) |
| W3C PROV | Provenance vocabulary for activities, use and generation (§5.5) |
| W3C SKOS | Concept labels and broader, narrower, related, exact-match relations (§5.8) |
| Wikidata data model | Statements with qualifiers such as point in time and location (§5.7) |
| Neo-Davidsonian event semantics | Events as entities with participant roles (§5.7) |
| Allen's interval algebra; TimeML | Time qualifiers and temporal relations (§5.7, §9.7) |
| Natural language inference models | Cross-slot contradiction candidates (§9.7) |
| CaMeL; Fides | Information-flow enforcement for agents and its security–utility tradeoffs (§8) |
| LoRA (Hu et al., 2021) | Low-rank adapters on a fixed base model (§9.8) |
| SISA training (Bourtoule et al., 2021) | Sharded retraining as an exact-unlearning option if full retrains become costly (§9.8) |
| RAPTOR (Sarthi et al., 2024); GraphRAG (Edge et al., 2024) | Hierarchical summaries for orientation and routing (§10.5) |
| Hippocampal indexing theory (Teyler and DiScenna, 1986); complementary learning systems (McClelland, McNaughton and O'Reilly, 1995) | Fast index over a slow archive; consolidation of gist over time (§10.5) |
| LongMemEval; LoCoMo | Public long-memory evaluation sets that may supplement §15.2 |
