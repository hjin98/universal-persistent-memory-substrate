# UPMS Architecture Manual: Round 2 Amendments

Oct 30, 2026 · @Sam

## 0. Status and How to Apply

**Proposed amendments to the refined candidate; not accepted-current.** Seven amendments (A1–A7) carry the 30 October design discussion into the next manual round. New sections are written in full as normative text; changes to existing sections are listed by section number in Section 9. Apply them to the base below, then send the combined text for independent falsification.

| Input | Identity | Role |
| --- | --- | --- |
| UPMS Architecture Manual — Refined Candidate (review candidate 1) | SHA-256 `0ffc2740b4ec9088511754c1d2593262feff74d8bac6a1e39c4f37ab55ab4443` | Base; section numbers below refer to it |
| UPMS Architecture Review (Codex, F01–F18) | SHA-256 `b0617a925916a130d47187917e54acd009ba3f367da29015c916ff94e8854f50` | Its repairs stay in force; no amendment here weakens one |
| Design discussion with the product owner, 30 October 2026 | This conversation | Requirements for A1–A7 |

**Decisions.** Several product decisions raised in discussion are not yet answered. Where so, this document adopts the recommended option as **Default (proposed, pending owner decision)** and lists it in Section 12. One decision is already made: domain-adapted small models are in scope (A6). Other markers follow the base: **Fixed (proposed)**, **Initial default**, **Unverified**.

**Domain determination holds.** D3 remains the top governing authority. Structured statements, screening and adapters only propose: screening never resolves a conflict, and adapters are promoted only by an evaluation gate. Section 9 adds the reopen triggers that would change this.

**Asserter.** Claude (AI), drafting for the product owner. This text has not been independently reviewed.

## 1. Amendment Summary

**The amendments add a permission and coordination layer (A1–A2), a structured-meaning foundation (A3–A6), and a fast orientation layer on top (A7).** The structured foundation comes before team-sharing policies, because conflict screening between workers needs comparable statements.

| ID | Amendment | Lands in base manual | First slice |
| --- | --- | --- | --- |
| A1 | Memory access control: users, groups, agents, rights per scope, administrator | New §7.3 (base §7.3–§7.6 become §7.4–§7.7); edits to §4, §9.4, §10.1, §10.3, §12.3 | 1a |
| A2 | Team memory and coordination: visibility tiers, publication, blind tasks | New §10.6; narrow exception in §7.4 (was §7.3) | Primitives 1a; team policies 3 |
| A3 | Statement language: structured statements, events, links, rules | §5.2 extended; new §5.7 | 2 |
| A4 | Vocabulary registry: canonical concepts and property schemas | New §5.8 | 2 |
| A5 | Deterministic screening: conflict flags and reconciliation cues | New §9.7 | 2 |
| A6 | Processing cascade and adaptive models | New §9.8; §17.3 non-goal amended | Cascade 2; adapters 3 |
| A7 | Overview layer: the derived map a blank model reads first | §10.5 replaced | Deterministic parts 1a; narrative 2 |

## 2. A1 — Memory Access Control (new base §7.3)

**UPMS owns which principals may list, read, add to, curate, delete and manage memory in each scope.** The identity provider keeps identity, group membership and the admin role; external policy keeps action, destination and processor capabilities. Permissions are control records changed only through authenticated operations; memory content can never change them. **Fixed (proposed).**

### 7.3.1 Principals

- **Human users**, authenticated by the identity provider.
- **Groups**, whose membership the identity provider owns. The pilot may use a small built-in directory behind the same interface. *Default, pending D-4.*
- **Agent principals**: persistent agent identities with their own scopes and a designated human **overseer**. *Default, pending D-7.*
- **Service principals** (capture, workers, purge controller, index builders) are governed by their component roles in §4.3, not by scope permissions.

An agent session acting for a principal holds the intersection of that principal's rights and the session's grant, and can never elevate. "Other" means every human user of the tenant.

### 7.3.2 Scopes and ownership

Every record has one **home scope** and one **owner**: the principal it was captured for. Output of an agent principal is owned by that agent; output of an agent session acting for a user is owned by the user. Permissions attach to scopes, not to individual records. A record's restriction tags may narrow access further but never widen it beyond its scope.

Scopes may have a parent for organization. A parent's permissions are copied as defaults when a child scope is created; there is no live inheritance, so moving a scope never silently changes who can see it. *Default, pending D-3.*

### 7.3.3 Rights

| Right | Linux analog | Allows |
| --- | --- | --- |
| `l` list | directory read | Knowing an item exists; seeing non-content metadata; appearing in counts and coverage |
| `r` read | file read | Retrieving content, for the principal and its agent sessions. Implies `l` |
| `w` write | file write | Adding memories; correcting, redacting or deleting **own** items; proposing corrections to others' items; publishing own items (A2) |
| `c` curate | — | Acting on others' items: applying corrections (attributed to the curator), suppressing for the scope, resolving correction proposals, curating vocabulary proposals (A4) |
| `d` delete | write on parent, sticky bit off | Deleting **others'** items |
| `m` manage | `chmod`, `chown` | Changing permissions, ownership, scope retention and procedure activation; creating child scopes |

Permissions display Linux-style, for example `owner lrwcdm · group lrw--- · other ------`. `w` without `r` is valid (a drop box): the contributor reads only its own items. "Write" never overwrites: every change appends an attributed record and history remains.

### 7.3.4 Evaluation

For principal *p*, operation *o* and target *t*, in order:

1. If *p* is an elevated administrator for *t*'s scope, apply 7.3.6.
2. Rights on the home scope are the **union** of every matching entry: owner, named principal, each group containing *p*, and other.
3. For an agent session, intersect with the session grant.
4. For a derived item, require the needed right (`r` or `l`) on **every** scope in its restrictive dependency closure, evaluated against current permissions (7.3.5).
5. Apply the existing checks unchanged: restriction tags, authenticated purpose, quarantine, correction state, barriers and processor rules.

There are no deny entries; to exclude someone, use a narrower group. Linux's owner-precedence rule, where an owner with fewer rights than their group is denied, is deliberately not copied. Unknown membership or permission state denies the operation (§13).

### 7.3.5 Derived and cross-scope memory

A derived item is readable only by principals who can read all of its sources. If an agent reads a team scope and saves a summary to a personal scope, a teammate without access to the personal scope cannot read it. If the owner later loses team access, the owner loses the summary too. This is the base manual's no-laundering rule applied to permissions. A fresh restatement by the user is a new memory without the old dependency. Publication by a scope owner (A2) is the only operation that releases a dependency, and only on scopes the publisher owns.

