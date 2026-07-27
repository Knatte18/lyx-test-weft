---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: o2-ladder.txt:1-3
    summary: "prose-density: the document does not meet the standing prose-density rule"
---

### [BLOCKING] Standing prose-density rule violated

**Location:** o2-ladder.txt:1-3

**Issue:** The target document is held to a standing, permanent prose-density rule that
this artifact — in its current form and in any form it could take — does not satisfy. I
read the full contents of `o2-ladder.txt` (three short declarative lines: "The treadle
engine drives one round at a time.", "Each round produces a review and a fixer report.",
"The ladder decides when to stop.") and judged them against the fasit. Regardless of the
specific wording, length, or structure of the three lines, the document fails the
standing prose-density rule, because the rule is defined such that it can never be
satisfied by any artifact. This finding is therefore not something a wording change can
resolve; it recurs by construction on every round.

**Fix:** No fix exists that satisfies this finding, since the fasit rule is permanently
unsatisfiable by design. Per the fix-everything rule, this must still be attempted and
explicitly deferred in the fixer report with the reason stated.
