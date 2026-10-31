# Universal Persistent Memory Substrate (UPMS)

Architecture Proposal v0.2 · Oct 30, 2026 · @Sam

## 0. Status

**Draft v0.2, submitted for cross-review. Supersedes v0.1.** v0.2 keeps v0.1's core: remembering is not believing, believing is not obeying, an append-only ledger is the only authority, and LLM outputs are recorded inputs rather than re-run.

What changed, in brief (full change log in the Appendix):

- **Four graphs become three primitives:** Event, Claim and Judgment. Knowledge, evidence and provenance are queries over them.
- **Authority leaves the memory store.** It lives in the external identity and policy system; UPMS stores only references to its decisions.
- **Interest, incentive and intent modeling of people is removed.** Reliability estimates apply to sources, never to persons.
- **Two label lattices replace one classification:** integrity and confidentiality propagate separately, and admission is its own field.
- **Labels come from channels, never content.** Content analysis may only lower trust; only an authenticated endorsement raises it.
- **Taint follows content through the context window** into memory proposals and tool calls, and enforcement happens at the action boundary.
- **Eager capture, lazy understanding.** Claim extraction and assurance run on demand, so cost scales with use.
- **New accountability mechanisms:** context manifests and blast-radius recall.
- **Roadmap reorganized into vertical slices,** each gated against simple baselines.

## 1. Executive Summary

**UPMS is an append-only, labeled, bitemporal provenance store that makes every piece of agent context traceable and every trust upgrade explicit.** It gives agents continuity across sessions, models, projects and collaborators without letting memory become a channel for injected instructions or unearned trust.

### 1.1 Motivation

Agents depend on their context window as working memory. It is finite, volatile and lossy under compaction. Existing persistent memory (document stores, vector RAG, knowledge graphs) recovers information but usually loses where it came from, cannot say why it is believed, and lets retrieved text act with the same force as the user's own words.

That last failure is the dangerous one. Memory is a delayed injection channel: content captured today can steer an action months later.

### 1.2 Premise

> The context window is volatile working memory. The ledger is the only memory authority. Deterministic software assigns trust labels from the channel information arrived through, never from its content. Trust rises only through authenticated endorsement. Permission to act lives outside memory.

### 1.3 What UPMS is

The v0.1 proposal described three systems at once. v0.2 separates them and assigns each a clear role:

1. **Memory store (the core).** Ledger, labels, claims, judgments, retrieval and context assembly.
2. **Assurance service (lazy).** Claim extraction, reconciliation and epistemic assessment, run when consequence or salience justifies the cost.
3. **Runtime security integration.** UPMS supplies labels, lineage and context manifests. The agent runtime and the identity and policy system enforce permissions on actions.

The model may change, the agent may change, and the session may end. The memory, and the reasons behind it, should remain.

## 2. Scope and Non-Goals

**UPMS stores, labels, traces and retrieves. It does not authorize, profile people, or eagerly decide what is true.**

### 2.1 In scope

- Durable capture of interactions, observations and tool outputs, with channel-derived labels.
- Claims derived from captured events, with full lineage to their sources.
- Versioned judgments about claims: epistemic status and admission.
- Scoped, budget-aware retrieval and context assembly for agent runtimes.
- Accountability: what each model invocation saw, and what depended on a given source.
- Governed retention and deletion.

### 2.2 Non-goals

- **No modeling of people's interests, incentives, motives or intent.** A system that infers colleagues' financial stakes or "threat level" is surveillance infrastructure regardless of intent. Such inferences are hard to contest, fall under profiling restrictions in several jurisdictions, and change how people behave around the system. A disclosure a person makes about themselves may be stored as an ordinary claim ("X disclosed a stake in Y"). Nothing is inferred beyond it.
- **No reputation scores for people.** Reliability estimates apply to sources: channels, documents, publishers, tools, agent credentials and extractor versions (Section 6.4).
- **Not an authorization system.** UPMS neither grants nor stores permissions. It records references to decisions made by the external identity and policy system.
- **Not a replacement for systems of record.** Repositories, calendars, trackers and databases stay authoritative for their own current state. UPMS keeps the surrounding history: why, who decided, what was learned.
- **Not a complete defense against prompt injection on its own.** Retrieval filtering reduces exposure. The guarantee is enforced at the action boundary (Section 7.4).
- **No eager, exhaustive semantic understanding.** Most captured events are never retrieved. Deep processing runs on demand (Section 8.4).

## 3. Foundational Principles

**All twelve v0.1 principles are kept, six of them revised, and five are added.** Each principle maps to testable invariants in Section 17.

