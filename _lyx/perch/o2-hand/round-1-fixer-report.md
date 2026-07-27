---
verdict: BLOCKING
fixed:
  - id: F1
    summary: R1-trailing-period violated on line 1
---

### Fixed

**F1 — R1-trailing-period violated on line 1**

Changed line 1 of `C:\Code\lyx-test-HUB\lyx-test\o2-hand.txt` from:

```
alpha line one
```

to:

```
alpha line one.
```

Appended a trailing period so line 1 satisfies R1-trailing-period. No other bytes on line 1 were changed, and lines 2–7 were left byte-for-byte untouched.

### Deferred

None. The single finding recorded in job A was fixed in job B.
