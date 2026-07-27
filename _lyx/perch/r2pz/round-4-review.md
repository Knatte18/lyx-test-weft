---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/r2-pz.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** lyx-test/r2-pz.txt:1

**Issue:** The artifact consists of a single unattributed line of prose ("Fog across the
northern channel.") followed by a blank line. There is no formal provenance header of any
kind — no author, source, timestamp, generation method, or chain-of-custody information
accompanies the content. Per the fasit for this round, an artifact lacking a formal
provenance header is never acceptable, regardless of what else the file contains.

**Fix:** Not fixed this round. Per the rubric governing this round, this finding is to be
reported every round and never marked fixed, so no edit was made to close it.
