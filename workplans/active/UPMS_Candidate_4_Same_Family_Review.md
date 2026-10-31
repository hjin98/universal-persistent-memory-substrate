# UPMS Candidate 4 Review (Same-Family)

31 October 2026 · requested by the product owner (Sam) · reviewer: Claude (AI, Opus 5.5)

**Object under review:** `UPMS_Architecture_Manual_Review_Candidate_4_1.md`, SHA-256 `19a9e3edd77d4543ae1343fa0a7bba88dd92a0625a2514ee1f5138deab1d57df`. This is the hash that `UPMS_Re-Review_Request_Candidate_4_1.md` names for the object under review, although that request calls the file `UPMS_Architecture_Manual_Review_Candidate_4.md`. The repository also holds a different file under that name (SHA-256 `d2146daa…`), which was not reviewed.

**Independence.** The reviewer is from the same model family (Claude) as the candidate's author. This review therefore **cannot be the independent falsification** that §1.3, §16 (Gate 0) and §18.1 require. It is a same-family review, like the interim review of candidate 3, and can inform a candidate 5. Gate 0 still needs an independent reviewer.

Governing method: SSDP 7.2.1. Neither the task nor the workplan assigns a `protocol_version`.

## 1. Disposition

**NO-PASS for Gate 0 entry.** The candidate is careful and much stronger than candidate 2, but one guarantee in an early slice is false as written.

**SERIOUS CHALLENGE SC-1 (TM1, D-17, §8.1, §10.6.2).** In Slice 1a-team, any principal working through an agent can declassify another human's records that UPMS itself released, without that human's confirmation. The candidate does not record what UPMS releases to a session, and it describes the overseer's confirmation as if it were the owner's (finding N-01). The defect is in D3, not D4, and it has a direct D3 repair. Without the repair, TM1 cannot be accepted for Slice 1a-team.

Blocking alongside SC-1: none separately. N-02 must be resolved before Slice 1b is inside the accepted boundary. The other findings are Medium or Low and can be repaired in candidate 5.

## 2. Closure Tables

The candidate 2 cross-review (CR) and the candidate 3 interim review (M) are not in this repository. I therefore checked each closure against the finding as summarized in the candidate's Appendices A.4 and A.5, and against the current text. I could not verify the summaries against the original findings.

### 2.1 CR01–CR10

| ID | Status | Basis and residual |
| --- | --- | --- |
| CR01 | Closed in text, with residual | Ancestry is separated from waivable requirements (§5.5, §11.2) and traversed by exclusion and erasure (T30, T50). Residual: in Slice 1a-team, ancestry is not recorded for agent derivations (N-01) |
| CR02 | Closed | The narrative unit is one invocation's output, withheld whole (§10.5.2–§10.5.3, T38). Overlay notes are units too |
| CR03 | Closed | Correctness is promised only for exact projections and change entries. The narrative is labeled synthesis, and slot tables show status (§10.5.1–§10.5.2, T42) |
| CR04 | Closed, with residual | Ancestry enforcement at `submit_assessment` (§9.3, E3, T43). Residual: flag investigations can never be admitted (N-06) |
| CR05 | Closed for list and read | Own-record and oversight entitlements, the overseer cap and the protected grant (§7.3.4, §7.3.8, T44, T49). Residual: `c` and `d` are not bounded (N-03) |
| CR06 | Closed, with residual | There is no shortening path for existing access records (§11.4, T24). Residual: lengthening has no upper bound (N-09) |
| CR07 | Closed | Comparison cues are separate from flags. Only prohibitions are screened, and exceptions are met only by approval records. Absent obligations are reported as unscreened (§9.7, T32, T33) |
| CR08 | Closed in structure, with residual | Replay cap, budget, regions and concept-scoped retraining (§10.5.4, §14.2, T40, T54). Residual: global-pass deadlines and language multiplier (N-04, N-05) |
| CR09 | Closed, with residual | The Slice 1a overview is built from coordination records with read-time catch-up and four revocation stages (§7.3.7, §10.5.3, T45, T46, T56). Residual: coordination-key identity (N-07) |
| CR10 | Closed | Continuity warning restored and shown in task continuation (§10.5.5, T47) |

