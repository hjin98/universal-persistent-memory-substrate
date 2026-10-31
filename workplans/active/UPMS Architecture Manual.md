# UPMS Architecture Manual

Oct 30, 2026 · @Sam

## 1. Status and Authority

**Status: proposed D3 architecture, not accepted-current.** This manual formalizes the UPMS v0.3 proposal and the architecture review of 30 October 2026 into one normative architecture surface. It becomes accepted-current only through the owning acceptance process: independent cross-review that attempts to falsify it, followed by explicit acceptance by the product owner.

### 1.1 Governing inputs

| Input | Role |
| --- | --- |
| UPMS Architecture Proposal v0.3 (30 October 2026) | Stakeholder requirements, product boundary, record model and invariants |
| Architecture review of v0.3 (30 October 2026) | Seven findings incorporated as proposed D3 decisions (marked **\[R1\]**–**\[R7\]**) plus smaller corrections |
| Software Design protocol, SSDP 7.2.1 | Form of this manual: one owner per claim, structured contracts, delegated D4 space, reopen triggers |

There is no scientific (D1) or numerical-method (D2) parent. Section 1.5 records that determination, its basis, and the triggers that would reopen it.

### 1.2 What this manual owns

Component and state ownership, interfaces between components and external owners, data and control flow, persistence and recovery, concurrency, trust boundaries, lifecycle state machines, resource-bound structure, deployment-profile structure and architectural invariants.

It does not own the identity and policy system, key management, connected systems of record, model behavior, or concrete implementation choices (Section 17).

### 1.3 Decision status markers

- **Fixed (proposed):** a D3 decision this manual makes; binding on implementation once the manual is accepted.
- **Default (proposed):** a value or rule a deployment profile may tighten; loosening requires a recorded policy-owner decision.
- **Open:** unresolved; Section 18 names the gate that must close it.

### 1.4 Scientific realized records

None material, because UPMS does not produce, transform or certify scientific results. Where it retains discussion of results owned by external systems, it stores references and attributed statements only. Re-evaluate if a deployment makes UPMS the retention home for realized scientific records.

### 1.5 Domain determination

**The top governing authority is D3, under the stakeholder requirements in 1.1.** UPMS's governed outcome is an engineering contract (provenance, information flow, correction, deletion, continuity), not a scientific question whose answer the software computes, and no consumer relies on a numerical approximation guarantee. Empirical work still shapes the system, but what it discovers is which implementation choices and policy defaults satisfy the D3 contract; the contract itself is fixed in advance.

| Content that resembles D1 or D2 | Owner here | Basis |
| --- | --- | --- |
| Epistemic statuses, evidence independence | D3 categories (5.3); per-domain rulesets owned by deployment policy | No truth model is asserted; each ruleset defines support for its own domain |
| Integrity and confidentiality propagation, grounding | D3 security (7, 8) | Deterministic predicates; security semantics attach at D3 |
| Bitemporal time, imprecise intervals | D3 data model (5.6) | Records what was stated or believed, not objective truth |
| Ranking, approximate indexes, context selection | Delegated implementation (17.1) | Quality is judged end to end; the hard constraints (eligibility, budget fit) are exact D3 rules |
| Gate evaluations | Evidence specification bound to D3 gates (15) | Empirical and decision-sensitive, but product acceptance rather than scientific authority |

**Reopen triggers.** A D1 or D2 determination is required before design when:

1. source-reliability scoring or any calibrated numerical confidence is introduced (D1 defines what is estimated; D2 owns the estimator, prior and uncertainty);
2. a gate or consumer comes to rely on a guaranteed approximation bound, such as retrieval recall or iterative-method convergence (D2);
3. UPMS becomes the retention home for realized scientific records or for scientific projects' memory. Section 1.4 is then re-evaluated, those projects' authority semantics become an external contract on this manual, and their D1 governs any admission ruleset in their domains.

## 2. Background and Terminology

**UPMS (Universal Persistent Memory Substrate) is a model-independent memory service: it preserves what agents encountered, keeps revisable assessments of it, and supplies the metadata an instrumented runtime needs to enforce permitted use.** The terms below are used normatively throughout; each is defined once here and owned by the section named.

| Term | Definition | Owner |
| --- | --- | --- |
| Event | Immutable record of what an authenticated capture component observed | 5.1 |
| Claim | Statement extracted from an event or proposed by reasoning; carries no truth, admission or permission by itself | 5.2 |
| Judgment | A process's scoped, dated assessment of one claim revision under a named ruleset | 5.3 |
| Control record | Endorsement, correction, suppression, redaction, deletion, procedure activation, policy reference or receipt | 5.4 |
| Evidence relation | `supports`, `opposes`, `supersedes`, `retracts`, `same_as`: an assessor's statement about meaning | 5.5 |
| Exposure relation | `observed_from`, `exposed_to`, `generated_by`: a runtime observation of data flow | 5.5 |
| Source class | Provenance fact about how a span originated: authored, relayed, connector-declared, external or model-generated | 7.1 |
| Dependency set | The conservative set of retained inputs an object was exposed to, transitively | 8.2 |
| Protected use | An action or disclosure whose consequence class has an integrity rule | 7.2 |
| Reliance endorsement | Authorized permission for one protected use to rely on one exact value | 7.4 |
| Instrumented runtime | An adapter that captures every runtime-visible input and mediates every output path | 8.1 |
| Handle | An opaque reference to an untrusted value, visible to planning without its content | 8.3 |
| Context manifest | Sealed record of the exact runtime-visible input sequence of one model invocation | 11.1 |
| Serving barrier | Durable restriction that blocks reads, processing and output release for targets and descendants | 12.3 |
| Transition owner | The single logical committer of canonical records within a tenant partition | 9.1 |
| Snapshot position | Ordered commit position at which a read or assessment was taken | 9.1 |
| Coverage | What a result could and could not consider: captured, indexed, processed, available | 10.3 |

**Abbreviations:** MCP (Model Context Protocol), KMS (key-management system), TCB (trusted computing base), D3/D4 (architecture/implementation-specification domains of the Software Design protocol).

## 3. Architecture at a Glance

**The mechanism in brief:** three record types (Event, Claim, Judgment) and lifecycle control records live in one memory core with a single committer per tenant partition. Two relation families keep meaning and data flow apart: evidence relations explain beliefs; exposure relations drive security, deletion and recall. Two integration profiles bound what can be claimed: a plain memory service guarantees scoped retrieval, correction and deletion; only an instrumented runtime, which seals every invocation's inputs, propagates dependencies and checks every dispatch, can claim end-to-end information-flow properties. Permission always comes from the external policy system.

