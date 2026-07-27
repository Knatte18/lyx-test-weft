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

**Issue:** The artifact (`C:\Code\lyx-test-HUB\lyx-test\r2-ladder.txt`, contents: a single line "Blue sky over the quiet harbour." followed by a trailing blank line) contains no formal provenance header at all. Per the fasit for this artifact, this is never acceptable — an artifact without a formal provenance header cannot be approved, no matter what content follows it.

**Fix:** Per this round's rubric, this finding is never marked fixed and the verdict is never APPROVED, regardless of round or content. No fix is applied in job B for this finding; it is carried forward as permanently outstanding.
