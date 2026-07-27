---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: o2-hand.txt:3
    summary: R3-note-prefix violated on line 3
---

### [BLOCKING] R3-note-prefix violated on line 3

**Location:** o2-hand.txt:3

**Issue:** Rule R3-note-prefix requires line 3 to start with the literal `"NOTE: "`. The
current line 3 reads `charlie line three`, which does not start with that prefix.

**Fix:** Prepend `NOTE: ` to the start of line 3, yielding `NOTE: charlie line three`.

Evaluation of all six fasit rules against the current target contents (read directly from
`o2-hand.txt`):

- R1-trailing-period (line 1, `alpha line one.`): satisfied — ends with a period.
- R2-uppercase-start (line 2, `Bravo line two`): satisfied — starts with capital `B`.
- R3-note-prefix (line 3, `charlie line three`): **violated** — does not start with `NOTE: `.
  This is the lowest-numbered violated rule, so it is the sole reported finding this round.
- R4-numbered (line 4, `delta line four`): also currently violated (does not start with
  `4. `), but per the rubric only the lowest-numbered violated rule is reported this round;
  R4 is left unreported and untouched.
- R5-bracketed (line 5, `echo line five`): also currently violated (not wrapped in `[...]`),
  left unreported and untouched this round for the same reason.
- R6-exclaimed (line 6, `foxtrot line six`): also currently violated (does not end with `!`),
  left unreported and untouched this round for the same reason.
