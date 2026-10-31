# Check of UPMS Review Candidate 4 against the Candidate 3 Interim Review

**Object:** `c4_check.md`, SHA-256 `e34b4832918f5d829bab1447d3463ce9624921e98a4e275475ad7fb78107bf88` (verified with `sha256sum` before reading).
**Baseline:** `c3_frozen.md`, SHA-256 `dcf61fc1…2a97` (verified). The interim review hash cited in §1.1 and A.5, `d4626211…9834`, was also verified.
**Asserter:** Claude (AI) subagent, same model family as the author; independence limited. This is a documentary check only. Every trajectory is constructed and nothing was executed. No input file was edited.

## 0. Disposition

- **Closure.** Of the 26 findings, 18 are closed, 8 are partly closed and none is open. All five owner answers (Q1–Q5) were applied as recommended.
- **SC-1 is not fully closed.** The candidate keys the waiver on record ownership, which closes the original trajectory. Four new declassification paths now exist:
  - the waiver's "published" clause has no target (K-03);
  - dropping the scope-owner condition lets a team scope's records leave without the scope's manager (K-04);
  - the overseer's new `m` on an agent's private scope (K-05);
  - coordination records written straight into the shared pool (K-07).
- **SC-2 is not fully closed.** The deadline rule filters sources only, so the L2 pages that consolidation replays bring near-expiry deadlines back in (K-01). Under the candidate's own rules, the cost of deadline-driven re-consolidation grows with the volume of retained material (K-02).
- **Decision record.** The record misattributes several changed decision outcomes to the owner (K-10).
- **Severity.** I found no blocker that is a safety leak through the overview. Most of the permission findings are major and cheap to fix.

## 1. Closure table (M-01 to M-26)

