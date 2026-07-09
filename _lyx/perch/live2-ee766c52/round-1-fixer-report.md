# Round 1 Fixer Report

Verdict under fix: BLOCKING — 2 findings, both fixed.

## Changes made

- **F1 (BLOCKING, r3work/essay2.txt:1):** Changed "Water boils at 50 degrees Celsius at sea
  level." to "Water boils at 100 degrees Celsius at sea level." — now matches the fasit.
- **F2 (BLOCKING, r3work/essay2.txt:2):** Changed "The Pacific is the smallest ocean on
  Earth." to "The Pacific is the largest ocean on Earth." — now matches the fasit.

Line 3 (Everest is the tallest mountain above sea level) was already correct and was left
unchanged.

Both edits applied in a single edit to `r3work/essay2.txt`. The file now reads:

```
Water boils at 100 degrees Celsius at sea level.
The Pacific is the largest ocean on Earth.
Mount Everest is the tallest mountain above sea level.
```

## Deferred (with reason)

None. Every recorded finding was fixed this round.
