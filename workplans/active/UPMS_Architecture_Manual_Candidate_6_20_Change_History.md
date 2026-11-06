# UPMS Architecture Manual, Change History A.30 (Candidate 6.19 → 6.20)

5 November 2026 · written by Claude (AI, Opus 5.5) · change history, not architecture

Revision 6.20 repairs the Codex review of candidate 6.19, D1 1.18 and D2 1.1 (PASS for D1 1.18; NO-PASS for D2 1.1 and core 6.19), under the owner's delegation of the review cycle. The core changes only in its version references and review records; the repairs are in D2 1.2 and the annex; D1 1.19 is editorial. Version replacements marked "not followed by a digit" replace only whole version numbers (so `candidate 1.1` does not touch `candidate 1.16`). Each replaced passage is quoted verbatim.

| Input | SHA-256 |
| --- | --- |
| `UPMS_Architecture_Manual_Review_Candidate_6_19.md` | `c0fc446c4493aab2c2dd6b6f4611e3cd34b991cbcfa36235891ca73921fef3c3` |
| `UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md` | `a737a6a64d15d23f310bbd4e41137eacebff03a86c4c8de63ef90f1b3fb9c0bb` |
| `UPMS_Architecture_Manual_Review_Candidate_6_20.md` | `15aaee9a8930d468dd678c4ec9a044cf98a563b18b1a5a6a7fde24bbce1043fc` |
| `UPMS_Architecture_Manual_Review_Candidate_6_20_Annex_Retrieval_Scale.md` | `ccf5ac80462d12991092978c5e79d7aceff05fcd5670b4f253554542e5149f16` |
| `UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19_Change_History.md` | `16287eecd2dcdb1490d8bfd19cb75b0fb2ed0b63fe0dd31c89baa2994f410d8b` |
| `UPMS_Retrieval_Method_D2_Candidate_1_2_Change_History.md` | `2aa193e5a8fc3e3d73a3e9c25b78c5670ae65322787adfd3986045537aabccd7` |

## Dispositions of the Codex review of 6.19

Review: `UPMS_Candidate_6_19_Independent_Review.md`, SHA-256 `35be5d6e4131d9f884ecea427102936105e9b6cc6b38ec9f1025c63c6dc9a766`. "Repaired" is the author's claim, for the next review to test.

| Finding | Repair | Where |
| --- | --- | --- |
| SC619-01 (cost units and budget comparison) | `W` in CPU-seconds; elapsed engine time predicted per plan family and measured; internal tokens `T` and returned context `C` budgeted separately; admission compares point predictions componentwise; cold-start rule; runtime caps on time and tokens; acceptance compares componentwise with a budget-limited share | D2 1.2 §2, §7.1 to §7.4, §10.3; annex R9.1, R15 |
| SC619-02 (answerability and partial answers) | Reference adjudication with its own budget and a three-valued reachability; exclusive part outcomes and overlapping request indicators with denominators; a worked two-part example | D2 1.2 §10.1, §10.2 |
| F619-01 (§0.1 authority sentence; predecessor wording) | Sentence corrected; 1.16 labeled accepted predecessor, 1.18 immediate candidate predecessor | D1 1.19 §0.1 |
| F619-02 (T168) | Two dispositions: within the bound workload the target must be met; overload or injected failure must hold barriers and report `purge_failed` | Annex T168 |
| §4.3 (statistics and hidden content) | Displayed estimates, explanations and continuations use only statistics whose counting domain satisfies R5; segment counts are not assumed safe; T167 widened to explanations, continuations and coverage | D2 1.2 §7.2 item 3; annex T167 |

The review's owner questions 1 and 2 (requirements and workload before measurement; the partial-answer weight) stay with the owner under D-120; D2 §10.3 and §13 propose values. Question 3 needs no decision.

## Core edits

### A.30.c.1 title

Was:

````text
# UPMS Architecture Manual (Review Candidate 6.19)
````

Now:

````text
# UPMS Architecture Manual (Review Candidate 6.20)
````

### A.30.c.2 status

Was:

````text
review candidate 6.19; not accepted-current
````

Now:

````text
review candidate 6.20; not accepted-current
````

### A.30.c.3 annex file (1 places, not followed by a digit)