| ID | Status | Evidence in candidate 4 | Residual |
| --- | --- | --- | --- |
| M-01 | **Partly closed** | §10.6.2: "a scope's requirement is dropped only when every ancestor record from that scope in the item's closure is owned by the publisher, or has been published or confirmed for this publication by its own owner". §7.2 C4: "an agent's self-publication under §10.6.2 is the one pre-authorized class". §10.6.3: "Required categories apply only to items whose waivable ancestry the agent owns entirely". Also TM1 and T48. | K-03, K-04, K-07, K-08, K-18 |
| M-02 | Closed | §7.3.8: "agent `lrwcd`; overseer `lrdm` as a protected grant"; the agent-operational scope adds "its overseer `lr`". §7.3.4 step 3: "keeps `w`, `c` and `d`, and it never holds `m`". AC3, T44. | The new overseer `m` reopens the widening hazard (K-05). |
| M-03 | **Partly closed** | §10.5.3 "Deadline-aware replay"; §10.5.4 "Replay cap … L2 pages and sources together"; accrual; budget-gated global passes; budget base per profile; §14.2 rows; T54. | K-01, K-02, K-15, K-16 |
| M-04 | Closed | §11.2: "a purged node keeps its opaque ancestry edges, segment membership and subject-discovery entries … until no descendant remains … Traversal that reaches a stripped node fails closed". H1, §10.6.4, T50. | — |
| M-05 | Closed for grants and ownership | §7.3.6: "An elevated administrator cannot grant rights to themselves or to agents they oversee, or take ownership of any scope; transferring an active user's personal scope requires a second administrator". T51. | Oversight self-transfer is not covered (K-06). |
| M-06 | Closed | §7.3.6 and §11.4: "durably committed to the replicated control plane (§12.4) before the content is released"; §12.4 "control and audit state"; §18.1 latency row; T51. | — |
| M-07 | Closed | §7.3.4 step 2: "when every input record in *t*'s ancestry is owned by that same principal"; §7.3.5 adds the same-scope sentence; AC7, T44. | The oversight-entitlement condition is ambiguous (K-13). |
| M-08 | Closed | §5.8: "Curation is a derivation, never a waiver … base vocabulary accepts only concepts with no requirement beyond what all users can read"; §9.8 "every scope in its requirement closure"; AD1, T53. | — |
| M-09 | Closed in the owning text | §7.3.4 step 3: "overseer's non-elevated `l` and `r`, recomputed for every scope checked in step 4"; §7.3.7: "transferring ownership or oversight, narrowing an overseer's rights (for every agent it oversees)"; T49. | The §9.4 and §6.7 lists are stale (S-2, S-3). |
| M-10 | **Partly closed** | §5.4 `CoordinationRecord`; §4.3 `record_coordination`, `close_coordination`; §6.9 lifecycle and same-key rule; §10.5.1 "never as 'in force'"; CO1, T55. | K-09: authority conflicts with §6.1. Checkpoints still carry obligations and decisions, so they remain a third owner. Claim-to-key matching is undefined. The record's retention is undefined. |
| M-11 | Closed | §10.5.3: "applies the same deterministic projection function to every canonical commit beyond the hub's projection watermark"; scan budget in §14.2; overlay split into change entries and notes (§10.5.2); OV1, T56, T57. | — |
| M-12 | **Partly closed** | §9.3: "The core enforces this at `submit_assessment` by ancestry … an agent claim written after reading a hub … never admitted"; endorsements admitted; T43 rewritten. | In the memory-service profile, UPMS does not record what an agent read (§8.1), so "an agent claim written after reading a hub" cannot be detected. E3 holds only where Slice 2 runs on 1b. |
| M-13 | Closed | §9.7: "suppressed only by an approval record … replay reads that evidence, never the identity provider's current state"; §5.4 approval records; §4.3 `record_approval`; T33. | — |
| M-14 | Closed | T30 is split into parts (a)/(b)/(c). T38 sits only at Gate 2. §15.2 now reads "T01–T58". T48, T50, T52 and T24 are added or extended. Every test from T01 to T58 is assigned to a gate. | New split-mapping gaps (K-11). |
| M-15 | Closed | §16 now has 1a-core and 1a-team gates; D-16. | K-11 |
| M-16 | Closed | §9.8: "Retention expiry is planned instead"; concept-scoped triggers; "Adaptation is query-side only in the pilot"; T35. | Minor wording conflict on the base-vocabulary threshold (S-14). |
| M-17 | Closed | §10.6.2: "publication records a retention extension, and the copy follows the target scope's retention"; §12.1 "including for retention expiry, for every ancestor the publisher does not own"; T52. | Conflicts with §12.1's "more restrictive deadlines win" (K-14). |
| M-18 | **Partly closed** | §2 "Dependency" row; §5.5 retitled; AC1 and C2 now use requirement and ancestry. | "Dependency" still means ancestry in §5 common fields, §8.2, §9.4, §9.8 and §13, which falsifies §2's "Elsewhere, 'dependency' means a requirement". "Waivable ancestry" and "item's closure" are undefined (K-18). |
| M-19 | Closed | §11.4: "a reduction applies only to records created after it takes effect, so no administrator can shorten the retention of existing records, their own included"; AC4, T24, D-13. | — |
| M-20 | Closed | §9.7 `ComparisonCue`; truth table; per-statement vocabulary versions; "Flags and cues are never required processing"; obligations reported as unscreened. | T32 wording is garbled (S-10). |
| M-21 | Closed | §10.5.3: "one invocation per scope … Cross-area analysis is a separately budgeted optional step". | A global invocation's input has no cap (K-16). |
| M-22 | **Partly closed** | §10.5.1: "Recent events from R- or X-class sources appear in L0 only as locators"; "the 1a overlay is measured from the reader's or task's last checkpoint". | Coordination-record values and checkpoints still appear verbatim in L0, with no source-class rule. A reader with no checkpoint has an unbounded overlay (K-19). |
| M-23 | Closed | §10.5.5: "checkpoint or explicitly pinned item … task continuation"; hubs excluded; T47. | "Pinned item" has no operation, and "pin" means a retention extension in §14.2 (S-12). |
| M-24 | Closed | §10.6.4: "Only principals with list rights on the named sources, or the task's coordinator role"; §10.6.2 "private source of ⟨publisher⟩"; T58. | "Coordinator role" is undefined. Foreign endpoints are mislabelled as the publisher's (K-20). |
| M-25 | **Partly closed** | Currency wording, derived overlay, slot "stated by", T21, figures, deletion status listing copies, revocation-stage edges, Gate 0 MCP identity and §15.2 C4 wording are all fixed. | Per A.5 itself, "a full per-value origin column is not restored" (F17). T44's "ownership transfer keeps these rules" still has no oracle. |
| M-26 | **Partly closed** | A.4 is corrected, §18.2 has its alternatives column again, and the decision history is stated. | A.5 is itself inaccurate (K-12), and §18.2 misattributes changed outcomes (K-10). The A.4 c2→c3 list was not verified, because candidate 2 was out of my read scope. |

