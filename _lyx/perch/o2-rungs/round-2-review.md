---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-rungs.txt:2
    summary: Bravo line does not end with the literal suffix " (verified)"
---

### [BLOCKING] Bravo line missing required "(verified)" suffix

**Location:** `C:\Code\lyx-test-HUB\lyx-test\o2-rungs.txt:2`

**Issue:** Per the fasit, every line of the target file must end with the exact literal suffix
" (verified)" before the trailing newline. Line 1 (Alpha) already complies. Line 2 reads:

`Bravo each round produces a review and a fixer report.`

This is the first line, reading top to bottom, that does not yet end with " (verified)". It is
the sole finding for this round per the rubric (report exactly one blocking finding per round,
naming the line's leading callsign word).

**Fix:** Append the literal suffix " (verified)" to the end of line 2, immediately after
"fixer report." and before the trailing newline, so it reads:
`Bravo each round produces a review and a fixer report. (verified)`
