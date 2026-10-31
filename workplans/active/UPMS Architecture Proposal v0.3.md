# Universal Persistent Memory Substrate

## Architecture Proposal v0.3

**Date:** October 30, 2026  
**Status:** Draft for independent cross-review  
**Prepared for:** Sam  
**Draft author:** Codex, incorporating the v0.1 and v0.2 proposals and the subsequent architecture review  
**Intended readers:** Architecture reviewers, agent-runtime developers, security engineers, and prospective product owners

This proposal defines a model-independent memory service that preserves evidence and task continuity, retrieves relevant history with explicit uncertainty, and supplies the information an integrated runtime needs to enforce permitted uses. It retains the Event, Claim, and Judgment model introduced in v0.2 and makes its security, correction, deletion, and replay contracts more precise.

v0.3 is the proposed successor to v0.2. It is not an accepted implementation specification or a report of demonstrated security or benchmark performance. Requirements below describe the proposed design; implementation acceptance depends on the evidence in Sections 15–17. The immediate review decision is whether this architecture is coherent and sufficiently bounded to proceed to a first implementation specification.

## 1 Purpose and product boundary

An agent should be able to resume useful work after a session ends without inventing what happened, forgetting a correction, or treating an old document as permission to act. Users should be able to inspect what was remembered, see why it was retrieved, correct it, restrict its use, and delete it.

UPMS separates three questions:

1. **What was encountered?** Preserve the observed record and its provenance.
2. **What does the available evidence support?** Maintain scoped, revisable assessments.
3. **What may be done with it?** Obtain current authorization and enforce information flow outside model reasoning.

The ledger is authoritative for UPMS's recorded history. It is not an authority on external truth, the current state of connected applications, or permissions.

### 1.1 Initial product

The first deployment targets continuing project work by a small group of users and multiple agent sessions within one administrative tenant. It supports isolated personal and project scopes, with explicit sharing. Cross-organization federation is deferred.

The first useful journeys are:

- Resume a task with its objective, completed work, open questions, obligations, and artifact references intact.
- Find an earlier statement or decision and inspect its source.
- Correct a remembered fact and prevent its stale version from being presented as current.
- Retrieve relevant history without exposing another scope's information.
- Suppress unwanted proactive reminders or delete retained material through distinct operations.

“Universal” means a portable data model and integration contract. It does not mean every runtime supplies the instrumentation required for every guarantee.

### 1.2 Non-goals

UPMS does not provide a general truth oracle, infer people's motives or threat levels, assign reputation scores to people, or replace repositories, calendars, trackers, and other systems of record. It does not train model weights on retained memory as part of this proposal.

UPMS does not grant permissions, guarantee faithful model reasoning, or provide complete prompt-injection protection through retrieval alone. It does not promise erasure of information already delivered to an uncontrolled recipient, or exact knowledge of which source caused a model to produce a particular answer.

## 2 Design principles

| ID | Principle | Consequence |
| --- | --- | --- |
| P01 | Preserve evidence separately from interpretation | Summaries and extracted claims never replace retained source records. |
| P02 | Remembering does not imply believing | Capture, assessment, and retrieval admission have distinct meanings. |
| P03 | Believing does not grant permission | Memory cannot create capabilities or activate procedures by its content. |
| P04 | Preserve provenance through transformation | A summary cannot acquire authenticated authorship or remove restrictions merely by being generated. |
| P05 | Separate exposure from evidential support | Security dependence and a claim's asserted basis are recorded as different relationships. |
| P06 | Deterministic software owns state transitions | Model outputs are recorded proposals; replay does not invoke a model. |
| P07 | Apply controls before disclosure and action | Access restrictions are hard checks, including at output destinations. |
| P08 | Make corrections and uncertainty visible | Conflicts, staleness, and incomplete processing are not hidden by fluent presentation. |
| P09 | Preserve history subject to retention | Append-only operation does not prevent authorized payload erasure. |
| P10 | Bound work and context | Retrieval, processing, storage, and context assembly have explicit budgets. |
| P11 | Keep derived state disposable | Indexes, working sets, and checkpoints have identifiable dependencies and can be rebuilt or replaced. |
| P12 | Require complexity to justify its cost | Add mechanisms for demonstrated user value or a necessary safety property. |

## 3 Ownership and deployment

UPMS has four responsibility boundaries. The initial implementation may place them in one service with separate credentials and access paths where needed; these are not four mandatory network services.

| Boundary | Owns | Does not own |
| --- | --- | --- |
| Memory core | Durable records, revisions, transition validation, retention and deletion state | External truth or permission grants |
| Retrieval service | Eligible search, current projections, context selection, coverage and freshness reporting | Authorization policy or semantic acceptance by ranking |
| Processing workers | Extraction, reconciliation, entity-match and summary proposals with recorded inputs and outputs | Direct canonical promotion or security-policy changes |
| Runtime integration | Invocation capture, complete manifests, information-flow enforcement, action checks, procedure activation | Rewriting memory provenance or inventing user authority |

An external identity and policy system owns authentication, capabilities, delegation, revocation, purpose compatibility, and permission decisions. A key-management system owns cryptographic key lifecycle. UPMS records references to relevant decisions and consumes their results.

The ordinary flow is:

```text
Authenticated capture -> Memory core -> Eligible retrieval -> Runtime context
                              ^                ^                    |
                              |                |                    v
                     Validated proposals   Derived indexes    Model invocation
                              ^                                     |
                              |                                     v
                       Processing workers                  Proposed output or action
                                                                    |
                                                                    v
                                                   Runtime and policy enforcement
                                                                    |
                                                                    v
                                                     Permitted destination or tool
```

The external policy system participates at capture, retrieval, processing disclosure, endorsement, deletion, and action boundaries. The diagram shows the main data flow, not an alternative authorization route.

### 3.1 Integration profiles

**Memory-service profile:** UPMS controls its own capture, storage, retrieval, and deletion surfaces. A runtime using only an ordinary search interface receives scoped results but cannot claim complete invocation tracking or downstream action enforcement.

**Instrumented-runtime profile:** An adapter records all runtime-visible invocation inputs, propagates restrictions through outputs, and mediates every relevant action and disclosure path. Only this profile may claim the corresponding end-to-end properties, within its documented coverage.

Adapters declare supported input modalities, tools, destinations, provider behavior, and bypass risks. Unknown or missing coverage is reported explicitly. A transport such as Model Context Protocol (MCP) does not establish the instrumented-runtime profile by itself.

### 3.2 Service interface

The typed internal API is primary; transport adapters preserve its authentication, scope, and lifecycle semantics. Callers receive only the operations allowed by their credential. The initial operation families are:

| Operation | Caller and boundary |
| --- | --- |
| `record_event` | Authenticated capture component; records an observation, not its semantic truth |
| `record_manifest`, `record_outcome` | Instrumented runtime; seals invocation inputs and appends outcomes |
| `get_context`, `search`, `expand`, `get_evidence` | Authorized runtime or agent; scoped results and coverage metadata |
| `propose`, `report_conflict`, `request_assessment` | Agent or worker; records candidates or queues bounded work without granting admission |
| `correct`, `suppress` | Authorized principal; targeted lifecycle changes with distinct effects |
| `endorse`, `revoke_endorsement` | Principal holding the relevant scope capability; exact-object attestations |
| `delete`, `deletion_status` | Authorized principal or retention controller; staged deletion and status inspection |
| `recall` | Authorized operator; incident impact traversal with controlled disclosure |

No caller can bypass transition validation by directly writing labels, judgments, permissions, or procedure activation state. UI actions and background controllers use the same underlying lifecycle operations. Feedback can improve retrieval evaluation but cannot directly promote a claim or source.

## 4 Durable records and provenance

### 4.1 Event

An Event records what an authenticated capture component observed: a user message, a tool response, an imported document, an action receipt, or a system observation. It establishes that the component received those bytes or that result; it does not establish the truth of every statement in them.

Only a capture component may append an observation event. When an agent reports that it completed work, the runtime can record that the agent made the report. A claim that the work actually completed requires its own basis, such as an execution receipt or inspected artifact.

Identifiers are opaque and stable. A digest used to check payload integrity is separate from event identity, scoped against cross-tenant correlation, and protected according to the payload's retention policy. Plaintext content hashes must not become undeletable identifiers for sensitive facts.

### 4.2 Claim

A Claim is a statement extracted from an event or proposed through reasoning. It records what is asserted, by whom when known, in which scope, about which period, and with which qualifications. A claim is not automatically true, admitted, or authorized for consequential use.

A normalized subject–predicate–value representation supports retrieval, but the original statement and a source locator remain available. Normalization must preserve negation, quantities, units, conditions, attribution, and uncertainty. A sentence that cannot be safely normalized remains a source-linked textual claim.

### 4.3 Judgment

A Judgment records a process's assessment of a claim under a specified ruleset, scope, and evidence snapshot. It can be superseded without changing the claim or source event.

Judgments carry epistemic assessment and retrieval admission as separate fields. The fields are semantically distinct; policy may inspect both. Structural validation of a judgment does not prove the assessor's interpretation correct.

When an assessment depends on a model, its proposed assessment is recorded first. The canonical transition owner checks assessor authority, input revisions, scope, completeness, and applicable transition rules before committing a judgment. An assessor cannot silently choose a more permissive ruleset.

### 4.4 Relationship types

| Relationship | Meaning | Principal use |
| --- | --- | --- |
| `observed_from` | A capture component received this event from a particular channel or source | Attribution and ingestion audit |
| `exposed_to` | An invocation received this item among its inputs | Conservative information-flow tracking and incident recall |
| `generated_by` | An artifact was produced by a recorded invocation or deterministic operation | Production lineage |
| `supports` or `opposes` | An assessor identifies this material as evidence bearing on a claim | Explanation and assessment |
| `supersedes` or `retracts` | A later record changes the applicable status of a specified earlier record | Correction and current-state projections |
| `same_as` | A proposed identity relationship between entities, subject to judgment | Reversible entity resolution |

An evidence link is itself an assessment, not proof that the source entails the claim. Its author, locator, and status are retained. Exposure links are runtime observations and do not depend on the model's self-reported citations.

