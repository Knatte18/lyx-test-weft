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

**Issue:** The target file consists solely of the line "Grey rain over the empty quay." with no
formal provenance header of any kind (no author, source, timestamp, revision, or origin
metadata preceding the content). Per the fasit, an artifact lacking a formal provenance header
is never acceptable, regardless of the quality or content of the body text.

**Fix:** Not fixed — see fixer-report deferred section. A "formal provenance header" is an
operator-defined convention (required fields, format, placement) that has not been specified
anywhere in the target repository, the fasit, or the rubric. Inventing a header format
unilaterally would not satisfy an unstated formal standard, and the rubric explicitly directs
that this finding is never to be marked fixed in any round.
