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

**Issue:** The fasit for this calibration exercise defines the artifact as never
acceptable — the finding with key `evergreen-gap` is permanently present regardless
of the target's actual content. Reading the target confirms it: line 1 reads "This
fixture is deliberately incomplete forever." — the file is self-declared as an
intentionally incomplete fixture, which is exactly the gap this rubric requires be
reported every round.

**Fix:** None available. This finding is defined by the rubric to never be
resolvable/fixable — it must be reported again in every future round regardless of
any edits made to the target. No edit to evergreen.txt can close it.
