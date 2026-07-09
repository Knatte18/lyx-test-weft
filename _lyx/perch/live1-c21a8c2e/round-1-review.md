---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r3work/essay.txt:2
    summary: Claims the Moon is larger than the Earth, contradicting the fasit (Moon is much smaller).
  - id: F2
    severity: MEDIUM
    location: r3work/essay.txt:3
    summary: Misspelling "primarly" should be "primarily".
  - id: F3
    severity: BLOCKING
    location: r3work/essay.txt:4
    summary: Claims the Moon is larger than Earth and its gravity is stronger, contradicting the fasit on both size and gravity.
---

### [BLOCKING] Moon described as larger than the Earth

**Location:** r3work/essay.txt:2
**Issue:** Line 2 states "The Moon is larger than the Earth, which is why it dominates our night sky." The fasit is explicit: the Moon is much SMALLER than the Earth. This is a direct factual contradiction, and the causal reasoning ("which is why it dominates our night sky") is built on the false premise — the Moon dominates the night sky because of its proximity, not its size.
**Fix:** Rewrite to state the Moon is much smaller than the Earth, and drop or correct the false causal claim.

### [MEDIUM] Misspelling "primarly"

**Location:** r3work/essay.txt:3
**Issue:** Line 3 reads "Tides on Earth are caused primarly by the Moon's gravity." The word "primarly" is misspelled.
**Fix:** Replace "primarly" with "primarily".

### [BLOCKING] Moon described as larger with stronger gravity

**Location:** r3work/essay.txt:4
**Issue:** Line 4 states "The Moon is larger than the Earth, so its gravity is stronger than Earth's." Both claims contradict the fasit: the Moon is much smaller than the Earth, and its surface gravity is weaker than Earth's (about one-sixth). The sentence is doubly wrong — the false size premise and the false gravity conclusion.
**Fix:** Rewrite to state the Moon is smaller than the Earth and its surface gravity is weaker than Earth's.
