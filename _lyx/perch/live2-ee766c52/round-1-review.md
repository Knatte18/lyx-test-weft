---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r3work/essay2.txt:1
    summary: Claims water boils at 50 degrees Celsius at sea level; fasit says 100 degrees Celsius.
  - id: F2
    severity: BLOCKING
    location: r3work/essay2.txt:2
    summary: Claims the Pacific is the smallest ocean; fasit says the Pacific is the LARGEST ocean.
---

The essay makes three factual claims. Judged against the fasit (water boils at 100°C at
sea level; the Pacific is the LARGEST ocean; Everest is the tallest mountain above sea
level), two of the three claims are false and one is correct.

### [BLOCKING] Water boiling point is wrong

**Location:** r3work/essay2.txt:1
**Issue:** The line reads "Water boils at 50 degrees Celsius at sea level." The fasit states
water boils at 100 degrees Celsius at sea level. 50 is factually wrong.
**Fix:** Change 50 to 100.

### [BLOCKING] Pacific ocean size is wrong

**Location:** r3work/essay2.txt:2
**Issue:** The line reads "The Pacific is the smallest ocean on Earth." The fasit states the
Pacific is the LARGEST ocean. "Smallest" is factually wrong (the smallest is the Arctic).
**Fix:** Change "smallest" to "largest".

### Correct claim (no finding)

Line 3 — "Mount Everest is the tallest mountain above sea level." — matches the fasit and
needs no change.
