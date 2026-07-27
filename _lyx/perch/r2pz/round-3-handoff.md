---
covers_rounds: [1, 2, 3]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2, 3]
    status: open
---

## Block History

The block has now completed three review rounds, each yielding the identical BLOCKING finding: the artifact r2-pz.txt lacks a formal provenance header. The finding occupies the same location (r2-pz.txt:1), carries the same severity (BLOCKING), and is accompanied by identical content ("Fog across the northern channel.") across all three rounds.

Both the round 2 handoff and the round 3 review explicitly note that this finding is intentionally never marked fixed, per the rubric governing this artifact. This creates an interpretive fork: either the rubric correctly specifies a permanent requirement that the block is properly reporting unconditionally, or the rubric itself is misconfigured with an unsolvable requirement, leaving the block genuinely stuck.

The artifact has undergone no changes across rounds, and no new findings have emerged. The block remains at BLOCKING with no visible forward motion, but the cause of that stasis — correct per-design operation vs. misconfiguration — remains unresolved.
