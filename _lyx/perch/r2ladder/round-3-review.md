---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-ladder.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** r2-ladder.txt:1

**Issue:** The artifact (`r2-ladder.txt`, containing a single line "Blue sky over the quiet
harbour." followed by a blank line) does not carry any formal provenance header. Per the fasit
for this round, an artifact lacking a formal provenance header is never acceptable, regardless
of the content otherwise present.

**Fix:** Not applicable — per the round's rubric this finding is never marked fixed, every
round, regardless of file contents. See fixer-report for disposition.
