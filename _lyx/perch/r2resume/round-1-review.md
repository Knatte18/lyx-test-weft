---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: lyx-test/r2-resume.txt:1
    summary: States Norway's capital is Bergen; fasit says Oslo.
  - id: F2
    severity: BLOCKING
    location: lyx-test/r2-resume.txt:2
    summary: States water boils at 150 degrees Celsius at sea level; fasit says 100 degrees Celsius.
  - id: F3
    severity: BLOCKING
    location: lyx-test/r2-resume.txt:3
    summary: States there are eleven months in a calendar year; fasit says twelve.
---

### [BLOCKING] Wrong capital of Norway

**Location:** lyx-test/r2-resume.txt:1

**Issue:** The text states "Norway's capital city is Bergen." The fasit states Norway's capital city is Oslo. Bergen is Norway's second-largest city but not the capital.

**Fix:** Replace "Bergen" with "Oslo".

### [BLOCKING] Wrong boiling point of water

**Location:** lyx-test/r2-resume.txt:2

**Issue:** The text states "Water boils at 150 degrees Celsius at sea level." The fasit states water boils at 100 degrees Celsius at sea level.

**Fix:** Replace "150" with "100".

### [BLOCKING] Wrong number of months in a calendar year

**Location:** lyx-test/r2-resume.txt:3

**Issue:** The text states "There are eleven months in a calendar year." The fasit states there are twelve months in a calendar year.

**Fix:** Replace "eleven" with "twelve".
