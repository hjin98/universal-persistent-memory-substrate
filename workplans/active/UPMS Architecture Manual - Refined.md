# UPMS Architecture Manual — Refined Candidate

**Date:** 30 October 2026 (America/Chicago)  
**Revision:** review candidate 1  
**Status:** proposed D3; not accepted-current or implementation-qualified  
**Editor and reviewer of the supplied baseline:** Codex (AI), this chat

## 1. Status, authority and scope

UPMS is a model-independent memory service for continuing project work. It preserves observations, keeps revisable assessments, and supplies an instrumented runtime with the information needed to enforce permitted use. It does not infer permission from remembered text.

This candidate consolidates the supplied manual and proposal. The original files remain unchanged. Review findings and changes are recorded in the companion **UPMS Architecture Review.md**. This editor's self-check is not the independent falsification required for promotion of this revised candidate.

### 1.1 Inputs and their status

| Input | Binding and role |
| --- | --- |
| User's request in this chat | Authorizes architecture review and refinement, not implementation or deployment |
| User's follow-up in this chat | Codex with OpenAI/ChatGPT-family models first; Claude second; configurable retention; delegates initial missing-detail choices to the reviewer |
| UPMS Architecture Proposal v0.3, 30 October 2026 | Supplied draft product/design baseline; not evidence of stakeholder acceptance |
| UPMS Architecture Manual, 30 October 2026 | Supplied proposed D3 baseline; replaces no accepted-current architecture |
| Earlier architecture review cited by the manual | Not supplied; its seven reported findings cannot be independently reconciled with the original record |
| Requested software-design skill | SSDP 7.2.1 review method; no task/workplan `protocol_version` was assigned |

Source SHA-256 identities:

```text
UPMS Architecture Manual.md
16ccdcb0d4afa62c088d9d7920a3630a9e3c9945f689ad32f0ad556dd0cd2200

UPMS Architecture Proposal v0.3.md
da109215e9de0bafb3e7aff68bbe4d768c017c5e70050aa7d6811795284a6f0b
```

**Fixed (proposed)** means a durable architectural constraint if this candidate is accepted. **Initial default** means an agent-chosen, configurable starting value under the user's delegation; it is not a measured capability or a ratified organizational policy. **Unverified** means implementation or external evidence is needed. Defaults never permit weakening a fixed invariant. Changes to product scope or guarantee strength require D3 reconsideration.

### 1.2 Product boundary

The first journeys are task resumption, source inspection, targeted correction, scoped recall, suppression and deletion. Personal and project scopes are explicit. The first deployment is one administrative tenant; cross-organization federation is excluded. Codex is the first integration target; Claude follows after the same adapter contract is qualified independently.

UPMS owns record/state semantics, interfaces, persistence, recovery, concurrency, trust boundaries, resource structure and deployment profiles. External owners retain identity/policy, keys, source-application current state, model behavior and external effects. Model/vendor choice is not a storage identity.

### 1.3 Acceptance boundary

The architecture follows proposal → independent falsification of the exact candidate → product-owner acceptance → bounded implementation specification → implementation acceptance. The user's request to refine and choose defaults authorizes this proposal work, not self-promotion to accepted-current. Section 18 separates unresolved architecture evidence from choices now provisionally bound.

### 1.4 Domain and inspectability

No scientific or numerical-method parent is supplied or required for this bounded engineering contract. UPMS records attributed statements and references; it does not certify their truth. Assessment categories and approximate retrieval are engineering policies, not calibrated confidence or approximation guarantees.

No realized scientific results were generated or reviewed here. Material operational records are sources, assessments, corrections, access/lifecycle decisions, invocation inputs/outcomes, failed or incomplete processing, retrieval coverage, and deletion evidence. Intended readers are users, incident investigators and operators; their routine questions are in Section 17.2. Scientific-project use reopens this determination before UPMS becomes the retention home for required scientific evidence. It must then preserve that project's authority, findings, uncertainty and retention requirements. Source reliability estimates, calibrated confidence or guaranteed numerical approximation also require upstream D1/D2 determination.

## 2. Terms and precedence

| Term | Exact meaning | Owner |
| --- | --- | --- |
| Event | Immutable observation by an authenticated capture component; not proof of its contents | 5.1 |
| Claim | An attributed statement or reasoning proposal, without intrinsic truth or permission | 5.2 |
| Judgment | Assessment of one claim revision under a named scope/ruleset and evidence snapshot | 5.3 |
| Control record | Typed lifecycle, authorization-reference, procedure, dispatch or receipt record | 5.4 |
| Source class | How bytes entered the system; not authorship proof, truth or action intent | 7.1 |
| Dependency | A restrictive dependency for information flow, deletion and recall, recorded by trusted capture/runtime or an approved deterministic transform | 5.5, 8.2 |
| Evidence relation | An attributed assessment about support, opposition or identity; never a permission edge | 5.5 |
| Snapshot position | Ordered canonical commit position for an assessment/read | 9.1 |
| Evidence epoch | Monotone revision of a scope's assessment-relevant collection | 9.3 |
| Restriction epoch | Monotone revision used to invalidate cached security eligibility | 9.4 |
| Handle | Principal/scope-bound reference to a protected value; not an access capability | 8.3 |
| Release | Bytes or a command crossing the last UPMS-controlled boundary | 8.4 |
| Barrier | Durable restriction whose effect is serialized with releases and descendant commits | 9.4, 12.3 |
| Coverage | Captured, indexed, processed, retained and instrumented extent actually available | 10.3 |

The strongest applicable restriction wins: deletion/access denial blocks ordinary use; quarantine permits only its investigation route; correction prevents stale-current use but can permit qualified history; suppression affects proactive retrieval only. Admission never overrides any restriction. Current external policy controls each new decision; historical policy references explain history only.

## 3. Architecture at a glance

```text
                         Identity and policy owner
                          | checks at every boundary
Capture adapter ---> Memory core <--- Processing proposals
                       |     ^                 ^
           transactional     |                 |
                outbox       |            permitted inputs
                       v     |                 |
                Derived indexes ---> Retrieval service
                                         |
                               eligible attributed data
                                         v
                              Runtime adapter / segments
                               | manifest before input
                               | durable dispatch intent
                               v
                         Controlled egress boundary
                               |
                    permitted model / tool / recipient

KMS protects payload units. Source applications own current external state.
All canonical writes, including runtime records, go through the memory core.
```

The four internal components are responsibility boundaries, not four compulsory services. In-process code is within the same trust boundary; separate credentials alone do not isolate hostile code in one process. Run untrusted parsers/extensions/workers with process and capability isolation when required.

## 4. Ownership and interfaces

### 4.1 Component ownership

| Component | Owns | Cannot do |
| --- | --- | --- |
| Memory core | Canonical append/transition validation, revision/epoch allocation, barriers, dependency integrity, purge state, durable outbox | Grant external permissions; infer external truth; invoke models or actions during replay |
| Processing workers | Bounded execution and proposals; durable attempts submitted to core | Directly write canonical state, choose permissive rulesets or lower restrictions |
| Retrieval service | Disposable indexes/projections, selection, coverage and explanation | Promote a claim by ranking or bypass final release checks |
| Runtime adapter | Capture instrumentation, segment/handle execution, complete submitted-context capture, propagation and mediated egress | Forge provenance, infer authority from content, release without current checks |

Canonical ownership and execution responsibility differ: the runtime produces manifests, handles and outcomes, but the core commits their durable records. In-memory handles vanish at restart unless their protected backing and bindings were committed. Workers own no authoritative durable state.

### 4.2 External contracts

Identity/policy owns authenticated principals, membership, delegation, purpose compatibility, current capabilities, revocation and processor permissions. KMS owns key lifecycle. Connected repositories, trackers and calendars own their current state. Providers are processors, not implicitly authorized destinations. Tools own their own effect and retry semantics.

Policy decisions bind principal, tenant, authenticated purpose, operation, exact resource/destination, applicable policy revision, validity and revocation conditions. A caller-supplied purpose string cannot widen scope. Unknown identity, scope mapping or processor permission denies the affected use. Policy-cache validity and revocation delay must be explicit; the initial profile requires online decisions for consequential releases.

### 4.3 Typed operation families

| Operations | Caller and guard | Commit owner |
| --- | --- | --- |
| `record_event`, `record_manifest`, `record_outcome`, `record_processing` | Registered capture/runtime/worker identity for that type | Core |
| `search`, `get_context`, `expand`, `get_evidence` | Authorized caller, purpose, scope and intent | Read-only; release checked |
| `propose`, `report_conflict`, `request_assessment` | Scoped, quota-limited; never directly promotes or quarantines | Core |
| `submit_assessment` | Registered assessor, assigned ruleset, complete attempt, dependency/epoch checks | Core computes allowed judgment transition |
| `correct`, `suppress`, `redact`, `delete`, `deletion_status` | Target-specific authority; subject ambiguity remains explicit | Core |
| `endorse`, `revoke_endorsement` | Exact-object/type/use capability | Core |
| `approve_procedure`, `activate_procedure`, `suspend_procedure`, `revoke_procedure` | Exact version plus distinct approval/activation authority | Core |
| `quarantine`, `release_quarantine` | Policy-authorized detector/investigator, bounded scope, reason | Core |
| `prepare_dispatch`, `record_dispatch_outcome` | Trusted egress adapter; exact action and idempotency binding | Core |
| `recall`, `export`, `import` | Operator/caller capability, scoped disclosure and migration validation | Core for imported records; checked output otherwise |