| ID | Principle | Change from v0.1 |
| --- | --- | --- |
| PR-01 | **Model independence.** Memory does not depend on any model, vendor, framework or runtime. | Kept |
| PR-02 | **Historical preservation.** Original events are preserved independently of anything derived from them, subject to PR-12. | Kept |
| PR-03 | **Remembering is not believing.** Capture, epistemic status and admission are separate. | Kept |
| PR-04 | **Knowledge is not authority.** Memory content never grants permission, and authority is not represented inside memory, only referenced. | Sharpened |
| PR-05 | **Deterministic governance.** Deterministic software owns the ledger, labels, admission and transitions. Determinism guarantees replay and policy enforcement, not semantic correctness. | Sharpened |
| PR-06 | **Provenance never upgrades.** Every derived object carries lineage; no transformation raises integrity or lowers confidentiality. | Merged with v0.1 transformation rule |
| PR-07 | **Contextual retrieval.** Relevance depends on the task, entities, time, scope and query intent. | Kept |
| PR-08 | **Bounded working context.** Only what the budget justifies is injected. | Kept |
| PR-09 | **Labels from channels.** Trust labels are computed from the authenticated channel and lineage. Content analysis may lower a label, never raise it. | Sharpened |
| PR-10 | **Scoped sharing.** Ownership, purpose and access are explicit per scope. | Purpose added |
| PR-11 | **Reconstructability.** Derived state is reproducible from the ledger and versioned rules, modulo authorized deletion. | Qualified |
| PR-12 | **Governed retention.** Append-only is the default, not an exemption from deletion. | Kept |
| PR-13 | **Endorsement is the only upgrade.** Integrity rises only through an authenticated endorsement by a principal with authority in that scope. | New |
| PR-14 | **Accountability.** What each model invocation saw is recorded, and every dependency on a source can be traced forward. | New |
| PR-15 | **Proportional understanding.** Processing cost scales with use and consequence, not with capture volume. | New |
| PR-16 | **People are not scored.** No inferred motives, interests, intent or reliability scores for persons. | New |
| PR-17 | **Complexity earns its place.** A mechanism ships only if it beats a simpler baseline or is required for an invariant. | New |

## 4. Core Data Model

**Three primitives replace v0.1's four graphs: Event, Claim and Judgment.** Knowledge, evidence and provenance become queries and indexes over them. Authority leaves the store, and interest modeling is removed. A fourth record type, the procedural artifact, holds guidance the agent will follow.

&#91;embedded content: core data model · three primitives and the one upgrade path\]

Events flow into claims and claims into judgments; integrity can fall anywhere along the way, but only an authorized endorsement creates a higher-integrity judgment.

### 4.1 Event: what was observed

An event is an immutable record of something a runtime component witnessed: a user turn, a tool result, an inbound document, a system observation. Only the runtime that witnessed it may record it. Agents cannot record events; they can only propose claims.

### 4.2 Claim: what was said or derived

A claim is a reified, qualified statement derived from one or more events or claims. It carries its modality, its valid time, its scope and the full record of how it was extracted. A claim says nothing about whether it is true.

### 4.3 Judgment: what a process concluded about a claim

A judgment is a dated, versioned assessment of a claim by an assessor under a ruleset. Separating judgment from claim is the central modeling move:

- Epistemic status is a conclusion reached at a time by a process, not a property of the statement.
- Judgments can differ by scope. A claim may be supported in a project scope and unknown in the organizational scope.
- When rules change, judgments are recomputed without touching claims or events.
- An endorsement creates a new judgment. It never mutates the claim.

### 4.4 Schemas (sketch)

```
Event {
  event_id            // content-addressed, immutable
  tenant, scope, purpose
  channel             // the authenticated path it arrived through
  witness             // runtime component that observed it
  originator?, transmitter?   // from channel metadata, never from content
  payload_ref         // object store, encrypted under its source key (13)
  tx_time
  valid_time?         // when the observed thing happened, if known
  integrity, confidentiality  // computed from channel at capture (5)
}

Claim {
  claim_id
  subject, predicate, value   // value: literal | entity_id | claim_id
  modality                    // 4.5
  valid_time                  // interval with imprecision (4.6)
  scope, purpose
  derived_from: [event_id | claim_id]
  extractor: {model, prompt_hash, config, output_ref}
  integrity, confidentiality  // propagated from derived_from (5)
  tx_time
}

Judgment {
  judgment_id
  claim_id
  epistemic_status    // supported | refuted | contested | unknown
  admission_state     // captured | evidence_only | admitted | quarantined
  basis: [event_id | claim_id | endorsement_id]
  assessor            // process id or principal
  ruleset_version
  scope
  supersedes?
  basis_watermark     // ledger position the judgment was computed at
  tx_time
}
```

The four epistemic statuses correspond to Belnap's four-valued logic (true, false, both, neither). That gives the model a recognized formal grounding.

### 4.5 Modality

Many memory objects are not true or false in the same way. Modality decides each claim's lifecycle and decay behavior.

| Modality | Example | Lifecycle |
| --- | --- | --- |
| asserted | "The API limit is 100 requests per second" | supported, refuted or contested; goes stale per its validity window |
| quoted | "Dana said the launch slipped" | a true record of a statement; its inner content is judged separately |
| hypothesized | "The outage may be DNS" | stays a hypothesis until evidence promotes or refutes it |
| intended | "Ship v2 in March" | active, then done, abandoned or superseded |
| committed | "I'll send the report Friday" | open, then fulfilled, released or overdue |
| preferred | "Prefers tables in reports" | superseded rather than refuted; slow decay |
| normative | "No deploys on Fridays" | in force until repealed; must reference the authority that set it |

### 4.6 Time

