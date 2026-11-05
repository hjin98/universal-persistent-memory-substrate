# UPMS Owner Decisions on the Candidate 6.5 Independent Review, 5 November 2026 (D-86 to D-89)

5 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**The product owner accepted the author's recommendations on the independent review of D1 candidate 1.5 and architecture candidate 6.5.** The author put them to the owner in a Claude Code session, and the owner answered: "Proceed". This record states those recommendations as decided and binds them to the review they answer. Claude wrote this record and cannot widen the decisions: where this record and the recommendations as put to the owner differ, the recommendations govern.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_5_Independent_Review.md` | `92ddcda5861711af8cdcdbd43a1b938767ab871cadd7ab6dbfbc8a8c8f2eb515` | Codex (OpenAI GPT family; the same reviewer and family as the 6.4 and proposal reviews) review: NO-PASS for D1 1.5 and for core 6.5 with anonymous-review annex 6.5; SC65-01, SC65-02, R65-01 to R65-03, simplicity §7 |

## 2. Decisions

**Common mechanism.** SC65-01 is the second failure in a row of the applicability rule (after SC64-01). The decisions therefore re-derive it once instead of patching it: one **reliance footprint**, the set of records a decision or claim relied on, from which both the applicable objections and the coverage statement are derived.

| ID | Decision | Answers |
| --- | --- | --- |
| **D-86** | **Replacing an assessment never ends an objection's applicability; only resolving the objection does.** A decision's footprint includes the endpoints of every assessment of its basis routes that was effective at any position from the decision's commit to the read, and the full chain of sharing originals of every record in it, not only one step. The footprint only grows and is derived from committed history; no registry is added. It replaces the rule that a decision keeps the objections it held at commit. A claim's own view stays current-only: it shows the claim as it stands now | SC65-01 |
| **D-87** | **The coverage statement is computed over the same footprint, by configuration alone.** It is shown when the reader cannot read some record in the footprint, or does not read every scope that may home objections to it, or works in a task with a lineage exclusion. A retired objection-home registration stays among the possible homes, so retiring one never removes the statement. An objection carries no restriction tag of its own: it is readable by a reader who reads its home and satisfies its target's restriction tags. A critic with sensitive material puts it in a separate restricted record and cites it; the cited record shows as an unreadable source. The alternative put to the owner (show the statement whenever a scope allows a tag that excludes the reader) was not adopted | SC65-02 |
| **D-88** | **Sharing is qualified, not guarded; a rebind checks the current audience.** This amends D-80. Sharing rechecks no audience and is never refused because of objections. A copy's reader who cannot read where the original's objections may be homed sees "shared copy: objections to the original may not be visible to you". A rebind is refused unless every current reader of the new target, including readers through an own-record entitlement and under its restriction tags, can read the objection's home; the refusal reveals nothing, because only the objection's author can rebind | R65-02 |
| **D-89** | **Relations have fixed target shapes.** `favors` compares exactly two distinct claim revisions; every other relation kind has exactly one target. A comparison among three or more alternatives is recorded as separate pairwise `favors` relations. A relation whose targets do not match its kind is refused when recorded; no bearing is assigned by default | R65-01 |

**Corrections that need no decision** (the author's to make):
- core §7.8 and §11.5 name the 6.3 anonymous-review annex instead of 6.5 (R65-03);
- D1 §11 names candidate 6.4 §17.2, and D1 §0.1 describes the 6.4 review as a review of candidate 6.5 (R65-03);
- the trajectories of SC65-01, SC65-02, R65-01 and R65-02 become acceptance scenarios;
- D-85 continued (review §7 items 1 to 4): D1's author chronology, its §14 catalogue of repaired drafting findings and the revision-by-revision anchoring notes of both texts move to their change histories; F-20a and SE1 cite the annex instead of restating it.

## 3. What this record does not decide

- **It accepts no text.** The revisions that apply these decisions stay proposed until a reviewer outside the Claude family has falsified them and the owner accepts them (`AGENTS.md`).
- **Independence.** The 6.4 and 6.5 reviews were by the same reviewer and family (Codex). The owner directed that reviews be run with the Codex CLI; a reviewer of another family would add independence before ratification.
- **The Gate 0 obligations** (pilot languages and profile, a bounded D4 specification, an executable evidence specification, runtime, storage, KMS and restore feasibility) stay open.
- **Warning frequency.** Whether the coverage statement is shown so often that readers ignore it is not decided by text; it is to be measured in E1, E4 and E5.
