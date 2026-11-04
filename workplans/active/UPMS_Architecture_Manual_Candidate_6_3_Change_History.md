# UPMS Architecture Manual, Candidate 6.3: Change History

3 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** change history of review candidate 6.3, moved out of the manual by D-56. It records how the text came to be and the author's dispositions of earlier findings; it is not architecture and decides nothing. A.1 to A.9 are carried from candidate 6.1, where "this candidate" means candidate 6 or 6.1 as each heading says; A.10 and A.11 are carried from the 6.2 change history (SHA-256 `a20ecbdd33a3e2e4d858f2cce8b281a8c3cb7edf143597c101db9b9dec2a0b31`), unchanged; A.12 and A.13 are new.

## Change map

**Every candidate 5 section, every proposal section that bears on the architecture, and every re-review finding the proposal maps has a stated place here.** "Copied" means the candidate 5 text is carried verbatim; "edited" means carried with the named changes; "rewritten" means replaced. Candidate 5 is unchanged (SHA-256 `406cf3b4…`).

### A.1 Candidate 5 → candidate 6, by section

| Candidate 5 | Disposition | Candidate 6 |
| --- | --- | --- |
| §1 status, inputs | Rewritten: new inputs, D1 parent, review boundary | §1, §1.1 |
| §1.2 product boundary | Edited: scientific-inquiry journeys added; action safety moved to the agent runtime; SCIRE and SSDS boundaries | §1.2 |
| §1.3 acceptance boundary | Edited: joint review of proposal, D1 and candidate 6 | §1.3 |
| §1.4 domain | Rewritten: D1 parent required (triggers 1 and 4 fire); D2 conditions; custody home | §1.4 |
| §2 terms | Rewritten: four rights; theory terms; publication → sharing; release segment → release record; dependency, requirement closure, handle, release, elevation and restriction epoch removed or narrowed | §2 |
| §3 at a glance | Rewritten: front end, projection service, no runtime adapter | §3 |
| §4.1 components | Edited: runtime adapter → capture and session adapter; projection service; sealed attribution in the core | §4.1 |
| §4.2 external contracts | Edited: action safety, processor policy, SCIRE, SSDS | §4.2 |
| §4.3 operations | Rewritten for four rights and theory operations; `publish`, `confirm_publication`, `elevate`, `prepare_dispatch`, `record_dispatch_outcome` retired | §4.3 |
| — | New: front-end contract | §4.4 |
| §5 common fields | Edited: retention deadline and requirement closure removed; archive state and sealing added | §5 |
| §5.1 Event | Edited: transmitter as front end; external reference; observation semantics | §5.1 |
| §5.2 Claim | Rewritten: D1 modality set, conditions, regime, time scope, acts, synthesis, subject kind | §5.2 |
| §5.3 Judgment | Edited: kinds, conditioned status values, judgment basis (proposed) | §5.3 |
| §5.4 controls and processing | Edited: decision fields on coordination records; publication removed; sealing, archive and deletion markers added; publication paragraph of coordination records removed | §5.4 |
| §5.5 relations, ancestry, requirement closure | Rewritten: relation families of proposal §4; ancestry never access | §5.5 |
| §5.6 identity, time, scope | Edited: last sentence (inherited restrictions) replaced by time scope | §5.6 |
| §5.7 statement language | Copied; modality list in qualifiers widened (change history A.7) | §5.7 |
| §5.8 vocabulary | Copied except the Scope paragraph (requirement closure removed); vocabulary-is-not-meaning and measurement property types added | §5.8 |
| §5.9 natural languages | Copied; grounding sentence edited (change history A.7) | §5.9 |
| — | New: Question, Objection, Review obligation | §5.10–§5.12 |
| §6.1 modality projections | Edited: D1 modalities added; modality survival rule | §6.1 |
| §6.2–§6.6 | Copied; right names edited | §6.2–§6.6 |
| §6.7 permissions and elevation | Rewritten: administrator mode; no fence for narrowing | §6.7 |
| §6.8 publication | Rewritten as sharing | §6.8 |
| §6.9 coordination records | Edited: first paragraph copied; publication paragraph replaced by decision rendering and integrity checks | §6.9 |
| — | New: objections, review obligations, archive lifecycles | §6.10–§6.12 |
| §7.1 source classes | Copied | §7.1 |
| §7.2 consequence classes and grounding | **Retired from the core** (D-24); what a runtime needs from memory stays | §7.2 |
| §7.3 access control | Rewritten for four rights (D-28); requirement closure, D-6 and elevation removed; D-9 cap kept as pending | §7.3 |
| §7.4 confidentiality and purpose | Rewritten: tags narrow only the record; processor eligibility; declassification paragraph moot | §7.4 |
| §7.5–§7.6 | Copied; "published team items" → "shared items" | §7.5–§7.6 |
| §7.7 threat model | Rewritten proportionately; truth-robustness table (proposal §8.3); operator residual | §7.7 |
| — | New: sealed attribution and anonymous-review back end; strict profile (deferred) | §7.8, §7.9 |
| §8.1 two profiles | Rewritten: the instrumented runtime is outside UPMS | §8.1 |
| §8.2 conservative propagation, release segments | Rewritten: release records as provenance; propagation kept only for UPMS model calls (§8.4) | §8.2, §8.4 |
| §8.3 handles and reset | **Retired** (D-24) | §8.3 (heading kept) |
| §8.4 checked dispatch | **Retired** for agent actions; manifest-before-submission kept for UPMS workers | §8.4 |
| §8.5 egress | Edited: UPMS workers and views | §8.5 |
| §8.6 resources | Edited: traversal budgets; no expiry | §8.6 |
| §9.1–§9.3 | Copied; §9.3's judgment-on-judgment sentence points to §9.10 | §9.1–§9.3 |
| §9.4 barriers | Rewritten: deletion, correction, quarantine only | §9.4 |
| §9.5–§9.6 | Copied | §9.5–§9.6 |
| §9.7 screening | Copied; three channels, synthesis checks and "theory guides evidence" added | §9.7 |
| §9.8 processing cascade | Copied to the re-embedding rule; per-scope access and deletion bullets edited; expiry planning removed | §9.8 |
| — | New: standing projection, judgment bases (proposed), impact traversal, fact-checking, source assessment, SSDS references | §9.9–§9.14 |
| §10.1–§10.2 | Copied with right names; theory routes and archive rule added | §10.1–§10.2 |
| §10.3 response contract | Rewritten: modality, act state, standing, objections, archive state, traversal coverage | §10.3 |
| §10.4 context assembly | Copied; last sentence edited | §10.4 |
| §10.5 intro and figure | Copied; figure's L2 line edited | §10.5 |
| §10.5.1–§10.5.4 | Rewritten: question pages, understanding section; deadline machinery removed | §10.5.1–§10.5.4 |
| §10.5.5 | Copied except the continuity warning, removed | §10.5.5 |
| §10.6 intro | Edited: publication → sharing; team policies to Slice 4 | §10.6 |
| §10.6.1 | Copied | §10.6.1 |
| §10.6.2–§10.6.3 | Rewritten as sharing and sharing categories | §10.6.2–§10.6.3 |
| §10.6.4–§10.6.6 | Copied with small edits; review packages added | §10.6.4–§10.6.6 |
| §11 accountability | Reconciled (A.3) | §11 |
| §12 retention and deletion | Reconciled (A.3) | §12 |
| §13 failure | Reconciled (A.3) | §13 |
| §14.1 runtime choices | Edited: instrumented integration leaves; SCIRE integration | §14.1 |
| §14.2 pilot defaults | Edited: every retention row removed; elevation and fence rows simplified; theory rows added | §14.2 |
| §14.3 storage | Edited: sealed store; traversal over relation tables | §14.3 |
| §15 invariants and tests | Reconciled (A.3, A.4) | §15 |
| §16 slices | Re-planned (D-30, proposal §14) | §16 |
| §17 delegation, inspection, reopen | Edited: new non-goals, beyond-deliverable surfaces, reopen triggers | §17 |
| §18 readiness and decisions | Rewritten: D-1 to D-36 status, challenges | §18 |
| Appendix A review lineage (A.1–A.7) | Not repeated; it stays in candidate 5 and remains the lineage of the retained text | — |
| Appendix B sources | Not repeated; candidate 5 Appendix B stays the source list for retained claims about Codex and hippocampal indexing | Appendix B here |