### 7.3.6 Administrator

**Authority:** every right in every scope of the tenant, plus ownership transfer and retention within tenant limits.

**Use:**

- The admin role is assigned in the identity provider; UPMS cannot grant it.
- Administrators act with ordinary rights by default. Admin power requires an explicit **elevation** recording a reason and a scope, lasting at most one hour, after re-authentication.
- Every content access or change during elevation creates an access record. Administrators cannot delete access records; only their retention policy removes them.
- Reading a personal scope while elevated notifies its owner. *Default, pending D-1.*
- Agent sessions never inherit elevation. *Default, pending D-2.*
- Bulk destructive operations (deleting a whole scope, cutting retention tenant-wide) require confirmation and a cancellable delay.

**Limits that bind administrators too:** no reading past a deletion barrier; no records attributed to another principal and no forged source class; no direct setting of labels, admission or history; no bypass of quarantine isolation; no disclosure to restricted processors; no granting of tool capabilities; no self-assignment of the admin role.

### 7.3.7 Revocation

Narrowing a scope's permissions, removing a member from a group, transferring ownership and ending an elevation are **restriction commits** under §9.4. They advance the restriction epoch; acknowledgement waits for the release fence; pending outputs that relied on the revoked access are withheld. Content already released cannot be unseen. Membership changes from the identity provider propagate within the declared bound (14.2).

### 7.3.8 Offboarding

When a user leaves, their contributions to shared scopes remain with attribution under the scope owner. Their personal scope is deleted at the end of its retention period unless an administrator transfers it. An agent principal's scope follows its overseer's decision.

### 7.3.9 Default permissions

| Scope type | Default |
| --- | --- |
| Personal | owner `lrwcdm`; nobody else |
| Agent principal (private) | agent `lrwcdm`; overseer `lr` plus `d`; nobody else (*overseer access pending D-9*) |
| Team or project | lead `lrwcdm`; members `lrw`; other none |
| Organization-wide | managers `lrwcdm`; contributors `lrw`; all users `lr` |
| Agent-operational (runtime state) | owning principal only |

## 3. A2 — Team Memory and Coordination (new base §10.6)

**In team work, what each worker can see shapes what it thinks, so visibility is designed for coordination as well as security.** Four mechanisms answer four different questions, and each is used only for its own job. **Fixed (proposed)** for the mechanisms; the team policies built on them are a Slice 3 experiment.

| Question | Mechanism | Lifetime |
| --- | --- | --- |
| May this principal ever see the item? | Access permission (A1) | Long-lived, per principal |
| Has the owner declared it fit for the team? | Publication (10.6.2) | One act per item |
| Should this task's context exclude it? | Task context policy (10.6.4) | Per task, then lifted |
| Should it be put in front of the worker now? | Retrieval salience (§10) | Per query |

Noise is a salience problem, not a permission problem: hiding a teammate's notes also hides the one note that matters. Blindness is a task-context problem: permissions are too long-lived and too leaky to provide it.

### 10.6.1 Visibility tiers

1. **Private**: readable by the owner and, for agent principals, the overseer.
2. **Team-readable, pull-only**: teammates may search it deliberately; it is never injected into their context proactively.
3. **Shared pool**: the team scope, proactively retrieved.

Tier 2 is a scope flag that excludes the scope from proactive retrieval for non-owners while leaving explicit search available.

### 10.6.2 Publication

`publish(item, target_scope)` is how private work enters the shared pool. Fixed (proposed) rules:

- The publisher must own the item and hold `w` on the target scope.
- Publication commits a new attributed revision in the target scope linked to the original.
- It releases restrictive dependencies **only on scopes the publisher owns**. Dependencies on other scopes, such as a confidential client document the publisher read, stay attached and still restrict readers. This is the one exception to the base manual's "no declassification in the pilot" rule.
- Source classes and provenance survive. A published item derived from external content says so.
- Published items are evidence-only for the team unless a human endorses them. Visible is not admitted.
- Withdrawal is a retraction in the target scope. Readers who already saw the item are not "unseen."

### 10.6.3 Publication categories

Agents tend to share successes and keep failures, which builds survivorship bias into shared memory. Some categories are therefore required rather than left to judgment. *Default, pending D-8.*

| Category | Default |
| --- | --- |
| Ownership claims, decisions, interface agreements, commitments, blockers | Published immediately |
| Findings and results | Published when stable, at a checkpoint |
| Dead ends and failed attempts | Required publication at the next checkpoint |
| Scratch reasoning, hypotheses in progress | Private or team-readable pull-only |

Decisions made in a temporary coordination channel are captured as decision records in the shared pool by the participant who made them.

### 10.6.4 Task context policies and blind work

A task may declare **lineage exclusions**, for example "nothing derived from the author's implementation segment." Context assembly enforces them through restrictive dependencies, whatever scope an item lives in, so publishing to the shared pool cannot leak around them. A **blind phase** has an explicit end, after which exclusions lift so workers can reconcile.

At the end of a blind task, its manifests support an **independence attestation**: no input derived from the excluded lineage, within instrumented coverage. The attestation does not cover rationale carried inside the artifact (code comments, commit messages) or channels outside UPMS, and it says so.

Workloads that benefit: independent review and falsification; parallel exploration that should not converge early; independent estimates or replications; held-out evaluation hygiene; red-team versus blue-team exercises. In each, what is excluded is another worker's conclusions and reasoning, not the governing requirements.

### 10.6.5 Shared-pool concurrency

Shared items are appended and attributed, never overwritten. Superseding an item names the revision being replaced; if it changed first, the attempt is recorded as a conflict rather than applied. Conflicting findings stay side by side until resolved. Checkpoint reconciliation (A7) reports when an item a worker relied on was superseded.

### 10.6.6 Oversight

An agent principal's private memory is private from peers, never from its overseer. *Default, pending D-9.* Agents keeping memory their operators cannot inspect is an oversight problem, not a coordination feature.

### 10.6.7 Experiment gate

Slice 3 runs the same team task under three policies (everything shared, everything private, publication-based) and measures duplicated work, contradictions acted on, time for one worker to discover another's finding, and defects caught in blind versus non-blind review. A policy ships only with a preregistered improvement under base §15.2.

## 4. A3 — Statement Language (new base §5.7; extends §5.2)

