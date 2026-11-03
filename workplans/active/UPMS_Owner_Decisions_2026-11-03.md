# UPMS Owner Decisions, 3 November 2026 (D-37 to D-46)

3 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**The product owner accepted every author's recommendation in candidate 6.1 §18.2 and §18.3.** The owner's words, in a Claude Code session: "Yes I accept the recommendations, proceed." This record states what that acceptance decides, binds it to the exact text it refers to, and states what it does not decide. Claude wrote this record and cannot widen the decision: where the record and the bound text differ, the bound text's recommendation is what the owner accepted.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_1.md` | `d9246151302ba268569b89ffd95cc42905413b61cc9a489defb339dc1fe0b91a` | The recommendations accepted: every "Author's recommendation" entry in §18.2 and §18.3, and the recommended texts they point to (§1.2, §7.8, §9.10, §9.13, §12.3) |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_1.md` | `c1fafce3afa25678978a5a9b1259b3d5b9d926d00714c97d08cdc611a830752d` | The D1 recommendations accepted: F-8 (D-36 reading), F-9a (de-attribution), §6.5 (deferral) |

Neither file is changed by this record. Where those texts say "pending", "open", "proposed (open)" or "author's recommendation" for an item below, read it as decided here.

## 2. Confirmations of earlier decisions

| Decision | Confirmed outcome | Where |
| --- | --- | --- |
| D-1 | Administrator reads of personal scopes, as simplified: logged in the canonical store before release; the owner sees the access records. It also governs drafts an anonymous critic keeps in a personal scope, which the review tells the critic | 6.1 §7.3.6, §7.8, §11.4 |
| D-4 | Groups come from the identity provider; revocation as change and observation | 6.1 §7.3.7 |
| D-8 | Moot under D-24: publication becomes sharing, with the required sharing categories for agents | 6.1 §10.6.2–§10.6.3 |
| D-9 | An agent principal's read is capped at its overseer's; curate capped outside its own scopes; write uncapped; never `manage`; the overseer grant is protected. The review chair is a service role outside the cap, and only the critic's own agent or a temporary review-service session may assist an anonymous critic | 6.1 §7.3.1, §7.8 |
| D-16 | Slice 1a split, with import and export in 1a-team | 6.1 §16 |
| D-18 | Narrative coverage reported as a measured fraction, without expiry | 6.1 T54 |
| D-19 | One narrative language per scope; detected locales never decide a typed value | 6.1 §5.9 |
| D-29 (importance, left proposed) | Recency of use only orders records that already have a substantive reason; it is never itself a reason (C6-2) | 6.1 §12.1 rule 4 |

## 3. New decisions

| ID | Decision | Where |
| --- | --- | --- |
| **D-37** | **D-36 is read narrowly.** An anonymous objection is never a procedural veto. An attributed judgment that independently establishes what it pointed out changes the route's status like any judgment, whoever supplied the lead | D1 F-8; 6.1 §5.11 (SC-TE04) |
| **D-38** | **SCIRE's objection rule** requires a consequential decision's basis statement to address every unresolved objection in its applicable set, anonymous or signed. This gives no objection a veto. It binds SCIRE's front-end specification, not the UPMS core | D1 F-8; 6.1 §18.2 D-36 row |
| **D-39** | **Judgment on judgment is deferred** (proposal §15 item 6). Candidate 5 §9.3 governs the first product. Revisit, with `current` dependencies only, if the Slice 2 demonstration shows assessors need it | D1 §6.5; 6.1 §9.10 |
| **D-40** | **Operator custody:** the first product accepts that whoever controls storage and keys can technically read sealed identities. This is stated to every contributor before they write anonymously. Revisit before any deployment whose operator the contributors do not already trust | 6.1 §7.8 Limits (C6-1) |
| **D-41** | **Erasure** creates deletion obligations for the owners of authored descendants; nothing is deleted automatically. Where an obligation on a verified external request is declined, an administrator acting on that request may delete the descendant | 6.1 §12.3 (C6-5) |
| **D-42** | **Anonymous review arrives in Slice 3.** No sealed identity is collected before then; the Slice 2 SCIRE demonstration runs with open review | 6.1 §7.8, §16 (C6-7) |
| **D-43** | **First-product boundary:** no embargoed, human-subject or industry-restricted material. A project's creator attests this at creation, as a recorded condition of use | 6.1 §1.2 (C6-14, D-27) |
| **D-44** | **De-attribution:** on request, UPMS-derived representations name a person by role. Authorship of records, others' signed claims and identity relations are unchanged; removing one's own contribution is deletion, with a withdrawal marker | D1 F-9a; 6.1 §12.3, T107 (C6-12, re-review V4-12 (iii)) |
| **D-45** | **Channel assessment is deferred.** Works are assessed from Slice 3. Assessments of non-person channels and their track records move to Slice 4 and are built only if measured need justifies them; until then the core refuses a source judgment whose target is a channel | 6.1 §9.13, §16 (C61-7, C6-13) |
| **D-46** | **The repairs of SC-61 and SC-62 are the chosen direction:** a reason and an attributed deletion marker when a curator deletes another's standing-bearing record; everything an anonymous-role session causes is sealed, extended by C61-3 to C61-6 | 6.1 §7.8, §12.3, §18.3 |

## 4. What this record does not decide

- **It accepts neither text.** Candidate 6.1 and D1 candidate 1.1 stay proposed. Acceptance still needs independent falsification by a reviewer outside the Claude family, then the owner at Gate 0 (`AGENTS.md`).
- **Owner choices are not technical verification.** D-46 and the repairs C61-1 to C61-6 are directions the owner chose. Whether they actually defeat the trajectories they answer is for the reviewer. The same holds for the "Reviewer check" items C6-3, C6-4, C6-8 to C6-11 and the Codex findings in 6.1 Appendix A.8.
- **Still open:**
  - C6-6, the owner's acknowledgement of the process deviation (6.1 §18.3);
  - V4-12 (iv), where an argument may stop (D1-F4);
  - V4-15, the versioned exchange vocabulary with SSDS (6.1 A.8);
  - type-specific propagation beyond §9.9 (TE-R11);
  - the strict profile's SC-42 rule (6.1 §7.9);
  - the reviewer's request to name text that can go (C6-13).
- **No product commitment.** These decisions shape the proposed first product, and they imply no date.

## 5. Effect on later work

The next revision of the candidate and the D1 text should fold these decisions in, replacing the pending and recommendation wording, after the outside review rather than before it, unless the owner asks otherwise. SCIRE's front-end specification must reflect D-37, D-38 and D-42.