### A.2 Proposal → candidate 6

| Proposal | Candidate 6 | Note |
| --- | --- | --- |
| §1–§2 | §1, §3 | |
| §3.1 Event, observation | §5.1 | |
| §3.2 claims, modality, acts | §5.2, §6.1 | D1 Definitions 2.2–2.3 |
| §3.3 Question | §5.10 | `linked_questions` added (SCIRE v0.4 §5.3 "link") |
| §3.4 Objection | §5.11, §6.10 | Homing rule added (C6-4); `resolution` as target |
| §3.5 Decision | §5.4, §6.9 | Kind `resolution` added (C6-10); integrity checks (C6-11); rendering (C6-9) |
| §3.6 Judgment | §5.3 | |
| §4 relations | §5.5 | Identity family (`same_as`) kept from candidate 5 |
| §5 evidence semantics | D1 §5; §5.5, §9.9, §9.11, §9.14 | |
| §6.1 standing; judgment on judgment | D1 §6; §9.9, §9.10 | Item 6 carried as Proposed (open) |
| §6.2 three channels | §9.7 | Statistical disagreement deferred to D2 (D1 §9) |
| §6.3 fact-checking | §9.12 | |
| §6.4 source assessment | D1 §7; §9.13 | Identity relations (D1-F1) |
| §7, §7.1 front end; facilitation; anonymous review | §4.4, §7.8 | Process stays SCIRE's; back end only; SC-62 |
| §8.1 what stays | §7.1, §7.3, §7.4, §7.7, §10.4 | |
| §8.2 what leaves | §7.2, §7.3.5, §6.7, §8.3–§8.4, §11, §12.4 | Quarantine kept under the fence (C6-8) |
| §8.3 truth-based robustness | §7.7 | |
| §9 retention | §12 | C6-2, C6-3, C6-5, SC-61 |
| §10 SSDS | §9.14; borrowed mechanisms in D1 §12 | |
| §11 overview | §10.5 | |
| §12 invariants TE-01–TE-15 | §15 | Kept as invariant IDs |
| §13.1 capability transfer from SCIRE | §4.4, §5, §9, §10.5 | |
| §13.2 re-review findings | A.5 | |
| §13.3 candidate 5 disposition | A.1, A.3 | The rows for §§11–13 and §15 are completed here |
| §14 sequencing | §16 | Anonymous review placed in Slice 3 (C6-7) |
| §15 owner decisions | §18.2 | |
| §16 inspectability | §17.2; D1 §11 | |
| §17 risks | §7.7, §17.4, §18.3 | |

### A.3 Reconciliation of candidate 5 §§11, 12, 13 and 15 with D-24 and D-25

The proposal's author had not read these sections in full (proposal Appendix A); its §13.3 gave one line for each. Each clause is reconciled here.

**§11 Accountability and inspection records**

| Candidate 5 clause | Disposition | Reason |
| --- | --- | --- |
| §11 lead: the instrumented runtime seals every invocation | Rewritten | D-24: action mediation leaves the core |
| §11.1 `InvocationManifest`, `InvocationOutcome` | Retired for agent runtimes; kept for UPMS workers as processing records with committed input manifests (§11.1, §8.4); runtime manifests accepted as external-reference events | Memory does not execute actions; UPMS still needs to know what its own models saw, for provenance and independence |
| §11.1 manifests as evidence for independence attestations | Narrowed to UPMS-assembled context (§10.6.4) | Coverage stated honestly |
| §11.2 skeleton and rendered fragments split | Retired | It existed to give operational records separate retention deadlines |
| §11.2 reconstruction deadline, pinned windows, seven-day rendered context | Retired | D-25 |
| §11.2 representation expiry versus semantic-object expiry | Kept as representation versus record, for space deletion (§11.2, §12.1) | The distinction still decides what "delete suggested" may offer |
| §11.2 ancestry kept while descendants survive; purged nodes keep opaque edges; stripped node fails closed | Kept (§11.2, H1) | Provenance is the basis of impact and independence |
| §11.2 deletion status reports surviving descendants and their deadlines | Edited: surviving descendants, no deadlines | D-25 |
| §11.3 incident recall | Kept and merged with impact traversal (§9.11, §11.3) | One traversal for scientific and security causes |
| §11.4 access records committed to a replicated control plane before release | Edited: committed in the canonical store before release | D-24 (simple logged administrator access) |
| §11.4 owner notice for elevated reads (D-1) | Simplified: owners see access records | D-1 simplified |
| §11.4 protected audit retention, minimum one year, fixed maximum (D-13) | Retired; replaced by "persist until an authorized explicit deletion the named principal cannot make" | D-25; D-13 moot |
| — | New §11.5 anonymous-review records | D-33 to D-36 |

**§12 Retention, redaction, deletion and portability**

| Candidate 5 clause | Disposition | Reason |
| --- | --- | --- |
| §12 lead: staged lifecycle with barrier, purge, completion | Kept, simplified (§12.4) | Honest deletion |
| §12.1 deletion units and surfaces | Kept; question pages and review packages added; backups reported rather than purged (§12.3) | |
| §12.1 who may delete: `w` own, `d` others, administrators, retention policy | Edited: `write` own, `curate` others with the SC-61 marker, administrator on verified external request; retention policy removed | D-28, D-25 |
| §12.1 propagation along restrictive requirements to descendants in unseen scopes | Rewritten: UPMS-derived representations purged; authored descendants keep content, get `input_deleted` obligations; erasures create deletion obligations (§12.3) | D-6 superseded under D-24; C6-5 |
| §12.1 published copies and their retention | Moot; sharing copies are listed in the preview | D-12 moot |
| §12.1 retention as versioned policy, deadlines, renewal, retention changes with delay | Retired; bulk-deletion delay kept (§7.3.6) | D-25 |
| §12.2 redaction as copy-and-erase | Kept (§12.5) | |
| §12.2 redaction keeps the original's retention deadline | Retired | No deadlines |
| §12.2 redaction never declassifies | Kept: the copy stays in the original's scope with its tags | |
| §12.3 deletion lifecycle states | Edited: `purged_live` and `complete` replace `complete_within_scope`; preview added to `requested` (§12.4) | Honest deletion |
| §12.3 subject erasure needs discovery and a coverage statement | Kept | |
| §12.4 per-unit cryptographic erasure and wrapper caveats | Retired; not claimed | D-24 (proportionate) |
| §12.4 encrypted backups with short expiry; completion waits for backup expiry | Kept as infrastructure rotation; reported, never a memory retention rule | Backups are not memory records |
| §12.4 separately durable recovery control plane for deletion, revocation, permission history and access records | Reduced to a separately backed-up tombstone log that a restore must apply first (§12.4) | Restore must not resurrect; the rest is sized for an operational tenant |
| §12.5 minimal audit, tombstones, honest erasure claims | Kept (§12.4 honest claims); deletion markers added | |
| §12.5 provider retention evidence, processor category bans by retention | Edited: processor eligibility per scope (§7.4) | No retention categories |
| §12.6 import, export | Copied (§12.6); sealed attribution never exported | |
| — | New §12.1 retention recommendations, §12.2 archive and liveness | D-25, D-29 |

**§13 Failure behavior**

| Candidate 5 row | Disposition |
| --- | --- |
| Capture or payload cannot commit; model unavailable; index stale; permission unknown; KMS unavailable; owner failover; outbox duplicate; vocabulary unavailable; consolidation fails; consolidation fails screening; adapter blocked; ancestry cycle; unsupported schema; storage exhausted | Kept, wording adjusted (storage exhaustion never deletes records) |
| Identity provider unavailable: "no consequential release" | Edited: reads within the cache bound; consequential release is the runtime's |
| Policy decision or revocation status unknown | Replaced by processor eligibility unknown |
| Source application unavailable | Kept; SSDS added (D-E) |
| Manifest or dispatch journal commit fails | Retired for agent actions; replaced by "release record cannot commit" and "UPMS model submission uncertain" |
| Tool or provider result uncertain | Narrowed to UPMS model submissions |
| Restriction fence cannot finish | Kept for deletion, correction and quarantine barriers |
| Purge or backup expiry fails | Edited: `purge_failed` or `purged_live` with backups listed |
| Unsupported schema or stale restore controls | Edited: restore without the tombstone log stays closed |
| — | New rows: standing traversal limit; impact traversal pending; liveness check; synthesis screening; sealed store; agent chair |