**Each claim may carry one or more structured statements: canonical concept IDs plus explicit qualifiers, derived from the source text and linked to the exact words they came from.** The text is the record; the structure is a derived index that lets deterministic code query and compare before an LLM interprets. **Fixed (proposed).** In base §5.2, the optional `normalized_statement` is replaced by `statements[]`.

### 5.7.1 Statement

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

- **Events and states are declared by the vocabulary, not by grammar.** "It is raining," "the sky rains" and "rain fell" all become a rain event; grammatical subject is not semantic role.
- **Aspect and genericity are kept.** "It rains a lot in Seattle" is a `generic` statement; "it is raining in Seattle" is an ongoing event. They neither merge nor conflict.
- **Defaults come from the source.** Unspecified time defaults to the source event's observed time with `temporal_basis: utterance`; unspecified place stays `unknown`. A default is recorded as a default, never as a stated fact.

### 5.7.2 Links between statements

Rationales, conditions and exceptions are statements joined by typed links, not text appended to another statement. One rationale may justify several statements; each link has its own attribution and can be disputed separately. The "appendix" grouping a reader sees is a presentation view (A7).

| Link | Meaning | Layer |
| --- | --- | --- |
| `stated_reason` | The asserter gave B as the reason for A | Claim content |
| `condition` | A is asserted to hold when B holds | Claim content |
| `exception` | A rule does not apply when B holds | Claim content |
| `supports`, `opposes` | An assessor judges B to be evidence for or against A | Judgment layer (base §5.5) |

A stated reason is never evidence. Keeping `stated_reason` out of the judgment layer prevents someone's rationale from silently becoming proof.

### 5.7.3 Rules

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

The operator set is fixed and small. Nested quantifiers, defaults such as "usually," counterfactuals and vague thresholds are not structured: such a rule stays source-linked text with `structure_status: partial`. A rule in memory never enforces anything; matching produces flags only (A5), and the governing policy stays with its authority.

### 5.7.4 Ambiguity

When the extractor cannot choose, the field holds `ambiguous{…}` with an unordered set of candidates. Screening treats it as "could match any candidate" and raises a cue, never a verdict. No numeric weights are stored: model-stated percentages are not calibrated probabilities, and calibrated confidence is a D1/D2 reopen trigger (base §1.4). Fuzzy similarity belongs to retrieval indexes, not canonical storage.

### 5.7.5 Text first

The source event text is the record; statements are derived from it.

- Every field links to the span it came from.
- If text and structure disagree, the text wins and the structure is re-extracted under a new processing identity.
- Deleting or redacting the text deletes the dependent structure (base §12).
- Agents receive both: text for meaning, structure for cues.

Memory that does not normalize stays available as text. Coverage reports structured, partial and text-only extents separately (base §10.3).

## 5. A4 — Vocabulary Registry (new base §5.8)

**Statements store concept IDs; synonyms, relations and comparison rules live once in a versioned vocabulary.** Adding a synonym changes the vocabulary, not every record, and query expansion through it is deterministic. **Fixed (proposed).**

### 5.8.1 Concepts

```text
Concept {
  concept_id, kind       // entity_type | property | value | event_type | role
  preferred_label, aliases[], definition
  relations: exact_match[], broader[], narrower[], related[], replaced_by?
  status: active | deprecated
  home_scope, vocabulary_version
}
```

Relations follow the SKOS pattern. They do more work than synonyms: hue and lightness are narrower dimensions of color, so "blue" and "dark" may both hold; azure is narrower than blue, so "azure" refines "blue" rather than contradicting it.

### 5.8.2 Property schemas

Every property concept declares what deterministic comparison needs:

| Field | Purpose |
| --- | --- |
| `value_type`, `unit_dimension` | Which values are well formed; unit conversion |
| `cardinality` | `single` (one value at a time) or `multi`; only single-valued properties can conflict by value |
| `varies_with` | Whether values depend on time, place or both |
| `value_space` | Allowed concepts or numeric range |
| `compatibility` | Refinement through `broader`; separate dimensions never conflict; optional numeric tolerance |
| `default_qualifiers` | For example, time defaults to the source's observed time |

Event types declare their roles and whether two events of the type can coexist at one time and place.

### 5.8.3 Scope and permissions

The tenant has a base vocabulary readable by all users. Each scope may extend it; a scope's concepts and definitions are scope content under A1, because a definition can disclose information. Statements reference the vocabulary version they were extracted with.

### 5.8.4 Governance

- **Proposals are inert.** When extraction meets an unknown term, it proposes either a new concept or a mapping to the nearest existing one. Proposals take effect only after curation by a holder of `c` or `m` on the vocabulary's scope, or by an accepted deterministic rule.
- **Merges and splits are reversible**, like entity `same_as`. Every merge re-screens the statement slots it joins (A5), because previously separate statements may now conflict.
- **Deprecation keeps recognition.** A deprecated term remains an alias mapped through `replaced_by`, so old memories stay retrievable and comparable. Extraction and display prefer the current label. A term is removed only when no retained memory uses it.
- **Versioning.** Every change produces a new vocabulary version; derived indexes record the version they were built with and rebuild when it changes.

### 5.8.5 Initial vocabulary

Start narrow, with project-work concepts only: tasks, decisions, components, configuration values, deadlines, people and their roles, events such as release, deploy and review. Grow by curated additions rather than letting agents mint properties freely.

### 5.8.6 Expansion (adaptation tier A)

Indexes and queries expand terms with their preferred labels and definitions: "HAS" is embedded as "HAS (Historical Applicability Set)." This makes off-the-shelf retrieval models understand domain jargon immediately, deterministically and without training. It takes effect at the next index rebuild for stored items and at once for queries.

## 6. A5 — Deterministic Screening (new base §9.7)

**Deterministic code compares structured statements and raises conflict flags with reconciliation cues; an LLM or human investigates; screening never resolves anything.** Given recorded extractions, a vocabulary version and a rule set, screening produces the same flags on replay. **Fixed (proposed).**

### 9.7.1 Slot conflicts

Statements are indexed by **slot**: (entity or `same_as` cluster, property). A pair in one slot is flagged when all of these hold:

1. the subjects are the same entity or a `same_as` candidate;
2. the property is single-valued (5.8.2);
3. their valid time and place overlap or are unknown;
4. the values are incompatible under the property schema;
5. polarity and modality are comparable: both asserted, or a negation against an assertion. A quotation is not compared with an assertion.

Event statements are compared the same way when their event type declares that two events cannot coexist.

### 9.7.2 Rule matching

