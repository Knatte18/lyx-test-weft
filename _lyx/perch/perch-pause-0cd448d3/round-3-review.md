---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: evergreen.txt:1
    summary: "evergreen-gap: the fixture is deliberately incomplete"
---

### [BLOCKING] evergreen-gap: the fixture is deliberately incomplete

**Location:** evergreen.txt:1

**Issue:** The target file's own content states, verbatim, "This fixture is deliberately incomplete forever." Per the fasit for this calibration exercise, the artifact is defined as never acceptable — this gap is permanent and structural, not a transient defect that a text edit can resolve. The file consists of a single declarative line asserting its own incompleteness (line 1) followed by a blank line 2, with no further content addressing what is "missing."

**Fix:** None available within the scope of a single burl round. This finding is designed to remain permanently present per the calibration rubric — it must be re-reported, unfixed, in every subsequent round regardless of any edits made to the file.
