---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-hand.txt:2
    summary: R2-uppercase-start violated on line 2
---

### [BLOCKING] R2-uppercase-start violated on line 2

**Location:** `lyx-test/o2-hand.txt:2`

**Issue:** Line 2 reads `bravo line two`, starting with a lowercase `b`. Fasit rule
R2-uppercase-start requires line 2 to start with a capital letter. This is the
lowest-numbered still-violated fasit rule (R1 is already satisfied — line 1 ends
with a period), so it is the sole finding for this round.

**Fix:** Capitalize the first letter of line 2, changing `bravo line two` to
`Bravo line two`. No other characters on the line change, and no other lines are
touched.
