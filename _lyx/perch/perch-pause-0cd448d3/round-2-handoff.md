---
covers_rounds: [1, 2]
ledger:
  - key: evergreen-gap-permanent
    rounds: [1, 2]
    status: open
---

## Block Summary

This perch block contains a calibration fixture (evergreen.txt) that is intentionally incomplete and designed by the rubric to report a permanent, unfixable finding every round. Round 1 and Round 2 both correctly identify the `evergreen-gap` finding at evergreen.txt:1 with BLOCKING severity. This is expected, steady-state behavior—the same finding reappears each round because the fixture is explicitly designed to be permanently incomplete and unsolvable. No fix is available or expected. The block is functioning as intended for this type of calibration exercise.
