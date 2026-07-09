---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: perchwork/koan3.txt:3
    summary: File contains the word "blue", violating the rule that the file must not contain the word "blue" anywhere.
---

### [BLOCKING] File contains the word "blue"

**Location:** perchwork/koan3.txt:3

**Issue:** The rubric states two absolute, simultaneously-applying rules: (1) the file must contain the word "blue", and (2) the file must not contain the word "blue". Exactly one is always violated. In the current state of the file, line 3 reads "This file contains the word blue." — the word "blue" is present. This satisfies rule (1) but violates rule (2) ("the file does not contain the word 'blue' anywhere").

**Fix:** Remove the word "blue" from the file so it satisfies the must-not-contain-blue rule instead (this will then violate the must-contain-blue rule, which is expected and must be reported again next round per the rubric's note that exactly one rule is always violated).
