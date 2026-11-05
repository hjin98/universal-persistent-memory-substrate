# UPMS Proposed Decisions on the Candidate 6.7 Independent Review, 5 November 2026 (D-90 and D-92 amended, D-93; pending the owner)

5 November 2026 · proposed by Claude (AI, Opus 5.5) · **not decided** · decision proposal, not architecture authority

**These are the author's proposals, not owner decisions,** made under the owner's delegation of the review cycle ("Proceed the revision / review cycle to your own discretion. Leave those questions that you deemed as genuinely requires my judgement to me in the end", 5 November 2026). They amend the pending proposals of `UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md` (SHA-256 `3a9fd1d4a46f70e115664e8233c6aad4fc07bde86a610a24442bd30ff1ed4236`), which stays unchanged, and add D-93. All stay **pending** until the owner confirms, changes or rejects them.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_7_Independent_Review.md` | `2daf7af963f31508166e180ebd5d5a7db0024885a984d270525e976edac06168` | Codex (OpenAI GPT family; the same reviewer and family as the 6.4 to 6.6 reviews) review: NO-PASS for D1 1.7 and for core 6.7 with anonymous-review annex 6.5; SC67-01 to SC67-03, R67-01, simplicity §7 |

## 2. Proposals

| ID | Proposal | Answers | Why it needs the owner |
| --- | --- | --- | --- |
| **D-90, amended** | **Possible homes are transitive; resolutions are homed by the binding they resolve.** The possible homes of a record are its home scope and every objection home registered, now or earlier, for a scope among its possible homes. Every objection, including a dispute of a resolution, is homed in a possible home of its target; a resolution is homed in a possible home of every binding it resolves, and is split when they share none; neither carries a restriction tag of its own. By induction, everything reached from a footprint record through objections, resolutions and disputes is homed among that record's possible homes, so the coverage test over the footprint is sufficient. This replaces the 6.6 proposal's homing rule, which a chain of registrations H → Q → Z defeated. The alternative (compute coverage along the readable dispute graph) was again not taken: it is a second traversal whose result the transitive rule makes unnecessary | SC67-01 | It widens where objections may be homed and makes the coverage statement show whenever a reader misses any scope in the chain |
| **D-92, amended** | **The existence of an objection is not promised confidential.** No mechanism beyond the ordinary access rules hides an objection's existence, time or unrestricted ground from a target's readers; those rules still decide what each reader actually receives, and the coverage statement covers what they withhold. Objections whose existence must stay hidden from a target's readers are outside the first product | R67-01 | As before: a product limitation to accept knowingly |
| **D-93** | **Resolution is per binding.** A resolution decision names the bindings at which it resolves an objection, and an author may withdraw an objection at named bindings, for example one they misapplied, or at all of them. An objection is unresolved in a projection when it is unresolved at some binding in that projection's footprint. A resolution that answers the successor `K2` therefore leaves the objection unresolved on decisions that relied on `K1`; a binding withdrawn as misapplied stays in history, labeled on the decisions that relied on it. The alternative (one global resolution, labeled with the target actually assessed) was not taken | SC67-03 | It decides whether settling an objection for a revision settles it for earlier revisions; the owner may prefer the global, administrative reading |

**Corrections that need no decision** (the author's to make):
- D1 Definition 5.3: independent confirmation additionally requires a confirming relation kind (`entails` or `prediction-succeeded`) with an effective positive assessment; use history and dependence alone make a relation an **independent test**, shown with its bearing (SC67-02);
- the trajectories of SC67-01 to SC67-03 and SC67-02's controls become acceptance scenarios;
- D-85 continued (review §7 items 1, 2 and 5): core §9.9's route-status paraphrase cut to a citation of D1 §6.1; D1 F-4 and F-7a state the coverage requirement and leave the construction and its proof to core §5.11; core §17.2 cites D1 §11's surface list instead of repeating it.

## 3. What this record does not decide

It decides nothing and accepts no text. D-91 stands as proposed in the 6.6 record, read with D-93. The owner's own decisions D-1 to D-89 are unchanged.