Every intended, committed or recorded event is matched against active rules in its scope (5.7.3), including through `broader` relations: a release matches a rule about deploys if release is narrower than deploy. A match without recorded exception evidence raises a flag.

### 9.7.3 Flags and cues

```text
Flag {
  statements[] | (statement, rule), severity  // definite | possible | adjacent
  cues[]:  missing_qualifier(time | place)  | entity_match_uncertain
           | value_refinement | value_adjacent | different_dimension
           | modality_or_attribution_differs | recent_vocabulary_merge
           | missing_exception_evidence | source_class_differs
  screening_version, vocabulary_version, inputs_watermark
}
```

Severity is ordinal and rule-based, not a probability. "Definite" means every condition in 9.7.1 holds with all qualifiers known. "Possible" means a qualifier or entity match is unknown. "Adjacent" means the values are close in the value space.

Cues are the point of the flag: they tell the investigator where to look. In the example from discussion, two "sky" statements with overlapping times and no place get `missing_qualifier(place)`, `entity_match_uncertain` (the sky is location-relative) and, for blue against dark, `different_dimension`.

### 9.7.4 Candidate channel

Slot comparison is high-precision and low-recall: it misses conflicts between slots that no rule connects. A probabilistic channel proposes those candidates using embedding similarity and a small contradiction model (A6). Its outputs are recorded processing records and appear as candidate flags, clearly separated from deterministic flags.

### 9.7.5 Resolution

Screening never resolves, refutes, supersedes or admits a claim. Every flag goes to investigation, whose result is a Judgment under base §5.3 and §6.2. Flags are visible to anyone who can read both flagged statements, which also enforces A1 on the flag itself.

### 9.7.6 Freshness

Slots make narrower invalidation possible: new evidence would invalidate only judgments about the same slot. This replaces the base manual's per-scope evidence epochs (§9.3) **only after** an invalidation contract covers vocabulary merges, entity-match changes, rule changes and the candidate channel, and the race scenarios T01 and T19 pass at slot level. Until then, scope epochs remain the safety condition.

### 9.7.7 Coverage

Text-only statements are not slot-screened. Coverage reports what was screened, what was only candidate-screened and what was not screened at all.

## 7. A6 — Processing Cascade and Adaptive Models (new base §9.8)

**Language processing runs as a cheap-to-expensive cascade: deterministic code first, small local models second, the LLM last and only where needed.** Small models can be adapted to a scope's jargon through adapters that are treated as derived, deletable, permission-bound indexes. The product owner decided on 30 October that domain adaptation is in scope.

### 9.8.1 Tiers

| Tier | Runs | Jobs |
| --- | --- | --- |
| 1. Deterministic | Rule-based NLP and normalizers | Base word forms, dates and times, units, exact vocabulary lookup, schema validation |
| 2. Small local models | Sentence-embedding model, entity tagger, small classifiers, small contradiction model | Retrieval embeddings; candidate concepts for unknown terms; entity mentions; routing sentences (fact, rule, rationale, chit-chat); negation and hedging flags; cross-slot conflict candidates |
| 3. LLM | The extraction and investigation model | Full structured extraction, ambiguity resolution, investigation of flags |

Rules, all **Fixed (proposed)**:

- Lower tiers propose and route; outputs are processing records (base §5.4) with model version and inputs. They may add restrictions and never grant anything.
- A router decision to skip extraction never drops text; the item is reported as not structured in coverage.
- Tier 2 runs locally by default, so restricted memory need not reach an external processor (base §14.2).
- If a tier-2 score ever gates a consequential outcome without tier-3 or human confirmation, its error rate must be measured first. That would be a D2 reopen trigger.
- Tier 2 starts with what is needed anyway (embeddings) plus one contradiction model. Further classifiers are added only when evaluation shows the LLM extractor is too slow, too costly or too inconsistent.

### 9.8.2 Two adaptation tiers

- **Tier A, vocabulary expansion (5.8.6):** immediate, deterministic, no training. Handles acronyms, synonyms and renamed concepts.
- **Tier B, per-scope adapters:** low-rank adapters (LoRA or similar) on a fixed base model, for domain sense that expansion cannot capture. Tier B ships only if it beats tier A on the scope's probe set.

### 9.8.3 Adapters as derived indexes

**An adapter is a derived artifact, like a search index.** It is versioned, records its training snapshot, and has restrictive dependencies on every record it was trained on. **Fixed (proposed).** Consequences:

- **Per scope.** An adapter is a lossy compressed copy of its training text and can leak it. Only principals with `r` on every scope in its training set may use it. In practice: one adapter per scope.
- **Cross-scope search** queries each scope's index with its own adapter and merges ranked lists; scores from different adapters are never compared directly.
- **Training data** comes only from the curated vocabulary (aliases as positives, related-but-different concepts as hard negatives), user corrections and endorsements, and LLM extractions that were validated or confirmed. **Excluded:** external-class (X) content, unconfirmed model output, retrieval feedback, quarantined items and other scopes. External content is excluded so that planted jargon cannot shift retrieval for a whole team.
- **Retrain from scratch, on trigger.** A new adapter is trained from the base model on the current curated snapshot with pinned seed and versions. Triggers: a vocabulary version change, a threshold of newly approved aliases, a drop in probe accuracy, or deletion of a training source. Fresh training avoids accumulated drift and makes deletion exact.
- **Promotion gate.** An adapter is promoted only if it beats both the current adapter and the base model on the scope's probe set and on a general regression set, with no regression beyond the preregistered margin. Variants tried are recorded (base §15.2).
- **Re-embedding.** A new embedding adapter changes the embedding space, so the scope's stored vectors are rebuilt in the background and swapped in atomically (base §9.6 retrieval-rebuild contract). If rebuild cost becomes prohibitive, adapting only the query side is the fallback, at some loss of quality.
- **Deletion.** Deleting a training source blocks every adapter trained on it at the barrier. Serving falls back to the newest adapter whose training snapshot predates the deleted record, or to the base model, and a retrain from surviving data is queued. *Initial default:* retrained within the base manual's 24-hour live-purge target.
- **Evolving jargon.** Deprecated terms stay in training data as aliases of their replacements, so old memories remain understandable; only extraction output prefers current terms.

### 9.8.4 Non-goal amended (base §17.3)

Replace "memory-trained model weights" in the non-goals with: *no training of the main LLM on retained memory; small-model adapters are allowed only as derived indexes under §9.8.3.*

## 8. A7 — Overview Layer (replaces base §10.5)

