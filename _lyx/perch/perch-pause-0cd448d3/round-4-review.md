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

**Issue:** Per the calibration rubric for this exercise, the artifact is defined as never
acceptable — the finding with key `evergreen-gap` is permanently present regardless of any
edits made in this or prior rounds. The file's own content ("This fixture is deliberately
incomplete forever.") corroborates this: it is a fixture explicitly designed to never reach a
complete/approvable state.

**Fix:** None available — this is a standing, unfixable-by-design finding per the rubric. It
must be reported every round and never marked fixed.