**Counts:** 18 closed, 8 partly closed (M-01, M-03, M-10, M-12, M-18, M-22, M-25, M-26), 0 open.

**Owner answers Q1–Q5.**

| Q | Applied? | Notes |
| --- | --- | --- |
| Q1 | Applied | §10.6.2 and D-8 key on record ownership. D-9 bounds reach only, and agents never hold `m`. Applying it exposed K-04 and K-05. |
| Q2 | Applied | D-13: "no shortening path", and reductions apply only to later records. |
| Q3 | Applied | D-12 and §10.6.2 as recommended. |
| Q4 | Applied | The coordination control has key, value, author and supersedes, plus an operation, a lifecycle and a same-key rule, and it shows "recorded". The candidate also adds `interface_agreement`, `due` and `withdrawn`. |
| Q5 | Applied | 1a-core also carries coordination records and the overview, which follows from D-15. |

## 2. New defects (most severe first)

### K-01 · §10.5.3 deadline-aware replay against §14.2 and §12.1 · **Major (SC-2 remains open in Slice 2)**

The rule filters only *sources*: "takes as narrative input only sources whose retention deadline is at least the planned narrative lifetime away". But a regional pass "Replays the region's L2 pages and the sources selected under the deadline rule", and the L2 pages are not filtered. Under §14.2, derived artifacts expire "No later than the earliest required input deadline". A narrative unit "depends on every input of that invocation" and records "the earliest retention deadline among those inputs".

**Trajectory:**
1. Entity page E lists statement s1, extracted from event e1, which was captured on day 0 and has its deadline on day 180.
2. Consolidation runs on day 160. e1 is excluded as a source, but page E is replayed and its ancestry includes s1 and e1. The unit's deadline is therefore day 180, 20 days away rather than 30.
3. In steady state, page E always contains a statement from the oldest retained source, so the unit's deadline is about one day. This is exactly the SC-2 mechanism, now running through L2 pages.

The sentence "older material reaches the narrative only through exact projections and the claims and coordination records that outlive it" is also false:
- claims expire with their sources (§14.2 derived-artifact row; §14.2 note "the derived record expires");
- coordination records have no retention row at all.

**Fix:**
- Apply the deadline filter to every input, including L2 lines and statements, through a deadline-filtered L2 view.
- Drop "claims … that outlive it", or define a retention basis that actually outlives the source.
- Bind coordination-record retention in §14.2.
- Extend T54 to check that the L2 path is covered.

### K-02 · §10.5.4 cost model and planning estimate against §14.2 · **Major**

Every narrative unit, including every sub-hub's, now needs re-consolidation within 30 days, changed or not. Steady-state demand is therefore about (eligible retained replay tokens) ÷ 30 per day. That contradicts §10.5.4's claim that work grows "not with the retained history of the whole archive", and it contradicts OV4.

The estimate assumes "twenty capped regions", meaning at most 1.2 M replayable tokens tenant-wide. At the §14.2 corpus envelope there are about 83,000 eligible events, which is about 14 tokens per event. At an illustrative 200 tokens per event:

| Quantity | Value |
| --- | --- |
| Eligible tokens | ≈ 16.7 M |
| Capped sub-hubs | ≈ 280 |
| Deadline-driven input per day | ≈ 556,000 tokens, above the 500,000 absolute cap |

T54 ("at the corpus envelope … over twenty areas") is therefore internally inconsistent: twenty areas at the envelope divide into hundreds of sub-hubs.

There is also no priority rule between triggers. The 7-day trigger (≈ 171,000 tokens/day for 20 regions) and the 20 % overlay trigger (600 tokens on a 3,000-token L1) compete for the same budget. If they win, deadline passes are deferred, units expire and are withheld, the "withheld unit" trigger fires, and demand rises further. That is the SC-2 feedback loop again.

**Fix:**
- State that demand scales with retained eligible volume, and bound the volume or the coverage instead. For example, consolidate only sub-hubs with retrieval demand, and leave the rest projection-only.
- Give deadline passes priority over fragmentation triggers.
- Recompute the estimate from the envelope (see §4).

### K-03 · §10.6.2 waiver clause "published or confirmed for this publication by its own owner" · **Major (blocker if the unbound reading is intended)**

The clause has no target binding for "published".

**Trajectory:**
1. Human H publishes message m1 from agent Ag's private scope P_Ag to a two-person scope S1.
2. Ag derives summary s from m1 and publishes s to team scope T.
3. Every P_Ag ancestor of s is now either Ag-owned or "published by its own owner", so the P_Ag requirement is dropped.
4. T's readers see m1's content although H published it only to S1.

The waiver also survives H withdrawing the publication from S1. T48 does not test this.

**Fix:** Waive only if the owner published that record *to the same target scope or a narrower one*, or confirmed this exact publication. Re-check at withdrawal.

### K-04 · §10.6.2, §2, §7.4: the record-ownership key drops the scope manager's control · **Major (regression from candidate 3; owner question)**

Candidate 3 waived only "on scopes the publisher owns". Candidate 4 waives any scope whose ancestors are all publisher-owned.

**Trajectory:**
1. Agent principal Ag is a member of a confidential client team scope T1 (`lrw`) and writes notes there; Ag owns them.
2. In the memory-service profile (Slice 1a-team), Ag's notes carry no ancestry to the client documents it read (§8.1, "Only UPMS-owned workers").
3. Ag publishes its notes to the organization-wide scope, where it is a contributor. All T1 ancestors are Ag-owned, so the T1 requirement is waived.
4. This is a pre-authorized C4 class (§7.2), so no human is involved. The client content becomes readable by "all users".

Humans who write in T1 can do the same thing. The scope's `m` holder never consents.

**Fix:** Waive a scope's requirement only when both conditions hold: the publisher holds `m` on that scope (or the scope is the publisher's own private scope), and every ancestor from it is publisher-owned or owner-confirmed. Alternatively, record the owner's explicit choice in D-8.

### K-05 · §7.3.8 overseer `lrdm` against §10.6.2 and D-8 · **Major (the SC-1 harm with a different actor)**

The A-02 "repair hazard" was `m` on a scope that holds human-owned messages. Candidate 4 removes `m` from the agent but gives it to the overseer.

**Trajectory:**
1. Human H (not the overseer) messages agent Ag, overseen by O. The messages are owned by H and stored in P_Ag.
2. O calls `set_permissions` on P_Ag with "other `lr`". §6.7 "Grant or widen … effective immediately".
3. H's private messages become readable by the whole tenant, with no publication and no involvement from H. D-8's "keeps that human's requirement unless the human publishes" is bypassed.

**Fix:** Nobody may widen a scope that holds records owned by a principal other than the scope's agent and overseer without those owners' consent. Alternatively, give the overseer `m` only for narrowing and deletion.

### K-06 · §7.3.6 against §10.6.5: elevated oversight self-transfer · **Major (M-05 pattern)**

§7.3.6 forbids elevated self-grants and ownership-taking, and §10.6.5 says "only an administrator can transfer oversight". Nothing forbids an administrator from transferring oversight *to themselves*.