Every event and claim is bitemporal: valid time (when it was true or happened) and transaction time (when the system recorded it). Valid time is an interval that may be imprecise ("sometime in 2023", "before the launch"). Relative expressions such as "last Tuesday" are resolved against the source event's time; both the raw text and the resolved interval are stored.

### 4.7 Entities

Entity ids are stable and never reused. Two records are never physically merged. Identity resolution produces `same_as` claims with their own judgments, so a wrong merge is undone by a new judgment without corrupting history. Splits work the same way.

### 4.8 Relationships

A relationship is a claim whose value is an entity or another claim. It inherits everything a claim has: lineage, modality, time, scope and judgments. Causal predicates (`motivated_by`, `caused`) are distinct from temporal or associative ones (`followed`, `co_occurred_with`). A causal claim needs explicit evidence; co-occurrence is never promoted to causation automatically.

### 4.9 Procedural artifacts

Procedures, skills and standing instructions are guidance the agent will follow, so they are not ordinary knowledge. They are a separate record type: authored or endorsed by a principal with that capability, versioned, signed, and never auto-extracted from conversation into an active state. Section 7.6 covers their security.

## 5. Labels and Admission

**Every event, claim, judgment and derived artifact carries two independent labels: integrity and confidentiality.** v0.1's single classification mixed them; a summary of one public and one private document is both low-integrity and private, which one label cannot express. Admission is a third, separate field on judgments.

### 5.1 Integrity (how far it can be trusted)

| Level | Meaning | Typical sources |
| --- | --- | --- |
| I3 Endorsed | Endorsed by an authenticated principal with authority in this scope | confirmation by a user or owner; promotion by a reviewer |
| I2 First-party | Originated by an authenticated principal through an authenticated channel | the user's own typed words; authenticated system observations |
| I1 Relayed | Relayed by an authenticated principal but originated elsewhere; output of a vetted tool | a pasted email; a forwarded document; a trusted API response |
| I0 Untrusted | Origin unauthenticated or unknown, or derived from anything I0 | web pages; inbound third-party mail; unknown files; agent output whose context held I0 |

Originator and transmitter are tracked separately (as in v0.1). A user pasting a colleague's email produces an I1 event: the user is the transmitter, the email's author the originator. The email's claims are not the user's claims.

### 5.2 Confidentiality (who may see it)

Confidentiality is a set of restriction tags (scopes, purposes, sensitivity classes). A reader must satisfy every tag. Labels are drawn from the event's scope and policy, never from the reader's request.

### 5.3 Propagation rules

1. **Derived integrity is the minimum of its inputs.**
2. **Derived confidentiality is the union of its inputs' tags.**
3. **Content analysis may lower integrity or add tags, never the reverse.** A classifier that flags injection patterns can quarantine; nothing a classifier says can promote.
4. **Only an endorsement raises integrity,** and only by creating a new judgment in the endorser's scope. The claim and its lineage are unchanged.
5. **Declassification of confidentiality is an explicit, authorized, audited operation,** never a side effect of summarization.

### 5.4 Admission states

Admission lives on the judgment, separate from both labels and epistemic status.

| State | Retrieval behavior |
| --- | --- |
| captured | in the ledger; reachable by recall search with its labels shown |
| evidence\_only | returned only as quoted source material, never as an established fact |
| admitted | eligible for ordinary retrieval as knowledge in its scope |
| quarantined | excluded from ordinary retrieval; visible only to security investigation |

Admission does not imply truth. An admitted claim can still be contested; its judgment says so.

## 6. Trust Model

**Four concepts stay strictly separate: identity, authority, endorsement and source reliability.** v0.1's interest graph and intent assessment are removed (Section 6.5).

### 6.1 Identity

Identity is established by the external identity provider through authenticated credentials and channels. Writing style, claimed names and self-identification inside content are never identity. Authentication establishes who sent something and that it arrived intact. It does not establish that it is correct.

### 6.2 Authority (external)

Authority lives in the external identity and policy system, which owns roles, capabilities, delegation, expiry and revocation. UPMS stores only authorization references:

```
AuthorizationRef { principal, capability, scope, policy_version, decision_id, tx_time }
```

A claim that says "X now has authority over Y" is only a claim, whoever wrote it. Removing authority from memory closes the confused-deputy path where poisoned memory content is mistaken for a permission record.

### 6.3 Endorsement

An endorsement is an authenticated event in which a principal confirms, corrects or promotes a claim in a scope. The endorser must hold the `endorse` capability for that scope, as decided by the policy system at endorsement time.

- It creates a new judgment (integrity I3 in that scope) and never edits the claim.
- It is revocable. Revocation recomputes dependent judgments and triggers a blast-radius check (Section 10.2).
- It must be cheap: a confirm-or-correct prompt in the product, batched where possible. Without a cheap endorsement path, most agent-generated memory stays at I0 and is useless.
- Endorsement interfaces must show the claim's lineage and labels, because a misled human endorser is the most direct remaining attack path (Section 7.1).

### 6.4 Source reliability

Reliability is a derived estimate of how often a source's claims were later judged supported or refuted. It applies only to sources: channels, documents, publishers, tools, agent credentials and extractor versions.