No API accepts caller-chosen effective labels, permissions or admitted state. Model assertions and conflict reports are data. A trusted detector may impose restriction under policy; arbitrary claims of contamination cannot quarantine another user's entire corpus. Every mutation has a principal/tenant-scoped request identity, expected revision where applicable, and same-request/same-payload idempotency. Identity reuse with different arguments is an explicit conflict.

## 5. Durable records

There are three semantic record types (Event, Claim, Judgment), typed controls, processing records, and one typed relation store. Manifests and dispatches are typed operational records, not a second knowledge ledger. Schemas below specify meaning; serialization remains D4.

Common fields: opaque logical ID and immutable revision ID, tenant, scope, authenticated capture/use purpose, schema version, commit position/time, retention-policy version/deadline, source classes, confidentiality restrictions, and restrictive dependency reference. Fields that contain content or identifying metadata are protected payloads even when stored in a database column. Labels, locators, usernames, relation endpoints, policy references, query text and error text are not presumed public.

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

Only capture appends observations. An agent's claim of completion is an observed statement; actual completion needs a receipt or inspected artifact. Changed source bytes create a revision. Repeated IDs from separate connectors cannot collide: the authenticated source namespace is part of identity.

### 5.2 Claim

```text
Claim {
  statement_ref, source_locators[]
  normalized_statement?        // protected; preserve qualifiers and attribution
  modality, qualifications, asserted_by?
  valid_time, temporal_basis, generated_by
}
```

Modalities: asserted, quoted, hypothesized, intended, committed, preferred, normative. A model's normalization does not prove extraction fidelity. Preserve negation, quantity, units, conditions, attribution and uncertainty, or keep a source-linked textual claim. Original wording is recoverable while retained and authorized; otherwise return an explicit deletion/expiry/unavailability marker, never a fabricated substitute.

### 5.3 Judgment

```text
Judgment {
  claim_revision, scope, ruleset_version
  epistemic_status             // supported | refuted | contested | unknown
  admission_state             // captured | evidence_only | admitted | quarantined
  supporting_refs[], opposing_refs[], qualification_refs[]
  assessor, assessment_output_ref?, processing_ref
  read_dependencies[], evidence_scope_epochs[], snapshot_position
  applicable_time, supersedes?
}
```

Each ruleset defines qualifying support/opposition, correlated-source treatment, missing evidence, applicable domain and admission criteria. Copies of one source are not independent support. Model confidence is not evidence. Restrictive exposure and evidential sufficiency remain separate: an independent basis can support a conclusion without using a disputed derivation, but an artifact exposed to a deleted/private source keeps its restrictions.

Judgments in different scopes/rulesets coexist. Within one claim/scope/ruleset lineage, replacement names the prior head and checks it atomically. Concurrent disagreement is not resolved by last write. The initial policy returns authorized conflicting judgments with their scope and leaves conflicts unresolved; no cross-scope most-permissive selection.

### 5.4 Controls and processing

Controls include correction, suppression, quarantine, redaction, deletion, endorsements, procedure versions/activation, policy references, dispatch intents and receipts. Their state is derived from validated appended transitions.

```text
ProcessingRecord {
  kind, invoker, input_manifest_ref
  model_or_program_version, prompt_or_program_ref, configuration_ref
  output_ref?, outcome         // completed | partial | failed | cancelled | uncertain
  started_at, completed_at?
}
```

Attempts and outputs are separate immutable records. A timeout or crash never synthesizes completion. Reprocessing has a new identity. Required programs, transformations and reducer versions remain available for replay of surviving records.

### 5.5 Relations and dependency closure

| Kind | Relations or records | Semantics |
| --- | --- | --- |
| Exposure/production | `observed_from`, `exposed_to`, `generated_by` | Trusted observations; source → invocation → output traversal supports forward recall |
| Evidence | `supports`, `opposes`, `same_as` | Assessor, exact endpoints, scope, locator, status and qualification |
| Lifecycle | Validated controls with `supersedes`/`retracts` links | Only the authorized transition changes current state; an agent-proposed link is inert |

Restrictive dependencies are stored as object → prerequisite revision references. A model output depends on its manifest's complete inputs; a dispatch depends on its arguments and the context that selected it. Reverse traversal finds descendants. Pre-existing sources do not become descendants merely by sharing a manifest. Operational records and relations receive the restrictions of information they expose.

Restrictive dependencies form a DAG over immutable production revisions. Reject cycles, nonexistent references, foreign-tenant edges and unvalidated narrowing. Evidence relations may be cyclic but are traversed with visited sets and limits. Closure indexes are derived accelerators. Missing closure, incomplete runtime coverage or a traversal timeout is not proof of independence: contain the affected use/scope. Dependency validation and barrier checks are synchronous at commit/release; background graph expansion is not the safety mechanism.

### 5.6 Identity, time and scope

IDs are opaque, stable and never reused. Digests are separate protected integrity data, tenant-scoped and erased with payloads; no durable plaintext hash of a sensitive value. Entity matching is a reversible scoped `same_as` assessment, never a physical merge or an access grant.

Bitemporal records distinguish transaction order from valid time, durations from uncertain occurrence intervals, and unknown from exact time. Relative expressions retain raw wording, source timestamp, timezone if known and resolution basis. Reprocessing temporal interpretation creates a new assessment. Cross-scope derived artifacts inherit all restrictions; membership alone does not broaden an item's readership or permitted purpose.

## 6. Lifecycles

Ordinary transitions append; payload/metadata erasure is the explicit physical exception. Current views are projections of canonical records, not separately editable facts.

### 6.1 Modality projections

| Modality | Lifecycle contract |
| --- | --- |
| asserted | Applicability/freshness is separate from superseded/retracted status; either can change without passing through a mandatory stale state |
| quoted | Quotation fidelity and the inner claim are distinct; quotation can be corrected without accepting its contents |
| hypothesized | Open or abandoned investigation; supported/refuted/contested/unknown comes only from Judgment |
| intended | Active → completed, abandoned or superseded, with authorized statement or completion evidence |
| committed | Open → fulfilled, released or superseded; overdue is a time-derived flag on an unfulfilled commitment, not a terminal state |
| preferred | In force → superseded or withdrawn by the same principal within the applicable scope |
| normative | Historical reference plus applicability from the actual authority source; memory cannot enact or repeal policy |

No completion, cancellation or release is inferred from retrieval decay. Scope policy defines who may release a commitment, including explicit delegation; a model cannot invent a counterparty's approval.

### 6.2 Assessment, admission and quarantine

No judgment means captured. A completed authorized assessment produces evidence-only or admitted under the assigned ruleset and Section 9.3. New evidence or rule changes invalidate current admission until revalidated; old judgments remain historical.

Quarantine is an access restriction layered over assessment. Removing quarantine removes only that restriction, then recomputes current admission, authority and freshness; it never restores a previously admitted state blindly. Authorized investigation is isolated and has restricted egress. Ordinary users may report a concern, not directly rewrite another principal's admission state.

### 6.3 Correction

`requested → applied | proposed_to_owner | pending_clarification | rejected`; pending requests may be clarified or withdrawn. A principal can retract/correct their own attributed statement. A correction to someone else's source is proposed to its owner. A request about an agent-generated claim concerning the requester may correct that claim under scope policy, but cannot erase independent third-party sources. Verified non-user correction uses the deployment's identity and visibility process.

The UI presents exact event/revision/spans or claim, scope and effect. Ambiguous requests remain visibly pending; any provisional restriction is limited to already authorized targets. Applied correction atomically appends the replacement/retraction, invalidates current dependents and establishes the barrier in Section 9.4. Historical recall may show the old version explicitly paired with its correction when otherwise permitted. Correction does not claim erasure.

### 6.4 Endorsements

`presented → valid → revoked | expired`; new bytes/use require a new endorsement. Bind object revision, field/claim, type, meaning, scope, intended use, endorser, current policy decision and validity conditions. Types are extraction fidelity, factual attestation and permitted reliance. None changes provenance, confidentiality or general action capability. Revocation invalidates future reliance and schedules dependent reassessment/recall. A historical endorsement remains a historical fact, not current permission.

### 6.5 Procedures

`draft → approved → active → suspended | revoked`; a suspended version requires fresh authorized activation to resume. Any edit is a new draft. Approval binds exact bytes; activation binds scope/applicability and current authority. Loading and each consequential use recheck revocation. No procedure grants a tool capability. Agent proposals and imported procedures are inert until independently activated.

### 6.6 Suppression

`active ↔ lifted` by an authorized scope principal. Suppression blocks proactive surfacing only; explicit authorized recall can still return the item with its status. It does not alter truth, admission, access, retention or deletion.

## 7. Trust and action policy

### 7.1 Source classes

