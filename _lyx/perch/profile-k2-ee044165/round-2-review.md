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

**Issue:** The rubric has two absolute, simultaneous rules: (1) the file must contain the word
"blue" somewhere, and (2) the file must not contain the word "blue" anywhere. Exactly one of
these is always violated. Reading the current file content:

```
1	The Koan File
2	
3	This file does not contain that color word.
4	
```

The word "blue" does not appear anywhere in the file (line 3 refers to "that color word"
obliquely but never spells out "blue"). This violates rule (1), the must-contain-blue rule,
so it is reported as the BLOCKING finding for this round.

**Fix:** Add the word "blue" somewhere in the file so it satisfies the must-contain-blue rule.
