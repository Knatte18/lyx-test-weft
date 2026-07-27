---
verdict: BLOCKING
fixed:
  - id: F1
    summary: R2-uppercase-start violated on line 2
---

### Fixed

**F1 — R2-uppercase-start violated on line 2**

Changed line 2 of `C:\Code\lyx-test-HUB\lyx-test\o2-hand.txt` from:

```
bravo line two
```

to:

```
Bravo line two
```

Capitalized the first letter so line 2 satisfies R2-uppercase-start. No other
characters on line 2 changed, and lines 1 and 3–7 were left byte-for-byte
untouched.

### Regression check

Confirmed round 1's fix (R1-trailing-period on line 1: "alpha line one.") is
still intact and untouched.

### Deferred

None. The single finding recorded in job A was fixed in job B.
