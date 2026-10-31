# Universal Persistent Memory Substrate (UPMS)
## Architecture Proposal v0.1

**Status:** Draft — Submitted for Independent Architectural Review  
**Architecture class:** Model-independent, multi-agent, multi-user persistent cognitive infrastructure  
**Primary objective:** Persistent, contextualized, evidence-grounded memory with autonomous retrieval and deterministic state governance.

---

# 1. Executive Summary

## 1.1 Motivation

Contemporary LLM agents primarily depend on their immediate context window as their working memory. Although context windows have grown substantially, they remain finite, volatile, and susceptible to information loss through compaction, summarization, and session termination.

This creates a fundamental limitation for agents expected to operate over extended periods, across multiple projects, applications, people, and organizational environments.

Existing persistent-memory implementations commonly rely on document-based records, vector databases, retrieval-augmented generation (RAG), or combinations thereof. These approaches provide useful capabilities but do not, individually, establish a comprehensive memory architecture.

In particular, conventional approaches frequently lack one or more of the following:

- Complete historical preservation.
- Temporal and relational knowledge representation.
- Reliable source attribution and provenance.
- Explicit epistemic uncertainty and evidence verification.
- Identity and authority separation.
- Protection against memory poisoning and prompt injection.
- Context-dependent retrieval and memory prioritization.
- Deterministic memory-state management.
- Cross-agent and cross-model continuity.
- Autonomous working-context management.

This proposal introduces the **Universal Persistent Memory Substrate (UPMS)**, a model-independent external memory infrastructure intended to provide persistent, contextualized, and appropriately governed memory to AI agents.

The fundamental architectural premise is:

> The context window is volatile working memory. The external memory substrate is the persistent historical and semantic memory authority. An independent deterministic control and retrieval infrastructure determines what information is retained, established, authorized, and made available to the agent.

The system should operate independently of any particular LLM, agent framework, inference provider, or application.

## 1.2 Architectural Vision

UPMS should provide an AI agent with continuity across:

- Sessions and conversations.
- Multiple days, months, and years.
- Multiple independent projects.
- Multiple human collaborators.
- Multiple agent runtimes and models.
- Multiple applications and organizational environments.

The memory substrate should maintain the historical record and continuously derive a structured representation of the relevant world.

Individual agents should not be responsible for managing the underlying memory database, maintaining relationships, reconciling contradictions, updating indexes, or determining their own authority.

These responsibilities belong to the external infrastructure.

The agent should receive compact, relevant, evidence-grounded context and have the ability to request additional information when necessary.

---

# 2. Foundational Architectural Principles

The following principles are proposed as non-negotiable design constraints.

### UPMS-PR-01 — Model Independence

Persistent memory must not depend on the identity, architecture, vendor, or lifecycle of an LLM.

Any compatible agent should be able to consume and contribute to the memory substrate through a standardized interface.

### UPMS-PR-02 — Historical Preservation

Historical events and original evidence must be preserved independently of derived summaries and semantic interpretations.

Memory consolidation must not silently destroy historical evidence.

### UPMS-PR-03 — Separation of Memory and Knowledge

Recording that information was encountered is distinct from accepting the information as established knowledge.

The system must support remembering information without believing it.

### UPMS-PR-04 — Separation of Knowledge and Authority

Factual knowledge does not grant instruction authority or operational permissions.

An external document, memory record, or agent-generated interpretation cannot independently modify the system's governing authority.

### UPMS-PR-05 — Deterministic State Governance

Canonical identity, permissions, memory admission, provenance, state transitions, and consistency must be enforced by deterministic software.

LLMs may interpret, investigate, and propose, but cannot independently authorize their own memory modifications.

### UPMS-PR-06 — Provenance Preservation

Every admitted assertion and derived representation must maintain traceable provenance.

Transformations must not silently upgrade the trust or authority of their original sources.

### UPMS-PR-07 — Contextual Retrieval

Memory relevance must depend on the current task, entities, projects, temporal context, and retrieval intent.

There must not be a universal, permanently fixed relevance ranking.

### UPMS-PR-08 — Bounded Working Context

The system must retrieve and inject only the information justified by the available context budget.

Persistent storage capacity must be independent of the model's context-window capacity.

### UPMS-PR-09 — Security by Architecture

Authentication, authorization, information-flow restrictions, and memory admission must be enforced externally rather than relying on an LLM to recognize and reject malicious content.

### UPMS-PR-10 — Multi-Agent and Multi-User Compatibility

Memory ownership, sharing, access, and authority must be explicitly scoped.

