# UPMS Architecture Manual, Review Candidate 6.3: Slice 4 Annex (consolidation and maintenance cost)

3 November 2026 · drafted by Claude (AI, Opus 5.5) for the product owner (Sam)

**Status:** part of review candidate 6.3, proposed D3 architecture; not accepted-current. Reviewed before Gate 4, not at Gate 0 (D-56). Section numbers are those of the core, `UPMS_Architecture_Manual_Review_Candidate_6_3.md`, whose terms, invariants (OV3 narrative part, OV4 to OV6), tests and decisions govern this text. The text is moved unchanged from candidate 6.2 §10.5.3, §10.5.4 and §14.2, except for headings, at the same-family review's suggestion (F62 §3.7 item 1). The core keeps exact projections, read-time catch-up and the projection mode, which Slice 1a needs; everything here is built only if E2 supports consolidated narratives (§15.2, §16).

### 10.5.3 Consolidation

**Exact projections are current at read or explicitly marked stale; the narrative becomes coherent through consolidation and is always labeled as synthesis.** Fast updates never edit the narrative piecemeal; they accumulate in the overlay, and consolidation, a regional replay that rewrites a region's narrative as one coherent piece, absorbs them.


| Mode | When | What it does | LLM? |
| --- | --- | --- | --- |
| Overlay note | When a significant change reaches a hub about to be read, or at the end of a task | Adds a short source-linked note, labeled synthesis; never edits the narrative | Optional, bounded |
| Regional consolidation | When the region's fragmentation crosses its threshold and budget remains; at idle time | Replays the region's L2 pages and selected sources, within the replay cap; rewrites its narrative units; absorbs the overlay; checks synthesis (§9.7) before replacement | Yes, batched |
| Scope L0 rewrite | After a regional consolidation of the scope, and in the weekly global pass | Rewrites the scope's L0 section from its consolidated L1 units, one invocation per scope | Yes, batched |
| Global consolidation | Weekly, only when at least one region changed and the estimated work fits the budget | Runs the scope L0 rewrite for each changed scope; schedules retraining only of adapters whose training inputs changed | Yes, batched |

- **Overlay, not edits.** Between consolidations the narrative does not change; readers see it with its watermark, followed by the overlay.
- **Fragmentation and importance drive consolidation, never deadlines.** Each hub tracks overlay size, withheld narrative units, age of its narrative, and contradiction, omission and characterization flags against its exact projections. Crossing a threshold schedules regional consolidation when the estimated work fits the budget; regions are ordered by retrieval demand, importance (§12.1) and explicit priority. Candidate 5's deadline-aware replay, deadline-filtered views, narrative lifetimes and L0 deadlines are removed (D-25).
- **Archived material** is not narrated: consolidation reads active records only, and a region whose material is archived says its narrative covers active records.
- **Full replay, interleaved.** Consolidation re-reads old and new material together, not only the delta.
- **Bottom-up order.** Regions consolidate from L2 to L1; scope L0 rewrites then rebuild each scope's L0 section from its consolidated L1.
- **Significance.** Decisions, rule changes, obligations, commitments, conflicts and flags, objections and their resolutions, retractions and review obligations, corrections, deletions and sharing always propagate upward; routine items stay at L2 (in Slice 1, in the overlay) unless retrieval demand or explicit priority raises them. A small classifier may propose significance; deterministic rules decide.
- **Understanding as an output.** Consolidation also proposes what deserves to be learned: recurring patterns, lessons from dead ends, cross-area dependencies, emerging rules, vocabulary changes. Each is a `hypothesized` claim attributed to the consolidation run, linked to its supporting instances, and evidence-only until judged or endorsed. Such claims are pointers, never support (§9.3).
- **Guarding against consolidation errors.** The archive stays verbatim; generalizations are labeled hypotheses; citations must resolve to sources readable by the narrative's readers; a new narrative replaces the old one only if synthesis screening passes (§9.7); and the diff from the previous consolidation is recorded. **Passing these checks does not certify that the narrative is supported or faithful**: an unsupported causal link outside any slot can pass them, which is why the narrative is always labeled synthesis.
- **Deletion, correction, quarantine and loss of access.** When an input of a narrative unit or note is deleted, corrected or quarantined, the whole unit is withheld; when an input becomes unreadable to a reader, the unit is withheld from that reader. The hub falls back to exact projections and the overlay until the region is re-consolidated from surviving inputs.
- **Stability.** Structure and wording are kept where facts have not changed, by aligning the new narrative with the previous one after generation; the previous narrative is never an input to its replacement. Churn is measured.
- **Piggybacking.** At the end of a task, the working agent's checkpoint becomes overlay notes for its area at little extra cost, labeled as synthesis; consolidation checks them against sources.

### 10.5.4 Maintenance cost

**Maintenance work is bounded per pass and has its own budget, so it never competes with the work it supports.** Work per pass is capped by the replay cap and total work by the budget (§14.2); what grows with the archive is the share of it left projection-only, which is labeled.

- Projection, standing and impact traversal are database work; overlay notes are small; consolidation is the main LLM cost.
- **Regions.** A region is one scope's area; a project spanning scopes has one region per scope. When a region's input exceeds the replay cap, consolidation divides it into sub-regions with their own L1 sub-hubs, by entity or question, then by time window; regions never merge across scopes.
- **Global passes** read one scope's consolidated L1 hubs per invocation, capped at the replay cap, rolled up hierarchically when needed.
- **No per-reader or per-language LLM cost.** L0 is composed per reader deterministically from per-scope sections; narratives are written in the scope's narrative language only (§5.9); translations a reader requests are charged to that reader's task budget.
- **Budget.** Maintenance has its own quota below task work (§14.2), at least half reserved for consolidation. Correction, deletion, quarantine and permission invalidation are deterministic and never budget-limited.
- **Graceful exhaustion.** When the budget is spent, the narrative ages and the overlay grows, both labeled. Coherence and freshness degrade; exact projections, standing and invalidation do not.
- **Measured:** maintenance-to-work cost ratio, replayed input tokens per pass, deferred work, narrated fraction per region, overlay size and withheld units at read time, synthesis flags, churn, and cold-start success (§15.2). Without expiry, the narrated fraction is bounded by budget against active-record volume; T54 measures it (D-18).

### 14.2 Pilot defaults for this annex

| Parameter | Initial value or rule |
| --- | --- |
| Consolidation triggers | Regional consolidation when a hub's overlay exceeds 20% of its token budget, a narrative unit is withheld or a synthesis flag is raised, ordered by retrieval demand, importance and priority; global consolidation weekly when a region changed, subject to the budget |
| Maintenance budget | min(500,000, max(100,000, 15% of the tenant's measured daily task-model tokens over a rolling 7 days)) tokens per day; 100,000 where task usage is unmeasured; unused budget accrues up to 7 days' allowance; at least half reserved for consolidation; invalidation exempt |
| Overview replay cap | ≤ 60,000 input tokens per regional pass, L2 pages and sources together |
| Adapter retraining after training-source deletion | Within 24 h; older qualifying adapter or base model serves meanwhile |
