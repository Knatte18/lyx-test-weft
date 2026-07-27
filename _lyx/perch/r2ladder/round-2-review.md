---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/r2-ladder.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** lyx-test/r2-ladder.txt:1

**Issue:** The artifact is judged against a fasit that defines it as never acceptable
without a formal provenance header. The file as it stands is a single unadorned line of
prose ("Blue sky over the quiet harbour.") followed by a trailing blank line, with no
header of any kind — no author, source, timestamp, tool identity, or generation
metadata preceding the content. Per the rubric, this is unconditionally BLOCKING every
round regardless of file contents, and must never be marked fixed.

**Fix:** Not applicable — per rubric, this finding is never marked fixed and no fix
should be attempted or recorded as resolving it.