Multiple agents and humans may share relevant knowledge without automatically receiving unrestricted access to each other's memories.

### UPMS-PR-11 — Reconstructability

Derived memory state, indexes, summaries, reputation profiles, and contextual projections should be reproducible from authoritative records and versioned processing rules wherever technically feasible.

### UPMS-PR-12 — Privacy and Retention Governance

Historical preservation is subject to explicit privacy, retention, deletion, and security-remediation policies.

Append-only behavior is the normal operating model, not an exemption from authorized deletion.

---

# 3. Conceptual Memory Model

UPMS distinguishes three primary memory lifecycles.

## 3.1 Episodic Memory — Historical Authority

Episodic memory records what happened.

It is the foundational historical record of interactions, observations, actions, decisions, and significant events.

The underlying event ledger should be append-only by default.

It must preserve the original information or a durable, integrity-verified reference to its source.

Events should accommodate the conceptual 5W1H framework:

- When: Occurrence time and recording time.
- Where: Location, project, conversation, environment, or application.
- Who: Originators, observers, participants, transmitters, and agents.
- What: The actual event and its substantive content.
- Why: Stated motivation, rationale, or subsequently derived explanation.
- How: Method, process, and outcome.

5W1H is an extraction framework, not a rigid requirement that every event contain six populated fields.

Additional mandatory metadata includes provenance, epistemic status, security classification, and temporal validity where applicable.

### Bitemporal representation

Every relevant record should distinguish:

- **Valid time:** When the information was true or the event occurred.
- **Transaction time:** When the system recorded or accepted the information.

This is necessary for reconstructing historical knowledge and handling delayed reports, corrections, and retroactive information.

## 3.2 Semantic Memory — Derived Knowledge

Semantic memory represents what the system currently understands.

It is derived from episodic records and contains:

- Entities.
- Atomic assertions.
- Events and their semantic classifications.
- Relationships.
- Decisions.
- Preferences.
- Goals.
- Obligations.
- Procedures.
- Hypotheses.
- Evidence relationships.

The semantic representation should be a structured, versioned projection of historical evidence.

It must not replace the underlying historical authority.

### Atomic claims

Messages and documents must be decomposable into independently meaningful information units.

A single message may contain several factual assertions, interpretations, instructions, quotations, and speculative statements.

Each should receive its own provenance, epistemic, authority, and security assessment.

### First-class relationships

Relationships must be independently identifiable records rather than simple, context-free graph edges.

A relationship may carry:

- Type and direction.
- Supporting evidence.
- Origin and provenance.
- Temporal validity.
- Confidence and epistemic status.
- Scope.
- Supersession information.

Examples include:

- Person A collaborated with Person B.
- Decision X was motivated by Observation Y.
- Project A superseded Project B.
- Assertion X contradicts Assertion Y.
- Person C delegated authority to Agent D.

Causal relationships must be distinguished from mere temporal or statistical associations.

## 3.3 Operational Memory — Working Context

Operational memory represents what the agent currently needs.

It is a dynamic projection of episodic and semantic memory.

It includes:

- Agent and user orientation.
- Active projects.
- Current responsibilities.
- Relevant people.
- Accepted decisions.
- Outstanding obligations.
- Recent significant events.
- Retrieved historical evidence.
- Temporary task-specific information.

Operational memory is disposable and reconstructable.

It must never become an independent historical or semantic authority.

---

# 4. Semantic Graph Architecture

UPMS proposes four logically distinct graph structures.

These are conceptual namespaces and ownership boundaries. They do not necessarily require four physically independent graph databases.

## 4.1 Knowledge Graph

Represents what is known, asserted, disputed, or historically established.

Contains entities, events, claims, relations, decisions, and other semantic objects.

## 4.2 Evidence and Provenance Graph

Represents why information is believed and where it originated.

Tracks:

- Original sources.
- Direct observations.
- Witness testimony.
- External publications.
- Supporting and contradictory evidence.
- Derivation chains.
- Independent corroboration.
- Evidence dependence.

It must distinguish independent evidence from repeated transmission of the same original source.

## 4.3 Trust and Authority Graph

Represents authenticated principals, organizational relationships, roles, delegation, and authority boundaries.

It should reference authoritative identity and permission records.

The graph itself is not the ultimate authorization mechanism. Enforcement belongs to a dedicated policy engine.

## 4.4 Interest and Incentive Graph

Represents the interests and potential conflicts of different actors.

Examples:

- Financial interests.
- Organizational competition.
- Shared project objectives.
- Professional incentives.
- Personal stakes.
- Conflicting commercial objectives.

