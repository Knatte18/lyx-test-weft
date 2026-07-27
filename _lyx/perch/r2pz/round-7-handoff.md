---
covers_rounds: [1, 2, 3, 4, 5, 6, 7]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2, 3, 4, 5, 6, 7]
    status: open
---

## Block History

Across all seven rounds, the block reports a single BLOCKING finding: the artifact `r2-pz.txt` lacks a formal provenance header. Per the rubric specification (documented since round 5), this finding is intentionally permanent — the artifact is defined as never acceptable and "cannot satisfy the provenance requirement, and it does not."

Round 7 confirms the identical finding from round 6 with no change. The review reiterates that this finding "is never marked fixed in any round. No fix is applied."

The block has stabilized into a predictable steady state: it will continue reporting this single, unchanging, intentionally-permanent requirement until the hard cap (round 20). No oscillation has occurred (the finding was never fixed then broken again), no new findings have emerged, and the artifact content remains unchanged. The underlying ambiguity persists unresolved: whether this represents productive permanent-gate design (a correctly-functioning block) or a block genuinely stuck reporting the same unchangeable requirement round after round.
