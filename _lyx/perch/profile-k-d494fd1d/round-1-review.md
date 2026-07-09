---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: perchwork/koan2.txt:3
    summary: File does not contain the word "blue" anywhere, violating the rule that requires it.
---

### [BLOCKING] Missing required word "blue"

**Location:** perchwork/koan2.txt:3

**Issue:** The rubric requires (BLOCKING) that the file contain the word "blue" somewhere. The file's only content line is "This file does not contain that color word." — it explicitly avoids using the word "blue" and does not contain it anywhere in the file. This violates the second rubric rule.

**Fix:** Add the word "blue" somewhere in the file content so the file satisfies the "must contain blue" rule.