### 2.2 M-01–M-26

| ID | Status | Note |
| --- | --- | --- |
| M-01 | **Open for Slice 1a-team** | Closed where ancestry is recorded; open where the memory-service profile records none (N-01) |
| M-02 | Closed in text; A.5 inaccurate | §7.3.8 gives the overseer `lrd`, but A.5 says the overseer “holds `m`” (N-12) |
| M-03 | Partly closed | Regional passes are deadline-aware. Global passes, L0 sections and overlay notes are not (N-04) |
| M-04 | Closed | §11.2: ancestry is kept while a descendant survives, and traversal fails closed |
| M-05 | Closed, minor residual | Elevated `create_scope` with self as owner is not named among the refused acts (N-11) |
| M-06 | Closed | §11.4, §12.4 |
| M-07 | Closed | §7.3.4 step 2 |
| M-08 | Closed | §5.8, §9.8, T53 |
| M-09 | Closed | §7.3.4 step 3, §7.3.7, T49 |
| M-10 | Closed, with residual | Type, operation, lifecycle and conflict rule are all defined. The key namespace is not (N-07) |
| M-11 | Closed | §10.5.3 catch-up and scan budget, T56, T57 |
| M-12 | Closed, with residual | N-06 |
| M-13 | Closed | §9.7, T33 |
| M-14 | Closed, minor residual | Several tests sit at the wrong gate (N-11); A.5 still says “T01–T58” (N-12) |
| M-15 | Closed | §16, D-16 |
| M-16 | Closed | §9.8, T35 |
| M-17 | Closed | §10.6.2, T52. The retention of redaction copies is a separate gap (N-09) |
| M-18 | Closed | §2 defines one vocabulary, and the named exceptions are stated |
| M-19 | Closed | §11.4 |
| M-20 | Closed | §9.7 |
| M-21 | Closed | §10.5.3 |
| M-22 | Closed | §10.5.1 |
| M-23 | Closed | §10.5.5 |
| M-24 | Closed | §10.6.2, §10.6.4, T58 |
| M-25 | Closed as disclosed | The per-value origin column is not restored, and the candidate says so |
| M-26 | Partly closed | A.4 is corrected, but A.5 has new inaccuracies (N-12) |

## 3. New Findings

Most severe first. Each finding names its owning domain: **D3** means the architecture text must change; **D4** means implementation may choose.

### N-01 — Agent derivation declassifies UPMS-released records in Slice 1a-team (SC-1, Blocking)

**Section and invariant:** §8.1 memory-service row; §10.6.2; §7.3.5 (D-6); TM1; D-17.

**Counterexample:**

1. Human B writes record *b* in team scope T.
2. Agent principal A, overseen by H, is a member of T, so A and H can both read *b*.
3. Through MCP, A calls `get_context`, receives *b* in a release that UPMS checks, and writes note *n* into its private scope P_A.
4. The memory-service profile records no ancestry from *b* to *n*. §10.6.2 says UPMS “cannot see what an agent read before writing.”
5. A publishes *n* to the organization-wide scope. Under D-17, H confirms.
6. The waiver test sees only P_A ancestry owned by A, so the waiver passes. Every reader in the organization now sees *b*'s content. B never confirmed.

TM1 says the owner's confirmation is obtained “through overseer confirmation”. When the owner is not the overseer, that claim is false.

**Variant with no human check:** user U's agent session (not an agent principal) reads *b*, writes into U's personal scope, and U publishes. D-17 does not apply, so no confirmation of any kind is required. Unlike a deliberate human restatement, U need not know the text came from *b*.

**Severity:** Blocking for Gate 1a-team. The premise of §10.6.2 is wrong for the case that matters most: UPMS cannot see what an agent read elsewhere, but it does know what it released itself.

**Proposed alternative:**

