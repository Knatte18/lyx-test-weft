---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: perchwork/report.txt:7
    summary: Summary sentence says "revenue shrank" but the body (line 3) says revenue grew 12% in Q3.
  - id: F2
    severity: BLOCKING
    location: perchwork/report.txt:6
    summary: Misspelled word "employes" should be "employees".
  - id: F3
    severity: MEDIUM
    location: perchwork/report.txt:4-5
    summary: Run-on sentence — two independent clauses ("...the third consecutive quarterly decline" and "however operating costs also grew 12%...") are joined with no punctuation or conjunction between them.
  - id: F4
    severity: MEDIUM
    location: perchwork/report.txt:5
    summary: Missing sentence-initial capitalization — "we expect Q4 revenue growth of 8-10%." should start with "We".
---

### [BLOCKING] Summary contradicts body on revenue direction

**Location:** perchwork/report.txt:7

**Issue:** The closing sentence states "In summary, revenue shrank while costs were contained," but the opening sentence of the report (line 3) states "Revenue grew 12% in Q3." These two claims directly contradict each other — one says revenue shrank, the other says it grew. Additionally, "costs were contained" contradicts the body's statement that "operating costs also grew 12%."

**Fix:** Rewrite the summary sentence to match the body: revenue grew 12% and costs also grew 12%, keeping margins flat (not "revenue shrank while costs were contained").

### [BLOCKING] Misspelled word "employes"

**Location:** perchwork/report.txt:6

**Issue:** "Headcount grew from 240 to 260 employes during the quarter." — "employes" is a misspelling of "employees".

**Fix:** Change "employes" to "employees".

### [MEDIUM] Run-on sentence joining churn-decline and cost-growth clauses

**Location:** perchwork/report.txt:4-5

**Issue:** "Our churn rate fell from 5.2% to 4.1%, the third consecutive quarterly decline however operating costs also grew 12%, which means margins were flat." runs two independent clauses together with no conjunction or punctuation ("...quarterly decline" / "however operating costs...") — a run-on sentence.

**Fix:** Split into two sentences (or insert a semicolon/period) before "however", e.g.: "Our churn rate fell from 5.2% to 4.1%, the third consecutive quarterly decline. However, operating costs also grew 12%, which means margins were flat."

### [MEDIUM] Missing sentence-initial capitalization on "we expect"

**Location:** perchwork/report.txt:5

**Issue:** The sentence "we expect Q4 revenue growth of 8-10%." begins with a lowercase "we".

**Fix:** Capitalize to "We expect Q4 revenue growth of 8-10%."
