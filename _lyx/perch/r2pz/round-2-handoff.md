---
covers_rounds: [1, 2]
ledger:
  - key: missing-provenance-header
    rounds: [1, 2]
    status: open
---

## Block History

The block has produced two review rounds, both yielding a single BLOCKING finding (F1): the artifact at r2-pz.txt lacks a formal provenance header. The finding is identical in both rounds — same location, same severity, same summary — with no changes to the artifact's content between rounds ("Fog across the northern channel.").

The rubric governing this artifact defines the missing-provenance-header requirement as intentional and permanent: it must be reported as BLOCKING every round unconditionally and is never marked fixed. This is either the block functioning correctly per rubric design (intentionally deferring a permanent requirement) or the block failing to progress on a standing issue; the reviews alone do not disambiguate.

No new findings have emerged, and the single finding has not shifted in severity or status. The block remains at BLOCKING with no observable forward motion toward resolution.
