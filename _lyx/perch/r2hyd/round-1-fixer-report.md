---
round: 1
target: r2-hyd.txt
findings_fixed: [F1, F2]
findings_deferred: []
---

## Fixed

- **F1** (BLOCKING): Corrected both misspellings of "captial" to "capital" on line 1.
- **F2** (BLOCKING): Corrected the stated capital of Norway from "Bergen" to "Oslo" on line 1.

Both fixes were applied in a single edit to line 1, changing:
`The captial of France is Paris. The captial of Norway is Bergen.`
to:
`The capital of France is Paris. The capital of Norway is Oslo.`

## Deferred

None. All findings from the review were fixed.
