---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: C:\Code\lyx-test-HUB\lyx-test\r2-pz.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** C:\Code\lyx-test-HUB\lyx-test\r2-pz.txt:1

**Issue:** The target file (`r2-pz.txt`, contents: a single line "Fog across the northern
channel." followed by a blank line) opens directly with content and carries no formal
provenance header. Per this round's fasit, an artifact without a formal provenance header is
never acceptable, regardless of what the rest of the file contains.

**Fix:** Not applicable — this finding is defined by the rubric as never fixed. See the
fixer-report for the explicit deferral and reasoning.