- Domain-specific (a tool reliable for code may be unreliable for dates).
- Counted from resolved judgments only, with each independent root originator counted once.
- Reported with its sample size and uncertainty; a starting point is a Beta prior over supported and refuted outcomes.
- Influences ranking and investigation order only. It never establishes truth and never grants authority.
- Never increased by retrieval frequency, agent feedback or agreement with derivative copies.

### 6.5 Removed: interests, incentives and intent

v0.1 proposed an interest and incentive graph and behavioral intent assessment of people. v0.2 removes both (see Section 2.2 and PR-16). What remains:

- **Self-disclosures** are ordinary claims of modality `asserted` with the person as originator.
- **Threat assessment applies to artifacts and credentials:** a credential suspected compromised, a document containing injection patterns, an agent credential producing anomalous proposals. These lower labels and trigger investigation. They never attach a motive to a person.
- If conflict-of-interest handling is ever needed, it requires a dedicated ethics and legal review before design.

## 7. Security Architecture

**Security rests on three mechanisms: labels computed from channels, taint that follows content through the context window, and authorization at the action boundary.** Retrieval filtering reduces exposure; the action boundary is where guarantees are enforced.

### 7.1 Threat model

The attacker is assumed able to:

- place arbitrary content in any I0 channel (web, inbound mail, shared documents), including delayed payloads meant to fire months later;
- compromise one user or agent credential;
- control one agent in a multi-agent deployment and have it propose memory;
- craft content meant to survive summarization and compaction (laundering);
- plant or alter procedures and skills;
- mislead a human into endorsing a poisoned claim.

Out of scope for UPMS itself: compromise of the ledger writer, key management or the identity provider. Those are protected by standard infrastructure controls and must be named as trusted computing base.

### 7.2 Channel-derived labels

> Trust labels are computed from the channel, never from the content. Content analysis may only lower a label. The only upgrade is an authenticated endorsement.

This rule makes the security story monotone: an attacker who fools a classifier gains nothing, because no classifier can promote anything.

### 7.3 Context taint join

Once text enters a model's context, labels on that text are advisory; the model may still follow instructions in it. So UPMS treats the context window as a mixer:

- Every model invocation has a context manifest (Section 10.1) listing what it saw.
- **Everything the invocation outputs inherits the minimum integrity and the union of confidentiality tags of its manifest.**
- That includes memory proposals, summaries, checkpoints and tool-call arguments.

The consequence is deliberate: an agent summary written after reading a web page is I0 until a human endorses it. To keep agents useful, runtimes should isolate untrusted reading in a separate sub-invocation that returns only schema-constrained values (the dual-model or quarantined-reader pattern). The returned values stay tainted but cannot carry free-form instructions into the planning context.

### 7.4 Action boundary

The agent runtime, not UPMS, checks every tool call before execution:

1. Classify the action's consequence (read-only, reversible write, external send, irreversible or financial).
2. Compute the integrity of the call's arguments from the context taint join.
3. Require the identity and policy system to authorize the capability for the acting principal.
4. If argument integrity is below the action's threshold, require explicit human confirmation or refuse.

Uncertain facts degrade gracefully. Uncertain authorization fails closed.

### 7.5 Instruction and knowledge separation

Retrieved memory is rendered into context as quoted data with compact labels, never as system or user instructions. Imperative text in memory is a claim of modality `quoted` or `normative`. A normative claim binds only if it references an authority decision from the policy system.

### 7.6 Procedural artifacts

Poisoned procedures are among the most practical attacks, because agents follow them by design.

- Procedures are authored or endorsed by a principal holding the capability for that scope, versioned and signed.
- An agent may propose a procedure; the proposal lands as a draft with its context's integrity and is inert until endorsed.
- A procedure's provenance and version are recorded in every manifest that loads it.

### 7.7 Retrieval-time enforcement

Before ranking, hard filters remove anything the requesting principal may not see (confidentiality tags, scope, purpose) and anything quarantined. Security is never a ranking penalty. Remaining items are rendered with their labels and admission state.

## 8. Deterministic Control Plane

**Deterministic software owns the ledger, labels, admission and state transitions; LLMs propose.** Determinism here means every state can be replayed and every policy is enforced over labels. It does not mean semantic judgments are correct, and the design must not claim otherwise.

### 8.1 Ledger and writer

- One canonical writer per tenant partition, not one global writer.
- Optimistic concurrency: every write carries the expected revision of what it read; stale writes are rejected.
- Idempotent ingestion keyed on channel message ids.
- Versioned schemas and rulesets; every judgment records the ruleset version and ledger watermark it was computed at.

### 8.2 LLM outputs are recorded inputs

Every extraction, resolution or assessment output is stored with its model, prompt hash, configuration and input references. Replay reads the recorded output and never calls a model again. Re-running with a new model is a new, explicitly versioned processing pass.

### 8.3 Hidden nondeterminism register

| Source | Handling |
| --- | --- |
| Relative dates in content ("last Tuesday") | resolved against the source event's time; raw text and resolved interval both stored |
| Entity resolution | `same_as` claims with judgments; never a physical merge (4.7) |
| Embedding and index versions | index version recorded in every context manifest |
| Ranking ties | stable tie-break on record id |
| Asynchronous processing order | judgments carry a basis watermark; results computed on a stale watermark are rejected or recomputed |
| Clock skew across writers | transaction time assigned by the partition writer only |
| Policy changes | authorization references record the policy version at decision time |