| Class | Capture meaning |
| --- | --- |
| A — direct entry | Adapter-observed direct input by an authenticated principal with trustworthy span marking |
| R — relayed | Pasted, attached, forwarded or quoted content; all chat text when input-mode provenance is unavailable |
| C — connector-declared | Exact fields independently configured as produced by the source system itself |
| X — external/unknown | Untrusted connector fields, web content, third-party messages, unknown origin |
| M — model-generated | Every model output |

A does not prove intellectual authorship, correctness or intent: a person can retype malicious text. C is field- and contract-specific, not trust in an entire tool response. Missing input-mode instrumentation uses R; content classifiers cannot manufacture A or C. Model-derived objects carry M plus the union of input classes. Automated analysis can add restrictions only.

### 7.2 Consequence classes and grounding

Every operation has a trusted registered contract defining effects, target-binding arguments, payload/disclosure fields, normalization, execution identity, resource limits, conditions and idempotency behavior. Recipient, host, path, account, amount, permission subject, query string, headers and attachments cannot escape checks by a convenient field name. An unknown or inadequately characterized operation is **blocked** until contracted; a generic C4 confirmation cannot make unknown effects reviewable.

Grounding means an exact, canonically resolved value is authorized **for this argument role and operation**, through a trusted task-intent binding, a connector field declared authoritative for that role, a valid exact-use reliance endorsement, or explicit dispatch confirmation. Mere occurrence of the same string in an A/C span is insufficient. Resolve relative paths against a bound root, symbolic links at use, recipients/accounts against their actual identity, and URLs through the controlled network path. Ambiguous resolution blocks the action. The runtime enforces this; the model supplies proposals only.

| Class | Examples | Initial integrity rule (capability, confidentiality and barrier checks always apply) |
| --- | --- | --- |
| C0 | Scoped memory read | Authorized scope/purpose; bounded read |
| C1 | Reply to requesting principal | Recipient may receive every restriction; render retrieved material as attributed data |
| C2 | Memory proposal or isolated draft | Restricted artifact in authorized storage; an arbitrary filesystem write is not automatically C2 |
| C3 | External disclosure, fetch, message, contracted tool write | Role-bound grounding; policy permits influencing sources; X-influenced outgoing payload requires exact-payload confirmation by default |
| C4 | Irreversible, financial, permission-changing operation | C3 requirements plus per-action confirmation by the authorized principal |

Confirmation shows normalized operation, effective target, payload, consequences and relevant qualifications. It is nonce-bound, single-dispatch, time-bounded and invalid after argument/revision changes. Capability is separate from task intent. Conservative provenance plus grounding does not guarantee semantic obedience; end-to-end action quality remains an evaluated limitation.

**Public-reader exception:** a registered, explicitly enabled public browsing operation may waive target grounding and X-payload confirmation for an isolated public reader. It must have no private inputs, credentials, cookies, authorization headers, local files, internal-network reachability or persistent privileged provider state. All bytes and observable request choices must be eligible for public disclosure. The broker allows only contracted public HTTP(S) reads, bounds redirects/size/time and revalidates destination addresses and each redirect at connection time. DNS rebinding, loopback, link-local, metadata services and private destinations are denied. Public GET is not assumed effect-free; capability and destination policy still apply. This exception is disabled in the initial pilot until qualified.

### 7.3 Confidentiality and purpose

Restrictions are conjunctive: every tag must permit the recipient, processor, destination and authenticated purpose. Derived data inherits the union. A result containing multiple scopes may consequently be unusable; isolate work instead of dropping tags. Read permission, factual endorsement and summaries never declassify. Declassification is disabled in the pilot. Processor identity includes the actual account, region/endpoint, retention mode and downstream handling where material, not just a vendor name.

### 7.4 Reliance endorsements

An endorsement permits reliance only on its exact object/value, role and use. It cannot authorize unrelated output, survive a changed value by text similarity, or grant access. Runtime resolution checks current endorser authority and revocation. Batch UI must preserve each differing scope, payload and consequence.

### 7.5 Default admission

The initial ruleset admits only attributed first-party statements: “P stated S,” from verified direct-entry spans by P, about P or expressing P's preference, intention or commitment, within an authorized personal/project scope. It admits the attributed statement, not S as external fact. Extraction fidelity must be established by an exact source-linked rendering or a valid fidelity endorsement; a model-normalized paraphrase alone stays evidence-only. Relayed user material can still be recalled and endorsed through the normal path. Other domains remain evidence-only until a domain ruleset is separately accepted. Admission never makes memory normative authority.

### 7.6 Threat model and isolation

Attackers may control documents, ordinary credentials, untrusted fields and cooperating agents; inject delayed instructions; mislead endorsers; attempt cross-scope disclosure, false memory, unauthorized effects and resource exhaustion. The TCB includes core validation/barriers, retrieval access enforcement, egress, capture/manifest instrumentation, identity/policy, KMS and deployment isolation. Compromise of these components is outside the guarantee. An ordinary compromised credential retains its legitimate permissions until revoked; UPMS cannot infer the human's real intent.

Untrusted text/archives are data, never executable deserialization, shell instructions, plugin activation or policy. Restrict filesystem/network credentials and parser resources. Secrets used by connectors remain outside model context and ordinary logs. A privileged arbitrary shell or uncontrolled outbound network route is incompatible with a claimed fully mediated instrumented profile.

## 8. Runtime flow and egress

### 8.1 Two integration profiles

| Property | Memory-service profile | Instrumented-runtime profile |
| --- | --- | --- |
| Eligible scoped retrieval and UPMS lifecycle controls | Required | Required |
| Every runtime-visible model input captured | Not claimed | Required within declared modality/runtime coverage |
| Output dependency propagation and dispatch checks | Only UPMS-owned workers and releases | All enabled paths in the qualified adapter |
| Downstream recall and deletion containment | UPMS-controlled surfaces | Also recorded runtime outputs/actions within retained coverage |

A missing egress path cannot be advertised as fully instrumented merely by listing a gap. Disable that path, narrow the profile to memory-service use, or repair and qualify the adapter. Provider-internal pretrained state is outside the runtime boundary; undisclosed persistent session state that may contain prior user inputs is not a harmless exception and must be disabled or conservatively tracked.

### 8.2 Conservative propagation

Every opaque model invocation's outputs inherit all runtime-visible inputs: instructions, messages, retrieval, tool results, images/files, procedures, summaries/compaction, prior session state, and model-visible handle metadata. A segment's dependency set grows monotonically until a validated reset. A deterministic non-model transformation may narrow dependencies only through a specified and tested contract; citations, schema validation and model judgments cannot do so.

Restrictions follow control dependence too. Choosing a public URL, a branch, a result count or which handle to return based on private content discloses information even when no source text is copied. No product claim of complete physical timing/resource noninterference is made; semantic metadata leakage is forbidden and residual timing/resource channels require profile-specific assessment in Section 14.

### 8.3 Segments, handles and reset

A handle binds tenant, permitted principal/segment, scope/purpose, exact value revision, type, expiry and dependencies. IDs are unguessable references, not bearer permission. Labels and origins stay in the trusted store unless disclosure of them is permitted. Cross-principal passing, guessing, stale revision, replay after expiry and post-barrier resolution fail ordinary checks.

There are two valid transfer contracts:

1. **Opaque fixed slot:** the trusted runtime allocates a handle slot and fixed type/shape before an untrusted reader runs. The planner sees no result-dependent value, status, count, label or identifier. This tested deterministic interface may avoid importing hidden value dependencies into the planner; resolution at dispatch still imports the value's dependencies into the action.
2. **Result-dependent transfer:** any returned metadata, chosen handle, success bit, variable count, text or unwrap imports its full dependencies and restrictions into the planner. This is the default when independence is unproved.

A secret-reading segment cannot use a public success/error channel to avoid confidentiality. A segment reset starts from a trusted context-selection contract and retained eligible records; model-written summaries keep all old dependencies. If the selected records, objective, query or reset decision came from tainted context, those dependencies remain unless a tested deterministic boundary proves the narrower transfer. Reset also discards provider-side conversation state or carries its dependencies forward. Handle lifetime is no longer than its backing object's eligibility and retention.

### 8.4 Checked dispatch and release

Before any provider submission, tool call, reply or export:

1. Resolve the registered contract and effective effects, values, destinations and argument roles.
2. Include invocation/control dependencies and resolved handle dependencies; check target and payload confidentiality, purpose and processor eligibility.
3. Obtain current capability/task-intent decisions and apply Section 7.2, including current endorsements and confirmations.
4. Check fresh required judgments, corrections, barriers, revocations and external preconditions.
5. Commit a dispatch intent before an effect can escape, binding exact protected arguments, operation/version, caller, dependencies, policy/restriction epochs, nonce, expiry and external idempotency key when supported.
6. At the final controlled boundary, revalidate and serialize release with barriers under Section 9.4; consume the release authorization once. Use an external conditional-write precondition where available.
7. Append completed, blocked, failed, cancelled or uncertain outcome with the receipt and actual destination. A crash after send and before receipt is uncertain, not failed.

