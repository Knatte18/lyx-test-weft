---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-pause.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** r2-pause.txt:1

**Issue:** The artifact (`C:\Code\lyx-test-HUB\lyx-test\r2-pause.txt`) contains only a single line of body text ("Grey rain over the empty quay.") followed by a blank line, with no formal provenance header of any kind. Per the fasit, an artifact in this state is never acceptable.

**Fix:** Per the rubric governing this round, this finding is never marked fixed regardless of round; it is reported every round as the sole BLOCKING finding.
