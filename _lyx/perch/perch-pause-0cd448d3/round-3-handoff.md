---
covers_rounds: [1, 2, 3]
ledger:
  - key: evergreen-gap
    rounds: [1, 2, 3]
    status: open
---

This block has received a single, consistent BLOCKING finding across all three rounds: `evergreen-gap` at evergreen.txt:1. The finding is permanent by design — the fixture's own content declares "This fixture is deliberately incomplete forever," and all three reviews explicitly acknowledge the finding as unfixable within the scope of the calibration rubric. This is not a failed fix loop or oscillation; rather, the block is correctly identifying an intentionally permanent gap that the rubric requires be reported in every round. The finding shows no progression toward resolution because none is intended.
