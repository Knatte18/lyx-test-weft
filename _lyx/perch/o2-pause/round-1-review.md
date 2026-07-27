---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: C:\Code\lyx-test-HUB\lyx-test\o2-pause.txt:1
    summary: Alpha line does not end with the literal suffix " (verified)"
---

### [BLOCKING] Alpha line missing required " (verified)" suffix

**Location:** `C:\Code\lyx-test-HUB\lyx-test\o2-pause.txt:1`

**Issue:** Per the fasit, every line of the target file must end with the exact literal
suffix " (verified)" before the trailing newline. Reading top to bottom, line 1 ("Alpha the
treadle engine drives one round at a time.") is the first line that does not yet end with
that suffix — it currently ends with a period only.

**Fix:** Append the literal suffix " (verified)" to the end of line 1, immediately after the
existing text, before the line's trailing newline.
