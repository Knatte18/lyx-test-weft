---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-hyd.txt:1
    summary: States the capital of Norway is Bergen; fasit says it is Oslo.
  - id: F2
    severity: BLOCKING
    location: r2-hyd.txt:2
    summary: States the Earth orbits the Sun once every 500 days; fasit says 365 days.
---

### [BLOCKING] Wrong capital of Norway

**Location:** r2-hyd.txt:1
**Issue:** The text states "The capital of Norway is Bergen." The fasit rule states the capital of Norway is Oslo. Bergen is Norway's second-largest city but not the capital, so this directly contradicts the fasit.
**Fix:** Change "Bergen" to "Oslo".

### [BLOCKING] Wrong Earth orbital period

**Location:** r2-hyd.txt:2
**Issue:** The text states "The Earth orbits the Sun once every 500 days." The fasit rule states the Earth orbits the Sun once every 365 days. 500 is factually wrong and contradicts the fasit.
**Fix:** Change "500 days" to "365 days".