Was:

````text
UPMS_Architecture_Manual_Review_Candidate_6_19_Annex_Retrieval_Scale.md
````

Now:

````text
UPMS_Architecture_Manual_Review_Candidate_6_20_Annex_Retrieval_Scale.md
````

### A.30.c.4 D1 file (1 places, not followed by a digit)

Was:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_18.md
````

Now:

````text
UPMS_Theory_Evidence_Formulation_D1_Candidate_1_19.md
````

### A.30.c.5 D2 file (1 places, not followed by a digit)

Was:

````text
UPMS_Retrieval_Method_D2_Candidate_1_1.md
````

Now:

````text
UPMS_Retrieval_Method_D2_Candidate_1_2.md
````

### A.30.c.6 D1 version a (3 places, not followed by a digit)

Was:

````text
candidate 1.18
````

Now:

````text
candidate 1.19
````

### A.30.c.7 D1 version b (4 places, not followed by a digit)

Was:

````text
D1 1.18
````

Now:

````text
D1 1.19
````

### A.30.c.8 D2 version (7 places, not followed by a digit)

Was:

````text
candidate 1.1
````

Now:

````text
candidate 1.2
````

### A.30.c.9 §1 histories

Was:

````text
A.29 in `UPMS_Architecture_Manual_Candidate_6_19_Change_History.md`, and all are cited below
````

Now:

````text
A.29 in `UPMS_Architecture_Manual_Candidate_6_19_Change_History.md`, A.30 in `UPMS_Architecture_Manual_Candidate_6_20_Change_History.md`, and all are cited below
````

### A.30.c.10 §1 revision 6.20

Was:

````text
and the core changes only in its version references (change history A.29). The review package (D-56) is:
````

Now:

````text
and the core changes only in its version references (change history A.29). **Revision 6.20** repairs the Codex review of 6.19 (`UPMS_Candidate_6_19_Independent_Review.md`: PASS for D1 1.18, NO-PASS for D2 1.1 and this core): the repairs are in D2 1.2 and the annex, D1 1.19 is editorial, and the core again changes only in its version references (change history A.30). The review package (D-56) is:
````

### A.30.c.11 §1.1 review row

Was:

````text
| D2 retrieval method, candidate 1.2 |
````

Now:

````text
| Independent review of candidate 6.19 with D1 1.18 and D2 1.1 (Codex, OpenAI family) | `UPMS_Candidate_6_19_Independent_Review.md` | PASS for D1 1.18; NO-PASS for D2 1.1 (SC619-01, SC619-02) and this core; F619-01 and F619-02 repaired in this revision (A.30) |
| D2 retrieval method, candidate 1.2 |
````

### A.30.c.12 §18.1 challenge row

Was:

````text
and that revisions 6.18 and 6.19 change no other rule of 6.17 (A.28, A.29) |
````

Now:

````text
and that revisions 6.18 to 6.20 change no other rule of 6.17 (A.28 to A.30) |
````

### A.30.c.13 §18.3

Was:

````text
A.29 also maps the repairs of the Codex review of 6.18.
````

Now:

````text
A.29 and A.30 also map the repairs of the Codex reviews of 6.18 and 6.19.
````

### A.30.c.14 App A range

Was:

