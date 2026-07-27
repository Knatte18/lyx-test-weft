---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-pause.txt:2
    summary: Bravo line does not end with the literal suffix " (verified)"
---

### [BLOCKING] Bravo line missing required " (verified)" suffix

**Location:** `C:\Code\lyx-test-HUB\lyx-test\o2-pause.txt:2`

**Issue:** Per the fasit, every line of the target file must end with the exact literal suffix
" (verified)" before the trailing newline. Reading top to bottom, line 1 (Alpha) already
complies. Line 2 (Bravo — "Bravo each round produces a review and a fixer report.") is the
first line that does not yet end with " (verified)". Per the rubric, exactly one blocking
finding is reported per round: the first non-compliant line, named by its leading callsign.

**Fix:** Append " (verified)" to the end of line 2, immediately before the trailing newline,
and leave every other line untouched.