&#91;embedded content: component architecture · four internal components, external owners\]

Content enters through the runtime with its source classes, is committed only by the memory core, and leaves only through eligible retrieval or a checked dispatch.

## 4. Ownership Map

**Every durable state and decision has exactly one owner; no component may write another's state except through that owner's interface.** The four internal boundaries are responsibility boundaries with separate credentials, not mandatory separate network services. **Fixed (proposed).**

### 4.1 Internal components

| Component | Owns | Exposes | Must not |
| --- | --- | --- | --- |
| Memory core (transition owner) | Canonical records, revisions, commit positions, transition validation, serving barriers, retention and deletion state | Typed lifecycle operations (4.3) | Decide external truth; grant permissions; call models during replay |
| Processing workers | Nothing durable; produce proposals and processing records | Proposals submitted to the memory core | Commit canonical state; change labels, admission or policy; send restricted content to an unpermitted processor |
| Retrieval service | Derived indexes, current-state projections, context selection, coverage reporting | `search`, `get_context`, `expand`, `get_evidence` | Treat ranking as admission; expose ineligible content or its metadata |
| Runtime adapter (instrumented profile) | Invocation capture, context manifests and outcomes, span source marking, dependency propagation, handle store, action and disclosure checks, procedure loading | Capture events, manifests, outcomes to the memory core; mediated dispatch to tools | Rewrite provenance; infer user authority; release output whose dependencies fail a check |

### 4.2 External owners

| Owner | Owns | UPMS relationship |
| --- | --- | --- |
| Identity and policy system | Authentication, capabilities, delegation, revocation, purpose compatibility, integrity and confidentiality policy decisions | Consulted at capture, retrieval, processing disclosure, endorsement, deletion and dispatch; UPMS stores decision references only |
| Key-management system (KMS) | Key lifecycle and destruction | Wraps per-unit data keys; destruction semantics bound in the deployment profile (14) |
| Systems of record (repositories, trackers, calendars) | Their own current state | Authoritative for current-state questions; UPMS keeps references and surrounding history |
| Model providers | Inference | Treated as processors: receive only content whose confidentiality restrictions permit that provider |
| Tools and destinations | Effects outside UPMS | Reached only through mediated dispatch in the instrumented profile |

### 4.3 Operation ownership

| Operation family | Permitted caller | Committed by |
| --- | --- | --- |
| `record_event`, `record_manifest`, `record_outcome` | Capture component or instrumented runtime | Memory core |
| `search`, `get_context`, `expand`, `get_evidence` | Authorized runtime or agent | Read-only (retrieval service) |
| `propose`, `report_conflict`, `request_assessment` | Agent or worker | Memory core, as candidates without admission |
| `correct`, `suppress`, `redact` | Authorized principal | Memory core |
| `endorse`, `revoke_endorsement` | Principal with the scope capability | Memory core, after a policy decision |
| `delete`, `deletion_status` | Authorized principal or retention controller | Memory core |
| `recall` | Authorized operator | Read-only, with controlled disclosure |

No operation writes labels, judgments, permissions, reliability values or procedure activation directly. User-interface actions and background controllers use the same operations. MCP and other transports are adapters over this typed interface and inherit its authentication and scoping.

## 5. Durable Records

**Three semantic record types (Event, Claim, Judgment), one family of control records, one processing record, and one typed relation store make up all canonical state.** Field lists fix semantics, not serialization; the concrete schema is D4. **Fixed (proposed).**

Every record carries: opaque ID, tenant, scope, purpose, schema version, commit position, committed time, retention class and security metadata (source classes, dependency reference, confidentiality restrictions).

### 5.1 Event

```text
Event {
  channel, witness_principal, transmitter_identity?
  origin_identity?, origin_authentication_evidence?
  payload_ref                 // protected deletion unit (12.1)
  spans: [{range, source_class, origin_ref?}]   // [R3] from the adapter
  source_message_id?, source_revision?
  observed_at, stated_occurrence_time?
}
```

Only a capture component appends observation events. An agent's report of completed work is recorded as the agent's statement; completion needs its own basis (a receipt or inspected artifact). Changed source content creates a new event revision; nothing is overwritten.

### 5.2 Claim

```text
Claim {
  statement_ref, source_locators[]    // original wording always recoverable
  normalized_statement?               // only if negation, quantity, units, conditions,
                                      // attribution and uncertainty are preserved
  modality, qualifications, asserted_by?
  valid_time, temporal_basis
  generated_by                        // processing record or capture
}
```

Modalities: asserted, quoted, hypothesized, intended, committed, preferred, normative. Each modality's lifecycle is owned by 6.1. A sentence that cannot be normalized safely stays a source-linked textual claim.

### 5.3 Judgment

```text
Judgment {
  claim_id, claim_revision, scope
  epistemic_status        // supported | refuted | contested | unknown
  admission_state         // captured | evidence_only | admitted | quarantined
  supporting_refs[], opposing_refs[], qualification_refs[]
  assessor, assessment_output_ref?, ruleset_version
  read_dependencies[], snapshot_position     // [R6] freshness, 9.3
  applicable_time, supersedes?
}
```

Epistemic status and admission are separate fields. Status categories are defined by the named ruleset, not by a general logic; repeated copies of one source are not independent support, and model self-reported confidence is never a support criterion.

### 5.4 Control and processing records

Control records: endorsement, endorsement revocation, correction, suppression, redaction, deletion request and status, procedure version and activation, authorization-decision reference, action receipt. Each has its own lifecycle in Section 6.

```text
ProcessingRecord {
  kind, invoker, input_manifest_ref
  model_or_program_version, prompt_or_program_ref, configuration_ref
  output_ref, outcome          // completed | partial | failed
  started_at, completed_at
}
```

Reprocessing creates a new processing record. Failed and partial attempts never present as completed assessment.

### 5.5 Relations

| Relation | Kind | Asserted by | Use |
| --- | --- | --- | --- |
| `observed_from` | exposure | capture component | attribution, ingestion audit |
| `exposed_to` | exposure | instrumented runtime | information flow, deletion dependency, recall |
| `generated_by` | exposure | memory core | production lineage |
| `supports`, `opposes` | evidence | assessor | explanation, assessment |
| `supersedes`, `retracts` | evidence | correction or assessor | current-state projections |
| `same_as` | evidence | assessor, subject to judgment | reversible entity resolution |

