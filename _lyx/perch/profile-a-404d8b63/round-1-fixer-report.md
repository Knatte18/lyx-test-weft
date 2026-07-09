# Round 1 Fixer Report

Verdict from review: BLOCKING (3 blocking findings, 1 low finding). All findings were fixed.

## Fixes applied

- **F1 + F2** (both BLOCKING): The green-cheese self-contradiction and the false composition
  claim were the same sentence, fixed with a single edit: deleted "The moon is made of green
  cheese, which is why astronauts brought crackers." from perchwork/essay.txt. This removes both
  the contradiction with "made of rock and dust" and the standalone false factual claim.
  Commit: `f6a071b` — "essay: fix F1,F2 — remove self-contradicting false green-cheese claim"

- **F3** (BLOCKING): Corrected "The moon orbits the earth once every 28 days" to "every 27.3
  days" (the moon's sidereal orbital period), replacing the inaccurate figure.
  Commit: `5d55415` — "essay: fix F3 — correct orbital period from 28 to 27.3 days"

- **F4** (LOW): Reordered and joined the remaining sentences (composition, orbit, Armstrong
  landing) into a single connected paragraph with transitional phrasing, instead of four
  disconnected sentences.
  Commit: `1c4ca48` — "essay: fix F4 — reorder and connect sentences into coherent paragraph"

## Final essay content

```
The Moon Essay

The moon is made of rock and dust, and it orbits the earth once every 27.3
days. In 1969, Neil Armstrong became the first person to walk on its surface.
```

## Deferred

None. All findings recorded in round-1-review.md were fixed this round.
