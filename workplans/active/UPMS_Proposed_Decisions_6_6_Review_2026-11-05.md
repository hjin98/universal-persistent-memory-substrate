# UPMS Proposed Decisions on the Candidate 6.6 Independent Review, 5 November 2026 (D-90 to D-92, pending the owner)

5 November 2026 · proposed by Claude (AI, Opus 5.5) · **not decided** · decision proposal, not architecture authority

**These are the author's proposals, not owner decisions.** The product owner delegated the revision and review cycle to the author ("Proceed the revision / review cycle to your own discretion. Leave those questions that you deemed as genuinely requires my judgement to me in the end", 5 November 2026). That delegation lets the author draft revisions that apply proposed decisions so the next review can test them. It does not let the author make owner decisions. D-90 to D-92 stay **pending** until the owner confirms, changes or rejects them; any text that applies them is conditional on that.

## 1. Bound text

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Candidate_6_6_Independent_Review.md` | `ac282071dbe79aa61262b70237a5f6e981ddb156a44e652dfb422eb1f0cc39f4` | Codex (OpenAI GPT family; the same reviewer and family as the 6.4 and 6.5 reviews) review: NO-PASS for D1 1.6 and for core 6.6 with anonymous-review annex 6.5; SC66-01, SC66-02, R66-01, R66-02, simplicity §7 |

## 2. Proposed decisions

| ID | Proposal | Answers | Why it needs the owner |
| --- | --- | --- | --- |
| **D-90** | **Resolutions and their disputes live where the resolved objection may live.** A `resolution` decision is homed in a possible home of every objection it resolves (the objections' targets' home scope or an objection home registered for it); one resolving objections with no common home is split. An objection that disputes a resolution is homed in a possible home of the objection it disputes. A resolution decision carries no restriction tag of its own. Coverage over the reliance footprint then covers the dispute branch without a second traversal. The alternative (extend the coverage calculation along every resolution and dispute link) was not taken: it adds a second traversal for a case the homing rule removes | SC66-01 | It narrows where people may record resolutions and disputes |
| **D-91** | **An objection applies through every target it has been bound to.** Its bindings are its first target, every successor it was carried to and every record it was rebound to. It applies to every decision or claim whose footprint contains one of its bindings, with its current handling, resolution and mode, shown with the binding through which it applies. A rebind therefore adds a binding and removes none: a decision that cited the earlier target keeps showing the objection (D1 F-3a), and decisions on the new target receive it. An objection is readable by a reader who reads its home and satisfies the restriction tags of the binding through which it applies | SC66-02 | It fixes what a rebind means for earlier decisions; the alternative is that re-examination ends applicability to the old target |
| **D-92** | **The existence of an objection is not confidential.** Anyone who reads a target can see that an objection to it exists, when, and its unrestricted ground; a restricted cited record hides only its own content. Objections whose existence must stay hidden from a target's readers are outside the first product, which says so in its conditions of use | Review §5 item 3 | It is a product limitation the owner should accept knowingly |

**Corrections that need no decision** (the author's to make):
- the late-objection delta's baseline is the applicable set of the proposed basis at the policy evaluation position, derived from the policy result's recorded basis and position; the decision's enduring footprint still starts at its commit (R66-01);
- §15.2 requires every applicable scenario in the bound inventories instead of naming a range (R66-02);
- the cases of SC66-01, SC66-02 and R66-01 become acceptance scenarios;
- D-85 continued (review §7): the predecessor genealogies in D1 §0.1 and core §1.1 cut to current parents, the immediate review and the governing decisions, with the rest moved to the change histories; core §1.3's drafting chronology moved; core §9.9 cites D1 F-6 instead of paraphrasing it; the repeated no-veto explanation in core §5.11 cut to a pointer.

## 3. What this record does not decide

It decides nothing and accepts no text. The owner's own decisions D-1 to D-89 are unchanged.