Never blindly retry an uncertain consequential action. Reconcile by external receipt/status or the same supported idempotency key. If neither is available, keep uncertainty and require an explicit authorized recovery decision. There is no exactly-once claim across an uncontrolled external service.

Model invocations additionally require a committed input manifest before submission. Their outputs are durably captured or withheld before release; a provider timeout can leave an uncertain submission and separately accounted retry. Streaming uses checked bounded chunks; nothing already released can be retracted by a later barrier. The initial adapter buffers externally visible model output until dependencies and the release decision are recorded.

### 8.5 All egress counts

Replies, inter-agent traffic, tools, URL/query/header fields, logs, diagnostics, exports, embeddings, rerankers and model inputs are disclosures. This applies to UPMS processing workers in both profiles. Operational logging uses content-free events by default; adding payload logs creates a protected deletion surface. No worker or alternate transport may bypass the same processor restrictions.

### 8.6 Resource boundaries

Bound capture bytes/formats, nesting, decompression, relation fan-out, traversal work, search/time/token budgets, queue/storage growth, per-principal inference spend and concurrent jobs. Reserve capacity for restriction commits and deletion remediation. Unknown limits or exhausted validation budgets fail closed for the affected action; ordinary permitted recall may degrade with explicit coverage. Never discard lineage or safety checks to satisfy latency.

## 9. Commit, freshness and recovery

### 9.1 One transition owner

One logical owner serializes canonical commits within the tenant, with fencing enforced by the storage boundary. A stale process cannot commit with a superseded fencing generation. A transaction validates authority, expected revisions, dependencies and barriers; appends records; advances relevant epochs; and schedules derived work through a transactional outbox. Outbox delivery is at least once; consumers deduplicate by operation identity and advance durable watermarks without skipping failed predecessors.

Ingestion identity is `(tenant, authenticated source_namespace, source_message_id, source_revision)`. Without a stable source ID, capture allocates a request ID before retry. Same identity with different bytes is a conflict, not silent overwrite. All lifecycle operations share Section 4.3's mutation idempotency. Transactions never span tenants. Cross-scope reads within the tenant use a consistent snapshot and current access checks.

### 9.2 Payload publication and capture

Apply identity, capture/never-store and resource policy before retention. Write protected payload bytes to non-serving storage, verify durability and integrity, then commit their canonical reference and outbox. Acknowledgement follows both payload and metadata durability. Object-store and database writes are not assumed atomic: abandoned staged objects have run-owned expiry/cleanup; missing committed payloads cause explicit unavailability and repair, never invented data. Temporary files, uploads and rejected content are covered by cleanup policy.

No model runs on the synchronous capture path. Never-store detection has a declared scope: deterministic categories and authenticated channel policy, not a claim that all semantically sensitive content is recognizable. If a channel cannot satisfy its capture policy, reject it or disable retention for it. Asynchronous indexing/extraction uses only eligible inputs and permitted processors.

### 9.3 Freshness without the insertion race

**Initial rule:** the core maintains a conservative evidence epoch per scope. Any committed source addition/revision, claim, evidence relation, correction, relevant lifecycle change, entity-resolution change or ruleset assignment that can affect assessment advances the scope epoch in that same transaction. Unknown relevance invalidates the whole affected scope. Publishing a judgment or completing a processing attempt alone does not advance the evidence epoch; rulesets in the pilot assess source/claim evidence, not a circular collection of judgments. Cross-scope evidence captures every participating scope epoch.

An assessment binds a snapshot, exact read revisions, assigned ruleset and scope epochs. Admission requires unchanged revisions and epochs at commit. If evidence arrives between snapshot and commit, retain the assessment as historical/evidence-only and queue reassessment; it cannot become a fresh admitted head. Unprocessed newly captured evidence also invalidates: pending extraction cannot hide an opposition window. Deep processing need not finish before basic recall.

At every current-state presentation or protected reliance, the effective judgment must still match current scope epochs, rule assignment, validity interval and the maximum age bound, with no unresolved required processing or reassessment. Otherwise show evidence-only with qualifications or block the dependent action. The core's epoch comparison is the safety condition; an asynchronous reassessment queue is only a liveness mechanism. Raw event capture time is not the judgment's freshness time.

Narrower entity/predicate collections are a later optimization only after a complete relevance/invalidation contract and race tests exist. Global scope invalidation may reduce availability; measure it before adopting finer machinery. Timeout or an unknown scope makes an assessment stale, not fresh. External current-state claims additionally need source-owner refresh/preconditions; no epoch makes a remote fact current automatically.

### 9.4 Barriers and the release race

The core owns restriction epochs and orders restriction commits with final controlled releases. A check followed later by an uncoordinated socket/file write is insufficient.

For a correction or deletion, publish the target restriction and advance the affected epoch synchronously. Cached eligibility is invalid immediately; derived descendants are rejected through validated dependency closure even before purge/index jobs run. A bounded closure failure contains the affected scope. No new ordinary descendant of a deletion-blocked input may commit; restricted cleanup/audit transitions remain possible without re-serving content.

Release and barrier activation use a core-coordinated gate. A release either crosses the controlled boundary before the barrier, or revalidates after it and is rejected if affected. Remote egress processes must participate in the fence; an offline cached permit is insufficient. Before acknowledging `serving_blocked` or an applied correction, all older release rights must have completed, been cancelled or been conclusively fenced. A stuck participant can cause a deadline failure; the request stays restricting/pending and is not falsely acknowledged. No lock is held waiting for an uncontrolled recipient's execution receipt.

The guarantee concerns **future releases from controlled surfaces**, not arrival of bytes already sent, deletion of human knowledge, or cancellation of external actions already dispatched. Report those as prior/uncertain exposures. An old-context invocation's pending output is withheld and, if needed, regenerated from a new eligible context. Historical correction recall uses a newly qualified context explicitly containing the corrected history; it does not relabel an old pending answer as safe.

External policy revocation is enforced according to its declared propagation/decision validity. Strict post-acknowledgement revocation requires the policy integration to participate in this fence; otherwise expose the bound and do not claim instantaneous revocation. Pilot consequential decisions are online, single-use and fail closed on uncertainty.

### 9.5 Read-your-writes and bounded work

Targeted reads and acknowledged corrections use canonical state immediately. Search overlays post-index commits through a bounded scan. If the overlay cannot cover the gap, return explicit partial coverage and a continuation token; never claim complete search or current absence. Barriers always apply, even when the index is unavailable. Queries can request a minimum commit position and receive either that consistency or an explicit unable-to-satisfy result.

Lazy processing responds to explicit requests, obligations, retrieval need, consequential reliance and a bounded age-weighted background sweep. Rarely retrieved obligations are not silently starved. Queue saturation stops new nonessential work, preserves canonical capture within quota, and reports deferred processing. Deletion and barrier capacity has priority over extraction.

### 9.6 Replay and compatibility

| Contract | Promise | Limit |
| --- | --- | --- |
| Canonical replay | Rebuild surviving states from retained records, recorded outputs and versioned reducers | No model calls, external queries, actions or erased bytes |
| Historical input reconstruction | Exact submitted runtime-visible sequence while every required byte/revision remains retained | Deletion, expiry and unknown provider internals are explicit gaps |
| Retrieval rebuild | Rebuild eligible content to qualified retrieval criteria | Approximate index bytes/order need not match |

Each durable schema has an explicit READ/MIGRATE/REJECT compatibility rule. Unsupported versions do not fall through to permissive defaults. Migrations preserve IDs, labels, controls, history and deletion restrictions; use staged validation and atomic publication, with interruption recovery. Rollback cannot roll back barriers or resurrect erased content. Caches/indexes may be discarded and rebuilt; canonical data cannot be silently reinterpreted to fit a cache. A model/tokenizer/embedding replacement creates new processing/projection versions with remapped evidence.

## 10. Retrieval, context and continuity

### 10.1 Eligibility before ranking and release

Tenant, principal, purpose, scope, quarantine, correction intent and deletion constrain candidates before payloads reach a ranker, reranker, snippet generator or external processor. Shared approximate structures may be internal to the TCB only if ineligible content cannot affect exposed snippets/counts/explanations or unauthorized model inputs. Partition/filter strategy is D4 and must be qualified; post-filtering an untrusted reranker's input is too late.

Final return passes the release gate. Cache identity includes relevant principal/capability context, purpose, scope, restriction epochs, snapshot, query/intent and model/render versions. Cache hits still recheck current eligibility. Pagination and continuation tokens are scoped, protected, time-bounded and revalidated. Unknown object IDs and denied objects use an indistinguishable unauthorized response unless existence disclosure is explicitly permitted. Timing/resource side-channel exposure is measured separately; there is no unsupported constant-time claim.

### 10.2 Intent routes

| Intent | Route and qualification |
| --- | --- |
| Historical recall | Accessible sources/claims with attribution, valid/transaction time, correction and retention status |
| Current state | Source application where available; otherwise fresh admitted projections, with conflicts/applicability |
| Explanation/verification | Authorized evidence and judgments, including opposition and assessed-as-of position |
| Task continuation | Checkpoint plus changes since watermark; confirmed completion distinct from intention/uncertainty |
| Association | Optional bounded relation expansion with path provenance and relation status |
| Prior discussion | Scoped search with explicit coverage; “not found here” is not global absence |