**§15 Invariants and acceptance evidence**

| Candidate 5 item | Disposition (identity map in A.4) |
| --- | --- |
| H1, H2, E1, E2, A1, A2, AC5, AC6, P1, F3, ST1, ST2, VO1, SC1, OV1–OV3, OV5, OV6, C2, R1, D1, D3, O1–O4, O6, M1, CO1 | Kept; wording adjusted where rights, retention, sealing or new projections touch them |
| E3 | Kept; extended by the judgment-basis contract if accepted (§9.10) |
| A3 | Edited: action-grounding clause removed; interpretation confirmation added |
| AC1 | Edited: requirement closure removed |
| AC2 | Edited: no fence for permission narrowing |
| AC3 | Edited: four rights |
| AC4 | Edited: administrator mode; replicated plane and retention bounds removed |
| AC7 | Edited: own-record entitlement no longer conditioned on all-owned ancestry |
| F1 | Edited: provenance survival, with conservative propagation for UPMS models only |
| F5 | Edited: release records as provenance, never access |
| TM1 | Rewritten for sharing |
| TM2 | Edited: review packages; UPMS-assembled context |
| AD1 | Edited: per-scope access without closure |
| OV4 | Edited: deadline planning removed |
| C1 | Edited: UPMS model invocations |
| D2 | Edited: live surfaces and backups awaiting rotation |
| ML1 | Edited: grounding clause moved to the runtime |
| F2, F4, C3, O5 | Retired (D-24) |
| — | New: DL1, AR1, DC1, SE1, TE-01 to TE-15 |
| §15.1 T01–T64 | Kept, edited or retired as in A.4; T65–T103 added |
| §15.2 evaluation protocol | Kept; theory-layer studies E1, E2, E4, E5 added; confirmation-burden threshold and Slice 1b clause removed with D-24 |

### A.4 Invariant and test identity map

**Invariants.** Kept unchanged in substance: H2, E1, E2, A1, A2, AC5, AC6, P1, F3, ST1, ST2, SC1, OV1, OV2, OV3, OV5, OV6, C2, R1, D1, D3, O1–O4, O6, M1, CO1. Edited: H1, E3, A3, AC1–AC4, AC7, F1, F5, TM1, TM2, VO1, AD1, OV4, C1, D2, ML1. Retired: F2, F4, C3, O5. New: DL1, AR1, DC1, SE1, MV1, TE-01–TE-15.