Exposure relations are runtime observations and never depend on model-reported citations. Evidence relations are assessments with their own author and status. Security, deletion and recall use exposure relations; explanation and assessment use evidence relations.

### 5.6 Identity and time

- IDs are opaque, stable and never reused. Integrity digests are separate from identity, tenant-scoped, and deleted with their payload; a plaintext content hash never becomes a durable identifier.
- Entities are never physically merged; `same_as` is a scoped claim. Equality expansion never grants access to a restricted entity.
- Records are bitemporal: valid time (what period a statement describes) and transaction time (commit position and time). Valid time supports durations, imprecise ranges and unknown. Relative expressions keep the raw text, source timestamp, timezone if known, and resolution basis.

## 6. Lifecycle State Machines

**Every lifecycle change is an appended control record or a new judgment committed by the memory core; no state is edited in place.** Deletion and access denial override every state below; the deletion lifecycle is owned by 12.3. **Fixed (proposed).**

### 6.1 Claim lifecycles by modality

| Modality | States | Leaving a state requires |
| --- | --- | --- |
| asserted | current → stale → superseded | validity window expiry; a `supersedes` relation |
| quoted | recorded | never changes; inner content judged as its own claim |
| hypothesized | open → supported / refuted / abandoned | investigation outcome or explicit abandonment |
| intended | active → completed / abandoned / superseded | completion evidence (receipt or artifact), or a later statement by the intending principal |
| committed | open → fulfilled / released / overdue | fulfillment evidence; release by the counterparty; due time passing |
| preferred | in force → superseded | a later preference by the same principal in the same scope |
| normative | referenced → in force / repealed | the referenced authority source; memory text alone never changes it |

Declining retrieval priority never changes these states.

### 6.2 Judgment and admission

| From | To | Trigger | Guard |
| --- | --- | --- | --- |
| (no judgment) | — | event committed | behaves as `captured`; absence of a judgment is never admission |
| captured | evidence\_only | assessment committed | ruleset does not permit admission |
| captured or evidence\_only | admitted | assessment committed | admission rule satisfied (7.5); judgment fresh (9.3) |
| any | quarantined | content-analysis flag, compromised source, recall | none: restriction may always be added |
| quarantined | prior state | investigator release | authorized investigation capability; recorded decision |
| admitted | new judgment | new opposing claim, correction, ruleset change | reassessment is a new judgment that supersedes; the old one is kept |

An assessor cannot select a more permissive ruleset than the scope's policy assigns.

### 6.3 Correction

| From | To | Trigger | Guard |
| --- | --- | --- | --- |
| requested | applied | target resolved | principal may correct the target: their own statement, or an agent-generated claim about themselves |
| requested | proposed\_to\_owner | target is another principal's statement | disagreement never suppresses another's evidence |
| requested | pending\_clarification | target ambiguous | affected known items withheld or marked pending |
| pending\_clarification | applied / withdrawn | principal clarifies or withdraws | — |
| proposed\_to\_owner | applied / rejected | owning principal decides | — |

On `applied`, one transaction commits a `retracts` or `supersedes` relation and a serving restriction effective at acknowledgement (9.4).

### 6.4 Endorsement

| From | To | Trigger | Guard |
| --- | --- | --- | --- |
| presented | valid | principal confirms | policy decision grants the endorse capability for this scope and type; UI showed exact object, meaning and use |
| valid | revoked | revocation | — ; triggers reassessment and recall where dependents exist |
| valid | expired | validity condition ends | — |
| valid | invalid | endorsed object gets a new revision | a changed object needs a new endorsement |

Types: extraction fidelity, factual attestation, permitted reliance (7.4).

### 6.5 Procedure

| From | To | Trigger | Guard |
| --- | --- | --- | --- |
| draft | approved | authenticated approval of exact bytes | approver holds the procedure capability for the scope |
| approved | active | activation record | scope and applicability declared |
| active | suspended / revoked | authorized decision or recall | — |
| any | (new draft) | edit | every change is a new version starting at draft |

Agent-proposed procedures enter as drafts and are inert. The runtime loads only active versions and checks current capability at each load.

### 6.6 Suppression

`active ↔ lifted`, by the scope's authorized principal. Suppression removes items from proactive retrieval only; direct authorized recall still returns them.

## 7. Trust Model

**Provenance is recorded as facts (source classes); trust decisions are policy rules evaluated over those facts at protected uses.** There is no trust ladder and no operation that raises an object's trust. Authentication establishes who sent bytes, never that their content is correct or authored by the sender.

### 7.1 Source classes \[R3\]

| Class | Assigned to | Assigned by |
| --- | --- | --- |
| A — authored | spans typed by the authenticated principal, in an adapter that marks paste and attachment spans | runtime adapter, at capture |
| R — relayed | spans pasted, attached, forwarded or quoted by an authenticated principal; **all chat text from an adapter without span marking** | runtime adapter, or capture default |
| C — connector-declared | fields a connector contract declares as produced by the connected system itself (a commit id, a calendar time) | connector contract, configured independently of content |
| X — external | web content, inbound third-party messages, connector fields declared untrusted, unknown origin | capture default |
| M — model-generated | every output of a model invocation | runtime adapter |

**Propagation (Fixed):** an object's source-class set is the union of its own spans' classes and the classes of everything in its dependency set (8.2). A model output always carries M plus every class in its context manifest. Content analysis may add restrictions; nothing assigns A, R or C from content.

Span marking is an adapter conformance requirement (14.2). Without it, almost no user text can qualify as authored, and first-party memory collapses into relayed memory.

### 7.2 Default integrity policy \[R1\]

A **target-binding argument** is an operation argument that selects where data goes or what is affected: recipient, URL or host, path, account, amount, permission subject. Operation contracts declare which arguments are target-binding; an operation without a contract is treated as C4.

A target-binding argument is **grounded** if its exact value (a) appears literally in an A or C span of the invocation's manifest, (b) resolves from a handle (8.3) whose value has class C, (c) carries a valid reliance endorsement for this use, or (d) is confirmed by the acting principal for this dispatch. Grounding is checked by the runtime, deterministically, never by the model.

