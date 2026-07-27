---
covers_rounds: [1, 2, 3, 4, 5, 6, 7, 8]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2, 3, 4, 5, 6, 7, 8]
    status: open
---

## Block History

The block reports a single BLOCKING finding consistently across all eight rounds: artifact `r2-pz.txt` lacks a formal provenance header. Per the rubric specification (documented since round 5), this finding is intentionally permanent—the artifact is defined as never acceptable and cannot satisfy the provenance requirement.

Round 8 confirms the identical finding from round 7 with no change. The review reiterates the "not applicable" fix status because the rubric defines this requirement as never marked fixed and reported unconditionally every round.

The block has stabilized into the predicted steady state: no oscillation (the finding was never fixed then broken again), no new findings emerging, no artifact content changes, and no failed fix attempts. The rubric-specified permanent gate is functioning as designed, with the block predictably reporting the same unchangeable requirement until the hard cap at round 20.