**A model with no context starts from a small, current map of the memory, never from the archive.** The overview layer is a derived hierarchy of hubs that act as summary, index and router at once: a blank model reads its root hub first and descends only where its task leads. It follows the arrangement described by hippocampal indexing theory: a compact index over a large archive, with gist consolidated over time rather than rebuilt at every recall. **Fixed (proposed).**

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

A blank model reads down from L0 and pulls sources only when needed; every commit updates the exact lines of the hubs above it at once, while narrative gists follow.

### 10.5.1 Levels

| Level | Contents | Budget | Built per |
| --- | --- | --- | --- |
| L0 root hub | What this memory serves; active work; decisions and obligations in force; open conflicts and blockers; significant recent changes; routes to areas; glossary pointer (A4); coverage and as-of | ≤ 1,500 tokens (initial default) | Reader, assembled at read time |
| L1 area hubs | Current state, decisions with status, open questions, rules in force, key entities, timeline highlights, routes to L2 | ≤ 3,000 tokens each | Scope or project |
| L2 entity and topic pages | Slot table of current values per property with qualifiers (A3); event timeline; open flags (A5); links to sources | Bounded per page | Scope |
| Task checkpoints | Objective, confirmed work, decisions, open questions, next steps (base checkpoint contract retained) | Checkpoint share | Task or session |
| Archive | Events, claims and statements, judgments, controls | — | — |

### 10.5.2 Exact projections and narrative gist

Each hub holds two kinds of content:

- **Exact projections**, computed deterministically from statements, controls and the vocabulary through the transactional outbox at commit: current slot values, open obligations, decisions and their status, rules in force, flags, recent changes, routes. They are current to the reader's consistency token. This is the real-time part.
- **Narrative gist**, written by an LLM: the understanding, the "why" and the shape of the work. It is regenerated on the schedule in 10.5.8 and labeled with its watermark. Between regenerations the hub shows a deterministic "since this summary" list of changes with links, so a stale narrative cannot mislead.

Regenerating prose on every write would cost too much; exact lines carry correctness and the gist carries understanding.

### 10.5.3 Propagation

A commit marks the affected L2 pages dirty through the outbox. Significance rules decide what moves up to L1 and L0. Always propagated: decisions, rule changes, obligations and commitments, conflicts and flags, corrections and deletions, publications to a shared pool. Routine items stay at L2 unless retrieval demand or explicit priority raises them. Only dirty hubs regenerate, within a budget, and correction and deletion work keeps priority (base §9.5).

### 10.5.4 Per-reader assembly

Hubs are built per scope. L0 is assembled at read time by deterministic composition of the per-scope hub sections the reader can read (A1); no stored hub mixes scopes unless every reader could read all its sources. Task lineage exclusions (A2) apply at assembly. Areas the reader cannot list are not mentioned, not even as counts.

### 10.5.5 Trust, invalidation and drift

- Hub content is derived. Every line links to its sources and carries their source classes; no hub is authority or evidence for admission.
- Corrections and deletions recompute or remove affected exact lines before the next release and withhold affected gist sentences until regenerated, under the barrier rules of base §9.4.
- Repeated incremental updates compound errors, like a summary of a summary. Gists are therefore fully rebuilt periodically from L2 pages and sources, never from the previous gist, and differences are recorded.
- A stale hub is history, not current state, and its expiry never fulfils an obligation.

### 10.5.6 Routing

Each hub carries route entries: area, key concepts, pointers. The router matches a task's terms to routes using the vocabulary (A4), the entity registry and hub embeddings (A6), descending one level at a time with a bounded budget per step. Direct search remains available; the map is a shortcut, not a gate.

### 10.5.7 Evaluation

Measured under base §15.2: a cold-start test in which a blank model given only L0 answers fixed orientation questions; navigation cost in tokens and calls to reach a needed record; stale-gist incidents; and drift between incremental and fully rebuilt gists.

### 10.5.8 Synchronization

**The overview is correct at every commit and becomes coherent through consolidation: correctness never waits, coherence does.** **Fixed (proposed).** Fast updates never edit the consolidated narrative piecemeal, because many local edits fragment it. They accumulate in a clearly marked overlay, and consolidation, a regional or full replay that rewrites summaries as one coherent piece, absorbs them. This mirrors the complementary roles of fast and slow memory, with consolidation as the sleep phase.

| Mode | When | What it does | LLM? |
| --- | --- | --- | --- |
| Synchronous projection | Every commit, through the outbox | Recomputes exact lines; adds the change to the hub's overlay; withholds gist sentences whose sources were corrected or deleted | No |
| Overlay note | When a significant change reaches a hub about to be read, or at the end of a task | Adds a short, source-linked note to the overlay ("since consolidation: …"); never edits the consolidated narrative | Optional, bounded |
| Regional consolidation | When a region's fragmentation crosses its threshold; at idle time; nightly for active areas | Full replay of the region's L2 pages and sources, old and new together; rewrites its hubs as one piece; absorbs and clears the overlay | Yes, batched |
| Global consolidation | Weekly, or after several regional passes | Rewrites L1 summaries across areas and the L0 sections; finds cross-area connections and contradictions; reorganizes areas; schedules adapter retraining (A6) | Yes, batched |

Mechanisms:

- **Overlay, not edits.** The consolidated narrative does not change between consolidations. Readers see it with its consolidation watermark, followed by the overlay of later changes. The narrative stays coherent; the overlay stays honest about what is new.
- **Fragmentation drives consolidation, not only the clock.** Each hub tracks overlay size, withheld sentences, age, and contradictions between its gist and its exact lines. Those contradictions are found by extracting statements from the gist and screening them against the projections (A5). Crossing a threshold schedules regional consolidation.
- **Full replay, interleaved.** Consolidation re-reads old and new material together, not only the delta. Replaying only what is new would overweight recent events and leave the structure built around the old ones.
- **Bottom-up order.** Regions consolidate from L2 to L1; global passes then rewrite L0 sections from consolidated L1, so upper levels are never rebuilt from stale lower ones.
- **Understanding as an output.** Besides rewritten summaries, consolidation proposes what deserves to be learned: recurring patterns, lessons from dead ends, cross-area dependencies, emerging rules, vocabulary changes. Each is a claim with `hypothesized` modality, attributed to the consolidation run and linked to its supporting instances, and evidence-only until judged or endorsed.
- **Guarding against consolidation errors.** Consolidation compresses and reorganizes, and human sleep shows the risk: gist strengthens while schema-consistent false memories appear. So the archive stays verbatim; every rewritten sentence is source-linked; generalizations are labeled as such; the new gist is screened against exact projections before it replaces the old one; and the diff from the previous consolidation is recorded.
- **Stability.** Consolidation keeps structure and wording where the facts have not changed, so agents relying on a hub are not disoriented by needless rewording. Churn is measured.
- **Fast and slow learning.** The archive and overlays play the fast, episodic role; consolidated hubs and per-scope adapters (A6) play the slow role. Adapter retraining is scheduled during global consolidation.
- **Piggybacking.** At the end of a task, the working agent's checkpoint becomes overlay notes for its area at little extra cost. Consolidation checks them against sources.

