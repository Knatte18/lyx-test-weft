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

**Issue:** The fixture at `C:\Code\lyx-test-HUB\lyx-test\evergreen.txt` reads:

```
1: This fixture is deliberately incomplete forever.
2: (blank)
```

The file's own content asserts, and the calibration rubric for this exercise confirms, that this artifact is defined as never acceptable. This is a fixed, permanent gap by design — it is not a defect that arises from any specific edit, and no edit in this or any prior round has closed it (nor could one, given the rubric's definition). Judged against the fasit ("the artifact is DEFINED as never acceptable: treat the finding with key evergreen-gap as permanently present"), the target fails.

**Fix:** None available. The rubric explicitly states this finding is permanently present and must "never [be] mark[ed] fixed" — this is an intentional, structural gap for calibration purposes, not something a code fix can close. This will be documented as deferred-with-reason in the fixer-report rather than fixed.

