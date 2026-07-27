---
covers_rounds: [1, 2]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2]
    status: open
---

## Narrative

The block has been stuck on a single BLOCKING finding across both rounds: the target artifact (r2-pause.txt) lacks a formal provenance header. Per the rubric, this finding is intentionally unfixable — no operator-defined spec for the required header format has been provided, and the fasit does not detail one. The finding is reported every round and explicitly marked as never to be marked fixed, making this a standing requirement gap rather than a fixable defect. No forward motion has occurred; R1 and R2 show identical verdicts and the same unresolved F1.