One relationship store can support these distinctions. W3C PROV provides useful vocabulary for activities, usage, generation, derivation, and attribution; UPMS adopts only the subset needed by its contracts. [W3C PROV-DM](https://www.w3.org/TR/prov-dm/)

### 4.5 Schema sketch

The following fields define the intended semantics, not a frozen serialization format. Every record has an opaque ID, tenant identity, schema version, commit position, and security metadata. Sensitive fields are protected as described in Section 12.

```text
Event {
  id, tenant, scope, capture_purpose
  channel, witness_principal, transmitter_identity?
  origin_identity?, origin_authentication_evidence?
  payload_ref, source_message_id?, source_revision?
  observed_at, committed_at, commit_position
  stated_occurrence_time?
  security_metadata, retention_class
}

Claim {
  id, tenant, scope, purpose
  statement_ref, normalized_statement?
  modality, qualifications, asserted_by?
  valid_time, temporal_basis
  source_locators[], generated_by
  created_at, security_metadata
}

Judgment {
  id, tenant, claim_id, claim_revision, scope
  epistemic_status, admission_state
  supporting_refs[], opposing_refs[], qualification_refs[]
  assessor, assessment_output_ref?, ruleset_version
  read_dependencies[], snapshot_position
  applicable_time, supersedes?, committed_at
  security_metadata
}

ProcessingRecord {
  id, kind, invoker, input_manifest_ref
  model_or_program_version, prompt_or_program_ref, configuration_ref
  output_ref, outcome, started_at, completed_at
  security_metadata
}
```

Additional control records cover endorsements, procedure activation, corrections, suppression, deletion, policy-decision references, and invocation/action receipts. These are explicit lifecycle records, not additional general-purpose knowledge graphs.

### 4.6 Entities and time

Entity IDs are never reused. Matching two entities creates a scoped `same_as` claim with a judgment. Underlying records are not physically merged, and a rejected match invalidates affected projections. Equality expansion cannot grant access to an otherwise restricted entity or relationship.

UPMS distinguishes **valid time**, the period a statement purports to describe, from **transaction time**, when UPMS committed it. Temporal representations distinguish a duration from an uncertain occurrence somewhere within a range. Unknown time remains unknown. Relative dates retain the raw expression, source timestamp, timezone when known, and resolution basis; ambiguous timezone or calendar interpretation remains explicit.

Bitemporal queries answer what was recorded about a period and what the recorded view was at a later time. They do not establish objective historical truth.

## 5 Assessment and memory lifecycle

### 5.1 Epistemic assessment

| Status | Meaning under the named assessment rules |
| --- | --- |
| Supported | Available evidence meets the stated support criterion, without qualifying opposition sufficient to make the claim contested |
| Refuted | Available evidence meets the stated refutation criterion, without qualifying support sufficient to make the claim contested |
| Contested | Qualifying support and opposition coexist |
| Unknown | Available evidence or processing is insufficient for the other classifications |

These are assessment categories inspired by four-valued approaches to incomplete and inconsistent information. v0.3 does not claim to implement Belnap logic or a general theorem prover. Rulesets must define support, opposition, source dependence, and the treatment of missing information for their actual domain.

Repeated copies of one source are not independent corroboration. LLM confidence alone is not a support criterion. Freshness, extraction completion, and source availability are additional metadata; they are not disguised as truth values.

An inference records disputed premises in its derivation. An independent sufficient basis may support the same conclusion without using the disputed derivation. The system must not erase a dispute or mechanically contaminate every unrelated supporting path.

### 5.2 Admission

| State | Retrieval behavior |
| --- | --- |
| Captured | Available for authorized historical recall as an observed record; semantic assessment may be absent |
| Evidence only | Available as attributed material, without presentation as an established conclusion |
| Admitted | Eligible for ordinary scoped knowledge retrieval, with current assessment and qualifications |
| Quarantined | Excluded from ordinary retrieval; available only through an authorized investigation path |

Events can be retrieved before claims or judgments exist. The absence of a judgment never means admission. Deletion and access denial override every admission state.

Conflicting judgments in different scopes are returned with their scope when relevant and authorized. The caller does not receive whichever judgment is most favorable. If a task needs a single decision and no authorized resolution rule applies, the conflict remains unresolved. Restricted judgments cannot be exposed merely to explain why a visible claim has limited usability.

### 5.3 Modality

| Modality | Example | Lifecycle consequence |
| --- | --- | --- |
| Asserted | The limit is 100 requests per second | Assess evidence, time, applicability, and staleness |
| Quoted | Dana said the launch slipped | Assess fidelity of quotation separately from its inner claim |
| Hypothesized | DNS may explain the outage | Preserve the hypothesis and later investigation outcomes |
| Intended | Ship the release in March | Track active, abandoned, completed, or superseded intent |
| Committed | I will send the report Friday | Track the responsible party, due time, and fulfillment evidence |
| Preferred | Use tables in reports | Preserve scope and later preference changes |
| Normative | No deployments on Fridays | Record the statement and its authoritative source; resolve applicability outside memory |

Completion, fulfillment, and procedure activation require their own records; extraction cannot manufacture them. A preference's declining retrieval priority does not revoke it. An old commitment does not disappear because it is rarely retrieved.

### 5.4 Source quality

The first implementation records provenance and assessment outcomes without maintaining reputation scores. Later source-quality estimates require independently defined outcomes, domain applicability, uncertainty, and safeguards against correlated evidence and feedback loops. A publisher or channel that maps to one person cannot be used to circumvent the prohibition on person-level reputation scoring.

## 6 Identity and permitted reliance

### 6.1 Separate security dimensions

v0.3 removes the universal I0–I3 ladder. Authenticated transmission, factual support, confidentiality, and endorsement are retained separately.

| Dimension | Recorded meaning |
| --- | --- |
| Authentication and provenance | Verified transmitter, channel, witness, origin evidence, and unknowns |
| Integrity constraints | Which sources may influence a protected use under the applicable policy |
| Confidentiality restrictions | Which recipients, processors, scopes, and purposes may receive or use the information |
| Scoped endorsement | An authorized attestation concerning an exact object and specified meaning or use |

Authentication establishes the sender of a message, not the authorship of every passage. Text entered in a chat box may include quotations or pasted material. Structured quotation or attachment metadata can preserve this distinction; otherwise the system records the authenticated transmitter and leaves unsupported origin claims unverified. Content classification may impose additional restrictions, never authenticate origin or confer authority.

A tool is not uniformly trusted. Its channel may reliably establish that it returned a result, while individual fields contain untrusted external content. Connectors declare those distinctions through independently configured contracts.

### 6.2 Endorsement

An endorsement identifies the exact object version, claim or field, attestation type, scope, intended use, endorser, authorization decision, and validity or revocation conditions. The initial human-facing types are:

- **Extraction fidelity:** this representation accurately reflects the identified source.
- **Factual attestation:** this principal asserts the claim under the stated qualifications.
- **Permitted reliance:** the specified use may rely on this exact value under the stated conditions.

An endorsement does not rewrite source provenance or remove confidentiality. It is not an action authorization. At a protected use, policy may accept a valid, narrowly scoped reliance endorsement as an explicit exception to an integrity restriction. That exception does not raise the trust of the invocation's other outputs or of subsequent summaries.

An altered claim or broader use requires its own applicable endorsement. Revocation invalidates dependent reliance decisions for future use and triggers reassessment and incident recall where appropriate. Historical records preserve that an endorsement was valid at an earlier time.

Routine recall does not require endorsement. Public or unverified material can remain useful as attributed evidence or tentative context. Interfaces show what is being endorsed and its consequences; batch endorsement cannot conceal materially different scopes, uses, or qualifications.

Confidentiality declassification is a separate operation and is disabled by default in the initial deployment. If later enabled, it must bind an exact output, permitted destination and purpose, a current declassification capability, and an audit record. Factual endorsement, summarization, or permission to read cannot implicitly declassify content.

### 6.3 Authority and procedures

Memory stores references to external authorization decisions. Replaying a historically valid decision explains a past action; it cannot authorize a new action. Capabilities and purpose constraints are checked against current policy at the relevant boundary.

Procedures and standing instructions are versioned artifacts with an authenticated approval and activation record. Agent proposals remain inactive drafts. Signing identifies the approved bytes and signer; it does not prove the procedure correct or grant tools permission to execute it. Revocation, applicability, and current capability checks remain mandatory.

Normative memory claims link to the actual authority source. Text saying that a policy changed cannot activate that change. A runtime resolves governing instructions through its authorized configuration and policy paths.

## 7 Runtime security

### 7.1 Threat model and trusted components

Attackers may control external documents or tool-result content, plant delayed memory injections, cooperate through a malicious agent, compromise an ordinary user or agent credential, and mislead an authorized endorser. They may attempt data exfiltration, unauthorized state changes, false memories, cross-scope disclosure, and resource exhaustion.

The trusted computing base includes the canonical transition owner, access and egress enforcement, capture and manifest instrumentation, identity and policy services, key management, and relevant infrastructure isolation. Compromise of these components is outside the protection claimed by the memory design and requires infrastructure controls. A compromised ordinary credential retains whatever legitimate permissions it had until detected or revoked; UPMS cannot infer the human's true intent from authentication.

### 7.2 Conservative information flow

Every model invocation is treated as an opaque transformation. Its outputs inherit the union of confidentiality restrictions and the conservative set of integrity dependencies of every runtime-visible input, including messages, retrieved memory, tool responses, procedures, and compacted context.

These sets are semantic dependencies and may be represented by references rather than copying their full transitive closure into every record. A deterministic transformation can have a narrower dependency contract only when that contract is defined and tested. An LLM's self-reported citations or influence estimates cannot narrow security dependencies.

Isolating untrusted reading can reduce unnecessary exposure. Schema validation constrains output shape but does not establish safe meaning: an email address or boolean can redirect an action without containing prose instructions. If untrusted output enters a planning invocation, its restrictions enter that invocation too. Any narrower control/data separation requires an enforcing runtime, not a prompt convention. CaMeL and Fides are relevant precedents for such enforcement, with guarantees tied to their respective execution models. [CaMeL](https://arxiv.org/html/2503.18813v1), [Fides](https://www.microsoft.com/en-us/research/publication/securing-ai-agents-with-information-flow-control/)

### 7.3 Action and disclosure checks

Before executing a tool call or releasing an output, the runtime must:

1. Resolve the operation, target, recipient or destination, payload, and relevant resource limits using a registered operation contract. Unknown effects are not classified as harmless by the model.
2. Obtain the output's restrictions and dependencies from the actual invocation or operation record.
3. Check the acting principal's current capability for this exact action and target.
4. Check that the destination, processor, recipient, and purpose satisfy the payload's confidentiality restrictions.
5. Check whether the influencing sources are permitted for this use, including any explicit, valid reliance exception.
6. Revalidate relevant corrections, deletion state, access revocation, and external-state preconditions before dispatch; bind the decision to the actual arguments and their versions.
7. Record the decision and execution outcome, including a blocked, failed, or uncertain outcome.

Where the external tool supports conditional writes, use its preconditions to prevent a check/use race. Otherwise expose the weaker guarantee and use a bounded dispatch authorization; do not imply atomicity across an uncontrolled external service.

All disclosure paths count: user-facing replies, inter-agent messages, search query strings, network requests, logs, exports, embedding services, and model-provider inputs. Read-only calls can leak data. Capability to send is distinct from permission to disclose a particular payload to a particular destination.

Permission uncertainty fails closed for the affected operation. Ordinary permitted recall can continue. Human confirmation is required only where the relevant policy or missing action intent requires it; generic approval of a summary cannot authorize an unspecified downstream action.

### 7.4 Resource and investigation boundaries

Capture and parsing enforce size, format, nesting, and decompression limits. Retrieval and graph expansion enforce result, time, hop, and token limits. Agent-triggered processing is quota-limited. Feedback and repeated retrieval cannot raise reliability, admission, or authority.

Investigation access uses isolated contexts and restricted egress. Access to quarantined evidence does not permit feeding it into an ordinary privileged context without its restrictions. Procedure content, imported records, and benchmark fixtures are data until independently authorized for their intended use.

## 8 Capture and deterministic state management

### 8.1 Capture and processing

Capture performs authentication, capture-policy and never-store checks, initial restriction assignment, payload protection, and a durable append before acknowledging retention. It records rejected or unavailable capture only to the extent permitted by policy, without preserving forbidden content.

Full-text indexing, embeddings, entity extraction, and deep assessment run asynchronously. Embeddings are not assumed cheap or permitted for every provider. Retrieval can overlay recent committed records or use a bounded direct scan to supply read-your-writes behavior while indexes lag. Responses disclose the relevant coverage and processing state.

Lazy processing is triggered by explicit requests, unresolved task obligations, retrieval need, consequential reliance, or a bounded background budget. Scheduling must avoid making retrieval frequency the sole measure of importance. Basic recall remains available when deep processing is unavailable; consequential reliance can require an assessment or source refresh first.

Every processing attempt records input references, actual runtime context, program or model identity, configuration, output, and outcome. Reprocessing is a new attempt, not a silent replacement of the earlier result. Failed and partial attempts cannot appear as completed assessment.

### 8.2 Canonical commits and concurrency

One logical transition owner serializes canonical commits within each tenant partition. This is an ownership constraint, not a requirement for one permanent process. A leader-based implementation needs fencing so a former writer cannot continue committing after failover.

The commit transaction validates authority and dependencies, appends canonical records, advances revisions, and durably schedules projection work. Ingestion is idempotent on tenant, channel, and source message identity; changed source content creates a new revision rather than overwriting a prior event.

Processing results carry their actual read dependencies. Changes to unrelated records do not automatically invalidate a result. Validation must also cover relevant collection or query changes: a newly inserted contradictory claim can matter even when no previously read row changed. Rulesets define the affected dependency scope and how uncertain relevance is handled.

The initial deployment keeps transactions within a tenant. Cross-tenant atomicity and federation are deferred. A cross-scope query within the tenant uses a consistent snapshot and current eligibility checks. Publicly visible timestamps do not replace ordered commit positions for concurrency.

### 8.3 Corrections and read-your-writes

A correction identifies a claim version, source event, or selected source span whenever possible. Authorization distinguishes correcting one's own statement from proposing a correction to someone else's. Disagreement does not grant permission to suppress another principal's evidence.

For an authorized, unambiguous target, the canonical correction transaction creates a retraction or supersession record and a serving restriction that takes effect at acknowledgement. It invalidates affected projections and working sets before they can be reused as current. Historical recall may still show the old statement with its correction, unless deletion or access policy forbids it.

If the target has not been extracted, the correction can bind to the original event or span. If the target is ambiguous, the system records a pending correction and requests clarification. It must not claim that every paraphrase was synchronously repaired. Known affected items can be withheld or visibly marked pending; unresolved matching remains a coverage limit.

The same serving checks apply to caches and checkpoints. A previously assembled invocation cannot be made to unsee information: the runtime prevents affected pending outputs from being released and regenerates them when necessary.

### 8.4 Three reconstruction contracts

| Contract | Required behavior |
| --- | --- |
| Canonical replay | Reconstruct committed record status and deterministic projections from retained records, recorded processing outputs, and versioned reducers, subject to deletion |
| Historical context reconstruction | Recover the exact runtime-visible input arrangement from immutable manifests and retained item revisions, or explicitly identify missing/deleted parts |
| Retrieval rebuild | Rebuild eligible searchable content and meet declared retrieval-quality criteria; byte-identical approximate indexes or rankings are not assumed |

Replay does not call models, query live systems, or repeat actions. Policy references and execution receipts explain prior decisions; new decisions use current policy. If an embedding or derived summary cannot be reconstructed without a new inference, its replacement receives a new processing identity. Stable tie-breaking is useful but does not make approximate indexing deterministic.

## 9 Retrieval and context assembly

### 9.1 Query intent

| Intent | Route | Required qualification |
| --- | --- | --- |
| Historical recall | Hybrid lexical and vector search over accessible events and claims | Attribution, time, and material coverage limits |
| Current state | Owning system of record when applicable; otherwise scoped current projections | Source revision, freshness, applicability, and unresolved conflicts |
| Explanation or verification | Evidence and assessment traversal | Supporting and opposing evidence, assessor, and ruleset |
| Task continuation | Current checkpoint plus relevant events, changes, and obligations | Observed completion versus proposed next steps |
| Multi-hop association | Bounded relationship expansion | Relationship status and path provenance |
| Search for prior discussion | Scoped search with declared coverage | “Not found within this scope,” not an unrestricted absence claim |

Exact exhaustive scans may establish absence only for a defined deterministic predicate over a fully enumerated accessible corpus. Semantic retrieval does not prove that an idea was never discussed.

### 9.2 Eligibility and ranking

Tenant, principal, scope, purpose, quarantine, correction, and deletion checks constrain candidate eligibility before content is exposed to ranking components or external rerankers. A final serving check closes races with policy and lifecycle changes. Internal approximate-search implementations must not use inaccessible content in a way that leaks it through snippets, explanations, counts, or other exposed metadata.

The starting ranking combines lexical and vector retrieval with time, task scope, explicit user priority, freshness, and unresolved obligations. Duplicate reduction preserves useful diversity. Ranking is not admission and cannot grant access.

Graph traversal is optional and bounded. Personalized PageRank is a research-informed candidate for demonstrated multi-hop gaps, not an initial requirement; HippoRAG illustrates this family of retrieval methods. [HippoRAG](https://arxiv.org/abs/2405.14831)

### 9.3 Response contract

```text
MemoryResult {
  query_id, intent, effective_scope, time_constraints
  snapshot_position, index_and_projection_versions
  items: [{object_ref, selected_span, source_refs, judgment_refs,
           attribution, freshness, qualifications, security_metadata}]
  coverage: {capture_extent, indexed_extent, processing_extent,
             relevant_unavailability, truncation, timeout}
  conflict_or_pending_correction_refs
  budget: {requested_tokens, selected_tokens, omissions}
}
```

Coverage metadata itself is access-controlled. It must not reveal the existence or contents of another tenant's records. A user can receive “limited to your accessible project history” without receiving counts of inaccessible material.

### 9.4 Working context and continuity

A root manifest supplies compact orientation and pointers. A checkpoint preserves the objective, completed work with evidence, current decisions and their status, unresolved questions, obligations, blockers, artifact references, and proposed next steps. It records its generation inputs, scope, watermark, and qualifications.

Checkpoints and summaries are derived artifacts. They cannot establish completion or acceptance by existing. On reuse, the runtime checks relevant revision, access, correction, deletion, and external-state changes. A stale checkpoint may be useful as history but cannot silently stand in for current state.

Context assembly respects the target model's tokenizer and total input limit, reserving space for mandatory runtime instructions, the user request, tool definitions, and the required output allowance. If mandatory content does not fit, the runtime uses an explicit overflow policy; it does not silently discard authority or safety constraints.

Retrieval occurs automatically at session start and lightly at user turns. Deeper search is available when needed. Before consequential action, refresh relevant state and permission checks. Relevance decay affects selection, not historical existence or obligation validity.

### 9.5 Suppression

“Do not surface this proactively” is a scoped preference separate from deletion. Direct authorized recall can still retrieve suppressed information. The interface distinguishes proactive suppression, correction, access restriction, quarantine, and deletion so a user can predict their consequences.

## 10 Invocation accountability and incident recall

### 10.1 Complete runtime manifests

The instrumented runtime commits an immutable input manifest before dispatching a model invocation. It records the exact runtime-visible input sequence, not only the memory items selected by search.

```text
InvocationManifest {
  invocation_id, principal, tenant, runtime_version
  model_identifier, provider, configuration_ref
  ordered_inputs: [{immutable_ref, selected_span_or_transform_ref,
                    role, rendered_revision, security_metadata}]
  procedure_versions, tool_schema_versions
  compaction_and_template_versions, tokenizer_version
  policy_decision_refs, snapshot_position
  aggregate_restrictions, input_coverage, committed_at
}

InvocationOutcome {
  invocation_id, output_refs, proposed_action_refs
  provider_receipt?, status, completed_at
}
```

Outcomes are appended separately because they do not exist when the input manifest is sealed. A manifest reference is not a hidden copy of its source content. References, rendered fragments, templates, and transformations must collectively recover the actual input while retained; newly materialized text is a protected derived object with deletion dependencies.

Provider-internal prompts, hidden transformations, or state unavailable to the runtime are declared limitations. Accountability covers the submitted runtime-visible context, not inaccessible provider internals or model pretraining. Unsupported persistent provider sessions cannot be advertised as fully reconstructed.

### 10.2 Conservative recall

When a source, credential, procedure, extractor, or ruleset is compromised or found wrong, recall identifies affected records, traverses recorded exposure and generation links, finds judgments whose basis is affected, and lists downstream outputs and actions.

The report separates:

- recorded evidential dependence;
- potential influence through exposure;
- affected procedures or credentials;
- confirmed execution, failed execution, and uncertain action outcomes;
- instrumentation gaps and external destinations outside UPMS control.

Recall is complete only relative to the declared instrumented boundaries and recorded dependency model. It produces reassessment and remediation candidates; it cannot prove a model's actual causal reliance or undo an external action.

## 11 Scope and human control

Personal, project, team, organizational, and agent-operational scopes remain explicit. A reference across scopes does not grant access. Task purpose is supplied or approved through authenticated policy context; an agent cannot broaden its access by inventing a compatible purpose string.

Capture records the original purpose. Retrieval, processing, and disclosure check compatibility with the requested use. Derived artifacts inherit all applicable restrictions. If combining scopes produces an unusable artifact, isolate the work rather than dropping restrictions.

The user-facing product must support these questions within the proposed deliverable:

- What did you remember, from which source, and when?
- Why was this item retrieved or treated as current?
- What supports it, what contradicts it, and what remains unprocessed?
- Did my correction, suppression, revocation, or deletion take effect?
- Which recorded outputs or actions might be affected by this source?

Inspection follows the same access controls as normal retrieval. A report may explain that a decision has restricted supporting material without exposing that material. Minimal operational evidence is retained for correction, access, deletion, and action outcomes; detailed scientific-result records belong to the external systems that own them. UPMS can retain their permitted references and discussion without certifying scientific validity.

For non-users mentioned in organizational records, retain only information justified by the scope and purpose. The deploying organization must define a verified correction and visibility process that also protects other people's information. This proposal does not establish jurisdiction-specific legal compliance.

## 12 Retention and deletion

### 12.1 Retention boundaries

Retention policy applies to raw payloads, normalized claim values, extracted text, summaries, prompts, embeddings, indexes, manifests, caches, logs, and backups. Protecting only the original document is insufficient. Some data is never captured, and processor selection must respect the same restrictions before content is sent for extraction or embedding.

The canonical journal is append-only for ordinary semantic operations. Authorized deletion may erase protected payloads and sensitive metadata while retaining a minimal, opaque lifecycle record. This is an explicit exception to physical immutability, not an undocumented violation of it.

### 12.2 Encryption and deletion dependencies

Use standard authenticated encryption and a key service with explicit deletion semantics. Objects have independently addressable encryption and deletion units. The initial default is event-level source deletion and object-level derived-artifact deletion; unusually large or mixed-sensitivity sources may require smaller capture units before use.

v0.3 does not prescribe multi-source key inheritance. Deletion dependencies are an explicit relation derived from production and exposure records. For model-generated objects, all exposed retained inputs are conservative deletion dependencies unless an independently specified, tested non-model transformation establishes narrower dependence. Self-reported citations do not narrow this relation.

Deleting one source can therefore invalidate a mixed summary that also contains useful unrelated information. The remedy is to generate a new summary from surviving sources, retaining a new processing identity. An independently captured source remains usable when policy permits; deleting one occurrence does not imply that every independently obtained statement of the same fact must disappear.

Users must be able to distinguish deleting identified records from a broader request to delete retained information about a subject. The latter needs discovery across the authorized scope, candidate review where ambiguous, and explicit coverage limits. A partial discovery cannot be reported as complete subject erasure.

### 12.3 Deletion lifecycle

| Stage | Required result |
| --- | --- |
| Authorized | A valid principal or retention policy identifies the deletion target and scope |
| Serving blocked | A durable deletion barrier excludes targets and affected descendants from reads, processing, and output release |
| Purging | Payloads, searchable content, caches, protected metadata, and applicable keys are being removed or made unrecoverable |
| Complete within scope | The named controlled surfaces have met the deletion contract; evidence and remaining external limitations are reported |

Acknowledgement that serving is blocked is distinct from completion of erasure. Dependency validation prevents new descendants from being committed after the barrier. Already running jobs are canceled or their outputs withheld and purged. Unknown dependency coverage prevents an unqualified completion claim and requires containment of the affected serving scope until resolved.

An invocation cannot unsee deleted content. Its pending output cannot be released under a new manifest that omits the deleted input. A new invocation using permitted inputs is required when that dependency matters.

### 12.4 Keys and backups

Deleting a row containing a wrapped data key is not cryptographic erasure if a backup can restore that wrapper and the wrapping key still exists. The chosen key hierarchy must make the specified deletion unit unrecoverable across retained copies, or the product must report physical purge/retention expiry as the remaining completion condition.

Cached plaintext and data keys require explicit invalidation or bounded expiry. Revoking a key service operation does not necessarily invalidate an already available plaintext data key; this limitation appears in real key-management systems. [AWS KMS data-key behavior](https://docs.aws.amazon.com/kms/latest/developerguide/unusable-kms-keys.html)

Restores apply all deletion barriers, access revocations, and key-state restrictions before serving. The deletion-control record must survive restoration of an older data backup; restoring data alone cannot roll back erasure decisions. Index snapshots, database logs, and exported diagnostic bundles are included in the retention inventory.

### 12.5 Audit and replay after deletion

Deletion audit retains only the minimum permitted actor or pseudonymous actor reference, policy decision, opaque target identifiers, lifecycle status, and operational counts. Sensitive relationships, names, low-entropy plaintext hashes, and record-existence metadata must be assessed for deletion too. Retaining a fingerprint requires a justified protected construction, not an exception by convenience.

Canonical replay reproduces the surviving record state and deletion markers. It cannot reconstruct erased content or old contexts that depended on it. Rebuilding a useful artifact from surviving inputs is new computation. Information already delivered to an external recipient is listed as outside local erasure control, with any supported external deletion request tracked separately.

## 13 Technical foundation and failure behavior

PostgreSQL is the initial canonical-store candidate, with protected payloads in object storage where appropriate. Typed tables hold events, claims, judgments, lifecycle records, and dependency edges. Derived indexes provide lexical search, vector retrieval, adjacency lookup, and current projections. Separate graph infrastructure is deferred until workload evidence justifies it.

The database is not assumed to provide application-level confidentiality merely through tenant partitioning. Service credentials, row access, administrative paths, index isolation, encryption boundaries, backups, and logs are part of the deployment threat model. Searchable plaintext or embeddings remain sensitive even when the source payload is encrypted. A confidentiality label is a policy constraint; it is not encryption.

The initial implementation uses one authoritative commit path and a durable queue or transactional outbox for projections. Jobs are retryable and idempotent. Projection revisions and lag are visible; a failed index update cannot make an uncommitted fact appear canonical.

| Failure | Required behavior |
| --- | --- |
| Capture cannot commit | Do not claim the memory was saved; retry using the same ingestion identity |
| Extraction or embedding unavailable | Preserve capture and permit bounded source recall with explicit processing limits |
| Index stale or unavailable | Use a bounded permitted fallback or report incomplete retrieval; continue applying serving barriers |
| Identity or policy service unavailable | Refuse operations requiring an authorization decision that cannot be established |
| Source application unavailable | Return a visibly stale historical observation if permitted; do not present it as refreshed current state |
| Writer fails over | Fence obsolete writers and recover from committed records |
| Tool dispatch outcome uncertain | Record uncertainty; use tool idempotency or reconciliation before retrying a consequential action |
| Deletion purge fails | Keep serving blocked, retry remediation, and report incomplete erasure |
| Budget exhausted | Stop the bounded operation and expose truncation or deferred work |

A deployment profile must bind expected corpus size and event rate, concurrent users and agents, latency budgets, context limits, processing quotas, retention periods, deletion deadlines, and recovery objectives before an implementation gate can pass. These parameters are open in this early proposal; none is implied by the choice of database.

## 14 Migration and portability

Legacy files enter as captured historical aggregates with import time, original source location, available authorship evidence, scope, and capture policy. A name in a file is not authenticated authorship. Existing “accepted” or “verified” labels are imported as historical assertions unless their authority and evidence can be independently resolved.

Lazy extraction preserves links to the source aggregate and reports unprocessed portions. Partial migration cannot be presented as a complete memory corpus. A user may provide a scoped endorsement through the ordinary path; migration itself does not grant reliance permissions or activate procedures.

Portable export includes permitted records, relationships, schema versions, source references, lifecycle state, and provenance. It excludes credentials and does not export an automatic right to access another deployment. Imported endorsements retain their history but require local authority mapping before future reliance. Export and import must preserve deletion restrictions and record when evidence or payloads are unavailable.

Model independence requires storage formats and semantic identities to outlive model-specific prompts, embeddings, and tokenizers. Replacing those components creates new processing or index versions. The first release needs one instrumented runtime adapter plus adapter conformance tests, not superficial integrations with many runtimes.

## 15 Evaluation and acceptance evidence

### 15.1 Baselines and experimental discipline

Compare the first usable slice against source-preserving lexical retrieval, hybrid lexical/vector retrieval over transcript chunks, and full-history context where it fits. Later slices also compare against the previous accepted slice. Use the same accessible corpus, authorization constraints, answer model, and declared budgets where the comparison permits.

LongMemEval supplies useful tests of extraction, multi-session reasoning, temporal reasoning, knowledge updates, and abstention. LoCoMo supplies long-conversation tasks. Neither establishes UPMS's access, deletion, or action-security guarantees, which need a dedicated workload. [LongMemEval](https://arxiv.org/abs/2410.10813), [LoCoMo](https://arxiv.org/abs/2402.17753)

Separate development cases from held-out evaluation. Record corpus and harness revisions, model and judge versions, prompts, configuration, repetitions, failed runs, and all materially evaluated variants. If held-out outcomes influence a design change, report that reuse and obtain fresh evaluation before claiming an untouched holdout result. Human adjudication should inspect consequential attribution and security failures rather than relying solely on a model judge.

### 15.2 Required scenario families

| Scenario | Required observable outcome |
| --- | --- |
| Repeated deadline changes and a late-arriving correction | Correct applicable view, preserved history, explicit ambiguity where unresolved |
| A correction arrives before claim extraction | Targeted source correction takes effect or remains visibly pending clarification |
| An old injection survives summarization and compaction | Restrictions survive and an unauthorized operation is blocked |
| A schema-valid value redirects a tool call | Destination and reliance checks reject the unauthorized use |
| A private source is read before an external search or send | Confidentiality is enforced on the query or payload destination |
| Access is revoked after context assembly | Subsequent release/action is rechecked and blocked when no longer permitted |
| A human endorses one claim | Unrelated outputs, broader uses, and disclosures receive no implicit upgrade |
| A source in a mixed summary is deleted | Affected serving stops; new generation uses surviving inputs only |
| An old backup is restored after deletion | Deleted material does not become queryable or decryptable contrary to the declared contract |
| Independent evidence survives source deletion | The independent record remains available when policy permits |
| Two agents disagree or a new opposing claim arrives during assessment | Conflict is preserved; stale assessment is rejected or appropriately qualified |
| An entity match is reversed | Affected projections update without erasing original entities or leaking another scope |
| Indexing, capture, or extraction is incomplete | Coverage is visible and no unrestricted absence claim is made |
| A session ends after partial execution | Resumption distinguishes confirmed completion, uncertainty, and proposed work |
| Writer failover or tool timeout occurs | No duplicate canonical transition or blind retry of an uncertain consequential action |

Each scenario exercises the real storage, retrieval, runtime, and policy boundaries that own the behavior. A mock-only demonstration is not evidence of production enforcement. Extend adversarial cases across cooperating agents, compromised ordinary credentials, poisoned procedures, endorsement phishing, retrieval metadata leakage, and resource exhaustion.

### 15.3 Metrics and shipping rule

Measure end-task success, recall and precision at fixed context budgets, attribution fidelity, stale-current-answer rate, temporal correctness, conflict visibility, coverage accuracy, and useful task continuation. Also measure unauthorized disclosure/action attempts that succeed, legitimate operations unnecessarily blocked, confirmation burden, deletion latency, recovery correctness, and instrumentation gaps.

Report total lifecycle cost: capture, indexing, model processing, storage, retrieval, regeneration, and human attention. Report warm and cold latency distributions and degradation behavior, not just an average.

A new mechanism must satisfy required safety properties and provide a justified improvement or tradeoff on the declared workload. Equal or lower token cost is not an absolute requirement: an increase may be justified by materially better correctness or lower operational cost. The tradeoff must be stated before acceptance, with uncertainty and important regressions visible.

Zero observed violations in a test suite is bounded evidence, not a universal proof. A gate must not pass a known violation of a required invariant merely because an aggregate score improved.

## 16 Architectural invariants

These are proposed acceptance properties within a declared deployment and integration profile. The associated tests are planned obligations, not reported results.

| ID | Invariant | Evidence family |
| --- | --- | --- |
| H1 | Ordinary semantic operations append revisions; authorized deletion is the explicit payload-erasure exception | Storage audit and replay |
| H2 | Each claim and assessment resolves to recorded source/processing records or an explicit deletion/unavailability marker | Dependency and migration tests |
| E1 | Capture, epistemic assessment, admission, provenance, and permission remain distinguishable | Schema and end-to-end presentation tests |
| E2 | Conflicts and disputed derivations remain inspectable without erasing independent evidence | Reconciliation scenarios |
| A1 | Memory text cannot grant a capability or activate a procedure | Adversarial authorization tests |
| A2 | Only authorized capture and transition components commit their respective record types | Credential and API tests |
| A3 | Every reliance exception binds an exact object, scope, meaning/use, and currently applicable authorization | Endorsement and revocation tests |
| F1 | Model outputs preserve conservative exposure dependencies and all applicable confidentiality restrictions | Runtime property tests |
| F2 | Every mediated disclosure checks payload destination, purpose, and current authorization | Egress and processor tests |
| F3 | Ordinary retrieval never exposes forbidden or quarantined content, including through explanations | Tenant/scope and metadata tests |
| C1 | Every claimed instrumented invocation has a sealed manifest of its runtime-visible inputs and a separate outcome record | Adapter conformance tests |
| C2 | Recall finds all seeded dependencies within the declared instrumentation boundary and states its gaps | Seeded compromise tests |
| R1 | Acknowledged targeted corrections and serving-blocked deletions apply to subsequent retrieval and pending output release | Race and cache tests |
| D1 | No covered target or affected descendant is served after its deletion barrier, including from restored state | Deletion and restore tests |
| D2 | Deletion completion is reported only for the controlled surfaces and key/physical-purge conditions actually satisfied | Key, cache, backup, and purge tests |
| O1 | Canonical transitions are serialized within their partition and validated against relevant dependency changes | Concurrency and failover tests |
| O2 | Canonical replay uses recorded computation outputs and never repeats external actions | Replay and recovery tests |
| O3 | Context assembly fits the declared budget or returns an explicit overflow outcome | Tokenizer and boundary tests |
| O4 | Retrieval exposes material coverage and freshness limits without disclosing inaccessible records | Partial-processing and isolation tests |

## 17 Delivery plan

### 17.1 Gate 0 and implementation specification

Before the first slice, resolve review findings that affect the core contracts. Bind the deployment profile, trusted components, authority and purpose rules, operation schemas, capture/deletion units, numerical resource targets, retention deadlines, and required adapter coverage. Define concrete correction and endorsement interfaces and choose the initial evaluation corpus.

Output: a bounded implementation specification and executable acceptance cases. Cross-review of this proposal is input to that decision; it does not itself demonstrate a conforming implementation.

### 17.2 Slice 1 Reliable recall and continuity

Deliver source capture, protected storage, scoped lexical/hybrid retrieval, source-linked results, coverage reporting, task checkpoints, targeted correction, suppression, deletion lifecycle, and one instrumented runtime adapter. Support the control and provenance records needed for these features without requiring exhaustive claim extraction. Current-state questions use the owning external system or visibly limited source recall.

Security and deletion are included from the start. The slice must demonstrate its stated boundaries through end-to-end scenarios, recovery tests, and user inspection flows. It must deliver a measured continuity or recall benefit against simple baselines at an acceptable declared total cost.

### 17.3 Slice 2 Structured claims and judgments

Add lazy claim extraction, scoped assessment, temporal projections, reversible entity matches, conflict presentation, and limited endorsement. Demonstrate improvement on updates, contradictions, temporal questions, and correction handling without weakening Slice 1 guarantees.

Extraction fidelity, unsupported normalization, and stale assessments are primary failure measures. Claims that remain unprocessed continue to be available as source records with explicit limits.

### 17.4 Slice 3 Selective sophistication

Consider graph-assisted retrieval, richer assurance, more adapters, and broader collaboration only for demonstrated gaps. Each addition needs an ablation or equivalent comparison, lifecycle/security coverage, and a documented cost tradeoff. Source-quality scoring, general logical inference, specialized graph storage, and cross-organization federation remain deferred unless independently justified.

## 18 Decisions requested from cross-review

Reviewers should first challenge whether the proposed guarantees follow from the specified boundaries. The most consequential unresolved decisions are:

1. **Product focus:** Is continuing project work the right first workload, and which real sessions can be used with permission for evaluation?
2. **Runtime coverage:** Can the intended runtime mediate all relevant model inputs, outputs, tools, and processor disclosures? What remains outside its control?
3. **Integrity policy:** Which protected uses need source restrictions or reliance endorsements, and can those policies remain useful without frequent confirmation?
4. **Assurance rules:** Which limited claim domains have criteria strong enough for admission, and which should remain evidence-only?
5. **Deletion granularity:** Is event-level source deletion practical, and what collateral invalidation is acceptable for mixed summaries and checkpoints?
6. **Key and backup design:** Which concrete key hierarchy and retention arrangement can satisfy the chosen deletion-completion contract?
7. **Correction targeting:** How should the interface resolve ambiguous corrections without silently suppressing other people's evidence?
8. **Judgment scope:** Which domain rules, if any, can reconcile conflicting assessments across scopes without choosing the most permissive one?
9. **Operational limits:** What corpus, concurrency, latency, context, processing, deletion, and recovery budgets define the first deployment?
10. **Simplification:** Can any proposed record or boundary be removed while preserving the stated user journeys and invariants?

A useful review finding identifies the affected section or invariant, a concrete counterexample, its consequence, and a proposed alternative with costs and verification criteria. Distinguish defects in this architecture from implementation choices it deliberately leaves open. Reviewers should challenge unsupported guarantees even when the individual components are familiar.

## 19 Research basis and claim limits

The following sources inform specific design choices; they are not evidence that UPMS implements or inherits those systems' results.

| Source | Relevance | Limit on use here |
| --- | --- | --- |
| [W3C PROV-DM](https://www.w3.org/TR/prov-dm/) | Vocabulary for provenance, activities, usage, generation, and derivation | Provenance does not establish factual truth or model causal reliance |
| [CaMeL](https://arxiv.org/html/2503.18813v1) | External data/control-flow enforcement and limitations of untrusted structured values | Its guarantees depend on its interpreter and policy model |
| [Fides](https://www.microsoft.com/en-us/research/publication/securing-ai-agents-with-information-flow-control/) | Confidentiality/integrity enforcement and security–utility tradeoffs | UPMS requires its own runtime contract and evaluation |
| [LongMemEval](https://arxiv.org/abs/2410.10813) | Long-history extraction, reasoning, updates, and abstention evaluation | Does not replace UPMS-specific governance tests |
| [LoCoMo](https://arxiv.org/abs/2402.17753) | Long-conversation memory evaluation | Public tasks are starting points, not the whole target workload |
| [HippoRAG](https://arxiv.org/abs/2405.14831) | Graph-assisted associative retrieval using Personalized PageRank | Motivates an optional experiment, not an initial dependency |
| [AWS KMS data-key behavior](https://docs.aws.amazon.com/kms/latest/developerguide/unusable-kms-keys.html) | Concrete example of cached data keys surviving key-service unavailability | A chosen deployment needs its own full erasure analysis |

## Appendix A Changes from earlier proposals

| Earlier idea | v0.3 treatment | Reason |
| --- | --- | --- |
| Event, Claim, Judgment | Preserved with explicit evidence and exposure relations | Keep the simple model while separating different meanings of dependency |
| External authority | Preserved and clarified at every use boundary | Historical permission references cannot authorize new actions |
| Universal I0–I3 trust hierarchy | Replaced by provenance, integrity constraints, confidentiality, and scoped endorsement | Authentication, correctness, and permitted reliance are different dimensions |
| Whole-context taint | Preserved conservatively, with explicit adapter coverage | Avoid unsupported claims about per-span model influence |
| Schema-constrained quarantined reader | Retained as an isolation technique, without a safety guarantee from schema alone | Valid structured data can still redirect actions |
| Endorsement raises a judgment's integrity | Replaced by typed attestation and exact-use reliance exceptions | Prevent silent provenance upgrades and approval spillover |
| One lineage mechanism for truth, security, and deletion | Typed relations in one store | Preserve evidence distinctions and make conservative deletion cost explicit |
| Multi-source key inheritance | Replaced by explicit dependencies and a deletion lifecycle | Avoid an unspecified cryptographic construction and hidden backup assumptions |
| Exact incident causal recall | Conservative recall with separate evidence and exposure paths | Runtime exposure does not reveal model causation |
| Exact reconstruction of all derived state | Separate replay, context reconstruction, and retrieval rebuild contracts | Approximate indexes and new inference have different reproducibility limits |
| Eager capture, lazy understanding | Preserved; embeddings and most indexing are asynchronous | Keep ingestion durable and its latency bounded |
| Source reliability scores | Deferred | Avoid circular outcomes, correlated evidence, and indirect person scoring |
| Baseline-gated vertical slices | Preserved with total lifecycle cost and explicit safety floors | Token count alone is an incomplete engineering objective |
| Root manifest and task checkpoints | Preserved with correction, deletion, and revision checks | Continuity must not become a second authority |

v0.1 already placed final permission enforcement outside its authority graph, permitted asynchronous semantic processing, and required security from the foundation. v0.2 strengthened those boundaries. v0.3 continues that refinement rather than treating those concerns as newly introduced.

## Appendix B Source document identities

The source proposals are retained unchanged. These SHA-256 digests identify the files used for this revision; they are document provenance, not an endorsement of their contents.

```text
UPMS Architecture Proposal v0.1.md
a93d65cd28fcb8a471206cb31bd262525fdcac8d327730b9d589b94300240a40

UPMS Architecture Proposal v0.2.md
ba07773e5b1f4a815636499891712892d2d27d8a7a9b18e097f7f5fba827bcb0
```
