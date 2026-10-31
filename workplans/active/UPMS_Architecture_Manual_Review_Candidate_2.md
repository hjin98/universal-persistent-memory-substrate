# UPMS Architecture Manual (Review Candidate 2)

Oct 31, 2026 · @Sam

## 1. Status, Authority and Scope

**Status: proposed D3 architecture, review candidate 2; not accepted-current and not implementation-qualified.** UPMS (Universal Persistent Memory Substrate) is a model-independent memory service for continuing project work by people and agents. It preserves observations, keeps revisable assessments, gives each reader a fast orientation map, and supplies an instrumented runtime with what it needs to enforce permitted use. It never infers permission from remembered text.

This candidate consolidates review candidate 1 (Codex's refined manual) with the round-2 amendments A1–A7 from the 30 October design discussion, as one coherent text. Its author's self-check is not the independent falsification required before promotion.

### 1.1 Inputs and their status

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Architecture Manual — Refined Candidate (review candidate 1) | SHA-256 `0ffc2740b4ec9088511754c1d2593262feff74d8bac6a1e39c4f37ab55ab4443` | Base text; its repairs F01–F18 are retained |
| UPMS Architecture Review (Codex) | SHA-256 `b0617a925916a130d47187917e54acd009ba3f367da29015c916ff94e8854f50` | Findings F01–F18 and their dispositions |
| UPMS Architecture Manual: Round 2 Amendments | Claude Docs artifact, 30 October 2026 | Amendments A1–A7; change rationale |
| Earlier architecture review of proposal v0.3 (R1–R7) | Appendix A | Closes the base text's “review not supplied” item |
| Product owner's instructions | This design conversation | Codex with OpenAI-family models first, Claude second; configurable retention; delegated initial defaults; decisions D-1 to D-11 (§18.2) |
| Software Design method | SSDP 7.2.1; no task `protocol_version` assigned | Form of this manual |

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
| Dependency | Restrictive dependency for information flow, deletion and recall, recorded by trusted capture or runtime or an approved deterministic transform | 5.5, 8.2 |
| Evidence relation | An attributed assessment of support, opposition or identity; never a permission edge | 5.5 |
| Publication | Owner's act of releasing an item into a target scope, removing dependencies only on scopes the owner owns | 10.6 |
| Lineage exclusion | Task-level rule excluding everything derived from named sources from a context | 10.6 |
| Snapshot position | Ordered canonical commit position for an assessment or read | 9.1 |
| Evidence epoch | Monotone revision of a scope's assessment-relevant collection | 9.3 |
| Restriction epoch | Monotone revision used to invalidate cached security eligibility | 9.4 |
| Handle | Principal- and scope-bound reference to a protected value; not an access capability | 8.3 |
| Release | Bytes or a command crossing the last UPMS-controlled boundary | 8.4 |
| Barrier | Durable restriction serialized with releases and descendant commits | 9.4, 12.3 |
| Flag, cue | A screening result and the reasons it gives the investigator | 9.7 |
| Adapter | Per-scope low-rank weights on a fixed small base model, held as a derived index | 9.8 |
| Hub | A derived overview page (L0, L1 or L2) with exact projections, a consolidated narrative and an overlay | 10.5 |
| Consolidation | Regional or global replay that rewrites hubs as one coherent piece | 10.5 |
| Coverage | Captured, indexed, processed, structured, screened, retained and instrumented extent actually available | 10.3 |

**Precedence.** The strongest applicable restriction wins: deletion and access denial block ordinary use; quarantine permits only its investigation route; correction prevents stale-current use but can permit qualified history; a task's lineage exclusion removes items from that task's context only; suppression affects proactive retrieval only. Admission never overrides a restriction. Permissions decide who may access a scope; restriction tags, purpose and barriers can only narrow that further. Current external policy controls each new decision; historical policy references explain history only.

## 3. Architecture at a Glance

**The mechanism in brief.** Three record types (Event, Claim, Judgment) and typed control records live in one memory core with a single committer per tenant partition. Two relation families keep meaning and data flow apart: evidence relations explain beliefs; exposure relations drive security, deletion and recall. Claims carry structured statements over a curated vocabulary, so deterministic code can screen for conflicts before an LLM investigates. Scope permissions decide who may list, read, write, curate, delete or manage memory. A derived overview layer gives every reader a small, current map, kept correct at each commit and made coherent by consolidation. Two integration profiles bound what can be claimed: a memory service guarantees scoped retrieval, correction and deletion; only an instrumented runtime can claim end-to-end information-flow properties. Permission to act always comes from external policy.

```text
Capture adapter ──events──▶  MEMORY CORE  ◀──proposals── Processing workers
(authenticates,             (single committer,           (extract, screen,
 marks spans)                barriers, permissions,       consolidate; propose
                             vocabulary)                  only, never commit)
                                  │ outbox: projections, hubs
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
| `submit_assessment`, `submit_screening`, `submit_overview` | Registered assessor or worker, assigned ruleset or schedule, complete attempt, dependency and epoch checks | Component role | Core computes the allowed transition |
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

No API accepts caller-chosen effective labels or admitted state, and no content changes a permission. Model assertions and conflict reports are data. A trusted detector may impose a restriction under policy; arbitrary claims of contamination cannot quarantine another user's corpus. Every mutation has a principal- and tenant-scoped request identity, an expected revision where applicable, and same-request, same-payload idempotency; reusing an identity with different arguments is an explicit conflict. MCP and other transports are adapters over this typed interface and inherit its authentication and scoping.

## 5. Durable Records

**Three semantic record types (Event, Claim, Judgment), typed controls, processing records, one typed relation store, structured statements on claims, and a versioned vocabulary make up all canonical state.** Manifests and dispatches are typed operational records, not a second knowledge ledger. Schemas specify meaning; serialization is D4.

**Common fields:** opaque logical ID and immutable revision ID; tenant; **home scope**; **owner**; authenticated capture or use purpose; schema version; commit position and time; retention-policy version and deadline; source classes; confidentiality restrictions; restrictive dependency reference. Fields that contain content or identifying metadata are protected payloads even when stored in a database column. Labels, locators, usernames, relation endpoints, policy references, query text, concept definitions and error text are not presumed public.

### 5.1 Event

```text
Event {
  channel, witness_principal, transmitter_identity?
  origin_identity?, origin_authentication_evidence?
  payload_ref
  spans: [{range, source_class, origin_ref?}]
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

Controls: correction, suppression, quarantine, redaction, deletion, endorsements, procedure versions and activation, policy references, dispatch intents and receipts, **scope-permission revisions, elevations and access records, publications, vocabulary changes, adapter promotions and overview consolidations**. Their state is derived from validated appended transitions.

```text
ProcessingRecord {
  kind, invoker, input_manifest_ref
  model_or_program_version, prompt_or_program_ref, configuration_ref
  output_ref?, outcome    // completed | partial | failed | cancelled | uncertain
  started_at, completed_at?
}
```

Attempts and outputs are separate immutable records. A timeout or crash never synthesizes completion. Reprocessing has a new identity. Required programs, transformations, reducers, vocabulary versions and screening versions stay available for replay of surviving records.

### 5.5 Relations and dependency closure

| Kind | Relations or records | Semantics |
| --- | --- | --- |
| Exposure and production | `observed_from`, `exposed_to`, `generated_by` | Trusted observations; source → invocation → output traversal supports forward recall |
| Evidence | `supports`, `opposes`, `same_as` | Assessor, exact endpoints, scope, locator, status and qualification |
| Statement content | `stated_reason`, `condition`, `exception` | What an asserter said; part of claim content (§5.7.2), never evidence |
| Lifecycle | Validated controls with `supersedes` and `retracts` links | Only an authorized transition changes current state; an agent-proposed link is inert |

Restrictive dependencies are object → prerequisite-revision references. A model output depends on its manifest's complete inputs; a dispatch depends on its arguments and the context that selected it; an adapter depends on every record it was trained on; a hub depends on every item it summarizes. Reverse traversal finds descendants. Pre-existing sources do not become descendants merely by sharing a manifest. Operational records and relations receive the restrictions of the information they expose.

Restrictive dependencies form a DAG over immutable production revisions. Cycles, nonexistent references, foreign-tenant edges and unvalidated narrowing are rejected. The only narrowing operations are the deterministic transforms specified and tested in this manual: certified redaction copies (§12.2) and owner publication (§10.6.2). Evidence relations may be cyclic and are traversed with visited sets and limits. Closure indexes are derived accelerators. Missing closure, incomplete runtime coverage or a traversal timeout is not proof of independence: the affected use or scope is contained. Dependency validation and barrier checks are synchronous at commit and release; background graph expansion is not the safety mechanism.

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
  deontic:     prohibited | required | permitted
  pattern:     event_type | (entity_type, property)
  constraints: conjunction of comparisons on properties and qualifiers
               (=, ≠, <, >, ∈, weekday, interval relations)
  exceptions:  patterns
  scope, authority_ref        // the actual authority source
}
```

The operator set is fixed and small. Nested quantifiers, defaults such as “usually,” counterfactuals and vague thresholds are not structured; such a rule stays source-linked text with `structure_status: partial`. A rule in memory never enforces anything: matching produces flags only (§9.7), and the governing policy stays with its authority.

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
  preferred_label, aliases[], definition
  relations: exact_match[], broader[], narrower[], related[], replaced_by?
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

**Scope.** The tenant has a base vocabulary readable by all users. Each scope may extend it; a scope's concepts and definitions are scope content under §7.3, because a definition can disclose information. Statements record the vocabulary version they were extracted with.

**Governance.**

- Proposals are inert. When extraction meets an unknown term, it proposes a new concept or a mapping to the nearest existing one; the proposal takes effect only after curation by a holder of `c` or `m` on the vocabulary's scope, or by an accepted deterministic rule.
- Merges and splits are reversible, like entity `same_as`. Every merge re-screens the slots it joins (§9.7).
- Deprecation keeps recognition: a deprecated term remains an alias mapped through `replaced_by`, so old memories stay retrievable and comparable, while extraction and display prefer the current label. A term is removed only when no retained memory uses it.
- Every change produces a new vocabulary version; derived indexes record the version they were built with and rebuild when it changes.

**Initial vocabulary.** Project-work concepts only: tasks, decisions, components, configuration values, deadlines, people and roles, and events such as release, deploy and review. It grows by curated additions, not by agents minting properties freely.

**Expansion (adaptation tier A).** Indexes and queries expand terms with preferred labels and definitions: “HAS” is embedded as “HAS (Historical Applicability Set).” Off-the-shelf retrieval models then understand domain jargon immediately, deterministically and without training.

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
| Grant or widen | `m` on the scope, or elevated administrator | New permission revision; effective immediately |
| Narrow, remove member, transfer ownership | `m`, elevated administrator, or identity-provider membership change | Restriction commit under §9.4; acknowledged only after the release fence |
| Elevation opened | Administrator role; re-authentication; reason; scope; duration ≤ profile limit | Elevation record; access records for every content access during it |
| Elevation ended | Expiry, explicit end, or role revocation | Restriction commit; pending releases relying on it are withheld |

### 6.8 Publication

`published → superseded | withdrawn`. Publication creates a new attributed revision in the target scope (§10.6.2). Superseding names the revision being replaced and is recorded as a conflict if that revision has changed. Withdrawal is a retraction in the target scope; readers who already saw the item are not “unseen.”

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

Grounding means an exact, canonically resolved value is authorized **for this argument role and operation**, through a trusted task-intent binding, a connector field declared authoritative for that role, a valid exact-use reliance endorsement, or explicit dispatch confirmation. Mere occurrence of the same string in an A or C span is insufficient. Relative paths resolve against a bound root, symbolic links at use, recipients and accounts against their actual identity, URLs through the controlled network path. Ambiguous resolution blocks the action. The runtime enforces this; the model only proposes.

| Class | Examples | Initial integrity rule (capability, confidentiality and barrier checks always apply) |
| --- | --- | --- |
| C0 | Scoped memory read | Authorized scope, rights and purpose; bounded read |
| C1 | Reply to the requesting principal | Recipient may receive every restriction; retrieved material rendered as attributed data |
| C2 | Memory proposal or isolated draft | Restricted artifact in authorized storage; an arbitrary filesystem write is not automatically C2 |
| C3 | External disclosure, fetch, message, contracted tool write | Role-bound grounding; policy permits influencing sources; X-influenced outgoing payload requires exact-payload confirmation by default |
| C4 | Irreversible, financial or permission-changing operation | C3 requirements plus per-action confirmation by the authorized principal |

Confirmation shows normalized operation, effective target, payload, consequences and qualifications. It is nonce-bound, single-dispatch, time-bounded and invalid after any argument or revision change. Capability is separate from task intent. Conservative provenance plus grounding does not guarantee semantic obedience; end-to-end action quality remains an evaluated limitation.

**Public-reader exception.** A registered, explicitly enabled public browsing operation may waive target grounding and X-payload confirmation for an isolated public reader with no private inputs, credentials, cookies, authorization headers, local files, internal-network reachability or persistent privileged provider state. All bytes and observable request choices must be eligible for public disclosure. The broker allows only contracted public HTTP(S) reads, bounds redirects, size and time, and revalidates destination addresses at connection time and on every redirect; DNS rebinding, loopback, link-local, metadata services and private destinations are denied. Public GET is not assumed effect-free. **Disabled in the initial pilot until qualified.**

### 7.3 Memory access control

**UPMS owns which principals may list, read, add to, curate, delete and manage memory in each scope.** Permissions are control records changed only through authenticated operations. **Fixed (proposed).**

#### 7.3.1 Principals

- **Human users**, authenticated by the identity provider.
- **Groups**, whose membership the identity provider owns (pilot: built-in directory behind the same interface; *pending D-4*).
- **Agent principals**: persistent agent identities with their own scopes and a designated human **overseer** (*pending D-7*).
- **Service principals** (capture, workers, purge controller, index and adapter builders), governed by component roles (§4.3), not scope permissions.

An agent session acting for a principal holds the intersection of that principal's rights and the session's grant, and never elevates. “Other” means every human user of the tenant.

#### 7.3.2 Scopes and ownership

Every record has one home scope and one owner: the principal it was captured for. Output of an agent principal is owned by that agent; output of an agent session acting for a user is owned by the user. Permissions attach to scopes, not individual records; a record's restriction tags may narrow access but never widen it beyond its scope. Scopes may have a parent for organization: a parent's permissions are copied as defaults when a child is created, with no live inheritance, so moving a scope never silently changes who can see it (*pending D-3*).

#### 7.3.3 Rights

| Right | Linux analog | Allows |
| --- | --- | --- |
| `l` list | directory read | Knowing an item exists; non-content metadata; appearing in counts, coverage, flags and overviews |
| `r` read | file read | Retrieving content, for the principal and its agent sessions; implies `l` |
| `w` write | file write | Adding memories; correcting, redacting or deleting own items; proposing corrections and concepts; publishing own items |
| `c` curate | — | Acting on others' items: attributed corrections, scope suppression, resolving proposals, curating vocabulary |
| `d` delete | write on parent, sticky bit off | Deleting others' items |
| `m` manage | `chmod`, `chown` | Permissions, ownership, scope retention, procedure activation, child scopes |

Displayed Linux-style, for example `owner lrwcdm · group lrw--- · other ------`. `w` without `r` is valid (a drop box): a contributor then reads only its own items. Writing never overwrites; every change appends an attributed record.

#### 7.3.4 Evaluation

For principal *p*, operation *o* and target *t*, in order:

1. If *p* is an elevated administrator for *t*'s scope, apply 7.3.6.
2. Rights on the home scope are the **union** of every matching entry: owner, named principal, each group containing *p*, other.
3. For an agent session, intersect with the session grant.
4. For a derived item, require the needed right (`r` or `l`) on **every** scope in its restrictive dependency closure, against current permissions (7.3.5).
5. Apply all other checks unchanged: restriction tags, authenticated purpose, quarantine, correction state, barriers, processor rules, and the task's lineage exclusions.

There are no deny entries; exclusion uses narrower groups. Linux's owner-precedence rule is deliberately not copied. Unknown membership or permission state denies (§13).

#### 7.3.5 Derived and cross-scope memory

A derived item is readable only by principals who can read all of its sources. If an agent reads a team scope and saves a summary in a personal scope, a teammate without access to the personal scope cannot read it, and the owner loses it upon leaving the team (*pending D-6*). A fresh restatement by the user is a new memory without the old dependency. Owner publication (§10.6.2) is the only operation that releases a dependency, and only on scopes the publisher owns.

#### 7.3.6 Administrator

**Authority:** every right in every scope of the tenant, ownership transfer, and retention within tenant limits.

**Use:**

- The administrator role is assigned in the identity provider; UPMS cannot grant it.
- Administrators act with ordinary rights by default; admin power requires an explicit **elevation** with a reason and scope, lasting at most the profile limit, after re-authentication.
- Every content access or change during elevation creates an access record, which administrators cannot delete; only its retention policy removes it.
- Reading a personal scope while elevated notifies its owner (*pending D-1*).
- Agent sessions never inherit elevation (*pending D-2*).
- Bulk destructive operations (whole-scope deletion, tenant-wide retention cuts) require confirmation and a cancellable delay.

**Limits that bind administrators too:** no reading past a deletion barrier; no records attributed to another principal and no forged source class; no direct setting of labels, admission or history; no bypass of quarantine isolation; no disclosure to restricted processors; no granting of tool capabilities; no self-assignment of the administrator role.

#### 7.3.7 Revocation and offboarding

Narrowing permissions, removing a group member, transferring ownership and ending an elevation are restriction commits under §9.4: the restriction epoch advances, acknowledgement waits for the release fence, and pending outputs that relied on the revoked access are withheld. Content already released cannot be unseen. Membership changes propagate within the profile bound (§14.2).

When a user leaves, their contributions to shared scopes remain with attribution under the scope owner; their personal scope is deleted at the end of its retention period unless an administrator transfers it. An agent principal's scope follows its overseer's decision.

#### 7.3.8 Default permissions

| Scope type | Default |
| --- | --- |
| Personal | owner `lrwcdm`; nobody else |
| Agent principal (private) | agent `lrwcdm`; overseer `lr` plus `d` (*pending D-9*); nobody else |
| Team or project | lead `lrwcdm`; members `lrw`; other none |
| Organization-wide | managers `lrwcdm`; contributors `lrw`; all users `lr` |
| Agent-operational (runtime state) | owning principal only |

### 7.4 Confidentiality and purpose

Restrictions are conjunctive: every tag must permit the recipient, processor, destination and authenticated purpose. Derived data inherits the union. A result spanning several scopes may therefore be unusable; isolate the work instead of dropping tags. Read permission, factual endorsement and summaries never declassify. **Declassification is disabled in the pilot, except owner publication, which releases dependencies only on scopes the publisher owns (§10.6.2).** Processor identity includes the actual account, region or endpoint, retention mode and downstream handling where material, not just a vendor name.

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

Every opaque model invocation's outputs inherit all runtime-visible inputs: instructions, messages, retrieval, overview hubs, tool results, images and files, procedures, summaries and compaction, prior session state, and model-visible handle metadata. A segment's dependency set grows monotonically until a validated reset. A deterministic non-model transformation may narrow dependencies only through a specified and tested contract; citations, schema validation and model judgments cannot.

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

**Initial rule:** the core maintains a conservative evidence epoch per scope. Any committed source addition or revision, claim, statement, evidence relation, correction, relevant lifecycle change, entity-resolution change, vocabulary merge or ruleset assignment that can affect assessment advances the scope epoch in the same transaction. Unknown relevance invalidates the whole affected scope. Publishing a judgment, a flag or an overview, or completing a processing attempt, does not advance it. Cross-scope evidence captures every participating scope's epoch.

An assessment binds a snapshot, exact read revisions, assigned ruleset and scope epochs. Admission requires unchanged revisions and epochs at commit; if evidence arrived between snapshot and commit, the assessment is kept as historical or evidence-only and reassessment is queued. Unprocessed new evidence also invalidates: pending extraction cannot hide an opposition window. Basic recall never waits for deep processing.

At every current-state presentation or protected reliance, the effective judgment must still match current scope epochs, rule assignment, validity interval and the maximum age bound, with no unresolved required processing or reassessment; otherwise it is shown as evidence-only with qualifications, or the dependent action is blocked. The epoch comparison is the safety condition; the reassessment queue is only liveness. Capture time is not freshness time.

Slot-level epochs (§9.7) may replace scope epochs **only after** an invalidation contract covers vocabulary merges, entity-match changes, rule changes and the candidate channel, and race scenarios T01 and T19 pass at slot level. Until then, scope epochs remain the safety condition; their availability cost is measured first. Timeouts and unknown scopes make an assessment stale, never fresh. External current-state claims also need source-owner refresh or preconditions.

### 9.4 Barriers and the release race

The core owns restriction epochs and orders restriction commits with final controlled releases; a check followed later by an uncoordinated socket or file write is insufficient. **Restriction commits** include corrections, deletions, permission narrowing, group-membership removal, ownership transfer and the end of an elevation.

For each, the target restriction is published and the affected epoch advanced synchronously. Cached eligibility is invalid immediately; derived descendants (statements, flags, hub lines, adapters) are rejected through validated dependency closure even before purge or index jobs run. A bounded closure failure contains the affected scope. No new ordinary descendant of a deletion-blocked input may commit; restricted cleanup and audit transitions remain possible without re-serving content.

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

**Slot conflicts.** Statements are indexed by slot: (entity or `same_as` cluster, property). A pair in one slot is flagged when (1) the subjects are the same entity or a `same_as` candidate; (2) the property is single-valued; (3) valid time and place overlap or are unknown; (4) the values are incompatible under the property schema; and (5) polarity and modality are comparable — both asserted, or a negation against an assertion; a quotation is not compared with an assertion. Event statements are compared likewise when their type declares that two events cannot coexist.

**Rule matching.** Every intended, committed or recorded event is matched against active rules in its scope (§5.7.3), including through `broader` relations: a release matches a rule about deploys if release is narrower than deploy. A match without recorded exception evidence raises a flag.

```text
Flag {
  statements[] | (statement, rule), severity  // definite | possible | adjacent
  cues[]:  missing_qualifier(time | place) | entity_match_uncertain
           | value_refinement | value_adjacent | different_dimension
           | modality_or_attribution_differs | recent_vocabulary_merge
           | missing_exception_evidence | source_class_differs
  screening_version, vocabulary_version, inputs_watermark
}
```

Severity is ordinal and rule-based, not a probability: definite when every condition holds with all qualifiers known; possible when a qualifier or entity match is unknown; adjacent when values are close in the value space. Cues tell the investigator where to look: two “sky” statements with overlapping times and no place get `missing_qualifier(place)`, `entity_match_uncertain` and, for blue against dark, `different_dimension`.

**Candidate channel.** Slot comparison is high-precision and low-recall. A probabilistic channel proposes cross-slot candidates using embedding similarity and a small contradiction model (§9.8); its outputs are recorded processing records shown as candidate flags, separate from deterministic flags.

**Resolution and visibility.** Screening never resolves, refutes, supersedes or admits a claim. Every flag goes to investigation, whose result is a Judgment (§5.3, §6.2). A flag is visible only to principals who can read both flagged items. Text-only statements are not slot-screened, and coverage says so.

### 9.8 Processing cascade and adaptive models

**Language processing runs deterministic code first, small local models second and the LLM last, only where needed.** Small models may be adapted to a scope's jargon through adapters held as derived, deletable, permission-bound indexes. Domain adaptation is in scope by owner decision D-11.

| Tier | Runs | Jobs |
| --- | --- | --- |
| 1. Deterministic | Rule-based NLP and normalizers | Base word forms, dates and times, units, exact vocabulary lookup, schema validation |
| 2. Small local models | Sentence-embedding model, entity tagger, small classifiers, small contradiction model | Retrieval embeddings; candidate concepts for unknown terms; entity mentions; sentence routing (fact, rule, rationale, chit-chat); negation and hedging; cross-slot candidates; significance proposals for overview updates |
| 3. LLM | Extraction, investigation and consolidation model | Full structured extraction; ambiguity resolution; flag investigation; overlay notes and consolidation |

**Fixed (proposed):**

- Lower tiers propose and route; outputs are processing records with model version and inputs. They may add restrictions and never grant anything.
- A router's decision to skip extraction never drops text; the item is reported as not structured.
- Tier 2 runs locally by default, so restricted memory need not reach an external processor.
- A tier-2 score that gates a consequential outcome without tier-3 or human confirmation needs measured error rates first (a D2 reopen trigger, §1.4).
- Tier 2 starts with embeddings and one contradiction model; other classifiers are added only when evaluation shows the LLM extractor is too slow, costly or inconsistent.

**Two adaptation tiers.** Tier A is vocabulary expansion (§5.8): immediate, deterministic, no training. Tier B is per-scope low-rank adapters (LoRA or similar) on a fixed base model, for domain sense expansion cannot capture; it ships only if it beats tier A on the scope's probe set.

**Adapters as derived indexes.** An adapter is versioned, records its training snapshot, and has restrictive dependencies on every record it was trained on. **Fixed (proposed):**

- **Per scope.** An adapter is a lossy compressed copy of its training text; only principals with `r` on every training scope may use it. Cross-scope search queries each scope's index with its own adapter and merges ranked lists, never raw scores.
- **Training data** comes only from the curated vocabulary (aliases as positives, related-but-different concepts as hard negatives), user corrections and endorsements, and validated or confirmed extractions. Excluded: X-class content, unconfirmed model output, retrieval feedback, quarantined items and other scopes, so planted jargon cannot shift a team's retrieval.
- **Retrain from scratch on trigger:** vocabulary version change, a threshold of newly approved aliases, a probe-accuracy drop, a training-source deletion, or global consolidation (§10.5). Training uses pinned seed and versions.
- **Promotion gate.** Promote only if the adapter beats both the current adapter and the base model on the scope's probe set and a general regression set, with no regression beyond the preregistered margin; variants tried are recorded (§15.2).
- **Re-embedding.** A new embedding adapter changes the embedding space, so the scope's vectors are rebuilt in the background and swapped atomically. If that becomes too costly, query-side-only adaptation is the fallback.
- **Deletion.** Deleting a training source blocks every adapter trained on it at the barrier. Serving falls back to the newest adapter whose snapshot predates the deleted record, or the base model, and a retrain from surviving data is queued (§14.2).
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

**A model with no context starts from a small, current map of the memory, never from the archive.** The overview layer is a derived hierarchy of hubs acting as summary, index and router: a blank model reads its root hub first and descends only where its task leads. It follows the arrangement described by hippocampal indexing theory — a compact index over a large archive, with understanding consolidated over time rather than rebuilt at every recall. **Fixed (proposed).**

```text
Blank model                                                  Commits flow up:
reads down   L0  Root hub per reader (≤ 1,500 tokens)          ▲  exact lines and
    │            active work, decisions, obligations, routes   │  overlay at once;
    │        L1  Area hubs, one per scope or project           │  narrative waits
    │            state, decisions, open questions, rules       │  for consolidation
    │        L2  Entity and topic pages                        │
    │            slot tables, timelines, conflicts, sources    │
    ▼        Archive: events (original text), claims and statements,
                      judgments, controls
L0 is assembled per reader from hubs of scopes they may read.
```
*Figure: Reads go down the map; updates flow up it.*

A blank model reads down from L0 and pulls sources only when needed. Every commit updates hubs' exact lines and overlays at once; the narrative is rewritten only by consolidation.

#### 10.5.1 Levels

| Level | Contents | Budget | Built per |
| --- | --- | --- | --- |
| L0 root hub | What this memory serves; active work; decisions and obligations in force; open conflicts and blockers; significant recent changes; routes to areas; glossary pointer (§5.8); coverage and as-of | ≤ 1,500 tokens (initial default) | Reader, assembled at read time |
| L1 area hubs | Current state, decisions with status, open questions, rules in force, key entities, timeline highlights, routes to L2 | ≤ 3,000 tokens each | Scope or project |
| L2 entity and topic pages | Slot table of current values per property with qualifiers (§5.7); event timeline; open flags (§9.7); links to sources | Bounded per page | Scope |
| Task checkpoints | Objective, confirmed work with evidence, decisions, open questions, obligations, blockers, artifacts, next steps | Checkpoint share | Task or session |
| Archive | Events, claims and statements, judgments, controls | — | — |

#### 10.5.2 Hub content

Each hub has three parts:

- **Exact projections**, computed deterministically from statements, controls and the vocabulary through the outbox at commit: current slot values, open obligations, decisions and status, rules in force, flags, recent changes, routes. Current to the reader's consistency token.
- **Consolidated narrative**, written by an LLM during consolidation: the understanding, the “why” and the shape of the work. Stored as sentences, each linked to the statements or sources it summarizes, and labeled with its consolidation watermark.
- **Overlay**, the clearly labeled “since consolidation” list of later significant changes, as exact entries or short source-linked notes.

#### 10.5.3 Synchronization and consolidation

**The overview is correct at every commit and becomes coherent through consolidation: correctness never waits, coherence does.** Fast updates never edit the consolidated narrative piecemeal, because many local edits fragment it; they accumulate in the overlay, and consolidation — a regional or full replay that rewrites summaries as one coherent piece — absorbs them. This mirrors the complementary roles of fast and slow memory, with consolidation as the sleep phase.

| Mode | When | What it does | LLM? |
| --- | --- | --- | --- |
| Synchronous projection | Every commit, through the outbox | Recomputes exact lines; adds the change to the overlay; withholds narrative sentences whose sources were corrected, deleted or made unreadable | No |
| Overlay note | When a significant change reaches a hub about to be read, or at the end of a task | Adds a short source-linked note to the overlay; never edits the narrative | Optional, bounded |
| Regional consolidation | When a region's fragmentation crosses its threshold; idle time; nightly for active areas | Full replay of the region's L2 pages and sources, old and new together; rewrites its hubs as one piece; absorbs and clears the overlay | Yes, batched |
| Global consolidation | Weekly, or after several regional passes | Rewrites L1 summaries across areas and the L0 sections; finds cross-area connections and contradictions; reorganizes areas; triggers adapter retraining (§9.8) | Yes, batched |

- **Overlay, not edits.** Between consolidations the narrative does not change; readers see it with its watermark, followed by the overlay. The narrative stays coherent and the overlay stays honest about what is new.
- **Fragmentation drives consolidation, not only the clock.** Each hub tracks overlay size, withheld sentences, age, and contradictions between narrative and exact lines — found by extracting statements from the narrative and screening them against the projections (§9.7). Crossing a threshold schedules regional consolidation.
- **Full replay, interleaved.** Consolidation re-reads old and new material together, not only the delta; replaying only the new would overweight recent events.
- **Bottom-up order.** Regions consolidate from L2 to L1; global passes then rewrite L0 sections from consolidated L1, so upper levels are never rebuilt from stale lower ones.
- **Significance.** Decisions, rule changes, obligations, commitments, conflicts and flags, corrections, deletions and publications always propagate upward; routine items stay at L2 unless retrieval demand or explicit priority raises them. A small classifier may propose significance; deterministic rules decide.
- **Understanding as an output.** Consolidation also proposes what deserves to be learned: recurring patterns, lessons from dead ends, cross-area dependencies, emerging rules, vocabulary changes. Each is a `hypothesized` claim attributed to the consolidation run, linked to its supporting instances, and evidence-only until judged or endorsed.
- **Guarding against consolidation errors.** Consolidation compresses and reorganizes, and human sleep shows the risk: gist strengthens while schema-consistent false memories appear. So the archive stays verbatim; every rewritten sentence is source-linked; generalizations are labeled; the new narrative is screened against exact projections before it replaces the old one; and the diff from the previous consolidation is recorded.
- **Stability.** Structure and wording are kept where facts have not changed, so agents relying on a hub are not disoriented; churn is measured.
- **Fast and slow learning.** The archive and overlays play the fast, episodic role; consolidated hubs and per-scope adapters play the slow role.
- **Piggybacking.** At the end of a task, the working agent's checkpoint becomes overlay notes for its area at little extra cost; consolidation checks them against sources.

#### 10.5.4 Maintenance cost

**Maintenance cost scales with the amount of change, not the size of the archive, and has its own budget so it never competes with the work it supports.**

- Synchronous projection is database work and overlay notes are small; consolidation is the main LLM cost, spent deliberately because it buys coherence.
- A regional pass reads one area's L2 pages and sources; a global pass reads consolidated L1 hubs, not the archive. Quiet regions are not reconsolidated.
- L0 is composed per reader deterministically from per-scope sections, so the LLM writes each scope's section once, not once per reader.
- Cheapest adequate model per job: deterministic code for projections, small models for significance, a smaller LLM for overlay notes, the strongest model at batch rates for consolidation.
- Maintenance has its own quota below task work, with part reserved for consolidation (§14.2). Correction, deletion and permission invalidation is deterministic and never budget-limited.
- When the budget is spent, the narrative stays coherent but ages and the overlay grows, both labeled. Coherence and freshness degrade; correctness does not.
- Measured: maintenance-to-work cost ratio, overlay size and withheld sentences at read time, narrative-versus-projection contradictions, churn, and cold-start success (§15.2).

#### 10.5.5 Per-reader assembly, trust and routing

Hubs are built per scope. L0 is assembled at read time by deterministic composition of the per-scope hub sections the reader can read; no stored hub mixes scopes unless every reader could read all its sources. Task lineage exclusions apply at assembly. Areas the reader cannot list are not mentioned, not even as counts.

Hub content is derived: every line links to its sources and carries their source classes; no hub is authority or evidence for admission. A stale hub is history, not current state, and its expiry never fulfills an obligation. Each hub carries route entries (area, key concepts, pointers); the router matches a task's terms to routes using the vocabulary, entity registry and hub embeddings, descending one level at a time with a bounded budget per step. Direct search remains available; the map is a shortcut, not a gate.

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

`publish(item, target_scope)` moves private work into the shared pool:

- The publisher must own the item and hold `w` on the target scope.
- It commits a new attributed revision in the target scope, linked to the original.
- It releases restrictive dependencies **only on scopes the publisher owns**; dependencies on other scopes (a confidential client document the publisher read) stay attached and still restrict readers. This is the one exception to “no declassification in the pilot” (§7.4).
- Source classes and provenance survive; a published item derived from external content says so.
- Published items are evidence-only for the team unless a human endorses them.
- Withdrawal is a retraction (§6.8); readers who already saw the item are not “unseen.”

#### 10.6.3 Publication categories

Agents tend to share successes and keep failures, building survivorship bias into shared memory, so some categories are required (*pending D-8*):

| Category | Default |
| --- | --- |
| Ownership claims, decisions, interface agreements, commitments, blockers | Published immediately |
| Findings and results | Published when stable, at a checkpoint |
| Dead ends and failed attempts | Required publication at the next checkpoint |
| Scratch reasoning, hypotheses in progress | Private or team-readable pull-only |

Decisions made in a temporary coordination channel are captured as decision records in the shared pool by the participant who made them.

#### 10.6.4 Lineage exclusion and blind work

A task may declare lineage exclusions, such as “nothing derived from the author's implementation segment.” Context assembly and overview assembly enforce them through restrictive dependencies, whatever scope an item lives in, so publishing to the shared pool cannot leak around them. A **blind phase** has an explicit end, after which exclusions lift so workers can reconcile. Its manifests support an **independence attestation**: no input derived from the excluded lineage, within instrumented coverage. The attestation excludes rationale carried inside the artifact (code comments, commit messages) and channels outside UPMS, and says so.

Useful for independent review and falsification, parallel exploration that should not converge early, independent estimates or replications, held-out evaluation hygiene, and red-team versus blue-team work. In each, what is excluded is another worker's conclusions and reasoning, not the governing requirements.

#### 10.6.5 Shared-pool concurrency and oversight

Shared items are appended and attributed, never overwritten. Superseding names the revision being replaced; if it changed first, the attempt is recorded as a conflict. Conflicting findings stay side by side until resolved, and screening (§9.7) flags them. Overlays and checkpoint reconciliation report when an item a worker relied on was superseded.

An agent principal's private memory is private from peers, never from its overseer (*pending D-9*). Agents keeping memory their operators cannot inspect is an oversight problem, not a coordination feature.

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

The minimum restrictive lineage is kept while surviving objects require it; removing links for space never makes a live descendant independent. When all affected descendants are purged, sensitive source links and labels are stripped from audit skeletons, keeping only permitted minimal receipts. Recall coverage ends with retained lineage.

### 11.3 Incident recall

Given a source, credential, procedure, processor, ruleset, vocabulary version or adapter identity, recall traverses restrictive dependencies and, separately, evidential dependence. It returns authorized affected records, manifests, outputs, dispatches, outcomes, procedures, hubs and adapters; distinguishes possible influence from causal proof; and lists processing, instrumentation and retention gaps, uncertain effects and destinations outside local control. No report grants permission to expose another scope's records (recall output is filtered by the investigator's rights) or to undo an external action. Recall can schedule authorized reassessment, quarantine, re-consolidation or adapter retraining through normal interfaces.

### 11.4 Access records

Elevations, and every content access or change during them, produce access records: principal, elevation reference, operation, opaque target identity, time and outcome, with no content. Owners of personal scopes can see access records for their scopes (*pending D-1* for notification). Administrators cannot delete access records; only their retention policy removes them (§14.2).

## 12. Retention, Redaction, Deletion and Portability

**Deletion is a staged lifecycle: a durable serving barrier takes effect at acknowledgement, purge follows across every surface, and completion is reported only for what was actually satisfied.**

### 12.1 Deletion units, surfaces and rights

Default source unit: event revision; default derived unit: object revision. Unusually large or mixed-policy inputs are split into declared units at capture. Every content-bearing representation is covered: raw and normalized text, statements, embeddings, summaries, overview hubs (narratives, overlays, projections), adapters, prompts, fragments, handles, indexes, query and response caches, staging files, logs, journals and WAL, replicas, backups and managed exports. Restricting the original object alone is insufficient.

**Who may delete:** own items with `w`; others' items with `d`; administrators while elevated; retention policy. A deletion cascades through restrictive lineage to descendants in scopes the requester cannot see, without disclosing them; their owners see only “an input is unavailable.”

Retention is versioned policy per tenant, scope and category with effective deadlines and a deletion plan. More restrictive applicable deadlines win. Reads never renew retention silently. Longer retention requires an authorized explicit change before expiry; nothing resurrects erased bytes. A retention change cannot silently purge an unexpectedly broad corpus: it shows scope, counts the actor may see, affected continuity and effective date, then applies the authorized transition, with a cancellable delay for tenant-wide cuts (§7.3.6). Retention expiry uses the same barrier and purge evidence as explicit deletion.

### 12.2 Redaction without self-deleting the replacement

`redact(event_revision, spans)` is an authorized deterministic copy-and-erase transaction, not model rewriting. Exact byte and span boundaries and authority are validated; a new protected revision containing only retained spans, with mapped provenance, is staged. Publishing the replacement and applying the original revision's deletion barrier happen atomically; no acknowledgement occurs until both are durable and the release fence is complete.

The certified retained-span copy is an explicit, narrow dependency exception: a new source unit, not an ordinary descendant of the whole original for erasure propagation. It keeps the original's confidentiality and purpose restrictions; redaction never declassifies. The protected redaction control records input and replacement identities and transform version for audit, without reintroducing removed bytes. No model, arbitrary program or caller can use it to strip dependencies. Retained-byte equality and removed-byte exclusion are acceptance properties. Every pre-existing descendant of the original (statements, flags, hub lines, adapters) is still withheld or purged and regenerated from the replacement or independent surviving sources.

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

Deletion, revocation and permission-narrowing control history lives in a separately durable recovery control plane under the same logical core authority, outside ordinary data-backup rollback, with authenticated checkpoints, monotone positions and redundant copies. A restore must prove it has the latest applicable control state and enforce it **before** any serving or new derivation; otherwise it stays closed. Data restore alone cannot resurrect access. Tombstones outlive every compatible backup, export or replica that could reintroduce the target; identity reuse is forbidden.

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
| Consolidation fails, is deferred or exhausts its budget | Hubs keep their last narrative, current exact lines and overlay, all labeled; correctness unaffected |
| Consolidation output fails screening against projections | Previous narrative stays; the failure is recorded for review |
| Adapter blocked by deletion, or retraining fails | Serve the older qualifying adapter or the base model; report reduced retrieval quality |
| Dependency cycle, missing reference or traversal limit | Reject the unsafe commit or use; contain the uncertain scope |
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

These values are **agent-chosen planning and qualification targets** under the owner's delegation, not benchmark results, legal conclusions or approved policies. Configuration is schema-validated, versioned, audited and attached to every evaluation; changing a material binding invalidates only affected evidence. Overrides may tighten defaults; increasing exposure, relaxing an invariant or broadening scope requires the owning decision.

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
| Overview synchronization | Exact lines and overlay at every commit; regional consolidation when a hub's overlay exceeds 20% of its token budget, 10 withheld sentences or 7 days, and nightly for active areas; global consolidation weekly |
| Maintenance budget | ≤ 15% of the tenant's task-model tokens over a rolling 7 days plus a daily cap, at least half reserved for consolidation; invalidation exempt |
| Adapter retraining after training-source deletion | Within 24 h; older qualifying adapter or base model serves meanwhile |
| Raw source retention | 180 days from capture; an explicit authorized pin may extend |
| Durable user-approved task records | 365 days or a shorter scope policy; dependencies must also be lawfully retained, or the record becomes unavailable |
| Derived artifacts and handles | No later than the earliest required input deadline; handles ≤ 1 h and current segment eligibility |
| Rendered context window | Replay-only copies up to 7 days, shortened by any input's policy or deletion; novel canonical inputs keep their own deadline |
| Operational lineage | 180 days, and as long as a surviving dependent requires it within policy |
| Access records | 1 year |
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

No one-year task record silently extends a source's 180-day retention: either an explicit permitted extension covers its inputs, or the derived record expires or becomes unavailable. A user's fresh independent statement can be a new source event; presenting old model text for endorsement does not erase its dependencies. Retention controllers use server-recorded capture time and trusted current time; clock uncertainty never prolongs a security lease or falsely certifies expiry.

### 14.3 Storage and deployment

**Initial default:** PostgreSQL for canonical records, permissions, vocabulary, outbox and adjacency tables; protected payloads in object storage; derived lexical and vector indexes, hubs and adapters as derived artifacts. No dedicated graph database, event bus, universal confidence service or general policy engine inside UPMS; the scope-permission evaluator is data-local authorization, like a filesystem's. A small deployment may colocate trusted components, but access paths and process isolation must match the threat model. Identity, policy and KMS may be integrated providers behind their interfaces.

Per-object data-key envelopes and encrypted backup expiry follow §12.4. Concrete KMS and storage products, supported schema versions and availability layout are D4 choices if they meet these contracts; qualification establishes real key caching, backup, restore and deletion behavior. Tenant partitioning is not itself isolation. Searchable plaintext, embeddings, adapters, hubs and diagnostic metadata remain sensitive.

Timing and resource side channels, administrator access and provider-held data are explicit residuals. Before multi-user release, semantic isolation is tested and cross-scope timing leakage measured under the chosen index, cache and adapter design. A stronger noninterference promise needs an accepted stronger profile and evidence.

## 15. Invariants and Acceptance Evidence

**These are planned acceptance obligations, not executed tests; every applicable invariant must hold, and a better aggregate metric never compensates for a known violation.**

| ID | Acceptance property | Owner | First slice |
| --- | --- | --- | --- |
| H1 | Ordinary semantic state appends; erasure is explicit, scoped and audited | 5–6, 12 | 1a |
| H2 | Claim, statement and judgment provenance resolves to retained records or explicit unavailability | 5, 9.6 | 2 |
| E1 | Capture, assessment, admission, provenance and permission stay distinguishable | 5–7 | 1a; full assessment 2 |
| E2 | Authorized conflicts stay visible; independent evidence is never silently suppressed | 5.3, 6.3 | 2 |
| E3 | New evidence invalidates current admission atomically; fresh use checks collection epochs | 9.3 | 2 |
| A1 | Memory or imported text cannot grant a capability, a permission or a procedure activation | 6.5, 7 | 1a |
| A2 | The core alone commits canonical transitions; callers cannot forge labels or admission | 4, 9.1 | 1a |
| A3 | Endorsement and confirmation bind exact values, roles, scope, use and current authority | 6.4, 7.2, 7.5 | 1b; judgment endorsements 2 |
| AC1 | Content or existence is released only with current `r` or `l` on the home scope and every scope in the item's restrictive dependency closure | 7.3.4–7.3.5 | 1a |
| AC2 | Permission narrowing, membership removal, ownership transfer and end of elevation are fenced like barriers | 7.3.7, 9.4 | 1a |
| AC3 | An agent session's rights never exceed its principal's; sessions never elevate | 7.3.1, 7.3.6 | 1a |
| AC4 | Elevation is explicit, time-bounded and re-authenticated; every access during it is recorded, and administrators cannot delete those records | 7.3.6, 11.4 | 1a |
| AC5 | No principal, including administrators, can forge attribution or source class, set labels or admission, read past a barrier, bypass quarantine or disclose to a restricted processor | 7.3.6 | 1a |
| AC6 | Memory content cannot change permissions, membership or roles | 4.2, 7.3 | 1a |
| P1 | Source classes follow observed capture and field contracts and conservative propagation | 7.1 | 1a; runtime propagation 1b |
| F1 | Model and control dependencies and restrictions survive summaries, overviews, reset and transfer | 8.2–8.3, 10.5 | 1b; UPMS workers 1a |
| F2 | Every release or action passes its complete contract and current checks; only the qualified public-reader exception waives grounding | 7.2, 8.4 | 1b; UPMS releases 1a |
| F3 | Ineligible content or existence metadata never reaches unauthorized rankers or recipients | 10.1–10.3 | 1a |
| F4 | Only a tested fixed-slot interface avoids hidden-value taint; result-dependent handle metadata propagates restrictions | 8.3 | 1b |
| TM1 | Publication releases dependencies only on scopes the publisher owns; provenance and source classes survive | 10.6.2 | 1a |
| TM2 | Lineage exclusions hold at context and overview assembly within instrumented coverage; attestations state their coverage | 10.6.4 | 1a primitive; 1b runtime |
| ST1 | Every structured field links to its source span; text wins on disagreement; deleting text deletes dependent structure | 5.7.5 | 2 |
| ST2 | Stated reasons and rules are claim content, never evidence or enforcement | 5.7.2–5.7.3 | 2 |
| VO1 | Vocabulary proposals are inert until curated; merges are reversible and trigger re-screening | 5.8 | 2 |
| SC1 | Screening is deterministic on replay and never resolves, refutes, supersedes or admits | 9.7 | 2 |
| AD1 | An adapter serves only principals with `r` on every training scope; training excludes X-class and unconfirmed output; deleting a training source blocks it at the barrier | 9.8 | 3 |
| OV1 | Overview content is derived, source-linked and watermarked; exact projections are current to the reader's consistency token | 10.5 | 1a |
| OV2 | Per-reader assembly never includes unreadable scopes; corrections, deletions and revocations remove affected lines before the next release | 10.5.5 | 1a |
| OV3 | What a hub presents is correct whether or not consolidation has run | 10.5.3 | 1a exact parts; 2 narrative |
| OV4 | Maintenance spend stays within budget; exhaustion degrades coherence and freshness, never correctness or invalidation | 10.5.4 | 2 |
| OV5 | Between consolidations the narrative is never edited piecemeal; later changes appear only in the labeled overlay or as withheld sentences | 10.5.3 | 2 |
| OV6 | Consolidation output is source-linked; generalizations are hypothesized claims; a new narrative replaces the old only after screening against projections | 10.5.3 | 2 |
| C1 | Each instrumented invocation has a pre-dispatch manifest and a separate outcome | 11.1 | 1b; UPMS model workers when enabled |
| C2 | Recall finds all seeded retained dependencies within declared coverage and reports gaps | 11.3 | 1a memory; 1b downstream |
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
| T21 | A user is removed from a group while an agent session streams output that used the group's scope: nothing released after the removal is acknowledged |
| T22 | An agent saves a team-scope summary into a personal scope: a teammate without personal access cannot read it; the owner loses it after leaving the team |
| T23 | Injected content in an administrator's agent session requests a mass export or delete: refused, since sessions never elevate |
| T24 | Elevated read of a personal scope: access record and owner notice created; the administrator's attempt to delete the record is refused |
| T25 | An administrator records a memory attributed to another user, or sets a claim admitted: rejected |
| T26 | A user with `w` but not `d` deletes their own item and is refused on another's; a `w`-only drop-box contributor cannot read others' items |
| T27 | A deletion cascades into scopes the requester cannot see without disclosing them; descendant owners see only “an input is unavailable” |
| T28 | Search, counts, coverage, flags and overviews reveal nothing about scopes where the requester lacks `l` |
| T29 | A published note derived from a private note and a confidential document: the private dependency is released; the confidential one still restricts readers |
| T30 | A blind reviewer's context excludes the author's lineage even after the author publishes a summary of their rationale to the shared pool |
| T31 | Two agents supersede the same shared item concurrently: one applies, the other is recorded as a conflict |
| T32 | “Sky is blue” and “sky is dark” at overlapping times without places: a possible flag with `missing_qualifier(place)`, `entity_match_uncertain` and `different_dimension` cues |
| T33 | A Friday release intention against a no-Friday-deploy rule, with and without recorded approval: flagged only without approval |
| T34 | A deprecated term still retrieves and screens memories that use it; new extractions use the current label |
| T35 | Planted jargon in web content never enters adapter training; deleting a training source makes the adapter fall back at once and the retrained adapter excludes it |
| T36 | A blank model given only its L0 hub answers orientation questions; after a correction, L0's exact lines change before the next release |
| T37 | Consolidation paused for a week while work continues: exact lines current, overlays complete, narratives labeled with their age |
| T38 | A source cited by one narrative sentence is deleted: that sentence is withheld before the next release with no LLM call; the rest remains |
| T39 | Maintenance budget exhausted mid-day: no further maintenance LLM calls; task work and invalidation unaffected |
| T40 | The archive grows tenfold at the same change rate: maintenance cost per change stays within its bound |
| T41 | Hundreds of small changes in one area without consolidation: the narrative stays unchanged and coherent, the overlay carries every change, and the fragmentation threshold schedules a regional consolidation |
| T42 | Consolidation writes an unsupported connection or a value contradicting a slot: screening against projections blocks the replacement; unsupported generalizations appear only as labeled hypotheses |

### 15.2 Evaluation protocol

Corpus, implementation and configuration, oracle, prompts, models and judges, budget and decision rule are frozen before measuring. Baselines: B0 source-preserving lexical retrieval; B1 hybrid transcript chunks; B2 full history where it fits; later slices also compare against the previous accepted slice, with the same authorized corpus, answer model and matched budgets. B2's non-applicable cases are reported, not silently excluded.

Initial evaluation: 200 synthetic continuing-project episodes, 100 for development and 100 held out, with at least 10 held-out episodes in each of update and correction, temporal reasoning, scope isolation, continuation, absence and abstention, team coordination and cold-start orientation (overlap allowed and disclosed). Every applicable T01–T42 scenario runs separately; correctness cases are never replaced by aggregate benchmarks. Real-session evaluation is optional until permission is obtained; synthetic results cannot establish real-user generality.

Primary outcome: paired task completion at a fixed declared context budget, with an exact source, permission and lifecycle correctness rubric. Gate target: at least one preregistered continuity or recall outcome improves with a paired 95% interval excluding zero, no mandatory invariant fails, and material task-success regressions exceed neither the preregistered 5-percentage-point margin nor its uncertainty bound. If the sample cannot establish the rule, the result is inconclusive and a new evaluation is specified; the rule is never relaxed after results. Slice 1b may justify equivalent task success with materially better measured enforcement under a preregistered cost tradeoff. Each later slice must show incremental value over the previous one.

Secondary outcomes: attribution fidelity, stale-current answers, temporal correctness, conflict visibility and screening precision and recall, coverage, unnecessary blocking, confirmation prompts, cold-start orientation success and navigation cost, overview staleness and churn, maintenance-to-work cost ratio, extraction consistency across runs and models, normalization coverage, total lifecycle cost and warm and cold latency. Initial confirmation usability threshold: median ≤ 1 integrity confirmation per completed task and p95 ≤ 3 on the ordinary workload; C4-heavy tasks reported separately. Human attention and false blocks count as cost. These thresholds are reviewer choices, not observed results.

Human adjudication reviews every consequential authorization or attribution failure plus a stratified 20% sample of other held-out judgments; a model judge is validated against that sample and disagreements are resolved visibly. All evaluated variants, failures, post-outcome changes, held-out reuse and unknown prior selection history are recorded. Adapter promotion and team-policy experiments (§9.8, §10.6.6) use this same discipline. Public benchmarks may supplement but cannot qualify security or deletion. No results or comparative superiority are claimed here.

## 16. Delivery Slices and Gates

**Useful, permission-aware recall with a deterministic overview ships first; end-to-end runtime instrumentation, structured meaning and consolidation follow as separately gated slices; team policies and adapters are experiments on top.** No date or shipping commitment is implied, and no slice borrows a previous slice's acceptance for an untested guarantee.

| Gate or slice | Deliverable | Required closure |
| --- | --- | --- |
| Gate 0 | This candidate accepted with named owners; decisions D-1 to D-10 confirmed or changed; bound profile; bounded D4 specification and executable test specification | Independent falsification of this exact text; product acceptance; feasibility evidence for Codex coverage and for the storage, KMS and backup arrangement; evaluation frozen before measurement |
| Slice 1a / Gate 1a | Codex-facing memory service via MCP: capture, protected storage, scoped lexical and hybrid recall, coverage, checkpoints, correction, suppression, redaction and deletion, import and export; scope permissions, groups, agent principals and overseers, administrator elevation and access records; publication, shared-pool concurrency and lineage-exclusion primitives; deterministic overview projections and overlays (L0 and L1 exact parts) | 1a invariants on real boundaries (including AC1–AC6, TM1, OV1–OV2, OV3 exact parts); T02–T04, T10, T12–T17, T21–T29, T31, T36–T38 exact parts; recoverable payload and control state; purge and restore evidence; inspection journeys; matched recall and continuity evaluation; no claim about unmediated Codex actions |
| Slice 1b / Gate 1b | One qualified Codex instrumented adapter: manifests, segments, handles, current policy, controlled egress, dispatch recovery, runtime lineage exclusions and independence attestation | T18 coverage demonstrated; F1, F2, F4, C1, C3, O5, TM2 in the runtime; T05–T09, T20, T30; adversarial races; confirmation-burden threshold; no enabled bypass |
| Slice 2 / Gate 2 | Lazy claims and structured statements; vocabulary registry and expansion; deterministic screening and candidate channel; processing cascade tiers 1–2; judgments, temporal and conflict projections; reversible identity matching; limited endorsements; L2 pages; consolidated narratives with regional and global consolidation | H2, E2, E3, ST1–ST2, VO1, SC1, OV3–OV6; T01, T11, T19, T32–T34, T37–T42; extraction consistency and normalization coverage measured on real sessions before screening is relied on; incremental value over 1a; 1b guarantees retained where enabled |
| Slice 3 / Gate 3 | Team visibility policies (experiment §10.6.6); per-scope adapters (tier B); graph-assisted retrieval; Claude adapter; broader collaboration | AD1; T35; adapters beat tier A; team policies beat all-shared and all-private baselines; ablation or comparator and full lifecycle and security evidence for each addition; explicit cost tradeoff; Claude qualified independently of Codex |

The structured foundation (Slice 2) precedes team policies because conflict screening between workers needs comparable statements; basic recall, publication and pull-only notebooks work on text alone. A memory-service release is not the final first-runtime instrumented deliverable.

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

**Readiness: NO-PASS for unconditional implementation-ready or accepted-current status; ready for independent D3 review.** This candidate integrates the identified repairs and the owner's round-2 requirements into one text and binds pilot defaults under delegation. That is not a demonstration of the runtime, storage or evaluation contracts.

### 18.1 Remaining closure

| Item | Evidence still required | Owner and boundary |
| --- | --- | --- |
| Independent review | The author of this candidate cannot independently accept it | Independent reviewer of this exact text, then the product owner at Gate 0 |
| Codex instrumented feasibility | Documented MCP, hooks and app-server features do not establish exact context capture, complete egress control or runtime lineage exclusion | Runtime and architecture owner; before accepting Slice 1b |
| KMS, backups and recovery | Concrete service and copy inventory; restored-control proof; adapter and hub purge behavior | Security and infrastructure owner; feasibility before specification freeze, full tests at Gate 1a |
| Structured-meaning feasibility | Extraction consistency across runs and models; normalization coverage on permitted real sessions; screening precision and recall | Architecture and evaluation owners; before Slice 2 relies on screening |
| Consolidation economics | Maintenance-to-work ratio and coherence measures at pilot scale | Evaluation owner; Gate 2 |
| Evaluation freeze | Corpus, rubric, judge and harness identities, randomness and repetition plan | Evaluation owner; before measurement |
| Source reconciliation | Base inputs and both review records are now available (§1.1, Appendix A); no acceptance record exists for any earlier version | Product owner: confirm no other governing record exists |

### 18.2 Owner decisions

The product owner kept the recommended options below as proposed defaults for this review round; each may still be changed at Gate 0.

| ID | Decision | Proposed default | Main alternative |
| --- | --- | --- | --- |
| D-1 | Administrator reads of personal scopes | Elevated, logged, owner notified | Logged only; or silent, as root |
| D-2 | Administrator power through agent sessions | Never in the pilot | Allowed with per-action confirmation |
| D-3 | Scope nesting | Defaults copied at creation; no live inheritance | Live inheritance |
| D-4 | Source of groups | Identity-provider interface, built-in directory for the pilot | Groups native to UPMS |
| D-5 | Rights granularity | Six rights: `l r w c d m` | Strict `r w x` |
| D-6 | Derived memories lost when access to a source scope is lost | Accepted (no-laundering) | Re-statement prompt before access ends |
| D-7 | Agents as persistent principals | Yes, with own scopes and a human overseer | Sessions acting only for humans |
| D-8 | Who decides publication | The agent, under required-category rules | Human approval for some categories |
| D-9 | Overseer access to agent private memory | Always on | Configurable |
| D-10 | Blind review in the pilot | Primitive in 1a, policy in Slice 3 | Required in 1a |
| D-11 | Domain adaptation of small models | **Decided:** in scope, as per-scope adapters (§9.8) | — |

Default values are not missing decisions merely because they are configurable; missing enforcing capabilities and required evidence remain missing. Gate 0 may narrow a workplan to an accepted Slice 1a boundary without claiming later closure, but cannot silently discard the full Codex integration objective.

## Appendix A. Review Lineage

**Three review rounds shaped this text; each item below names where its result now lives.** Assertions in this appendix are by the AI authors named, not by an independent reviewer.

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
