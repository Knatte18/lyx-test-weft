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

**Issue:** The target file states, in its own text, "This fixture is deliberately incomplete
forever." Per the rubric governing this calibration exercise, the artifact is defined as never
acceptable — this gap is permanent by construction, not something any edit within this round can
close. Judged against the fasit (which defines the artifact as never acceptable), the file fails
review.

**Fix:** None available — the rubric explicitly states this finding must be reported every round
regardless of any edits, and must never be marked fixed. No code/content change in this round can
satisfy the fasit, since the fasit defines the target as permanently incomplete.
