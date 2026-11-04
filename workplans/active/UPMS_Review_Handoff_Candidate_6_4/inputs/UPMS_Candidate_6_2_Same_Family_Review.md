# UPMS Candidate 6.2 and D1 Candidate 1.2 Review (Same-Family)

3 November 2026 · requested by the product owner (Sam) · reviewer and asserter: Claude (AI), model Fable 5.1 (`claude-fable-5-1`), in a Claude Code subagent session. Tools used: file reading, `grep`, `diff`, `sha256sum`, `git rev-parse`. No further agents were launched. No code was run beyond those utilities.

**Governing method:** SSDP 7.2.1. No task or workplan assigns a `protocol_version`. The software-design skill was used for the D3 core and annex, the scientific-formulation skill for the D1 text; both review contracts, including the Challenge Pass, were followed.

**Independence.** I am the same model family (Claude) as the author of every text under review, of the proposal, of the 6.1 same-family review and of every earlier UPMS review except Codex's. I am a different model (Fable 5.1, not Opus 5.5), but `AGENTS.md` makes same-model-family review non-independent, so this review **cannot be the independent falsification** that `AGENTS.md`, core §1.3 and §16 (Gate 0) require. Shared blind spots are likely; a finding I did not make is not evidence that none exists. I saw only the files, not the author's reasoning. I treated the change history (A.10, A.11), core §18.3's C62 dispositions and D1 Appendix D as claims to test against the operative text, not as evidence. I did not read the 6.1 review until after hashing, and I tested each of its findings against the 6.2 text rather than against the author's disposition of it. I have not softened findings on account of being same-family.

Owner decisions D-20 to D-56 are treated as product choices. I do not re-litigate them for preference. Where one contributes to a material failure I say so and give the trajectory.

## 0. Bound inputs

All hashes were computed with `sha256sum` on the working tree at UPMS commit `73f5090b0e94c6cbfad834ae9cf2953ba1c4353c` (branch `upms-candidate-6-d1-formulation`, clean tree). **Every hash named in the request §1 matched.** The request itself matched its stated hash `8b150963fa657bbb768df003937f16248bbc396f84dec39c377755486197e31c`.

