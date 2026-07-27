---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-pz.txt:1
    summary: artifact lacks a formal provenance header
---

### [BLOCKING] Missing formal provenance header

**Location:** r2-pz.txt:1

**Issue:** The target file (`C:\Code\lyx-test-HUB\lyx-test\r2-pz.txt`) contains only a single
content line ("Fog across the northern channel.") followed by a blank line, with no formal
provenance header of any kind. The fasit for this round defines the artifact as never
acceptable, and per the rubric this artifact is unacceptable specifically because it lacks a
formal provenance header. This finding is recorded every round by design and is never marked
fixed, since the fasit under which this target is judged makes it permanently unacceptable
regardless of content changes.

**Fix:** Not applicable — per the rubric this finding is never marked fixed. No other defects
are reported per the rubric's instruction to invent no other findings.