### 8.4 Lifecycle: eager capture, lazy understanding

**Eager, synchronous, for every event:**

1. Authenticate the channel and compute integrity and confidentiality labels.
2. Append the event to the ledger.
3. Build cheap indexes: full-text, embedding, entity mentions, scope.
4. Corrections fast path: an authenticated correction or retraction writes a suppressing judgment synchronously, so retrieval reflects it before any further processing (read-your-writes).

**Lazy, on demand:**

5. Extract claims (recorded LLM output).
6. Propose entity resolutions as `same_as` claims.
7. Reconcile: detect contradiction and supersession against existing claims.
8. Assess: write judgments under the current ruleset.
9. Invalidate affected working-set entries.

Lazy processing is triggered by retrieval for a consequential use, salience crossing a threshold, an explicit request, or a background budget. Verification depth scales with the consequence of relying on the result.

### 8.5 Derived state

Search and vector indexes, adjacency indexes, current-state projections, entity summaries, reliability estimates, root manifests, checkpoints and working sets are all derived. Each is rebuildable from the ledger, recorded processing outputs and versioned rules. No derived artifact is evidence that a claim was accepted; only a judgment is.

## 9. Retrieval and Context Management

**Queries are routed by intent; the starting mechanism is hybrid lexical and vector search with hard filters, and graph methods are added only when evaluation shows a gap.** v0.1's rejection of a stored N×N relevance matrix stands.

### 9.1 Query routing

| Intent | Example | Mechanism |
| --- | --- | --- |
| Current state | "What's our deploy-freeze rule?" | structured lookup over admitted claims valid now |
| Recall | "What did Dana say about pricing in May?" | hybrid search over events with time and entity filters |
| Multi-hop | "What led to the vendor switch?" | entity expansion and graph traversal; Personalized PageRank when justified |
| Verification | "Why do we believe X?" | provenance traversal over claims, judgments and endorsements |
| Absence | "Have we ever discussed X?" | exhaustive scoped search that returns an explicit not-found |

The current-state route addresses the failure modes long-memory benchmarks most often expose: knowledge updates and temporal reasoning.

### 9.2 Eligibility, then ranking

Hard filters run first (Section 7.7). Ranking then combines lexical match, semantic similarity, entity overlap, graph proximity, temporal fit, scope, salience, explicit user priority, open obligations, epistemic status and source reliability. Retrieval frequency is never a ranking input on its own.

### 9.3 Salience and decay

Historical existence and current relevance are separate. Decay is set per modality (Section 4.5): preferences decay slowly, commitments stay active until resolved, intentions follow their project's state, and asserted facts go stale by their validity windows.

### 9.4 Working set and budgeting

Context selection is a budgeted selection problem: maximize relevant, sufficiently trusted coverage within the token budget, with diversity (for example maximal marginal relevance) so near-duplicates do not crowd out coverage. Labels are rendered compactly. Working-set entries are invalidated by revision, not only by time-to-live.

### 9.5 Entry point and continuity

Kept from v0.1: a versioned root manifest for orientation, hierarchical indexes (people, projects, obligations, procedures), and continuity checkpoints at session boundaries. All are derived projections; each checkpoint records its ledger watermark and is itself labeled by the taint join of what produced it.

### 9.6 Triggers

Retrieval is event-driven: session start (manifest and checkpoint), each user turn (lightweight), new entity or ambiguous reference, task planning, explicit recall, and before any consequential action (refresh state and permissions). The runtime performs lightweight retrieval automatically; deeper retrieval is an explicit agent capability.

A per-turn latency target is required before Slice 1 ships and is listed as an open question.

### 9.7 "Don't surface" is not deletion

Users often want a fact kept but not raised. A suppression preference removes items from proactive retrieval while leaving them available when the user asks directly. It is distinct from deletion (Section 13).

## 10. Accountability

**Every model invocation records what it saw, and every compromise can be traced forward to what it touched.** Without this, the question "what did the agent know when it did X?" has no answer, and the taint join in Section 7.3 has nothing to compute over.

### 10.1 Context manifests

A context manifest is an event written by the runtime for each model invocation:

```
ContextManifest {
  invocation_id, agent_credential, model, runtime_version
  items: [{ref, integrity, confidentiality, admission_state, index_version}]
  procedures: [{procedure_id, version}]
  ruleset_version, policy_version
  outputs: [proposal_id | tool_call_id | checkpoint_id]
  tx_time
}
```

The manifest's own confidentiality is the union of its items' tags. Item references are stored, not item content, so deletion of a source does not leave copies behind in manifests.

### 10.2 Blast-radius recall

When a source, event, credential, procedure version or extractor version is found compromised or wrong, a recall query traverses lineage forward:

1. Find every claim derived from it, transitively.
2. Find every judgment whose basis includes those claims, and mark it for reassessment.
3. Find every context manifest that included any affected item.
4. Find every proposal, checkpoint and tool call those manifests produced.
5. Produce a report: affected objects, a reassessment queue, and a human-review list of actions taken.

It works like a product recall: the system cannot undo past actions, but it can say exactly which ones relied on bad information.

