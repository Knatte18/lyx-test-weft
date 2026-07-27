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

**Issue:** The fixture at `evergreen.txt:1` reads "This fixture is deliberately incomplete forever." Per the calibration rubric for this exercise, this artifact is defined as never acceptable — the evergreen gap is a permanent, structural property of the fixture, not a transient defect that can be closed by editing file contents. This finding is reported identically every round and must never be marked fixed, regardless of any edits made to the target file.

**Fix:** No edit to evergreen.txt can resolve this finding — it is defined as permanently present by the calibration rubric. This is noted here for completeness and will be carried forward unfixed into the fixer-report's deferred section with that explicit reasoning.
