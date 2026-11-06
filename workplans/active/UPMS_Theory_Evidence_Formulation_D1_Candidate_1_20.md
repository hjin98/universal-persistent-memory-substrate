# UPMS Theory–Evidence Memory: D1 Formulation (Candidate 1.20)

**Kind:** Scientific Method Paper family (D1), first candidate, revision 1.20. It is the proposed successor of candidate 1.16, which the owner ratified as accepted-current (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`); candidates 1 to 1.19 stay unchanged. Its change maps are map S (1.16 → 1.17, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17_Change_History.md`), map T (1.17 → 1.18, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18_Change_History.md`) map U (1.18 → 1.19, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19_Change_History.md`) and map V (1.19 → 1.20, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20_Change_History.md`); maps B to R are listed in map R (owner decision D-85).
**Date:** 5 November 2026
**Status:** PROPOSED D1 authority. Not accepted, not ratified; D1 1.16 stays accepted-current until this revision is ratified. Revision 1.17 added §16, the meaning of an answer from memory, and revised §9's hand-off to D2, under owner decisions D-101 to D-120; every rule of 1.16 is kept. Revision 1.18 repairs the Codex review of 1.17 (NO-PASS, `UPMS_Candidate_6_18_Independent_Review.md`): it restores the resolution-basis rule, names the representation a lexical route searches, adds capture and count status to coverage, and corrects §13 (map T). Revision 1.19 is editorial: it changes no rule of 1.18, which had a technical PASS for Gate 0 entry in the Codex review of 6.19 (`UPMS_Candidate_6_19_Independent_Review.md`); it corrects §0.1 (F619-01) and its parent and consumer versions (map U). Revision 1.20 is editorial too: 1.19 had a technical PASS in the Codex review of 6.20 (`UPMS_Candidate_6_20_Independent_Review.md`), and 1.20 changes only the versions of its D2 parent and D3 consumer (map V). It is the D1 parent that UPMS architecture manual candidate 6.21 (`UPMS_Architecture_Manual_Review_Candidate_6_21.md`) with its retrieval-and-scale annex concretizes, and the D1 parent of the D2 retrieval method candidate 1.3 (`UPMS_Retrieval_Method_D2_Candidate_1_3.md`). No file is accepted by being in the repository.
**Author / asserter:** Claude (AI, Opus 5.5), in a Claude Code session, at the product owner's request. No subagents were used. Each revision answers a review or owner decisions; the revision-by-revision account is in the change history (owner decision D-85). Revision 1.17, at the product owner's request "Start drafting" (5 November 2026), drafts §16 from design note revision 3 (`UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`). Revisions 1.18 to 1.20 answer the Codex reviews of 1.17 to 1.19 under the owner's delegation of the revise-and-review cycle.
**Governing method:** SSDP 7.2.1; no task or workplan assigns a `protocol_version`.
**Acceptance route:** independent falsification by a reviewer **outside the Claude family**, then ratification by the product owner. Same-family review does not count (`AGENTS.md`).

---

## 0. Authority metadata

### 0.1 Inputs

| Input | Identity | Role |
| --- | --- | --- |
| D1 candidate 1.19, and its review (Codex, OpenAI family) | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19.md`; `workplans/active/UPMS_Candidate_6_20_Independent_Review.md` | Immediate candidate predecessor; PASS for Gate 0 entry |
| D1 candidate 1.18, and its review (Codex, OpenAI family) | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md`; `workplans/active/UPMS_Candidate_6_19_Independent_Review.md` | Candidate predecessor of 1.19; PASS for Gate 0 entry; F619-01 was corrected in 1.19 (map U) |
| UPMS Theory–Evidence Formulation, D1 candidate 1.17, and its review (Codex, OpenAI family) | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md`; `workplans/active/UPMS_Candidate_6_18_Independent_Review.md` | Candidate predecessor of 1.18 (NO-PASS); SC618-01, F618-01 and F618-02 were repaired in 1.18 (map T) |
| UPMS Theory–Evidence Formulation, D1 candidate 1.16 (accepted-current) | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md`, SHA-256 `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54`; ratified in `workplans/active/UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`, SHA-256 `7c5a079342ed548cb78c78fff42ddd27731062ec9d27a6d72544c7568ca25310` | Accepted predecessor; every rule kept |
| Owner decisions D-101 to D-116 | `workplans/active/UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md`, SHA-256 `34aef9d97785c9f2b861cf27074bd9679d78071723453fda1a620e043eab739c` | Retrieval at scale, translation and economy; folded in (§16, §9) |
| Owner decisions D-117 to D-120 | `workplans/active/UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md`, SHA-256 `2a971426b0f3c631be7b9760540471046d65f7f930088a0d2b7123ef0002c951` | Refinements after the Codex critique; folded in (§16) |
| Retrieval design note, revision 3 | `workplans/active/UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`, SHA-256 `9009efb9edb9440ac8e1f3b57a71ead3ab610fcafb3cfa6181046321f6aacb4f` | Direction, not authority; Codex found it sound to draft from (`UPMS_Retrieval_Design_Note_R3_Codex_Critique.md`, SHA-256 `66a2ae248a4ce55196561180cbdfb504b8de83ecb55909df8f4feb5835d19da4`) |
| UPMS Theory–Evidence Memory: Structural Proposal v0.1 | `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md`, SHA-256 `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction; §3–§6 are the source of this formulation (§14 step 2); owner decisions D-20 to D-36 |
| SCIRE Conceptual Proposal v0.4 | SCIRE repository, `workplans/active/SCIRE_Conceptual_Proposal_v0.4.md`, SHA-256 `181642331557b4c0b918332520e0159e3fc69ba8ba690024e9d88e187a9de002` | Theory semantics, §§3–7 (principles, record, inquiry, evidence, history) |
| SCIRE v0.4 same-family re-review | SCIRE repository, `workplans/active/SCIRE_v0.4_Re-Review.md`, SHA-256 `2d5fb01e6dce22340f87d58bda81caba9001c27adfe56de7d480b0bd9ee6b52e` | Repairs SC-41, V4-06, V4-07, V4-12, V4-13 adopted here where they are D1 |
| Independent review of the proposal (Codex, OpenAI GPT-6 family) | `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md`, SHA-256 `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | NO-PASS for the proposal; its D1 findings (SC-TE01, SC-TE04, TE-R10 to TE-R12) are answered in §6, §4.2 and §7. It arrived after the first draft of this text |
| Independent reviews of D1 candidate 1.15 with architecture candidates 6.15 and 6.16 (Codex, OpenAI family) | `workplans/active/UPMS_Candidate_6_15_Independent_Review.md`, SHA-256 `195d27b21f2917e010a732bb15740b43ea617d7a3349421ba5b159f38de7f251`; `workplans/active/UPMS_Candidate_6_16_Independent_Review.md`, SHA-256 `727afb383999fdd89c1f4103041be2a4bb86104d62855690059d34d9aa17afa4` | PASS for Gate 0 entry for D1 1.15, retained in the 6.16 review. Earlier reviews are listed in map R |
| Owner decision D-100 | `workplans/active/UPMS_Owner_Decisions_6_13_Review_2026-11-05.md`, SHA-256 `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343` | Folded in here (§6.1, F-25, F-28) |
| Owner decisions D-97 to D-99 | `workplans/active/UPMS_Owner_Decisions_6_11_Review_2026-11-05.md`, SHA-256 `e9f0bd7e0abfd80fcdd763a61bb9542a027dff726bb6fced4a1681f4bc033295` | Folded in here. D-97 decides the author's proposal of it in amended form |
| Owner decisions D-92 and D-94 to D-96 | `workplans/active/UPMS_Owner_Decisions_6_8_Review_2026-11-05.md`, SHA-256 `5e9b40d43746059cbd4f23ff671bab735af7eccec5b940d3a36890f24cec33e9` | Folded in here; supersede the author's proposals D-90, D-91 and D-93 (moved to map K) |
| UPMS Theory–Evidence Formulation, D1 candidate 1.15 | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_15.md`, SHA-256 `8d934751f65cd6506d343b3ebde23a31c60ff5f57582a110023d80999d8d5b2c` | Immediate predecessor; the history moved out of it is in map R |
| D1 change map R | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16_Change_History.md`, SHA-256 `c63d3054062b540baf5e6637b6ea99c3e7fc934a5419279257bb7a111413a11d` | Lists maps B to R and the earlier reviews with their hashes; holds the text moved out of candidate 1.15. History, not authority |
| Owner decisions D-86 to D-89 | `workplans/active/UPMS_Owner_Decisions_6_5_Review_2026-11-05.md`, SHA-256 `8cc6ffc8e9bf89119a92b0500ac4be3fee9775e0d818821bfb30985ee0aa59fa` | Folded in here |
| Owner decisions D-79 to D-85 | `workplans/active/UPMS_Owner_Decisions_6_4_Review_2026-11-04.md`, SHA-256 `20144a3a92753313d1163378c3bdf338509a0910962bdb44fd38f458104c9671` | Folded in here |
| Owner decisions D-37 to D-46 | `workplans/active/UPMS_Owner_Decisions_2026-11-03.md`, SHA-256 `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | Folded in here |
| Owner decisions D-63 to D-70 | `workplans/active/UPMS_Owner_Decisions_6_2_Review_2026-11-03.md`, SHA-256 `e47594521218b5124b6d9914b6cc3c988520af29edaf1a4466d8ea7cf433a485` | Folded in here |
| Owner decisions D-71 to D-78 | `workplans/active/UPMS_Owner_Decisions_Math_Review_2026-11-03.md`, SHA-256 `161b6318ab3734357fd213ea98f47deb40f01bcdaeff2c33ce9313a24f09210f` | D-71, D-72 and D-74 folded in here; the rest bind the mathematics texts |
| UPMS Architecture Manual, review candidate 5 | `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md`, SHA-256 `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen input (D-23): record types, modality, screening, the §1.4 reopen triggers |

Earlier predecessors, reviews and change maps are listed with their hashes in map R. Until D1 1.16 was ratified on 5 November 2026, no accepted D1 authority existed for UPMS; 1.16 is the accepted predecessor of this revision. Candidate 5 §1.4 needed none; its triggers 1 (source-reliability scores) and 4 (custody of scientific records) now fire (proposal §2.3). Nothing here amends SSDS authority or the SCIRE proposals.

### 0.2 What this document owns, and what it does not

| Owned here (D1) | Owned elsewhere |
| --- | --- |
| The meaning of an answer from memory: plans, exact facts and assessments of items, coverage, absence for a plan, grounded answers, consequence classes, context frames, declarations, renderings, resolutions (§16) | How answers are computed: indexes, partitions, the compiler and resolver, budgets, deletion and recovery at scale: candidate 6.21 and its retrieval-and-scale annex (D3). Pruning guarantees, error models, cost models and evaluation: the D2 retrieval method candidate 1.3 |
| The meaning of every theory–evidence record and relation: modality, objection state, evidential relation kinds, use history, independence, origin, qualification, usability, warrants, tension kinds, comparability, standing, review obligations, source assessment, meaning identity, historical reads | Storage, commits, permissions, retrieval, sealing, deletion mechanics: candidate 6.21 (D3) |
| What may and may not be concluded from those records; which conclusions are reserved for attributed acts | Statistical comparison models, thresholds and any numeric score: D2, not opened for them (§9) |
| Adequacy and falsification criteria for this formulation | Discussion process, facilitation, review process, inquiry policy (the objection rule, finalization, authority): SCIRE front end (D-22) |

Security mechanisms (data-never-instructions, quarantine, scope rights) are not D1. They are D3 side constraints and appear here only where a scientific meaning depends on them.

---

## 1. Problem and intended use

### 1.1 The question

What must a project memory record, and what must it refuse to infer, so that a later reader (a person or an agent) can recover **what the project believed, why, how strongly, what bore against it, and how that changed**, without the memory itself deciding scientific truth?

The memory serves open, academic-like science (D-24): collaborative research among people and agents, with unpublished work inside projects and ordinary attribution. It also serves ordinary project memory, which uses the same records without the theory layer (proposal §7).

### 1.2 What the memory's "observables" are

The memory measures nothing physical. Its realized quantities are **epistemic records**: attributed statements with modality, assessments with their basis, relations with their conditions, objections with their state, decisions with their authority. The derived quantity of interest is the **standing** of a claim at a position in history (§6). Failure means a reader is misled about status, dissent, support, independence or history, for example an interpretation shown as an assertion, a disputed resolution shown as settled, or a fitted observation shown as independent confirmation.

### 1.3 Validity regime

- **In regime:** qualitative and ordinal epistemic states; explicit typed statements; human and agent assessors; projects of any size storage permits (D-101), qualified first at the pilot profile of candidate 6.21 §14.2 (D-120).
- **Out of regime, by design:** calibrated probabilities of truth; automated scoring of sources; general theorem proving; inference of a speaker's intent or motive; any judgment of a person by the system (D-32).
- **Out of regime until D2 is accepted for them:** quantitative statistical comparison of measurements (§5.6) and any numeric weight (§9). The D2 retrieval method candidate covers retrieval guarantees, error and cost only (§9).

---

## 2. Terminology and primitive notions

Every term is defined before later sections use it. "Record" means an immutable revision with identity, attribution and record time; "attributed act" means a record whose author is an authenticated principal (a human, or an agent principal with a human overseer) and that names what it acts on.

**Definition 2.1 — Event and observation.** An *event* `e` is an immutable record that something was said, received, observed or run, by whom, when and through which channel. It is not proof of its contents. An *observation* is an event whose payload is a measured, computed or reported result `o`. Its observation statement carries, where known: value `x`; unit; uncertainty `u`; conditions and regime `c`; instrument, code or method `μ`; origin `ω(o)` (Definition 2.9); qualification `q(o)`; observation time.

**Definition 2.2 — Claim and statement.** A *claim revision* `κ` is an attributed proposition with a modality `mod(κ) ∈ M`, conditions and regime `c(κ)`, optional time scope `τ(κ)` and links to source spans. `M` is:

| Modality | Meaning | Establishes truth? |
| --- | --- | --- |
| asserted | put forward as true by its asserter | No; it records that someone asserted |
| quoted | recorded words of another; fidelity is separate from content | No |
| reported | relayed from literature or another party | No |
| hypothesized | proposed for investigation | No |
| assumed | adopted for an inquiry, without a claim of truth | No |
| defined | a definition; establishes no truth or existence | No |
| predicted | an explicit prediction, with the conditions it covers | No |
| found | a recorded outcome of an investigation | No; it records that the investigation reported it |
| intended, committed, preferred | agentive project modalities | No |
| normative | a rule, with an external authority source | No; authority stays with the source |

A *statement* is a structured rendering of a claim (concept identifiers, typed value, qualifiers). Text is the record; structure is derived from it.

**Definition 2.3 — Three acts on an interpretation.** For a source span `s`:
- an *interpretation* `I(s)` is a claim extracted from `s`, attributed to its extractor (an AI or a person) as that extractor's reading;
- a *confirmation* is an attributed act by the speaker of `s`, and only the speaker, that `I(s)` is what they meant;
- an *adoption* is an attributed act by any participant that creates a new claim `κ'`, linked to `I(s)`, under the adopter's own attribution.

`I(s)` stays "interpretation, unconfirmed" until confirmed. Adoption changes nothing about `I(s)`.

**Definition 2.4 — Question.** A *question* `Q` is a record of an open problem with scope, kind (`ordinary` or `discrepancy`), live positions `pos(Q)` (claim references), status (`open`, `closed-answered`, `closed-unresolved`, `closed-unproductive`, `split`) and outcomes. Questions organize records and own none of them.

**Definition 2.5 — Objection.** An *objection* `O` has a target `tgt(O)` (a claim revision, an inference step, an evidence relation, an applicability condition, a resolution, another relation such as a `renders` link or a symbol binding, or an observation such as a tool check), a ground, an author, a *handling* `h(O) ∈ {open, acknowledged, deferred, answered}` and an optional *resolution* `r(O) ∈ {resolved-by-assessment, withdrawn}`, which records the target it assessed, where `withdrawn` means withdrawn by the objection's own author. Its **target history** `bind(O)` is its first target and every record it has been carried or rebound to (F-3a, F-3b); `tgt(O)` is the latest (owner decision D-94; Codex review SC66-02). Nothing that happens to the target resolves `O`: a revision carries it (F-3a), and a withdrawal of the target leaves it unresolved (F-3b; owner decision D-63). The predicate

```text
unresolved(O)  ⇔  r(O) is absent
```

does not depend on `h(O)`. One resolution closes `O`'s workflow everywhere it applies: nobody must resolve it again (owner decision D-94). Whether `O` still counts against what a view shows is decided per record. In a view over a footprint `F` (F-6), `O` **applies through** each record of `bind(O) ∩ F`; a dispute, which F-6 adds through the resolution it disputes, applies through that resolution. `O` is **settled for** a record `x` it applies through when `r(O) = withdrawn`, or when `r(O) = resolved-by-assessment`, the resolution assessed `x`, and that resolution is not disputed (F-4); otherwise `O` is **open for** `x`. `O` is **open in** the view when it is open for some record it applies through there. "Open in" is the one test for route status (§6.1), travel to decision projections (F-7), SCIRE's objection rule (F-8), the derived predicates (F-28) and mandatory lists (architecture §10.5.1). A view that shows `O` through a record other than the one its resolution assessed says so, for example "resolved by assessment at `K2`, not assessed for `K1`", so it never reads as settling the earlier target (D-94, D-97; Codex reviews SC67-03, SC68-01; Gemini reviews SC69-02, SC610-01, R610-02).

**Definition 2.6 — Evidence relation.** An *evidence relation* `E = (o, T, k, m, c, a, U, b)` states how observation `o` bears on target claims `T`, whose shape is fixed by the relation kind (Definition 5.1), under:
- relation kind `k` (Definition 5.1);
- conditioning model `m` and conditions `c`;
- assessor `a`;
- use history `U` (Definition 5.2);
- binding `b` = the exact claim revisions, regime and method it assessed.

**Definition 2.7 — Inference step.** An *inference step* `S = ({P₁…Pₙ}; c) --[t]--> C` asserts that premises `Pᵢ` (claim revisions) under conditions `c` support conclusion `C`, with type `t ∈ {deductive, computational, statistical, causal, abductive, analogical, heuristic}`. It exists only when someone asserts it as an argument. A *stated reason* (one claim given as the reason for another inside a speaker's words) is claim content and is never an inference step until someone asserts it as one. A *derivation* is a set of inference steps asserted together as one argument. A step of a derivation may **introduce** a hypothesis, a claim of modality `assumed` local to that derivation, and a later step of the same derivation may **discharge** it, so that the later step's conclusion no longer depends on it (for example by implication introduction, case analysis or reductio). A hypothesis is discharged **for a conclusion** only when every path in the derivation from a step that uses it to that conclusion passes through a step that discharges it (owner decision D-72); it is then not a premise of that conclusion (D-70). A hypothesis that is not discharged for a conclusion, and the defining relations and assumptions of a declared model that a step uses, are **carried conditions** of the conclusion, not premises to be established (D-71; §6.1). A step belongs to at most one derivation, and a derivation is acyclic.

**Definition 2.8 — Judgment.** A *judgment* `J` is an attributed assessment of one target revision under a named scope `σ`, a ruleset `ρ` and an evidence snapshot `π`. Its kinds are: claim assessment, evidential assessment (of an evidence relation), inference assessment (of a step's validity under its conditions), comparability assessment (§5.7), objection resolution (§4.2), source assessment (§7), retention recommendation (candidate 6.21 §12). A child formulation may add kinds: the mathematics formulation adds `fidelity` (whether a rendering says what a claim says) and `inspection` (what a human inspected, and to what depth). Those are separate statuses; they never enter route status (§6.1) and are never cited in an inference assessment's basis (owner decision D-70). A claim assessment carries an epistemic status

```text
status(J) ∈ {supported, refuted, contested, unknown,
             supported-under(c), disfavored-under(c)}
```

where `c` is a stated condition set. Judgments in different `(σ, ρ)` coexist; none overrides another by recency. Every judgment has a validity interval, unbounded unless it states one. A judgment may **supersede** only an earlier judgment by the same assessor; a judgment by another assessor of the same target under the same `(σ, ρ)` is a concurrent head, never a replacement (same-family review F62-01). The assessor of a judgment is always named to its readers: anonymous-role sessions never submit judgments (F-8; owner decision D-64).

**Definition 2.9 — Origin, qualification, usability.** For observation `o`:
- origin `ω(o) ∈ {external-system run, project-recorded, external-reported, uninstrumented}`;
- qualification `q(o) ∈ {qualified-for(scope), unqualified, provisional, failed, unknown}`, as stated by a named qualifying authority;
- usability `ν(o, use) ∈ {usable, usable-with-limits, under-review, not-usable}`, as concluded by an assessor for a given use.

**Definition 2.10 — Decision.** A *decision* `D` is an attributed act of kind `{inquiry, outcome, finalization, override, external, resolution}` with decider, authority basis (a reference to a project rule), scope and purpose, effective interval, basis statement reference, cited basis records `B(D)`, applicable objections and overrides, dissent, and exposure (the record versions and views the decider was shown). Which decisions are permitted, and when, is SCIRE policy; what a decision record means is defined here. The kind `resolution` is the decision that records an objection resolution by assessment (§4.2).

**Definition 2.11 — Review obligation.** A *review obligation* `R = (dependent, cause, assignee, state)` exists on a dependent relation or claim because a cause (retraction, correction, inapplicability, definition change, claim revision) reached it (§6.4). `state ∈ {pending, closed}`.

**Definition 2.12 — Meaning link.** A *meaning link* between two terms or statements is an attributed, contestable claim of kind `identical`, `equivalent-under(c)`, `refines` or `related`. The default for two similar statements is `unresolved possible match`.

**Definition 2.13 — Discovery link.** `arose_from(X, Y)` records that `X` was pursued because of `Y`.

**Definition 2.14 — Principal, person, work, channel.** A *person* is a human principal, or a group or institution of humans (labs, groups, venues count as persons here, D-32). An *agent principal* is not a person. A *work* is a bounded product: a publication, dataset, measurement, analysis, argument, reported result, model output. A *channel* is the route by which works of a kind reach the memory: an instrument, a dataset, a database, a model family, a person's reported results.

---

## 3. Principles (normative)

These restate SCIRE v0.4 §3 as memory semantics.

- **P1 — Record, interpretation and decision are distinct** (Definitions 2.1–2.3, 2.10).
- **P2 — Status changes only by a recorded act:** a judgment, objection, resolution, decision, revision, retraction or deletion. An assessment's result changes only by an attributed judgment (F-8; owner decision D-98). Repetition, summarization, persistence, retrieval rank, copying, age or archive placement change no status.
- **P3 — Handling an objection is not resolving it** (Definition 2.5).
- **P4 — Evidence is conditional** on a model and conditions (§5.1).
- **P5 — How data were used matters** (§5.2).
- **P6 — Agreement is not corroboration;** independence is a claim with dimensions (§5.4).
- **P7 — Competing explanations may coexist;** uncertainty does not justify choosing one.
- **P8 — Formal structure is not strength.** Length, connectivity, citation count, retrieval rank and consensus are not support.
- **P9 — Inquiry need not converge.** A null result, an exclusion or an unresolved contradiction can be a complete outcome.
- **P10 — Works are judged, people are not** (D-32; §7).
- **P11 — Importance is not truth.** What is kept active, archived or recommended for archive never changes standing (D-25).

---

## 4. Claims, objections and decisions

### 4.1 Modality preservation (normative)

**F-1.** For every derived rendering `ρ(κ)` (copy, summary, projection, export, narrative, translation), the modality and attribution of `κ` are recoverable from `ρ(κ)`, and `ρ(κ)` never presents `κ` in a stronger modality than `mod(κ)`. "Stronger" is any move from {quoted, reported, hypothesized, assumed, defined, predicted, interpretation-unconfirmed} to asserted or found.

**F-2.** An interpretation `I(s)` never supports a decision basis unless it is confirmed by the speaker or adopted (Definition 2.3). Confirmation and adoption never remove restrictions the source carries.

### 4.2 Objection semantics (normative)

**F-3 — Resolution.** `r(O) = resolved-by-assessment` only through a decision `D` of kind `resolution` that cites an objection-resolution judgment and names the target that judgment assessed. That decision carries the fields of Definition 2.10 (authority basis, basis statement, exposure, dissent), so resolution costs what an override costs in visibility (re-review SC-41 repair).

**F-3a — Revision carries objections** (same-family review SC-R1). When `tgt(O)` is revised to a successor revision, `O` is **carried** to the successor with the state "carried, pending re-examination". It stays unresolved, applies and travels exactly as before, until its author withdraws it, its author rebinds it to the successor (which only records that the author re-examined it), or a `resolution` decision under F-3 states that the successor no longer meets it, which resolves it, labeled as assessed at the successor (D-94). A reviser who thinks the revision answers `O` records that resolution, and F-5 labels it "self-resolved" where it applies. A revision never resolves anything by itself. Carrying and rebinding add a binding and remove none, so a decision that cited the earlier revision keeps showing `O` in its current projections, whatever later happens to `O`'s target (F-6). **Steps and relations** (same-family review F62-05): an inference step or evidence relation that names an earlier one through `supersedes` is a revision of it for this rule when it keeps the same conclusion (a step) or the same observation and targets (a relation), and objections on the earlier one are carried.

**F-3b — Withdrawing a target does not resolve its objections** (owner decision D-63; same-family review S62-1). When `tgt(O)` is retracted, withdrawn or deleted by its author with no successor revision, `O` stays unresolved, with the state "target withdrawn, not re-examined". It stays live and is shown on the target's withdrawal or deletion marker and on the page of every question in which the target was a position, until its author withdraws it, its author rebinds it to another record (for example a new claim that restates the target) of which its home is a possible home (architecture §5.11; otherwise the critic records a new objection there, citing this one; Gemini review R69-02), or a `resolution` decision under F-3 resolves it. A new decision may still cite the withdrawn record. Every projection of it then shows "cites a withdrawn record", and `O` joins its `A(D)` like any objection to a cited record (F-6; owner decision D-83; Codex review R64-03). Nothing is refused for it. A decision that cited the target before keeps showing `O` (F-3a, F-7). Whoever withdraws or deletes a target is first shown its unresolved objections.

**F-4 — Disputed resolution.** If an objection `O'` targets the resolution of `O`, then `O'` applies wherever `O` applied, and every projection that would have shown `O` shows "resolved by assessment, disputed" with both records. A resolution is **disputed** at a position while some objection that targets it is open for it (Definition 2.5); when every such dispute is withdrawn or resolved, it is no longer disputed, and views of earlier positions still show it disputed (F-31; Gemini review SC69-03). A dispute is never absorbed into the resolution's own record. Every dispute, at any depth, is an objection in `N(F)` and is covered by F-7a (Codex reviews SC66-01, SC67-01).

**F-5 — Self-resolution.** If the principal who resolved `O` is also the decider of a decision `D` whose basis `O` targeted, every projection of `D` labels the resolution "self-resolved". Whether self-resolution is permitted is SCIRE policy.

**F-6 — Applicability.** This rule is the one definition of which objections apply. Route status, standing, decision projections, mandatory lists, the late-objection delta and the coverage statement (F-7a) all cite it and none restates it (owner decisions D-85, D-86).

The **endpoints** `ends_q(R)` of a route `R` at position `q` are:
- for an evidence relation, its observation (the event and the observation claim), its conditioning model and condition, and every calibration, definition or model record it cites by identity;
- for an inference step, its premises and conditions;
- for either, every `renders` link and tool check that an assessment of `R` effective at `q` (Definition 6.0) cites in its basis (Codex review SC64-01).

The **reliance footprint** `F(X, I)` of a set of records `X` over an interval of positions `I` is the least set that contains `X`, contains `ends_q(R)` for every route `R` in it and every `q ∈ I`, and contains the original of every sharing copy in it (architecture §6.8). Its **objection neighbourhood** is

```text
N(F) = { O : bind(O) ∩ F ≠ ∅ }  ∪  { O' : O' disputes the resolution of some O ∈ N(F) }
```

An objection applies through every target in its history, with its current handling, resolution and mode, and each projection names the target through which it applies (D-94). Endpoints are not routes, so the footprint stays one hop from `X`. The closure over originals follows a chain of copies to its first original: a sharing copy is a rendering of its original (F-1), so objections to any original in the chain apply wherever a copy is relied on (owner decision D-86; Codex review SC65-01).

For a decision `D` with cited basis records `B(D)` (its basis claims and every record its basis statement cites by identity: premises, inference steps, evidence relations, applicability conditions), read at position `p`, the applicable set is

```text
A(D) = N(F(B(D), [commit(D), p]))
```

The interval only grows, so `A(D)` only grows, except by explicit deletion (architecture §12): replacing an assessment never removes an objection from a decision's set, and an objection recorded later against an endpoint the decision relied on at any time since its commit applies to it. Only resolving an objection changes what F-7 shows. Whether an assessment was effective at a position is computed from committed history (Definition 6.0), so the footprint is derived, never stored. For a claim revision `κ` read at `p`, `A(κ) = N(F({κ} ∪ routes(κ), [p, p]))`: a claim's own view shows the claim as it stands now. A route `R` is challenged at `p` when some `O ∈ N(F({R}, [p, p]))` is open in that view (Definition 2.5; §6.1).

`A(D)` is one hop from the basis, following re-review V4-06: the basis statement sets the coverage boundary, and omitting a material premise is a visible defect of the basis, not a way to escape objections. A front end may widen `A(D)`; nothing narrows it. Objections further upstream are reported on request with their coverage, as "upstream", and are not part of `A(D)`.

**F-7 — Travel.** Every `O ∈ A(D)` that is open in `D`'s view (Definition 2.5), and every override covering `D`, is part of every projection of `D`, an objection resolved at another record with the label of Definition 2.5 (Gemini reviews SC69-01, SC610-02). Objections settled for every record they apply through are not listed; they stay in `D`'s history, whatever `O`'s handling, mode (open, single-blind, double-blind) or archive placement.

**F-7a — Coverage of applicable objections** (owner decisions D-80, D-87, D-88; Codex reviews SC64-03, SC65-02). A projection shows only the objections its reader may read. It therefore states "objections you cannot read may apply" whenever the reader could miss one, over the same footprint as F-6 (`F(B(D), [commit(D), p])` for a decision, `F({κ} ∪ routes(κ), [p, p])` for a claim), that is, when the reader
- cannot read some record in the footprint;
- does not read every scope in which objections to some record in it may be homed, including homes whose registration was retired (architecture §5.11); or
- works in a task with a lineage exclusion (architecture §10.6.4).

Where the record is the original of a sharing copy, the statement reads "shared copy: objections to the original may not be visible to you". An objection carries no restriction tag of its own: a reader who reads its home and satisfies the restriction tags of the target through which it applies can read it (D-94). The statement must cover every objection in `N(F)`, including disputes of resolutions at any depth. Which homing rule makes the conditions above sufficient, and the proof that it does, belong to the architecture (architecture §5.11; D-94). A critic with sensitive material puts it in a separate restricted record and cites it, and that record shows as an unreadable source. Every condition depends only on the reader's access, the task and the scopes' configuration, never on whether such an objection exists, so the statement reveals nothing. The memory never grants access to an objection to complete a projection, and never refuses a change of access or a share because of one. Moving an objection to another target (a rebind) is refused unless every current reader of the new target can read the objection's home (D-88).

**F-8 — Anonymous objections.** An anonymous objection has the same semantics as any objection (F-3 to F-7): it is unresolved until resolved, it travels, and it is judged on its argument. Anonymity neither adds nor removes argumentative weight. That it never **blocks** a decision (D-36) is part of SCIRE's objection rule, not of its meaning; the memory records whether an objection was anonymous at each time, so the rule can be applied and audited. **D-36 is read narrowly (owner decision D-37; Codex review SC-TE04):** an anonymous objection is never a procedural veto, but an attributed judgment that independently establishes what it pointed out (for example, that a relied-on inference step is invalid) changes the route's status (§6.1) like any judgment, whoever supplied the lead. **SCIRE's objection rule (D-38)** requires a consequential decision's basis statement to address every objection in `A(D)` that is open in `D`'s view (Definition 2.5), anonymous or signed, which gives no objection a veto. Neither the existence of an objection nor its arrival after a decision was evaluated is ever grounds for the memory to refuse the decision; it is recorded and travels (F-7). A critic who later signs makes it a signed objection from then on; the earlier interval stays anonymous in history. **An anonymous participant never submits a judgment** (owner decision D-64; same-family review F62-02): anonymous-role sessions submit objections, critiques, questions and claims that are not about a person. **What an anonymous objection changes** (owner decision D-98, clarifying D-64; Codex cross-check SC-CC611-01): while it is open in a view, it marks routes `challenged` and sets the challenge predicates (§6.1, F-28) exactly as a signed objection does. It never supplies an assessment: whether a route is valid, invalid, usable or not usable, and a claim's epistemic status, change only through attributed judgments (Definition 2.8, D-37), so it alone never makes a route broken or a premise not established, and the memory refuses no decision because of it.

**F-9 — Claims about people are never anonymous** (D-32, D-33). A claim whose subject is a person's reliability, competence, conduct or motive is a signed, attributed claim, linked to any reply by the person judged.

**F-9a — De-attribution of derived statements (owner decision D-44; re-review V4-12 (iii)).** A person may ask that derived statements stop naming them: summaries, overviews, narratives, translations and statements extracted from others' records then refer to them by role ("a participant", "an author"). What de-attribution never changes: who authored each record (attribution is a recorded fact, F-20 and TE-11), the content of a claim another human signed, and the identity relations used for independence and conflict checks. A person who wants their own contribution gone asks for deletion instead, which leaves a withdrawal marker where others relied on it (candidate 6.21 §12.3). Complete erasure and permanent true attribution cannot both be promised; this rule keeps attribution and limits repetition. **It is presentational:** anyone who may open the underlying record sees its author one step away, and the requester is told so. **Accountability renderings are exempt** (same-family review R-15): who decided, signed or resolved a decision, which curator deleted a record (the marker), which administrator read a scope in administrator mode, and which review chair blocked a message are always named, since F-1 and the dissent guarantees depend on them.

### 4.3 Decisions (normative)

**F-10 — Exposure.** A decision's exposure is evidence about the decision process, never about the science. It identifies the record revisions and the as-of position of each view shown.

**F-11 — Joint sign-off binds content.** A signature binds one exact decision revision. Any change to the decision content creates a new revision on which earlier signatures do not count (re-review V4-20a).

**F-12 — A decision is not support.** A decision that makes a position "current" for a purpose never adds evidential or inferential support to it. Its dissent and applicable objections appear with it (F-7).

---

## 5. Evidence semantics

### 5.1 Relation kinds (normative)

**Definition 5.1.** `k` is one of:
- `entails(κ)` or `refutes(κ)`: deductive, under stated hypotheses;
- `favors(A over B | m)`: comparative, under model `m`, with `A ≠ B`;
- `adequate(κ, purpose)` or `inadequate(κ, purpose)`: absolute, under stated criteria;
- `prediction-succeeded(P)` or `prediction-failed(P)`: for an explicit `predicted` claim `P`;
- `consistent-with(κ)`: the observation does not discriminate `κ` from the other live positions;
- `bears-on(κ), unassessed`.

**Targets** (owner decision D-89; Codex review R65-01). `T` is exactly the claims the kind names: `{A, B}` for `favors`, and the one claim for every other kind. A comparison among three or more alternatives is recorded as separate `favors` relations, one for each pair the assessor compares. A relation whose targets do not match its kind is refused when it is recorded. No bearing is ever assigned by default, so the bearing of §6.1 is defined for every target of every relation.

**F-13.** Comparative and absolute relations are recorded separately: `favors(A over B)` together with `inadequate(A)` and `inadequate(B)` is consistent. No relation implies another kind.

**F-14.** Reassessment adds a judgment on `E`; it never rewrites `o` or an earlier judgment.

### 5.2 Use history and warrant

**Definition 5.2.** The use history `U(E)` is a chronological, non-exclusive sequence of entries `(dataset, subset, analysis revision, use, breadth, leakage, coverage)`, where `use ∈ {suggested, fitted, selected, tested-pre-specified, model-check, not-applicable}`, `breadth` records the variants tried, `leakage` records known shared dependence, and `coverage` marks intervals where the history is unknown.

**Definition 5.3 — Independent test and independent confirmation** (Codex review SC67-02). `E` is an *independent test* of `κ` within coverage `Γ` only when `κ ∈ T` is a target revision that `E` binds (Definitions 2.6, 5.1; Codex cross-check SC-CC611-02), and then if and only if
1. no entry of `U(E)` within `Γ` has `use ∈ {suggested, fitted, selected}` for `κ` or an ancestor revision of `κ`;
2. the provenance of `o` and of the data that suggested, fitted or selected `κ` (their sources, instruments, code and populations) is recorded within `Γ` and shows no shared leakage, instrument, code or population dependence between them; missing provenance leaves the label not established (F-19; Codex review SC68-03);
3. `Γ` is stated, and an unknown interval inside `Γ` falsifies the label.

An independent test is shown with its kind and bearing (§6.1), whatever they are: a failed prediction can be an independent test. `E` is an *independent confirmation* of `κ` within `Γ` only if, in addition, its kind is `entails(κ)` or `prediction-succeeded(κ)` and it has an effective positive assessment (Definition 6.0) under the reader's `(σ, ρ)`. Relative support (`favors`) and adequacy for a purpose are qualified conclusions and are never called confirmation. For a claim that is not one of `E`'s targets, `E` is neither, whatever its use history. The labels are narrow. Uses that fail them can still carry evidential value; they are not called independent tests or confirmations.

**F-15 — Inference-specific warrant.** What `E` justifies is decided by the warrant its assessor names (for example, a selection-adjusted analysis under its assumptions, or a proof under its hypotheses and checking basis). Use-history roles may be `not-applicable` for proofs.

### 5.3 Origin, qualification, usability

**F-16.** `ω`, `q` and `ν` are recorded separately. `ω(o)` never implies `q(o)`: an external-system run may be unqualified, failed or provisional.

**F-17 — Uninstrumented observations.** If `ω(o) = uninstrumented`, `o` is carried with that label until *upgraded*: its material inputs, conditions and regime are recovered and its admissibility assessed. Re-entering the same number elsewhere is not an upgrade (re-review V4-12 (ii), restored). A finalization or outcome decision whose evidential routes, followed from its basis claims, all rest only on uninstrumented observations is **labeled** "sole uninstrumented backing" on every projection, however the routes are cited. Whether such a decision may proceed is SCIRE's finalization rule, which must not let it pass unlabeled; the memory labels and does not refuse (same-family review R-07).

**F-18 — Snapshots of external results.** A retained snapshot of an external result (for example from SSDS) is evidence of the value at the cited revision. Its qualification is "as of the snapshot; later changes unknown", and a claim relying on it states this (re-review V4-13).

### 5.4 Independence

**Definition 5.4.** An *independence claim* between two lines of evidence states the dimensions in which they are independent (data, method, instrument or code, model, analyst, model family, prompt, retrieved sources) and a coverage statement.

**F-19.** Missing provenance never establishes independence. Unknown authorship is never treated as independent (from SSDS). Copies of one source are one source. Several agents agreeing from shared inputs are one line of evidence for counting, though each argument stays inspectable.

**F-20 — Identity relations, not attributes.** Who did an analysis enters assessment **only** through identity relations: same principal or not, declared collaboration, declared conflict of interest, and, for conflict checks only, same sealed author. Using these to count independence, or to check a reviewer's conflict, is not judging a person. No attribute or aggregate of a person (§7.3) enters any assessment. **Roles under a project rule** (a decider's authority basis, Definition 2.10; a designated verifier, mathematics Definition M.11) are recorded acts of the project, not labels the memory assigns. They enter computed status only as membership, and are never inferred, ranked or aggregated (same-family review FM-R12).

**F-20a — Independence never depends on a sealed identity** (Codex review TE-R13). For the analyst dimension of independence, two lines of evidence count as independent only when both are attributed to different principals, or both are anonymous under different pseudonyms in the same review. For every other pair, including an anonymous record and a signed one, or anonymous records in different reviews, analyst independence is **not established**, whatever the sealed truth. The rule is the same for every such pair, so applying it reveals nothing about who wrote what; its cost is that an anonymous critic's agreement never counts as independent of an attributed line. This is F-19 applied to authorship the reader may not know. What else a released result may depend on is stated once, in architecture annex §7.8 (owner decision D-79). An authenticated account is not proof of a unique human, so independence by principal or pseudonym is bounded by the identity provider's assurance.

### 5.5 Applicability over time

**F-21 — Staleness.** `E` binds the claim revision, regime and method it assessed (`b`). When `κ` is revised to `κ'`, `E` is **under review** for `κ'` and does not carry over silently. A stale failing observation is not admissible evidence against `κ'`, and a stale passing one is not admissible confirmation of `κ'` (from SSDS).

### 5.6 Tension kinds

**Definition 5.5.** A tension between records is one of:
- **logical contradiction:** two statements cannot both hold under the same premises;
- **statistical disagreement:** observations of the same estimand differ by more than a **declared comparison model** makes plausible under a **declared decision rule**;
- **failed prediction:** an observation differs from what a `predicted` claim says in the conditions it covers;
- **not comparable for this target:** the compared quantities answer different questions, relative to a stated target claim (§5.7);
- **unexpected observation:** against expectation, not against a statement;
- **data error,** including unit and definition errors;
- **incommensurable models:** the frameworks define the compared quantity differently.

**F-22.** A statistical disagreement is never called a logical contradiction. Without a declared comparison model and decision rule there is no statistical disagreement, only a cue that values differ (§9, D2 hand-off).

**F-23 — Regime as the test.** If a claim asserts invariance across regimes, a difference between regimes is the test, not a reconciliation. A claim's coverage is recorded so that narrowing the framing cannot hide a mismatch (SCIRE §5.3, subgroup example).

**F-24 — No automatic reconciliation.** Pooled means with inflated errors presuppose a shared estimand; stratification by a variable affected by cause and outcome can create bias; a parameter fitted to the same data is not independent confirmation. Each is a claim needing its own justification.

### 5.7 Comparability

**Definition 5.6.** A *comparability assessment* is a judgment relative to a target claim. It names: the target claim and the population, regime and quantity it is about; the compared quantities, their estimand definitions, units and conventions; what the target predicts about change or invariance between the compared conditions; the uncertainty, the comparison model and known shared dependencies. Completing it does not settle the question.

### 5.8 Warrants

**F-25 — Warrants, not actors.** Support that is circular, or that reaches neither an applicable root in events nor a valid argument with no premises left to establish, is not a warrant, whoever produced it; support rooted only in a valid argument holds under that argument's carried conditions and is labeled so (owner decision D-100). Shared roots are not new independent evidence. A flag, a view, a narrative, a retrieval rank or a recommendation is never evidence. A machine proof checker can supply a valid check under named assumptions; a human's insertion does not validate a circular warrant. How a basis reaches a root (Definition 6.2), what a basis that cites nothing means, and when support is circular are defined in §6.1 (owner decisions D-99, D-100).

**F-26 — Discovery is not support.** `arose_from` is never traversed as support.

### 5.9 Meaning

**F-27.** Curating a vocabulary label is indexing; it asserts no scientific equivalence. Scientific equivalence is a meaning link (Definition 2.12). A label may be recorded as **contested**, and statements using it are then compared only within the meaning each statement declares. A change of meaning creates review obligations, never truth changes.

---

## 6. Standing

### 6.1 Route status

For a claim revision `κ`, a *route* is one evidence relation `E` with `κ ∈ T`, or one inference step `S` with conclusion `κ`. Each route has a status computed from recorded judgments, objections and obligations:

**Definition 6.0 — Effective judgment** (same-family review SC-R2). A scientific judgment `J` of a target under `(σ, ρ)` is *effective* at position `p` if and only if
1. `J` is a head of its `(target, σ, ρ)` lineage at `p`; only `J`'s own assessor can supersede it, so heads by different assessors coexist (Definition 2.8);
2. `p` lies inside `J`'s validity interval, which is unbounded unless `J` states one;
3. the target revision `J` binds is current at `p` (otherwise the route is under review, F-21), and every evidence revision `J`'s basis cites is current and not retracted, corrected or deleted;
4. no review obligation is pending on the target;
5. `J`'s basis cites no flag, hub, narrative, projection, standing report, recommendation, source assessment or other judgment (D-39 defers judgment on judgment). Having been **shown** such a view is recorded as exposure and does not by itself make `J` ineffective;
6. `ρ` is a ruleset registered for the scope at `p`. `ρ` names a ruleset identity and version: a new version is a new `ρ`, unless its registration states that it continues the previous version, in which case judgments under the previous version stay effective (same-family review F62-06 b);
7. `J`'s assessor is attributed, not sealed (D-64).

No wall-clock age applies unless `ρ` states one, and activity elsewhere in the scope does not affect effectiveness. This is a definition for scientific standing only; the currentness rule for project-memory facts is the architecture's and is unchanged. A judgment that exists but is not effective is never ignored: the route shows it, with the condition that fails. Each judgment is also labeled with whether its assessor had been shown prior assessments or the standing of the same target (its recorded exposure), so a reader can see where an assessment may echo an earlier one (F62-06 c).

**Positive and negative** (same-family review S62-3). An inference assessment is positive when it finds the step valid under its conditions and negative when it finds it invalid. An evidential assessment is positive at `usable` or `usable-with-limits` (the limits are listed with the route), negative at `not-usable`, and neither at `under-review`, which puts the route under review. A claim assessment is positive at `supported` or `supported-under(c)`, negative at `refuted` or `disfavored-under(c)`, and neither at `contested` or `unknown`.

**Direction** (owner decision D-81; Codex review R64-01). Positive and negative say whether a route is valid or usable, not which way it bears. The **bearing** of a route on `κ` is fixed by its kind:
- **supports:** an inference step concluding `κ`; `entails(κ)`; `prediction-succeeded(κ)`;
- **supports relative to an alternative:** `favors(κ over B | m)`, always shown with `B` and `m`;
- **adequate for a purpose:** `adequate(κ, purpose)`, always shown with the purpose;
- **adverse:** `refutes(κ)`, `prediction-failed(κ)`, `inadequate(κ, purpose)`, `favors(A over κ | m)`;
- **neutral:** `consistent-with(κ)`, `bears-on(κ), unassessed`.

The first three are **supporting** bearings. A usable adverse or neutral route is reported as a usable route of its own kind and never as support (F-28).

**Premises** (owner decisions D-69 and D-70; same-family review F62-03, F62-04). The premises of a step are its premise claims other than hypotheses discharged for its conclusion and its carried conditions (Definition 2.7; D-70 to D-72). A route through the step is at most supported under its carried conditions, and the standing report lists them with every discharge and the step that discharged it. A carried condition is never shown as established, and never silently dropped. A step's **context** is its stated conditions (`c` in Definition 2.7), the carried conditions of its conclusion, and the hypotheses it discharges: inside the step a hypothesis it discharges is an assumption in force, and beyond it the hypothesis no longer applies (D-70, D-72; Codex review SC614-01). Whatever serves a step, a premise's judgment or a step in a premise's root witness, is checked against the step's context. A premise is **established** for the route when it is rooted (Definition 6.2, below), which needs an effective judgment of it with status `supported`, or `supported-under(c')` with `c'` **compatible** with the step's context. Compatibility is established only when `c'` and the step's context cite the same condition record by identity, or an effective comparability judgment (§5.7) states that `c'` covers the step's context and no other effective comparability judgment under the same `(σ, ρ)` states that it does not. While two effective comparability judgments disagree, the premise shows "compatibility disputed" with both, and neither is chosen, by recency, count or order (owner decision D-82; Codex review R64-02). Otherwise the premise shows "compatibility not established". A premise's judgment counts under the premise's home scope when that scope and the reader's scope register the same ruleset identity; otherwise the premise shows "assessed under another ruleset". The reader's scope is the claim's home scope unless the reader names another, and the report names the scope and ruleset under which each premise was judged.

**Roots and eligible support** (owner decisions D-99 and D-100; F-25). A *supporting judgment* of a claim `Y` **for** an inference step `R` that has `Y` as a premise is an effective claim assessment of `Y` that could establish it for `R` by the rules above: status `supported`, or `supported-under(c')` with `c'` compatible with `R`'s context, counted under the ruleset rule. Its basis may cite routes of `Y` and retained events; a supporting judgment whose basis cites neither is **rootless** and is shown with the premise. Two kinds of record can end a chain of support:
- a **terminal basis**: a cited event that is applicable (condition 3 of Definition 6.0), with the part of it the judgment checked named, for example a span of its payload; or a cited evidence relation whose observation is applicable and which has no effective negative evidential assessment (D-99, D-100);
- a **valid argument**: an inference step that is valid for the step it supports (below) and has no premises left to establish once discharged hypotheses and carried conditions are set aside (D-70, D-71, D-100).

An inference step `R'` is **valid for** `R` when it has an effective positive inference assessment and no effective negative one, counted under the ruleset rule applied to `R'`'s home scope, and each of its stated conditions and the carried conditions of its conclusion is compatible with `R`'s context by the compatibility rule above; the hypotheses `R'` itself discharges are not among them. A step nobody has assessed, a step judged invalid and a disputed step are valid for no step. Because each step of a chain must meet the context of the step it supports, a condition carried in a chain reaches the route's own step unless a step on the way discharges it; a hypothesis used on a branch that bypasses the discharging step stays a carried condition of the conclusion (Definition 2.7, D-72), so it still reaches that step (D-100; Codex review SC614-01).

**Definition 6.2 — Root witness** (owner decision D-100; Codex review SC613-01). A *root witness* of `Y` for `R`, avoiding a set of claims `X`, at `p`, is a finite tree over the records committed at `p`: `Y ∉ X`, and some supporting judgment of `Y` for `R` cites either a terminal basis, which ends the branch, or an inference step `R'` concluding `Y` that is valid for `R`, with a root witness of each premise of `R'` for `R'` avoiding `X`; a valid argument has no premises left, so it ends the branch. `Y` is **rooted for `R` avoiding `X`** when it has a root witness. A rooted claim is **event-rooted** when some root witness of it ends only at terminal bases; otherwise it is shown **"rooted in a valid argument, not in an event"** wherever it is shown as established.

Because a witness is finite, a support cycle with no exit roots nothing; because each branch passes only through supporting judgments and steps valid for the step they serve, a rootless or ineligible judgment (under incompatible conditions, or another ruleset) and an unassessed, invalid or disputed step never count at any depth. A witness is found by one traversal of cited records, never from projected standing. A premise `P` of a step `S` with conclusion `κ` is
- **rooted** when it is rooted for `S` avoiding `{κ}`;
- **circular** when it is not rooted and **reaches** `κ` for `S`, where a claim `Y` reaches `κ` for a step `R` when `Y` is `κ` (Codex review R613-01), or some supporting judgment of `Y` for `R` cites an inference step `R'` one of whose premises reaches `κ` for `R'`; an actual dependence on `κ` then exists and nothing roots `P` without it;
- **without a root** otherwise.

A premise is established only when it is rooted. A premise without a root is not established and never circular: the route shows "premises not established", with "rootless" when the premise's supporting judgments cite nothing and "no root reached" otherwise. Reaching follows every step a supporting judgment cites, assessed or not, because dependence is a fact about what a judgment relied on; only rooting asks for validity. A rootless judgment reaches nothing.

**What rooting certifies** (Codex review of 1.13, §4.5). Each premise of an assessed-sound inference route has a root witness every step of which was assessed valid, with no effective assessment finding it invalid, and every end of which is a terminal basis or a valid argument. It does not certify that every other recorded support of the premise is valid, and an open objection to a step inside a witness does not take the step out of it (D-98: objections change challenge state, not assessments). Both are shown one level down, where the report is exact to its depth (F-30).

| Route status | Condition |
| --- | --- |
| **unassessed** | no evidential or inference assessment of the route under the reader's `(σ, ρ)` |
| **assessed, not effective** | assessments exist, none is effective; each is listed with the condition of Definition 6.0 it fails |
| **under review** | a pending review obligation exists on the route, or the route binds an earlier revision of `κ` (F-21) |
| **challenged** | some objection in `N(F({R}, [p, p]))` (F-6) is open in the route's view (Definition 2.5) |
| **disputed** | effective positive and effective negative assessments of the route coexist; both are listed, and neither is chosen |
| **premises not established** | the route has an effective positive assessment and some premise is not established; each such premise is listed with its status, or "unassessed", "rootless", "no root reached", "compatibility not established", "compatibility disputed" or "assessed under another ruleset" |
| **broken** | the route has at least one effective assessment and every effective assessment of it is negative (Codex review SC612-03) (step invalid; observation not usable for this use); or a premise is retracted, superseded, or has an effective negative judgment that applies to the step's conditions; or the route is circular (Well-foundedness below; F-25) |
| **assessed-sound** | some effective assessment of the route is positive and none is negative, every premise is established, no effective negative judgment applies to a premise, and none of the above holds; it is sound under its carried conditions, which are listed, and is shown "rooted in a valid argument, not in an event" when it is an inference step with no premises left to establish or some premise of it is rooted only in a valid argument (D-100) |

Every route meets at least one condition. Several can hold; the report lists all of them, and the table order is used only to choose a one-word label.

**Well-foundedness** (Codex review SC-TE01, TE-R11). Route status depends on premises only through their own **effective judgments** (Definition 6.0), never through their projected standing, so it is computed in one pass, with no fixed point over standing. **Circularity is judged per derivation, by actual dependence** (same-family review R-02; owner decisions D-99 and D-100): an inference step `S` is **circular** when some premise of it is circular (Definition 6.2 and the premise classes after it). One root witness avoiding `κ` keeps a premise from being circular, so a third party's converse step cannot break a well-founded route, and nothing that cannot root a premise clears its dependence on `κ`. An empty basis is never a cycle. A circular route gives no positive warrant; a recursive definition (modality `defined`) or a proof by induction is not a support cycle. Negative information counts: an added adverse judgment or objection changes a route's status even when no cited revision changed. Ordinal statuses are never multiplied, averaged or voted on.

### 6.2 Standing report (normative)

**Definition 6.1.** The *standing* of `κ` for a reader at position `p` is the report

```text
standing(κ, p) = { judgments of κ per (σ, ρ), with status;
                   routes of κ, each with its status, bearing and its own standing one level down;
                   A(κ) (F-6), with state and mode, and the coverage statement of F-7a;
                   review obligations on κ and its routes;
                   source assessments of the works κ rests on;
                   decisions that rely on κ, with dissent;
                   coverage: what the reader may not read, what is unprocessed,
                             and where traversal stopped }
```

computed over the exact revisions committed at `p` that the reader may read.

**F-28 — Status, not winners.** `standing` contains no aggregate verdict, score or ranking of alternatives. Three derived predicates are defined exactly, for front ends to use (owner decision D-81):

```text
has-sound-support(κ)       ⇔  some route of κ with a supporting bearing (§6.1) is assessed-sound
                               and no O ∈ A(κ) is open in κ's view (Definition 2.5)
has-sound-adverse-route(κ) ⇔  some route of κ with an adverse bearing is assessed-sound
has-open-challenge(κ)      ⇔  some O ∈ A(κ) is open in κ's view
```

Each true predicate is shown with the routes that make it true and their qualifiers: the alternative and model of a relative support, the purpose of an adequacy, the carried conditions, and "rooted in a valid argument, not in an event" where it applies (D-100). What a sound route certifies about its premises is stated in §6.1 (What rooting certifies). Both of the first two can hold at once, and neither cancels the other (P7).

Standing never merges kinds of assessment that SCIRE v0.4 §5.4 keeps apart: qualitative plausibility, evidential bearing, inferential validity, model adequacy, quantitative probability, participant judgment and decision each stay in their own records and labels.

A position is shown as "current" only where a recorded decision makes it so (F-12).

**F-29 — Projection, not admission.** Propagating standing from premises to conclusions is computed at read time over exact revisions and is recomputed when an input changes. No stored judgment is created or changed by propagation.

**F-30 — Depth and coverage.** The report is exact to the depth it is computed. Where the traversal is bounded, the bound is part of `coverage`, and nothing beyond it is reported as sound or as absent.

### 6.3 History

**F-31.** Two reads are answerable and distinct:
- **as held then** at record position `t`: the records and standing as committed by `t`, evaluated under the rules and the projection version in force at `t` (from SSDS: historical decisions are never recomputed under newer rules; same-family review R-03);
- **as now assessed about then:** current assessments of records dated before `t`.

A later correction is never reported as what was held earlier. The memory never invents when somebody learned something. Where explicit deletion or a restore from backup removed records (candidate 6.21 §12), "as held then" is incomplete and says so, naming the interval a restore may have lost (re-review V4-20c; owner decision D-65).

### 6.4 Retraction and review obligations

**F-32 — Creation.** When a source is retracted or corrected, found inapplicable, or has a definition changed, or a claim is revised, or a rendering is judged to diverge from what it renders (which makes every tool check of that rendering inapplicable as evidence for it; owner decision D-74), a deterministic traversal of the provenance, evidential, inferential and meaning-link graphs within stated coverage creates a review obligation on each dependent route and claim, with an assignee.

**F-33 — Present eligibility.** While an obligation on a route is pending, the route is under review (§6.1) and cannot newly back a consequential use unless an explicit qualification is recorded. That qualification travels like an override (F-7).

**F-34 — Closure.** An obligation closes **only** through an attributed reassessment of the route's usability. Assigning, acknowledging, archiving or answering it does not close it (re-review V4-07).

**F-35 — No truth propagation.** Retraction, revision and definition change never make anything true or false. Past decisions are flagged, never undone.

### 6.5 Judgment on judgment (deferred, owner decision D-39)

A judgment whose basis cites another judgment is not effective (Definition 6.0, condition 5) and is shown as an assessment that is not effective. The proposed contract for admitting such judgments, with dependency modes and `current`-only reliance, is candidate 1.1 §6.5 (SHA-256 `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d`); it is to be revisited only if the Slice 2 demonstration shows assessors need it.

---

## 7. Source assessment

### 7.1 Meaning

**Definition 7.1.** A *source assessment* is a judgment about a **work** (or, once channel assessment is built under D-45, a non-person channel) as an evidence channel **for a kind of claim**. Its value is ordinal:

```text
established > generally-reliable > mixed > unreliable,  plus  unknown (unordered)
```

It is never a probability or a calibrated quantity. Its recorded basis is: provenance class and channel integrity; for non-person channels only, track record (Definition 7.2); retractions and corrections; declared conflicts of interest; known shared dependencies.

**Definition 7.2 — Track record** (non-person channels only; deferred with channel assessment, owner decision D-45): in Appendix B.

**F-36 — Assessment, not computation.** A source assessment is made by an attributed assessor, who states how the basis yields the ordinal value. No rule maps counts to a value automatically in this formulation. An automatic mapping, a numeric score or calibration reopens D2 (§9).

**F-37 — Limited use.** A source assessment may order retrieval and fact-checking work. It never sets a claim's standing alone and never hides a claim.

**Realization note.** Owner decision D-45 defers assessments of non-person channels and their track records to a later slice, built only if measured need justifies their proxy risk (candidate 6.21 §9.13). Their meanings are kept in Appendix B so they are not reviewed as current text; deferring them changes no meaning.

### 7.2 Guards

**F-38 — No reward for agreement.** Disagreeing with the prevailing theory is never a mark against a source; only outcomes assessed independently of the source and of the claim's own position count (Definition 7.2).

**F-39 — No person-level output** (D-32). For any person `π`, no score, rank, rating, track record, tendency, outcome count or label is computed, stored or shown. Authorship is never an input to a work's assessment, to a source assessment or to retrieval ranking. No view aggregates works by author to compare or characterize authors, and no view lists a person's works together with their assessment values; a work's assessment appears when that work is opened (same-family review R-17). A reader who opens a person's works one by one can still compile them; that residual is stated. A work never borrows standing, good or bad, from its author's other work. F-20's identity relations are the only use of authorship in assessment.

**F-40 — Humans judge people, accountably.** A judgment of a person exists only as a signed human claim (F-9), linked to the person's replies. It never feeds any assessment or ranking, is never surfaced proactively and is never repeated by an agent as its own view.

**F-41 — Proxies.** Institutions, groups and venues are persons for F-39. A channel must be a technical production or measurement mechanism with its own error behavior; a collection defined by authorship or affiliation (one researcher's papers, a lab's outputs, a venue's articles) is not a channel (Codex review TE-R12). An agent principal is a channel (a model family as a technical system), not a person; its assessment must not serve as a proxy for its human overseer.

**F-41a — Track-record coverage:** deferred with channel assessment, in Appendix B.

**F-42 — Conflicts of interest** are facts about the work they concern, never judgments of a person.

---

## 8. Assumptions, limitations and uncertainty

### 8.1 Assumptions

- **A-1:** Attribution is authentic within the deployment's trust boundary (candidate 6.21 §7). If attribution can be forged, every F-rule that names an author fails.
- **A-2:** Assessors state their warrant and basis. The memory cannot make an assessor honest; it makes the assessor's basis inspectable.
- **A-3:** The front end records basis statements that cite records by identity. F-6 is only as strong as those citations.
- **A-4:** Use history is reported by people and agents. Unknown intervals are recorded as unknown, never as "no use".

### 8.2 Limitations

- Truth-based robustness (proposal §8.3) resists planted falsehoods only where independent, well-supported evidence exists. A plausible fabrication in a sparsely evidenced area is resisted weakly. Instruction injection and disclosure are not truth problems and are not addressed by this formulation.
- Internal consistency of natural-language arguments is mostly not checkable deterministically; it is flagged for human review.
- Blinding is best effort: style, self-citation and timing can identify authors.
- **The existence of an objection is not promised confidential** (owner decision D-92; Codex review R67-01). No mechanism beyond the ordinary access rules hides an objection's existence, time or unrestricted ground from a target's readers; those rules still decide what each reader actually receives, and F-7a's statement covers what they withhold. Objections whose existence must stay hidden from a target's readers are outside this formulation.

### 8.3 Uncertainty semantics

- Model-stated percentages are not calibrated probabilities and are never stored as such.
- Uncertainty attached to an observation (`u`) is recorded as stated, with its type (standard uncertainty, interval, distribution reference). Its use in comparison is a D2 matter (§9).
- Standing is ordinal and structural. Its uncertainty is expressed by coverage (what was not read, not processed, not traversed) and by conditions on status, never by a number.

---

## 9. D1 → D2 hand-off

D2 is **opened for retrieval only**, by owner decisions D-101 to D-120: memory designed for any size storage permits, answers whose exactness rests on a pruning guarantee, measured translation error, asymmetric evaluation and latency targets put requirements on error and cost models (§16). The D2 retrieval method candidate 1.3 (`UPMS_Retrieval_Method_D2_Candidate_1_3.md`) owns them. Every other item stays as it was: no numeric method is used for theory–evidence meanings.

| Item | D1 constraint handed to D2 | Until D2 is accepted |
| --- | --- | --- |
| Pruning guarantee (F-44) | A step that skips part of a population never skips an item that satisfies the plan; the guarantee holds per predicate, version and published state | No step skips any part of the population except by a mandatory filter; execution is reported incomplete where a part was not evaluated |
| Error of translation (F-43, F-50, F-51) | Extraction, resolution and plan compilation have measured error per field type and per kind of mention, against held-out references; processing extent is never offered as recall | Every interpretation-only match is labeled; no error rate is claimed |
| Evaluation of answers (F-46, F-48) | Confident wrong answers cost more than abstentions, and a useful-answer floor and cost limits set by the owner keep abstention from winning by default (D-111, D-120) | No quality claim is made beyond the coverage of each answer |
| Cost and latency (F-49) | Cost is estimated before a search and capped while it runs; latency is measured by component | Budgets are the profile's caps; an exhausted budget is reported |
| Operational estimates | Estimates of runtime, cost or yield have their own defined meaning; they are never probabilities of a claim's truth and never stored on claims | Not used except as the profile's caps |
| Statistical disagreement (F-22) | A disagreement candidate is defined only relative to a declared comparison model and decision rule, with the estimand, uncertainty type and independence assumptions named | The evidence–evidence channel emits only unit, definition and "values differ, no comparison model" cues |
| Prediction check | Whether an observation falls outside what a typed prediction allows needs a stated tolerance or model | The evidence–theory channel emits "prediction check" flags only for exact typed values and stated intervals, and "not covered" cues |
| Any numeric score, calibrated confidence, automatic source-assessment mapping | Must preserve F-36 to F-42 and P8 | Not permitted; the D2 retrieval candidate does not open it |
| Small-model and embedding candidates | Propose only; never decide (F-44) | No D2 needed for proposing (candidate 5 §1.4 trigger 3 stays closed) |

---

## 10. External adequacy and falsification

### 10.1 What would show this formulation adequate

The formulation is adequate if real readers, using its records, recover status, dissent, support, independence and history more faithfully than with an archive plus search, at acceptable cost. The proposal's experiments test this:
- **E1 (status and dissent loss),** **E2 (orientation)** and **E4 (elicitation cost)** from SCIRE v0.4, run on UPMS records;
- **E5 (standing faithfulness),** new: given real histories, does `standing` and the understanding section report status, dissent and retractions more faithfully, and at what reader cost?

The owner sets error and cost limits before each study. No experiment has been run; nothing here claims adequacy.

### 10.2 What would falsify or reopen it

- A trajectory in which a reader, following F-1 to F-42, is shown a disputed resolution as settled, an interpretation as an assertion, a fitted observation as independent confirmation, a stale relation as current, or a person characterized by the system.
- A trajectory in which F-6's one-hop boundary systematically hides material objections despite complete basis statements.
- E5 showing that `standing` misleads readers more than an archive plus search.
- E1, E4 or E5 showing that the coverage statement of F-7a is shown so often that readers stop reading it.
- A need for calibrated probability, automatic source scoring or person-level outputs. The last is excluded by D-32 and would need the owner.

### 10.3 Stress cases carried from the SCIRE reviews

Each must fail as intended against this formulation:
1. Acknowledge and defer, then finalize: fails by F-7.
2. Resolve, dispute, then finalize: fails by F-3, F-4 and F-7 (SC-41).
3. Retract a source, acknowledge the obligation, then rely: fails by F-34 (V4-07).
4. Fitted data presented as confirmation: fails by Definition 5.3, test and confirmation alike.
5. Two agents agree from shared inputs: one line of evidence (F-19).
6. Constant-across-regimes claim against regime-varying data: a failed prediction, not a reconciliation (F-23).
7. A dissenting source down-ranked for disagreeing: fails by F-38.
8. A narrative that drops the live alternative: the mandatory list still shows it; the omission flag is only a cue (candidate 6.21 §10.5.1, and §10.5.3 in its Slice 4 annex).
9. Retract a claim with an unresolved objection, restate it as a new claim, then finalize: the objection stays on the withdrawn target and on the question page (F-3b; S62-1).
10. A second assessor supersedes the first assessor's positive judgment to turn "disputed" into "broken": not possible; both stay heads (Definition 2.8; F62-01).
11. An anonymous participant records an invalidity judgment: refused (F-8; D-64).
12. A valid step on a premise nobody has assessed: "premises not established", never "assessed-sound" or "unassessed" (§6.1; S62-3).
13. A derivation from a model's defining relations, with one open assumption: sound under "within the model, assuming h", never "premises not established" and never sound without the conditions (D-71; SM-2).
14. A hypothesis used on a side branch that bypasses the discharging step: still a carried condition of the conclusion (D-72; SM-3).
15. A step backed by a passed tool check whose rendering is then judged to diverge: the route goes under review (F-32, D-74; SM-1).
16. A decision cites only a step; an objection targets the tool check the step's assessment cites: the objection is in `A(D)` and travels (F-6; SC64-01).
17. A usable `refutes(κ)` relation and no other route: `has-sound-adverse-route(κ)`, never `has-sound-support(κ)` (F-28; R64-01).
18. Two assessors disagree on whether a premise's condition covers the step's: "compatibility disputed", never "assessed-sound" (§6.1; R64-02).
19. The target's author loses access to the scope that homes an objection to their claim: their view of the claim says objections they cannot read may apply (F-7a; SC64-03).
20. A decision relies on a step whose assessment cites tool check `T`; the assessment is replaced by one that does not cite `T`; an objection to `T` recorded before or after the replacement is in `A(D)` and is never dropped (F-6; SC65-01).
21. `K` is shared as `C1`, `C1` as `C2`, and a decision cites `C2`: `K`'s objection is in `A(D)` (F-6; SC65-01).
22. The reader reads the basis and every home of its objections, and a cited tool check only through an own-record entitlement: the decision's view carries the coverage statement, whether or not an objection to the tool check exists (F-7a; SC65-02).
23. An objection narrowed by a restriction tag of its own: not possible; it is read under its target's tags, and sensitive grounds go in a cited restricted record (F-7a; D-87).
24. A `favors` relation with three targets: refused; three pairwise relations give each alternative its bearing (Definition 5.1; R65-01).
25. A resolution of an objection to `K` is recorded in a scope that is not a possible home of `K`'s objections, and disputed there: not possible; it is homed among `K`'s possible homes, so a reader who could miss the dispute gets the coverage statement (F-4, F-7a; SC66-01).
26. An objection to `K1` is carried to `K2` and rebound to it: a decision that cited `K1` keeps it, a decision citing `K2` has it; a resolution that assessed `K2` closes it on both, the first decision says "resolved by assessment at `K2`, not assessed for `K1`", and `has-sound-support(K1)` stays false (Definition 2.5, F-3a, F-6, F-28; SC66-02, SC69-02; D-94, D-97).
27. A review scope tries to register an objection home of its own: refused, so a chain of disputes stays in its objection's home, and a reader who cannot read that home gets the coverage statement (F-7a; SC67-01, SC68-02; D-94).
28. An independent, pre-specified prediction fails: an independent test with adverse bearing, never an independent confirmation (Definition 5.3; SC67-02).
29. An observation whose instrument and code provenance is not recorded tests a pre-specified prediction, which succeeds: neither an independent test nor an independent confirmation (Definition 5.3, F-19; SC68-03).
30. A dispute of a resolution is withdrawn by its author: the resolution is no longer disputed, and a view of a position before the withdrawal still shows it disputed (F-4; SC69-03).
31. A dispute of a resolution is resolved by a decision whose judgment assessed that resolution: the dispute is settled, the resolution is no longer disputed, and the claim the original objection targeted is no longer challenged by either (Definition 2.5, F-4; SC610-01).
32. An anonymous objection targets an inference step that a sound route consists of, and no judgment changes: the route is `challenged` and `has-open-challenge` holds at once, its assessment stays positive, and no decision is refused (Codex review R612-01); after an attributed judgment finds the step invalid, the route is broken through that judgment (F-8; D-98; SC-CC611-01).
33. A premise whose only supporting judgment cites a retained event directly, naming the span checked: established, and the step concluding from it is not circular (§6.1; D-99; SC-CC611-03).
34. A premise whose only supporting judgment cites nothing: rootless, so the premise is not established and the route shows "premises not established", never circular or broken (§6.1, F-25; D-99).
35. A premise supported only through a converse step from the conclusion: the step is circular and broken; a further supporting judgment of the premise that cites an independent terminal basis makes it non-circular (§6.1; D-99; R-02).
36. A premise supported through a step assessed valid, whose own premise is grounded in an event, and also through a step from the conclusion: it is rooted without the conclusion, so the step is not circular; if the intermediate step is unassessed, judged invalid or disputed, the premise is circular (§6.1; D-99, D-100; Codex review R614-01).
37. `prediction-failed(P)` with complete use history and provenance, read for an unrelated claim `Q`: neither an independent test nor an independent confirmation of `Q` (Definition 5.3; SC-CC611-02).
38. Claims `P` and `Q` support each other through two steps, neither supported by any event, and a valid step concludes `K` from `P`: `P` has no root witness, so the step shows "premises not established", is not circular, and `has-sound-support(K)` is false (§6.1, F-25; SC612-01).
39. The premise of a step concluding `K` is supported through a converse step from `K` and through the `P`–`Q` cycle of case 38: the step is circular; the cycle clears nothing (§6.1; SC612-01).
40. The premise of a step under condition `c` is supported only through a converse step from the conclusion, and also by an event-backed judgment under an incompatible condition `d`: the step stays circular; an event-backed judgment under `c`, or a comparability judgment that `d` covers `c`, makes it sound (§6.1, D-69, D-82; SC612-02).
41. A route with no assessment, or with assessments none of which is effective: "unassessed" or "assessed, not effective"; that alone never makes it "broken", which can still follow from a retracted, superseded or refuted premise or from circularity (§6.1; SC612-03; Codex review R613-02).
42. A step `Z` with no premises concludes `P`, nobody has assessed `Z`, and the only supporting judgment of `P` cites `Z`; a valid step concludes `K` from `P`: `P` has no root ("no root reached"), the step shows "premises not established", and `has-sound-support(K)` is false. With a converse step from `K` that the judgment also cites, the step is circular (§6.1, F-25; D-100; SC613-01).
43. As case 42, with an effective positive inference assessment of `Z` and none negative: `P` is rooted in a valid argument, the step is assessed-sound and shown "rooted in a valid argument, not in an event", and the converse step does not make it circular (§6.1, F-28; D-100).
44. As case 43, where `Z` carries an undischarged hypothesis `h`: `Z` counts for the step concluding `K` only when `h` is in that step's context (it carries or discharges `h`) or an effective comparability judgment states that `h` covers that context; otherwise `P` has no root (§6.1; D-70, D-71, D-100).
45. `Q` is supported by a judgment citing an applicable event, step `U` concludes `P` from `Q`, `P`'s only supporting judgment cites `U`, and `U` has an effective negative inference assessment, or both a positive and a negative one: `P` has no root, so a valid step concluding `K` from `P` shows "premises not established", although `P`'s own judgment is positive (§6.1; D-100; Codex review of 1.13, §4.5).
46. A step concludes `K` from `K`, and `K`'s supporting judgment cites an applicable event: the premise is circular and the step broken (§6.1; R613-01).
47. A supporting judgment cites an evidence relation whose only effective evidential assessment is `not-usable`: the relation is not a terminal basis (§6.1; D-100).
48. A derivation introduces hypothesis `h`; step `U` concludes `B` from `h` alone, and step `D` concludes `K` from `B`, discharging `h`; both have effective positive inference assessments and none negative; `B` is judged `supported-under(h)` citing `U`, and `K` is judged `supported` citing `D`; a valid unconditional step `T` concludes `L` from `K`: `K` is rooted for `T` in a valid argument, `h` is shown introduced and discharged and is not a condition of `K` or `L`, and `T` is assessed-sound (§6.1; D-70, D-72, D-100; Codex review SC614-01).
49. As case 48, where `h` is also used on a branch to `K` that bypasses `D`: `h` is a carried condition of `K`, so the step concluding `K` counts for `T` only when `h` is in `T`'s context or a comparability judgment covers it; otherwise `K` has no root (§6.1; D-72; case 14).
50. As case 48 without `D`, where a valid unconditional step `T'` concludes `L` from `B`: `h` is never discharged, `B` holds only under `h`, and for `T'` its judgment shows "compatibility not established" and `B` has no root (§6.1; D-71, D-100).

---

## 11. Scientific inspectability (O1)

**Material realized record.** Events and observations with origin and qualification; claims with modality, conditions and acts; questions; evidence relations with use history; inference steps; objections with handling, resolution and mode; judgments, including comparability, source and retention-recommendation judgments; decisions with authority, exposure and dissent; review obligations; flags with cues; archive and deletion records; sealed attribution, blocks and appeals for anonymous review. **Destructive boundaries:** only explicit deletion (candidate 6.21 §12); archival is not destructive.

**Intended readers.** Researchers, PIs, reviewers and their agents; for project memory, the users, overseers, incident investigators and operators of candidate 5 §1.4.

**Routine questions.** What do we believe about X, why and how strongly? What bears against it? What changed since a given time? What was retracted, and what depends on it? Was this observation used to fit or to test? Which sources does this rest on, and how independent are they? What did we hold then? What is recommended for archive, and why? What did this answer search, what did it skip, and which of its statements are supported by cited text (§16)?

**Product inspectability surfaces.** All are **beyond the requested deliverable** of this formulation and bind only after the owner accepts them: question pages and the understanding section; the standing report with its basis; fact-check results; the retraction impact view; the retention recommendation queue; masked review packages and the block-and-return flow; decision status (`reported`, `recorded`, `validated` awaiting signatures or complete) with its labels and late-objection delta; deletion and withdrawal markers; the participant-visible fields of anonymous-review records (same-family review R-19 m); the "target withdrawn, not re-examined" state on markers and question pages (D-63); the restore coverage line (D-65); the objection coverage statement (D-80, D-87) and its shared-copy form (D-88); the "cites a withdrawn record" label (D-83); the "resolved by assessment at" target label (D-94); and the appointment-refusal warning shown to critics before they write anonymously (D-79). Architecture candidate 6.21 §17.2 repeats this marking. Technical acceptance of this formulation does not accept them. **Within the requested deliverable** (the owner's requirements of D-104 and D-110): the plan, coverage and support state carried by every answer (§16), since the owner asked that the memory say what it could not settle rather than present a loss as fact.

No realized scientific results were produced or examined in drafting this document, and no variants were evaluated.

---

## 12. Supporting rationale and provenance

| Source | Contribution |
| --- | --- |
| SCIRE v0.4 §3 | P1–P9 |
| SCIRE v0.4 §4.3, §4.4, §4.5 | Definition 2.3; F-3 to F-7, with the re-review's SC-41 and V4-06 repairs |
| SCIRE v0.4 §5.3 | Definitions 5.5 and 5.6; F-22 to F-24 |
| SCIRE v0.4 §6 | Definitions 5.1 to 5.4, 2.9; F-13 to F-19; F-25; F-32 to F-35 with the V4-07 repair |
| SCIRE v0.4 §7.1 | F-31 |
| Re-review V4-12 | The status vocabulary in Definition 2.8 and F-17, restored |
| SSDS 8.0 (through the proposal §10.2) | F-19 (unknown authorship), F-21 (stale evidence), F-31 (historical rules), the judgment basis in §6.5 |
| Proposal §6.4 and D-32 | §7 |

Literature is not cited as authority. The formulation borrows the distinctions of argumentation and evidence theory as used in the SCIRE texts; it does not import any external theorem.

---

## 13. Evidence and dependency impact

- **Concretized by:** UPMS candidate 6.21 (D3), which maps each F-rule to a record, check or projection and an acceptance test (its §15 and Appendix A); its retrieval-and-scale annex realizes §16 (its §R16 maps F-43 to F-55 to invariants and tests).
- **D2 dependent:** the D2 retrieval method candidate 1.3 (§9).
- **Front-end dependents:** SCIRE's front-end specification (proposal §14 step 2) relies on F-3 to F-12 and must not narrow them.
- **Reopen triggers** in candidate 5 §1.4: triggers 1 and 4 are answered by this formulation; trigger 1 reopens again for any numeric score (§9). Triggers 2 and 3 are unchanged.
- **Accepted predecessor:** D1 1.16, ratified (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`). **Recorded tensions bearing on it, and their applicability to this revision** (assessed by Claude, AI, Opus 5.5; proposed until this revision's acceptance considers them): the SERIOUS CHALLENGE recorded with owner decisions D-101 to D-116 (`UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` §3, as corrected by `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` §3), asserted by Claude on the owner's requirement and bound to core 6.17's concretization, not to a D1 rule: **applicable**, since §9 and §16 are this revision's answer at D1; it is a challenge to the adequacy of the ratified pilot design for the larger requirement, not a defect of that design within its envelope. **Searched:** `workplans/active/` decision, ratification, review and critique records of 5 November 2026; `history/SEMANTIC_EVOLUTION.md`; the predecessor's §15. **Not reachable:** native GitHub issues. Tensions recorded against the SCIRE v0.4 texts are carried as listed in §12.

---

## 14. Findings raised while drafting

The author's findings on the proposal's D1 content, D1-F1 to D1-F25, are each repaired or decided in the text above; their table is in map H's moved text (owner decision D-85; Codex review of 6.5, §7 item 3). None is a Serious Challenge to a D1 meaning. Live challenges are in §15; the D3-level challenges are in the architecture change histories.

---

## 15. Open challenges

1. **Judgment on judgment** (§6.5): deferred by owner decision D-39.
2. **De-attribution on request** (D1-F4): decided (D-44, F-9a); V4-12 (iv), where an argument may stop, stays open.
3. **Whether F-6's one-hop default is enough** for SCIRE's objection rule, or a front end should widen it by default: to be tested by E1 and E5.
4. **Whether E5's faithfulness criterion can be stated operationally** before data: the owner sets error and cost limits first.
5. **Whether the coverage statement is shown acceptably often** (F-7a; D-87, D-88): to be measured in E1, E4 and E5.
6. **Whether a directly cited event is enough of a root** (D-99): a terminal basis rests on the attributed assessor's statement of what in the event was checked; real use should show whether some claim kinds need a route instead.
7. **Whether the simplified objection model is enough** (D-94): it gives up registered objection homes other than review scopes and per-target resolution; real use should show whether projects need them.
8. **Whether a valid-argument root is read for what it is** (D-100): a route rooted only in a valid argument is sound under its carried conditions and labeled so; E5 should show whether readers keep that label in view, and whether a witness of steps assessed valid is enough or some uses need every recorded support of a premise to be valid.
9. **Whether readers keep exact facts and assessments apart** (F-43): an answer shows both; E1 and E5 should show whether readers treat a route match or a citation as support.
10. **Whether speakers' declarations are reliable enough to lean on** (Definition 16.9, D-107): a wrong declared referent is the speaker's error, but it is also the cheapest route; its error must be measured (D2).
11. **Whether coverage is carried into replies** (F-49): agents may drop limitations when they summarize; the evaluation of D2 measures it.

---

## 16. Answers from memory (owner decisions D-101 to D-120)

**An answer from memory states what a stated search found, separately from what anyone judged it to mean.** This section defines what an answer to a question or a command claims about the memory. It owns no mechanism: plans, indexes, coverage records and budgets are realized by candidate 6.21 and its retrieval-and-scale annex (D3); pruning guarantees, error models and cost models belong to the D2 retrieval method candidate 1.3 (§9). It adds nothing to the theory–evidence meanings of §§2 to 8, which apply unchanged to every record an answer returns.

### 16.1 Plans and items

**Definition 16.1 — Plan.** A *plan* `π` for a request `q` is a pair `(Pop, R)`:
- the *population* `Pop` is fixed by **mandatory filters**: the reader's eligibility (candidate 6.21 §7.3.4 and §10.1), and any scope, time window, record types, history position and archive inclusion the request states;
- the *discovery routes* `R` are a set of routes, each of one kind: a **lexical predicate** over a stated text representation, either the original text or a named rendering revision (Definition 16.10), a **structural predicate** over recorded interpretations and references, a **similarity route** or a **hub route**.

A plan is an interpretation of `q` (Definition 2.3), attributed to its compiler, with `q` as its source span; its resolutions of mentions in `q` are part of it.

**Definition 16.2 — Exact facts of an item.** For an item `x` returned under `π`, its *exact facts* are the following, each decidable from records without interpretation:
- **source integrity**: the cited span is the stated span of the stated canonical revision;
- **eligibility**: the reader may read `x` at the read's position;
- **population membership**: `x` satisfies every mandatory filter of `π`;
- **route match**: for each lexical or structural route, whether `x` satisfies its predicate over the route's stated representation at the stated analyzer, extractor and index versions. A match in a rendering is an exact fact about the rendering's text, not about the original; its citation names both the rendering revision and the original span, and no original-text match is reported for words absent from the original; for a similarity or hub route, only that the route proposed `x` ("similarity only").

**Definition 16.3 — Assessments of an item.** The *assessments* of `x` are attributed judgments that may be wrong:
- **interpretation fidelity**: that an extraction, resolution or rendering through which `x` matched says what its span says;
- **relevance**: that `x` bears on `q`;
- **support**: that a cited span of `x` supports a stated part of the answer.

Each assessment has an assessor (a person, an agent or a processor) and may be absent.

**F-43 — Exact facts and assessments stay apart** (D-118). No exact fact implies an assessment. An answer never presents fidelity, relevance or support as following from source integrity, eligibility, a route match, a citation's existence or an extractor's processing extent. Processing extent ("extractor v3 processed 87% of the population") is not extraction recall.

**F-44 — Similarity adds; it never removes** (D-102). An item is excluded from an answer only by a mandatory filter, or because no route proposed it over the part of the population the routes evaluated. A similarity or hub route may propose items; its not proposing an item never excludes it, and never supports absence. A step that skips part of the population is admissible only if it cannot skip an item that satisfies the plan; that guarantee is D2's (D2 candidate 1.3).

### 16.2 What an answer may say about absence and coverage

**Definition 16.4 — Execution completeness.** A plan's *execution* is complete when every exact route was evaluated over the whole population at the stated versions, with no part skipped for budget, availability or time, and no truncation of the match set. Execution completeness says nothing about whether `π` captures `q`.

**Definition 16.5 — Coverage.** The *coverage* of an answer states, each with its counting unit (spans, records, payloads or sources) and reasons:
- **capture**: what of the source history was captured, and known capture gaps (candidate 6.21 §10.3, `capture_extent`);
- **execution**: what was evaluated or skipped, total matches (each stated as exact, a lower bound, an estimate or unknown) against returned matches, and how to continue;
- **processing**: which extractor and resolver versions covered which part of the population, and what is unprocessed;
- **availability**: bytes unavailable, deletion markers and "private source" endpoints, under the restriction of F-46;
- **interpretation**: which items matched only through an interpretation, and that interpretation's separate facts (F-50);
- **answer support**: which statements of the answer have an assessment of support, by whom, and which have none.

Several dimensions may report limitations at once.

**F-45 — Absence is stated for a plan.** "None" is stated only as "no item of population `Pop` satisfies routes `R` at versions `V`", and only when execution is complete. It never states that the memory, or the world, contains no such thing. This applies candidate 6.21 §10.2's absence rule ("Absence is assertable only for a deterministic predicate over a fully enumerated authorized corpus") to plans; a similarity route never contributes to an absence statement.

**F-46 — Coverage is honest and discloses nothing hidden** (D-110; SC-R2-01).
1. Every material limitation along any dimension is stated, and none is turned into a finding: a skipped partition, an unprocessed population or an exhausted budget is never reported as "none found" or "not in memory".
2. Coverage speaks only of records the reader may know exist (`read`). Hidden records are never counted, and "results cover only records you may read" is stated whether or not hidden matches exist.
3. Known losses (truncation, skipped parts, unprocessed spans, quantization on a similarity route, summarization in a hub, an exhausted budget) are listed. Meaning that an extractor or summary dropped cannot be listed without an independent oracle; for it, coverage states the method, its inputs, its processing extent and its measured error limits (D2), never a claim to list every omission.

**Definition 16.6 — Grounded answer.** An answer is *grounded* when every statement it makes about what the memory holds cites spans, and each statement carries its support state: assessed as supported (by whom), assessed as unsupported, or unassessed. Content without citations is labeled **orientation**.

**F-47 — Answers are grounded** (D-104). An answer passed to a reader or agent is grounded. A citation shows where a statement comes from; it does not show that the span supports it. Hub text and narrative are orientation unless their statements cite spans.

**F-48 — "Cannot be confident" is an answer** (D-110). An answer that states it cannot settle the question, with its reason (cost beyond the budget, an ambiguous source, an incomplete record, an unprocessed population, a similarity-only result), is a correct answer. An answer that presents a limitation as a fact is a defect, whatever its other merits.

**Definition 16.7 — Consequence class.** A request has one *consequence class*: **orientation**, **recall**, **explanation**, **decision basis** or **mutating command**, in increasing order.

**F-49 — Limitations are stated in proportion to consequence.** The higher the class, the more of the coverage the answer itself must carry. For a decision basis, every incomplete execution, unassessed support and interpretation-only match bearing on the basis is stated in the answer, not only in its metadata, and F-2 applies to every interpretation it relies on. For a mutating command, F-53 applies. A lower class may summarize its limitations, but never omits one that could change the reader's use of the answer.

### 16.3 Interpretation layers

**F-50 — Annotate, never replace** (D-106). Every structure, resolution and rendering is an interpretation over exact spans (Definition 2.3), attributed and versioned, with its basis. The original text is never replaced, and where text and an interpretation disagree, the text wins. A match found only through an interpretation is labeled as such. For an interpretation, three facts are separate and may all hold: whether its speaker confirmed it; which adoptions of it exist, each a new claim under its adopter's attribution (Definition 2.3: adoption "changes nothing about" the interpretation); and which attributed fidelity assessments exist. F-2 is unchanged: an interpretation supports a decision basis only if confirmed by its speaker or adopted.

**Definition 16.8 — Context frame.** The *context frame* of a span records the circumstances of its production: speaker, addressees, session, task, time and time zone, scope, the preceding turns, and the project and files in use, each field either known with its source or recorded as unknown. A context frame identifies the speaker and addressees of the outer utterance only; quoted speech, reported dialogue, role-play, several addressees and pasted content are not resolved by it.

**Definition 16.9 — Declaration.** A *declaration* is a statement by a span's speaker, made with the span, of the identities and records the span refers to and of index terms for it. It is the speaker's own statement of intended meaning, attributed to the speaker. It is not a fidelity assessment of the span, and nobody can make a declaration for another speaker's span. Agent principals make declarations with their writes (D-107); people may.

**Definition 16.10 — Standalone rendering.** A *standalone rendering* of a span is a minimal edit of it in which every insertion is marked as added and carries a link and its basis. It is an interpretation (Definition 2.3): the speaker's own when the speaker supplies it (D-109), otherwise its processor's. It states the context it drew on; it does not make the span independent of context. A rendering is shown with its original.

**Definition 16.11 — Resolution.** A *resolution* binds a mention in a span to an identity or a record. It records its candidates, the exact revisions it used as its basis and the history position at which it was made. It is an interpretation.

**F-51 — Resolutions are read at their position** (D-106; extends F-31).
1. A **reconstruction as held** at a span's position uses only records that existed at that position. A **current interpretation** of an older span may use later records and is labeled current. A later interpretation is never shown as what was held earlier.
2. A resolution never rests on another resolution that its speaker has not confirmed (design note R3 §5.4). Adopting a resolution creates the adopter's own claim, which may be relied on as that claim (F-2); it does not make the resolution a basis for further resolutions, because adoption "changes nothing about" the resolution (Definition 2.3).
3. Confirmation of a resolution attributes intended meaning to the speaker. It is not independent verification: two confirmed resolutions can share one mistaken identification.
4. A resolution that binds a mention to a person is an identification: an interpretation the speaker may confirm, limited to identities the reader and the source's scope may know (D-108). It never characterizes the person (D-32, F-39).

**F-52 — Occurrences are distinct.** The same text in two records is two occurrences: an interpretation of one is not an interpretation of the other, and their authorship, conditions, history and evidential independence are their own (Definition 5.4, F-19).

### 16.4 Commands and discovery

**F-53 — A command's target is an exact set.** A request to change or delete records is authorized for an exact set of record revisions, compiled from its description and shown before confirmation; the description itself authorizes nothing. If the set the command would act on differs from the confirmed set when it is committed, the command is not the confirmed one and needs confirmation again. An ambiguous referent is asked about, never chosen.

**F-54 — Unexplored is not excluded** (D-116). In stepwise discovery (a broad step, then narrowing), the parts of the population a later step did not pursue are unexplored. The final answer reports them, with their known sizes, as unexplored; it never treats them as searched, and F-45 applies to the final plan only. Counts shown in a broad step state their counting unit and whether each is exact, partial, bounded or estimated (D-117); an unstructured or unknown population is always shown, so counts of extracted annotations never stand for the meaning of the whole.

**F-55 — Working estimates are not records of confidence.** An investigator's changing sense of where to look is the investigator's. It is never stored as a confidence on a claim (§9); if it is recorded, it is an attributed claim with its reasons, under §§2 to 8.

### 16.5 Validity

In regime: answers from memory of any size storage permits (D-101), qualified first at the pilot profile of candidate 6.21 §14.2 (D-120). Out of regime: a guarantee that a plan captures its request; a guarantee that an interpretation is faithful; any probability that an answer is true. Their errors are measured (D2) and reported as coverage, never assumed away.

---

## Appendix A. Independence and coverage

- **Family:** written by Claude (AI, Opus 5.5), the same model family and model as the proposal, candidates 4.1 and 5, the SCIRE v0.3 and v0.4 texts and the SCIRE v0.4 re-review. Shared blind spots are likely. A reviewer outside the Claude family is required before acceptance.
- **Read directly (1.17):** design note revision 3, its three Codex critiques and decision records D-101 to D-120, in full; core 6.17 §§1.4, 5.5 to 5.6, 7.3 to 7.4, 8.2, 9.1 to 9.6, 10, 11.2, 12 and 14. **Read directly (earlier revisions):** the proposal in full; candidate 5 §§1–18 in full (Appendix A by heading); SCIRE v0.4 §§2–7 in full; the SCIRE v0.4 re-review §§1–9 in full; the Codex review of the proposal in full, after the first draft.
- **Anchoring:** every revision from 1.1 to 1.20 was written by the same author in answer to a review or owner decisions, so its repairs were fitted to existing text and need an independent check. Which reviewer and family reviewed each revision is in map R.
- **Not read:** SCIRE v0.4 §§8–17 (facilitation, orientation, interfaces, invariants, experiments), except as summarized by the proposal and the re-review; SSDS sources (reached only through the proposal's §10).
- **Realized results:** none produced, run or reviewed. **Variants:** none evaluated.

---

## Appendix B. Deferred: channel assessment (owner decision D-45)

Kept so the meaning is ready when channel assessment is built; not current text.

**Definition 7.2 — Track record (non-person channels only).** For channel `ch` and claim kind `k`, the track record is the set of later judgments `J` on claims of kind `k` from `ch` such that `J`'s assessor is not among the authors of the assessed claim, and `J`'s basis consists of evidence independent of `ch` in the sense of Definition 5.4. A judgment whose basis is agreement with the prevailing position, rather than independent evidence, is excluded.

**F-41a — Track-record coverage.** A track record is reported with its denominator and coverage: the channel's claims of the kind, how many were later assessed, and how they came to be assessed. Preferential checking of disfavored sources biases an otherwise independent collection.
