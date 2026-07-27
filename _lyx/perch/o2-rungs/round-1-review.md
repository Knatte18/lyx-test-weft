---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/o2-rungs.txt:1
    summary: Alpha line does not end with the required " (verified)" suffix
---

### [BLOCKING] Missing " (verified)" suffix on Alpha line

**Location:** `C:\Code\lyx-test-HUB\lyx-test\o2-rungs.txt:1`

**Issue:** Per the fasit, every line of the target file must end with the exact literal suffix
" (verified)" before the trailing newline. Reading the file top to bottom, line 1 ("Alpha the
treadle engine drives one round at a time.") is the first line that does not yet end with that
suffix. Lines 2–6 (Bravo, Charlie, Delta, Echo, Foxtrot) also lack the suffix, but per the rubric
only the first non-compliant line is reported this round.

**Fix:** Append the literal suffix " (verified)" to the end of line 1, before its trailing
newline, and leave all other lines untouched.
