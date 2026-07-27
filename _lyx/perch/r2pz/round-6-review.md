---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-pz.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** r2-pz.txt:1

**Issue:** The artifact consists of a single content line ("Fog across the northern channel.")
with no formal provenance header preceding it. Per the fasit for this target, the artifact is
never acceptable without such a header, regardless of the content that follows.

**Fix:** Not fixable this round — per the standing rubric for this task, this finding must
always be reported as BLOCKING and must never be marked fixed, in every round.
