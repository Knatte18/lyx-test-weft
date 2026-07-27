---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r2-hyd.txt:1
    summary: "capital" is misspelled as "captial" (both occurrences on line 1)
  - id: F2
    severity: BLOCKING
    location: r2-hyd.txt:1
    summary: States the capital of Norway is Bergen; the fasit says it is Oslo
---

### [BLOCKING] Misspelled "capital"

**Location:** r2-hyd.txt:1

**Issue:** The word "capital" is spelled "captial" in both instances on line 1 ("The captial of France is Paris. The captial of Norway is Bergen."). The fasit requires "capital" to be spelled correctly.

**Fix:** Replace both occurrences of "captial" with "capital".

### [BLOCKING] Wrong capital of Norway

**Location:** r2-hyd.txt:1

**Issue:** The text states "The captial of Norway is Bergen." The fasit states the capital of Norway is Oslo, not Bergen.

**Fix:** Replace "Bergen" with "Oslo".