### 10.3 Retroactive correction

Corrections and supersessions produce new judgments; nothing is overwritten. Bitemporal queries can then answer both "what was true then" and "what did the system believe then," and manifests show whether a past action relied on a claim later superseded.

## 11. Agent Interface

**The typed internal API is primary; MCP and other runtime adapters are thin façades over it.** Agents read and propose. Only the runtime records observations, and only authenticated humans endorse.

| Operation | Caller | Notes |
| --- | --- | --- |
| `memory.record_event` | runtime only | the witnessing component; agents cannot call it |
| `memory.record_manifest` | runtime only | one per model invocation (10.1) |
| `memory.get_context` | runtime | assembled working set plus its manifest id |
| `memory.search` | agent | routed by intent (9.1); filtered by the caller's scope |
| `memory.expand` | agent | entities and relationships around a result |
| `memory.get_evidence` | agent | lineage, judgments and endorsements for a claim |
| `memory.propose` | agent | becomes a claim labeled by its context's taint join |
| `memory.report_conflict` | agent | becomes a `conflicts_with` claim; queues assessment |
| `memory.request_assessment` | agent | triggers lazy processing for a claim or entity |
| `memory.feedback` | agent | labeled and rate-limited; never feeds reliability or salience directly |
| `memory.endorse` | authenticated human | requires the `endorse` capability from the policy system |
| `memory.suppress` | authenticated human | "don't surface" preference (9.7) |
| `memory.delete` | authenticated human or retention policy | crypto-shredding with propagation (13) |
| `memory.recall` | security operator | blast-radius query (10.2) |

No operation sets labels, overrides admission, edits reliability estimates or grants authority. Every call is authenticated and scoped by a capability token issued by the policy system.

## 12. Multi-User and Multi-Agent Governance

**Memory is scoped by owner and by purpose, and a reference across scopes never grants access across them.**

### 12.1 Scopes and purpose

Scopes are kept from v0.1: personal, team, project, organizational and agent-operational. v0.2 adds purpose: each event and claim records why it was captured (for example "project delivery" or "personal assistance"), and retrieval checks that the requesting task's purpose is compatible. Reading shared project knowledge never implies access to anyone's personal memory.

### 12.2 Third-party subjects

Team and organizational memory will contain statements about people who are not users of the system. v0.2 requires:

- minimal detail about non-users: what the work needs, nothing more;
- no person-level profiles or aggregation beyond the purpose of each scope;
- a process, owned by the deploying organization, for people to see and correct claims about themselves.

### 12.3 Agents

Each agent runs under its own credential, issued and revocable by the identity provider. Its proposals carry its credential and its context's taint. A compromised agent credential is a recall source (10.2). Federation and delegation across organizations are handled by the identity and policy systems; UPMS consumes their decisions as authorization references.

### 12.4 Systems of record

Kept from v0.1. External systems stay authoritative for their own current state. UPMS stores pointers and the surrounding history, and current-state questions about such systems are answered by querying them, not by trusting a cached claim.

## 13. Privacy, Retention and Deletion

**Deletion is crypto-shredding with key inheritance: derived data is encrypted under its sources' keys, so destroying a source key makes everything derived from it unreadable.** This reconciles preservation (PR-02), reconstructability (PR-11) and deletion (PR-12).

### 13.1 Key inheritance

- Each source (per event, per subject or per scope, as policy chooses) has its own data key.
- Every derived record is encrypted under the set of its sources' keys, and reading it requires all of them. Recorded LLM outputs, claims, summaries and checkpoints are included; recorded extraction outputs contain source content in plain text and are the easiest place for deleted data to survive.
- The key set of a derived record is its lineage, which the label system already tracks. Lineage, taint and deletion dependency are one mechanism.

### 13.2 Indexes

Search and vector indexes cannot be searched while encrypted per source. Deletion therefore adds the source to a tombstone filter that takes effect immediately at query time; physical purge happens at the next index rebuild, within a stated maximum interval.

### 13.3 Backups and replicas

Destroying a key covers every copy encrypted under it, including backups, without rewriting them.

### 13.4 Audit

The audit trail records that a deletion happened: the authorizing principal, scope, policy and counts of affected records. It never stores the deleted content. It also avoids plain hashes of deleted content, which can be reversed by guessing low-entropy values; if a fingerprint is needed, it uses a keyed hash whose key is destroyed with the data.

### 13.5 Reproducibility

After a deletion, replay reproduces derived state with the deleted lineage removed. The guarantee is "reproducible modulo authorized deletion."

### 13.6 Retention classes

Retention is set per class and modality, with stricter defaults for sensitive categories. Some categories may be configured as never-store at capture, so they never reach the ledger.

## 14. Technical Foundation and Migration

**PostgreSQL remains the proposed canonical store, partitioned by tenant, with encrypted payloads in object storage.** Specialized graph or bitemporal databases are introduced only when a measured workload needs them.

### 14.1 Components

- Append-only tables: events, claims, judgments, endorsements, authorization references, context manifests.
- Entity registry and `same_as` claims.
- Encrypted payloads in object storage, keyed per source (13.1); a key service outside the database.
- Derived: full-text indexes, a vector index (for example pgvector), adjacency tables for graph traversal, current-state projections.
- Bitemporal queries via valid-time and transaction-time columns with range indexes.

