# UPMS Architecture Manual, Review Candidate 6.3: Checking Annex (Slice 3, with deferred channel assessment)

3 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** part of review candidate 6.3, proposed D3 architecture; not accepted-current. Reviewed before Gate 3, not at Gate 0 (D-56). It replaces the 6.2 checking annex, which stays unchanged; revision 6.3 adds the concept-level rules of §5.9 (moved from the core) and the mathematical statement kinds of hook H4, and changes nothing else. Section and test numbers are those of the core, `UPMS_Architecture_Manual_Review_Candidate_6_3.md`, which leaves a stub at each moved section and whose terms, invariants and decisions govern this text.

### 5.7 Statement language

**A claim may carry structured statements: canonical concept IDs plus explicit qualifiers, derived from the source text and linked to the exact words they came from.** They let deterministic code query and compare before an LLM interprets. **Fixed (proposed).**

#### 5.7.1 Statement

```text
Statement {
  statement_id, claim_ref, kind     // state | event | generic | rule
                                   // | equation | inequality | identity | definition | assumption
                                   // | approximation | conditional | conjecture   (mathematics annex, H4)
  expressions[]?                    // mathematical expressions, for the H4 kinds
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
    modality:    asserted | quoted | reported | hypothesized | assumed
                 | defined | predicted | found | intended | committed
                 | preferred | normative            // the D1 set, §6.1
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


**Scope.** The tenant has a base vocabulary readable by all users. Each scope may extend it; a scope's concepts and definitions are scope content under §7.3, because a definition can disclose information. A concept curated from a scope's records lives in that scope; the base vocabulary accepts only concepts whose definitions and examples every user may read. Statements record the vocabulary version they were extracted with.

**Curated vocabulary is not meaning identity** (D1 F-27). Curating "Tc" as one concept does not assert that resistivity onset and Meissner onset are one quantity. Scientific equivalence is a meaning link (§5.5). A curator may mark a label **contested**: statements using it are then indexed under the label but compared only within the meaning each statement declares, and screening never joins their slots through the contested label.

**Measurement property type.** A property concept may declare itself a measurement: an estimand definition, a value type with unit dimension, an uncertainty type (standard uncertainty, interval or distribution reference) and the conditions that define the regime. The evidence–evidence channel (§9.7) uses it; a comparison model is D2 and is not part of this candidate (D1 §9).

**Governance.**

- Proposals are inert. When extraction meets an unknown term, it proposes a new concept or a mapping to the nearest existing one; the proposal takes effect only after curation by a holder of `curate` or `manage` on the vocabulary's scope, or by an accepted deterministic rule.
- Merges and splits are reversible, like entity `same_as`. Every merge re-screens the slots it joins (§9.7).
- Deprecation keeps recognition: a deprecated term remains an alias mapped through `replaced_by`, so old memories stay retrievable and comparable, while extraction and display prefer the current label. A term is removed only when no retained memory uses it.
- Every change produces a new vocabulary version; derived indexes record the version they were built with and rebuild when it changes.

**Initial vocabulary.** Project-work concepts only: tasks, decisions, components, configuration values, deadlines, people and roles, and events such as release, deploy and review. It grows by curated additions, not by agents minting properties freely.

**Expansion (adaptation tier A).** Indexes and queries expand terms with preferred labels and definitions, in every pilot language (§5.9): “HAS” is embedded as “HAS (Historical Applicability Set).” Off-the-shelf retrieval models then understand domain jargon immediately, deterministically and without training.

### 5.9 Natural languages: concept-level rules (moved from the core in revision 6.3)

The core's §5.9 keeps the record-level rules (original text is the record, names are not translated, retrieval across languages, translation is never authority, pilot languages). These rules apply once structured statements and the vocabulary exist. **Fixed (proposed).**

- **Concepts are language-neutral.** A concept has labels and definitions per language. Words that mean the same thing in different languages are labels of one concept, so statements, slots, rules, screening and hubs work across languages with no translation step: “production deploy” and “本番デプロイ” resolve to one event-type concept, and a no-Friday-deploy prohibition written in English screens an event recorded in German.
- **Equivalence is curated, not assumed.** Languages divide meaning differently: a word in one language may cover two concepts in another. A label joins a concept only through curation; model-proposed translations are inert proposals like any other (§5.8). Where meanings only overlap, the concepts stay separate and are linked by `close_match`, which never joins slots: a comparison across a close match gives at most a possible flag with the cue `cross_language_mapping`. A word curated as a label of a broader concept, because its language does not distinguish the narrower ones, is compared only at the broader level, and screened coverage reports those statements as compared at that level.
- **Values and formats.** Numbers, dates, times, units and currencies are parsed into typed values before comparison. A detected language is a model output, so it never decides a value alone: the plausible locales of a span are its detected language, the author's declared locale and any other language detected above the floor (§14.2). A value whose parse is the same under every plausible locale, or is written in an unambiguous canonical form, becomes a typed value; one whose parse differs (“1.000”) is stored as `ambiguous{candidate values}` (§5.7.4); a parse failure leaves the statement text-only. UPMS offers as canonical only the value parsed under the principal's declared locale or an unambiguous form, so that a front end or agent runtime that grounds or confirms an argument from memory uses and displays that canonical value (§7.2).
- **Rendering for readers.** Exact projections render concept labels in the reader's preferred language deterministically, falling back to another label with its language marked. Quotes are always shown in the original language; a translation may accompany a quote only as labeled synthesis (source class M) with its own ancestry. **Each scope's narrative is written once, in the scope's designated narrative language** (§14.2), so maintenance cost does not grow with the number of reader languages. A reader may request a translation of a narrative unit: it is labeled synthesis, depends on the unit, is withheld with it, and is charged to the reader's task budget, never to maintenance (§10.5.4).
- **Spoofing.** Labels, aliases and entity names are checked for confusable and mixed-script strings (Unicode UTS #39); a proposal that collides with an existing label across scripts is flagged to the curator, so a look-alike cannot capture a concept.

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

**Resolution and visibility.** Screening never resolves, refutes, supersedes or admits a claim, and the absence of a flag never certifies support, fidelity or currency. Every flag goes to investigation, whose result is an evidence-only Judgment (§5.3, §6.2); admitting a claim afterwards needs a separate assessment that does not read the flag or the investigation (§9.3). A flag is visible only to principals who can read both flagged items. Text-only statements are not slot-screened, and coverage says so. Required actions are not screened in the pilot, so an unfulfilled obligation is reported as unscreened coverage, never as “no flag”. Reversing a vocabulary merge restores the prior comparisons and retires flags that depended on the merge.


**Three consistency channels.** Slot screening above is the deterministic core of the evidence–evidence channel. The theory–evidence layer adds two more channels; all three **raise flags with cues for investigation; none resolves anything, and the absence of a flag certifies nothing** (TE-07, D1 F-25). **Fixed (proposed).**

| Channel | Deterministic checks | Model-proposed candidates | Limit |
| --- | --- | --- | --- |
| **Evidence–evidence** | Slot conflicts above. For a measurement property type (§5.8): unit and dimension mismatch, estimand-definition mismatch, and the cue `values_differ_no_comparison_model` | Cross-slot candidates (candidate channel above) | Noisy measurements are not conflicting values. A *statistical disagreement* exists only under a declared comparison model and decision rule, which is D2 and not in this candidate (D1 F-22, §9). Never called a logical contradiction |
| **Evidence–theory** | A typed `predicted` claim against a typed observation of the same estimand within the regime the prediction covers yields a `prediction_check` flag when the observation lies outside an exact value or stated interval; outside that regime a `not_covered` cue, unless the claim asserts invariance across regimes, in which case the regime difference is flagged as the test (D1 F-23) | Candidate bearings of new observations on live positions, recorded as `bears_on, unassessed` proposals | Whether a prediction failed is the assessor's judgment under a model |
| **Theory–theory** | Contradictory asserted statements in one slot; one symbol defined differently in one scope; unit and dimension errors in typed equations; **circular support** in the inferential graph; reliance on a refuted, retracted or superseded claim; a decision basis citing a route under review without a qualification | Candidate contradictions between natural-language arguments; missing premises | No general theorem prover (§17.3). Internal consistency of prose arguments stays mostly flagged for human review |

**Synthesis checks.** The same screening runs on statements extracted from synthesis: hub narratives (§10.5.3), overlay notes and claims marked `synthesis` (facilitator summaries). Beyond contradiction with exact projections, it flags an **omission** (the synthesis omits a live position or an unresolved or disputed objection that the exact projection of its subject shows) and a **characterization of a person's** reliability, competence or motives (§9.13). Either flag blocks a narrative's replacement and withholds an agent-written synthesis from overviews; a human's flagged summary is shown with the flag. **Both detectors are fallible cues** (SC-TE03): an omission need not contradict anything, a characterization can be oblique, and a false positive can flag legitimate criticism of a work, so a flag never withholds a human's text. No flag certifies faithfulness or the absence of a characterization. **What keeps dissent visible is construction, not detection:** every view that presents a claim, question or decision carries its deterministic mandatory list (§10.5.1), and no synthesis replaces that list.

**Theory guides evidence.** A front end may propose discriminating investigations: observations whose expected outcomes differ across live positions. These are recorded as claims with modality `hypothesized` or as recorded needs (coordination records), never as evidence.

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

**Adapters as derived indexes.** An adapter is versioned, records its training snapshot, and has ancestry edges on every record it was trained on, so deletion and lineage exclusion reach it. **Fixed (proposed):**

- **Per scope.** An adapter is a lossy compressed copy of its training text; only principals with `read` on its scope may use it, and a scope's adapter trains only on records homed in that scope. Cross-scope search queries each scope's index with its own adapter and merges ranked lists, never raw scores.
- **Training data** comes only from the curated vocabulary (aliases as positives, related-but-different concepts as hard negatives), user corrections and endorsements, and validated or confirmed extractions. Excluded: anything whose ancestry includes X-class content, or R-class content without a factual attestation or permitted-reliance endorsement (§6.4; a fidelity confirmation is not enough); unconfirmed model output; retrieval feedback; quarantined items; other scopes. This keeps known external lineage out of training. It cannot stop a misled curator from approving a planted term, which is why curation is attributed and reversible.
- **Retrain from scratch on trigger:** a change to a vocabulary concept in the adapter's training set, a threshold of newly approved aliases for concepts in its training set, a probe-accuracy drop, or a training-source deletion. Global consolidation (§10.5) retrains only adapters whose training inputs changed. Training uses pinned seed and versions.
- **Promotion gate.** Promote only if the adapter beats both the current adapter and the base model on the scope's probe set and a general regression set, with no regression beyond the preregistered margin; variants tried are recorded (§15.2).
- **Re-embedding.** Adaptation is query-side only in the pilot: document vectors come from the base embedding model and carry no adapter ancestry, so deleting an adapter's training source never blocks the vector index. Document-side adaptation needs its own dependency contract and a base-vector fallback index.
- **Deletion.** Deleting a training source blocks every adapter trained on it at the barrier. Serving falls back to the newest adapter whose snapshot predates the deleted record, or the base model, and a retrain from surviving data is queued (§14.2). Candidate 5's planned-expiry rule is removed: nothing expires (D-25), so routine retraining is driven only by vocabulary changes, approved aliases and probe-accuracy drops.
- **Evolving jargon.** Deprecated terms stay in training data as aliases of their replacements, so old memories remain understandable; only extraction output prefers current terms.
- **Archive.** Archived records stay eligible as training inputs only where they meet the training-data rule; archiving never forces a retrain.

### 9.12 Fact-checking

Fact-checking combines source tracing (from a claim to the events and spans it came from), quotation and extraction fidelity (the cited span says what the claim says), the three consistency channels and source assessments. **Its output is an evidential assessment with its basis, never a hidden edit.** A fact-check by an agent is an evidence-only judgment unless its ruleset admits it; a correction it suggests goes through §6.3.

### 9.13a Track record of non-person channels (deferred, D-45)

Not current text; kept for the slice that builds channel assessment.

**Track record** for a non-person channel is assembled only from later judgments whose assessor is not among the assessed claim's authors and whose basis is evidence independent of the channel; judgments whose basis is agreement with the prevailing position are excluded (D1 Definition 7.2, F-38). It is shown with its denominator and coverage: the channel's claims of that kind, how many were later assessed, and how they came to be assessed, since preferential checking of disfavored sources biases it. The assembly is a projection the assessor reads, not a score.

## Acceptance tests in this annex

| Case | Adversarial trajectory and required discriminator |
| --- | --- |
| T32 | “Sky is blue” and “sky is green” at overlapping times without places: a possible flag with `missing_qualifier(place)` and `entity_match_uncertain`; “blue” against “dark” raises no conflict flag, only a recorded `ComparisonCue` of kind `different_dimension` |
| T33 | A Friday release intention against a no-Friday-deploy prohibition: flagged without approval; not flagged with an authenticated in-scope approval record; still flagged, with `unverified_exception`, when approval is only claimed in text or is forged, expired, out of scope or only a statement attributed to the role holder; replay after the role is revoked gives identical flags |
| T34 | A deprecated term still retrieves and screens memories that use it; new extractions use the current label |
| T59 | With the pilot languages named at Gate 0 (for example English, Japanese and German): the same decision recorded in two of them resolves to one concept and one slot; a contradicting value recorded in a third raises a flag; each citation shows its original language |
| T61 | Two concepts linked only by close\_match never share a slot, and comparing them gives at most a possible flag with cross\_language\_mapping; a model-proposed translation stays inert until curated; a look-alike label in another script is flagged at proposal |
| T91 | Three channels: a typed prediction and an observation of the same estimand in its regime outside the stated interval give `prediction_check`; outside the regime `not_covered`, unless the claim asserts invariance, when the regime difference is flagged; two measurements that differ, with no comparison model, give only `values_differ_no_comparison_model`; one symbol defined twice in a scope, a unit error in a typed equation and reliance on a refuted claim are flagged |
| T92 | "Tc" curated as one concept with a contested label: resistivity-onset and Meissner-onset statements stay in separate slots and are never flagged against each other through the label; a meaning link of kind `equivalent_under` is needed to compare them, and it is attributed and contestable |
| T82 | A channel whose claims were later judged against the prevailing view, on agreement alone, and one judged on independent evidence: only the second enters its track record; disagreement with the current view never lowers an assessment |
