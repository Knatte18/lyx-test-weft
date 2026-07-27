---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: C:\Code\lyx-test-HUB\lyx-test\o2-rungs.txt:3
    summary: Charlie line does not end with the literal suffix " (verified)"
---

### [BLOCKING] Charlie line missing required "(verified)" suffix

**Location:** `C:\Code\lyx-test-HUB\lyx-test\o2-rungs.txt:3`

**Issue:** Per the fasit, every line of the target file must end with the exact literal
suffix " (verified)" before the trailing newline. Reading top to bottom, line 1 (Alpha) and
line 2 (Bravo) already comply. Line 3 — "Charlie the ladder decides when to stop." — is the
first line that does not end with " (verified)".

**Fix:** Append the literal suffix " (verified)" to the end of line 3, immediately after the
final period, with no other changes to the line's text.