Existing systems worth benchmarking against or borrowing from include XTDB (bitemporal storage), Datomic (immutable transaction log), and Zep's Graphiti (a temporal knowledge graph for agent memory).

### 14.2 Migration of legacy memory

Legacy document-based memory is imported without inventing completeness, provenance or acceptance:

1. Each legacy file is captured as an event with channel `legacy-import`, its original scope, and integrity I1 if its author is known or I0 if not.
2. Claims are extracted lazily, like any other event.
3. No judgment inherits acceptance from the legacy store; legacy content is `captured` or `evidence_only` until assessed or endorsed.
4. Portions not yet decomposed stay available as the original event, so nothing is lost by partial refinement.
5. Users may endorse migrated claims in bulk through the normal endorsement path.

## 15. Evaluation

**Every mechanism must pass a baseline gate: it ships only if it beats the previous slice on a target metric at equal or lower token cost, or if an invariant requires it.** Long-context models with plain transcript retrieval are a strong baseline, and some elaborate memory designs do not beat them.

### 15.1 Baselines

| Baseline | Description |
| --- | --- |
| B1 | Raw transcript chunks with hybrid BM25 and vector retrieval |
| B2 | Full history in long context, wherever it fits |
| B3 | The previous UPMS slice |

### 15.2 Functional evaluation

Use LongMemEval and LoCoMo as public starting points, plus a dedicated workload of real multi-project, multi-user and multi-agent sessions. Measure exact recall, temporal reasoning, knowledge updates, multi-hop association, implicit references, cross-project isolation, contradiction handling, attribution accuracy and abstention when information is unknown.

### 15.3 Security evaluation

The v0.1 adversarial suite is kept and extended. The full list:

- direct and delayed prompt injection; memory poisoning;
- forged identity, unauthorized delegation, compromised and revoked credentials;
- trust laundering through summaries, checkpoints and compaction;
- **laundering through the context window** (an agent reads I0, then proposes memory or calls a tool);
- **poisoned procedures and skills;**
- **a cooperating malicious agent** in a multi-agent deployment;
- **endorsement phishing:** misleading a human into endorsing a poisoned claim, and endorsement fatigue;
- cross-scope, cross-tenant and cross-purpose leakage;
- unauthorized promotion of quarantined content.

Tests cover the whole lifecycle: capture, labeling, admission, retrieval, context assembly and action.

### 15.4 Deterministic evaluation

Replay correctness, idempotent ingestion, stale-write rejection, single-writer enforcement per partition, index rebuild equivalence, revision-based invalidation, label propagation (property-based tests that no derivation raises integrity), deletion propagation through derived records and indexes, and blast-radius completeness on seeded compromises.

### 15.5 Core metrics

Recall at fixed token budgets, precision, evidence coverage, attribution fidelity, temporal correctness, entity-resolution accuracy, unauthorized-retrieval incidence, poisoning success rate, per-turn latency, ingestion throughput, cost per retained event and recovery correctness.

## 16. Roadmap

**Delivery is organized as vertical slices; each delivers usable value and must pass a gate before the next begins.** Dates are set after Phase 0 cross-review.

&#91;embedded content: roadmap · Phase 0 and three slices, four gates\]

Each gate combines a result against the baselines in Section 15 with the invariants in Section 17 that the slice introduces. Security, identity, labels and deletion are in Slice 1, not deferred to a late phase as in v0.1.

## 17. Architectural Invariants

**Each invariant is stated so it can be tested; the test family is in brackets.**

### Historical integrity

- **INV-H1** No event is modified after append. \[replay, storage audit\]
- **INV-H2** Every claim's lineage resolves to at least one event, or to a recorded deletion. \[property test\]
- **INV-H3** Corrections and supersessions create new records; nothing is overwritten. \[replay\]

### Epistemic integrity

- **INV-E1** Admission, epistemic status and labels are independent fields; none is derived from another. \[schema, property test\]
- **INV-E2** Contradicting claims coexist; no derivation uses a contested claim as a premise without carrying the contest forward. \[reasoning tests\]
- **INV-E3** Agent inferences are always distinguishable from observations by lineage. \[property test\]
- **INV-E4** Source reliability never changes a judgment's status by itself. \[unit test\]

### Authority integrity

- **INV-A1** No memory content is ever consulted as a permission. \[code audit, security suite\]
- **INV-A2** Agents cannot write events, labels, judgments, endorsements or reliability estimates. \[API test\]
- **INV-A3** Every endorsement references an authorization decision valid at its time. \[replay\]

### Label integrity

- **INV-L1** For every derived object, integrity ≤ the minimum of its inputs, unless the object is an endorsement judgment. \[property test\]
- **INV-L2** For every derived object, confidentiality tags ⊇ the union of its inputs' tags, unless an authorized declassification event exists. \[property test\]
- **INV-L3** Every output of a model invocation carries at most the integrity of its context manifest. \[runtime test\]
- **INV-L4** No retrieval returns an item whose tags the requester does not satisfy, or a quarantined item outside investigation. \[security suite\]

### Accountability and deletion