**Tests.**
- **Copied verbatim:** T01, T02, T10, T11, T14–T17, T19, T23, T25, T28, T31–T34, T36–T42, T46, T55–T61, T64 (with the right-name and slice-name edits of A.7).
- **Rewritten under the same identity:** T03, T04, T13, T20, T21, T22 (inverted), T24, T26, T27, T30, T35, T43, T44, T45, T49, T50, T51, T54, T62 (part (a) only), T63.
- **Retired:** T05–T09, T12, T18, T29, T47, T48, T52, T53, T62 part (b).
- **New:** T65–T103 (T98–T103 from the Codex review's proposed contract checks).

### A.5 SCIRE v0.4 re-review findings (proposal §13.2)

| Finding | Proposal mapping | Disposition here |
| --- | --- | --- |
| SC-41 resolution by assessment | Front end, with a back-end fix | Back end: `resolution` decisions (§5.4, §6.9), disputed resolutions travel, self-resolution labeled (D1 F-3 to F-5, T67). Whether self-resolution is permitted: SCIRE |
| SC-42 hidden applicable objections | Needs a uniform rule only in the strict profile | Default profile: objection homing (§5.11, C6-4, T90). Strict profile: returns with §7.9 |
| SC-43 unknown lineage | Dissolves with the boundary and D-24 | Dissolved: a note is the writer's responsibility (§7.3.5); release records record what UPMS released |
| V4-04 basis statement in SCIRE-11 | Front end | SCIRE |
| V4-05 closed list of consequential uses | Front end | SCIRE; the back end's integrity checks (§6.9) apply to every decision kind and are not consequential-use policy |
| V4-06 applicability coverage | Front end | Back-end default one hop from cited basis (D1 F-6, §9.9); SCIRE may widen |
| V4-07 review-obligation closure | UPMS | Closed only by reassessment (§5.12, §6.11, T74) |
| V4-08 trusted-producer empty set | Dissolves | Dissolved; release records cover only UPMS releases and say so (§8.1) |
| V4-09 over-restriction | Dissolves (E3 only for the strict profile) | Two-sided limits for studies (§15.2) |
| V4-10 reviewed intervals | Front end | SCIRE |
| V4-11 triggers before reliance | Front end | SCIRE; occurrence time recorded (§5.1) |
| V4-12 dropped v0.3 properties | UPMS | (i) status vocabulary restored (§5.3); (ii) uninstrumented upgrade rule restored (D1 F-17, §6.9); (iii) de-attribution: open (§18.2, C6-12); (iv) where an argument may stop: open (D1-F4) |
| V4-13 snapshot currency | UPMS | §9.14, D1 F-18, T80 |
| V4-14 materiality and overlap judgments | Front end | SCIRE |
| V4-15 one enumeration | UPMS | Origin, qualification and usability enumerations owned by D1 Definition 2.9; execution outcome remains the ProcessingRecord enumeration; investigation outcomes are question outcomes |
| V4-16 duplicated rules | Dissolves | Dissolved: one owner |
| V4-17 cross-system dependence | Dissolves | Dissolved for UPMS and SCIRE; SSDS links per §9.14 |
| V4-18 undefined manifest | Not mapped | Moot: the disclosure-review manifest belonged to SCIRE's dropped §9.2 confidentiality rules |
| V4-19 cost of new mechanisms | Front end | E4 cost measures (§15.2) |
| V4-20 joint signatures, retention revocation, incomplete history | Not mapped | (a) §6.9 check 5; (b) moot without retention permissions; (c) TE-09 discloses deletion gaps |

### A.6 Where this candidate departs from the proposal

Each departure is listed in §18.3 with its reason: SC-61 (deletion marker), SC-62 (sealing of anonymous-role records), C6-2 (recency), C6-3 (irrelevance), C6-4 (objection homing), C6-5 (erasure obligations), C6-7 (slice of anonymous review), C6-8 (quarantine fence), C6-9 (decision rendering), C6-10 (`resolution` kind), C6-11 (integrity checks), C6-14 (first-product boundary). Departures that follow the Codex review are in A.8. The D1-level departures are D1-F1 to D1-F5. Nothing else in the proposal is changed; where the proposal is silent, this candidate keeps candidate 5.

### A.7 Edits inside copied candidate 5 text

The copied blocks are verbatim except: right names (`l`, `r`, `w`, `c`, `d`, `m` → `read`, `write`, `curate`, `manage`); the statement qualifiers' modality list (§5.7.1) widened to the D1 set; the base-vocabulary curation paragraph (§5.8) replaced; §5.9's grounding sentence; §6.5's activation right; §7.6's "published" → "shared"; §9.3's last sentence on judgment on judgment; §9.8's per-scope access bullet; §10.1's right names and epochs; §10.2's recall row; §10.4's last sentence; §10.5's figure line for L2; §10.6.4's attestation coverage; §10.6.5's "restriction commit"; §10.6.6's slice number; §9.6's reconstruction row (expiry removed); §9.8's adapter-ancestry sentence; §10.5.5's "cannot list" and hub-age wording; §10.6.4's "published copy" and requirement-closure clause; T23's elevation wording; T28 and T58's right names; T46's slice number.

### A.8 Codex review of the proposal: status of each finding in this candidate

The author's assessment only. "Repaired" means this candidate's body text contains a repair the author believes defeats the review's trajectory; the review's own rule is that a finding closes only when an independent check of the operative text agrees.

| Finding | Status here | Where |
| --- | --- | --- |
| SC-TE01 / TE-R01 judgment-basis currentness and cycles | Repaired in the standing projection (premises only through effective judgments; negative information; acyclic support); the judgment-basis contract follows the review's §4 and **stays open** for the owner. **Candidate 6 overstated this:** `content` entries admitted without going stale; fixed in 6.1 (C61-1) | §9.9, §9.10, D1 §6.1, §6.5; T94, T98 |
| SC-TE02 / TE-R02 sealed chair against D-9 and operators | Partly repaired: the chair is a confined service role, identities never reach its model, metadata paths are sealed, recovery and replacement stated; the operator residual is **open** for the owner. **Candidate 6 missed** the overseer of an assisting agent; fixed in 6.1 (C61-6) | §7.3.1, §7.8, §7.7; C6-1, SC-62; T86, T101 |
| SC-TE03 / TE-R03 screening as a guarantee | Repaired: mandatory deterministic lists carry dissent; omission and characterization detectors are fallible cues | §9.7, §10.5.1, MV1, OV6; T93 |
| SC-TE04 / TE-R04 D-36's boundary | Narrow reading applied provisionally; **owner decision** | §4.4, §5.11, D1 F-8; T99 |
| SC-TE05 / TE-R05 decisions current without authority or concurrency contract | Repaired: reported, recorded and validated statuses; atomic expected-revision and signature checks; only validated decisions make a position current. **Candidate 6 overstated this:** no policy-owner binding; fixed in 6.1 (C61-2) | §5.4, §6.9, DC1; T100 |
| TE-R06 confidentiality claim | Repaired as a statement of the weaker guarantee; first-product boundary is an **owner decision** | §1.2, §7.3.5; C6-14 |
| TE-R07 lineage completeness; masking versus rationale exclusion | Repaired: coverage gaps declared; review packages mask identity and exclude only other reasoning lineage | §8.1, §7.8, §10.6.4 |
| TE-R08 archive hides dissent | Repaired: liveness predicate; mandatory traversal ignores archive state | §12.2, §10.5.1; T83, T103 |
| TE-R09 deletion after removing requirement closure | Repaired: derived versus authored descendants, erasure obligations, restore-safe tombstones; propagation default is an **owner decision** | §12.3, §12.4; C6-5; T84 |
| TE-R10 judgment targets; uncovered dependencies | Repaired: typed targets; relations carry no assessment status; traversal covers cited definitions, models, calibrations and conditions | §5.3, §5.5, §9.11 |
| TE-R11 generic propagation; definition recursion | Partly repaired: condition compatibility, definition recursion distinct from support cycles, no aggregation of ordinal support; type-specific propagation beyond this is **open** | §9.9, D1 §6.1 |
| TE-R12 person proxies through channels; biased track record | Repaired: channels must be technical mechanisms; track record shows denominator and coverage | §9.13, D1 F-41 |
| TE-R13 count differencing; identity assurance | **Not repaired in candidate 6:** pseudonyms revealed the count, signing unmasked every record under a pseudonym, and independence and conflict results still depended on sealed attribution. Repaired in 6.1 (C61-3 to C61-5) | §7.8; T101 |
| TE-R14 chair governance gaps | Repaired: later conflicts, replacement, pending appeals, appeal self-identification warning | §7.8; T101 |
| TE-R15 truth-robustness overclaim | Repaired: bounded wording | §7.7 |
| TE-R16 growth without deletion | Repaired: quotas, refusal before acknowledgement, owner capacity choices | §8.6, §12.1 |
| TE-R17 incomplete capability transfer | Repaired for candidate 5 §§11–13 and 15 (A.3) and the re-review rows (A.5); V4-12 (iii) and (iv) **open** | A.3, A.5, §18.2 |
| TE-R18 Slice 2 before retraction propagation | Repaired: all impact traversal and validated decisions in Slice 2; anonymity unavailable until Slice 3 | §16 |
| TE-R19 experiments | Partly repaired: contract checks precede studies; E5 narrowed; persisted-narrative go/no-go restored; T98–T103 added. Two-sided E3 applies only if the strict profile is built | §15.1, §15.2 |
| TE-R20 history after deletion | Repaired: deletion gaps disclosed; exposure is what was released, not what was read | §9.9, §6.9 |
| Transfer audit: SC-42 "does not generally dissolve" | Partly repaired: objection homing removes the within-project case; personal scopes and permission changes still let a decider see less, which the standing report's coverage states; existence-independent qualification of decisions on partial coverage is **open** for the strict profile | §5.11, §9.9, §7.9 |
| Transfer audit: V4-15 one enumeration | Not repaired beyond A.5; a versioned exchange vocabulary with SSDS mappings is **open** | A.5 |
| Transfer audit: V4-16 one owner per meaning | Repaired for under-review eligibility (route status in §9.9 is its only owner) | §9.9 |
| Transfer audit: S §5.4 kinds of assessment | Repaired in D1: standing never merges plausibility, validity, adequacy, probability and participant judgment | D1 F-28 |
| Transfer audit: imported records keep origin "until assessed" | Clarified: assessment changes usability or admission, never the historical source class | §12.6 |

### A.9 Candidate 6 → candidate 6.1

Candidate 6 (SHA-256 `1b125d2c…`) is unchanged. Every other byte of this revision is candidate 6's.

| Where | Change | Finding or request |
| --- | --- | --- |
| Title, §1, §1.1, §1.4 | Revision 6.1; D1 parent is candidate 1.1; candidate 6 added as predecessor input | — |
| §1.2 | Creator's attestation of the first-product boundary, recommended | C6-14, owner request |
| §5.4 | De-attribution requests added to the controls | C6-12 |
| §6.9, §7.3.3 | Decision-policy owner in scope configuration; re-evaluation is a new revision | C61-2 |
| §6.10 | Signing attributes every record under the pseudonym | C61-4 |
| §7.7 | Anonymity row of the threat table: pseudonyms and independence instead of "one sealed author counts once" | C61-5 |
| §7.8 | Independence accounting removed from sealed uses; sealed conflict shows as decline; release principle replaces the count rule; who may assist; personal-scope drafts disclosed; all-or-nothing signing; custody recommendation | C61-3 to C61-6, C6-1 |
| §9.10 | Only `current` entries count; deferral recommended | C61-1, §15 item 6 |
| §9.13 | Same sealed author only for conflict checks; channel assessment deferred to Slice 4 | C61-5, C61-7 |
| §12.3 | Erasure recommendation; de-attribution of derived representations | C6-5, C6-12 |
| §15 | DC1, SE1, TE-15, T86, T94, T100, T101 edited; T104 to T107 added | C61-1 to C61-6, C6-12 |
| §16 | T107 in 1a-team; works only and T104–T106 in Slice 3; channel assessment and T82 in Slice 4 | C61-7 |
| §18.2, §18.3 | Author's recommendation on every open item; C61-1 to C61-7 added; C6-12 and the de-attribution row now proposed | Owner request |
| A.8 | Four statuses corrected (SC-TE01, SC-TE02, SC-TE05, TE-R13) | Re-reading against the body text |
| Appendix B | Revision coverage and anchoring | — |

### A.10 Candidate 6.1 → candidate 6.2

Candidate 6.1 (SHA-256 `d9246151…`) is unchanged. The core, the two annexes and this file together hold every byte of 6.1 except the changes below.

| Where | Change | Finding or decision |
| --- | --- | --- |
| §1 | Revision 6.2; D1 parent 1.2; 6.1, the same-family review and the owner decision record as inputs; the file split explained | D-56 |
| §1.2 | Attestation decided | D-43 |
| §4.3, §4.4 | Appointment bound to the front end that opened the review; no refusal for an objection's existence | D-50, D-52 |
| §5.3, §5.4 | `judgment_basis[]` removed; `applicable_at_decision` replaced by a derived set, `late_objections[]`, `applicable_position` and `signature_state`; manifest fields restored | D-39, R-08, D-50, D-51, A.3 check U5 |
| §5.11, §6.10 | Objections carried on revision; rebind; `superseded` narrowed; D-37, D-38 folded in; sealed lifecycle acts | D-47, D-37, D-38, SC-R3 |
| §6.9 | Late-objection delta; awaiting and complete signatures; attested change of policy owner; front-end registration as an operator act; check 3 a label; derived applicable set; `reported` and `recorded` kept apart | D-50 to D-52, R-07, R-08 |
| §7.4 | UPMS-derived representations carry the union of their inputs' tags | A.3 check U9 |
| §7.6, §9.3, §9.9, §14.2 | Scientific effectiveness separate from project-memory freshness; inquiry ruleset; new route statuses; endpoints; per-derivation circularity; projection version pinned | D-48, SC-R2, R-01 to R-03 |
| §7.8 (now in the anonymous-review annex) | Distinct session type, placement, sealed edges, pseudonym assignment, role-only lifecycle acts, review budget; temporary-session assistance only; critic-side conflicts and decline timing; D-40 folded in | D-49, SC-R3, R-09, R-11 |
| §8.2 | Anonymous-role releases never become ancestry of other writes | D-49 |
| §9.10 | Replaced by a pointer to candidate 6.1 §9.10 | D-39, R-20 |
| §9.11 | Sealed-authored dependents assigned to the pseudonym | SC-R3 |
| §9.13 | Author search without assessment values; `subject_kind` as partly a norm; track record moved to the checking annex | D-55, R-17, R-18, D-45 |
| §10.5 | "Archive" corpus renamed "Canonical records" | R-19 h |
| §11.4 | Access records in the recovery log; deleted only through §11.4 | D-53, A.3 check U11 |
| §11.5 (now in the anonymous-review annex) | Participant-visible fields enumerated per record type | R-12 |
| §12.3 | Uniform preview line; sealed self-deletion only from the anonymous role; D-41 folded in; "or nothing" restricted; de-attribution exemptions | R-13, R-15, R-16, D-41, D-54 |
| §12.4 | Recovery log for every restrictive or sealing control, with monotone authenticated positions and a consistent sealed-store point; backup service never serves; honest-claim and purge-controller sentences restored; payload-free survivors | D-53, A.3 check U1 to U4, M2 to M6 |
| §12.5 | Redaction as erasure; event-level deletion includes replacements | A.3 check U12, M1 |
| §13 | Endorsement and manifest rows; traversal limit at use; missed purge target; capacity for every restrictive control | A.3 check U6, U10, M6 to M8 |
| §15 | DC1, SE1 (TE-15 merged), AC1, A3, AC4, AD1, OV2 edited; DL2 added; E3 and T03, T13, T20, T27, T43, T51, T69, T75, T78, T81, T88, T100, T107 edited; T94 retired; T108 to T112 added; T01–T112 range | Above |
| §16 | Slice lists: T03 split; T70 and T99 to Slice 3; T108, T109 to Slice 2; T111, T112 to 1a-core; inquiry ruleset; Gate 0 review scope | R-19 c, d, D-56 |
| §17.2 | Decision status, markers and anonymous-review fields marked beyond the deliverable | R-19 m |
| §18 | Decisions folded in; D-37 to D-56 rows; C62-1 to C62-12 | — |
| Moves | §7.8, §11.5 and their tests to the anonymous-review annex; §5.7, §5.8, §9.7, §9.8, §9.12, the track-record paragraph, T82 and their tests to the checking annex; Appendix A.1 to A.9 to this file | D-56 |

### A.11 Same-family check of A.3 against candidate 5 (3 November 2026)

**Asserter:** a fresh Claude Opus 5.5 agent context launched by the author; read-only; same family, so not independent. It read candidate 5 §§11–13 and 15 in full, and 6.1's A.3, A.4, A.7 to A.9 and the sections they cite; it did not read candidate 5 §§1–10, 14 and 16–18, 6.1 §§1–6 beyond those cited, or the D1 text. It found that A.3 and A.4 account for all 43 invariants, 64 tests and 21 §13 rows of candidate 5, and that the defects are below item level.

| ID | Kind | Finding (candidate 5 → 6.1) | Disposition in 6.2 |
| --- | --- | --- | --- |
| U1 | Unsound | Recovery control plane reduced to deletion tombstones; revocations, access records and markers lost on restore | Repaired: recovery log (§12.4, D-53, T13) |
| U2 | Unsound | Quarantines, corrections, tags, eligibility narrowing, obligations, de-attribution, blocks, transfers and sealing records had no restore rule; sealed store could restore out of step | Repaired: in the recovery log; consistent restore point (§12.4, T13) |
| U3 | Unsound | No proof the log is the latest; `serving_blocked` not tied to durability in the log | Repaired (§12.4) |
| U4 | Unsound | Candidate 5's no-payload rule for records that outlive deletion was dropped; A.3 said C3 retired with D-24 | Repaired: DL2, §12.4, T112 |
| U5 | Unsound | ProcessingRecord lost the manifest's fields, which recall, purge and attestations need | Repaired (§5.4) |
| U6 | Unsound | Endorsement revocation lost its A3 clause, §13 row and T20 half | Repaired (A3, §13, T20) |
| U7 | Unsound | AC4 and T51 lost "no lasting rights or scope ownership"; administrator could share a personal scope's records into a scope they read | Repaired (AC4, T51) |
| U8 | Unsound | Deletion preview counted unreadable dependents | Repaired with R-16 (§12.3, T27) |
| U9 | Unsound | UPMS-derived representations had no tag rule | Repaired (§7.4, AD1, OV2, T111); T53 not revived, T111 replaces it |
| U10 | Unsound | Traversal limit only "at commit", not at use | Repaired (§13) |
| U11 | Unsound | Access records deletable by cascade or `curate` | Repaired (§11.4, T112) |
| U12 | Unsound | Redaction narrowed to UPMS-derived representations while A.3 said "kept" | Repaired: redaction as erasure (§12.5); A.3's "kept" is corrected here |
| M1 | Missing | Event-level deletion including redaction replacements | Repaired (§12.5) |
| M2 | Missing | Unknown dependency coverage; independent sources and subject-level discovery | Repaired (§12.4) |
| M3 | Missing | Purge-controller minimization | Repaired (§12.4) |
| M4 | Missing | Backup service never serves; restore access audited | Repaired (§12.4) |
| M5 | Missing | Strip sensitive links once no descendant remains | Repaired (§12.4, DL2) |
| M6 | Missing | Purge deadline miss | Repaired (§12.4 table, §13) |
| M7 | Missing | Reserved capacity for all restrictive controls | Repaired (§13); O6 and §14.2 still say "barrier" and should follow in D4 |
| M8 | Missing | Manifest commit failure row | Repaired (§13) |
| M9 | Missing | T43's positive clause | Repaired (T43) |
| X1 | Misdescribed | AC1 dropped the oversight entitlement, contradicting AC7 and §7.3.4 | Repaired (AC1) |
| X2 | Misdescribed | A.4 calls SC1, D1, OV2, CO1, E3, AC3, AC4, H1 and VO1 unchanged in substance, but each was edited | Corrected here; OV2 and AC4 repaired; the others are open for the reviewer, notably AC3's dropped "oversight transfer is fenced" and H1's "fails closed" → "reports it" |
| X3 | Misdescribed | A.3 §11.2 row claims a surviving-descendant count that §11.2 does not have | Corrected here |
| X4 | Misdescribed | A.3 §12.3 row omits the removed `authorized / restricting` state and the deadline-missed condition | Corrected here; M6 repaired |
| X5 | Misdescribed | A.3 §12.1 row omits the dropped "split into declared units at capture" and "WAL" | Corrected here; open for the reviewer |
| X6 | Misdescribed | A.3 §12.6 row says "copied", but 6.1 added "imported records keep source class X or R" | Corrected here; open for the reviewer |
| X7 | Misdescribed | §13 owner failover dropped "and egress rights" | Corrected here; probably safe given F5 |
| X8 | Misdescribed | T52's retirement attributed to D-25 although parts are D-6/D-24, and surviving-copy status in §10.6.2 has no test | Corrected here; open |
| X9 | Misdescribed | §15.2 range "T01–T103" | Repaired (T01–T112) |
| X10 | Misdescribed | §7.3.7 allows deleting a departed user's personal scope, but §12.3 names no deleter for it | Open |

### A.12 Owner-decision status and challenges at candidate 6.2 (moved from the core)

Moved unchanged from candidate 6.2 §18.2 and §18.3 (SHA-256 `0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc`), at the same-family review's suggestion (F62 §3.7 item 3). Section references inside it are to candidate 6.2. Core 6.3 §18.2 keeps the current decisions; none of D-1 to D-36 changed in 6.3. "Author's recommendation" entries were decided by D-37 to D-56.

#### Candidate 6.2 §18.2, Owner decisions

D-1 to D-19 are from candidate 5 §18.2; D-20 to D-36 from proposal §0.2. "Pending" means the owner has not confirmed the outcome this candidate uses; each may be revisited at Gate 0. D-37 to D-46 are recorded in `UPMS_Owner_Decisions_2026-11-03.md`. D-47 to D-56 were decided when the owner directed this revision on the author's recommendations ("Draft on these", 3 November 2026). Owner decisions are product choices; they verify nothing technically.

| ID | Decision | Status in candidate 6 |
| --- | --- | --- |
| D-1 | Administrator reads of personal scopes | **Confirmed** (3 November 2026): logged in the canonical store and the recovery log before release; the owner sees the access records; the replicated control plane and notice-delivery tracking are dropped (§7.3.6, §11.4, §12.4). It also governs drafts a critic keeps in a personal scope (annex §7.8) |
| D-2 | Administrator power through agent sessions | **Carried:** never (§7.3.1). Wording simplified to administrator mode |
| D-3 | Scope nesting | Carried |
| D-4 | Source of groups | **Confirmed:** carried; the four revocation stages reduce to change and observation (§7.3.7) |
| D-5 | Rights granularity | **Superseded by D-28** |
| D-6 | Derived memories when access to a source is lost | **Superseded in the default profile** under D-24: a record lives in its scope under its writer's responsibility (§7.3.5); a simple form returns only in the strict profile (§7.9) |
| D-7 | Agents as persistent principals | Carried |
| D-8 | Who decides publication | **Confirmed moot under D-24:** publication becomes sharing (§10.6.2); the required sharing categories for agents survive (§10.6.3) |
| D-9 | Oversight | **Confirmed, amended by D-49:** an agent principal's read is capped at its overseer's; curate capped outside its own scopes; write uncapped; never `manage`; the overseer grant is protected. The review chair is a service role outside the cap (§7.3.1); only a temporary review-service session assists an anonymous critic (annex §7.8) |
| D-10 | Blind review in the pilot | **Extended by D-33:** lineage exclusion plus masked review packages (§7.8, §10.6.4) |
| D-11 | Domain adaptation of small models | Carried; moves to Slice 4 |
| D-12 | Published copy when its private original is deleted or expires | **Moot under D-25:** nothing expires; deleting the original never deletes a sharing copy, which is listed for withdrawal (§10.6.2) |
| D-13 | Audit retention | **Moot under D-25:** access records persist until an authorized explicit deletion that the named principal can never make (§11.4) |
| D-14 | Rule screening in the pilot | Carried: prohibitions only |
| D-15 | Source of the Slice 1a overview | Carried |
| D-16 | Slice 1a boundary | **Confirmed:** import and export in 1a-team |
| D-17 | Agent publication before runtime lineage | **Moot under D-24:** no publication waiver and no overseer check |
| D-18 | Narrative coverage | **Confirmed:** a measured fraction (T54), without expiry, with scope and reader-language counts |
| D-19 | Multi-language support | **Confirmed:** one narrative language per scope; detected locales never decide a typed value; action grounding moves to the runtime |
| D-20 | One theory–evidence memory | Applied throughout |
| D-21 | SSDS stays outside | §9.14 |
| D-22 | SCIRE as front end and back end | §4.4 |
| D-23 | New structure before candidate 5's review | Candidate 5 frozen; this file is new |
| D-24 | Security proportionate to open science | §7, §8, §11; change history A.3 |
| D-25 | Retention by importance, never by time | §12; change history A.3 |
| D-26, D-31 | Superseded by D-32 | — |
| D-27 | No strict profile in the first product | §7.9; consequence: the first product excludes material needing derivative containment (§1.2, C6-14) |
| D-28 | Four rights | §7.3.3; with the SC-61 marker (§12.3) |
| D-29 | Any curator confirms archival | §6.12, §12.2, with the core's liveness check |
| D-30 | Project memory first | §16 |
| D-32 | Judge work, never score people | §9.13, §17.3 |
| D-33 | Anonymous and blinded review of works | §7.8; front-end process SCIRE's |
| D-34 | Reserved review chair; optional facilitator | §7.8 back end; facilitation SCIRE's (§4.4) |
| D-35 | Review-chair appointment | §7.8 checks; appointment SCIRE's; default in §14.2 |
| D-36 | Anonymous critiques inform, never block | §4.4, §5.11; read narrowly (D-37), with SCIRE's basis-statement rule (D-38); the core never refuses a decision because an objection exists (D-50) |
| §15 item 6 | Judgment on judgment | **Deferred** (D-39); §9.10 |
| New | De-attribution of a person from derived statements on request (re-review V4-12 (iii), D1-F4) | **Decided** (D-44), bounded by D-54; §12.3, T107 |
| D-37 to D-46 | Owner decisions of 3 November 2026 (D-36 reading, SCIRE basis rule, judgment on judgment, custody, erasure, anonymity slice, first-product boundary, de-attribution, channel assessment, SC-61 and SC-62 repairs) | As recorded in `UPMS_Owner_Decisions_2026-11-03.md`; realized in §1.2, §5.11, §7.8, §9.10, §9.13, §12.3 and §16 |
| D-47 | Objections on revision | A revision carries every objection to the successor, unresolved, until withdrawn, rebound or resolved by decision (D1 F-3a; §6.10; T108) |
| D-48 | Effectiveness for scientific standing | Defined by D1 Definition 6.0, with no wall-clock bound unless the ruleset states one; candidate 5 §9.3 governs project-memory facts only; a Slice 2 inquiry ruleset (§7.6, §9.9, §14.2; T109) |
| D-49 | Anonymous role as a session type | Distinct session type; sealed placement, edges, assignment and lifecycle acts; assistance only by a temporary review-service session, amending D-9 as confirmed; without proven session separation, critics write only through the front end's anonymous mode (annex §7.8; T110) |
| D-50 | Objections at decision commit | The core never refuses a decision because an objection exists or arrived late; late objections travel as a delta; SCIRE's policy decides whether to re-evaluate (§6.9; T100) |
| D-51 | Signature completeness | `validated` decisions are awaiting signatures or complete; only complete ones make a position current (§6.9; T100) |
| D-52 | Front-end and chair authority | Front-end registration is an operator act; a change of decision-policy owner needs the outgoing owner's attestation or an administrator-mode act and is shown; chair appointment belongs to the front end that opened the review, shown to participants; the core drops its `manage` rule for person chairs (§6.9, §14.2; T88, T100) |
| D-53 | Recovery log | Every restrictive or sealing control (permission revisions, access records, quarantines, corrections, tags, obligations, blocks, transfers, markers, sealing records, signatures) joins the tombstones in the separately backed-up recovery log applied before restore serves (§12.4, §14.2; T13) |
| D-54 | De-attribution and accountability | Accountability renderings are exempt from D-44; de-attribution is presentational (§12.3; T107) |
| D-55 | Author search | Works without their assessment values; a work's assessments appear when it is opened (§9.13, D1 F-39; T81) |
| D-56 | Structure of the review package | Core plus anonymous-review and checking annexes plus a separate change history; the outside reviewer reviews the core and the anonymous-review annex at Gate 0, and the checking annex before Gate 3 (§1, §16) |

#### Candidate 6.2 §18.3, Challenges and findings raised in that candidate

The author's findings while reconciling the proposal with candidate 5. Two are Serious Challenges to the proposal's text, each with a bounded repair applied provisionally here; the rest are clarifications or choices for the owner. The D1-level findings D1-F1 to D1-F5 are in the D1 formulation §14.

| ID | Kind | Finding | Provisional repair here | Needs |
| --- | --- | --- | --- | --- |
| **SC-61** | **Serious Challenge** | D-28 merges deleting others' items into `curate`, and the proposal gives any curator deletion on request. A curator, often the PI, could then delete a critic's objection, a dissent or an adverse judgment, and TE-04 and TE-09 could no longer hold. This is the dissent-loss failure SCIRE exists to prevent | A reason and an attributed deletion marker wherever the record would have appeared, for readers who could read it (§12.3, DL1, T85). `curate` keeps deletion; nothing is removed silently | Owner confirmation that D-28's curate includes deletion only with this marker **Decided:** D-46. |
| **SC-62** | **Serious Challenge** | Proposal §7.1 seals the author of an anonymous record, but release records (§8.2), processing records, quota and access records, and an assisting agent's overseer link would name the critic's principal. D-33's promise would fail through provenance the proposal itself keeps | Every record an anonymous-role session causes is sealed with it (§7.8, SE1, T86). The Codex review found the same class of leak from the proposal's text (SC-TE02: `witness_principal`, ownership, locators, logs, manifests, model requests); its paths are now listed | Reviewer check that no other record class leaks **Decided:** D-46, extended by C61-3 to C61-6 and D-49. |
| C6-1 | Clarification (owner) | "Sealed from administrators too" (proposal §7.1) holds against in-product access paths, but not against an operator controlling storage and keys. The Codex review reaches the same point (SC-TE02) | Stated as a TCB residual (§7.7, §7.8); the chair runs as a confined service role whose model never sees identities | Owner: accept the residual, require stronger custody, or withhold anonymity until it is met **Decided:** D-40. |
| C6-2 | Clarification | Importance includes "recency of use" (proposal §9.1 rule 5), which could become time-based retention by another name, against D-25 | Recency only orders records that already have a substantive reason (§12.1 rule 4) | Owner confirmation (D-29 left importance proposed) **Decided:** confirmed (3 November 2026). |
| C6-3 | Clarification | "Irrelevant to any live question" read as absence of links would recommend archiving unassessed observations and null results, which SCIRE treats as valuable | Irrelevance needs an attributed judgment; absence of links never suffices (§12.1 rule 3) | Reviewer check |
| C6-4 | Clarification | Proposal §13.2 says no hidden applicable objection arises within a project in the default profile. That holds only if objections are recorded where the target's readers can read them | Objection homing rule (§5.11, T90) | Reviewer check |
| C6-5 | Choice (owner) | Dropping D-6 removes candidate 5's deletion propagation along requirements. For an erasure that must not survive in copies, what happens to authored descendants is no longer defined by the proposal | Authored descendants get deletion obligations for their owners, never automatic deletion (§12.3) | Owner: obligations, or automatic propagation for erasures **Decided:** D-41. |
| C6-6 | Process | Proposal §14 step 1 (outside-family review of the proposal before drafting) had not happened when the owner asked for this draft. The Codex review then arrived during drafting; its repairs were folded in afterwards rather than designed in from the start | change history A.8 maps every finding; review against its trajectories (§1.3, Gate 0) | Owner acknowledgement |
| C6-7 | Choice (owner) | D-33 to D-36 postdate the proposal's slice plan, which does not place anonymous review | Back end placed in Slice 3; anonymity is unavailable, and no sealed identity is collected, before then (as the Codex review §7 step 4 recommends); the SCIRE demonstration in Slice 2 runs with open review | Owner: Slice 2 if the demonstration needs anonymity, with the whole §7.8 contract qualified first **Decided:** D-42. |
| C6-8 | Deviation | Proposal §8.2 keeps the release fence only for deletion and correction | Quarantine also uses it (§9.4), adding no mechanism | Reviewer check |
| C6-9 | Clarification | The proposal says decisions are "recorded but never shown as in force" (§3.5) and that a position is "current" only where a decision makes it so (§6.1) | Decisions render with decider, authority basis, purpose and interval; "current" only for that purpose (§6.9) | Reviewer check |
| C6-10 | Deviation | The proposal's decision kinds omit resolution by assessment, which the SC-41 repair needs | Kind `resolution` added (§5.4; D1-F2) | Reviewer check |
| C6-11 | Deviation | The proposal names no core check for D1 F-2 (no unconfirmed interpretation as basis) or F-17 (no sole uninstrumented backing); both are D1 meanings the proposal assigns to UPMS (§3.2, §5.3) | Core integrity checks at decision commit, never policy (§6.9) | Reviewer check that this does not trespass on front-end policy |
| C6-12 | Decided | De-attribution on request (re-review V4-12 (iii)) is carried by neither the proposal nor candidate 6 | Proposed in 6.1: D1 F-9a, §12.3, T107 | Owner decision. **Decided:** D-44, bounded by D-54. |
| C6-14 | Choice (owner) | D-27 defers the strict profile, and the default no longer contains derivatives (D-24). A project that ingests embargoed, human-subject or industry-restricted material before the strict profile exists would be unprotected (Codex review TE-R06, §5.1) | The first product excludes such material (§1.2); the default guarantee is stated as direct access control plus attributable sharing (§7.3.5) | Owner confirmation of the product boundary **Decided:** D-43. |
| C6-13 | Simplicity | Proposal §2.3 expected D-24 and D-25 to remove more text than the theory layer adds. They did not: the body before Appendix A is about 40,600 words against candidate 5's 31,900, before the 7,200-word D1 formulation; candidate 6 itself said 37,900 and 6,600, which was a miscount. In 6.1 the body is about 42,600 words and the D1 text about 8,000: the recommendations and repairs added more than the deferrals removed. The removals are real (§7.2, §8.3, §8.4, the deadline machinery of §10.5 and §12, publication), but the theory layer, the anonymous-review back end and the reconciliation notes outweigh them | None applied; carried-over text was copied verbatim rather than compressed, to keep it checkable against candidate 5 | Reviewer: name text that can go, especially in §5.9, §9.7 and §10.5 **Decided:** D-45, D-39 and D-56. |
| C61-1 | Finding against candidate 6 | §9.10 let `content` judgment-basis entries count for admission while only `current` entries went stale, so an admitted judgment could keep relying on an overturned judgment's content, and impact traversal (§9.11) does not treat judgment changes as a cause (the Codex review's SC-TE01) | Only `current` entries count (§9.10, D1 §6.5, T94) | Reviewer check |
| C61-2 | Finding against candidate 6 | §6.9 said no client can write `validated` for a policy it does not own, but nothing recorded which front end owns a scope's decision policy, so the rule could not be enforced; and it did not say that re-evaluation after a refused commit makes a new revision (SC-TE05) | Decision-policy owner in scope configuration, set under `manage`; transmitter checked at commit; re-evaluation is a new revision (§6.9, §7.3.3, DC1, T100) | Reviewer check |
| C61-3 | Finding against candidate 6 | One pseudonym per critic per review makes the number of anonymous critics visible, so candidate 6's "one or more critics" rule protected nothing (TE-R13) | Rule removed; the visible number is disclosed (§7.8, T101) | Reviewer check |
| C61-4 | Finding against candidate 6 | Signing one record under a stable pseudonym attributes every record under it, which candidate 6 did not say | Signing is all-or-nothing per review and shown first (§6.10, §7.8, T106) | Reviewer check |
| C61-5 | Finding against candidate 6 | Sealed attribution still reached released results: independence counting merged signed and anonymous records (D1 F-20), and a failed conflict check returned the reason class "critic", which tells the proposer that the person is an anonymous critic (TE-R13) | Nothing released depends on sealed attribution: analyst independence across anonymous and signed records, or across reviews, is "not established"; a sealed ground shows as a decline (§7.8, D1 F-20a, SE1, T104) | Reviewer check |
| C61-6 | Finding against candidate 6 | An agent assisting an anonymous critic whose overseer is someone else exposes the critic through the overseer's protected read grant on the agent's scopes (SC-TE02, D-9) | Only the critic's own agent or a temporary review-service session assists; drafts in a personal scope are disclosed as readable in administrator mode (§7.8, T105) | Reviewer check |
| C61-7 | Simplicity | Channel assessment and track records carry proxy risk (TE-R12) and serve no first-slice journey | Deferred to Slice 4, conditional on measured need; works are still assessed in Slice 3 (§9.13, §16) | Owner confirmation **Decided:** D-45. |
| C62-1 | Same-family review SC-R1 | A revision of a target resolved every objection to it, so a typo fix cleared dissent | Objections carried (D1 F-3a, §5.11, §6.10, T108) | D-47; reviewer check |
| C62-2 | Same-family review SC-R2 | "Effective" was candidate 5's admission rule, under which no route could be sound, or the admission rule was bypassed | D1 Definition 6.0, new route statuses, inquiry ruleset (§7.6, §9.3, §9.9, §14.2, T109) | D-48; reviewer check |
| C62-3 | Same-family review SC-R3 | Sealing followed sessions and a closed field list; session merging, placement, ancestry edges, assignment and lifecycle acts leaked | Distinct session type and the rules of annex §7.8 (SE1, T110) | D-49; reviewer check |
| C62-4 | Same-family review R-04, R-05, R-06, R-10 | The applicable-set check gave any objector a veto; signature completeness was undefined; a `manage` holder could swap the policy owner; chair appointment was a core `manage` rule | Late-objection delta; awaiting and complete; attested owner change; front-end-bound appointment (§6.9, §14.2, T88, T100) | D-50 to D-52; reviewer check |
| C62-5 | Same-family review R-14 | Restore applied only tombstones, so revocations, access records and markers inside the recovery-point window were lost | Recovery log (§12.4, §11.4, §14.2, T13) | D-53; reviewer check |
| C62-6 | Same-family review R-01 to R-03 | Objections on route endpoints never reached decisions; the cycle rule broke valid routes and disagreement showed as broken; history did not pin the projection version | Endpoints in D1 F-6 and §9.9; per-derivation circularity and "disputed"; pinned projection version (T69, T75, T78, T109) | Reviewer check |
| C62-7 | Same-family review R-07, R-08 | The uninstrumented-backing check was bypassable and refused a front-end decision; the stored applicable-set snapshot duplicated history | Label over routes; derived snapshot (§6.9) | Reviewer check |
| C62-8 | Same-family review R-09, R-11, R-12 | Critic-side conflicts were unchecked and declines were a timing oracle; quotas differenced the critic; participant-visible fields were unenumerated | Annex §7.8 and §11.5 (T88, T110) | Reviewer check |
| C62-9 | Same-family review R-13, R-15 to R-18 | "Or nothing" removal; de-attribution of accountability; preview existence count; author-search juxtaposition; self-declared `subject_kind` | §12.3, §9.13, D1 F-9a and F-39 (T27, T81, T107) | D-54, D-55; reviewer check |
| C62-10 | Same-family review R-19 | Consistency defects: ranges, T70 and T99 in Slice 2, T03 before obligations exist, citations, "Archive" for the canonical corpus, unmarked surfaces | Fixed (§5.11, §10.5.1, §16, §17.2, D1 §10.3, §11) | Reviewer check |
| C62-11 | Same-family review R-20 | Text and mechanisms that can go | §9.10 contract, `judgment_basis[]` and T94 removed; persistent-agent assistance removed; channel assessment moved to the checking annex; SE1 and TE-15 merged; check 3 a label; the snapshot derived; the package split. Not taken: merging `reported` and `recorded`, which SC-TE05 needs apart | Reviewer check |
| C62-12 | Same-family check of A.3 against candidate 5 | A.3 dropped or misdescribed candidate 5 obligations still needed under D-24 and D-25: restore safety beyond tombstones (U1 to U3); payload-free survivors (U4); manifest fields (U5); endorsement revocation (U6); administrator lasting access (U7); the preview count (U8); tags on derived representations (U9); traversal limits at use (U10); access-record deletion paths (U11); redaction erasure (U12); and M1 to M9, X1 to X10 | Repaired in §5.4, §7.4, §11.4, §12.3 to §12.5, §13, AC1, A3, AC4, AD1, OV2, DL2, T13, T20, T43, T51, T111, T112; X2 to X10 are recorded in change history A.11 as corrections to A.3 and A.4 | Reviewer check |

