---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: perchwork/koan3.txt:3
    summary: File does not contain the word "blue" anywhere, violating the must-contain-blue rule.
---

### [BLOCKING] File does not contain the word "blue"

**Location:** perchwork/koan3.txt:3

**Issue:** The rubric requires (rule 2) that the file contain the word "blue" somewhere. The file's only content-bearing line reads "This file does not contain that color word." — it alludes to a color word without ever spelling out "blue", so the literal string "blue" is absent from the file.

**Fix:** Add the word "blue" to the file so the must-contain-blue rule is satisfied.
