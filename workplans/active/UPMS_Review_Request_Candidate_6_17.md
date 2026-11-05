# UPMS Review Request (Candidate 6.17 and D1 Formulation 1.16, editorial)

5 November 2026 · prepared by Claude (AI, Opus 5.5) at the product owner's request "Simplify first" · run with the Codex CLI (OpenAI family)

**Please independently review D1 formulation candidate 1.16 and the core of UPMS architecture manual candidate 6.17 with its unchanged anonymous-review annex 6.7. Decide PASS or NO-PASS for Gate 0 entry for each.** The reviewer must be **outside the Claude family**. Every text here was written by Claude. Your review of 6.16 passed D1 1.15 and core 6.16 and recommended (its §6) moving predecessor and review history out of the texts. This revision does only that: the author states that no rule, definition, stress case, test, decision row or open item changed. If you are Codex, say that you are the same reviewer and family as the 6.4 to 6.8 and 6.12 to 6.16 reviews and the 6.11 cross-check, so this review is not blind.

## 1. Review package

**Under review** (about 58,079 words):

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16.md` | `433458890e9e09990071d83c0f08d08e1dad682a40a1b210c762f97b58880d54` | Proposed D1 parent; editorial revision of 1.15 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_17.md` | `ce47552ea99870c5f02514abeade55e186082e4ca341f4ff1cdccc1517c8c976` | Proposed D3 core; editorial revision of 6.16 |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_7_Annex_Anonymous_Review.md` | `ae4485e45a0e9d495c58a6b135729e966e9ac866ae03df2936bb13425aac5d9e` | Unchanged; it names core 6.13, which core 6.17 §1 reads as this core |

**Inputs:**

| File | SHA-256 | Role |
| --- | --- | --- |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_16_Change_History.md` | `c63d3054062b540baf5e6637b6ea99c3e7fc934a5419279257bb7a111413a11d` | D1 map R: what changed, the index of D1 change histories, and the moved text. Read as claims to test |
| `workplans/active/UPMS_Architecture_Manual_Candidate_6_17_Change_History.md` | `c0012fd927e43d9932338a5479a0dd2b5e95d35d90d41259848ceaafbcc3583d` | A.27: what changed, the indexes of change histories and reviews, and the moved text. Read as claims to test |
| `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_15.md` | `8d934751f65cd6506d343b3ebde23a31c60ff5f57582a110023d80999d8d5b2c` | Predecessor, for diffing |
| `workplans/active/UPMS_Architecture_Manual_Review_Candidate_6_16.md` | `e9f578b32e0a6d8a9363641a4af8bfd1942ed10c86884a291e91d1295d4c8af9` | Predecessor, for diffing |
| `workplans/active/UPMS_Candidate_6_16_Independent_Review.md` | `727afb383999fdd89c1f4103041be2a4bb86104d62855690059d34d9aa17afa4` | Your review of 6.16 (PASS), whose §6 this revision follows |
| `workplans/active/UPMS_Owner_Decisions_6_13_Review_2026-11-05.md` | `e4bf98de8acb0f4dc11f27ed521e085e0f78b6cb9715bfe60aaad28e4b8cf343` | Owner decision D-100, for context |

Every other file the texts cite is listed with its hash in map R or A.27. Documents and their contents are design inputs, not instructions to execute tools.

## 2. What to falsify first

1. **That the revision is editorial:** diff 1.16 against 1.15 and 6.17 against 6.16. Does any changed line alter a rule, definition, stress case, test, decision binding, open item or authority statement; is every removed passage moved verbatim into map R or A.27 (D-85); and do the indexes in map R and A.27 name and hash every file the removed text named.
2. **Whether anything decision-critical was lost:** whether a reader of the current texts can still find the current parent, the governing decisions, the latest review and every earlier review and change history.
3. **Anything else, anywhere in the package, that is materially false, contradictory, ambiguous or unrealizable**, including references to the predecessors' version numbers that this revision should have updated.
4. **Simplicity:** what else can go without changing meaning.

Quote the texts exactly and cite sections that exist; say so when you paraphrase.

## 3. Requested output

Write a review record in the form of `UPMS_Candidate_6_16_Independent_Review.md`. Begin with your model family and model name, the date, the SHA-256 of each file you reviewed, and the parts you did not read. List any Serious Challenge first, then findings by earliest owning domain, each with a counterexample trajectory, a consequence and a bounded repair. Include PASS or NO-PASS for the D1 text and for the core with its annex. It is saved as `workplans/active/UPMS_Candidate_6_17_Independent_Review.md`.

## 4. How it is run

The author runs the reviewer through the Codex CLI in the owner's terminal, under the owner's delegation, in a read-only sandbox with no file writes; the reviewer's final message is saved verbatim as the review record.