- **Release-set propagation in the memory-service profile.** Record each UPMS release to a session or principal in a protected release log, kept as operational lineage. Give every later write from that session, since its start or its last validated reset (§8.3), an ancestry edge to a segment node covering those releases. D-6 and TM1 then hold for UPMS-sourced content from Slice 1a-team onward. Content from outside UPMS remains a declared gap, as human restatement is.
- **Keep D-17's confirmation, renamed.** Overseer confirmation can stay as an extra check, but described as oversight, not owner consent.
- **Test.** Add the trajectory above to T48's Slice 1a-team part.
- **Cost.** More writes will inherit team requirements. This is exactly D-6's no-laundering semantics, and the blocking rate should be measured at Gate 1a-team.

**Domain:** D3.

### N-02 — Agent records in shared scopes: an operational-scope requirement that cannot be waived, and a second waiver path (High)

**Section and invariant:** §7.3.5 (“publication is the only waiver”), §7.3.8, §8.2, §10.6.2, §10.6.3; TM1, CO1.

**Counterexample:**

1. From Slice 1b, everything in A's context becomes ancestry of its outputs, including prior session state held in its agent-operational scope (§8.2).
2. §10.6.3 says A records a blocker “immediately as a coordination record in the shared scope”.
3. The record's requirement closure includes the operational scope (readers: A and H) and usually P_A. Teammates hold neither right, so they cannot read the blocker, and areas they cannot list are omitted from their overview.

§10.6.3 says an agent's coordination records “pass the same test as its publications”. If that means they waive requirements, `record_coordination` becomes a second waiver, contradicting §7.3.5 and §7.4. If it does not, agents cannot coordinate.

Separately, §10.6.2 waives only “the publisher's own personal or private scope” or a scope the publisher manages. Agent-operational scopes are a separate type in §7.3.8, and agents never hold `m`. Whether an operational scope can be waived at all is undefined. The same question applies to a human's own runtime state used by agent sessions.

**Severity:** High. It blocks shared-pool coordination journeys once runtime lineage exists, so it must be closed before Slice 1b enters the accepted boundary.

**Proposed alternative:**

- Classify operational scopes as private scopes of their owning principal for the waiver.
- Define `record_coordination` in a shared scope as publication of a new item, under the same waiver and confirmation rules, and list it in §7.3.5 and §7.4 as the same single exception.
- Extend T48 to agent coordination records in Slice 1b.

**Domain:** D3.

### N-03 — Overseers bound only list and read; an agent's `c` and `d` can exceed its overseer's (Medium; challenges D-9)

**Section and invariant:** §7.3.1, §7.3.4 step 3; AC3.

**Counterexample:**

1. The manager of team scope T grants group G `lrwcd`. Agent A is in G; its overseer H has only `lr` on T.
2. A's list and read reach is correctly capped. But A keeps `c` and `d` on T, so it can:
   - apply curator corrections to humans' records;
   - suppress them;
   - curate T's vocabulary;
   - delete others' items.
3. H could do none of these. Injected content in A's context can steer curation, which is the planted-term threat in §7.7, with no human holding those rights involved.
4. Step 3 says the agent keeps `w`, `c` and `d` “on its own private and operational scopes”. It does not say what happens on other scopes.

**Severity:** Medium.

**Proposed alternative:** On scopes other than the agent's own, cap `c` and `d` (and optionally `w`) at the overseer's non-elevated rights, exactly like `l` and `r`. Alternatively, require per-action overseer confirmation for curation and deletion acts on others' items. Extend AC3 and T49 accordingly.

**Domain:** D3 decision.

### N-04 — Global passes, L0 sections and overlay notes escape the deadline rule (Medium)

**Section and invariant:** §10.5.3, §10.5.4, §14.2; OV4, T54.

**Counterexample:**

