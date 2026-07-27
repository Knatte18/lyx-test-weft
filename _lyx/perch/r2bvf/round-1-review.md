---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: C:\Code\lyx-test-HUB\lyx-test\r2-gate.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** C:\Code\lyx-test-HUB\lyx-test\r2-gate.txt:1

**Issue:** The file consists solely of the line "A short note about the harbour." with no
formal provenance header preceding it. Per the fasit for this round, this artifact is defined
as never acceptable — no formal provenance header is present, and no content of this artifact
can satisfy that requirement this round.

**Fix:** Not applicable — per the rubric governing this round, this finding is never marked
fixed, regardless of what the file contains.