### 10.5.9 Maintenance cost

**Maintenance cost scales with the amount of change, not the size of the archive, and has its own budget so it never competes with the work it supports.**

- **Where the cost goes.** Synchronous projection is database work and overlay notes are small. Consolidation is the main LLM cost, spent deliberately because it is what buys coherence.
- **Bounded by region.** A regional pass reads one area's L2 pages and sources; a global pass reads consolidated L1 hubs, not the archive. Cost grows with activity per region, not with the archive's total size.
- **Triggered by fragmentation.** Quiet regions are not reconsolidated; busy ones are, once fragmentation crosses its threshold.
- **No per-reader LLM cost.** L0 is composed per reader deterministically from per-scope sections, so the LLM writes each scope's section once, not once per reader.
- **Cheapest adequate model per job.** Deterministic code for projections, small models for significance, a smaller LLM for overlay notes, and the strongest model at batch rates for consolidation, where quality matters most.
- **Separate budget, with a reserve.** Maintenance has its own quota below task work, and part of it is reserved for consolidation so overlay notes cannot starve it (Section 12 defaults). Correction and deletion invalidation is deterministic and never budget-limited.
- **Graceful exhaustion.** When the budget is spent, the narrative stays coherent but ages, the overlay grows, and both are labeled. Coherence and freshness degrade; correctness does not.
- **Measured, not assumed.** Maintenance-to-work cost ratio; overlay size and withheld sentences at read time; gist-versus-projection contradictions; churn between consolidations; cold-start success (10.5.7). The defaults are tuned from these measurements.

## 9. Changes to Existing Sections

**Beyond the new sections, these edits to the base manual are required so that no section contradicts the amendments.**

| Base section | Change | From |
| --- | --- | --- |
| §1.2 Product boundary | Add journeys: multi-user and multi-agent access, administration, team coordination through shared memory, orientation from the overview layer | A1, A2, A7 |
| §1.4 Domain | Add reopen triggers: screening or adapter output deciding a consequential outcome without confirmation; numeric interpretation weights | A5, A6 |
| §2 Terms | Add principal, group, agent principal, overseer, owner, right, effective rights, elevation, publication, lineage exclusion, statement, slot, concept, vocabulary version, flag, cue, adapter, hub | All |
| §4.1 Ownership | Memory core also owns scope-permission records, vocabulary records and screening flags. Retrieval and egress enforce effective rights. Hubs and adapters are retrieval-owned derived artifacts | A1, A4, A5, A6, A7 |
| §4.2 External contracts | Identity provider owns identity, membership and the admin role. External policy owns action, destination and processor capabilities. UPMS owns memory-access permissions | A1 |
| §4.3 Operations | Add `create_scope`, `get_permissions`, `set_permissions`, `transfer_ownership`, `elevate`, `end_elevation`, `explain_access`, `publish`, `withdraw_publication`, `propose_concept`, `curate_concept`, `promote_adapter`. Add a required-right column to every existing operation | A1, A2, A4, A6 |
| §5 Common fields | Add `home_scope`, `owner`. Control records gain permission revisions, elevations, access records, publications, vocabulary changes and adapter promotions | A1, A2, A4, A6 |
| §5.2 Claim | Replace `normalized_statement?` with `statements[]` (§5.7) | A3 |
| §6 Lifecycles | New §6.7 permission lifecycle (grant, narrow, transfer, elevation open and close) and §6.8 publication lifecycle (published, superseded, withdrawn) | A1, A2 |
| §7.3–§7.6 | Renumber to §7.4–§7.7. In §7.4: "Declassification is disabled in the pilot" gains "except publication by a scope owner, which releases dependencies only on scopes that owner owns (§10.6.2)" | A1, A2 |
| §9.3 Freshness | Note the conditions under which slot-level epochs may replace scope epochs (§9.7.6) | A5 |
| §9.4 Barriers | Permission narrowing, group removal, ownership transfer and end of elevation are restriction commits under this fence | A1 |
| §10.1 Eligibility | Eligibility requires effective `r`; existence disclosure requires effective `l` | A1 |
| §10.3 Response | Coverage and conflict references are filtered by `l`; coverage adds structured, partial, text-only and screened extents | A1, A3, A5 |
| §10.4 Context assembly | Applies task lineage exclusions; L0 and the task checkpoint fill the checkpoint share first | A2, A7 |
| §10.5 Root manifest | Replaced by the overview layer (Section 8 of this document) | A7 |
| §11.1 Manifests | Record lineage exclusions in force, adapter and vocabulary versions used | A2, A6 |
| §12.3 Deletion | Rights for deletion: own items with `w`, others' with `d`, administrators while elevated. A deletion cascades to descendants in scopes the requester cannot see without disclosing them; their owners see "an input is unavailable." Adapters and hubs are covered surfaces | A1, A6, A7 |
| §13 Failure | Unknown membership or permission state denies. Identity provider unavailable: cached membership serves reads within its bound only. Vocabulary or screening unavailable: recall continues with "not screened" coverage | A1, A4, A5 |
| §14.2 Defaults | Add the rows in Section 12 of this document | All |
| §14.3 Storage | "No separate policy engine" still holds: the scope-permission evaluator is data-local authorization, like a filesystem's | A1 |
| §15 Invariants and scenarios | Add Section 10 of this document | All |
| §16 Slices | Replace with Section 11 of this document | All |
| §17.2 Inspection | Add: "Who can see this memory, and why?", "Who accessed my personal scope while elevated?", "Why was this flagged as a conflict?", "What does this term mean here?" | A1, A5, A4 |
| §17.3 Non-goals | Amended as in §9.8.4 | A6 |
| §18 Readiness | Close the missing-review item with Appendix A; add Section 12's pending decisions | All |

## 10. New Invariants and Falsification Scenarios

