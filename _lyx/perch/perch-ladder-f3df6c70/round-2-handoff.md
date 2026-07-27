---
covers_rounds: [1, 2]
ledger:
  - key: evergreen-gap
    rounds: [1, 2]
    status: open
---

## Summary

This is a calibration fixture designed to validate detection of permanently unfixable defects. Both Round 1 and Round 2 identify the same BLOCKING finding (F1: evergreen-gap) at evergreen.txt:1, where the fixture deliberately states it is "incomplete forever." The reviews explicitly document this as a permanent, structural property of the test artifact — not a transient defect that can be closed through editing.

The consistent re-reporting of this finding across both rounds indicates the system is working correctly: it identifies and accurately reports a by-design, unfixable condition without claiming a fix exists or oscillating between fixed/broken states. The ledger carries forward evergreen-gap as `open` to indicate it remains a reported finding, though its permanent nature means it is not fixable by the block.
