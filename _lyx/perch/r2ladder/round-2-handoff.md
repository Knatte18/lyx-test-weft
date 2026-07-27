---
covers_rounds: [1, 2]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2]
    status: open
---

## Block Summary

Round 1 and 2 both report the same BLOCKING finding: F1 (missing formal provenance header). The artifact in question consists of a single unadorned content line ("Blue sky over the quiet harbour.") followed by a blank line, with no author, source, timestamp, tool identity, or generation metadata header preceding it.

Both reviews explicitly note that per the artifact's rubric, this finding is unconditionally reported every round and must never be marked fixed or attempted to be resolved. This creates an ambiguous picture: the repeated finding could indicate the block is stuck against an unsolvable constraint, or it could reflect expected test behavior. No other findings or variations have appeared across the two rounds. The block has not shown progress toward resolution of the provenance header issue, but the rubric's explicit design makes the intent and expected behavior unclear.
