# Workplans

This index lists the coordination records in `workplans/`. It routes to the documents and is not itself authority: each document states its own status. As of 31 October 2026 no architecture manual is accepted-current.

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
| `UPMS_Architecture_Manual_Review_Candidate_4_1.md` | Manual, review candidate 4 | Revised issue, SHA-256 `19a9e3ed…`; open for independent review |
| `UPMS_Re-Review_Request_Candidate_4_1.md` | Review request | Cites the revised issue under the file name `UPMS_Architecture_Manual_Review_Candidate_4.md` |

Not in this repository, although the review packages cite them: candidate 3, the candidate 2 cross-review, the candidate 3 interim review and its sub-reports A, B and C.
