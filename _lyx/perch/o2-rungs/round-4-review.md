---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-rungs.txt:4
    summary: Delta line does not end with the literal suffix " (verified)"
---

### [BLOCKING] Delta line missing " (verified)" suffix

**Location:** `C:\Code\lyx-test-HUB\lyx-test\o2-rungs.txt:4`

**Issue:** Per the fasit, every line of the target file must end with the exact literal suffix
" (verified)" before the trailing newline. Reading top to bottom, lines 1 (Alpha), 2 (Bravo),
and 3 (Charlie) already comply. Line 4 — "Delta the judge maintains a handoff between rounds." —
is the first line that does not yet end with " (verified)".

**Fix:** Append the literal suffix " (verified)" to the end of line 4, leaving all other lines
untouched.
