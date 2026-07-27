---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-hand.txt:6
    summary: R6-exclaimed violated on line 6
---

### [BLOCKING] R6-exclaimed violated on line 6

**Location:** `lyx-test/o2-hand.txt:6`

**Issue:** Line 6 reads `foxtrot line six` and ends with no punctuation at all. Per fasit rule R6-exclaimed, line 6 must end with an exclamation mark (`!`). This is the lowest-numbered still-violated rule this round; R1 through R5 are all already satisfied (line 1 ends with a period, line 2 starts with a capital letter, line 3 starts with `NOTE: `, line 4 starts with `4. `, line 5 is wrapped in square brackets) and are not re-reported.

**Fix:** Change line 6 to end with `!`, e.g. `foxtrot line six!`.