| Class | Examples | Default rule (proposed) |
| --- | --- | --- |
| C0 internal read | memory search within the caller's scope | confidentiality checks only |
| C1 reply to the requesting principal | chat answer | allowed; retrieved R, X content rendered with attribution |
| C2 reversible internal write | memory proposal, draft, sandbox file | allowed; the record carries its source-class set |
| C3 external disclosure or write | send a message, external search query, HTTP fetch, tool write | every target-binding argument grounded; payload passes confidentiality for the destination; if the payload's class set contains X, per-action confirmation showing the payload |
| C4 irreversible, financial, permission-changing, or uncontracted | delete external data, payment, grant access | C3 rules plus per-action confirmation by the authorized principal |

**Public-segment exception (Default, proposed):** a C3 *read* (fetch, external search) need not ground its target-binding arguments when every confidentiality tag in the invoking segment's dependency set permits the destination, so the request cannot carry restricted content. This lets an isolated reader segment (8.3) browse untrusted material without per-link confirmation; its outputs still carry X.

Deployment policy may tighten these defaults. Loosening one requires a recorded policy-owner decision. The X-payload confirmation in C3 is the default most likely to cost usability; its burden is measured before Gate 1b (18, O-3).

### 7.3 Confidentiality

Confidentiality is a set of restriction tags (scope, purpose, sensitivity class, permitted processors). A recipient, destination or processor must satisfy every tag. Derived objects carry the union of their inputs' tags. Declassification is disabled in the initial deployment; if enabled later it binds an exact output, destination, purpose, current capability and audit record. Summarization, endorsement and read permission never declassify.

### 7.4 Endorsement semantics

An endorsement binds: exact object revision, claim or field, type, scope, intended use, endorser, policy decision, validity conditions.

- **Extraction fidelity:** the representation matches the identified source.
- **Factual attestation:** the endorser asserts the claim under the stated qualifications.
- **Permitted reliance:** one protected use may rely on one exact value; grounds that value under 7.2(c).

An endorsement never changes source classes, provenance or confidentiality, never authorizes an action, and never extends to other outputs of the same invocation or later summaries. Batch endorsement may not hide differing scopes, uses or qualifications.

### 7.5 Default admission rule

**Default (proposed):** a claim may be admitted as an attributed first-party claim ("P stated …") when its originating span is class A by principal P; its modality is preferred, intended or committed, or it is asserted about P; and its scope is P's personal scope or a project scope P belongs to. All other claims stay evidence\_only until a domain ruleset admits them. Claims whose class set contains only X are never admitted by the default ruleset.

### 7.6 Threat model and trusted computing base

Assumed attacker capabilities: control of external content and untrusted connector fields; delayed memory injection; a cooperating malicious agent; compromise of an ordinary user or agent credential; misleading an authorized endorser; exfiltration, unauthorized change, false memory, cross-scope disclosure and resource exhaustion attempts.

TCB: memory core transition owner, serving barriers and egress enforcement, capture and manifest instrumentation, identity and policy system, KMS, and infrastructure isolation. Compromise of the TCB is outside the protection this architecture claims. A compromised ordinary credential keeps its legitimate permissions until revoked.

## 8. Runtime Flow Model and Action Boundary

**Information-flow guarantees exist only in the instrumented profile, where the runtime records every input, propagates dependencies conservatively, keeps untrusted values behind handles, and checks every dispatch.** Retrieval filtering alone reduces exposure but guarantees nothing about actions.

### 8.1 Integration profiles

| Guarantee | Memory-service profile | Instrumented-runtime profile |
| --- | --- | --- |
| Scoped, eligible retrieval with coverage | yes | yes |
| Correction, suppression, deletion barriers on UPMS surfaces | yes | yes |
| Complete context manifests | no | yes, within declared coverage |
| Dependency propagation through model outputs | no | yes |
| Action and disclosure checks (7.2, 8.4) | no | yes, on mediated paths |
| Incident recall through outputs and actions | memory surfaces only | yes, within declared coverage |

An adapter declares its supported input modalities, tools, destinations, provider behavior and known bypasses. Undeclared coverage is reported as a gap, never assumed. A transport (for example MCP) does not establish the instrumented profile by itself.

### 8.2 Conservative propagation

Every model invocation is an opaque transformation. **Fixed:** its outputs' dependency set is the union of all runtime-visible inputs (messages, retrieved items, tool results, procedures, compacted context); confidentiality tags and source classes follow by union. Dependency sets are stored by reference, not copied transitively. A deterministic transformation may declare a narrower dependency contract only if it is specified and tested. Model-reported citations or influence estimates never narrow dependencies.

### 8.3 Segments and handles \[R2\]

Without a structural remedy, conservative propagation accumulates: one untrusted read early in a session restricts every later output. **Fixed (proposed):** the instrumented adapter bounds accumulation with three mechanisms.

1. **Segments.** A segment is a sequence of invocations sharing an accumulating context; its dependency set only grows. Untrusted reading runs in a separate reader segment.
2. **Handles.** A reader segment returns values to the planning segment as handles: `{handle_id, declared_type, source_classes, confidentiality_tags}`, without the value. The planner can pass a handle as a tool argument; the runtime resolves it at dispatch and applies 7.2 to the resolved value. A handle's content enters the planner's context only through an explicit unwrap, which imports its classes and tags.
3. **Deterministic segment reset.** The runtime may start a new planning segment from a context assembled deterministically from committed records whose class sets suit the coming work. A model-written summary of a tainted segment carries that segment's classes and cannot be used to reset.

Schema validation of a reader's output constrains its shape, not its safety: a valid address can still redirect an action, which is why dispatch checks resolved values, not schemas.

### 8.4 Dispatch checks

Before executing a tool call or releasing any output, the runtime:

1. Resolves the operation through its registered contract (target-binding arguments, consequence class, effects). No contract means C4.
2. Resolves handles and computes each argument's dependency set and source classes from the actual invocation and handle records.
3. Obtains a current capability decision for this principal, action and target.
4. Checks the payload's confidentiality tags against the destination, recipient, processor and purpose.
5. Applies the 7.2 rule for the consequence class, including grounding and confirmations.
6. Revalidates corrections, serving barriers, revocations and external preconditions, and binds the decision to the exact argument values and revisions.
7. Dispatches (with the tool's conditional-write precondition where available), then records the outcome: completed, blocked, failed or uncertain.

Where a tool offers no precondition mechanism, the weaker guarantee is reported and a bounded dispatch authorization is used; atomicity across an uncontrolled service is never claimed. Permission uncertainty fails closed for the affected operation only.

### 8.5 Egress paths

All of these are disclosure paths and pass 8.4: user-facing replies, inter-agent messages, search query strings, network requests, tool arguments, logs and diagnostics, exports, embedding services and model-provider inputs (including UPMS's own processing workers). Permission to send is distinct from permission to disclose a particular payload to a particular destination.

### 8.6 Resource bounds

Capture enforces size, format, nesting and decompression limits before parsing. Retrieval, graph expansion and context assembly enforce result, hop, time and token limits. Agent-triggered processing is quota-limited per principal. Repeated retrieval and feedback never raise admission, reliability or authority. Investigation of quarantined material runs in isolated contexts with restricted egress. Concrete limits are deployment-profile bindings (14).

## 9. Commit, Concurrency, Freshness and Corrections

**One logical transition owner per tenant partition serializes canonical commits; assessments are valid as of a stated snapshot, and staleness is a visible, bounded property rather than a hidden one.**

### 9.1 Transition owner

**Fixed (proposed):**

- Exactly one logical transition owner commits canonical records per tenant partition. It is an ownership constraint, not a single permanent process; failover uses fencing tokens so a former writer cannot commit.
- A commit validates caller authority and declared dependencies, appends records, advances revisions and, in the same transaction, durably schedules projection work (transactional outbox).
- Ingestion is idempotent on `(tenant, channel, source_message_id, source_revision)`.
- Ordering uses commit positions, never wall-clock timestamps. Transactions never span tenants; cross-scope reads within a tenant use one consistent snapshot plus current eligibility checks.

### 9.2 Capture path

Synchronous, before acknowledging retention: authenticate the channel; apply capture policy and never-store rules; assign span source classes and confidentiality tags; protect the payload; append durably. If the append fails, the system does not report the memory as saved.

Asynchronous, after commit: full-text indexing, embedding (only through processors permitted by the content's tags), claim extraction, entity matching and assessment.

### 9.3 Judgment freshness \[R6\]

**Fixed (proposed):** a judgment is valid **as of** its snapshot position. Commit-time validation checks only the rows the assessment actually read (optimistic concurrency); it does not attempt to detect claims inserted after the snapshot.

- A newly committed claim touching the same entity and predicate as an existing judgment's claim enqueues reassessment of that judgment.
- Admission and reliance at C3 or C4 require a judgment younger than the profile's staleness bound and with no pending reassessment; otherwise the claim is served as evidence with its qualification.
- Every presentation of a judgment shows its "assessed as of" position.

This replaces predicate-level conflict detection, which was expensive and left undefined, with a visible freshness contract.

### 9.4 Corrections and read-your-writes

For an authorized, unambiguous target (6.3), one transaction commits the `retracts` or `supersedes` relation and a serving restriction effective at acknowledgement, and invalidates dependent projections, working sets and checkpoints. Retrieval overlays commits beyond the index watermark with a bounded direct scan, so acknowledged corrections are visible immediately. An invocation already holding the old item cannot release its output; the runtime withholds it and regenerates. A correction bound to an event or span applies even before claims are extracted.

### 9.5 Lazy processing

Triggers: explicit request, unresolved obligations, retrieval need, consequential reliance, and a bounded background budget. The background budget includes an age-weighted sweep so items rarely retrieved but important (obligations, normative claims) are not starved. Basic recall never depends on deep processing.

### 9.6 Reconstruction contracts

| Contract | Guarantee | Not guaranteed |
| --- | --- | --- |
| Canonical replay | Record states and deterministic projections rebuilt from retained records, recorded processing outputs and versioned reducers | Erased content; model re-invocation; repeated external actions |
| Historical context reconstruction | Exact runtime-visible input sequence of an invocation, within the manifest fragment retention window (11.2) | Contexts whose fragments expired or were deleted, which are reported as such |
| Retrieval rebuild | Eligible content re-indexed to declared quality criteria | Byte-identical approximate indexes or rankings |

Replay never calls a model, queries a live system or repeats an action. Historical policy references explain past decisions; new decisions use current policy.

## 10. Retrieval and Context Assembly

**Eligibility is decided before any content reaches ranking; every result states its scope, snapshot, freshness and coverage; context assembly fits a declared budget or fails explicitly.**

### 10.1 Eligibility

**Fixed (proposed):** tenant, principal, scope, purpose, quarantine, correction and serving-barrier checks constrain candidates before content is exposed to ranking, rerankers or snippet generation. A final serving check before return closes races with lifecycle changes. Approximate-search structures must not leak ineligible content through snippets, counts, explanations or timing-observable metadata. Ranking is never admission and never grants access.

### 10.2 Query intents

| Intent | Route | Required qualification |
| --- | --- | --- |
| Historical recall | hybrid lexical and vector search over accessible events and claims | attribution, time, coverage |
| Current state | owning system of record where one exists; else admitted current projections | source revision, freshness, applicability, open conflicts |
| Explanation or verification | evidence-relation and judgment traversal | supporting and opposing evidence, assessor, ruleset, "assessed as of" |
| Task continuation | current checkpoint plus changes since its watermark | confirmed completion versus proposed next steps |
| Multi-hop association | bounded relation expansion (optional, 16) | relation status and path provenance |
| Prior discussion | scoped search with declared coverage | "not found within this scope", never an unrestricted absence claim |

Absence may be asserted only for a deterministic predicate over a fully enumerated accessible corpus.

Ranking starts from lexical plus vector retrieval combined with time, task scope, explicit user priority, freshness and open obligations, with duplicate reduction. Graph methods such as Personalized PageRank are added only after a demonstrated multi-hop gap.

### 10.3 Response contract

```text
MemoryResult {
  query_id, intent, effective_scope, time_constraints
  snapshot_position, index_and_projection_versions
  items: [{object_ref, selected_span, source_refs, judgment_refs,
           source_classes, attribution, freshness, qualifications,
           confidentiality_tags}]
  coverage: {capture_extent, indexed_extent, processing_extent,
             unavailability, truncation, timeout}
  conflict_or_pending_correction_refs
  budget: {requested_tokens, selected_tokens, omissions}
}
```

Coverage is itself access-controlled: it never reveals the existence or count of records the caller cannot see.

### 10.4 Context assembly

Assembly uses the target model's tokenizer and total input limit, reserving space first for mandatory runtime instructions, the user request, tool definitions and the output allowance. Items are rendered as attributed data with compact source-class and qualification markers, never as instructions. If mandatory content does not fit, the runtime applies an explicit overflow policy and never silently drops authority or safety constraints.

Retrieval runs automatically at session start and lightly on each user turn; deeper retrieval is an explicit capability. Before any C3 or C4 dispatch, relevant state and permissions are refreshed (8.4).

### 10.5 Root manifest and checkpoints

A root manifest gives compact orientation and pointers. A checkpoint holds the objective, completed work with evidence, decisions with status, open questions, obligations, blockers, artifact references and proposed next steps, plus its generation inputs, scope, watermark and source classes. Both are derived: they establish nothing by existing. On reuse the runtime checks revisions, access, corrections, barriers and external state since the watermark; a stale checkpoint may serve as history but not as current state.

Suppression (6.6) applies to proactive retrieval only.

## 11. Accountability

**The instrumented runtime seals what every invocation saw before dispatch, keeps the reference graph long and the rendered content short, and can trace any compromised source forward to the outputs and actions it may have influenced.**

### 11.1 Context manifests

```text
InvocationManifest {
  invocation_id, segment_id, principal, tenant, runtime_version
  model_identifier, provider, configuration_ref
  ordered_inputs: [{immutable_ref, selected_span_or_transform_ref,
                    role, rendered_fragment_ref?, source_classes,
                    confidentiality_tags}]
  handles_in_scope[], procedure_versions, tool_schema_versions
  compaction_and_template_versions, tokenizer_version
  policy_decision_refs, snapshot_position
  aggregate_classes_and_tags, input_coverage, committed_at
}

InvocationOutcome {
  invocation_id, output_refs, proposed_action_refs,
  dispatch_decision_refs, provider_receipt?, status, completed_at
}
```

The manifest is committed before dispatch; outcomes are appended after. Provider-internal prompts or state unavailable to the runtime are declared coverage gaps.

### 11.2 Manifest retention \[R5\]

Manifests reference almost everything every agent saw, which makes them the most sensitive records in the store and a hub of deletion dependencies. **Fixed (proposed):** manifests are split by retention.

| Part | Contents | Retention |
| --- | --- | --- |
| Exposure skeleton | `exposed_to` and `generated_by` edges, ids, classes, tags, policy refs, outcomes | long: needed for propagation, deletion dependencies and recall |
| Rendered fragments | newly materialized text (templates, compaction output, rendered spans) needed for exact reconstruction | short, declared window (profile binding); each fragment is a protected derived object with its own deletion dependencies |

Exact historical context reconstruction (9.6) is guaranteed only within the fragment window. The skeleton never stores item content.

### 11.3 Incident recall

Given a compromised or wrong source, credential, procedure version, extractor version or ruleset, recall:

1. finds affected records and every object whose dependency set includes them, via exposure relations;
2. finds judgments whose evidence relations rely on them and enqueues reassessment;
3. finds manifests that included affected items and the outputs, proposals and dispatches they produced;
4. reports, separately: evidential dependence, potential influence through exposure, affected procedures and credentials, action outcomes (completed, failed, uncertain), instrumentation gaps, and destinations outside UPMS control.

Recall is complete only relative to the declared instrumented coverage. It identifies candidates for reassessment and remediation; it cannot prove a model's causal reliance or undo an external action.

## 12. Retention, Redaction and Deletion

**Deletion is a staged lifecycle: a durable serving barrier takes effect at acknowledgement, purge follows, and completion is reported only for the surfaces and key conditions actually satisfied.** Ordinary semantic operations are append-only; authorized payload erasure is the one explicit exception.

### 12.1 Units and surfaces

**Fixed (proposed):** the deletion unit is the event for captured sources and the object for derived artifacts; sub-event removal uses redaction (12.2). Retention and deletion cover every surface holding content: raw payloads, normalized claim values, extracted text, summaries, prompts, embeddings, indexes, manifest fragments, caches, logs, exports and backups. Processor selection respects the same restrictions before content is sent for extraction or embedding. Never-store categories are rejected at capture.

### 12.2 Redaction \[R7\]

`redact(event, spans)` commits a new event revision without the spans, protected as its own deletion unit, and places the original unit into the deletion lifecycle. Exposure is recorded per event, so every descendant of the original is treated as affected and is withheld until regenerated from the redacted revision. A user asking to "forget the part about X" in one message therefore loses no unrelated content from that message.

### 12.3 Deletion lifecycle

| From | To | Trigger | Guard or effect |
| --- | --- | --- | --- |
| requested | authorized | policy decision | principal or retention controller may delete this target in this scope |
| authorized | serving\_blocked | barrier committed | targets and all descendants excluded from reads, processing and output release; new descendants rejected at commit |
| serving\_blocked | purging | purge jobs scheduled | running jobs touching targets are cancelled or their outputs withheld and purged |
| purging | complete\_within\_scope | all named controlled surfaces purged and key conditions met (12.5) | report lists surfaces, evidence and remaining external limits |
| purging | purge\_failed | a purge step fails | serving stays blocked; retried; reported incomplete |
| purge\_failed | purging | retry | — |

Acknowledging `serving_blocked` is distinct from completion. Unknown dependency coverage prevents a completion claim and keeps the affected scope contained until resolved.

**Subject erasure** ("delete what you retain about X") first runs discovery across the authorized scope, reviews ambiguous candidates with the requester, then runs the lifecycle per target. Its report states discovery coverage; partial discovery is never reported as complete erasure.

### 12.4 Dependencies

Deletion dependencies come from exposure relations: a model-generated object depends on every retained input it was exposed to. Deleting one source therefore invalidates a mixed summary; a replacement is generated from surviving inputs under a new processing identity. An independently captured source of the same fact survives when policy permits.

### 12.5 Keys, caches, backups and restores

- Each deletion unit has its own data key, wrapped by the KMS. Destroying a wrapped key in the database is not erasure if a backup can restore the wrapper while the wrapping key exists; the deployment's key hierarchy must make the unit unrecoverable across retained copies, or completion waits for backup expiry (profile binding).
- Cached plaintext and cached data keys are invalidated explicitly or expire within a bound.
- Deletion-control records are stored outside data backups. A restore applies every barrier, revocation and key-state restriction before serving anything.

### 12.6 Audit and replay

Deletion audit keeps only: actor or pseudonymous reference, policy decision, opaque target ids, lifecycle status, counts. No names, sensitive relations or low-entropy plaintext hashes; a fingerprint requires a justified protected construction. Canonical replay reproduces surviving state plus deletion markers; it never reconstructs erased content. Content already delivered to an external recipient is reported as outside local erasure control.

## 13. Failure Behavior

**Every failure degrades toward less disclosure and less action, never toward unchecked state or silent completeness.** **Fixed (proposed).**

| Failure | Required behavior |
| --- | --- |
| Capture cannot commit | Do not report the memory as saved; retry with the same ingestion identity |
| Extraction, embedding or assessment unavailable | Keep capture; serve bounded source recall with explicit processing limits |
| Index stale or unavailable | Bounded permitted fallback (direct scan) or reported incomplete retrieval; serving barriers still apply |
| Identity or policy system unavailable | Refuse every operation that needs a decision it cannot obtain; permitted cached reads only within their validity |
| KMS unavailable | Refuse reads needing new data-key unwraps; deletion remains `serving_blocked` until purge can proceed |
| System of record unavailable | Return a visibly stale historical observation if permitted; never present it as current |
| Transition-owner failover | Fence the former owner; recover from committed records and the outbox |
| Tool outcome uncertain | Record `uncertain`; reconcile or use the tool's idempotency before any retry of a C3 or C4 action |
| Purge step fails | Keep serving blocked; retry; report incomplete erasure |
| Manifest commit fails | Do not dispatch the invocation |
| Budget exhausted | Stop the bounded operation; report truncation or deferred work |

## 14. Deployment Profile

**This manual defines an architecture family; a deployment profile binds one instance of it, and no implementation gate can pass until the profile's open bindings are fixed.** Evidence applies only to the instance it exercised.

### 14.1 Initial instance

One administrative tenant; a small group of users and multiple agent sessions doing continuing project work; personal and project scopes with explicit sharing; one instrumented runtime adapter. Cross-tenant and cross-organization federation, source-quality scoring and specialized graph storage are excluded from this instance.

### 14.2 Adapter conformance

An adapter may claim the instrumented profile only if it passes conformance tests for:

- span source marking of typed, pasted, attached and quoted text (7.1);
- manifest commit before every model dispatch, with declared coverage (11.1);
- conservative propagation through outputs (8.2);
- a handle store and deterministic segment reset (8.3);
- mediation of every egress path it declares (8.4, 8.5);
- registered operation contracts for every tool it exposes, with uncontracted tools treated as C4.

### 14.3 Bindings

| Binding | Kind | Status |
| --- | --- | --- |
| Expected corpus size and event rate | D3 instance constraint | Open, Gate 0 |
| Concurrent principals and agent sessions | D3 instance constraint | Open, Gate 0 |
| Per-turn lightweight retrieval latency (p95) | D3 instance constraint | Open, Gate 0 |
| Context budget split (mandatory, checkpoint, retrieved) | D4 public contract | Open, Gate 0 |
| Processing quotas per principal | D3 instance constraint | Open, Gate 0 |
| Judgment staleness bound for admission and C3/C4 reliance (9.3) | Default (policy-tightenable) | Open, Gate 0 |
| Manifest fragment retention window (11.2) | Default | Open, Gate 0 |
| Serving-block deadline and purge deadline | D3 instance constraint | Open, Gate 0 |
| Backup expiry and key hierarchy (12.5) | D3 instance constraint | Open, Gate 0 |
| Recovery point and recovery time objectives | D3 instance constraint | Open, Gate 0 |
| Capture size, nesting and decompression limits | D4 public contract | Open, Gate 0 |
| Permitted processors per sensitivity class | Policy (external owner) | Open, Gate 0 |
| Integrity-policy tightenings beyond 7.2 | Policy (external owner) | Optional |

### 14.4 Technical foundation

**Default (proposed):** PostgreSQL as the canonical store, partitioned by tenant; protected payloads in object storage; a transactional outbox for projection work; full-text and vector indexes as derived projections; adjacency tables for bounded traversal. Separate graph or bitemporal databases only when measured workload requires them.

Tenant partitioning is not a confidentiality control. Service credentials, row access, administrative paths, index isolation, encryption boundaries, backups and logs are all inside the deployment threat model. Searchable plaintext and embeddings stay sensitive even when payloads are encrypted; a confidentiality tag is a policy constraint, not encryption.

## 15. Architectural Invariants

**These are the acceptance properties of the architecture within a declared profile; each names the section that owns it, the evidence that tests it, and the first slice that must demonstrate it.** Tests are planned obligations, not reported results. Zero observed violations is bounded evidence, never proof, and no gate passes a known invariant violation because an aggregate metric improved.

| ID | Invariant | Owner | Evidence family | First slice |
| --- | --- | --- | --- | --- |
| H1 | Ordinary operations append; authorized payload erasure is the only exception | 6, 12 | storage audit, replay | 1a |
| H2 | Every claim and judgment resolves to source and processing records or an explicit deletion marker | 5 | dependency and migration tests | 2 |
| E1 | Capture, assessment, admission, provenance and permission stay distinguishable in storage and presentation | 5, 6 | schema and presentation tests | 1a |
| E2 | Conflicts and disputed derivations stay inspectable without erasing independent evidence | 6.2 | reconciliation scenarios | 2 |
| E3 | Judgments are presented with their "assessed as of" position; admission and C3/C4 reliance use only fresh judgments | 9.3 | freshness and race tests | 2 |
| A1 | Memory text never grants a capability or activates a procedure | 6.5, 7 | adversarial authorization tests | 1a |
| A2 | Only the owning component commits each record type | 4.3 | credential and API tests | 1a |
| A3 | A reliance exception binds an exact object revision, use, scope and current authorization | 7.4 | endorsement and revocation tests | 2 |
| P1 | Source classes come only from capture, adapter span marking and connector contracts, never from content | 7.1 | property and adversarial tests | 1a (span marking 1b) |
| F1 | Model outputs carry the conservative dependency set, source classes and confidentiality tags of their inputs | 8.2 | runtime property tests | 1b |
| F2 | Every mediated dispatch passes 8.4; C3 and C4 target-binding arguments are grounded | 7.2, 8.4 | egress and grounding tests | 1b |
| F3 | Retrieval never exposes ineligible or quarantined content, including through snippets, counts or explanations | 10.1 | isolation and metadata tests | 1a |
| F4 | Handle content enters a planning context only by explicit unwrap, importing its classes and tags | 8.3 | adapter conformance tests | 1b |
| C1 | Every instrumented invocation has a manifest committed before dispatch and a separate outcome record | 11.1 | adapter conformance tests | 1b |
| C2 | Recall finds every seeded dependency within declared coverage and states its gaps | 11.3 | seeded compromise tests | 1b |
| C3 | Manifest skeletons hold no item content; rendered fragments expire within their window | 11.2 | retention tests | 1b |
| R1 | Acknowledged corrections and serving barriers apply to all subsequent retrieval and pending output release | 9.4, 12.3 | race and cache tests | 1a |
| D1 | No covered target or descendant is served after its barrier, including from restored state | 12.3, 12.5 | deletion and restore tests | 1a |
| D2 | Deletion completion is reported only for surfaces and key conditions actually satisfied | 12.3, 12.5 | key, cache, backup and purge tests | 1a |
| D3 | Redaction removes the spans from serving; descendants are withheld until regenerated | 12.2 | redaction tests | 1a |
| O1 | One transition owner per partition; fenced failover; no duplicate canonical transitions | 9.1 | concurrency and failover tests | 1a |
| O2 | Replay uses recorded outputs and never calls models or repeats actions | 9.6 | replay and recovery tests | 1a |
| O3 | Context fits its budget or returns an explicit overflow outcome | 10.4 | tokenizer and boundary tests | 1a |
| O4 | Coverage and freshness limits are reported without disclosing inaccessible records | 10.3 | partial-processing and isolation tests | 1a |

Evidence must exercise the real storage, retrieval, runtime and policy boundaries that own the behavior; mock-only demonstrations do not count as enforcement evidence.

**Gate evaluations are pre-registered.** Each gate's evaluation is an evidence specification fixed before measurement: the estimand (for example, end-task success rate at a fixed token budget on a named workload), comparators, a decision rule that includes sampling uncertainty (an interval margin, not a point win), validation of any model judge against human adjudication on a sample, separation of development and held-out cases, and disclosure of every evaluated variant and any held-out reuse. A configuration chosen after seeing results is reported as selected, not pre-specified.

## 16. Delivery Slices and Acceptance Gates

**Slice 1 is split along the two integration profiles \[R4\]: reliable recall under the memory-service profile ships first, and the instrumented runtime follows as its own gated slice.** No dates are set until Gate 0. Security and deletion are in Slice 1a from the start; it simply makes only the claims its profile allows.

&#91;embedded content: delivery plan · specification, four slices, five gates\]

Each gate requires its invariants (15) on real boundaries and a declared-workload comparison against B1 (transcript chunks with hybrid retrieval), B2 (full history in context where it fits) and the previous slice. A cost increase passes only with a tradeoff stated before measurement; a required invariant is never traded for an aggregate gain.

## 17. Delegated Space, Non-Goals and Reopen Triggers

**Implementation may choose anything this manual does not fix, provided every invariant in Section 15 holds; a change that cannot hold them reopens this manual rather than patching around it.**

### 17.1 Delegated to implementation

Concrete schemas and serialization; table and partition layout; index structures and libraries; embedding and extraction models and prompts; ranking features and weights; retry, backoff and cache design; job scheduling; language and frameworks; transport adapters over the typed API; the concrete KMS product; layout of inspection interfaces.

### 17.2 Required inspection surfaces

Within the requested deliverable (stated by the v0.3 proposal, Section 11). Users must be able to answer, subject to normal access control:

- What was remembered, from which source, and when?
- Why was this item retrieved or treated as current?
- What supports it, what contradicts it, and what is unprocessed?
- Did my correction, suppression, redaction, revocation or deletion take effect?
- Which recorded outputs or actions might this source have affected?

An answer may say that supporting material is restricted without exposing it.

### 17.3 Non-goals

UPMS is not a truth oracle; does not infer people's motives, interests or threat levels; assigns no reputation to people; does not replace systems of record; does not grant permissions; does not guarantee faithful model reasoning or complete prompt-injection protection through retrieval; does not erase content already delivered to uncontrolled recipients; does not determine which input caused a model output; does not train model weights on retained memory.

### 17.4 Reopen triggers

| Observation | Reopens |
| --- | --- |
| The target runtime cannot implement handles or deterministic segment reset | 8.3, and the 1b slice |
| Measured confirmation burden exceeds the threshold agreed at Gate 0 | 7.2 defaults (with the policy owner), 8.3 |
| The staleness bound cannot be met at the instance's scale | 9.3 |
| The KMS and backup arrangement cannot make units unrecoverable within the purge deadline | 12.5 completion contract |
| A required egress path cannot be mediated | 8.1 profile claims, 14.2 |
| Demand for cross-tenant transactions or federation | 9.1, 14.1 |
| Slice 2 structures fail to beat Slice 1a on the declared workload | 5.2–5.3, 6.2 (simplify or remove) |
| Repeated wrappers, fallbacks or special cases accumulate around one mechanism | that mechanism's section, for simplification before further repair |

Changes to delegated items (17.1) that preserve all invariants are implementation reconciliation and do not reopen this manual.

## 18. Open Decisions

**Ten decisions remain open; six must close at Gate 0 before an implementation specification is written.** Owners are roles, to be named by the product owner.

| ID | Decision | Owner | Close by |
| --- | --- | --- | --- |
| O-1 | Confirm continuing project work as the first workload; identify real sessions usable, with permission, for evaluation | Product owner | Gate 0 |
| O-2 | Choose the runtime for the instrumented adapter; declare its coverage; decide whether planners may unwrap handles and under what limits | Architecture owner with runtime team | Gate 0 |
| O-3 | Set the confirmation-burden threshold and measurement method for the C3 X-payload and C4 rules | Product owner with policy owner | Gate 1b |
| O-4 | Choose claim domains whose rulesets may admit beyond the default rule; the rest stay evidence-only | Product owner | Gate 2 |
| O-5 | Choose the key hierarchy and backup arrangement that meets the purge deadline | Security and infrastructure | Gate 0 |
| O-6 | Design correction targeting for ambiguous targets without suppressing other people's evidence | Product owner | Gate 1a |
| O-7 | Decide whether any rule may reconcile conflicting judgments across scopes; if none, conflicts stay visible | Product owner | Gate 2 |
| O-8 | Bind every open profile parameter in 14.3 | Architecture owner | Gate 0 |
| O-9 | Pre-register the gate evaluation protocol (15): estimands, workloads and corpus, baselines, decision rules with uncertainty margins, judge validation, held-out discipline | Architecture owner | Gate 0 |
| O-10 | Simplification review: can any record type, relation or boundary be removed while keeping the user journeys and Section 15? | Independent cross-reviewers | Gate 0 |

A useful review finding names the section or invariant, gives a concrete counterexample and its consequence, and proposes an alternative with its cost and how to verify it.