1. Under rolling 180-day retention, the deadline filter is binding. A regional pass at time *t* makes an L1 unit whose deadline is about *t* + 30 days.
2. The weekly global pass reads that L1 unit at *t* + 7, when it has about 23 days left.
3. If the global pass's inputs go through the deadline-filtered view, as §10.5.3 says “every narrative input” does, the L1 unit is excluded. The L0 narrative is then empty almost all the time, and T54's assertion cannot hold.
4. If they do not go through the filter, the L0 section's deadline is the old L1 unit's deadline.
   - The region is re-consolidated near day 30.
   - An L0 section built from the old L1 unit is withheld at its deadline.
   - It stays withheld until the next weekly global pass, which itself is deferred when the budget does not fit: a surprise withholding of up to a week, which OV4 rules out.
5. Overlay notes and piggybacked checkpoints (§10.5.3) are narrative units built from recent inputs without the filter, so they too are withheld by surprise.

**Severity:** Medium. Correctness is unaffected; availability and OV4's claim are.

**Proposed alternative:**

- Exempt global-pass inputs from the 30-day filter.
- Give each L0 section a tracked deadline, and schedule a scope's global pass by that deadline as well as weekly. Equivalently, have each regional pass trigger its scope's L0 refresh.
- State that notes are short-lived units exempt from OV4's no-withholding clause.
- Make T54 check L0 availability.

**Domain:** D3.

### N-05 — Narratives in several languages multiply maintenance cost, and the estimate omits it (Medium)

**Section and invariant:** §5.9 (“rendering for readers”), §10.5.4, §14.2; OV4, D-18.

**Counterexample:**

1. §5.9 generates the narrative in the readers' preferred language, and a translated narrative is another narrative unit.
2. §10.5.4 promises “no per-reader LLM cost” because each scope's section is written once. With *k* reader languages, regional and global outputs, or their translations, multiply by *k*. That promise then holds only per language.
3. The planning estimate (about 20 regional passes per 30-day lifetime) and D-18's narrated fraction count neither *k* nor the number of scopes. The pilot allows 5 users and 10 agent sessions, so there are already at least 15 private scopes before any team scope, and weekly global passes scale with that number.

**Severity:** Medium.

**Proposed alternative:**

- Narrate each scope once, in a designated scope language.
- Render only exact projections deterministically in each reader's language.
- Offer a labeled on-demand translation of the narrative, charged to the reader's task budget rather than to maintenance.
- Put *k* and the scope count into the T54 simulation and the estimate.

**Domain:** D3 for the cost contract, D4 for the values.

### N-06 — Flag investigations can never be admitted (Medium)

**Section and invariant:** §9.3 vs §9.7 (“every flag goes to investigation, whose result is a Judgment”); E3, T43.

**Counterexample:**

1. An investigator is assigned a flag. Its recorded inputs include the flag, which §8.2's conservative propagation and control dependence require.
2. §9.3 keeps any assessment whose inputs include a flag as evidence-only. So no investigation can ever admit, even when it re-reads every source directly and cites only source evidence.
3. If an implementation omits the flag from the recorded inputs to avoid this, it escapes the very rule M-12 added.
4. The §1.2 journeys still work, because default admission covers only first-party direct entry. But the main route from screening to Judgment is permanently stuck at evidence-only, and nothing in the text says so.

**Severity:** Medium.

**Proposed alternative:** Either:

