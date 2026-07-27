---
covers_rounds: [1, 2]
ledger:
  - key: r1-trailing-period-line1
    rounds: [1]
    status: resolved
  - key: r2-uppercase-start-line2
    rounds: [2]
    status: open
---

Round 1 flagged a missing trailing period on line 1 of `lyx-test/o2-hand.txt` (rule R1-trailing-period); this was fixed and round 2 confirmed it satisfied. Round 2 then flagged a new, distinct issue: line 2 starts lowercase, violating rule R2-uppercase-start. No recurrence or oscillation observed yet — each round has surfaced a new, previously-unflagged rule violation on the next line/rule in sequence. Watch future rounds for whether R1 or R2 resurface (which would indicate circling) versus continued progress to new rules/lines.