````text
from candidate 5 to 6.19 (
````

Now:

````text
from candidate 5 to 6.20 (
````

### A.30.c.15 App A files

Was:

````text
and in A.29 (`UPMS_Architecture_Manual_Candidate_6_19_Change_History.md`).
````

Now:

````text
in A.29 (`UPMS_Architecture_Manual_Candidate_6_19_Change_History.md`) and in A.30 (`UPMS_Architecture_Manual_Candidate_6_20_Change_History.md`).
````

### A.30.c.16 App B

Was:

````text
- **Revisions 6.1 to 6.19:**
````

Now:

````text
- **Revisions 6.1 to 6.20:**
````

### A.30.c.17 App B read

Was:

````text
for 6.19, the Codex review of 6.18.
````

Now:

````text
for 6.19 and 6.20, the Codex reviews of 6.18 and 6.19.
````

## Annex edits

### A.30.a.1 title

Was:

````text
Review Candidate 6.19: Retrieval-and-Scale Annex
````

Now:

````text
Review Candidate 6.20: Retrieval-and-Scale Annex
````

### A.30.a.2 status

Was:

````text
part of review candidate 6.19;
````

Now:

````text
part of review candidate 6.20;
````

### A.30.a.3 core file

Was:

````text
the core of candidate 6.19 (`UPMS_Architecture_Manual_Review_Candidate_6_19.md`)
````

Now:

````text
the core of candidate 6.20 (`UPMS_Architecture_Manual_Review_Candidate_6_20.md`)
````

### A.30.a.4 version: D1 (2 places, not followed by a digit)

Was:

````text
D1 1.18
````

Now:

````text
D1 1.19
````

### A.30.a.5 version: D2 (2 places, not followed by a digit)

Was:

````text
candidate 1.1
````

Now:

````text
candidate 1.2
````

### A.30.a.6 drafted by

Was:

````text
change history A.29 maps each repair.
````

Now:

````text
change history A.29 maps each repair. Revision 6.20 repairs the Codex review of revision 6.19 (`UPMS_Candidate_6_19_Independent_Review.md`): budgets become componentwise and T167 and T168 are sharpened (change history A.30).
````

### A.30.a.7 R9.1 budgets

Was:

````text
A plan's **effective cap** is the smaller of its class cap and the §14.2 query limits; a larger cap needs the deep-retrieval capability with its budget (§10.4), requested as a new plan under item 3. Class selection never widens the pilot profile. Every plan runs under its effective cap (D2 §7.4).
````

Now:

````text
A plan's **effective budget** has three components, compared separately (D2 §7.3): the effective engine cap on elapsed engine time (the smaller of the class's engine cap and the §14.2 query limits), the internal-token limit (within the §14.2 processing limits), and the returned-context limit. A larger budget needs the deep-retrieval capability with its budget (§10.4), requested as a new plan under item 3. Class selection never widens the pilot profile. Every plan is admitted on its point predictions and runs under hard caps on each component (D2 §7.2, §7.4).
````

### A.30.a.8 R15 effective budget

Was:

````text
| Effective cap | The smaller of the class cap and the §14.2 query limits; larger only with the deep-retrieval capability and its budget |
````

Now:

````text
| Effective budget | Engine cap: the smaller of the class engine cap and the §14.2 query limits, on elapsed engine time; internal tokens: the class limit, within the §14.2 processing limits; returned context: the class limit. Larger only with the deep-retrieval capability and its budget |
````

### A.30.a.9 T167

Was:

````text
| T167 | Estimates and hidden content (R5, D2 §7.2): two worlds that differ only by hidden matching records show the same estimate to the reader |
````

Now:

````text
| T167 | Estimates and hidden content (R5, D2 §7.2): two worlds that differ only by hidden matching records show the reader the same estimates, the same explanation of them, the same continuation offers and the same coverage; any difference in timing or in the admission decision is reported as the measured residual of §10.1 |
````

### A.30.a.10 T168

Was:

````text
| T168 | Aggregate purge (RT11): deleting one item in each of many segments during sustained ingestion and a concurrent rebuild either meets the live-surface target for every deletion, with ingestion throttled first, or reports `purge_failed` for those missed; purge debt is reported throughout, and a crash during a rewrite leaves no deleted content served |
````

Now:

````text
| T168 | Aggregate purge (RT11), two cases. **Within the bound lifecycle workload and maintenance concurrency** (D2 §13, as bound for the profile under test): deleting one item in each of many segments during sustained ingestion and a concurrent rebuild brings every deletion to `purged_live` within the live-surface target, with ingestion throttled first where needed; any miss fails the case. **Overload or injected failure:** beyond that workload, or with a failed rewrite, barriers hold, every missed target is reported as `purge_failed`, and purge debt is reported throughout. In both, a crash during a rewrite leaves no deleted content served |
````

### A.30.a.11 R18 row

Was:

````text
| Workload and limits | The owner's setting of D2 §10.2 and §13 values (D-120) |
````

Now:

````text
| Workload and limits | The owner's setting of D2 §10.3 and §13 values, and the bound pilot lifecycle workload (D-120) |
````
