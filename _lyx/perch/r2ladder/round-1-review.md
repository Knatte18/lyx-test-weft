---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: C:\Code\lyx-test-HUB\lyx-test\r2-ladder.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** C:\Code\lyx-test-HUB\lyx-test\r2-ladder.txt:1

**Issue:** The target file consists of a single content line ("Blue sky over the quiet harbour.") followed by a blank line, with no provenance header of any kind preceding the content. Per the fasit for this round, an artifact without a formal provenance header is never acceptable, regardless of what else the file contains.

**Fix:** Per the rubric, this finding is never marked fixed in any round — it is reported every round unconditionally.
