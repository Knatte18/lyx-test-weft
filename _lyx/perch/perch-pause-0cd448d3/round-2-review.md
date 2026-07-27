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

**Issue:** The fasit for this calibration exercise defines the artifact as never acceptable —
the key `evergreen-gap` finding must be treated as permanently present, regardless of the
target's actual content. Reading the file confirms it: line 1 reads "This fixture is
deliberately incomplete forever." This is a self-describing fixture whose entire purpose is to
never satisfy the fasit. There is no edit to this file that can close this gap, since the
rubric fixes this finding as permanent for calibration purposes.

**Fix:** None available — this is a deliberately permanent, unfixable finding by design of the
calibration exercise. It will be re-reported unfixed in job B's fixer-report as a deferred item,
with this exact reason stated explicitly.
