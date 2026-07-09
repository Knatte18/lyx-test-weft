# Round 1b — Fixer Report

Target: `r3work/essay5.txt`
Verdict from review: **BLOCKING** (24 findings)

## What I changed

All 24 findings (F1–F24) are fixed. Each finding flagged a line claiming
"population is exactly N million" — unverifiable pseudo-precision. For every one
of the 24 lines I softened "is exactly N million" to "is approximately N
million", per the fasit.

| Finding | Line | Before | After |
| --- | --- | --- | --- |
| F1  | 1  | its population is exactly 1 million.  | its population is approximately 1 million.  |
| F2  | 2  | its population is exactly 2 million.  | its population is approximately 2 million.  |
| F3  | 3  | its population is exactly 3 million.  | its population is approximately 3 million.  |
| F4  | 4  | its population is exactly 4 million.  | its population is approximately 4 million.  |
| F5  | 5  | its population is exactly 5 million.  | its population is approximately 5 million.  |
| F6  | 6  | its population is exactly 6 million.  | its population is approximately 6 million.  |
| F7  | 7  | its population is exactly 7 million.  | its population is approximately 7 million.  |
| F8  | 8  | its population is exactly 8 million.  | its population is approximately 8 million.  |
| F9  | 9  | its population is exactly 9 million.  | its population is approximately 9 million.  |
| F10 | 10 | its population is exactly 10 million. | its population is approximately 10 million. |
| F11 | 11 | its population is exactly 11 million. | its population is approximately 11 million. |
| F12 | 12 | its population is exactly 12 million. | its population is approximately 12 million. |
| F13 | 13 | its population is exactly 13 million. | its population is approximately 13 million. |
| F14 | 14 | its population is exactly 14 million. | its population is approximately 14 million. |
| F15 | 15 | its population is exactly 15 million. | its population is approximately 15 million. |
| F16 | 16 | its population is exactly 16 million. | its population is approximately 16 million. |
| F17 | 17 | its population is exactly 17 million. | its population is approximately 17 million. |
| F18 | 18 | its population is exactly 18 million. | its population is approximately 18 million. |
| F19 | 19 | its population is exactly 19 million. | its population is approximately 19 million. |
| F20 | 20 | its population is exactly 20 million. | its population is approximately 20 million. |
| F21 | 21 | its population is exactly 21 million. | its population is approximately 21 million. |
| F22 | 22 | its population is exactly 22 million. | its population is approximately 22 million. |
| F23 | 23 | its population is exactly 23 million. | its population is approximately 23 million. |
| F24 | 24 | its population is exactly 24 million. | its population is approximately 24 million. |

## Verification

- Re-read the full file after editing: all 24 lines now read "population is
  approximately N million" with correct spacing (an intermediate edit briefly
  dropped the space after "approximately"; I rewrote the file to restore it and
  confirmed the final content).
- Period rule: every one of the 24 content lines still ends with a period — no
  regressions introduced.
- No occurrences of "exactly" remain in the file.

## Deferred (with reason)

None. All 24 findings were fixed this round.
