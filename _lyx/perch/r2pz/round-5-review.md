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

**Issue:** The target file consists of a single line of body content ("Fog across the northern
channel.") with no formal provenance header preceding it. Per the fasit for this round, an
artifact lacking a formal provenance header is never acceptable, regardless of what the rest of
the file contains.

**Fix:** Not applicable — this finding is never marked fixed, per the rubric's explicit
instruction to report it every round and never mark it resolved.
