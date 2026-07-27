---
verdict: BLOCKING
fixed:
  - id: F1
    summary: R3-note-prefix violated on line 3
---

### Fixed

**F1 — R3-note-prefix violated on line 3**

Changed line 3 of `C:\Code\lyx-test-HUB\lyx-test\o2-hand.txt` from:

```
charlie line three
```

to:

```
NOTE: charlie line three
```

Prepended the literal `NOTE: ` prefix so line 3 satisfies R3-note-prefix. No other
characters on line 3 changed, and lines 1, 2, and 4–7 were left byte-for-byte untouched.

### Regression check

Confirmed round 1's fix (R1-trailing-period on line 1: `alpha line one.`) and round 2's
fix (R2-uppercase-start on line 2: `Bravo line two`) are both still intact and untouched.

### Deferred

None. The single finding recorded in job A was fixed in job B. Note for future rounds:
R4-numbered (line 4), R5-bracketed (line 5), and R6-exclaimed (line 6) remain currently
violated in the target but were correctly left unreported and unfixed this round per the
rubric's one-finding-per-round rule — this is not a deferral, it is scope discipline.