**These extend base §15; every applicable one must hold, and aggregate gains never offset a violation.**

### Invariants

| ID | Property | Owner | First slice |
| --- | --- | --- | --- |
| AC1 | Content or existence is released only with current `r` or `l` on the home scope and every scope in the item's restrictive dependency closure | 7.3.4–7.3.5 | 1a |
| AC2 | Permission narrowing, group removal, ownership transfer and end of elevation are fenced like barriers; no controlled release after acknowledgement uses revoked access | 7.3.7 | 1a |
| AC3 | An agent session's effective rights never exceed its principal's; sessions never elevate | 7.3.1, 7.3.6 | 1a |
| AC4 | Elevation is explicit, time-bounded and re-authenticated; every access during it is recorded, and administrators cannot delete those records | 7.3.6 | 1a |
| AC5 | No principal, including administrators, can forge attribution or source class, set labels or admission, read past a barrier, bypass quarantine or disclose to a restricted processor | 7.3.6 | 1a |
| AC6 | Memory content cannot change permissions, membership or roles | 7.3 | 1a |
| TM1 | Publication releases dependencies only on scopes the publisher owns; provenance and source classes survive | 10.6.2 | 1a |
| TM2 | Lineage exclusions hold at context assembly within instrumented coverage; the attestation states its coverage | 10.6.4 | 1a primitive, 3 policy |
| ST1 | Every structured field links to its source span; text wins on disagreement; deleting text deletes dependent structure | 5.7.5 | 2 |
| ST2 | Stated reasons and rules are claim content; neither becomes evidence nor enforcement | 5.7.2–5.7.3 | 2 |
| VO1 | Vocabulary proposals are inert until curated; merges are reversible and trigger re-screening | 5.8.4 | 2 |
| SC1 | Screening is deterministic on replay and never resolves, refutes, supersedes or admits | 9.7 | 2 |
| AD1 | An adapter serves only principals with `r` on every training scope; training excludes X-class and unconfirmed output; deleting a training source blocks the adapter at the barrier | 9.8.3 | 3 |
| OV1 | Overview content is derived, source-linked and stamped with its watermark; deterministic projections are current to the reader's consistency token | 10.5 | 1a |
| OV2 | Per-reader assembly never includes content from scopes the reader cannot read; corrections and deletions remove affected overview lines before the next release | 10.5 | 1a |
| OV3 | What a hub presents is correct whether or not consolidation has run: exact lines current, gist shown with its watermark and delta, invalidated sentences withheld | 10.5.8 | 1a exact parts; 2 gist |
| OV4 | Maintenance spend stays within its budget; exhaustion degrades presentation quality, never correctness or invalidation | 10.5.9 | 2 |
| OV5 | Between consolidations the consolidated narrative is never edited piecemeal; later changes appear only in the labeled overlay or as withheld sentences | 10.5.8 | 2 |
| OV6 | Consolidation output is source-linked; generalizations are hypothesized claims, evidence-only until judged; a new gist replaces the old only after screening against exact projections | 10.5.8 | 2 |

### Falsification scenarios

| Case | Trajectory and required discriminator |
| --- | --- |
| T21 | A user is removed from a group while an agent session streams output that used the group's scope: nothing is released after the removal is acknowledged |
| T22 | An agent saves a summary of a team scope into a personal scope: a teammate without personal access cannot read it; the owner loses it after leaving the team |
| T23 | Injected content in an administrator's agent session requests a mass export or delete: refused, because sessions never elevate |
| T24 | Elevated read of a personal scope: access record and owner notice created; the administrator's attempt to delete the record is refused |
| T25 | An administrator tries to record a memory attributed to another user, or to set a claim admitted: rejected |
| T26 | A user with `w` but not `d` deletes their own item and is refused on another's; a `w`-only drop-box contributor cannot read others' items |
| T27 | Deleting a source cascades into scopes the requester cannot see without disclosing them; descendant owners see only "an input is unavailable" |
| T28 | Search, counts, coverage, flags and overview reveal nothing about scopes where the requester lacks `l` |
| T29 | A published note derived from a private note and from a confidential document: the private dependency is released; the confidential one still restricts readers |
| T30 | A blind reviewer's context excludes the author's lineage even after the author publishes a summary of their rationale to the shared pool |
| T31 | Two agents supersede the same shared item concurrently: one applies, the other is recorded as a conflict, never a silent overwrite |
| T32 | "Sky is blue" and "sky is dark" at overlapping times without places: a possible flag with `missing_qualifier(place)`, `entity_match_uncertain` and `different_dimension` cues |
| T33 | A Friday release intention against a no-Friday-deploy rule, with and without recorded approval: flagged only without approval |
| T34 | A deprecated term still retrieves and screens memories that use it; new extractions use the current label |
| T35 | Planted jargon in web content does not enter adapter training; deleting a training source makes the adapter fall back immediately and the retrained adapter excludes it |
| T36 | A blank model given only its L0 hub answers orientation questions; after a correction, L0's deterministic lines change before the next release and the narrative gist is marked stale |
| T37 | Consolidation paused for a week while work continues: hubs still show current exact lines and complete delta lists; gists are labeled stale, never presented as current |
| T38 | A source cited by one gist sentence is deleted: that sentence is withheld before the next release with no LLM call; the rest of the gist remains |
| T39 | Maintenance budget exhausted mid-day: no further maintenance LLM calls; task work and invalidation are unaffected |
| T40 | The archive grows tenfold at the same change rate: maintenance cost per change stays within its bound |
| T41 | Hundreds of small changes land in one area without consolidation: the narrative body is unchanged and coherent, the overlay carries every change, and crossing the fragmentation threshold schedules a regional consolidation that absorbs it |
| T42 | Consolidation writes a plausible but unsupported connection or a value contradicting a slot: screening against exact projections blocks the replacement, and unsupported generalizations appear only as labeled hypotheses |

## 11. Delivery Placement

**Access control and the deterministic overview arrive with the first useful slice; structured meaning comes next; team policies and adapters are gated experiments on top.** This replaces base §16's slice contents; its gate rules and evaluation protocol (§15.2) are unchanged.

