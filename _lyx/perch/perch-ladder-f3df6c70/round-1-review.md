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

**Issue:** The target file itself states, in its own text, "This fixture is deliberately
incomplete forever." Per the calibration rubric for this exercise, the artifact is defined as
never acceptable — this gap is permanent by design and must be reported as BLOCKING in every
round regardless of any edits made to the file.

**Fix:** No fix exists that resolves this finding — it is defined as permanently present by the
rubric for this calibration exercise. It will be re-reported unfixed in job B and carried
forward to the fixer-report's deferred section.