Interests must be contextual, temporal, and evidence-backed.

Declared interests must be distinguished from inferred interests.

A conflict of interest increases scrutiny but does not establish dishonesty.

---

# 5. Memory Provenance and Epistemic Assurance

## 5.1 Source Attribution

Every memory assertion must preserve the distinction between:

- Originator: Who originally made the assertion?
- Observer: Who directly observed the source or event?
- Transmitter: Who conveyed the information?
- Interpreter: Which agent or process derived the stored representation?

These identities may be different.

For example, a user reporting what a colleague said does not establish that the user directly witnessed the reported event.

The correct memory is that the user reported the colleague's statement.

### Source classifications

Initial source classes should include:

- Authenticated first-party interaction.
- Direct system observation.
- First-hand human testimony.
- Second-hand testimony.
- External publication.
- Tool-generated output.
- Agent inference.
- Agent-generated synthesis.

Authentication establishes source identity and message integrity where supported. It does not establish factual correctness.

## 5.2 Epistemic Status

Assertions should support at least the following classifications:

| Status | Meaning |
|---|---|
| Supported | Available evidence supports the assertion |
| Refuted | Available evidence contradicts it |
| Contested | Significant supporting and contradicting evidence exists |
| Unknown | Insufficient evidence to establish or refute it |

Epistemic status must remain independent of memory admission, source identity, and instruction authority.

Contradictory assertions must be preserved rather than arbitrarily overwritten.

The system should support paraconsistent handling so that localized contradictions do not invalidate the entire knowledge structure.

## 5.3 Assurance Engine

A dedicated Memory Assurance Engine should orchestrate:

1. Source and integrity validation.
2. Identity and authority checks.
3. Evidence inspection.
4. Temporal consistency checks.
5. Internal contradiction detection.
6. External verification where appropriate.
7. Confidence and uncertainty assessment.
8. Investigation and reconciliation.
9. Admission decisions.

Verification requirements should depend on the intended use and consequences of relying on the information.

A historical recollection may tolerate uncertainty. A consequential operational action requires substantially stronger verification.

Confidence must be evidence-derived and should not consist solely of an LLM's self-reported numerical confidence.

---

# 6. Identity, Authority, Reputation, and Interests

These four concepts must remain independent.

## 6.1 Identity

Determines who the source actually is.

Where possible, identity should be established through authenticated credentials and independently verified channels.

Writing style, claimed names, and self-identification are not sufficient authentication.

## 6.2 Authority

Determines what a principal is permitted to establish, modify, or authorize.

Authority should be:

- Explicit.
- Scope-limited.
- Capability-based.
- Delegated through authenticated records.
- Time-bounded where appropriate.
- Revocable.

A principal cannot grant itself authority by making a statement that claims such authority.

Authority in one domain does not imply authority in another.

## 6.3 Reputation

Reputation is a derived estimate of historical source reliability.

It should influence retrieval priority, evidence ranking, and investigation ordering.

It must never independently establish factual correctness or grant authority.

Reputation should be:

- Domain-specific.
- Behavior-specific.
- Evidence-derived.
- Sensitive to sample size.
- Associated with uncertainty.
- Recalculable and reversible.

Repeated derivative statements must not count as independent corroboration.

Retrieval frequency alone must not increase reputation.

## 6.4 Interest and Incentive

Interests provide contextual evidence about potential bias and incentives.

They may increase the required scrutiny of a statement but cannot establish intent by themselves.

## 6.5 Intent and Threat Assessment

Intent is not directly observable and must not be treated as a deterministic property inferred from message content.

The system should assess observable indicators:

- Interest alignment or conflict.
- Factual discrepancies.
- Nature and magnitude of errors.
- Source access to correct information.
- Historical behavior.
- Corrections following notification.
- Selective omission or fabricated evidence.
- Repeated suspicious patterns.
- Circumstantial context.

The system must distinguish honest mistakes, outdated information, negligence, strategic bias, and evidenced malicious behavior.

It should not force an intent conclusion when the evidence is insufficient.

Threat assessments should be scoped to the relevant person, account, document, communication channel, or agent credential.

Restrictions must be evidence-backed, reviewable, and revocable.

---

# 7. Security and Memory Admission

Security is a foundational architectural responsibility, not an optional retrieval feature.

## 7.1 Admission States

Historical capture and semantic admission must be separate operations.

Proposed admission categories:

- Captured: Preserved in historical memory.
- Quarantined: Restricted because of security concerns.
- Evidence-only: Available as source material without trusted semantic admission.
- Semantically admitted: Accepted into a derived knowledge projection under applicable policies.