### A.13 Candidate 6.2 → candidate 6.3

Candidate 6.2 and its annexes are unchanged. The 6.3 core, its four annexes and this file together hold every byte of 6.2 except the changes below. The same-family review of 6.2 (`UPMS_Candidate_6_2_Same_Family_Review.md`, SHA-256 `255bf6a844f8b17caaf39eed531156d1aa600efcb2dbbdb9a16b2909a24742b9`) and owner decisions D-63 to D-70 drive them.

| Where | Change | Finding or decision |
| --- | --- | --- |
| §1 | Revision 6.3; D1 parent 1.3; the 6.2 review and the decision records as inputs; the five-file package; the 6.1 paragraph removed | §3.6 a, §3.7 item 9 |
| §2, §4.3, §4.4 | Objection targets include resolutions; same-assessor supersession and no anonymous judgments at `submit_assessment`; deletion preview lists unresolved objections; `designate_verifier`; D-36 bullet shortened | §3.6 b, h; F62-01; D-64; H5; §3.7 item 4 |
| §5 opening, §5.1 | Annex record kinds (H7); `notation` on spans (H2) | Mathematics hooks |
| §5.3 | `fidelity` and `inspection` kinds (H1); `validity_interval`; same-assessor supersession | H1, F62-01, F62-06 a, §3.6 i, D-70 |
| §5.4 | `late_objections[]` removed; restore records and verifier designations among controls | F62-08, D-65, H5 |
| §5.5 | `renders` (H6); relation lifecycle `replaced`; replaced steps and relations carry objections; inference-step fields (H3) | F62-05, H3, H6, D-70 |
| §5.9 | Concept-level rules moved to the checking annex §5.9; record-level rules kept | §3.7 item 2 |
| §5.11, §6.3, §6.10 | `superseded` removed from resolutions; `target_state`; target withdrawal leaves objections live; rebind may move an objection to a restatement; carry for replaced steps | S62-1, D-63, F62-05 |
| §6.9 | Late-objection delta derived at read; pending decisions handed over on a change of policy owner; front-end registration shown | F62-08, F62-09, D-66 |
| §7.2, §7.3.1, §7.6, §7.7, §8.5 | Annex reference; D-9 status; ruleset registration and versions; TCB names the front end and transport; anonymity row cites SE1; pseudonymous logs | §3.6 c, k; F62-06 b; D-67; §3.7 item 5 |
| §9.3 | Condensed; stale reference to §9.10 as open removed | §3.7 item 8 |
| §9.9 | Lineage heads; "premises not established"; established premises, compatibility, cross-scope premises, discharged hypotheses; exposure label; restore interval in history | S62-3, F62-03, F62-04, F62-06 c, §3.6 g, D-69, D-70, D-65 |
| §9.11 | Obligations on anonymous records after closure | D-68 |
| §10.5.3, §10.5.4 | Consolidation and maintenance cost moved to the Slice 4 annex; exact projection, catch-up and the projection mode kept | §3.7 item 1 |
| §10.6.4 | Sealed records omitted uniformly | F62-14 |
| §12.2, §12.3 | Effective judgments and withdrawn targets are live; author deletion shows unresolved objections | F62-16, D-63 |
| §12.4 | Recovery log holds dissent, markers with reason class only, and has a synchronous off-site copy; restore record and coverage line; claim restated | F62-07, F62-17, D-65 |
| §13, §14.2 | Restore row; recovery point zero for the log; disk reserve aligned; Slice 4 rows moved | F62-07, §3.6 j, §3.7 item 1 |
| §15 | AC5, SE1, TE-04 extended; T13, T79, T84, T98, T100, T108, T109, T112 rewritten or extended; T115 new | S62-1 to S62-3, F62-01, F62-06 to F62-09, F62-16 to F62-18 |
| §16 | Gate 0 decisions D-1 to D-70 and the annex schedule; recovery log; T115 in Slice 2; T113, T114 in Slice 3, TE-15 removed; mathematics annex in Slice 3 | §3.6 e, f |
| §17.2 | New surfaces beyond the deliverable | D-63, D-65 |
| §18 | §18.2 keeps current decisions; history moved to A.12; §18.3 maps this revision's repairs C63-1 to C63-12 | §3.7 item 3 |
| Anonymous-review annex | Published and operational records split; sealed per-pseudonym area defined; no judgments; uniform decline wording; closure assignment; logs; review-scope `manage`; lineage-exclusion rule; signing leaves operational records sealed; stale assisting-agent text removed; T70, T86, T88, T99, T105, T106, T110 rewritten; T113, T114 new | S62-2, F62-02, F62-11 to F62-15, F62-18, D-64, D-67, D-68 |
| Checking annex | §5.9 concept-level rules added; H4 statement kinds | §3.7 item 2, H4 |
| Slice 4 annex | New file holding the moved text | §3.7 item 1 |
| Mathematics annex | §M.0 records the absorbed hooks and H7; front matter, slice row and open item 5 updated | Review §7 |

**Not taken:** folding `Rebind` into handling (§3.7 item 6), since D-63 lets a rebind move an objection to a restatement; trimming §12.4's honest claims (item 10). **Word count:** the core body before Appendix A is about 37,400 words against 6.2's 39,900 by the same count (whitespace-separated words; 6.2's own figure of 40,300 counted differently). About 5,000 words moved out, and the repairs, stubs and the new §18 added about 2,500. That is short of the reviewer's estimate of 34,000, because the reviewer did not count the repairs, and §10.5.5 and §5.9's retrieval rules stayed in the core, which Slice 1a needs.

**Author's finding while revising.** The mathematics annex's records (expressions, symbol contexts, models, derivations, inspection scopes) were new canonical kinds that the 6.2 core's §5 did not allow. The review checked only H1 to H6 and did not raise this; hook H7 now allows them.
