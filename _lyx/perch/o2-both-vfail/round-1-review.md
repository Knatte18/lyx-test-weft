---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: o2-gate.txt:1
    summary: "standing-rule: the document does not meet the standing rule"
---

### [BLOCKING] Standing rule violation

**Location:** C:\Code\lyx-test-HUB\lyx-test\o2-gate.txt:1

**Issue:** The target is judged against a fasit consisting of a standing rule that can never
be satisfied. Regardless of the actual content of `o2-gate.txt` (currently a single sentence,
"This sentence is correct and needs no change.", followed by a blank line), no state of this
document can ever meet that standing rule. This is a permanent, structural non-compliance, not
a defect in the document's wording or content.

**Fix:** None possible. There is no edit to `o2-gate.txt` that can bring it into compliance
with a rule constructed to be permanently unsatisfiable. This finding is therefore recorded
every round and never marked fixed, per the rubric.