These categories do not imply absolute factual certainty.

## 7.2 Information-Flow Taint Tracking

Every information unit must carry provenance and security classifications through its entire lifecycle.

Example origin classifications:

- Authenticated first-party interaction.
- Direct tool observation.
- External publication.
- Third-party report.
- Agent inference.
- Derived untrusted content.

Example security classifications:

- Normal.
- Unverified.
- Suspicious.
- Quarantined.
- Restricted.

A summary, embedding, graph relation, or derivative memory must preserve the relevant source lineage and security restrictions.

Transformation must never silently upgrade trust.

## 7.3 Instruction and Knowledge Separation

Memory content must not acquire instruction authority merely because it is written in imperative language.

The system must distinguish:

- Knowledge and evidence.
- Historical statements.
- Candidate directives.
- Authenticated and authorized instructions.

An external webpage claiming to contain a user's new instruction does not establish that instruction's authenticity.

A document cannot grant itself authority.

A trusted LLM summary cannot convert malicious source material into an authorized instruction.

## 7.4 Retrieval-Time Security

Security enforcement must occur before context injection.

The retrieval policy engine must evaluate:

- Requesting principal identity.
- Scope and authorization.
- Memory admission status.
- Epistemic and security classification.
- Confidentiality restrictions.
- Cross-user and cross-project access.
- Potential adversarial content.

The system must support excluding suspicious material, presenting it only as untrusted evidence, or restricting it to security investigation.

Context labels are useful but cannot replace external enforcement.

## 7.5 Consequential Actions

Retrieved memory must not independently authorize consequential operations.

The actual operation must pass through the relevant authenticated permission and policy infrastructure.

Uncertain factual context may permit graceful degradation. Uncertain authorization must fail closed.

---

# 8. Deterministic Memory Control Plane

The architecture should inherit the separation between semantic reasoning and deterministic control established in the SSDS design work.

The governing principle is:

> Agents interpret and propose. Deterministic software owns identity, permissions, provenance, canonical state, consistency, admission, and valid state transitions.

## 8.1 Canonical Event-Sourced State

UPMS should use:

- One authoritative event ledger.
- One canonical admission owner and writer.
- A deterministic state reducer.
- Versioned rulesets and schemas.
- Idempotent ingestion.
- Explicit revision identities.
- Stale-result rejection.
- Transactional state transitions.
- Deterministic replay and recovery.

No agent should be capable of bypassing the canonical admission process.

Derived state should be a function of recorded authoritative inputs, admitted processing results, and versioned rules.

## 8.2 Probabilistic Processing Boundary

LLMs will be used for:

- Semantic extraction.
- Entity resolution proposals.
- Claim decomposition.
- Interpretation.
- Investigation.
- Reconciliation recommendations.
- Memory synthesis.

These outputs are candidates, not canonical state.

The system should record the relevant model, prompt, configuration, input references, and output revision to support audit and reproducibility.

Replay must use recorded processing results rather than silently invoking an LLM again.

## 8.3 Canonical and Derived State

The following are derived projections, not independent authorities:

- Search indexes.
- Vector embeddings.
- Graph adjacency indexes.
- Entity summaries.
- Reputation profiles.
- Interest assessments.
- Continuity checkpoints.
- Working-set manifests.

They must be rebuildable or reconcilable against their authoritative inputs.

Semantic acceptance must not be inferred merely from the existence of an index, test result, review, agent output, or generated summary.

## 8.4 Processing Lifecycle

Proposed ingestion lifecycle:

1. Capture original event and source metadata.
2. Append the event to the authoritative ledger.
3. Extract candidate semantic records.
4. Validate identity, schemas, and permissions.
5. Evaluate provenance and security.
6. Reconcile against existing knowledge.
7. Admit or quarantine candidate assertions.
8. Update deterministic semantic projections.
9. Refresh affected retrieval indexes.
10. Invalidate or refresh affected working-set entries.

Initial capture should be durable and synchronous.

Expensive semantic processing may be asynchronous, provided the system supports read-your-writes consistency for important corrections and instructions.

---

# 9. Retrieval and Relevance Architecture

## 9.1 Dynamic Relevance

A dense, permanently stored N×N attention matrix is not recommended.

Its quadratic storage cost is impractical, and relevance is inherently conditional on the current query.

Instead, UPMS should use dynamic, sparse, contextual relevance calculation.

Retrieval relevance should consider:

- Lexical relevance.
- Semantic similarity.
- Entity overlap.
- Graph relationships.
- Temporal relevance.
- Project and task scope.
- Memory salience.
- Explicit user priorities.
- Unresolved obligations.
- Epistemic quality.
- Security eligibility.

Security and authorization are hard eligibility filters, not merely ranking penalties.

## 9.2 Retrieval Mechanisms

The initial retrieval architecture should support:

- Full-text search.
- Semantic vector search.
- Temporal search.
- Entity and relationship lookup.
- Graph traversal.
- Sparse associative relevance propagation.
- Hybrid candidate fusion and ranking.

The system should investigate graph-assisted retrieval methods such as Personalized PageRank and related associative retrieval techniques.

No single retrieval mechanism should be assumed sufficient for all query types.

## 9.3 Memory Salience and Temporal Decay

Historical existence and current relevance are separate properties.

Historical records should not disappear merely because their retrieval priority declines.

Different categories require different temporal behavior:

- Stable preferences: slow decay.
- Active projects: state-dependent relevance.
- Temporary priorities: faster decay.
- Unresolved obligations: remain active until resolved.
- Historical decisions: retained indefinitely subject to policy.
- Volatile facts: become stale according to validity requirements.

Retrieval frequency must not become a self-reinforcing substitute for importance.

## 9.4 Working-Set Management

The system should maintain a context working set containing:

- Pinned information.
- Active-task context.
- Retrieved historical evidence.
- Temporary tool outputs.

The working set must be bounded by the target model's context budget.

It should support:

- Admission.
- Refresh.
- Invalidation.
- Eviction.
- Revision tracking.
- Context reconstruction.

Revision-based invalidation should be preferred over relying exclusively on time-to-live expiration.

---

# 10. Entry Point and Continuity

## 10.1 Root Memory Manifest

A fresh agent context requires a compact orientation mechanism.

UPMS should maintain a versioned root memory manifest containing:

- Agent identity and operating boundaries.
- User and team identity.
- Stable preferences and constraints.
- Active projects.
- Important relationships.
- Current priorities.
- Recent significant events.
- Outstanding obligations.
- Important warnings.
- Pointers to detailed memory.

The manifest is an index and orientation artifact, not the complete memory.

## 10.2 Hierarchical Memory Indexes

The root manifest should point to progressively more specific indexes:

- People index.
- Project index.
- Activity index.
- Knowledge index.
- Obligation index.
- Security and authority index.

Detailed information should be retrieved only when relevant.

## 10.3 Continuity Checkpoints

The system should generate versioned checkpoints at significant milestones and session boundaries.

A checkpoint should contain:

- Current situation.
- Recent events.
- Accepted decisions.
- Outstanding obligations.
- Relevant people and projects.
- Unresolved questions.
- Supporting memory references.
- Ledger watermark and projection revision.

Checkpoints should be reconstructable projections, not independent authorities.

They should support model switching, agent handoffs, recovery, and long-term task continuity.

---

# 11. Context-Window Integration

UPMS should distinguish persistent storage, retrieved working memory, and immediate inference context.

The external service cannot directly rewrite an already-running model invocation's context window.

Therefore, automatic context management should be implemented through agent-runtime middleware or an equivalent orchestration interface.

## 11.1 Retrieval Triggers

| Trigger | Expected behavior |
|---|---|
| New session | Load root manifest and continuity checkpoint |
| New user turn | Perform lightweight contextual retrieval |
| New entity or project reference | Resolve relevant memory |
| Ambiguous reference | Retrieve historical context |
| Task planning | Retrieve decisions, constraints, and dependencies |
| Before consequential action | Refresh relevant state and permissions |
| Explicit recall request | Perform deeper historical retrieval |
| New significant event | Update affected working-set entries |

## 11.2 Retrieval Frequency

Retrieval should be event-driven rather than continuous polling.

The runtime should automatically perform lightweight retrieval before inference and permit deeper retrieval through explicit agent-facing capabilities.

The agent should not be required to remember to search memory during every conversation.

## 11.3 Context Budgeting

The retrieval engine should optimize information selection against a bounded token budget.

The objective is not to retrieve the greatest number of memories.

It is to maximize useful, relevant, sufficiently trustworthy information within the available context.

The system should measure retrieval recall, precision, evidence coverage, latency, and token efficiency.

---

# 12. Agent Interface and Integration

The memory service must remain independent of agent transports and execution frameworks.

The internal service API is primary. MCP is an agent-facing capability façade, not the control plane or canonical storage interface.

Proposed agent-facing operations:

| Operation | Responsibility |
|---|---|
| `memory.get_context` | Retrieve automatically or explicitly assembled context |
| `memory.search` | Search historical and semantic memory |
| `memory.expand` | Expand entities and relationships |
| `memory.get_evidence` | Retrieve supporting evidence |
| `memory.record_event` | Submit an authenticated event |
| `memory.propose` | Submit candidate semantic knowledge |
| `memory.report_conflict` | Report contradictory information |
| `memory.request_investigation` | Initiate deeper verification |
| `memory.feedback` | Report retrieval quality |
| `memory.get_assurance` | Inspect claim assurance and provenance |

There must be no unrestricted agent-facing operation to modify trust scores, grant authority, directly overwrite accepted knowledge, or bypass admission.

Agent capabilities must be authenticated and scoped.

The same internal service should be accessible through different adapters for different agent runtimes.

---

# 13. Multi-User and Multi-Agent Governance

UPMS is intended as a shared substrate, not merely a personal assistant's private memory.

Proposed memory scopes:

1. Personal.
2. Team.
3. Project.
4. Organizational.
5. Agent-specific operational memory.

Scopes may reference one another without automatically sharing unrestricted access.

Every memory object and relation should carry appropriate ownership, confidentiality, and authorization metadata.

The architecture should enforce:

- Tenant isolation.
- Principal-based access.
- Capability-scoped operations.
- Explicit delegation.
- Revocation.
- Confidentiality boundaries.
- Auditability.
- Cross-agent provenance.

An agent's ability to read shared project knowledge does not imply permission to access private personal memory.

## 13.1 External Systems of Record

UPMS must not become an uncontrolled duplicate of every connected application.

If a repository, calendar, project-management system, or database owns authoritative operational state, that system remains authoritative.

UPMS should preserve the contextual history:

- Why something happened.
- What discussions motivated it.
- Which decisions led to it.
- What historical constraints matter.
- What previous agents learned.

It should not silently replace the source application's current state.

---

# 14. Privacy, Retention, and Deletion

The event ledger is append-only by default, but retention and deletion must be explicitly governed.

The system should support:

- Data classification.
- Retention policies.
- Authorized deletion.
- Redaction.
- Cryptographic erasure where appropriate.
- Derived-index and cache cleanup.
- Replica and backup remediation.
- Auditable deletion operations.

Deletion should not unnecessarily preserve the deleted content in the audit trail.

Sensitive information must receive stricter handling than ordinary conversational memory.

The exact deletion and backup-remediation guarantees must be established before production deployment.

---

# 15. Proposed Technical Foundation

The initial implementation should minimize unnecessary infrastructure complexity.

A relational database such as PostgreSQL is a reasonable candidate for the canonical storage layer.

Potential components include:

- Append-only event tables.
- Typed assertion and relationship tables.
- Entity registry.
- Provenance and evidence records.
- Identity and permission records.
- Temporal indexes.
- Full-text indexes.
- Vector indexing.
- Graph adjacency indexes.
- Object storage for large original sources.

Specialized graph infrastructure should be introduced only when demonstrated workloads justify it.

The semantic graph is a logical representation, not a mandate to adopt a particular database technology.

All indexes and retrieval structures must remain derived from authoritative records.

---

# 16. Migration and Legacy Memory Compatibility

Existing document-based memory systems must be migratable without assuming that their contents are complete, correct, or uniformly trustworthy.

Legacy memory should initially be represented as an opaque historical aggregate.

Progressive refinement may decompose it into smaller semantic units, but must preserve:

- Original content.
- Original scope.
- Source lineage.
- Completeness information.
- Uncertainty.
- Existing authority boundaries.

Refinement must not silently transfer semantic acceptance from the original aggregate to newly extracted records.

This should follow a scope-conserving migration strategy: every refined unit must remain traceable to its original material, and unrepresented portions must remain explicitly unresolved.

This provides backward compatibility without requiring immediate full reconstruction of legacy memory.

---

# 17. Evaluation and Verification

Evaluation must be designed alongside implementation.

## 17.1 Functional Memory Evaluation

Test:

- Exact historical recall.
- Temporal reasoning.
- Associative retrieval.
- Implicit reference resolution.
- Multi-session continuity.
- Cross-project isolation.
- Contradiction handling.
- Source attribution.
- Evidence reconstruction.
- Abstention when information is unknown.

Existing benchmarks such as LongMemEval and LoCoMo may provide useful initial evaluation datasets.

A dedicated workload should additionally represent real multi-project and multi-agent operations.

## 17.2 Security Evaluation