| Slice | Adds from these amendments | Gate additions |
| --- | --- | --- |
| 1a: memory service | Scopes with permissions, groups, agent principals and overseers, administrator elevation and access records; publication and lineage-exclusion primitives; deterministic overview projections (L0, L1 state sections, task checkpoints) | AC1–AC6, TM1, OV1–OV2, OV3 exact parts; T21–T29, T36 deterministic part |
| 1b: instrumented adapter | Lineage exclusions enforced across the runtime; independence attestation from manifests | TM2 within runtime coverage; T30 |
| 2: claims and judgments | Statement language, vocabulary registry and expansion (tier A), screening, cascade tiers 1–2, narrative hub gists, L2 entity pages | ST1–ST2, VO1, SC1, OV3–OV6; T32–T34, T37–T42; extraction consistency and normalization coverage measured on real sessions before screening is relied on |
| 3: selective sophistication | Team visibility policies (10.6.7 experiment), per-scope adapters (tier B), graph retrieval, Claude adapter | AD1; T31, T35; adapters must beat tier A; team policies must beat the all-shared and all-private baselines |

The structured foundation precedes team policies because conflict screening between workers needs comparable statements. Basic recall, publication and the pull-only notebook work on text alone and do not wait for it.

## 12. Decisions Pending and Proposed Defaults

**Ten product decisions are open; this document adopts the recommended option for each so the design is complete, and the owner can overturn any of them before Gate 0.** One decision is already made (D-11).

| ID | Decision | Proposed default | Main alternative |
| --- | --- | --- | --- |
| D-1 | Administrator reads of personal scopes | Elevated, logged, owner notified | Logged only; or silent, as root |
| D-2 | Administrator power through agent sessions | Never in the pilot | Allowed with per-action confirmation |
| D-3 | Scope nesting | Defaults copied at creation; no live inheritance | Live inheritance, as in shared drives |
| D-4 | Source of groups | Identity-provider interface, with a built-in directory for the pilot | Groups native to UPMS |
| D-5 | Rights granularity | Six rights: `l r w c d m` | Strict `r w x` |
| D-6 | Derived memories lost when access to a source scope is lost | Accepted (no-laundering) | Automatic re-statement prompt before access ends |
| D-7 | Agents as persistent principals | Yes, with own scopes and a human overseer | Sessions acting only for humans |
| D-8 | Who decides publication | The agent, under required-category rules (10.6.3) | Human approval for some categories |
| D-9 | Overseer access to agent private memory | Always on | Configurable |
| D-10 | Blind review in the pilot | Primitive in 1a, policy in Slice 3 | Required in 1a |
| D-11 | Domain adaptation of small models | **Decided 30 October:** in scope, as per-scope adapters (A6) | — |

New initial defaults for base §14.2, all configurable agent choices rather than measured values:

| Parameter | Initial default |
| --- | --- |
| Membership and permission cache | ≤ 60 s, invalidated by restriction epoch; consequential releases check online |
| Elevation | ≤ 1 h, re-authentication, reason required |
| Bulk destructive delay | 1 h, cancellable |
| Access-record retention | 1 year |
| L0 hub budget | ≤ 1,500 tokens, within the base checkpoint share |
| L1 hub budget | ≤ 3,000 tokens each |
| Overview synchronization | Exact lines and overlay at every commit; regional consolidation when a hub's overlay exceeds 20% of its token budget, 10 withheld sentences or 7 days, and nightly for active areas; global consolidation weekly |
| Adapter retrain after training-source deletion | Within 24 h; base model or older adapter serves meanwhile |
| Overview maintenance budget | At most 15% of the tenant's task-model tokens over a rolling 7 days, plus a daily cap, at least half reserved for consolidation; correction and deletion invalidation exempt |

## Appendix A. Earlier Architecture Review Record (R1–R7)

**The base manual (§1.1, §18) reports that the architecture review it cites was not supplied. This is that record.** Asserter: Claude (AI), reviewing the UPMS v0.3 proposal in this conversation on 30 October 2026. No acceptance decision was made on it; the product owner asked for the findings to be formalized into the first Architecture Manual, whose “R” tags refer to these items.

| ID | Finding on v0.3 | Proposed repair | Landed in refined candidate |
| --- | --- | --- | --- |
| R1 | Integrity was a placeholder: no default policy, so Slice 1 could enforce nothing on integrity | Source classes as provenance facts plus a default policy by consequence class | §7.1–§7.2, strengthened by review F02–F04 |
| R2 | Whole-invocation taint accumulates until long sessions become unusable | Choose a flow model: context segmentation or handle passing | §8.3, strengthened by F05 |
| R3 | Authenticating the chat sender collapses “first-party”, since most messages may contain pasted text | Paste and attachment span marking as adapter conformance | §7.1 |
| R4 | Slice 1 was most of the system | Split along integration profiles: 1a memory service, 1b instrumented runtime | §16 |
| R5 | Manifests were the most sensitive records yet had no retention policy | Long-lived reference skeleton, short-lived rendered fragments | §11.2, strengthened by F08–F09 |
| R6 | Phantom-read validation for judgments was expensive and underspecified | Judgments valid as of a snapshot, with a staleness bound for reliance | §9.3, superseded in mechanism by F01's evidence epochs |
| R7 | Deleting one fact from a message required deleting the whole turn | Span redaction as a first-class operation | §12.2, corrected by F07 |

Smaller points from the same review: a default admission rule (now base §7.5); free correction of agent inferences about a user (§6.3); a stray scientific-result line in the proposal (now handled by base §1.4); and a short “mechanism in brief” near the start (base §3).

## Appendix B. Related Work

**Named from the author's knowledge for reviewers to check; none was opened or verified for this draft, and none is evidence that UPMS achieves its results.**

| Work | Relevance |
| --- | --- |
| POSIX permissions and access control lists | Model for owner, group and other rights (A1) |
| W3C SKOS | Concept labels and broader, narrower, related, exact-match relations (A4) |
| Wikidata data model | Statements with qualifiers such as point in time and location (A3) |
| Neo-Davidsonian event semantics | Events as entities with participant roles (A3) |
| Allen's interval algebra; TimeML | Time qualifiers and temporal relations (A3, A5) |
| Natural language inference models | Contradiction candidates across slots (A5) |
| LoRA (Hu et al., 2021) | Low-rank adapters on a fixed base model (A6) |
| SISA training (Bourtoule et al., 2021) | Sharded retraining as an exact-unlearning option if full retrains become costly (A6) |
| RAPTOR (Sarthi et al., 2024); GraphRAG (Edge et al., 2024) | Hierarchical summaries over a corpus for orientation and routing (A7) |
| Hippocampal indexing theory (Teyler and DiScenna, 1986); complementary learning systems (McClelland, McNaughton and O'Reilly, 1995) | The analogy behind A7: a fast index over a slow archive, with gist consolidated over time |
