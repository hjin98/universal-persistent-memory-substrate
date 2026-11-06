# UPMS Architecture Manual, Change History A.31 (Candidate 6.20 → 6.21)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not architecture

Revision 6.21 repairs the Codex review of candidate 6.20, D1 1.19 and D2 1.2 (PASS for D1 1.19; NO-PASS for D2 1.2 and core 6.20), under the owner's delegation of the review cycle. The core changes only in its version references and review records; the repairs are in D2 1.3 and annex T167; D1 1.20 is editorial. Replacements marked "not followed by a digit" replace whole version numbers only. Each replaced passage is quoted verbatim.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Architecture_Manual_Review_Candidate_6_20.md` | `15aaee9a8930d468dd678c4ec9a044cf98a563b18b1a5a6a7fde24bbce1043fc` |
| `UPMS_Architecture_Manual_Review_Candidate_6_20_Annex_Retrieval_Scale.md` | `ccf5ac80462d12991092978c5e79d7aceff05fcd5670b4f253554542e5149f16` |
| `UPMS_Architecture_Manual_Review_Candidate_6_21.md` | `e1f28af693ae8805acf2ed2d8cccbca5a1f90038440b7de9a3d3e93d53464f8c` |
| `UPMS_Architecture_Manual_Review_Candidate_6_21_Annex_Retrieval_Scale.md` | `1e12a4313742426b12bda5b1df5f94c86a39d41318e56f42b94c4661da2f284f` |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20_Change_History.md` | `af6cb053dc13567e352889ded76dd1f0809a9f86347b9d7c03c577bce11497f0` |
| `UPMS_Retrieval_Method_D2_Candidate_1_3_Change_History.md` | `c17701319981caf2c2b4731c9220722610ffe946467bab933e57a174dafdbbe2` |

## Dispositions of the Codex review of 6.20

Review: `UPMS_Candidate_6_20_Independent_Review.md`, SHA-256 `7bbbb2ae480bc96e0ef1bf01754929dec39a3a2198a8227c0e128940530f2229`. "Repaired" is the author's claim, for the next review to test.

| Finding | Repair | Where |
| --- | --- | --- |
| SC620-01 (no elapsed-time prediction at zero samples) | Fit after 20 pairs, interval after 100; qualification runs every bound family 20 times; a new family has prediction "unavailable": admission compares only tokens and context, the plan runs under hard caps, and the answer says there is no time estimate yet | D2 1.3 §7.2 item 1 |
| SC620-02 (parts reachable one at a time) | One jointly reachable count `k*` per request, with a witness response within the one shared budget and a reason for the parts that do not fit; `au` only when `k_c < k*`; a budget-justified partial answer is not charged; worked example 2 | D2 1.3 §10.1, §10.2 |
| SC620-03 (unknown parts removing known errors) | `e_wc`, `u` and `u_partial` over all evaluated requests; only `a_u` needs a known `k*`; worked example 3 | D2 1.3 §10.2 |
| F620-01 (T167 and resource outcomes) | T167 split into a same-resource-outcome case and a resource-outcome boundary case; D2 §7.2 item 3 names resource outcomes as the residual and keeps execution status honest | Annex T167; D2 1.3 §7.2 item 3 |

**Simplification.** Per-part reachability and five per-part outcomes are replaced by one count per request and five request indicators with stated denominators.

The review's owner questions 1 and 2 (requirements, budgets and workload before measurement; the partial-answer credit) stay with the owner under D-120. Question 3 is answered by the T167 repair.

## Core edits

### A.31.c.1 title

Was:

````text
# UPMS Architecture Manual (Review Candidate 6.20)
````

Now:

````text
# UPMS Architecture Manual (Review Candidate 6.21)
````

### A.31.c.2 status

Was:

````text
review candidate 6.20; not accepted-current
````

Now:

````text
review candidate 6.21; not accepted-current
````

### A.31.c.3 annex file (1 places, not followed by a digit)

Was:

````text
UPMS_Architecture_Manual_Review_Candidate_6_20_Annex_Retrieval_Scale.md
````

Now:

````text
UPMS_Architecture_Manual_Review_Candidate_6_21_Annex_Retrieval_Scale.md
````

### A.31.c.4 D1 file (1 places, not followed by a digit)

Was:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19.md
````

Now:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_20.md
````

### A.31.c.5 D2 file (1 places, not followed by a digit)

Was:

````text
UPMS_Retrieval_Method_D2_Candidate_1_2.md
````

Now:

````text
UPMS_Retrieval_Method_D2_Candidate_1_3.md
````

### A.31.c.6 D1 version a (3 places, not followed by a digit)

Was:

````text
candidate 1.19
````

Now:

````text
candidate 1.20
````

### A.31.c.7 D1 version b (5 places, not followed by a digit)

Was:

````text
D1 1.19
````

Now:

````text
D1 1.20
````

### A.31.c.8 D2 version (7 places, not followed by a digit)

Was:

````text
candidate 1.2
````

Now:

````text
candidate 1.3
````

### A.31.c.9 §1 histories

Was:

````text
A.30 in `UPMS_Architecture_Manual_Candidate_6_20_Change_History.md`, and all are cited below
````

Now:

````text
A.30 in `UPMS_Architecture_Manual_Candidate_6_20_Change_History.md`, A.31 in `UPMS_Architecture_Manual_Candidate_6_21_Change_History.md`, and all are cited below
````

### A.31.c.10 §1 revision 6.21

Was:

````text
and the core again changes only in its version references (change history A.30). The review package (D-56) is:
````

Now:

````text
and the core again changes only in its version references (change history A.30). **Revision 6.21** repairs the Codex review of 6.20 (`UPMS_Candidate_6_20_Independent_Review.md`: PASS for D1 1.19, NO-PASS for D2 1.2 and this core): the repairs are in D2 1.3 and annex T167, D1 1.20 is editorial, and the core changes only in its version references and review records (change history A.31). The review package (D-56) is:
````

### A.31.c.11 §1.1 review row

Was:

````text
| D2 retrieval method, candidate 1.3 |
````

Now:

````text
| Independent review of candidate 6.20 with D1 1.19 and D2 1.2 (Codex, OpenAI family) | `UPMS_Candidate_6_20_Independent_Review.md` | PASS for D1 1.19; NO-PASS for D2 1.2 (SC620-01 to SC620-03) and this core; F620-01; repaired in this revision (A.31) |
| D2 retrieval method, candidate 1.3 |
````

### A.31.c.12 §18.1 challenge row

Was:

````text
and that revisions 6.18 to 6.20 change no other rule of 6.17 (A.28 to A.30) |
````

Now:

````text
and that revisions 6.18 to 6.21 change no other rule of 6.17 (A.28 to A.31) |
````

### A.31.c.13 §18.3

Was:

````text
A.29 and A.30 also map the repairs of the Codex reviews of 6.18 and 6.19.
````

Now:

````text
A.29 to A.31 also map the repairs of the Codex reviews of 6.18 to 6.20.
````

### A.31.c.14 App A range

Was:

````text
from candidate 5 to 6.20 (
````

Now:

````text
from candidate 5 to 6.21 (
````

### A.31.c.15 App A files

Was:

````text
and in A.30 (`UPMS_Architecture_Manual_Candidate_6_20_Change_History.md`).
````

Now:

````text
in A.30 (`UPMS_Architecture_Manual_Candidate_6_20_Change_History.md`) and in A.31 (`UPMS_Architecture_Manual_Candidate_6_21_Change_History.md`).
````

### A.31.c.16 App B

Was:

````text
- **Revisions 6.1 to 6.20:**
````

Now:

````text
- **Revisions 6.1 to 6.21:**
````

### A.31.c.17 App B read

Was:

````text
for 6.19 and 6.20, the Codex reviews of 6.18 and 6.19.
````

Now:

````text
for 6.19 to 6.21, the Codex reviews of 6.18 to 6.20.
````

## Annex edits

### A.31.a.1 title

Was:

````text
Review Candidate 6.20: Retrieval-and-Scale Annex
````

Now:

````text
Review Candidate 6.21: Retrieval-and-Scale Annex
````

### A.31.a.2 status

Was:

````text
part of review candidate 6.20;
````

Now:

````text
part of review candidate 6.21;
````

### A.31.a.3 core file

Was:

````text
the core of candidate 6.20 (`UPMS_Architecture_Manual_Review_Candidate_6_20.md`)
````

Now:

````text
the core of candidate 6.21 (`UPMS_Architecture_Manual_Review_Candidate_6_21.md`)
````

### A.31.a.4 version: D1 (2 places, not followed by a digit)

Was:

````text
D1 1.19
````

Now:

````text
D1 1.20
````

### A.31.a.5 version: D2 (2 places, not followed by a digit)

Was:

````text
candidate 1.2
````

Now:

````text
candidate 1.3
````

### A.31.a.6 drafted by

Was:

````text
budgets become componentwise and T167 and T168 are sharpened (change history A.30).
````

Now:

````text
budgets become componentwise and T167 and T168 are sharpened (change history A.30). Revision 6.21 repairs the Codex review of revision 6.20 (`UPMS_Candidate_6_20_Independent_Review.md`): T167 separates equal-resource worlds from a resource-outcome boundary (change history A.31).
````

### A.31.a.7 T167

Was:

````text
| T167 | Estimates and hidden content (R5, D2 §7.2): two worlds that differ only by hidden matching records show the reader the same estimates, the same explanation of them, the same continuation offers and the same coverage; any difference in timing or in the admission decision is reported as the measured residual of §10.1 |
````

Now:

````text
| T167 | Estimates and hidden content (R5, D2 §7.2), two cases over worlds that differ only by hidden matching records. **Same resource outcome** (both admitted and complete, or both stopped at the same point): the reader sees the same estimates, explanations, continuation offers and coverage. **Resource-outcome boundary** (hidden work makes one world refused or budget-limited and the other complete): each world reports its own execution status honestly, and neither shows any count, estimate, explanation or continuation computed from hidden content; the difference in status is recorded as the measured residual of §10.1 |
````
