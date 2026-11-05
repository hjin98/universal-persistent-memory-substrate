# UPMS Owner Decisions on the Candidate 6.8 Independent Review, 5 November 2026 (D-92 decided, D-94 to D-96, C6-6)

5 November 2026 · decided by the product owner (Sam) · recorded by Claude (AI, Opus 5.5) · decision record, not architecture authority

**The product owner chose to simplify the objection model for the first product and answered the other questions the author left for them.** After the 6.8 review, the author put six questions to the owner in a Claude Code session. The owner answered the first, which way the objection model should go, with "Simplify the scope", and the rest with "2. Accept. 3-6 Proceed with your recommendation." This record states those answers as decided and binds them to the review they answer. Claude wrote this record and cannot widen the decisions: where this record and the questions and recommendations as put to the owner differ, those govern.

The questions as put to the owner, in short:
1. **Scope of the objection model** (recommended: simplify; "objections live only in the target's scope or one review scope; a rebind keeps only a history label; and one resolution, labeled with what it assessed, settles the objection everywhere");
2. **The pending proposals D-90 to D-93** ("Codex judged D-92 sound … The others depend on question 1");
3. **The late-objection delta:** flag only new objections, or also a known objection that newly applies through another target;
4. **Reviewer:** a reviewer from another model family for the next round;
5. **Pushing** the four local commits;
6. **C6-6,** the owner's acknowledgement of the early process deviation.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_8_Independent_Review.md` | `a5afb292830c940b3234caedec0e0827d5e5ba4ed266b076e0a28b5b0e2593ad` | Codex (OpenAI GPT family; the same reviewer and family as the 6.4 to 6.7 reviews) review: NO-PASS for D1 1.8 and for core 6.8 with anonymous-review annex 6.5; SC68-01 to SC68-03, R68-01 |
| `workplans/active/UPMS_Proposed_Decisions_6_6_Review_2026-11-05.md` | `3a9fd1d4a46f70e115664e8233c6aad4fc07bde86a610a24442bd30ff1ed4236` | Proposals D-90 to D-92 |
| `workplans/active/UPMS_Proposed_Decisions_6_7_Review_2026-11-05.md` | `3a0741c43d9d71802f99c5cce148bba8ab0c19c33878fc0ce1c87c3640c99d8a` | Proposals D-90 and D-92 amended, D-93 |

## 2. Decisions

| ID | Decision | Answers |
| --- | --- | --- |
| **D-94** | **A simplified objection model for the first product** (question 1). (a) **Homes:** an objection lives in its target's home scope or in a review scope opened to review that scope's work and registered as its objection home. No other scope can be registered, and a review scope registers no objection homes of its own. This narrows D-80's registered objection homes. (b) **Rebinding keeps a history label:** a carry or rebind changes the objection's target and records the earlier target in its target history; decisions that cited an earlier target keep showing the objection, labeled with that history (D-47 kept). (c) **One resolution, labeled with what it assessed:** an objection has one resolution, which settles it everywhere it applies; every projection that shows it through another target says which target the resolution assessed, so it never reads as settling the earlier target. A resolution, and every dispute of it, lives in the home scope of what it resolves or disputes | SC68-01, SC68-02; SC67-03; review §7 |
| **D-92** | **The existence of an objection is not promised confidential**, in its amended form (question 2): no mechanism beyond the ordinary access rules hides an objection's existence, time or unrestricted ground from a target's readers; those rules still decide what each reader receives. Objections whose existence must stay hidden from a target's readers are outside the first product | R67-01 |
| **D-95** | **The late-objection delta compares objection identities** (question 3, on the author's recommendation): an objection already in the evaluation baseline that later applies through another target is not in the delta; its projections show its target history | R68-01 |
| **D-96** | **The next review is by a reviewer from another model family** (question 4, on the author's recommendation). The author runs it with the Antigravity CLI (`agy`), Gemini family, under the owner's delegation of the review cycle | Review §8; independence |

**Question 2, read with question 1.** The owner accepted the pending proposals after choosing to simplify. D-92 is decided as above. D-91's selection of objections through every target in their history is kept, inside D-94(b). D-90 (both forms) and D-93 were proposals for the full model, which question 1 replaced; they are superseded by D-94 rather than adopted. If the owner meant otherwise, D-94 governs until they say so.

**C6-6 acknowledged** (question 6, on the author's recommendation). The owner acknowledges that the architecture candidates and the D1 formulation were drafted, on the owner's instruction, before the proposal's outside-family review existed, contrary to the proposal's own §14 step 1; later candidates were checked against that review's trajectories. C6-6 is closed.

**Question 5:** the owner approved pushing the branch. That is an action, not a decision.

**What the owner gives up, knowingly:** outside critics write only through a contributor right or a review scope; a resolution of an objection to a revised claim also closes it, as a labeled administrative act, on decisions that cited the earlier revision; objection existence is not confidential from a target's readers.

## 3. What this record does not decide

It accepts no text. The revision that applies these decisions stays proposed until a reviewer outside the Claude family has falsified it and the owner accepts it.