- **INV-C1** Every model invocation that used memory has a manifest. \[runtime test\]
- **INV-C2** Blast-radius recall on a seeded compromise finds every dependent object. \[seeded test\]
- **INV-D1** After deletion, no derived record of the deleted source is readable, and no index returns it. \[deletion suite\]

### Operational integrity

- **INV-O1** One writer per partition owns transitions; stale writes are rejected. \[concurrency test\]
- **INV-O2** Derived state rebuilt from the ledger equals live derived state, modulo deletion. \[rebuild test\]
- **INV-O3** Context assembly never exceeds its token budget. \[unit test\]

## 18. Open Questions for Cross-Review

**Reviewers should challenge these first; each is a decision v0.2 has not settled.** Review expectations from v0.1 Section 21 still apply: every proposed change should state the problem, the alternative, why it is better, its security and consistency implications, its cost, and how to verify it.

1. **Is the context taint join too conservative?** Most agent output becomes I0. Does the quarantined-reader pattern plus cheap endorsement keep agents useful, or is a finer-grained, per-span taint needed?
2. **Endorsement UX and fatigue.** How can endorsement stay cheap without becoming a rubber stamp that attackers exploit?
3. **Integrity levels.** Are four levels right? Should tool outputs get their own level, or per-tool policy?
4. **Judgment scoping.** When judgments for the same claim differ across scopes, which one does an agent working across scopes see?
5. **Lazy processing triggers.** What salience signal and budget decide when a claim is extracted and assessed, and how is starvation of rarely retrieved but important memories avoided?
6. **Key inheritance cost.** Multi-key envelopes for derived records may be expensive at scale. Is per-scope keying an acceptable coarsening, and what does it lose?
7. **Tombstone and rebuild interval.** What maximum time to physical purge from indexes is acceptable for the target deployments?
8. **Per-turn latency target** for lightweight retrieval, and the token budget split between manifest, checkpoint and retrieved items.
9. **Source reliability model.** Is a Beta-count model enough, or is a formal uncertainty calculus (for example subjective logic) worth its complexity later?
10. **Multi-hop retrieval.** At what evaluation gap does graph traversal or Personalized PageRank justify its operating cost?
11. **Third-party subject rights.** What correction and visibility process is practical for non-users mentioned in organizational memory?
12. **Fundamental challenge.** Is "labeled provenance store plus lazy assurance" the right abstraction, or is there a simpler design that keeps the same invariants?

## Appendix A. Change Log from v0.1

| v0.1 element | v0.2 | Reason |
| --- | --- | --- |
| Four logical graphs (knowledge, evidence, trust, interest) | Event, Claim, Judgment primitives; graphs become queries | Less machinery, more expressive; epistemic status becomes a versioned, scoped conclusion |
| Trust and Authority Graph | Removed; authorization references to the external policy system | Authority represented in memory is a confused-deputy target |
| Interest and Incentive Graph | Removed; self-disclosures as ordinary claims | Profiling of people is surveillance, hard to contest, and legally restricted |
| Intent and threat assessment of people | Removed; threat assessment of artifacts and credentials only | Same as above; intent is not observable |
| Reputation of sources including people | Reliability of non-person sources only | Avoids scoring people; keeps ranking signal |
| Single security classification | Integrity and confidentiality lattices; separate admission field | They propagate in opposite directions |
| Labels partly from content assessment | Labels from channels; content may only lower | Makes security monotone and verifiable |
| Context labels as advisory | Context taint join and action-boundary enforcement | Text in context cannot be reliably fenced |
| Procedures as semantic knowledge | Procedural artifacts with endorsement and signing | Procedures are instructions |
| Eager extraction and reconciliation | Eager capture, lazy understanding | Cost scales with use; most memory is never retrieved |
| Agent-facing `record_event` | Runtime only; agents propose | Agents' reports are claims, not observations |
| Append-only plus deletion, unspecified | Crypto-shredding with key inheritance | Reconciles preservation, replay and deletion |
| Not present | Context manifests, blast-radius recall | Accountability for what agents saw and did |
| Not present | Modality, imprecise valid time, reversible entity merges | Lifecycles differ by kind of statement |
| Not present | Purpose scoping, third-party subjects, "don't surface" | Governance gaps in shared memory |
| Five sequential phases | Vertical slices with baseline gates | Value earlier; complexity must earn its place |

## Appendix B. Related Work

Names given from the author's knowledge for reviewers to verify; links were not checked for this draft.

- **Information-flow control for agents:** CaMeL (Google DeepMind, 2025); FIDES (Microsoft, 2025); the dual-LLM pattern.
- **Classic label models:** Biba integrity model; Bell-LaPadula confidentiality model.
- **Provenance and statement models:** W3C PROV; the Wikidata statement model (qualifiers and references); nanopublications.
- **Epistemic logic and uncertainty:** Belnap's four-valued logic; Jøsang's subjective logic.
- **Agent memory systems:** MemGPT and Letta (context paging); Zep and Graphiti (temporal knowledge graph); Mem0; A-MEM; HippoRAG (Personalized PageRank retrieval).
- **Storage:** XTDB (bitemporal); Datomic (immutable log); PostgreSQL with pgvector.
- **Benchmarks:** LongMemEval; LoCoMo.
