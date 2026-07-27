---
covers_rounds: [1, 2, 3]
ledger:
  - key: evergreen-gap
    rounds: [1, 2, 3]
    status: open
---

## Summary

This calibration fixture is designed to validate detection of a permanent, unfixable defect. All three rounds consistently identify the same BLOCKING finding (evergreen-gap) at evergreen.txt:1, where the fixture's own content states "This fixture is deliberately incomplete forever." The rubric explicitly specifies this finding should never be marked fixed—it is a structural, by-design gap for calibration purposes.

The block has converged on the correct finding and continues to report it accurately without oscillation or degradation. However, no forward progress is plausible: the defect cannot be fixed, no new findings appear, and further rounds would only reproduce the same result. The reviews are stable and correct, indicating the system is working as intended for a permanently defective test artifact.

The ledger carries evergreen-gap forward as `open` across all three rounds to reflect its persistent, intentional nature—this is not a transient defect waiting to be closed, but a calibration marker of correct system behavior.
