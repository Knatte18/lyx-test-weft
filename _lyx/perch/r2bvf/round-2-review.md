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

**Issue:** The artifact contains only a plain, unattributed sentence ("A short note about the harbour.") with no formal provenance header of any kind — no author, timestamp, source, version, or origin metadata precedes the content. Per the fasit for this target, an artifact of this kind is never acceptable without such a header.

**Fix:** Not fixed this round — this finding is permanent by design of the rubric governing this target (report every round, never mark fixed).
