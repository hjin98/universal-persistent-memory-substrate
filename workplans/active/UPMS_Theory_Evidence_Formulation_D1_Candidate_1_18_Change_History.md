# UPMS D1 Formulation, Change Map T (Candidate 1.17 → 1.18)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not authority

Revision 1.18 repairs SC618-01, F618-01 and F618-02 of the Codex review of 1.17 (dispositions in core change history A.29). Every other rule of 1.17 is kept. Each replaced passage is quoted from the 1.17 file as it stands.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md` | `28bdee3084167701926da92944804cd06390f926cc3b4fe6d9019b57689d2bc8` |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md` | `efb04646f0be364ea955f269dffa38251a1a39eaae7017188e6f050414cc4fde` |

## Edits

### T.1 title

Was:

````text
(Candidate 1.17)
````

Now:

````text
(Candidate 1.18)
````

### T.2 Kind

Was:

````text
revision 1.17. It is the proposed successor of candidate 1.16, which the owner ratified as accepted-current (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`); candidates 1 to 1.16 stay unchanged. Its change map is map S, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17_Change_History.md`; maps B to R are listed in map R (owner decision D-85).
````

Now:

````text
revision 1.18. It is the proposed successor of candidate 1.16, which the owner ratified as accepted-current (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`); candidates 1 to 1.17 stay unchanged. Its change maps are map S (1.16 → 1.17, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17_Change_History.md`) and map T (1.17 → 1.18, `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18_Change_History.md`); maps B to R are listed in map R (owner decision D-85).
````

### T.3 Status

Was:

````text
Revision 1.17 adds §16, the meaning of an answer from memory, and revises §9's hand-off to D2, under owner decisions D-101 to D-120; every rule of 1.16 is kept. It is the D1 parent that UPMS architecture manual candidate 6.18 (`UPMS_Architecture_Manual_Review_Candidate_6_18.md`) with its retrieval-and-scale annex concretizes, and the D1 parent of the D2 retrieval method candidate 1.0 (`UPMS_Retrieval_Method_D2_Candidate_1_0.md`).
````

Now:

````text
Revision 1.17 added §16, the meaning of an answer from memory, and revised §9's hand-off to D2, under owner decisions D-101 to D-120; every rule of 1.16 is kept. Revision 1.18 repairs the Codex review of 1.17 (NO-PASS, `UPMS_Candidate_6_18_Independent_Review.md`): it restores the resolution-basis rule, names the representation a lexical route searches, adds capture and count status to coverage, and corrects §13 (map T). It is the D1 parent that UPMS architecture manual candidate 6.19 (`UPMS_Architecture_Manual_Review_Candidate_6_19.md`) with its retrieval-and-scale annex concretizes, and the D1 parent of the D2 retrieval method candidate 1.1 (`UPMS_Retrieval_Method_D2_Candidate_1_1.md`).
````

### T.4 Author

Was:

````text
drafts §16 from design note revision 3 (`UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`).
````

Now:

````text
drafts §16 from design note revision 3 (`UPMS_Retrieval_Translation_Economy_Design_Note_R3_2026-11-05.md`). Revision 1.18 answers the Codex review of 1.17 under the owner's delegation of the revise-and-review cycle.
````

### T.5 §0.1 row

Was:

````text
| UPMS Theory–Evidence Formulation, D1 candidate 1.16 (accepted-current) |
````

Now:

````text
| UPMS Theory–Evidence Formulation, D1 candidate 1.17, and its review (Codex, OpenAI family) | `workplans/active/UPMS_Theory_Evidence_Formulation_D1_Candidate_1_17.md`; `workplans/active/UPMS_Candidate_6_18_Independent_Review.md` | Immediate predecessor (NO-PASS); SC618-01, F618-01 and F618-02 are repaired here (map T) |
| UPMS Theory–Evidence Formulation, D1 candidate 1.16 (accepted-current) |
````

### T.6 version: candidate 6.18 → 6.19 (16 places)

Was:

````text
candidate 6.18
````

Now:

````text
candidate 6.19
````

### T.7 version: D2 candidate 1.0 → 1.1 (5 places)

Was:

````text
candidate 1.0
````

Now:

````text
candidate 1.1
````

### T.8 file: D2 1_0 → 1_1 (1 places)

Was:

````text
UPMS_Retrieval_Method_D2_Candidate_1_0.md
````

Now:

````text
UPMS_Retrieval_Method_D2_Candidate_1_1.md
````

### T.9 Def 16.1 lexical

Was:

````text
a **lexical predicate** over original text,
````

Now:

````text
a **lexical predicate** over a stated text representation, either the original text or a named rendering revision (Definition 16.10),
````

### T.10 Def 16.2 route match

Was:

````text
- **route match**: for each lexical or structural route, whether `x` satisfies its predicate at the stated analyzer, extractor and index versions;
````

Now:

````text
- **route match**: for each lexical or structural route, whether `x` satisfies its predicate over the route's stated representation at the stated analyzer, extractor and index versions. A match in a rendering is an exact fact about the rendering's text, not about the original; its citation names both the rendering revision and the original span, and no original-text match is reported for words absent from the original;
````

### T.11 Def 16.5 capture and counts

Was:

````text
- **execution**: what was evaluated or skipped, total matches against returned matches, and how to continue;
````

Now:

````text
- **capture**: what of the source history was captured, and known capture gaps (candidate 6.19 §10.3, `capture_extent`);
- **execution**: what was evaluated or skipped, total matches (each stated as exact, a lower bound, an estimate or unknown) against returned matches, and how to continue;
````

### T.12 F-51.2 restored

Was:

````text
2. A resolution never rests on another resolution that is neither confirmed by its speaker nor adopted, mirroring F-2.
````

Now:

````text
2. A resolution never rests on another resolution that its speaker has not confirmed (design note R3 §5.4). Adopting a resolution creates the adopter's own claim, which may be relied on as that claim (F-2); it does not make the resolution a basis for further resolutions, because adoption "changes nothing about" the resolution (Definition 2.3).
````

### T.13 §13 predecessor

Was:

````text
- **No accepted predecessor:** there are no recorded tensions against accepted D1 authority to carry, because none exists. Tensions recorded against the SCIRE v0.4 texts are carried as listed in §12.
````

Now:

````text
- **Accepted predecessor:** D1 1.16, ratified (`UPMS_Owner_Ratification_D1_1_16_Core_6_17_2026-11-05.md`). **Recorded tensions bearing on it, and their applicability to this revision** (assessed by Claude, AI, Opus 5.5; proposed until this revision's acceptance considers them): the SERIOUS CHALLENGE recorded with owner decisions D-101 to D-116 (`UPMS_Owner_Decisions_Retrieval_Translation_Economy_2026-11-05.md` §3, as corrected by `UPMS_Owner_Decisions_Retrieval_Critique_2026-11-05.md` §3), asserted by Claude on the owner's requirement and bound to core 6.17's concretization, not to a D1 rule: **applicable**, since §9 and §16 are this revision's answer at D1; it is a challenge to the adequacy of the ratified pilot design for the larger requirement, not a defect of that design within its envelope. **Searched:** `workplans/active/` decision, ratification, review and critique records of 5 November 2026; `history/SEMANTIC_EVOLUTION.md`; the predecessor's §15. **Not reachable:** native GitHub issues. Tensions recorded against the SCIRE v0.4 texts are carried as listed in §12.
````

### T.14 App A

Was:

````text
- **Anchoring:** every revision from 1.1 to 1.17 was written by the same author
````

Now:

````text
- **Anchoring:** every revision from 1.1 to 1.18 was written by the same author
````