Adversarial tests should include:

- Direct prompt injection.
- Delayed memory poisoning.
- Forged user identity.
- Unauthorized delegation.
- Compromised credentials.
- Trust laundering through agent summaries.
- Malicious instructions embedded in legitimate documents.
- Compaction-induced poisoning.
- Cross-project and cross-tenant leakage.
- Unauthorized promotion of quarantined information.
- Replayed or revoked credentials.

Testing must cover the complete capture, admission, retrieval, and action lifecycle.

## 17.3 Deterministic Evaluation

Verify:

- Replay correctness.
- Idempotent ingestion.
- Stale-result rejection.
- Single-writer enforcement.
- Transactional consistency.
- Index reconstruction.
- Revision-based invalidation.
- Authorization enforcement.
- Deletion propagation.

## 17.4 Core Performance Metrics

- Retrieval recall at bounded token budgets.
- Retrieval precision.
- Evidence coverage.
- Provenance fidelity.
- Temporal correctness.
- Entity resolution accuracy.
- Contradiction detection.
- Unauthorized retrieval incidence.
- Memory poisoning success rate.
- Context token efficiency.
- Retrieval latency.
- Ingestion throughput.
- Recovery correctness.

The primary performance objective is reliable retrieval of relevant information at minimal context cost, without compromising evidence quality or security.

---

# 18. Proposed Development Roadmap

Implementation should proceed incrementally.

## Phase 0 — Architectural Specification

Define:

- Canonical data model.
- Event and claim schemas.
- Identity and authority boundaries.
- Provenance semantics.
- Memory admission states.
- Security invariants.
- Temporal model.
- Internal service interfaces.
- Evaluation requirements.

Deliverable: Independently reviewed architecture specification.

## Phase 1 — Persistent Memory Foundation

Implement:

- Canonical event ledger.
- Source preservation.
- Bitemporal records.
- Identity registry.
- Access control.
- Event ingestion.
- Deterministic reducer.
- Replay and recovery.

Deliverable: Durable historical memory substrate.

## Phase 2 — Semantic Memory and Assurance

Implement:

- Atomic claim extraction.
- Entity registry.
- Typed relations.
- Provenance graph.
- Epistemic status.
- Contradiction detection.
- Admission and quarantine.
- Temporal reconciliation.

Deliverable: Evidence-grounded semantic memory.

## Phase 3 — Retrieval and Relevance

Implement:

- Hybrid search.
- Entity resolution.
- Graph expansion.
- Contextual ranking.
- Temporal relevance.
- Memory salience.
- Token budgeting.
- Retrieval evaluation.

Deliverable: Efficient contextual memory retrieval.

## Phase 4 — Context Management and Agent Integration

Implement:

- Root manifest.
- Continuity checkpoints.
- Working-set manager.
- Automatic context injection.
- Cache invalidation.
- Internal typed API.
- MCP adapter.
- Multi-agent identity and capabilities.

Deliverable: Model-independent persistent agent continuity.

## Phase 5 — Advanced Memory Intelligence

Implement:

- Advanced consolidation.
- Reputation estimation.
- Interest and incentive modeling.
- Behavioral threat assessment.
- Investigation orchestration.
- Cross-project associative memory.
- Multi-user collaboration.

Deliverable: Continuously maintained, adaptive memory infrastructure.

Security, identity, access control, and provenance are foundational requirements and must not be postponed until Phase 5.

---

# 19. Initial Architectural Invariants

The following invariants summarize the proposed system's required behavior.

### Historical Integrity

- Historical records are never silently overwritten.
- Original evidence remains independently recoverable, subject to authorized retention and deletion policies.
- Derived summaries preserve their source references.
- Corrections produce new versioned records.

### Epistemic Integrity

- Remembering does not imply believing.
- Authentication does not imply factual correctness.
- Reputation does not establish truth.
- Conflicting evidence is preserved.
- Inferences remain distinguishable from observations.
- Every admitted assertion has traceable provenance.

### Authority Integrity

- Knowledge does not grant authority.
- Authority is explicitly authenticated, scoped, and revocable.
- Agents cannot authorize their own memory modifications.
- Memory cannot modify governing security policy through content ingestion.

### Security Integrity

- Untrusted content cannot silently become trusted instructions.
- Provenance and security labels survive transformations.
- Retrieval enforces access restrictions before context injection.
- Consequential operations require independent authorization.
- Suspicious information can be retained without being admitted into ordinary trusted knowledge.

### Operational Integrity