- distinguish *routing inputs* (a flag's identity and which statements to examine) from *evidence inputs*. Admit an investigation only when its conclusion rests on a fresh read set of source, claim and statement evidence that passes the epoch check at commit; or
- state plainly that investigations are always evidence-only and that admission needs a separate assessment.

Add the chosen case to T43.

**Domain:** D3.

### N-07 — Coordination-record keys have no defined identity space (Medium)

**Section and invariant:** §5.4, §6.9, §10.5.1; CO1, T55.

**Counterexample:**

1. Alice records decision `db-choice` = PostgreSQL. Bob records decision `database` = SQLite, or the same topic under a Japanese key.
2. The same-key rule fires only on identical keys, so the 1a overview lists two “recorded” decisions with no conflict.
3. With no statements in Slice 1a, nothing else would catch it. Under D-19, keys are the first thing to diverge across languages.

**Severity:** Medium. Q5 asks whether the Slice 1a overview is non-misleading, and on this point it is not.

**Proposed alternative:**

- Require keys to come from a declared namespace per scope: identifiers from the system of record, or a small curated key registry.
- At entry, show existing similar keys as an inert proposal.
- Have the L0 coverage line say that conflict detection is limited to identical keys and that the rest of the memory is unscreened in Slice 1a.

**Domain:** D3 for the contract, D4 for the registry mechanics.

### N-08 — Locale-dependent parsing can change a grounded value (Medium)

**Section and invariant:** §5.9 (“values and formats”, detection at 0.8 or above), §7.2 grounding; ML1, F2.

**Counterexample:**

1. A direct-entry span reads “transfer 1.000”, where the language around it decides its meaning.
2. Language detection, a model output, labels the span German (1,000) or English (1.000).
3. §5.9 parses typed values with the span's locale before comparison. If that typed value feeds an argument binding, a misdetection changes the amount a thousandfold.
4. “Ambiguous resolution blocks the action” does not fire, because the detector is confident.

**Severity:** Medium.

**Proposed alternative:**

- Never use a detected locale for grounding or confirmation.
- Use the principal's declared locale or an unambiguous canonical form.
- Treat a value whose parse differs across plausible locales as ambiguous, which blocks it.
- Confirmation displays the canonical value.
- Add the case to T62.

**Domain:** D3 for the cross-section contract.

### N-09 — Gaps in retention bounds (Low–Medium; tension with F09)

**Section and invariant:** §11.2, §11.4, §12.2, §14.2; H1, AC4, D-13. Codex's F09 repair promised “protected lineage with bounded retention”.

**Counterexample:**

- **Access records.** An administrator can lengthen access-record retention to any length, and existing records can never be shortened again. They are then retained effectively forever, though they are sensitive metadata (principal, opaque target, time).
- **Redaction copies.** A redaction copy is “a new source unit”, and its deadline is unspecified. If raw retention (180 days from capture) restarts at redaction, repeated redaction extends retention indefinitely.
- **Ancestry of purged nodes.** This ancestry lives as long as any descendant. Repeated human republication can extend that chain. Each step is an explicit act, which is acceptable, but deletion status does not show how long it will last.

**Severity:** Low–Medium.

**Proposed alternative:**

- Set a tenant maximum for access-record retention, fixed at each record's creation.
- Have the redaction copy inherit the original's deadline.
- Have deletion status report the expected lifetime of retained ancestry.

**Domain:** D3.

### N-10 — Confirmation substitutes for departed users and agents are defined only for agent publishers (Low–Medium)

**Section and invariant:** §10.6.2, §7.3.7; TM1.

**Counterexample:**

1. The general rule requires that each non-owned ancestor's owner “has confirmed”.
2. The substitutes are stated only in the agent bullet: the scope's manager for a departed user, and the overseer for another agent.
3. For a human publisher, this has one of two readings:
   - the human can never publish anything with such an ancestor; or
   - by analogy, a team lead with `m` publishes a summary of a departed member's records and confirms on the departed owner's behalf. The lead alone then declassifies another principal's records, which is Q1's departed-user case.

**Severity:** Low–Medium.

**Proposed alternative:**

- State the substitutes for all publishers.
- Forbid a publisher from being its own substitute confirmer; require a second manager or an administrator, as for transferring oversight.
- Add the case to T48.

**Domain:** D3 decision.

### N-11 — Gate and test mapping (Low)

**Section:** §15, §16. Q7 asks whether the gates are thin and correctly mapped.

- **T62 is in Slice 1a-core, but tests grounding.** Slice 1a-core dispatches no actions (“no claim about unmediated Codex actions”). Its grounding clause belongs to Slice 1b.
- **T15 is in Slice 1a-core, but needs extracted claims.** Extracted claims and modalities arrive with Slice 2.
- **Several 1a invariants have no 1a-core test.** A2, AC6, E1 and P1 are marked “1a” but no Slice 1a-core test exercises them. A2's natural test, T25, sits in Slice 1a-team.
- **Elevated `create_scope` is not refused.** T51 does not cover an elevated administrator creating a scope with themselves as owner.
- **Slice 1a-core is single-user but not thin.** It carries import, export, redaction and the full purge, backup and restore lifecycle. Consider moving import and export (M1, T16) to Slice 1a-team or later.
- **D-17 is not adequate as an interim control.** See N-01.

**Domain:** D3 for the gate table.

### N-12 — Record accuracy (Low)

Q9 asks whether the records are accurate.

- **A.5 M-02** says the overseer “holds `m`”. §7.3.8 and D-9 give it `lrd`.
- **A.5 M-14** says §15.2 covers “T01–T58”. §15.2 now says T01–T62.
- **D-8 says “or scopes they manage”.** This wording appears in §18.2 and in the review request, but no agent principal holds `m` (D-9), so for agents the clause is empty.
- **A.4 CR06 is stale and unmarked.** It still describes candidate 3's two-administrator shortening, which M-19 replaced.
- **The review request names the wrong file.** `UPMS_Re-Review_Request_Candidate_4_1.md` calls the object under review `…_Candidate_4.md`, but it is stored as `…_Candidate_4_1.md`. A different `…_Candidate_4.md` also exists.

**Domain:** documentation.

## 4. Answers to the Request's Questions

1. **Publication.** Yes, through derivation in Slice 1a-team (N-01), and through human publishers with departed-user ancestors (N-10).
   - **Coordination records:** humans can always restate, which is inherent and accepted. Agent coordination records are N-01 in Slice 1a and N-02 from Slice 1b.
   - **Reuse of a confirmation for another target:** closed. Confirmations are single-use and bound to one target (§7.2, T48).
   - **Scope managers:** closed for members' records.
   - **Administrators:** closed except deliberate human restatement.
2. **Oversight.** List and read are consistent with AC3, AC7 and T44. Neither elevation nor a group grant widens them (T49), and elevated self-grants are refused (T51). Group grants do widen `c` and `d` beyond the overseer's rights (N-03).
3. **Ancestry retention.** It closes CR01's lineage and erasure paths (T30, T50) where ancestry is recorded. It stays bounded only partly in F09's sense (N-09), and is open where ancestry is not recorded (N-01).
4. **Overview economics.**
   - **Deadline-filtered view:** it covers regional passes but not global passes, L0 sections or notes (N-04).
   - **OV4:** budget-bounded coverage makes it true only if regions dropped from the budget are labeled before their deadline. That labeling is not stated (N-04).
   - **Coverage reporting:** honest, except that the estimate omits the scope count and the language multiplier (N-05).
5. **Coordination records.** They are coherent with §6.1. Commitments have one authority and an explicit key link, and overdue never closes a commitment. The Slice 1a overview is useful, but it is misleading where keys differ (N-07) and when agents' records cannot be read (N-02).
6. **Assessment and screening.** CR04 and CR07 are closed, and no §1.2 journey is blocked. Flag investigations, however, can never be admitted (N-06).
7. **Delivery.** The gates are mostly testable. They are not thin (Slice 1a-core is broad), and a few tests sit at the wrong gate (N-11). D-17 is not adequate (N-01).
8. **Multi-language support.**
   - **Mappings and translations cannot set a slot value, ground an action or suppress a flag.** Curated equivalence only joins slots; `close_match` yields at most a possible flag; translations are labeled synthesis.
   - **Detected locales can change a typed value (N-08).**
   - **Translation services are covered by processor policy.**
   - **Look-alike labels are flagged at proposal**, though not entity names inside extracted statements; screening only flags these.
   - **Curated equivalence plus `close_match` is adequate.** Where one language's word covers two concepts in another, mapping it to the broader concept loses conflicts between the narrower ones. That is acceptable only if screened coverage reports it.
   - **Degraded-coverage reporting is honest for languages without an analyzer**, but not for spans the detector misidentifies. Report the spread of detection confidence in coverage.
   - **T59's languages are a precondition.** T59 assumes Japanese and German. Bind the test to the languages named at Gate 0.
9. **Regressions.** No F01–F18 repair is weakened (§5). A1–A7 remain in place at the locations A.3 lists. Appendix A.5 has the inaccuracies in N-12. I could not check A.5 against the diff, because candidate 3 is not in the repository.

## 5. Regression Check: F01–F18

I checked each repair against Codex's review record (SHA-256 `b0617a92…`) and the current text.

| ID | Status in candidate 4 |
| --- | --- |
| F01 | Retained. Scope evidence epochs are checked at commit and at use, and unprocessed evidence invalidates (§9.3) |
| F02 | Retained, and strengthened: translation never grounds (§7.2). N-08 is a new edge case |
| F03 | Retained. The public-reader exception is disabled in the pilot (§7.2) |
| F04 | Retained (§7.2) |
| F05 | Retained (§8.3) |
| F06 | Retained, and extended to revocation stages (§9.4, §7.3.7) |
| F07 | Retained (§12.2). The redaction copy's deadline is a new gap (N-09) |
| F08 | Retained (§11.2) |
| F09 | Retained, in tension: lineage is kept for survivors (§11.2), but access records have no upper bound (N-09) |
| F10 | Retained. New submission paths are guarded (§4.3) |
| F11 | Retained. The coordination lifecycle (§6.9) matches the committed modality |
| F12 | Retained (§5.3, §7.6) |
| F13 | Retained (§9.1–§9.2) |
| F14 | Retained (§8.4) |
| F15 | Retained (§9.6, §12.6) |
| F16 | Retained. Coverage, counts and hub tokens are filtered by `l` or opaque (§10.3, §10.5.3) |
| F17 | Retained (§3, §16) |
| F18 | Retained (§14.1) |

## 6. Decisions

| ID | Position |
| --- | --- |
| D-1 to D-7 | Agree |
| D-8 | Agree in substance. Delete “or scopes they manage” for agents (N-12), and do not treat it as enforceable in Slice 1a-team until N-01 is repaired |
| D-9 | Disagree in part. Bound `c` and `d` on others' scopes too (N-03) |
| D-10, D-11 | Agree |
| D-12 | Agree. Add the redaction-copy deadline rule (N-09) |
| D-13 | Agree, with a tenant maximum fixed at creation (N-09) |
| D-14 to D-16 | Agree. D-15 needs a key namespace (N-07) |
| D-17 | Disagree. Overseer confirmation is not owner consent; adopt release-set propagation (N-01) |
| D-18 | Agree, provided the estimate and T54 include the scope count and the language multiplier (N-05) |
| D-19 | Agree, adding locale-explicit grounding (N-08), a narrative language policy (N-05) and tests bound to the named languages |

## 7. Evidence Ledger

**Read in full:**

- the object under review, all 1,547 lines (SHA-256 verified);
- `UPMS_Re-Review_Request_Candidate_4_1.md`.

**Read in part:**

- the F01–F18 findings table of `UPMS Architecture Review.md`.

**Not read:**

- `check_C4.md`;
- candidates 1 and 2;
- the earlier manual;
- proposals v0.1–v0.3;
- `UPMS_Round_2_Amendments.md`.

Regression against A1–A7 relied on the candidate's own Appendix A.3.

**Not available in the repository:**

- candidate 3;
- the candidate 2 cross-review (CR01–CR10);
- the candidate 3 interim review and sub-reports A, B and C.

For these, closures were checked only against the candidate's own summaries, and A.5 could not be checked against the diff.

**Limits:**

- This review is same-family, so it is not independent (see the header).
- No executable evidence exists or was produced.
- The Codex documentation cited in Appendix B was not reopened.
- Counterexamples are constructed traces through the text, not observed behavior.
- No realized scientific results were produced or reviewed. §1.4's determination that no D1 or D2 parent is needed was accepted, and no reopen trigger was found.
- No variant search was performed: one review pass, with no alternative reviews generated or selected among.
