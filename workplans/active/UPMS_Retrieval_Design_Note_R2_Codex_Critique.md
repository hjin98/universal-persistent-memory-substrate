# UPMS Retrieval Design Note Revision 2: Codex Critique

**Model family:** OpenAI GPT.  
**Model name:** GPT-6, operating as Codex; the exact serving variant is not exposed in this session.  
**Date:** 5 November 2026.  
**Reviewer:** Codex, an AI reviewer. I am the same reviewer and family as the revision 1 critique, the 6.4 to 6.8 and 6.12 to 6.17 reviews and the 6.11 cross-check. This check is not blind. Prior exposure creates anchoring and common-mode limits; earlier reviews do not establish closure here.  
**Governing method:** SSDP 7.2.1; no task or named workplan assigns a `protocol_version`.  
**Repository binding:** branch `upms-candidate-6-d1-formulation`, HEAD `f6131e1d0e65a508be357afe71a3f88ee8983897`.

## Input identities and reading limits

The request was read first. Its own hash and all eight hashes directly bound in its §1 were checked with `sha256sum` before substantive review. All matched. They were checked again before completion and remained unchanged. The ratification record’s hash also matched the earlier decision record’s binding.

Paths in the following table are relative to the repository root.

| File read | SHA-256 |
| --- | --- |
| `workplans/active/UPMS_Critique_Request_Retrieval_Design_Note_R2.md` | `b0d4bf469acfeb15eb7ea64502af25ce6fbbe3cafa9d11b40ed393d2588c5ad3` |
| `AGENTS.md` | `c729fc2a7b38458e6b6c8db09a4a84046d5406129f8a96a89b92da07740ad2c5` |
| `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R2_2026-11-05.md` | `013a7ef05c150e665c52ba04097bb3b90f8ca88fd0e835af9c97ac6c54fd71ce` |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` | `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` |
| `workplans/active/UPMS_Retrieval_Design_Note_Codex_Critique.md` | `aae43b0c104791ea35b622e1ef286a38c200d1ccc9e1a5847ee2a16661eef923` |
| `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_2026-11-05.md` | `49412e997735253135885fa78bcbbfdf81fb806b89f3a7a06c29073362188abb` |
| `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` | `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_3_Annex_Checking.md` | `e507f9bb72f018e48fe0582ac8a4b22d8a5b8175d787c57a268db2a1de127e51` |
| `workplans/active/UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md` | `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310` |
| `workplans/active/UPMS_Candidate_6_17_Independent_Review.md` — selected sections and headings | `b31cf91f8581cda5929c7dff7ff868a8924c7106e0a0e8d157e23ebbf3835029` |
| `history/SEMANTIC_EVOLUTION.md` — headings and final two entries | `2fdcb0a698a0d40837e654b0d48c6ae8ea88abd107f22dabf9c2b668d786fc2e` |

The request, `AGENTS.md`, both retrieval notes, the revision 1 critique, both retrieval decision records, the ratification record and checking annex were read in full. The operative text was compared directly; revision 2’s §11 was used as an index, not as evidence that its claims were true.

D1 was inspected selectively, including Definition 2.3, the principles, F-1–F-2, evidence semantics, standing-report and history provisions, review obligations, limitations, the D2 handoff and open challenges. Core inspection concentrated on §1.4, access and processor rules, releases, commits and freshness, historical reads, retrieval, context assembly, accountability, deletion, recovery and the pilot profile.

**Parts not completely read:** D1’s detailed objection and route-status derivations; the remainder of the core outside those inspected sections, especially its full acceptance-scenario and evaluation tables; the remainder of the 6.17 review and semantic history. Anonymous-review annex 6.7, Slice 4 and mathematics texts, change histories, original discussion transcripts, earlier decision records, SCIRE sources, implementation code and runtime configuration were not read. Embedded references were not recursively certified.

Local procedural sources were also consulted. Here `skills/` means `/home/samjin/.codex/skills/`, and `memories/` means `/home/samjin/.codex/memories/`.

| Additional file read | SHA-256 |
| --- | --- |
| `skills/software-design/SKILL.md` | `d5f0d045ee6af2db72dfd1cd5da86362b48512cc6e6bc4d293ad363747ee2364` |
| `skills/software-design/references/architecture-and-design.md` | `06a7f931935ae84f11d3fd9ec52124333489d5c162fe1de6996535cee839cfd6` |
| `skills/software-design/references/semantic-definition-and-traceability.md` | `584af70c51e2e0a58a2ed432be0c71546c84824e635c47492cdf1ee67d30de3c` |
| `skills/software-design/references/security-and-trust-boundaries.md` | `ffc0093283ef93451eef87a628514089af872cd6656481ccbdffe6647880be54` |
| `skills/software-design/references/storage-and-io.md` | `4934daccfd87ee5ae4564644c321267ad71f560a993d0baea7da2b587d1db052` |
| `skills/software-design/references/performance-and-parallelism.md` | `c201db92e971a93211cc40165d16e56ae8a7942b0ee553de64678719fa4470e0` |
| `skills/scientific-formulation/SKILL.md` | `111a13625cf40a70aa95cf0c3968ca8efa533bfab55ec94a772d5790b2a81b5c` |
| `skills/scientific-formulation/references/scientific-formulation.md` | `246cef460328c85c6d9ca4c0d2d45586486b70ecbf76308c7b7318f7df706f99` |
| `skills/numerical-algorithm-design/SKILL.md` | `4de404bb9c1e24e82e0d26806b35a01b43b933e63294a54492769d6b6ec2826d` |
| `skills/numerical-algorithm-design/references/numerical-algorithm-design.md` | `f41f73eb5d3acb09ce7138e3f18ca5cb9c26e90a651f13548b8eee3fa7ecf267` |
| `memories/MEMORY.md` — selected registry passages | `6ae0d4cb824d42e8b92db98d6bff34362970e6a43d3c850f3ffffc6db9887a4b` |

Procedural sources were inspected for routing and relevant concerns, not audited comprehensively. Memory supplied review-hygiene context only; current authority was rebound from repository evidence. No rollout files were opened.

No file was edited, created, renamed or deleted. Git use was limited to status and revision identification. No implementation, benchmark, model evaluation, KMS operation, purge or restore was executed. The trajectories below are constructed counterexamples, not observed UPMS failures.

## Closure of the revision 1 critique

“Closed” below means the design-direction defect is resolved sufficiently for drafting. It does not mean its eventual implementation or error properties have been qualified. These are reviewer assessments, not owner dispositions.

| Earlier item | Status | Operative-text assessment |
| --- | --- | --- |
| **SC-R01** — exact execution versus semantic adequacy | **Closed at direction level** | R2 §1, §§3.1–3.3 and §4 distinguish predicate execution, extraction fidelity, relevance and support. Mandatory filters and discovery routes resolve the approximate-candidate contradiction. The new presentation issue in finding R2-N01 remains. |
| **SC-R02** — uniformly cheap exact discovery map | **Closed** | R2 §8 items 1–2 replace the claim with eligible metadata summaries and optional, budgeted, qualified facets. Counts may be withheld. Unknown structure remains visible. |
| **SC-R03** — incompatible deletion and deduplication boundaries | **Closed at direction level** | R2 §§6.2 and 6.6 choose independent deletion units, prohibit destructive key sharing with survivors, distinguish erasure events and retain qualification limits. Feasibility remains unexecuted. |
| **R-01** — composable completeness and unknowable losses | **Partly closed** | R2 §6.1 separates dimensions, counting units and pagination; §6.4 stops claiming to enumerate unknown semantic omissions. The restricted-source example introduces the disclosure conflict in SC-R2-01. |
| **R-02** — fallible context interpretation and adoption | **Original defects closed; new presentation ambiguity** | R2 §§5.1–5.3 limit speaker resolution, qualify declarations, preserve source context and restore adoption’s separate meaning. §4 item 3 then lists adoption and fidelity checking as an interpretation’s “state”; see R2-N01. |
| **R-03** — historical and dependency semantics | **Closed** | R2 §5.4 binds basis revisions and snapshots, distinguishes the two reads, tracks dependencies and rejects confirmation as independent verification. Its references to D1 F-31 and core §9.9 preserve the historical rules. |
| **R-04** — D2 rationale and allocation | **Closed** | R2 §9 engages the approximation-bound trigger and explicitly revises the handoff. §6.3 removes the overly broad probability prohibition. Encryption and ordinary topology remain D3/D4. |
| **R-05** — pruning publication protocol | **Closed as a drafting contract** | R2 §3.3 specifies coverage, compatible merges, atomic publication, deltas, failure behavior, polarity and phrase boundaries. The correctness argument and qualification are still owed by D2 and its concretization. |
| **R-06** — locality versus sublinear guarantee | **Closed** | R2 §3.4 explicitly rejects a general sublinear guarantee, names workload families, permits existing index summaries and retains budgeted exact search. |
| **R-07** — scale arithmetic and architectural inference | **Partly closed; minor residual** | R2 §3.5 fixes units, HNSW assumptions, omitted overheads and rebuild estimates. It still claims the vectors “do not fit in memory” without a RAM binding; see R2-N02. |
| **R-08** — whole-chain evaluation and abstention | **Closed at direction level** | R2 §5.7 separates the chain measurements, held-out scoring and useful-answer requirements. §§6.1 and 7 add runtime caps and latency components. No scores or performance claims are qualified. |
| **R-09** — constant write-cost claim | **Closed** | R2 §§2 and 6.5 replace it with workload-bound amortized work, include background amplification and preserve the tenant committer. |
| **R-10** — complete eligibility on every path | **Partly closed** | R2 §§3.4 and 5.4 correctly reuse complete eligibility, processor authority and the core’s actual tag rules. The §6.1 restricted-source count conflicts with those provisions; see SC-R2-01. |
| **R-11** — occurrence identity and protected digests | **Closed** | R2 §6.2 preserves distinct occurrences and interpretations, specifies counting units and protects digests. |
| **R-12** — placement, archive and recovery | **Closed as direction** | R2 §§6.2 and 6.7 separate placement from archive, qualify hot-only searches and define a staged recovery direction. D-120 permits the larger profile’s detailed service target to remain a draft proposal. |
| **R-13** — purge independent of ordinary merging | **Closed as direction** | R2 §6.6 specifies a separate purge scheduler, bounded segments, temporary-output cleanup, reserved I/O, purge debt and failure reporting. |
| **R-14** — lazy discovery, starvation and retained outputs | **Closed** | R2 §§2, 5.2 and 6.3 preserve canonical model outputs, asynchronous processing, lexical reachability and the accepted liveness rule. The separate no-resend defect was missed in my first critique; see SC-R2-02. |
| **R-15** — mutation binding and challenge scope | **Closed** | R2 §5.5 item 4 binds confirmation and revalidation at commit. §1 scopes the challenge to adequacy for D-101. |
| **Reference error: query compilation** | **Closed** | R2 §4 item 1 correctly points to its §5.5. |
| **Reference error: absence rule** | **Closed** | R2 §1 correctly locates the core’s absence rule in §10.2. |
| **Simplicity and first-product scope** | **Addressed** | R2 §10 separates immediate invariants and the first product from accelerations awaiting measured need. |
| **D4 evidence obligations** | **Still obligations, not executed closure** | Publication, predicates, translation, eligibility, deletion/recovery and resource-limit discriminators remain necessary. Nothing in this review supplies their executable evidence. |

## Serious Challenges

### SC-R2-01 — D3: the coverage example permits disclosure of hidden-source counts

**Status:** newly introduced in R2; drafting blocker. This challenges the proposed coverage contract, not the accepted core.

R2 §3.4 states:

> Hidden records never appear in exposed counts or plans.

Its §6.1 nevertheless gives this Availability example:

> “2 sources are restricted; 1 was deleted”

Core §7.3.3 includes knowing an item exists and its appearance in counts within `read`. Core §10.3 states:

> Without `read`, even "restricted supporting material exists" is not shown, except as a "private source" endpoint of a relation the reader can read.

**What is wrong:** the example does not distinguish unavailable bytes of a source whose metadata the caller may know from a source whose existence is hidden. Counting restricted sources can disclose the latter. The complete-eligibility prose elsewhere does not make this example safe.

**Counterexample trajectory:** a caller may read the project’s ordinary notes but cannot read a tagged investigation record. A query has no visible matches. Returning “1 source is restricted” reveals an otherwise hidden record. Comparing counts across predicates can reveal further information. Filtering the content while exposing its count violates the accepted boundary.

The count could be legitimate in a different situation—for example, where the caller is entitled to know the relevant source metadata but a selected processor cannot receive its bytes. R2 leaves those meanings unseparated.

**Why it matters:** D1 could draft “availability coverage” as reporting withheld matches while D3 drafts it as covering only authorized metadata. Those are incompatible contracts.

**Bounded repair:** qualify availability coverage by the caller’s entitlement to the metadata being reported. Remove the unconditional restricted-source example. Report unavailable bytes, authorized deletion markers and permitted private-source endpoints only under their existing rules; do not count hidden records. A generic statement such as “Results cover only records you may read” must remain independent of whether hidden matches exist.

No new disclosure policy or owner decision is needed to preserve the accepted boundary. Revealing hidden-match counts would require an explicit reopening of it.

### SC-R2-02 — D3: a release record does not prove that text remains available to the current model

**Status:** newly identified here, retained from revision 1; drafting blocker. My first critique missed it.

R2 §6.3 states:

> nothing a session already received is resent (release records track it)

Core §8.2 explicitly says:

> compaction and resume continue the same session.

It also permits all of a principal’s agent sessions to count as one when context isolation cannot be established. That conservative exposure identity supports provenance; it does not prove shared or continuing context availability.

**What is wrong:** R2 turns evidence of prior release into a permanent prohibition on supplying the bytes again. A historical release record establishes exposure. It does not establish that a resumed or compacted model still has the span, that an external runtime retained it faithfully, or that another physical context included within a conservative session identity received it.

**Counterexample trajectory:**

1. UPMS releases the source containing an important condition.
2. The runtime compacts its context and drops that condition.
3. The session resumes and asks to inspect the exact source.
4. The no-resend rule returns a reference because the release record exists.
5. The model must work without the requested evidence or attempt to reconstruct it from a lossy summary.

The source can remain intact, eligible and perfectly indexed throughout this failure. The defect occurs at the consumer boundary.

**Why it matters:** the economy rule can defeat grounding and reinspection while all retrieval checks remain green. UPMS’s memory-service profile does not establish complete control over external runtime context.

**Bounded repair:** make reference-only reuse an optimization conditioned on demonstrable availability of the exact revision and rendering to the current consumer. Always permit an authorized explicit refetch, subject to current eligibility and budget. When availability is unknown, supply the requested span or report the budget limitation.

The simplest repair is to remove the unconditional prohibition. It does not require a new runtime-context registry, handle system or instrumentation requirement.

## Other findings by earliest owning domain

### R2-N01 — D1: adoption and fidelity checking must not replace confirmation state

**Status:** newly introduced presentation ambiguity; resolve before fixing the response schema.

R2 §4 item 3 describes:

> that interpretation's state (unconfirmed, confirmed by its speaker, adopted, fidelity-checked)

R2 §5.1 correctly says:

> adoption is a separate route and leaves the interpretation unconfirmed

D1 Definition 2.3 specifies that adoption creates a new claim under the adopter’s attribution and changes nothing about the original interpretation.

**What is wrong:** the §4 list can be drafted as a single status enumeration even though its entries concern different objects and independent facts. An interpretation may remain unconfirmed while someone adopts a new claim based on it and another assessor judges its fidelity.

I do not infer that R2 explicitly requires a mutually exclusive enum. The problem is that its presentation contract permits that reading despite §5.1’s correct account.

**Why it matters:** showing only “fidelity-checked” could conceal that the speaker never confirmed the interpretation. Showing an interpretation itself as “adopted” can conceal whose new claim supplies the permitted decision-basis route.

**Bounded repair:** require separate presentation of speaker-confirmation state, adoption acts and their new claim references, and attributed fidelity assessments. Multiple facts can appear together. Preserve D1 F-2’s actual permission boundary.

This requires no new epistemic state machine and no owner decision.

### R2-N02 — D2: storage arithmetic does not establish a RAM limit

**Status:** minor residual of R-07; not independently a drafting blocker.

R2 §3.5 says:

> They show that full-precision vectors for a TB corpus do not fit in memory

**What is wrong:** the arithmetic establishes approximately 2,048 GB for the specified float32 vector population. It establishes no available-RAM quantity. Corpus size alone cannot prove that the vectors do not fit.

**Why it matters:** the sentence retains a hardware-independent architectural conclusion immediately before presenting disk-resident ANN as a candidate. The candidate direction is credible; the claimed deduction is too strong.

**Bounded repair:** say that the vectors exceed the memory budget **when the bound profile’s available RAM is below their footprint plus required headroom and other working state**. Let D2 compare layouts against that binding. No new benchmark is needed to correct the sentence.

### D3 and D4 scope

The two D3 blockers are SC-R2-01 and SC-R2-02 above. No implementation was reviewed, so no D4 implementation defect is asserted.

The repairs should be expressed at their existing owners: the response/coverage contract, context assembly and reuse, and D1 interpretation presentation. Adding parallel permission logic or a second provenance authority would make them harder to resolve.

## Owner decisions and corrections

| Decision | Assessment against operative R2 |
| --- | --- |
| **D-117** | **Applied.** §8 begins with eligible metadata summaries and makes query-conditioned facets optional, budgeted and qualified. Withholding a count that cannot be safely established is consistent with the accepted recommendation. |
| **D-118** | **Applied in substance.** §§3.2–3.3 and 4 separate exact checks from semantic assessments and preserve a labeled similarity-only route. R2-N01 is a presentation correction needed to carry that separation consistently into the draft schema. |
| **D-119** | **Applied.** §§6.2 and 6.6 choose deduplication within independent deletion units and require survivor preservation before key destruction. Wider deduplication waits. This is design closure, not KMS or purge qualification. |
| **D-120** | **Applied.** §§3.4, 6.5, 6.7, 7 and 9 leave the larger workload and recovery defaults for D2 proposal and owner setting. The pilot targets remain in force within their envelope. No new numerical profile must be decided before drafting. |

Both corrections in the D-117–D-120 record’s §3 are right:

1. **Fidelity–serving correction.** Core §§9.5–9.6 and 14.3 already distinguish canonical state, bounded search fallback and rebuildable derived structures. R2 §1 accurately scopes the remaining challenge to adequacy for D-101. It does not establish that the ratified pilot architecture was false within its prior envelope.
2. **D2-trigger correction.** Core §1.4 expressly includes “no consumer relying on a guaranteed approximation bound.” A pruning guarantee relied on for completeness engages that condition. R2 §9 correctly opens the determination rather than using deterministic execution as a reason to evade error semantics.

The decision record’s §3 assertion that the other findings “are repaired” remains an author’s closure claim. The closure table above identifies its limits.

## Simplicity and evidence limits

R2’s growth is mostly justified. The five coverage dimensions, filter/route distinction, publication conditions and deletion/recovery provisions resolve actual ambiguities. Section 10 appropriately defers custom summary trees, wider deduplication, sophisticated ANN layouts and other accelerations.

Keep those separations. Simplify the remaining defects by subtraction:

- remove the unconditional hidden-source count;
- remove the unconditional no-resend rule;
- replace the interpretation-state list with the existing distinct acts and assessments;
- qualify the RAM statement by the profile.

Do not add machinery merely to preserve either faulty unconditional rule.

The accepted D1 and core meanings were checked against the supplied critique and decisions, selected 6.17 review sections, and the current semantic-history entries. The 6.17 review reports no new material defect in its reviewed package; the history records the later D-101 adequacy challenge as direction only. This was a bounded repository search, not an exhaustive tension audit. Earlier review bodies, external/native issue records and original transcripts were not comprehensively searched.

No scientific results or retrieval measurements were produced or reviewed. No experimental variants were selected. The evidence here consists of verified file identities, operative-text comparisons and constructed trajectories. Error limits, useful-answer rates, workload costs, processor behavior, segment publication, purge and recovery remain unmeasured. Existing inspectability exclusions and owner-acceptance boundaries remain unchanged.

## Verdict and questions for the owner

**REVISE BEFORE DRAFTING.**

Revision 2 resolves the three original Serious Challenges at the design-direction level and applies D-117–D-120. It still contains two consequential D3 conflicts: restricted-source counting and permanent suppression based on prior release. Correct those and make interpretation presentation preserve confirmation, adoption and fidelity as separate facts. The RAM sentence needs a small qualification.

These are bounded repairs under existing direction. They require neither a TB experiment nor another round of owner choices.

**Questions for the owner:** none required before these repairs and drafting. Larger-scale workload, concurrency, bulk-import, recovery and performance defaults remain proposals for the owner to set under D-120. This critique grants no Gate 0 passage, ratification or implementation qualification.