- The canonical writer owns state transitions.
- Derived state is reconstructable.
- Retrieval is budget-aware.
- Context management is external to the model.
- Memory remains model- and framework-independent.

---

# 20. Open Architectural Questions for Independent Review

This proposal intentionally leaves several implementation and theoretical decisions open.

The reviewing agent should challenge these rather than assume the proposed mechanisms are optimal.

1. **Data model:** Is the combination of an event ledger, atomic claims, and four logical graphs the most appropriate representation? Are there more expressive or simpler alternatives?

2. **Memory ontology:** Are the proposed object types sufficient? Should additional primitives be introduced or existing types consolidated?

3. **Epistemic model:** Is the proposed four-valued evidence classification sufficient? How should uncertainty, partial truth, ambiguity, and source dependence be represented?

4. **Trust architecture:** Are identity, authority, reputation, evidence, and interest sufficiently separated? Is any important dimension missing?

5. **Security:** Does the admission and retrieval architecture adequately address memory poisoning, prompt injection, compromised identities, and cross-agent trust laundering?

6. **Reputation:** What statistical model can provide useful domain-specific reliability estimates without creating self-reinforcing feedback loops or unjustified confidence?

7. **Interest modeling:** Is a separate interest and incentive graph justified? How should inferred conflicts be represented without creating unjustified assumptions about intent?

8. **Retrieval:** What combination of lexical, semantic, temporal, graph, and associative retrieval provides the best recall and precision under strict context budgets?

9. **Context management:** What is the optimal division between automatic middleware retrieval, agent-initiated retrieval, and proactive working-set maintenance?

10. **Determinism:** Is the proposed event-sourced single-writer control plane sufficient? Are additional consistency, concurrency, and recovery mechanisms necessary?

11. **Storage:** Is a relational canonical store with derived graph and vector indexes the best initial implementation, or is another architecture preferable?

12. **Multi-agent governance:** How should identity federation, delegation, cross-organizational sharing, and revocation work across heterogeneous agent runtimes?

13. **Privacy:** Can the proposed historical-preservation model coexist with enforceable deletion and retention requirements without compromising auditability?

14. **Migration:** How can legacy document-based memory be progressively refined without inventing completeness, provenance, or semantic authority?

15. **Fundamental challenge:** Is this architecture solving the correct abstraction of persistent AI memory? Are there more fundamental approaches that would be simpler, safer, or more capable?

---

# 21. Review Expectations

This document is submitted for an independent, ambitious, and adversarial architectural review.

The reviewer should not limit itself to checking whether the proposed components are internally consistent.

It should challenge the foundational assumptions.

In particular:

- Identify unnecessary complexity and opportunities for architectural condensation.
- Identify missing fundamental concepts.
- Challenge the four-graph model and propose alternatives where appropriate.
- Investigate whether the proposed epistemic and trust model is sufficiently rigorous.
- Examine adversarial failure modes, including failures involving multiple cooperating agents.
- Challenge the proposed retrieval and relevance mechanisms.
- Evaluate whether deterministic machinery is assigned the correct responsibilities.
- Identify hidden sources of nondeterminism and authority ambiguity.
- Propose better data structures, algorithms, and subsystem boundaries.
- Distinguish theoretical elegance from practical engineering value.
- Identify which mechanisms should be implemented initially and which should remain future extensions.

The reviewer is explicitly encouraged to propose substantial changes, including replacing parts of the proposed architecture when a better fundamental solution exists.

However, every proposed change should explain:

1. The problem with the current design.
2. The alternative mechanism.
3. Why the alternative is superior.
4. Its security and consistency implications.
5. Its implementation and operational costs.
6. How it can be independently verified.

The objective is not to preserve the proposal unchanged.

The objective is to arrive at the strongest practical architecture for universal, persistent, evidence-grounded AI memory.

---

# 22. Closing Vision

UPMS is intended to become a persistent cognitive substrate that outlives individual AI models, agents, sessions, and applications.

It should maintain an evolving representation of the environment in which its agents operate:

- What happened.
- What is known.
- Why it is believed.
- Who established it.
- Who has authority.
- What interests are involved.
- What remains uncertain.
- What has changed.
- What is currently important.
- What the agent should remember now.

Its purpose is not simply to store more information.

Its purpose is to preserve accumulated experience, establish trustworthy knowledge, protect against adversarial information, and make relevant context available efficiently.

The context window should no longer bear the responsibility of remembering everything.

Instead, the agent should operate against an independently maintained, continuously evolving memory substrate.

**The model may change. The agent may change. The session may disappear. The accumulated and appropriately governed memory should remain.**