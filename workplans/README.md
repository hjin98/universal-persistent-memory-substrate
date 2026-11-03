# Workplans

This index lists the coordination records in `workplans/`. It routes to the documents and is not itself authority: each document states its own status. As of 2 November 2026 no architecture manual is accepted-current.

## Lifecycle

- `active/` holds records whose obligations are still open, including superseded revisions that open review packages still cite.
- `archive/` holds records that are complete, or whose remaining obligations an accepted successor owns.
- Review packages bind inputs by file name and SHA-256, so files are not renamed or edited in place. A revision is a new file.

## Active records

| File | Kind | Note |
| --- | --- | --- |
| `UPMS Architecture Proposal v0.1.md` | Proposal | Initial proposal |
| `UPMS Architecture Proposal v0.2.md` | Proposal | Introduces the Event, Claim and Judgment model |
| `UPMS Architecture Proposal v0.3.md` | Proposal | Input to the first manual |
| `UPMS Architecture Manual.md` | Manual baseline | Reviewed NO-PASS in the Codex review |
| `UPMS Architecture Review.md` | Review record | Codex review of the baseline, findings F01–F18 |
| `UPMS Architecture Manual - Refined.md` | Manual, review candidate 1 | Repairs F01–F18 |
| `UPMS_Round_2_Amendments.md` | Amendments | A1–A7, applied to candidate 1 |
| `UPMS_Architecture_Manual_Review_Candidate_2.md` | Manual, review candidate 2 | Reviewed NO-PASS in the candidate 2 cross-review (CR01–CR10) |
| `UPMS_Cross_Review_Request.md` | Review request | Requests the candidate 2 cross-review |
| `UPMS_Architecture_Manual_Review_Candidate_4.md` | Manual, review candidate 4 | First issue, SHA-256 `d2146daa…` |
| `UPMS_Re-Review_Request_Candidate_4.md` | Review request | Cites the first issue of candidate 4 |
| `check_C4.md` | Review record | Same-family check of a candidate 4 draft, findings K-01–K-20 |
| `UPMS_Architecture_Manual_Review_Candidate_4_1.md` | Manual, review candidate 4 | Revised issue, SHA-256 `19a9e3ed…`; reviewed NO-PASS in the same-family review below; superseded by candidate 5 |
| `UPMS_Re-Review_Request_Candidate_4_1.md` | Review request | Cites the revised issue under the file name `UPMS_Architecture_Manual_Review_Candidate_4.md` |
| `UPMS_Candidate_4_Same_Family_Review.md` | Review record | Same-family (Claude) review of the revised candidate 4: NO-PASS, Serious Challenge SC-1, findings N-01–N-12; not the independent review Gate 0 requires |
| `UPMS_Architecture_Manual_Review_Candidate_5.md` | Manual, review candidate 5 | Repairs SC-1 and N-01–N-12 (change map in its Appendix A.7), SHA-256 `406cf3b4…`; proposes revised outcomes for D-8, D-9, D-13, D-16 to D-19, pending the owner; not yet reviewed; frozen as an input to the theory–evidence proposal below, and its independent review is not requested (D-23) |
| `UPMS_Theory_Evidence_Memory_Proposal_v0.1.md` | Structural proposal | Owner decisions D-20 to D-34: one theory–evidence memory, SCIRE as front end, SSDS outside, security proportionate to open science, retention by importance, works judged one by one and people never scored by the system (D-32 supersedes D-26 and D-31), four rights, project memory first, anonymous and blinded review under a neutral judge; sets the direction for the next manual candidate; not yet reviewed |

Not in this repository, although the review packages cite them: candidate 3, the candidate 2 cross-review, the candidate 3 interim review and its sub-reports A, B and C.
