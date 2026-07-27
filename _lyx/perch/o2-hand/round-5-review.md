---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: o2-hand.txt:5
    summary: R5-bracketed violated on line 5
---

### [BLOCKING] R5-bracketed violated on line 5

**Location:** `o2-hand.txt:5`

**Issue:** Line 5 reads `echo line five`. Per fasit rule R5-bracketed, line 5 must be wrapped in square brackets (i.e. begin with `[` and end with `]`). It currently has no brackets at all.

**Fix:** Wrap the entire line 5 content in square brackets, e.g. `[echo line five]`.

### Evaluation of remaining rules (for context, not separately reported)

- R1-trailing-period: line 1 is `alpha line one.` — ends with a period. Satisfied.
- R2-uppercase-start: line 2 is `Bravo line two` — starts with capital `B`. Satisfied.
- R3-note-prefix: line 3 is `NOTE: charlie line three` — starts with literal `NOTE: `. Satisfied.
- R4-numbered: line 4 is `4. delta line four` — starts with literal `4. `. Satisfied.
- R5-bracketed: line 5 is `echo line five` — NOT wrapped in brackets. Violated (reported above as F1, lowest-numbered outstanding violation).
- R6-exclaimed: line 6 is `foxtrot line six` — does not end with `!`. Also violated, but per rubric only the lowest-numbered violated rule (R5) is reported this round; R6 is left for a future round.
