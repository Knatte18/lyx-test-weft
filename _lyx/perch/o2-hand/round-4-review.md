---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: o2-hand.txt:4
    summary: R4-numbered violated on line 4
---

### [BLOCKING] R4-numbered violated on line 4

**Location:** o2-hand.txt:4

**Issue:** Line 4 reads "delta line four" but the fasit requires line 4 to start with the literal "4. ". It does not.

**Fix:** Prepend "4. " to the start of line 4, yielding "4. delta line four".