Absence is assertable only for a deterministic predicate over a fully enumerated authorized corpus. Ranking begins with lexical retrieval, optional qualified vector retrieval, time/task scope, explicit priority, freshness and open obligations, with duplicate reduction. Graph sophistication needs measured incremental value.

### 10.3 Response contract

```text
MemoryResult {
  query_id, intent, effective_scope, authenticated_purpose, time_constraints
  snapshot_position, index_watermarks, projection_versions, restriction_epoch
  items: [{revision_ref, selected_span, source_refs, judgment_refs,
           source_classes, attribution, freshness, qualifications,
           confidentiality_tags, correction_or_retention_status}]
  coverage: {capture_extent, indexed_extent, processing_extent,
             retained_extent, unavailability, truncation, timeout}
  authorized_conflict_or_pending_correction_refs
  budget: {requested_tokens, selected_tokens, omissions}
  continuation_token?
}
```

All metadata is access-controlled. Client-visible snapshot, watermark and epoch fields are opaque, caller/scope-bound consistency tokens, not raw tenant-wide counters that reveal other scopes' activity. Internal ordering remains exact. Even “restricted supporting material exists” is shown only if existence disclosure is allowed; otherwise say that current support/coverage is insufficient without implying a hidden object. Retention and processing gaps cannot be silently converted into “none found.”

### 10.4 Context assembly

Use the actual model tokenizer/input limit and account for non-text/tool-schema costs. Reserve mandatory runtime instructions, the current user request, tool definitions and output allowance before allocating checkpoint/retrieved content. If mandatory content exceeds capacity, return explicit overflow and require a supported replan; never silently drop authority or security constraints. Tokens reported in MemoryResult refer to the selected rendering, not source length.

Retrieved content is attributed data, never activated instructions. Retrieval at session start and lightweight user turns is bounded; deep retrieval requires its capability and budget. Runtime-private instructions that an integration cannot observe are a manifest coverage limitation, not a reconstructed value. Before consequential use, refresh source state and permission under Section 8.4.

### 10.5 Root manifest and checkpoints

These are derived projections of the objective, confirmed completed work and evidence, decisions/status, open questions, obligations, blockers, artifacts and proposed next steps. Bind generation inputs, scope/purpose, watermark, versions and dependencies. On reuse, reconcile corrections, lifecycle/policy changes and relevant external state since the watermark. A stale checkpoint can be history, never implicit current authority. Expiry of a checkpoint does not fulfill an obligation. Warn of impending retention loss when the user relies on continuity, within the authorized scope.

## 11. Accountability and inspection records

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
  policy_decision_refs, snapshot_position
  aggregate_classes_and_tags, input_coverage, committed_at
}

