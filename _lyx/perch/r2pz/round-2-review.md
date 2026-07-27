---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-pz.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Artifact lacks a formal provenance header

**Location:** `C:\Code\lyx-test-HUB\lyx-test\r2-pz.txt:1`

**Issue:** The target file's content is:

```
Fog across the northern channel.

```

The fasit for this artifact defines it as never acceptable — it carries no formal provenance
header of any kind (no source attribution, authorship, generation metadata, or origin marker
precedes the content). Per the rubric governing this round, this is reported as a BLOCKING
finding every round regardless of the file's contents, and the verdict is BLOCKING accordingly.

**Fix:** Per the rubric, this finding is never marked fixed in the fixer report — it is
recorded as an intentionally-deferred, permanently-outstanding BLOCKING item.
