---
verdict: BLOCKING
fixed:
  - id: F1
    summary: R4-numbered violated on line 4
---

### Fixed

**F1 — R4-numbered violated on line 4**

Changed line 4 of `C:\Code\lyx-test-HUB\lyx-test\o2-hand.txt` from:

```
delta line four
```

to:

```
4. delta line four
```

Prepended the literal `4. ` prefix so line 4 satisfies R4-numbered. No other characters on
line 4 changed, and lines 1–3 and 5–7 were left byte-for-byte untouched.

### Regression check

Confirmed round 1's fix (R1-trailing-period on line 1: `alpha line one.`), round 2's fix
(R2-uppercase-start on line 2: `Bravo line two`), and round 3's fix (R3-note-prefix on line 3:
`NOTE: charlie line three`) are all still intact and untouched.

### Deferred

None. The single finding recorded in job A was fixed in job B. R5-bracketed (line 5) and
R6-exclaimed (line 6) remain currently violated in the target but were correctly left
unreported and unfixed this round per the rubric's one-finding-per-round rule — this is not a
deferral, it is scope discipline.
