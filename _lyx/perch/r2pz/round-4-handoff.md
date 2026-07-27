---
covers_rounds: [1, 2, 3, 4]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2, 3, 4]
    status: open
---

## Block History

The block has produced four consecutive review rounds, each identifying the same single BLOCKING finding: the artifact (r2-pz.txt / lyx-test/r2-pz.txt) lacks a formal provenance header. The finding is consistent across all rounds—same location, same severity, same issue.

Per the rubric governing this artifact, the missing-provenance-header requirement is intentional and permanent: it must be reported as BLOCKING every round unconditionally and is explicitly never to be marked fixed. This is designed behavior, not a stuck block. There is no evidence of fix attempts or oscillation—each round simply and correctly reports the permanent constraint.

No new findings have emerged across the four rounds. The block is functioning as designed: reporting the same intentional, unfixable finding every round with no deviation or oscillation.