InvocationOutcome {
  invocation_id, output_refs, proposed_action_refs, dispatch_refs
  provider_receipt?, status, completed_at?
}
```

The manifest covers exactly what is submitted, including middleware transformations, attachments and prior state within the claim boundary. It is committed before provider dispatch; outputs/outcomes follow. A transcript or post-hoc summary is not a pre-dispatch manifest. Hidden provider reasoning/pretraining is not promised. If instrumentation cannot observe some runtime-generated prompts/compaction, the full instrumented profile remains unqualified.

### 11.2 Retention and reconstruction

Split the operational record into a protected reference skeleton and protected rendered fragments. The skeleton contains opaque links, classes, tags, policy/dispatch references and outcomes, never free-form payload text. Opaque links remain sensitive metadata and have a retention policy.

Exact reconstruction requires **all** referenced original revisions, rendered fragments, media bytes and transform/template versions, not just newly generated fragments. The effective reconstruction deadline is the earliest deadline among these items. The requested reconstruction window may pin copies only within applicable retention permission; deletion/access revocation overrides it. If policy forbids keeping a required item, record the shorter effective window at capture.

Distinguish **representation expiry** from **semantic-object expiry**. A replay-only duplicate of a retained canonical input, or rendering fully accounted for by a recorded deterministic transform and retained inputs, may expire without deleting the source or its semantic descendants. This loses exact replay when the rendering is no longer recoverable; it does not remove restrictive lineage. Novel prompt/compaction/model-generated content is itself a canonical protected input, not a replay-only copy, and must have a retention policy compatible with its descendants. Expiry/deletion of a canonical input invokes deletion and descendant invalidation. No content-bearing input may be relabeled a temporary representation to evade that rule. This distinction prevents a seven-day replay-copy window from unintentionally imposing seven-day retention on all otherwise lawful memories.

Keep the minimum restrictive lineage while surviving objects require it. Removing dependency links for space reasons cannot make a live descendant independent. When all affected descendants are purged, strip sensitive source links/labels from audit skeletons and retain only permitted minimal lifecycle receipts. Recall coverage explicitly ends with retained lineage; “long retention” never means forever.

### 11.3 Incident recall

Given a source, credential, procedure, processor or ruleset identity, traverse restrictive dependencies and separately evidential dependence. Return authorized affected records, manifests, outputs, dispatches, outcomes and procedures; distinguish possible influence from causal proof. Include processing/instrumentation/retention gaps, uncertain effects and destinations outside local control. No report grants permission to expose another scope's records or to undo an external action. Recall can schedule authorized reassessment or quarantine through normal interfaces.

## 12. Retention, redaction, deletion and portability

### 12.1 Deletion units and configuration

Default source unit: event revision; default derived unit: object revision. Split unusually large/mixed-policy inputs into declared units at capture. Every content-bearing representation is covered: raw/normalized text, embeddings, summaries, prompts, fragments, handles, indexes, query/response caches, staging files, logs, journals/WAL, replicas, backups and managed exports. Restricting the original object alone is insufficient.

Retention is versioned policy per tenant/scope/category with effective deadlines and a deletion plan. More restrictive applicable deadlines win. Reads do not renew retention silently. Longer retention requires an authorized explicit change before expiry; nothing resurrects erased bytes. A retention change cannot silently purge an unexpectedly broad corpus: show scope, counts the actor may see, affected continuity and effective date, then apply the authorized policy transition. Retention expiry uses the same serving barrier and purge evidence as explicit deletion.

### 12.2 Redaction without self-deleting the replacement

`redact(event_revision, spans)` is an authorized deterministic copy-and-erase transaction, not model rewriting. Validate exact byte/span boundaries and authority; stage a new protected revision containing only retained spans with mapped provenance. Atomically publish the replacement and apply the original revision's deletion barrier. No acknowledgement occurs until both are durable and the release fence is complete.

This is an explicit narrow dependency exception: the certified retained-span copy is a new source unit, not an ordinary descendant of the whole original unit for erasure propagation. Preserve the original's confidentiality/purpose restrictions conservatively; redaction does not declassify. The protected redaction control records input/replacement identities and transform version for audit, without reintroducing removed bytes into the replacement. It cannot be used by a model, arbitrary program or caller to strip dependencies. The retained-byte equality and removed-byte exclusion are acceptance properties. All pre-existing descendants of the original are still withheld/purged and must be regenerated from the replacement or independent surviving sources.

This preserves unrelated source spans, not uninterrupted availability of every old summary/checkpoint. If the caller asks to delete the whole logical event or subject, include all revisions/replacements in discovery; the exception cannot evade that wider target.

### 12.3 Deletion lifecycle

| State | Required condition |
| --- | --- |
| requested | Exact authorized target/scope or explicit discovery request recorded |
| authorized/restricting | Target restriction committed; old release rights being drained/fenced |
| serving_blocked | No later controlled release or ordinary descendant commit can use target/descendants; acknowledge this separately |
| purging | Idempotent per-surface cleanup and key/copy reconciliation in progress |
| purge_failed | At least one cleanup failed or deadline missed; barrier remains; retry/escalate |
| complete_within_scope | Every named controlled surface and required key/copy condition satisfied; evidence and external limits listed |

Never reopen serving to make purge succeed. Cancellation or timeout does not lift an established deletion barrier. Unknown dependency coverage contains the affected scope and prevents an unqualified completion claim. “Delete about X” requires authorized discovery, ambiguity resolution and an explicit coverage statement; semantic search alone cannot prove complete subject erasure. Independent sources survive an occurrence deletion when permitted; a subject-level request must discover them too.

The purge controller may access only the payloads/metadata needed for authorized cleanup; these internal operations are not ordinary recall or new model processing. Running model/worker results touched by a barrier are withheld and purged. Content already released outside control is listed as such.

### 12.4 Keys and backups

Use standard authenticated encryption with independently addressable data keys for payload units and protected content/metadata. Deleting a database wrapper is not cryptographic erasure if a backup restores it while the wrapping key survives. A chosen KMS may satisfy per-unit irreversible destruction only if all recovery/wrapper/key caches are covered; otherwise completion waits for physical copy/backup expiry.

**Initial design choice:** encrypted backups with short bounded expiry, not an unverified claim of immediate per-unit cryptographic erasure. Live stores, indexes and caches purge promptly; `complete_within_scope` waits for every relevant backup/WAL/replica/staging copy to expire or be verifiably purged. The recovery-only backup service never exposes content directly to retrieval. Administrative restore access is protected and audited. Cached plaintext and keys have bounded lifetimes and explicit invalidation.

Deletion/revocation control history lives in a separately durable recovery control plane under the same logical core authority, outside ordinary data-backup rollback. It has authenticated checkpoints/monotone positions and redundant recovery copies. A restore must prove it has the latest applicable control state and enforce it **before** any serving or new derivation. If it cannot, remain closed. Data restore alone cannot resurrect access. Tombstones outlive every compatible backup/export/replica that could reintroduce the target; identity reuse is forbidden.

### 12.5 Audit and erasure claims

Minimal audit retains authorized pseudonymous actor, policy reference, opaque target/request identity, state, surface evidence and counts. Strip names, payloads, sensitive free-form reasons, identifying relation labels and low-entropy plaintext hashes. Minimal tombstones/receipts are an explicit retained exception disclosed in deletion status; do not label this “nothing remains.” Any richer retained lineage is still protected data and blocks claiming its erasure.

External recipients and ungoverned exports cannot be erased by local key destruction. Contracted provider retention/deletion evidence is tracked separately. A processor whose retention conditions violate a category's policy cannot receive it in the first place. Completion reports distinguish local controlled surfaces, managed processor obligations and uncontrolled historical disclosures.

### 12.6 Import, export and schema portability

Legacy documents enter as historical captured aggregates with original location, import time, scope, purpose and available provenance. An author name or “accepted” label inside a file is an assertion, not authenticated authority. Missing origin maps to X (or R for explicitly relayed user content). Extraction coverage is visible; partial import is not complete memory. Imported endorsements/procedures remain historical/inert until local authority mapping and activation requirements are met.

Exports contain only authorized records, schema/revision identities, provenance, applicable lifecycle restrictions and explicit missing/deleted markers. Exclude credentials and automatic cross-deployment permissions. The destination is a checked disclosure; a managed export is tracked as a deletion surface, while an uncontrolled delivered export is an external limitation. Import verifies origin/version, remaps tenant-local identity without collision, preserves restrictive history and rejects packages that would resurrect tombstoned local records. A new independent capture is distinguished from replaying an old deleted identity. Portability does not manufacture access or erase audit gaps.

## 13. Failure behavior

| Failure | Required behavior |
| --- | --- |
| Capture/payload cannot commit | No saved acknowledgement; retry same identity; clean owned staging |
| Model/extraction/embedding unavailable | Retain permitted capture; bounded source recall with processing limits |
| Index missing/stale or overlay too large | Bounded permitted fallback or explicitly partial response; no bypass of restrictions |
| Policy decision/revocation status unknown | Deny affected release/action; no silent stale authorization |
| KMS unavailable | Deny new unwraps; barriers persist; purge may remain incomplete |
| Source application unavailable | Qualified historical observation only, never falsely refreshed current state |
| Owner failover | Fence stale writer and egress rights; recover canonical state/outbox |
| Outbox duplicate or worker crash | Idempotent delivery; no skipped watermark, duplicate transition or fabricated completion |
| Manifest/dispatch journal commit fails | No provider submission or external effect |
| Tool/provider result uncertain | Persist uncertainty; reconcile before consequential retry |
| Restriction fence cannot finish | No false serving-blocked acknowledgement; contain and report deadline failure |
| Purge/backup expiry fails | Keep blocked, retry/escalate, report incomplete and deadline miss |
| Dependency cycle/missing reference/traversal limit | Reject unsafe commit/use; contain uncertain scope |
| Unsupported schema or stale restore controls | Read/migrate only under compatibility contract, otherwise fail closed |
| Storage/quota/processing budget exhausted | Backpressure, reserve control/purge capacity, report partial/deferred work |

## 14. Initial deployment profile

### 14.1 Runtime choices and qualification limits

**User-selected:** Codex first with OpenAI/ChatGPT-family models; Claude next. **Reviewer-selected initial host:** a local/self-hosted Codex integration using supported MCP interfaces for memory-service operations; evaluate a controlled app-server integration for deeper instrumentation. This is an implementation target, not evidence that stock Codex exposes every hook UPMS needs. No model identifier is hard-coded as a permanent default; record the exact runtime, model, tokenizer, provider/account and configuration used in each qualification.

Official documentation describes MCP connections and app-server thread/turn/event/approval interfaces. Tool hooks cover many local calls but exclude hosted tools and some specialized paths; continuing an existing exec session does not repeat its pre-tool hook. Consequently **MCP plus hooks alone is insufficient evidence of the instrumented profile**. These are documented facts; the choice of a staged integration is this reviewer's design inference. [MCP](https://learn.chatgpt.com/docs/extend/mcp?surface=cli), [App server](https://learn.chatgpt.com/docs/app-server), [Hooks](https://learn.chatgpt.com/docs/hooks).

Before Slice 1b, demonstrate exact pre-provider context capture (including compaction/resume), output interception before display, procedure/handle enforcement, nested agents, shell/network/processor coverage, current policy and release fencing. Disable uncovered paths in the qualified instance. If supported APIs cannot supply these boundaries, keep Slice 1a's memory-service claim and reopen the adapter design; do not build a shadow transcript and call it complete instrumentation. A runtime fork or new enforcing host is a separate concrete design decision, not authorized implementation in this review.

Existing stock-client history, logs, provider sessions and local files outside UPMS ownership are named external surfaces. A memory-service deletion cannot erase previously returned text from those surfaces. Capturing/importing them needs explicit scope and capture permission. Claude must later pass the same contract independently; no Codex pass transfers automatically.

### 14.2 Configurable pilot defaults

The user delegated initial choices. These values are **agent-chosen planning/qualification targets**, not benchmark results, legal conclusions or externally approved policies. Configuration is schema-validated, versioned, audited and attached to every evaluation. Changing a material binding invalidates only affected evidence. Explicit category/scope overrides can tighten defaults; increasing exposure, relaxing a security invariant or broadening product scope requires the owning decision.

| Parameter | Initial effective value / rule | Origin and boundary |
| --- | --- | --- |
| Tenancy/workload | One tenant, up to 5 users, 10 active sessions; continuing project work | Proposal + reviewer scale choice |
| Corpus envelope | 100,000 live event revisions, 1 million total live canonical records, 10 GiB protected payloads | Reviewer target; beyond limit backpressure/requalify |
| Capture throughput | 1 event/s sustained, burst 10/s for 60 s within quota | Reviewer qualification target |
| Retrieval latency | p95 ≤ 500 ms warm, ≤ 2 s cold, excluding remote inference/source fetch; report both | Reviewer target at declared envelope |
| Query/graph limits | 200 candidates, 30 returned items, 3 hops/1,000 visited nodes, 2 s work budget | Reviewer default; truncation explicit |
| Capture limits | 1 MiB inline UTF-8 text; 10 MiB declared file; 20 MiB expanded aggregate, 1,000 members, depth 16, expansion ratio 20 | Reviewer defaults; initial text/Markdown only; no nested archives or active render |
| Context allocation | Mandatory content/output first; UPMS extras ≤ min(8,000 tokens, 20% of remaining input capacity), split 25% checkpoint/75% retrieval with unused budget reusable | Reviewer default; actual target tokenizer/capacity required |
| Processing limits | 1 deep job/principal, 2/tenant; 100 model calls and 1 million aggregate input+output tokens/principal/day, both limits apply | Reviewer cost guard; controlled pilots only |
| Required assessment age | At most 5 minutes plus exact current evidence epochs | Reviewer default; does not permit stale-epoch use |
| Raw source retention | 180 days from capture | Reviewer configurable default; explicit authorized pin may extend |
| Durable user-approved task records | 365 days or an explicit shorter scope policy | Reviewer default; underlying dependencies must also be lawfully retained or record becomes unavailable |
| Derived artifacts/handles | No later than earliest required input deadline; handle ≤ 1 hour and current segment eligibility | Reviewer default; no retention laundering |
| Rendered context window | Replay-only copies up to 7 days, shortened by any input's policy or deletion; novel canonical inputs retain their own category deadline | Reviewer default; effective reconstruction deadline recorded |
| Operational lineage | 180 days, and as needed while a surviving dependent requires it within applicable policy | Reviewer default; if policy forbids needed lineage, expire the dependent too |
| Content-free operational logs | 14 days | Reviewer default; payload logging off |
| Minimal deletion receipts | 1 year; tombstones longer only until all compatible resurrection sources retire | Reviewer default; retained exception disclosed |
| Serving-block acknowledgement | Target ≤ 2 s; no success if fence unfinished | Reviewer target; correctness does not yield to deadline |
| Live-surface purge | Target ≤ 24 h after barrier | Reviewer target with per-surface evidence |
| Backup expiry / complete purge | Backup copies expire ≤ 7 days; complete-within-scope target ≤ 8 days after barrier, including cleanup margin | Reviewer choice; longer-held copies prevent completion |
| Plaintext/key caches | ≤ 60 s TTL plus barrier invalidation before any new release | Reviewer bound, not delayed-serving permission |
| Recovery | Zero loss of acknowledged commits for process/single-node failure; site-loss data RPO ≤ 15 min, RTO ≤ 4 h; latest deletion controls required before serving | Reviewer targets; no unsupported zero site-loss claim |
| Disk admission | Reserve max(2 GiB, 20% of allocated capacity) for control/purge/recovery; stop nonessential ingestion before reserve | Reviewer initial guard, measure amplification |
| Security policy | No declassification; public-reader exception off; no uncontracted tool; no cross-scope judgment reconciliation | Conservative defaults |
| Model/embedding processors | Deny until exact provider/account/endpoint and category permission are bound; prefer local embeddings for restricted pilot data | Reviewer fail-closed default; vendor preference is not processor approval |

No one-year task record may silently extend a source's 180-day retention. Either obtain an explicit permitted retention extension for its required inputs or expire/mark the derived record unavailable. User-created independent statements can be new source events; presenting old model text for endorsement does not erase its dependencies.

Retention controllers use deadlines derived from server-recorded capture time and trusted current time; clock uncertainty never prolongs a security lease or falsely certifies expiry. Commit order remains the state-order authority.

### 14.3 Storage and deployment choice

**Initial default:** PostgreSQL canonical records/outbox and adjacency tables; protected payload object storage; derived lexical/vector indexes. No dedicated graph database, event bus, universal confidence service or separate policy engine inside UPMS. A single small deployment may colocate trusted components; access paths and process isolation must still match the threat model. Identity/policy and KMS may be integrated providers behind the external-owner interfaces.

Use a conventional per-object data-key envelope and encrypted backup expiry as specified in Section 12.4. The concrete KMS/storage products, supported schema versions and availability layout are D4 choices only if they meet those contracts; qualification must establish real key caching, backups, restore and deletion behavior. Tenant partitioning is not itself isolation. Searchable plaintext, embeddings and diagnostic metadata remain sensitive.

Timing/resource side channels, administrator access and provider-held data are explicit residuals. Before multi-user release, test semantic isolation and measure cross-scope timing leakage under the chosen index/cache design. A stronger noninterference promise requires an accepted stronger profile and evidence; never inherit it from encrypted storage alone.

## 15. Invariants and acceptance evidence

These are planned obligations, not executed implementation tests. Every applicable invariant must hold; a better aggregate metric cannot compensate for a known violation.

| ID | Acceptance property | Owner | First applicable slice |
| --- | --- | --- | --- |
| H1 | Ordinary semantic state appends; erasure is explicit, scoped and audited | 5–6, 12 | 1a |
| H2 | Claim/judgment provenance resolves to retained records or explicit unavailability | 5, 9.6 | 2 |
| E1 | Capture, assessment, admission, provenance and permission remain distinguishable | 5–7 | 1a, full assessment in 2 |
| E2 | Conflicts remain visible when authorized; independent evidence is not silently suppressed | 5.3, 6.3 | 2 |
| E3 | New evidence invalidates current admission atomically; fresh use checks collection epochs | 9.3 | 2 |
| A1 | Memory/imported text cannot grant capability or activate procedures | 6.5, 7 | 1a |
| A2 | Core alone commits canonical transitions; callers cannot forge labels or admission | 4, 9.1 | 1a |
| A3 | Endorsement and confirmation bind exact values, roles, scope, use and current authority | 6.4, 7.2–7.4 | 1b; judgment endorsements in 2 |
| P1 | Source classes follow observed capture/field contracts and conservative propagation | 7.1 | 1a; runtime propagation in 1b |
| F1 | Model/control dependencies and restrictions survive summaries, reset and transfer | 8.2–8.3 | 1b; UPMS workers in 1a |
| F2 | Every release/action passes its complete operation contract and current checks; only the explicitly qualified public-reader exception waives grounding | 7.2, 8.4 | 1b; UPMS releases in 1a |
| F3 | Ineligible content or existence metadata cannot reach unauthorized rankers/recipients | 10.1–10.3 | 1a |
| F4 | Only a tested fixed-slot interface avoids hidden-value taint; result-dependent handle metadata propagates restrictions | 8.3 | 1b |
| C1 | Each instrumented invocation has a pre-dispatch manifest and separate outcome | 11.1 | 1b; UPMS model workers when enabled |
| C2 | Recall finds all seeded retained dependencies within declared coverage and reports gaps | 11.3 | 1a for memory, 1b downstream |
| C3 | Skeletons contain no payload; reconstruction windows cover every required fragment/revision or report exceptions | 11.2 | 1b |
| R1 | Correction acknowledgement orders against release and preserves qualified history | 6.3, 9.4 | 1a for UPMS, 1b downstream |
| D1 | Deletion barriers reject all later affected controlled releases/descendant commits, including after restore | 9.4, 12 | 1a |
| D2 | Completion names evidence for every controlled surface/key/backup and discloses retained exceptions | 12.3–12.5 | 1a |
| D3 | Authorized retained-span redaction survives old-unit purge without retaining removed bytes; old descendants remain invalid | 12.2 | 1a |
| O1 | Fenced single-owner commits and idempotent mutations/outbox delivery prevent duplicate transitions | 9.1 | 1a |
| O2 | Replay never invokes models/actions; migration and rollback preserve restrictions | 9.6, 12.6 | 1a |
| O3 | Context fits actual model capacity or returns explicit overflow | 10.4 | 1a |
| O4 | Coverage distinguishes unavailable, unprocessed, unindexed and not found | 10.3 | 1a |
| O5 | Pre-effect intent plus uncertain-outcome recovery prevents blind consequential retries | 8.4 | 1b; external UPMS dispatch when enabled |
| O6 | Resource exhaustion preserves restriction/purge capacity and cannot downgrade safety | 8.6, 13–14 | 1a |
| M1 | Import/export preserves provenance and restrictive lifecycle without importing authority | 12.6 | 1a for supported import/export |

### 15.1 Required falsification scenarios

Acceptance cases exercise the real core, storage, retrieval and egress owners. Deterministic external doubles can control faults, but replacing the enforcing owner with a harness imitation cannot qualify it.

| Case | Adversarial trajectory and required discriminator |
| --- | --- |
| T01 | Concurrent contradictory capture after assessment snapshot, before commit: judgment cannot enter fresh admission; check before/after queue processing |
| T02 | Delete/correct after release check but before actual send; stream mid-flight; crash an egress participant: no later controlled release after acknowledged barrier |
| T03 | Delete input of a mixed summary with stale indexes/closure cache: descendants blocked immediately, independent sources remain permitted |
| T04 | Redact a middle span, crash between staging/commit, purge original and restore old backup: retained spans survive only through certified replacement; removed spans and old descendants do not reappear |
| T05 | Reader encodes a secret in handle count/type/status/selection or reset-selected objective: planner/action inherits restrictions or transfer is blocked |
| T06 | Same literal address appears in an unrelated user statement; injected source chooses it: no role-bound intent, so dispatch cannot pass merely by string match |
| T07 | Public fetch redirects or rebinds to local/metadata address, carries cookies or chooses a query from private context: exception denied |
| T08 | Invalid/foreign/stale/revoked handle and mismatched confirmation nonce: no capability or revision bypass |
| T09 | Process crashes before/after external send and before receipt: durable intent exists, uncertainty preserved, no blind duplicate |
| T10 | Duplicate ingestion/outbox messages, conflicting idempotency payloads and old writer after failover: exactly one canonical transition or explicit conflict |
| T11 | Quarantine release after ruleset/policy/evidence change: no restoration of obsolete admission |
| T12 | Expire original revision before manifest fragments, or delete source while reconstructing: exact reconstruction becomes explicitly unavailable; derived copies cannot launder retention |
| T13 | Restore without latest control history, stale KMS wrapper, WAL/replica/cache copy or expired backup awaiting physical cleanup: do not serve/certify erasure prematurely |
| T14 | Cross-scope search, cache/pagination reuse, snippet/reranker/error/coverage query: no unauthorized content or existence leak |
| T15 | Correct before extraction; ambiguous person/claim; commitment fulfilled after overdue; preference withdrawn: lifecycle remains coherent without erasing others' evidence |
| T16 | Import a file claiming acceptance/authority or a package carrying deleted identities; interrupted schema migration/rollback: history preserved, authority inert, no resurrection |
| T17 | Context overflow, graph cycle/fan-out, queue flood and simulated low disk: bounded explicit failure; barriers/purge remain serviceable |
| T18 | Codex compaction/resume, hosted tool, continued exec, subagent, hidden prompt injection and output stream: each enabled path captured/enforced or instrumented claim fails |
| T19 | Late source revision, non-independent corroboration, unsupported normalization, conflicting scope judgments and failed partial processing: attribution/coverage preserved, no fabricated fresh support |
| T20 | Revoke policy/endorsement after context assembly; provider input and telemetry carry private data: current destination/purpose checks deny unauthorized release |

### 15.2 Evaluation protocol

Freeze corpus, implementation/configuration, oracle, prompts/models/judges, budget and decision rule before measuring. Initial baselines: B0 source-preserving lexical retrieval; B1 hybrid transcript chunks; B2 full history where it fits; later slices also compare against the previous accepted slice. Use the same authorized corpus, answer model and matched budgets, and report non-applicable B2 cases instead of silently excluding hard cases.

Initial proposed evaluation: 200 synthetic continuing-project episodes, 100 development and 100 held-out, with at least 10 held-out episodes in each of update/correction, temporal reasoning, scope isolation, continuation and absence/abstention families (overlap allowed and disclosed). Include every T01–T20 scenario applicable to the slice separately; correctness cases are not replaced by aggregate benchmarks. Real-session evaluation is optional until permission is obtained; synthetic results cannot establish real-user generality.

Primary outcome: paired task completion at a fixed declared context budget, with exact source/permission/lifecycle correctness rubric. Gate target: at least one preregistered continuity/recall outcome improves with a paired 95% interval excluding zero, while no mandatory invariant fails and material task-success regressions exceed neither the preregistered 5-percentage-point margin nor its uncertainty bound. If sample size cannot establish the rule, report inconclusive and obtain a newly specified evaluation; do not relax it after results. Slice 1a compares with B0/B1 and B2 where applicable. Slice 1b may justify equivalent task success with materially improved measured enforcement, under a preregistered cost tradeoff. Slice 2 must show incremental value over 1a under the same profile.

Secondary outcomes: attribution fidelity, stale-current answers, temporal correctness, conflict visibility, coverage, unnecessary blocking, all confirmation prompts, total lifecycle cost and warm/cold latency. Initial confirmation usability threshold: median ≤ 1 integrity confirmation per completed task and p95 ≤ 3 on the declared ordinary workload; C4-intensive tasks reported separately and never exempted from their confirmation rule. Human attention and false blocks count as cost. These thresholds are reviewer choices, not observed results.

Human adjudication reviews every consequential authorization/attribution failure plus a stratified 20% sample of other held-out judgments. Validate a model judge against that sample and resolve disagreements visibly. Record all evaluated variants, failures, changes after outcomes, held-out reuse and unknown prior selection history. Public benchmarks may supplement this workload but cannot qualify security/deletion. No results or comparative superiority are claimed by this document.

## 16. Delivery slices and gates

The table replaces the missing embedded delivery artifact in the supplied manual. It deliberately separates useful recall from unproven end-to-end instrumentation.

| Gate/slice | Deliverable | Required closure |
| --- | --- | --- |
| Gate 0 | Exact accepted D3 candidate, named owners, initial profile, bounded D4 specification and test specification | Independent falsification; product acceptance; reconcile material baseline differences; binding/feasibility evidence for selected surfaces; freeze evaluation before measurement |
| Slice 1a / Gate 1a | Codex-facing memory-service via MCP: capture, protected storage, scoped lexical/hybrid recall, coverage, checkpoints, correction, suppression, redaction/deletion, inspectable status, bounded import/export | Real-boundary memory invariants, recoverable payload/control state, purge/restore evidence, inspection journeys and matched recall/continuity evaluation; no claim about unmediated Codex actions |
| Slice 1b / Gate 1b | One qualified Codex instrumented adapter: manifests, segments, handles, current policy, controlled egress and dispatch recovery | T18 coverage demonstrated; all applicable flow/action invariants, adversarial races, cost/confirmation threshold and no enabled bypass |
| Slice 2 / Gate 2 | Lazy claims, judgments, temporal/conflict projections, reversible identity matching, limited endorsements | Assessment fidelity, collection freshness, corrections and visible disagreements; incremental value over 1a; retain 1b guarantees wherever enabled |
| Slice 3 / Gate 3 | Optional Claude adapter, graph retrieval or broader collaboration | Demonstrated need, ablation/comparator, full affected lifecycle/security evidence, explicit cost tradeoff; Claude qualification independent of Codex |

No date or shipping commitment is implied. Later-slice architecture can be specified now, but it cannot borrow a prior slice's acceptance for an untested guarantee. A memory-service release is not the final first-runtime instrumented deliverable.

## 17. Delegation, inspection and reopen triggers

### 17.1 D4 space

Delegate language/frameworks, schemas/serialization, indexes/libraries, embedding and extraction models, ranking weights, helper functions, scheduling/backoff, cache representation, KMS product, UI layout and transport implementation. Preserve durable semantics, initial explicitly bound profile constraints, and acceptance at real owners. Avoid proliferating components to imitate a missing runtime hook; address the enforcing boundary or narrow the claim honestly.

### 17.2 Product inspection surfaces

The supplied proposal Section 11 already proposes these surfaces within the product. This revision preserves them; they remain proposed product requirements pending acceptance, not new authority created by review:

- What was remembered, from which source, and when?
- Why was it retrieved or presented as current, with which assessment and coverage?
- What supports/opposes it, and what is unprocessed or unavailable?
- Did correction, suppression, quarantine, redaction, revocation or deletion take effect, and what remains pending?
- Which retained outputs/actions might it have influenced, with what outcomes and limits?
- What retention deadline applies, and which controlled/external surfaces remain after deletion?

All answers obey access control, including existence disclosure. The final retention/deletion explanation is a clarification of the proposed deletion-status journey. No independent scientific-result database or new scientific dashboard is added. Technical review cannot accept a product surface beyond the user's requested deliverable on the product owner's behalf.

### 17.3 Non-goals and simplification

No truth oracle, motive/threat inference, person reputation, memory-trained model weights, general theorem prover, replacement system of record, cross-tenant transactions/federation, guaranteed model causal attribution, universal prompt-injection immunity, or erasure of uncontrolled recipients. No generic numerical confidence is introduced.

Keep Event/Claim/Judgment because observation, proposition and assessment have different identities/lifecycles. Do not require Claims/Judgments for basic recall. Keep evidence and exposure distinct inside one relation store. Keep the four ownership boundaries but avoid mandatory separate services. Use canonical storage/outbox instead of a second event bus. Replace duplicated hypothesis truth state with Judgment, and use scope epochs before a complex predicate-matching invalidation service. These are design tradeoffs, not measured optimality claims.

### 17.4 Reopen and impact rules

Reopen the owning D3 section if runtime capture/mediation cannot enforce it, hidden state prevents reset, conservative invalidation destroys usable availability, purge deadlines exceed feasible key/backup behavior, confirmation burden exceeds the declared threshold, or a new processor changes the confidentiality boundary. A request for scientific-record custody, calibrated scores or guaranteed approximation routes upstream. Cross-tenant/federated use, declassification and arbitrary privileged execution require new explicit architecture decisions.

On any accepted material change, remap affected records/APIs, adapters, operation/ruleset contracts, caches/indexes, migration/recovery, tests, docs and evaluation identities. Preserve unaffected evidence only with reason. No implementation/evidence corpus was supplied for this review, so downstream impact closure remains unexecuted. Equivalent D4 changes preserving these contracts do not reopen D3. Repeated wrappers/fallbacks around one broken mechanism trigger re-derivation before another additive repair.

## 18. Readiness and remaining closure

**Readiness: NO-PASS for unconditional implementation-ready/accepted-current status.** This candidate closes identified textual/mechanism gaps and binds pilot defaults under the user's delegation. It is ready for independent D3 review and a bounded Codex feasibility investigation; those activities are not a declaration that the runtime/storage contracts have been demonstrated.

| Item | Disposition and evidence still required | Owner / boundary |
| --- | --- | --- |
| First workload/runtime | Continuing project work; Codex/OpenAI first, Claude next, per user instruction | Bound; exact qualified runtime/model build recorded at implementation freeze |
| Profile/retention choices | Section 14 supplies configurable initial values; no need to invent stakeholder policies later | Proposed under delegated choice; validate operational feasibility before Gate 0 closes |
| Admission and judgment scope | Attributed first-party default only; no cross-scope reconciliation; other domains evidence-only | Bound conservative defaults; broader rulesets require Gate 2 decision |
| Correction UX | Exact target preview; ambiguous requests remain pending; independent sources protected | Design specified; concrete UI/identity flow and tests in D4 |
| Codex instrumented feasibility | Documented MCP/hooks/app-server features do not establish exact context capture and complete egress control | Runtime/architecture owner; mandatory before accepting Slice 1b mechanism or its implementation gate |
| KMS/backups/recovery | Conventional envelopes plus bounded backup expiry selected; concrete service/copy inventory and restored-control proof absent | Security/infrastructure owner; storage feasibility before production specification freeze, full tests at Gate 1a |
| Evaluation | Section 15.2 specifies a synthetic pilot protocol/default thresholds; corpus, rubric, judge/harness identities and randomness/repetition plan still need freezing before measurement | Evaluation owner; no private real sessions authorized or used |
| Source reconciliation | Both supplied documents inspected; earlier cited review and any acceptance record absent | Product/architecture owner: supply if still governing, or explicitly supersede historical dependency; no inferred acceptance |
| Independent review | This editor authored the revised candidate; self-check cannot independently accept it | Independent reviewer of exact candidate, then product owner at Gate 0 |

Default values are not missing decisions merely because they are configurable. Missing enforcing capabilities and required evidence remain missing. Gate 0 may narrow a workplan to an accepted Slice 1a boundary without claiming Slice 1b closure; it cannot silently discard the user's full Codex integration objective.
