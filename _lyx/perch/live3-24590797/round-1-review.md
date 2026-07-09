---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r3work/essay3.txt:1
    summary: Essay claims the Sun rises in the west, contradicting the fasit (the Sun rises in the east).
---

### [BLOCKING] Essay states the Sun rises in the west

**Location:** r3work/essay3.txt:1

**Issue:** The essay's only sentence reads "The Sun rises in the west every morning." The fasit is explicit that the Sun rises in the east. This is a direct factual contradiction of the source of truth, and the rubric marks any claim that contradicts the fasit as BLOCKING.

**Fix:** Replace "west" with "east" so the sentence reads "The Sun rises in the east every morning."
