---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: C:\Code\lyx-test-HUB\lyx-test\o2-gate.txt:1
    summary: "standing-rule: the document does not meet the standing rule"
---

### [BLOCKING] Standing rule violation

**Location:** C:\Code\lyx-test-HUB\lyx-test\o2-gate.txt:1

**Issue:** The artifact is judged against a standing rule that can never be satisfied. Regardless
of the actual content of the target file (currently a single line: "This sentence is correct and
needs no change."), the standing rule is not met and cannot be met by any content.

**Fix:** None possible. This finding can never be marked fixed, by construction of the standing
rule itself. No edit to the target file's content can resolve it.
