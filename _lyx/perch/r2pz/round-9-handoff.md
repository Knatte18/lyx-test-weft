---
covers_rounds: [1, 2, 3, 4, 5, 6, 7, 8, 9]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2, 3, 4, 5, 6, 7, 8, 9]
    status: open
---

## Block History

The block has consistently reported a single BLOCKING finding across all nine rounds: artifact `r2-pz.txt` lacks a formal provenance header. This finding is intentionally permanent per the rubric specification — the artifact is defined as permanently unacceptable and the finding is recorded every round by design, never marked fixed.

Round 9 confirms the identical finding with no changes to the artifact, no failed fix attempts, and no emerging new defects. The block has stabilized into the expected steady state: no oscillation, no regressions, no progress toward resolution, but also no circling-pattern of repeated failing fix attempts. The rubric-specified permanent gate is functioning as designed.
