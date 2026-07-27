---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/both.txt:1
    summary: the word capitol is used where capital is the correct spelling for the governmental sense of the word
  - id: F2
    severity: BLOCKING
    location: lyx-test/both.txt:1
    summary: the city name Osloo is misspelled and should be Oslo
---

### [BLOCKING] "capitol" used instead of "capital"

**Location:** lyx-test/both.txt:1

**Issue:** The sentence reads "The capitol of Norway is Osloo." The word "capitol" refers to a building (e.g., a legislative building), not the concept of a capital city. The fasit requires the sentence to read "The capital of Norway is Oslo." — the target uses the wrong word/spelling for this sense.

**Fix:** Replace "capitol" with "capital".

### [BLOCKING] "Osloo" misspelled

**Location:** lyx-test/both.txt:1

**Issue:** The city name is spelled "Osloo" with an extra "o". The correct spelling, per the fasit, is "Oslo".

**Fix:** Replace "Osloo" with "Oslo".