**Trajectory:**
1. Administrator Ad elevates and transfers oversight of agent Ag to Ad.
2. Ad now permanently holds the protected `lrdm` grant on P_Ag (including third parties' messages) and the oversight entitlement on every Ag-owned record, all through ordinary, unaudited rights after the elevation ends.
3. No owner is notified, because P_Ag is not a "personal scope".

A self-grant made through a group that contains the administrator is also not explicitly barred.

**Fix:**
- Add oversight transfer to the elevated prohibitions, or require a second administrator plus notice to the old overseer.
- State that grants to groups containing the actor count as self-grants.
- Extend T51.

### K-07 · §10.6.3 and §4.3 `record_coordination` against D-8 and TM1 · **Major**

§10.6.3 says decisions "are captured as coordination records (§5.4) in the shared pool". `record_coordination` needs only `w` on that scope, and it is not a publication, so neither the waiver test nor the confirmation queue applies.

**Trajectory (1a-team, memory-service profile):**
1. H privately tells Ag: "we drop vendor X, don't tell the team".
2. Ag calls `record_coordination(kind: decision, key: vendor, value: "drop vendor X", scope: T)`.
3. No ancestry is recorded (§8.1), so every T member's L0 shows the decision.

In the instrumented profile the record inherits P_Ag's requirement, and the required "Published immediately" decision silently becomes invisible to the team.

More generally, TM1's clause "an agent needs the owner's confirmation for anything derived from a human's records" is a runtime-propagation property (F1, a Slice 1b property) placed at 1a-team. T48 cannot be realized there.

**Fix:**
- Make agent coordination records in a shared scope subject to the same waiver test.
- Move TM1's derivation clause and T48 to 1b, or declare it unenforced in the memory-service profile.
- Reconcile "Published immediately" with "captured as coordination records".

### K-08 · §10.6.3 confirmation queue against §7.3.4, §4.3 and §10.6.2 · **Major**

The queued item is owned by Ag and homed in P_Ag. A human H who is not the overseer has no right on P_Ag, and the own-record entitlement does not apply, so showing H the item would violate AC1.

The alternatives do not work either:
- "Unless the human publishes" is impossible, because `publish` requires item ownership (§4.3).
- No confirmation operation exists in §4.3.
- The queue appears on no §17.2 inspection surface.

The D-8 confirmation path therefore works only when the human is the overseer.

**Fix:** Define `confirm_publication` (C4, by the ancestor's owner). Define a release rule that lets the confirming owner read the candidate item. Add the queue to §17.2.

### K-09 · §6.9 against §6.1 and §5.1: commitment authority · **Major**

§6.9: "Only the author, or a holder of `c` on the scope, closes or supersedes a record." That lets a commitment's author mark it fulfilled, released or withdrawn with no receipt and no counterparty. §6.1 says the opposite: "Scope policy defines who may release a commitment … a model cannot invent a counterparty's approval". §5.1 says actual completion "needs a receipt".

**Trajectory:** An agent closes its own overdue commitment as `fulfilled`. The obligation leaves L0's exact lines and task continuation (§10.2: "confirmed completion distinct from intention").

Three further gaps in the same area:
- "Matches an open coordination record's key" has no matching rule. Claims have no key, and matching is model-proposed, so it is not deterministic.
- A committed claim extracted later from an old message, matched against a record that is already fulfilled, opens a new obligation (resurrection).
- §6.1 lacks `withdrawn`.

**Fix:**
- Show `fulfilled` as "claimed by ⟨author⟩" unless it is receipt-linked.
- Make releasing or withdrawing a commitment follow §6.1's scope policy.
- Define deterministic key linkage (an explicit key reference at capture).
- Link checkpoint obligations to records.

### K-10 · §18.2 decision record · **Major (record integrity)**

The lead says the owner, after the interim review, "accepted the revised D-8, D-9, D-12 and D-13 and the new D-15 and D-16". But the outcomes of five other decisions were also rewritten:

| Decision | Change in candidate 4 |
| --- | --- |
| D-1 | "replicated control plane" |
| D-5 | Adds "oversight entitlements" |
| D-6 | "including summaries saved in the same scope" |
| D-10 | "Slice 1a-team" |
| D-11 | "query-side only in the pilot" |

The changes to D-6 and D-11 are substantive. They now read as owner-accepted.

**Fix:** Mark these five as consequential D3 edits pending owner confirmation, or record that the owner confirmed them.

### K-17 · §10.5.4 and §14.2 budget discontinuity · **Major** (listed here by severity)

In the measured profile, task usage of 700,000 tokens per 7 days gives 15 % = 105,000 per week, about 15,000 per day. Just below that threshold the bootstrap is 100,000 per day, so the budget falls by about 85 % as usage *rises*.

- **Estimate.** Consolidation needs 40,000/day, which requires usage of at least about 3.73 M tokens per week. Between 0.7 M and 3.73 M per week, the planning estimate fails.
- **"One capped pass always fits".** With 7 days of accrual (105,000) and only the reserved half usable, the share is 52,500, which is less than 60,000 plus output. This fails for usage below about 0.8 M per week.
- **Undefined value.** §10.5.4's "configured daily allowance" for the unmeasured profile has no §14.2 value.

**Fix:** Budget = min(cap, max(bootstrap, share)). Bind the allowance.

### K-11 · §16 slice split against §15 and §15.1 · **Minor**

The §16 note makes every "1a" invariant a 1a-core obligation except AC2–AC5, TM1 and TM2. Several others cannot be fully tested in a single-user slice:

- **AC7** ("overseers can do the same for their agents' records") is listed in Gate 1a-core, but its test T44 is at 1a-team, and 1a-core has no agents.
- **CO1 and T55** need "a supersession by someone without curate rights", which means a second principal, which 1a-core does not have.
- **H1** "traversal reaching a stripped node fails closed" and **C2** "across publications" depend on lineage exclusion and publication, which are 1a-team features.

**Fix:** Add AC7's overseer clause, CO1's multi-author clause, and H1's and C2's publication paths to the note's exception list. Mark T55's second half as 1a-team.

### K-12 · Appendix A.5 accuracy · **Minor**

- It lists SC1 as a changed invariant in rows M-13 and M-20. The diff shows SC1 unchanged.
- Changed sections §6.8 ("revision" became "copy"), §7.3.2 (the per-record rights sentence), §7.4 (the declassification sentence) and §13 ("exact projections unaffected") are mapped by no row.
- The M-09 row implies restriction-commit coverage, but §9.4 and §6.7 were not updated.
- The §1 claim that A.5 was "built from a section-level comparison" is therefore overstated.
- A.4's "Also changed" line was silently edited from §10.6.3 to §10.6.2.

### K-13 · §7.3.4 step 2, oversight entitlement · **Minor**

"An overseer holds the same `l` and `r` on every record its agent principal owns" is not explicitly limited to records built only from the agent's own records. AC7's "the same" implies the limit.

**Trajectory:** Under the literal reading, overseer O is removed from team T and still reads Ag's summary of T records. That holds unless step 4 is read as applying after entitlements, which §7.3.4 does not say for this entitlement.

**Fix:** Write "on every record its agent principal owns that is built only from that agent's records; others are checked under step 4".

### K-14 · D-12 retention extension against §12.1 · **Minor**

§12.1 says "More restrictive applicable deadlines win" and keeps per-category retention. §10.6.2 says the copy "follows the target scope's retention". The text does not say which wins for a category such as 30-day PII.

An agent's pre-authorized self-publication also extends the retention of its own captured material (the agent owns X-class material captured for it) with no human involved.

**Fix:** The copy's deadline is the stricter of the target scope's and category retention. The owner should confirm whether agents may extend retention this way.

### K-15 · Deadline rule against short-retention scopes · **Minor**

A scope whose retention is 30 days or less never has a source "at least the planned narrative lifetime away", so its narrative is permanently empty, and nothing discloses this.

**Fix:** Set lifetime = min(30 d, a fraction of the scope's retention), or disclose the empty narrative.

### K-16 · §10.5.3 and §10.5.4 global pass · **Minor**

"One invocation per scope" reads all of that scope's L1 hubs, including sub-hubs. No cap applies to that input. A scope with 400 sub-hubs feeds about 1.2 M tokens into one invocation, which exceeds model context and any daily budget, so the pass is deferred forever.

"Their number grows with archive size divided by the cap" describes L1 hubs, not passes.

**Fix:** Cap global-pass input, and use hierarchical L1 rollup.

### K-18 · Terminology: "waivable ancestry", "item's closure", "region" · **Minor**

- **"Waivable ancestry"** (§10.6.2, §10.6.3, D-8) is undefined. If it means ancestors whose requirements could be waived at all, then a human's message is non-waivable. An agent's derivative of it then has wholly self-owned waivable ancestry, publishes with no queue, and §10.6.3's queue never fires. T48 depends on which reading is meant.
- **"The item's closure"**: ancestry closure or requirement closure?
- **The §2 "Dependency" row**: "The requirement closure is the union over all ancestors" ignores waivers.
- **"Region"**: it is defined as "consolidated as a unit", yet it is divided into sub-hubs above the cap. "Project" areas can span scopes, while §10.5.5 says "Hubs are built per scope". It is unclear which quantity "exceeds the replay cap". "Does not split or merge regions dynamically" conflicts with division as an area grows.

### K-19 · L0 injection and overlay bound (M-22 residual) · **Minor**

- Coordination-record `value` text and checkpoint text, including agent-entered text whose class is undefined, are rendered verbatim into every blank model's L0.
- A reader or task with no checkpoint has an overlay that runs from the beginning of retention.

**Fix:** Render R-, X- and M-class coordination values and checkpoints as attributed data under the locator rule, or with a source-class label. Bound the overlay when no checkpoint exists.

### K-20 · Small contradictions · **Minor**

- §15.2: "C4-heavy tasks … never exempted from their confirmation rule" conflicts with §7.2's pre-authorized C4 class. Whether C3's X-payload confirmation applies to self-publication of X-influenced items is unstated.
- §10.6.2 labels every unlistable endpoint "private source of ⟨publisher⟩", which misattributes foreign ancestors, such as a client document, to the publisher.
- An item derived from another *agent's* records, or from a departed user's, has no defined confirming owner.

## 3. Stale phrases

| # | Location | Stale phrase or conflict |
| --- | --- | --- |
| S-1 | §18.1 KMS row | "full tests at Gate 1a". That gate no longer exists. |
| S-2 | §9.4 | "**Restriction commits** include corrections, deletions, permission narrowing, group-membership removal, ownership transfer and the end of an elevation". Oversight transfer and overseer narrowing are missing (cf. §7.3.7). |
| S-3 | §6.7 table | "Narrow, remove member, transfer ownership". Oversight transfer is missing. "Grant or widen … elevated administrator" is unqualified against §7.3.6. |
| S-4 | §9.4 | "rejected through validated dependency closure". |
| S-5 | §5 common fields | "restrictive dependency reference". |
| S-6 | §9.8 | "has restrictive dependencies on every record it was trained on". This means ancestry. |
| S-7 | §8.2 | "may narrow dependencies only through a specified and tested contract". Per §5.5 this limits acquired *ancestry*. |
| S-8 | §13 | "Dependency cycle, missing reference or traversal limit". This means the ancestry DAG. |
| S-9 | §2 | "Elsewhere, 'dependency' means a requirement". S-4 to S-8, `read_dependencies`, "current-head dependency contract" and "its own dependency contract" (§9.8) all contradict it. |
| S-10 | T32 | "only a recorded comparison cue, `different_dimension` cue". Garbled. |
| S-11 | §10.5.4 | "Global passes … their number grows with archive size divided by the cap". Passes are one per scope. |
| S-12 | §10.5.5 | "explicitly pinned item". There is no pin operation, and "pin" in §14.2 means a retention extension. |
| S-13 | §10.6.3 table | "Published immediately" for ownership claims and decisions, against "captured as coordination records in the shared pool". |
| S-14 | §9.8 | "a threshold of newly approved aliases in its scope or the base vocabulary". T35 says a base alias retrains "only adapters whose training set uses the concept". |
| S-15 | §10.5.4 | "otherwise a configured daily allowance". No §14.2 value exists. |
| S-16 | §6.1 committed | Lacks `withdrawn` (cf. §6.9). |
| S-17 | §10.5 lead | "starts from a small, current map". Unqualified, against "current at read or marked stale". |
| S-18 | §10.5.4 | "so one capped regional pass always fits". False in the measured profile near the threshold (K-17). |
| S-19 | T44 | "ownership transfer keeps these rules". Still no oracle (A-12 residual). |
| S-20 | §10.5.3 | "claims and coordination records that outlive it" (K-01). |

## 4. Planning-estimate check (§10.5.4)

The claim: "twenty capped regions every 30 days needs about 40,000 tokens a day, inside the bootstrap consolidation share".

| Item | Value or assessment |
| --- | --- |
| Arithmetic | 20 × 60,000 ÷ 30 = 40,000 input tokens per day. **Correct for input tokens only.** |
| Share | The bootstrap is 100,000/day, and "at least half" is reserved, so the share is 50,000. 40,000 is 80 % of it. |
| Omitted: outputs | About 3,000 per pass is about 2,000/day. |
| Omitted: weekly global passes | 20 × 3,000 L1 tokens = 60,000 per week, about 8,600/day plus outputs. |
| Omitted: other work | Narrative statement extraction for contradiction screening; retries after failed screening. |
| Omitted: slack | Re-consolidating *before* the deadline on a 25-day cadence gives 48,000/day. |
| Realistic total | About 50,000–58,000/day: **at or above** the share. |
| Other §14.2 triggers | The 7-day trigger alone gives about 171,000/day, more than the whole bootstrap budget. With no priority rule, it starves deadline passes (K-02). |
| Corpus envelope | The estimate needs at most 1.2 M tokens of eligible replay material tenant-wide, about 14 tokens per live event at the envelope. At 200 tokens per event (illustrative), deadline-driven demand is about 556,000/day; at 50 tokens per event, about 139,000/day. Either way it exceeds the share, and the first exceeds the 500,000 absolute cap. |
| Measured profile | Usage between 0.7 M and 3.73 M tokens per week gives less than 40,000/day for consolidation (K-17). |

**Verdict:** the arithmetic is right, but the premise ("twenty capped regions") is not derived from the §14.2 envelope, and the conclusion ignores the other triggers and the measured-profile budget. It should be relabelled a best case, with the envelope-derived figure stated, and T54's oracle tied to a stated tokens-per-event assumption.

## 5. Evidence ledger

- **Asserter:** Claude (AI) subagent, same model family as the author; independence limited.
- **Hashes verified with `sha256sum`:** c4_check.md `e34b…f88`, c3_frozen.md `dcf6…a97`, interim review `d462…834`.
- **Read in full:**
  - c4_check.md, lines 1–1457 (all sections through A.4 and A.5; Appendix B, lines 1491–1511, was not read);
  - `diff c3_frozen.md c4_check.md` (612 lines);
  - UPMS_Candidate_3_Interim_Review.md;
  - review_A_permissions.md.
- **Read in part:**
  - review_B_overview_screening.md: B-01 to B-16 and the CR table header;
  - review_C_consistency.md: §4 and §5.
- **Not read:** candidate 2 (outside the permitted file list), so A.4's c2→c3 section list is unverified. Also not read: the round-2 amendments, other /tmp or /root files, transcripts and memory.
- **Method:** text comparison and constructed trajectories. Every numeric demand figure in §4 uses the §14.2 defaults plus stated illustrative tokens-per-event assumptions; none is a measurement. No implementation, simulation or model run was performed.
