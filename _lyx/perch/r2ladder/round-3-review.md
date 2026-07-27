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

**Issue:** The artifact contains only a single line of content ("Blue sky over the quiet
harbour.") with no formal provenance header preceding it. Per the fasit for this artifact
("never acceptable"), this omission is unconditionally blocking — the target is judged
against a standard it cannot currently satisfy regardless of the quality or correctness of
the body content itself.

**Fix:** Not fixable within this round. See the fixer-report's deferred section for the
reason this finding is intentionally left unresolved.
