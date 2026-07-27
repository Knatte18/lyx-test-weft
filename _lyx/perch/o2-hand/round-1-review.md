---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-hand.txt:1
    summary: R1-trailing-period violated on line 1
---

### [BLOCKING] R1-trailing-period violated on line 1

**Location:** lyx-test/o2-hand.txt:1

**Issue:** Line 1 reads "alpha line one" and does not end with a period. Fasit rule R1-trailing-period requires line 1 to end with a period.

**Fix:** Append a period to the end of line 1 so it reads "alpha line one.".