| File | SHA-256 | Role here |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_2.md` | `219a81bbfa061cf5914df1c144246416ce1b28ea15a6f5985c1a4151ecd01ed2` | **Under review** (D1, "D1") |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2.md` | `0240825365cc66b645e3f78e52b790efe6ca4066f7490fd1e7ac6525c29662dc` | **Under review** (D3 core, "C6.2"; 40,290 words) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Anonymous_Review.md` | `f7083ddf4ab75ac83a9f8d881e821ba352b7f07c87b6c893f60373b723f1452f` | **Under review** (D3 annex, "annex") |
| `workplans/active/UPMS_Review_Request_Candidate_6_2.md` | `8b150963fa657bbb768df003937f16248bbc396f84dec39c377755486197e31c` | Request; §2 and §3 followed |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_2_Change_History.md` | `a20ecbdd33a3e2e4d858f2cce8b281a8c3cb7edf143597c101db9b9dec2a0b31` | A.10 and A.11 read as claims; A.1 to A.9 not read |
| `workplans/active/UPMS_Candidate_6_1_Same_Family_Review.md` | `f1ff9606f256f60a39394d7eb6e0485f0d137f1cda740fffb81fdcbe2d942592` | SC-R1 to SC-R3, R-01 to R-20; format |
| `workplans/active/UPMS_Owner_Decisions_2026-11-03.md` | `c1455f6f11246f697d68be7a449472f28209826146bcf4940a761dcae7ebb79e` | D-37 to D-46 |
| `workplans/active/UPMS_Theory_Evidence_Proposal_v0.1_Independent_Review.md` | `cf7433bf6fe7225ef096971ce2ec3e6b4c4af7c2f7776a66fc9b891da79b79b1` | Codex findings; §§1–2 read in full |
| `workplans/active/UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | `0053686dad6d1ca88d6b95daa9c22120c8eb4a08c3f43dc58d6053735b3dcbdc` | Direction; not read directly (§9) |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_1.md` | `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a` | Diffed against 6.2 only |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md` | `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | Diffed against 1.2 only |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_5.md` | `406cf3b44d1ece405bf6690b2aba0ba861d17a7abd116e604345362bd26bc750` | Frozen base; not read |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Checking.md` | `eb0332c9b75854b814606e840e72d8a4b5b6b0d58aac1aae4b4e4c549eb3323b` | Not under review; not read |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_2_Annex_Mathematics.md` | `f373d8ed01bf530bdbdaba475c6b5d1539654e80acefece8ff0a20e9bfeebbdf` | Not under review; only §M.0 read (§7 below). The request gives no hash for it; this is the working-tree hash |
| `workplans/active/UPMS_Mathematical_Models_Derivations_D1_Candidate_1.md` | `b50638641a506ae29861cec10fc76a647d6ed961d7345cff27dc0783168047a9` | Not under review; not read |

**Change-map check.** The 1.1→1.2 diff matches D1 Appendix D (every changed block is listed there). The 6.1→6.2 diff touches only sections A.10 names, plus one-line reference updates in §6.8, §12.1 and §12.5. I found no undeclared change.

## 1. Verdicts (same-family interim)

| Text | Verdict | Blocking reasons |
| --- | --- | --- |
| D1 formulation candidate 1.2 | **NO-PASS** | S62-1 (retracting or deleting a target and re-recording it clears every objection, bypassing F-3a); S62-3 (the route-status table has no row for an assessed route whose premises lack an effective `supported` judgment, the commonest state); F62-01 (another assessor can make a judgment ineffective by naming it as prior head); F62-02 (whether anonymous judgments count in route status is undefined) |
| D3 core 6.2 with the anonymous-review annex | **NO-PASS** | S62-1 and S62-3 through §6.10 and §9.9; S62-2 (the annex homes every record an anonymous-role session causes in a sealed area readable only by that role, which contradicts §5.11's homing rule and makes anonymous objections either unreadable or unsealed); F62-07 (restore "never forgets" is false for every non-restrictive record in the recovery-point window, and the loss is silent); F62-09 (the critic-side decline tells the proposed chair that a collaborator is an anonymous critic); F62-17 (acceptance tests T79, T84, T105 and T86 contradict the contracts they are meant to qualify) |

Candidate 6.2 does repair every 6.1 finding in the direction the owner chose, and most repairs defeat their original trajectories (§5). The blocking items are new paths through the repairs and contradictions between the new mechanisms. None requires reopening an owner decision; each needs a bounded text change and, in four cases, an owner choice (§6).

## 2. Serious Challenges

### S62-1 — Retract-and-re-record clears objections; F-3a covers only formal revisions (D1, then D3)

**Owner:** D1 Definition 2.5 and F-3a, then D3 §6.3, §6.10, §12.3. **Texts:** D1 Definition 2.5 ("`superseded` applies only when the target is retracted or withdrawn with no successor revision"), F-3a ("When `tgt(O)` is revised to a successor revision, `O` is carried"); C6.2 §6.3 ("A principal can retract or correct their own attributed statement (`write`)"), §6.10 ("Resolution: superseded — the core, only when the target is retracted or withdrawn with no successor revision — resolved for that target"), §12.3 ("A record deleted by its own author shows 'withdrawn and deleted by its author'"), §12.2 (liveness), §10.5.1 (mandatory lists), T108.

D-47 and F-3a close SC-R1's path: a **revision** carries objections. They leave open the path that does not use a revision.

**Trajectory.**
1. PI P records hypothesis claim κ as a position of question Q. Critic C records objection O against κ: a material counterexample, unresolved.
2. P **retracts** κ (§6.3, own statement, `write`), without naming a successor. The core sets `r(O) = superseded` (Definition 2.5, §6.10). O is now resolved, so it no longer travels (F-7), is no longer live (§12.2), and leaves every mandatory list (§10.5.1). Nothing notifies C; retraction creates review obligations on κ's *dependents* (F-32), and O is not a dependent.
3. P records κ″ as a **new claim** with the same content and adds it to Q's positions. κ″ has no objections. P records a finalization D citing κ″. A(D) is empty, `has_open_challenge(κ″)` is false, Q's page shows κ″ with no objection.
4. The same result follows if P **deletes** κ instead (§12.3: "withdrawn and deleted by its author"), since deletion is a withdrawal with no successor.

No signature, basis statement, resolution decision or exposure was required. This is the SC-R1 cost structure exactly, at the price of two ordinary writes instead of one. The core cannot detect that κ″ restates κ; F-3a is keyed on the formal `prior_revision` link, which the author controls. T108 tests only the revision path.

**Consequence.** Dissent against a claim can be cleared silently by its author. D1 §10.2 names this class as falsifying. Proposal §13.2's claim that no hidden applicable objection arises within a project (C6-4) also fails on this path, since the objection is not hidden but erased from applicability. TE-04 and MV1 are met literally and fail in substance.

**Bounded repair.**
- **D1.** Remove `superseded` from the *resolution* set. A retraction or withdrawal of the target with an unresolved objection leaves the objection **unresolved** with the handling-like state "target withdrawn, not re-examined". It stays live (§12.2) and stays in the mandatory list of every question in which the target was a position, until its author withdraws it or rebinds it to another record. It stops traveling with *new* decisions only because no new decision can cite a withdrawn record.
- **D3.** §6.10: replace the `superseded` row accordingly; at retraction or self-deletion, show the retractor every unresolved objection to the target and offer a successor link. §12.2: a withdrawn or retracted record with an unresolved objection stays live (so the question page keeps it). Question pages (§10.5.1) list withdrawn positions with unresolved objections under "withdrawn, objections not re-examined".
- **Test.** Extend T108: retract κ with an unresolved objection, record κ″ with the same text, finalize on κ″: the question page and the finalization's view must still show O.

**Confidence:** high that the text permits the trajectory. The only escape is reading "retracted or withdrawn with no successor revision" as excluding a later new claim; the core has no way to know that κ″ is a successor.

### S62-2 — The annex's placement rule contradicts the objection-homing rule; the anonymous role is unrealizable as written (D3 annex)

**Owner:** D3 annex §7.8, against core §5.11 and §7.3.8. **Texts:** annex §7.8 ("**Placement:** every record the session causes is homed in a sealed per-pseudonym area of the review, readable only by sessions in that same role and through the chair path, never in an agent's or a person's own scopes"); core §5.11 ("An objection is homed in its target's home scope, or in a scope whose readers include every reader of the target; `record_objection` refuses any other home"); §7.3.8 (review scope: participants `rw`); T70, T110; SE1.

Both rules are **Fixed (proposed)** and both bind the same record. An anonymous critique or objection is a record "the session causes". Under the annex it must be homed in the sealed per-pseudonym area, readable only by anonymous-role sessions and the chair path. Under §5.11 it must be homed where every reader of its target can read it, or `record_objection` refuses it. The texts give a D4 implementer three choices, each of which fails:

- **(a)** Follow the annex: the objection is readable only by the critic's role sessions and the chair. Participants never see it. T70 ("it travels and is shown as anonymous") fails; D-33's purpose fails.
- **(b)** Follow §5.11: the objection is homed in the review scope. Then "every record the session causes" is false, SE1's text is false, and the annex says nothing about which records go where. The implementer decides, and the decision is exactly the sealing boundary SC-R3 showed must be fixed by D3.
- **(c)** Home the objection in the review scope but its "owner" and locator fields sealed: that is what the author plainly intends, but it is not what either text says, and the sealed per-pseudonym area is then an undefined second home for an undefined class of records.

The sealed per-pseudonym area is also not a scope: §7.3 says every record has one home scope, permissions attach to scopes, and administrators hold every right in every scope (§7.3.6). Nothing says the area is outside `set_permissions`, outside administrator mode and outside `create_scope`. Only AC5's "no reading of sealed attribution" protects it, and a working note is content, not attribution.

**Consequence.** The central new mechanism of 6.2's anonymity repair cannot be implemented from the text without a D4 choice that decides a D3 question. Whichever way D4 chooses, SE1 or TE-04 is false.

**Bounded repair.**
- Split the annex's classes: **published records** (objections, critiques, replies, judgments if allowed, questions) are homed by §5.11 in the review scope under the pseudonym, with owner, locator, `witness_principal` and provenance edges sealed; **caused operational records** (release records, processing records, quota and access records, working notes, checkpoints, blocked text) are homed in the sealed per-pseudonym area.
- Define the area as a record class outside scope permissions: not a scope, not reachable by `set_permissions`, `create_scope`, administrator mode or export; readable only by sessions in that role for that pseudonym and by the chair path; add it to AC5 and T86.
- Rewrite SE1's clause "every record it causes is sealed and homed in a sealed per-pseudonym area" to match, and add to T110 that an anonymous objection is readable by every participant.

**Confidence:** high on the contradiction (direct reading of two Fixed rules). Medium on how far the area's undefined status matters, since the author's intent is recoverable.

### S62-3 — The route-status table is not total: an assessed route with an unestablished premise has no status (D1, then D3)

**Owner:** D1 §6.1, then D3 §9.9. **Texts:** D1 §6.1 table (rows unassessed, assessed-not-effective, under review, challenged, disputed, broken, assessed-sound) and the sentence "Several conditions can hold; the report lists all of them"; Definition 2.8 statuses `supported, refuted, contested, unknown, supported-under(c), disfavored-under(c)`; C6.2 §9.9 "Route status: unassessed, assessed but not effective, under review, challenged, disputed, broken or assessed-sound"; T98, T109.

SC-R2's third reading found a missing row for "assessed but not effective" and 6.2 added it. The table still has no row for the commonest state of an inference route.

**Trajectory.** Step S: P → C. Assessor A judges S valid (inference assessment, effective, positive). No objection targets S or P. No obligation is pending. P has **no judgment** in `(σ, ρ)`, or its only effective judgment has status `contested` or `unknown`, or `disfavored-under(c)` with `c` compatible with S's conditions. Now:
- not **unassessed**: an inference assessment of the route exists;
- not **assessed, not effective**: the assessment is effective;
- not **under review**, **challenged** or **disputed**: no obligation, objection or negative assessment;
- not **broken**: the premise is not retracted, superseded or `refuted`, and the route is not circular;
- not **assessed-sound**: the premise lacks an effective `supported` judgment.

No row holds. "The report lists all of them" lists nothing, and the one-word label is undefined. The same gap applies to `disfavored-under(c)` on a premise, which the text never mentions (it is neither `refuted` nor `supported`), and to an evidence route whose only effective evidential assessment is `usable-with-limits` or `under-review` (Definition 2.9), which is neither the "positive" nor the "negative" the table uses.

**Consequence.** The central derived quantity (D1 §1.2) is undefined for a valid step whose premise is unassessed or contested, which is the normal state of an argument in progress. D4 will invent a label; the two likeliest inventions ("unassessed", "sound") are each wrong. E5 cannot be scored where the expected disposition is undefined.

**Bounded repair.**
- **D1.** Add the row **premises not established**: the route has an effective positive assessment, no adverse condition holds, and some premise has no effective judgment in `(σ, ρ)` with status `supported` or compatible `supported-under`; list each such premise with its status or "unassessed". Place it after "disputed" and before "broken" in the label order.
- **D1.** Define positive and negative for each judgment kind: inference assessment valid/invalid; evidential assessment `usable` positive, `not-usable` negative, `usable-with-limits` positive with its limits listed, `under-review` neither (the route is then "under review"); claim assessment `supported`/`supported-under` positive, `refuted`/`disfavored-under` negative, `contested`/`unknown` neither.
- **D3.** §9.9 adopts the row; T98 adds a valid step on an unassessed premise and on a `contested` premise.

**Confidence:** high; this is a case analysis of the table as written.

## 3. Findings

Severity: **Blocking** means repair before the affected contract is accepted. **High**, **Medium**, **Low** as usual. Each finding names its earliest owner, a trajectory, a consequence and a bounded repair.

### 3.1 D1 formulation

#### F62-01 — Any assessor can make another's judgment ineffective by naming it as prior head (High; D1 Definition 6.0, D3 §5.3)

**Location:** D1 Definition 6.0 condition 1 ("`J` is a head of its `(target, σ, ρ)` lineage at `p` (concurrent heads by different assessors coexist)"); C6.2 §5.3 ("Within one target, scope and ruleset lineage, replacement names the prior head and checks it atomically; concurrent disagreement is never resolved by last write"); Judgment schema `supersedes?`, `assessor`; T109.

**Trajectory.** Assessor A judges step S valid (J_A, effective). Assessor B wants S "broken" rather than "disputed". B submits J_B (invalid) with `supersedes = J_A`. §5.3 lets any replacement name the prior head and checks only that it is the head; nothing restricts replacement to J_A's own assessor. J_A is no longer a head, so it fails condition 1 and is "not effective". Every effective assessment of S is now negative: **broken**. "Disputed" (R-02's repair) is reached only when B chooses not to supersede. If the order is reversed, A silences B the same way.

**Consequence.** Disagreement is again shown as failure, at the choice of whichever assessor writes last; P7 and the "disputed" row are defeated. T109 tests only the concurrent-head path.

**Repair.** D1: a judgment may be superseded only by a judgment of the same assessor (or by that assessor's retraction); a judgment by another assessor is always a concurrent head. D3 §5.3 and §4.3 `submit_assessment`: refuse `supersedes` across assessors. Add to T109. **Confidence:** high on the gap; the text never says who may supersede.

#### F62-02 — Whether an anonymous-role session may submit a judgment, and whether it counts, is undefined (High; D1 F-8 and Definition 6.0, then annex §7.8, §7.6)

**Location:** D1 Definition 2.8 ("attributed assessment"), §2 ("attributed act means a record whose author is an authenticated principal"), F-8 (an anonymous objection "never blocks"; "an attributed judgment that independently establishes what it pointed out changes the route's status"); annex §7.8 ("What may not be anonymous: claims about a person and AI critiques"); core §7.6 (inquiry ruleset: "attributed human and agent assessments"); §4.3 `submit_sealed`; T99.

**Trajectory.** Anonymous critic "Critic B" (a human, through the front end's anonymous mode) submits not an objection but an **inference assessment**: step S invalid, under the inquiry ruleset. The assessor is sealed; the record is an authenticated, attributed act in D1's sense. Definition 6.0 does not mention attribution mode, so J is effective. If S had a positive effective assessment, S is "disputed"; if not, S is **broken**, and `has_sound_route` is false for every claim resting on S. Under SCIRE's rule a broken route blocks consequential use. The anonymous participant has done alone what D-36 and D-37 reserve for "an attributed judgment ... whoever supplied the lead", with no signed assessor anywhere.

**Consequence.** D-36 is bypassed by recording a judgment instead of an objection. Alternatively, if the author intends that anonymous sessions cannot submit judgments, the text does not say so, and `submit_sealed` accepts any record kind.

**Repair.** Owner choice, then D1 F-8 and annex §7.8: either (a) anonymous-role sessions may submit claims, objections and questions only, and `submit_sealed` refuses judgments; or (b) a sealed-assessor judgment is shown as "assessed, anonymous" and is never effective (a seventh condition in Definition 6.0), so it informs like an objection. I recommend (a). Add to T99. **Confidence:** high on the gap.

#### F62-03 — "Compatible" conditions are undefined and not computable in Slice 2 (Medium; D1 §6.1, then D3 §9.9)

**Location:** D1 §6.1 assessed-sound ("`supported-under(c′)` with `c′` compatible with the step's conditions"); C6.2 §9.9 ("A premise supported only under conditions incompatible with the step's conditions does not make the route sound"); T98.

Conditions are free text until structured statements arrive in Slice 3 (checking annex, not under review). The projection service is deterministic code. It cannot decide compatibility of two texts, so in Slice 2 either every `supported-under` premise is treated as compatible (TE-R11's failure) or as incompatible (no conditioned premise ever supports). The owner record lists type-specific propagation as open, but this clause is stated as if decided.

**Repair.** D1: define compatibility for the first product as (i) the same condition record cited by identity, or (ii) an attributed comparability judgment (Definition 5.6) stating compatibility; otherwise "compatibility not established", which falls under S62-3's new row. D3: §9.9 computes exactly that. **Confidence:** medium-high.

#### F62-04 — Cross-scope premises can never be sound, and the reader's `(σ, ρ)` is unspecified (Medium; D1 §6.1, D3 §9.9, §7.6)

**Location:** D1 §6.1 ("every premise has an effective judgment in `(σ, ρ)`"); Definition 6.0 condition 6; C6.2 §7.6 ("one inquiry ruleset per inquiry scope"); §9.9 ("in the reader's scope and ruleset"); §9.3 ("Cross-scope evidence captures every participating scope's epoch").

**Trajectory.** Claim κ lives in project scope A with ruleset ρ_A. Its premise P lives in team scope B, judged `supported` under (B, ρ_B). A reader of κ in scope A asks for standing. No judgment of P exists in (A, ρ_A), so no route of κ through P is ever assessed-sound until someone re-judges P under A's ruleset. Nothing says a reader may choose σ = B, nor what σ means for a reader of many scopes.

**Consequence.** Either multi-scope inquiry cannot show soundness, or D4 picks a cross-scope rule (the "cross-scope most-permissive selection" §5.3 forbids for project memory).

**Repair.** D1: a premise's judgment counts under the premise's own home scope when the two scopes register the same ruleset identity; otherwise the premise is "assessed under another ruleset" and falls under S62-3's row. D3 §9.9: the reader's σ is the claim's home scope by default; the report names the scope and ruleset under which each premise was judged. **Confidence:** medium.

#### F62-05 — Revising a step or relation through `supersedes` may or may not be a "revision" for F-3a (Medium; D1 F-3a, D3 §5.5, §6.10)

**Location:** D1 F-3a ("revised to a successor revision"); C6.2 §5.5 (relations have "lifecycle status (active, superseded, retracted)", with `supersedes`); §6.10 "Carry on revision: the core, when the target is revised".

Inference steps and evidence relations are objection targets. They are not revised like claims; a new relation names the old through `supersedes`. The word "superseded" is used for the relation's lifecycle and for the objection's resolution. If a relation `supersedes` is not a "revision", an author objected to on step S supersedes S with S′ (same premises, reworded conditions), and O becomes `superseded` by §6.10's last row, since S was "withdrawn with no successor revision". That is S62-1 again, for routes.

**Repair.** D1 F-3a and D3 §6.10: a relation or step that is `superseded` by another with the same conclusion (or the same observation and targets) is a revision for F-3a; carry the objection. Rename the relation lifecycle state to `replaced` to end the homonym. **Confidence:** medium-high.

#### F62-06 — Smaller Definition 6.0 gaps (Low–Medium; D1 Definition 6.0, D3 §5.3)

| # | Gap | Repair |
| --- | --- | --- |
| a | Condition 2 needs a validity interval; the Judgment schema (§5.3) has `applicable_time` only, and a judgment with none is undefined | Name the field; default "unbounded" |
| b | A ruleset **version** change: condition 6 names ρ, not its version; §9.3 invalidates project-memory judgments on rule assignment change, §9.9 says nothing | State whether a new ruleset version is a new ρ (old judgments coexist as another ρ) or supersedes (old judgments ineffective) |
| c | Condition 5 is enforced on the *declared* basis only; exposure to a standing report is recorded and used by nothing. Laundering through unrecorded reliance is accepted by D-39, but the reader cannot see it | Label each effective judgment "assessor was shown prior assessments of this target: yes/no", computed from release records. Cheap and deterministic |
| d | Definition 6.1's `A(κ)` says "objections targeting κ or its routes"; F-28's `has-open-challenge` and the "challenged" row include endpoints | Add endpoints to Definition 6.1 |
| e | F-28: the sentence "Standing never merges kinds of assessment..." sits between "Two derived predicates are defined exactly" and the predicates | Move it |

### 3.2 D3 core: decisions and the front-end boundary

#### F62-07 — Restore "never forgets" is false for every non-restrictive record in the recovery-point window, and the loss is silent (High; D3 §12.4, §14.2, §11.4; D-53)

**Location:** C6.2 §12.4 ("**Restore never resurrects and never forgets** (D-53)"; the recovery log holds "deletion tombstones ... and every restrictive or sealing control"; "a restore verifies that it holds the latest position"); §14.2 ("site-loss RPO ≤ 15 min"); D1 F-31 ("Where explicit deletion removed records ... 'as held then' is incomplete and says so"); T13.

D-53 repairs R-14 for revocations, access records and markers. Two paths remain.

**Trajectory A (silent loss of dissent).**
1. At t−20 min, finalization D on κ is committed and complete (in the backup at t−10).
2. At t−5, critic C records objection O on κ. O enters A(D) and appears on every projection of D (F-7). O is not a restrictive control, so it is not in the recovery log.
3. At t the site is lost. Restore from t−10 applies the log. O is gone. D shows no objection. Nothing tells any reader that fifteen minutes of history vanished: §12.4 says nothing about disclosing a restore, and F-31's "incomplete and says so" covers explicit deletion only. The same holds for a `resolution` decision in the window (then the objection reappears unresolved, which is at least conservative), for signatures that completed a decision (held in the log, but the decision revision they bind may be lost, so they dangle), and for carried-objection states.

**Trajectory B (the "latest position" proof).** The log "has monotone, authenticated positions held in redundant copies" and a restore "verifies that it holds the latest position". After a site loss, a copy can prove its own integrity, not that it is the latest: the latest position may have existed only on the lost site. Nothing names an off-site witness or a synchronous off-site copy. If the copies are co-located, the log has the same ≤15 min RPO as the canonical store, and T13's "a revocation ... committed inside the recovery-point window survives restore" cannot be made true by any D4.

**Consequence.** A headline Fixed claim is false as written, and the failure class is the one SC-61 and TE-04 exist to prevent: dissent vanishing with no marker.

**Repair.**
- §12.4: a restore commits a **restore record** (a control, in the log) naming the canonical backup position and the log position applied; every scope's coverage and every "as held then" read between those positions carries "records committed in [t₁, t₂] may be missing (restore ⟨id⟩)". F-31 (D1): "where explicit deletion or a restore removed records".
- §12.4 and §14.2: state that the recovery log's redundant copies are synchronously held off-site (RPO 0 for the log) or that an external monotone position witness exists; otherwise drop "never forgets" to "never forgets restrictive controls, and discloses what else it may have lost".
- Owner choice: add objections, disputes and `resolution` decisions (small, append-only) to the recovery log, so dissent recorded inside the window survives.
- T13: add Trajectory A and a restore with co-located log copies.

**Confidence:** high on A (direct reading); medium-high on B (the text asserts a proof without a mechanism).

#### F62-08 — `late_objections[]` is a stored field on an immutable revision, but objections keep arriving during signing (Medium; D3 §5.4, §6.9, T100)

**Location:** §5.4 (`late_objections[]` in the decision record); §6.9 ("objections in the applicable set recorded after the policy result's position are committed with the decision as its late-objection delta"; the applicable set "is derived ... not stored separately (R-08)"); check 5; T100 ("an objection recorded between the policy result and a signature commits as the late-objection delta").

**Trajectory.** Validated decision D commits at p₁ with `late_objections[]` = {O₁} (recorded between `applicable_position` and p₁). PI A signs. At p₂ objection O₂ is recorded on a basis record. PI B signs at p₃. T100 says O₂ "commits as the late-objection delta". But the decision revision is immutable and any change makes a new revision on which A's signature does not count (check 5). So either the core silently edits a signed revision, or O₂ is not in the stored delta and the field is incomplete, or B's signature creates a new revision and signing never completes under a trickle of objections (R-04 returns in a milder form: no refusal, but no completion). The text also now has two owners for one meaning (the stored delta and the derived applicable set), the duplication R-08 removed for `applicable_at_decision`.

**Repair.** Derive the delta: late objections are the members of A(D) whose record position is later than `applicable_position`, computed at read like the rest of the applicable set; remove `late_objections[]` from §5.4; keep `applicable_position`. State that objections during the signing window never touch the decision revision. Fix T100's wording. **Confidence:** high.

#### F62-09 — A decision awaiting signatures is stranded by a change of decision-policy owner (Low–Medium; D3 §6.9)

§6.9: the core accepts a signature "only when its transmitting front end is the owner named by the decision's home scope at commit"; a change of owner "applies only to decisions recorded after it". A decision validated by the outgoing owner and still awaiting one signature after the change can be completed by neither front end: the outgoing owner is no longer the named owner (first clause), and the change does not apply to the decision (second clause). If the outgoing front end is unregistered, the decision stays "awaiting" forever and nothing says so. **Repair:** the attestation or administrator-mode act names the pending decisions it hands over; the incoming owner re-evaluates each as a new revision (check 5), and the old ones render "superseded by policy-owner change". **Confidence:** medium-high.

#### F62-10 — D-52 places front-end registration "inside the D-40 residual", which D-40 does not cover (Low; owner, then D3 §6.9, §7.7)

D-40 accepts that the storage-and-keys operator can read sealed identities. §6.9 extends the same residual to "registering a front-end principal is an operator act". An operator who registers a front end can, for any **new** scope whose `manage` holder cooperates, become its decision-policy owner and write `validated` decisions under any "policy". That is a different trust than D-40's, and the owner has not decided it. **Repair:** record a decision (owner) that operators may register front ends, and name the front end's registration, its operator and the registration time on every projection of a `validated` decision (§6.9 already shows the policy owner; add when it was registered). **Confidence:** high that the extension is undecided.

### 3.3 D3 annex: anonymous-review back end (beyond S62-2)

#### F62-11 — The critic-side decline tells the proposed chair that a collaborator is an anonymous critic (High; annex §7.8)

**Location:** annex §7.8 conflict checks: "On the critic's side, it also checks whether a proposed person chair is a declared collaborator, supervisor or co-author of any anonymous critic ... every critic-side ground shows as a decline"; "The proposed person is told the reason, which they already know".

**Trajectory.** PI proposes Dr X as person chair. X is a declared collaborator of Y, who is "Critic B". X accepts. The core declines on X's behalf and, per the text, tells X the reason. For the *sealed* ground (X is the critic) X already knows. For the *critic-side* ground X learns something new: one of X's declared collaborators, supervisors or co-authors is an anonymous critic in this review. X has three declared collaborators, one of whom works on this topic. X now knows who Critic B is, and X was chosen by the PI, who may ask (the disclosed residual). R-09 asked for critic-side checks to be declines; 6.2 added them and then told the declined person why.

**Consequence.** A sealed identity reaches a person outside the chair path through the conflict check itself.

**Repair.** The proposed person is told only "the review's conflict rules declined this appointment", for every ground that is not an open ground about the work; the reason classes "sealed" and "critic-side" are indistinguishable to them and to the proposer. Update T88 and T104. Disclose to critics that their declared collaborators cannot chair. **Confidence:** high.

#### F62-12 — The front end, the transport and operational logs are inside the anonymity boundary but outside the stated TCB (Medium; D3 §7.7, §8.5, annex §7.8; SCIRE front end)

**Location:** §7.7 (TCB list: "core validation, permission evaluation, sealing and barriers; retrieval access enforcement; capture and session instrumentation; identity; KMS; and deployment isolation"); §4.3 (`submit_sealed` by "the front end that opened the review"); annex §7.8 ("critics write only through the front end's anonymous mode"; sealed "submission logs"); §8.5 ("Operational logging is content-free by default"); §14.2 (content-free logs, 14 days).

A human critic authenticates to the front end, which transmits `submit_sealed`. The front end therefore knows the critic's identity and content at once; its own logs and sessions are outside UPMS. UPMS's transport adapter (MCP, HTTP) sees the authenticated principal on every request, including `submit_sealed` for review R at time t; §8.5 forbids *content* in operational logs, not principals, and "submission logs" in the annex most naturally means the core's. A 14-day request log naming (principal, `submit_sealed`, R, t) identifies every critic to anyone who reads infrastructure logs, which is wider than the storage-and-keys operator D-40 names.

**Repair.** §7.7: add the front end that opened the review and the transport adapter to the TCB for sealing, and say so to critics (D-40's disclosure). §8.5: for anonymous-role operations, operational and transport logs record a pseudonym or nothing, never the principal; include adapter logs in "submission logs". SCIRE front-end specification: the anonymous mode must keep no identity-bearing log of sealed submissions. **Confidence:** medium-high.

#### F62-13 — Obligations assigned to a pseudonym have no path after the review closes (Medium; annex §7.8, core §9.11, §6.11)

§9.11: a dependent "written in an anonymous role is assigned to its pseudonym through the chair path and never reassigned"; §6.11: a pending obligation keeps the route under review and blocks new consequential use; the temporary review-service session "ends with the review round". A year later a retraction reaches an inference step Critic B wrote. The obligation goes to a pseudonym of a closed review, whose author has no anonymous-role session to receive it, and is "never reassigned". The step is under review for ever; anything resting on it needs an explicit qualification. **Repair:** when a review closes, every pending or future obligation on its sealed-authored records is assigned uniformly to a curator of the review scope, as a rule stated before anyone writes, so the rule reveals nothing; or the review stays openable for its critics' role sessions. **Confidence:** medium-high.

#### F62-14 — Lineage-exclusion omission reports and blind tasks reveal sealed edges (Low–Medium; annex §7.8, core §10.6.4)

The annex seals provenance edges but lets lineage exclusion use them, and §10.6.4 reports "omissions it causes ... to the declarer exactly as ineligibility is". A blind task excluding author A's rationale omits Critic B's anonymous critique, and the declarer learns that the critique derives from A's rationale, which only A's team could read. This is SC-R3 path C moved from the endpoint view to the omission report. **Repair:** sealed records are excluded from blind tasks uniformly (every anonymous record is treated as derived from every excluded lineage) and omission reports count them as "sealed records: n" without stating why. **Confidence:** medium.

#### F62-15 — Smaller annex gaps (Low)

| # | Gap | Repair |
| --- | --- | --- |
| a | After `sign_sealed`, whether the sealed operational records (release, quota, working notes) also unseal is unstated | State they stay sealed |
| b | §7.8 "Anonymous-role sessions seal everything they produce" still lists "any overseer link of an assisting agent"; no agent principal may assist any more (D-49) | Delete the clause |
| c | The review-scope `manage` holder sees the scope's write grants (`get_permissions`), which is the candidate-critic set; §11.5 discloses "its write grants ... can narrow" but not that `manage` sees the full list | Say who holds `manage` on a review scope (the front end only) and that participants never do |

### 3.4 D3 core: deletion, archive, liveness

#### F62-16 — An effective negative judgment is not live, so its author can remove it without a marker (Low–Medium; D3 §12.2, §12.3)

§12.3 (R-13 repair): complete removal with no marker is allowed for a record "with no live dependents (§12.2) that is neither a decision nor a resolution". §12.2's liveness predicate does not include judgments. Assessor A's effective judgment "step S invalid" makes S broken. A deletes it with complete removal: nothing cites a judgment, so it has no live dependents. S is silently sound again. A could equally supersede it, which leaves history; complete removal leaves nothing. **Repair:** add to §12.2 "it is an effective judgment of a route or claim, or the only effective judgment of its lineage"; complete removal is then unavailable and the marker "withdrawn and deleted by its author" applies. **Confidence:** medium.

#### F62-17 — The recovery log holds deletable payload (Low–Medium; D3 §12.4, §12.3)

The log holds "deletion and withdrawal markers", and a marker's "free-text reason is itself deletable" (§12.4). The log has "monotone, authenticated positions", so it is append-only; a deletable text inside an append-only, separately backed-up, redundantly copied log is a deletion surface §12.3 must list and purge, or it is not deletable. **Repair:** the log holds the marker with its reason class only; the free text lives in the canonical store. **Confidence:** medium-high.

### 3.5 Acceptance tests that contradict their contracts

#### F62-18 — Tests still state the pre-6.2 behavior (Medium; D3 §15.1, annex tests)

The tests are the acceptance evidence; a test that contradicts its contract either fails a correct implementation or passes a wrong one.

| Test | Says | Contract says | Fix |
| --- | --- | --- | --- |
| T79 | A finalization with sole uninstrumented backing is "**refused** until an upgrade record..." | §6.9 check 3, D1 F-17: **labeled**, never refused (R-07) | Rewrite as a label test |
| T105 | "the critic's own agent and a temporary review-service session **succeed**" | Annex §7.8, D-49, SE1: the core **refuses** `submit_sealed` to any session of an agent principal | Own agent is refused |
| T84 | Preview shows "records the requester cannot see **as a count**" | §12.3, T27: the uniform line, never a count (R-16) | Match T27 |
| T86 | "an assisting agent's overseer link ... reveal nothing" | No agent principal assists | Delete the clause |
| T100 | An objection during signing "commits as the late-objection delta" | Immutable revision (F62-08) | After F62-08 |
| T13, §13 row | "latest **tombstone** log" | §12.4: recovery log | Rename |

### 3.6 Internal consistency and stale wording (Low)

| # | Location | Defect | Repair |
| --- | --- | --- | --- |
| a | C6.2 §1 | "concretizes a new D1 parent, the theory–evidence formulation candidate 1" | 1.2 |
| b | §4.4 bullet 4 | "(SC-TE04, pending the owner)" | D-37 decided |
| c | §7.3.1 | "(D-9, as proposed in candidate 5 and pending the owner)" | D-9 confirmed, amended by D-49 |
| d | §18.2 table header | "Status in candidate 6" | 6.2 |
| e | §16 Gate 0 | "decisions D-1 to D-36 confirmed or changed" | D-1 to D-56 |
| f | §16 Slice 3 | lists TE-15, merged into SE1 | Remove |
| g | §9.9 inputs | "evidence relations and inference steps with their **latest** assessments" | lineage heads (D1 Definition 6.0) |
| h | §2 "Objection" | target list omits "resolution" (D1 Definition 2.5, §5.11 schema include it) | Add |
| i | §5.3 Judgment schema | no validity-interval field (F62-06 a) | Add |
| j | §15 O6, §14.2 disk admission | "barriers, purge and recovery" while §13 reserves capacity for "every restrictive control" (A.11 M7 notes this) | Align |
| k | §7.6 | "Slice 2 registers one inquiry ruleset per inquiry scope": who registers (right) is unstated | `manage`, as scope configuration (§7.3.3) |
| l | Annex §7.8 | "that they may be asked why they declined is a disclosed residual (§18.3, C61-5, C62-8)" cites change-history IDs as if core sections | Cite §18.3 rows correctly or drop |

### 3.7 Simplicity: text and mechanisms that can go (request §2 item 8)

The core is 40,290 words. The split moved about 7,000 words out and the repairs added about 2,500. What can still go, in order of yield:

1. **§10.5.3 to §10.5.5 (consolidation, maintenance cost, routing), about 1,900 words, and the Slice 4 rows of §14.2.** Slice 4 machinery, conditional on E2. Move to a Slice 4 annex bound by hash; keep in the core the exact-projection and overlay contracts (OV1, OV2, OV3 exact parts) that Slice 1a-core needs.
2. **§5.9 Natural languages, about 950 words.** Keep the three bullets Slice 1a-core needs (original text is the record; names are not translated; translation is never authority) and move vocabulary, values and formats, retrieval analyzers, spoofing and pilot languages to the checking annex with ML1's Slice 3 part.
3. **§18.2 (D-1 to D-36 status rows) and §18.3 (SC-61 to C62-12), about 2,600 words.** These are change history. Keep D-37 to D-56 as a table of current decisions; move the rest to the change-history file, which already exists for this purpose.
4. **Three statements of D-36/D-37/D-38:** D1 F-8, §4.4 bullet 4 and §5.11's paragraph. Keep D1 F-8 and §5.11's two sentences on what the core does; §4.4 cites them.
5. **§7.7's anonymity row** restates the annex; cite SE1.
6. **The `Rebind` transition (§6.10).** It "records re-examination" and changes nothing; it is a handling state ("re-examined against revision n"), not a lifecycle row. Fold it into handling.
7. **`late_objections[]`** (F62-08): derive it.
8. **§9.3, about 650 words,** repeats §6.2 and §7.6 on project-memory admission. One statement of the ancestry rule and one of the epoch rule suffice; the flag-investigation paragraph can be two sentences.
9. **§1's "Revision 6.1" paragraph** is history.
10. **§12.4 "Honest claims"** duplicates D2 and DL2; keep the invariant rows.
11. **Not recommended:** merging `reported` and `recorded` (the author's reason stands); removing the "disputed" row (needed, with F62-01 fixed).

Taking 1 to 3 brings the Gate 0 core to roughly 34,000 words without changing a contract.

## 4. Codex findings: status against the operative 6.2 text

"Resolved" means the operative body text defeats the Codex trajectory as far as this same-family check can tell. It is not closure: Codex's revisit condition requires an independent check.

| Finding | Status (this review) | Basis in operative text; residual |
| --- | --- | --- |
| **SC-TE01** / TE-R01 | **Partly resolved** | Definition 6.0 gives effectiveness a fit definition; one-pass evaluation, negative information, per-derivation circularity and pinned projection version are present (D1 §6.1, F-31; §9.9; T98, T109). Open: the status table is not total (S62-3); another assessor can silence a judgment (F62-01); condition compatibility is uncomputable in Slice 2 (F62-03); cross-scope premises (F62-04) |
| **SC-TE02** / TE-R02 | **Resolved in direction; contradicted in text** | Confined chair service, no model sees identities, D-9 reconciled by D-49, operator residual accepted by D-40 and disclosed. Open: the placement rule contradicts §5.11 (S62-2); the front end and logs are outside the stated TCB (F62-12) |
| **SC-TE03** / TE-R03 | **Resolved in mechanism; residual** | Deterministic paginated mandatory lists (§10.5.1, MV1, T93). Residual: lists inherit S62-1 |
| **SC-TE04** / TE-R04 | **Resolved in meaning and in the core's mechanism** | D-37, D-50, D1 F-8, §5.11, §6.9 (no refusal for an objection's existence), T99, T100. Open: an anonymous *judgment* is undefined (F62-02) |
| **SC-TE05** / TE-R05 | **Mostly resolved** | Statuses, atomic checks, policy owner bound to the transmitter, attested owner change, signature completeness (§6.9, DC1, T100). Open: the stored delta on an immutable revision (F62-08); stranded pending decisions on owner change (F62-09); front-end registration trust (F62-10) |
| TE-R06 | **Resolved** | §7.3.5, §1.2 attestation (D-43), §7.9 |
| TE-R07 | **Resolved** | §8.1, §10.6.4, annex §7.8 (masking versus exclusion) |
| TE-R08 | **Resolved, except S62-1** | §12.2 liveness, T103; a retracted target's objection becomes non-live (S62-1) |
| TE-R09 | **Mostly resolved** | Direct versus descendant deletion, erasure obligations (D-41), recovery log (D-53). Open: window loss and no restore disclosure (F62-07); payload in the log (F62-17) |
| TE-R10 | **Resolved** | Typed judgment kinds; endpoints in F-6 and §9.9; cited definition, model and calibration records in §9.11 |
| TE-R11 | **Partly resolved** | Definition recursion distinct from cycles; no ordinal arithmetic. "Compatible" undefined (F62-03); type-specific propagation open (owner record) |
| TE-R12 | **Resolved** | F-41, D-45, D-55 (author search), residual stated |
| TE-R13 | **Mostly resolved** | F-20a uniform rule, enumerated fields (§11.5), review budget. Open: critic-side decline reason (F62-11); logs and front end (F62-12); omission reports (F62-14) |
| TE-R14 | **Mostly resolved** | Later conflict, replacement, pending appeal, self-identification warning, appointment bound to the opening front end (D-52). Open: F62-11; obligations after closure (F62-13) |
| TE-R15 | **Resolved** | §7.7 bounded wording |
| TE-R16 | **Resolved** | §8.6, §14.2 |
| TE-R17 | **Resolved by A.11, with its own open rows** | A.11 repairs U1–U12, M1–M9, X1, X9; A.11 itself leaves X2 (AC3 "oversight transfer is fenced", H1 "fails closed"), X5, X6, X8 and X10 open for the reviewer. I did not read candidate 5 and cannot close them; X10 (who deletes a departed user's personal scope) is a real gap |
| TE-R18 | **Resolved** | Slice 2 has invalidation, decision validity and obligations; T70 and T99 moved to Slice 3 with anonymity (D-42). T105 and T79 are stale (F62-18) |
| TE-R19 | **Mostly resolved** | Contract checks before studies; E5 narrowed. Missing contract checks: S62-1 retract path, S62-3 unestablished premise, F62-01 cross-assessor supersession, F62-02 anonymous judgment, F62-07 window loss, F62-11 decline reason; stale tests (F62-18) |
| TE-R20 | **Resolved** | Pinned projection version (F-31, §9.9); exposure is what was released |

## 5. 6.1 same-family findings: status against the operative 6.2 text

| Finding | Status | Note |
| --- | --- | --- |
| SC-R1 | **Repaired for revisions; bypassed by retraction and deletion** | F-3a, §6.10, T108 close the revision path. S62-1 |
| SC-R2 | **Repaired; new gaps** | Definition 6.0, inquiry ruleset, T109. S62-3, F62-01, F62-03, F62-04, F62-06 |
| SC-R3 | **Repaired in direction; contradicted in text** | Distinct session type, sealed edges, pseudonym assignment, role-only acts, review budget, no agent-principal assistance. S62-2 (placement), F62-11 to F62-15 |
| R-01 | **Repaired** | F-6 endpoints, §9.9, T69 |
| R-02 | **Repaired; residual** | Per-derivation circularity, "disputed". F62-01 reopens "disputed" |
| R-03 | **Repaired** | F-31, §9.9, T78 |
| R-04 | **Repaired; residual** | D-50; no refusal. F62-08 |
| R-05 | **Repaired; residual** | D-51; awaiting/complete. F62-09 |
| R-06 | **Repaired; owner gap** | Attested change, transmitter check, rendered owner. F62-10 |
| R-07 | **Repaired in contract; T79 stale** | Check 3 labels. F62-18 |
| R-08 | **Repaired; reintroduced** | Snapshot derived; `late_objections[]` stored. F62-08 |
| R-09 | **Repaired; new leak** | Critic-side grounds as declines, timing fixed. F62-11 |
| R-10 | **Repaired** | D-52; appointment bound; `manage` rule dropped; shown to participants |
| R-11 | **Repaired** | Review budget per pseudonym |
| R-12 | **Repaired** | §11.5 table |
| R-13 | **Repaired; residual** | "Or nothing" restricted. F62-16 |
| R-14 | **Repaired; residual** | Recovery log. F62-07 |
| R-15 | **Repaired** | D-54; exemptions in F-9a and §12.3; T107 |
| R-16 | **Repaired in contract; T84 stale** | Uniform preview line. F62-18 |
| R-17 | **Repaired** | D-55; F-39; T81 |
| R-18 | **Repaired** | Norm stated |
| R-19 a–m | **All repaired** | Each checked against the text; k is moot with §9.10 removed |
| R-20 | **Taken in part** | Items 1, 2 (text; T105 stale), 3, 5, 6 (snapshot; delta reintroduced), 7 (SE1/TE-15 merged; §4.4 and §7.7 still restate), 8 (checking annex only), 9 (A.1–A.9 moved; §18.2–§18.3 remain). Item 4 declined with reason. §3.7 above |

**On core §18.3 C62-1 to C62-12 and change history A.10.** Each "repaired" claim names a real text change that I located. The claims that overstate are C62-1 (SC-R1 "objections carried": only on revision), C62-3 (SC-R3: placement contradicts §5.11), C62-5 (R-14: restrictive controls only, no disclosure) and C62-11 (R-20 item 6: the delta reintroduces a stored copy). A.11's self-reported open rows (X2, X5, X6, X8, X10) are honest and remain open.

## 6. Owner decisions the texts still need

| Decision | Why it needs the owner | Reviewer's suggested framing |
| --- | --- | --- |
| What happens to an unresolved objection when its target is retracted or self-deleted (S62-1) | Extends D-47 to the path it does not cover; allocates the cost of withdrawal against dissent visibility | The objection stays unresolved and live, shown on the question page as "target withdrawn, not re-examined" |
| Whether anonymous-role sessions may submit judgments, and whether such judgments affect route status (F62-02) | Bounds D-36 and D-37 | Objections, critiques and questions only; `submit_sealed` refuses judgments |
| Restore disclosure, the log's RPO, and whether objections and resolutions join the recovery log (F62-07) | Changes the deployment profile and the D-53 claim | Restore record and coverage line; off-site synchronous log copies; objections and resolutions in the log |
| Front-end registration by operators, as D-52 states (F62-10) | D-40 did not cover it | Accept, with registration shown on every validated decision |
| The front end and transport inside the anonymity TCB (F62-12) | Changes what critics are told under D-40 | Named in §7.7 and in the pre-write disclosure |
| Obligations on sealed-authored records after a review closes (F62-13) | Trades a permanent "under review" against a uniform reassignment rule | Uniform reassignment to the review scope's curator at closure |
| Cross-scope premise judgments (F62-04) | Decides whether multi-scope inquiry can show soundness | Same ruleset identity counts across scopes; the report names the scope |
| Still open from the owner record and A.11 | — | C6-6 acknowledgement; V4-12 (iv); V4-15; TE-R11 type-specific propagation; strict-profile SC-42 rule; A.11 X2, X5, X6, X8, X10 |

## 7. Mathematics annex §M.0 hooks H1–H6: conflicts with the core as written

Read: §M.0 only. Not under review; this answers the request's one question.

| Hook | Conflict with the core as written? |
| --- | --- |
| H1 (Judgment `kind` adds `fidelity`, `inspection`) | **No direct conflict**; additive to §5.3. Two interactions: D1 Definition 2.8's kind list is closed and would need the D1 parent (or its mathematics child) to extend it; and Definition 6.0 condition 5 makes any judgment whose basis cites "other judgment" ineffective, so an inference assessment that cites a `fidelity` judgment of a rendering is not effective. If mathematical standing relies on fidelity checks as inputs, condition 5 blocks it, and D-39's deferral is implicated |
| H2 (Event span `notation: latex`) | **No conflict**; §5.1 spans are extensible and §5.9's language tag per span coexists |
| H3 (inference step `step_rule`, `introduces[]`, `discharges[]`, `approximation{order, validity}`) | **Interaction, not purely additive.** D1 §6.1 and §9.9 require "every premise has an effective judgment with status `supported`". An introduced-then-discharged assumption (modality `assumed`) can never be `supported`, so a derivation with a discharged hypothesis is never assessed-sound under the core as written. Absorbing H3 needs a D1 §6.1 rule for discharged premises, which is a D1 change, not a core enumeration extension. `approximation{order}` is recorded data, not a computed score, so §1.4's D2 condition is not triggered by the hook itself |
| H4 (checking annex §5.7.1 statement kinds) | Outside the core; no core conflict. The checking annex is not under review |
| H5 (Controls add `verifier_designation`) | **No conflict**; additive to §5.4, needs a guard row in §4.3 and a right |
| H6 (Meaning family adds `renders`, assessed only by `fidelity` judgments) | **No conflict** with §5.5 ("assessment lives only in judgments that target it"). One note: `renders` points claim → rendering; the core's §5 opening sentence closes the list of canonical record types, so a rendering must be an Event (with H2's notation span) or a Claim, not a new type |

Summary: H1, H2, H5 and H6 can be absorbed without changing a core meaning. H3 interacts with the premise rule of D1 §6.1 and §9.9 and needs a D1 rule before the core can absorb it. H1 interacts with Definition 6.0 condition 5.

## 8. Scientific inspectability and evidence

- **O1 content.** D1 §11 and C6.2 §17.2 state the material realized record, readers and routine questions, and mark the theory surfaces as beyond the requested deliverable; the surfaces R-19 m named are now marked. One new surface is unmarked: the restore record and its coverage line proposed in F62-07, if adopted. The "carried, pending re-examination" state and "sealed source" rendering are covered by the existing marks. Technical acceptance of either text, by any reviewer, does not accept a surface marked beyond the deliverable; only the owner can.
- **Accepted-authority tensions.** No accepted D1 or D2 authority exists for UPMS, so no tension search against accepted authority was owed or performed. I relied on no accepted authority for a consequential judgment.
- **Evidence executed.** Hash verification, `git rev-parse`, two diffs (6.1→6.2, 1.1→1.2), and reading and searching the bound files. Each counterexample is a constructed trace through the text, not observed behavior. No prototype, test, benchmark or study was run.

## 9. Coverage

**Read in full:**
- D1 candidate 1.2 (all 601 lines);
- C6.2 core (all 1,678 lines), including §15.1 T01–T112, §16, §17, §18 and Appendix B;
- the anonymous-review annex (all 71 lines);
- the review request;
- the owner decisions record;
- the 6.1 same-family review;
- the Codex review §§1–2 (Serious Challenges and the findings ledger); §§3–9 by heading only;
- change history A.10 and A.11;
- mathematics annex §M.0 and its status paragraph.

**Diffed only:** 6.1 against 6.2 (828 changed lines, sections checked against A.10); D1 1.1 against 1.2 (checked against Appendix D).

**Not read:**
- change history A.1 to A.9 (A.8 relied on through the 6.1 review and 6.2 §18.1);
- the proposal v0.1 (relied on through the Codex review, the owner record and the candidates' citations, so proposal-level defects may be missed);
- candidate 5 (frozen base; A.11's open rows X2, X5, X6, X8, X10 could not be checked);
- candidate 6.1 and D1 1.1 as texts (diffed only);
- the checking annex, the mathematics annex beyond §M.0, and the mathematics D1 candidate;
- the SCIRE v0.4 proposal and re-review; SSDS sources; `history/SEMANTIC_EVOLUTION.md`; `workplans/README.md`.

**Working tree.** At `73f5090`, no tracked file was modified. `git status` showed untracked environment files (`.bashrc`, `.bash_profile`, `.profile`, `.zshrc`, `.zprofile`, `.gitconfig`, `.gitmodules`, `.ripgreprc`, `.mcp.json`, `.idea`, `.vscode`, `.claude/`); these were not made by this review and I did not touch them. This file is the only change made. No commit, stage, push or branch.

**Realized results and variants.** None produced, run or reviewed. This record is a same-family input to the owner's Gate 0 preparation and is not gate evidence that can satisfy the independent-review requirement. One review pass was made; no alternative reviews or variants were generated or selected among. Every finding above was found in this pass and none was dropped.
