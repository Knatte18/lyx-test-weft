---
verdict: BLOCKING
findings:
  - id: F1
    severity: BLOCKING
    location: r3work/essay5.txt:1
    summary: Line 1 claims "population is exactly 1 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F2
    severity: BLOCKING
    location: r3work/essay5.txt:2
    summary: Line 2 claims "population is exactly 2 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F3
    severity: BLOCKING
    location: r3work/essay5.txt:3
    summary: Line 3 claims "population is exactly 3 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F4
    severity: BLOCKING
    location: r3work/essay5.txt:4
    summary: Line 4 claims "population is exactly 4 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F5
    severity: BLOCKING
    location: r3work/essay5.txt:5
    summary: Line 5 claims "population is exactly 5 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F6
    severity: BLOCKING
    location: r3work/essay5.txt:6
    summary: Line 6 claims "population is exactly 6 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F7
    severity: BLOCKING
    location: r3work/essay5.txt:7
    summary: Line 7 claims "population is exactly 7 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F8
    severity: BLOCKING
    location: r3work/essay5.txt:8
    summary: Line 8 claims "population is exactly 8 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F9
    severity: BLOCKING
    location: r3work/essay5.txt:9
    summary: Line 9 claims "population is exactly 9 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F10
    severity: BLOCKING
    location: r3work/essay5.txt:10
    summary: Line 10 claims "population is exactly 10 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F11
    severity: BLOCKING
    location: r3work/essay5.txt:11
    summary: Line 11 claims "population is exactly 11 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F12
    severity: BLOCKING
    location: r3work/essay5.txt:12
    summary: Line 12 claims "population is exactly 12 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F13
    severity: BLOCKING
    location: r3work/essay5.txt:13
    summary: Line 13 claims "population is exactly 13 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F14
    severity: BLOCKING
    location: r3work/essay5.txt:14
    summary: Line 14 claims "population is exactly 14 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F15
    severity: BLOCKING
    location: r3work/essay5.txt:15
    summary: Line 15 claims "population is exactly 15 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F16
    severity: BLOCKING
    location: r3work/essay5.txt:16
    summary: Line 16 claims "population is exactly 16 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F17
    severity: BLOCKING
    location: r3work/essay5.txt:17
    summary: Line 17 claims "population is exactly 17 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F18
    severity: BLOCKING
    location: r3work/essay5.txt:18
    summary: Line 18 claims "population is exactly 18 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F19
    severity: BLOCKING
    location: r3work/essay5.txt:19
    summary: Line 19 claims "population is exactly 19 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F20
    severity: BLOCKING
    location: r3work/essay5.txt:20
    summary: Line 20 claims "population is exactly 20 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F21
    severity: BLOCKING
    location: r3work/essay5.txt:21
    summary: Line 21 claims "population is exactly 21 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F22
    severity: BLOCKING
    location: r3work/essay5.txt:22
    summary: Line 22 claims "population is exactly 22 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F23
    severity: BLOCKING
    location: r3work/essay5.txt:23
    summary: Line 23 claims "population is exactly 23 million" — unverifiable pseudo-precision; must be softened to "approximately".
  - id: F24
    severity: BLOCKING
    location: r3work/essay5.txt:24
    summary: Line 24 claims "population is exactly 24 million" — unverifiable pseudo-precision; must be softened to "approximately".
---

## Review summary

The target `r3work/essay5.txt` contains 24 content lines (line 25 is a trailing
empty line). I reviewed each line individually against the fasit.

**Period rule:** All 24 content lines end with a period. This rule is satisfied
on every line — no findings on that axis. (The trailing line 25 is empty and
carries no sentence, so the "every line must end with a period" rule does not
apply to it.)

**Pseudo-precision rule:** Every one of the 24 lines contains the phrase
"population is exactly N million". Per the fasit, every "population is exactly N
million" claim is unverifiable pseudo-precision and must be softened to
"approximately". Per the rubric, a line claiming an exact population figure is
BLOCKING. Therefore all 24 lines are BLOCKING findings, one per line, recorded
below.

Verdict: **BLOCKING** — 24 blocking findings.

### [BLOCKING] Line 1 — exact population claim
**Location:** r3work/essay5.txt:1
**Issue:** The line states "its population is exactly 1 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 1 million" to "is approximately 1 million".

### [BLOCKING] Line 2 — exact population claim
**Location:** r3work/essay5.txt:2
**Issue:** The line states "its population is exactly 2 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 2 million" to "is approximately 2 million".

### [BLOCKING] Line 3 — exact population claim
**Location:** r3work/essay5.txt:3
**Issue:** The line states "its population is exactly 3 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 3 million" to "is approximately 3 million".

### [BLOCKING] Line 4 — exact population claim
**Location:** r3work/essay5.txt:4
**Issue:** The line states "its population is exactly 4 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 4 million" to "is approximately 4 million".

### [BLOCKING] Line 5 — exact population claim
**Location:** r3work/essay5.txt:5
**Issue:** The line states "its population is exactly 5 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 5 million" to "is approximately 5 million".

### [BLOCKING] Line 6 — exact population claim
**Location:** r3work/essay5.txt:6
**Issue:** The line states "its population is exactly 6 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 6 million" to "is approximately 6 million".

### [BLOCKING] Line 7 — exact population claim
**Location:** r3work/essay5.txt:7
**Issue:** The line states "its population is exactly 7 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 7 million" to "is approximately 7 million".

### [BLOCKING] Line 8 — exact population claim
**Location:** r3work/essay5.txt:8
**Issue:** The line states "its population is exactly 8 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 8 million" to "is approximately 8 million".

### [BLOCKING] Line 9 — exact population claim
**Location:** r3work/essay5.txt:9
**Issue:** The line states "its population is exactly 9 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 9 million" to "is approximately 9 million".

### [BLOCKING] Line 10 — exact population claim
**Location:** r3work/essay5.txt:10
**Issue:** The line states "its population is exactly 10 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 10 million" to "is approximately 10 million".

### [BLOCKING] Line 11 — exact population claim
**Location:** r3work/essay5.txt:11
**Issue:** The line states "its population is exactly 11 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 11 million" to "is approximately 11 million".

### [BLOCKING] Line 12 — exact population claim
**Location:** r3work/essay5.txt:12
**Issue:** The line states "its population is exactly 12 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 12 million" to "is approximately 12 million".

### [BLOCKING] Line 13 — exact population claim
**Location:** r3work/essay5.txt:13
**Issue:** The line states "its population is exactly 13 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 13 million" to "is approximately 13 million".

### [BLOCKING] Line 14 — exact population claim
**Location:** r3work/essay5.txt:14
**Issue:** The line states "its population is exactly 14 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 14 million" to "is approximately 14 million".

### [BLOCKING] Line 15 — exact population claim
**Location:** r3work/essay5.txt:15
**Issue:** The line states "its population is exactly 15 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 15 million" to "is approximately 15 million".

### [BLOCKING] Line 16 — exact population claim
**Location:** r3work/essay5.txt:16
**Issue:** The line states "its population is exactly 16 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 16 million" to "is approximately 16 million".

### [BLOCKING] Line 17 — exact population claim
**Location:** r3work/essay5.txt:17
**Issue:** The line states "its population is exactly 17 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 17 million" to "is approximately 17 million".

### [BLOCKING] Line 18 — exact population claim
**Location:** r3work/essay5.txt:18
**Issue:** The line states "its population is exactly 18 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 18 million" to "is approximately 18 million".

### [BLOCKING] Line 19 — exact population claim
**Location:** r3work/essay5.txt:19
**Issue:** The line states "its population is exactly 19 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 19 million" to "is approximately 19 million".

### [BLOCKING] Line 20 — exact population claim
**Location:** r3work/essay5.txt:20
**Issue:** The line states "its population is exactly 20 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 20 million" to "is approximately 20 million".

### [BLOCKING] Line 21 — exact population claim
**Location:** r3work/essay5.txt:21
**Issue:** The line states "its population is exactly 21 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 21 million" to "is approximately 21 million".

### [BLOCKING] Line 22 — exact population claim
**Location:** r3work/essay5.txt:22
**Issue:** The line states "its population is exactly 22 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 22 million" to "is approximately 22 million".

### [BLOCKING] Line 23 — exact population claim
**Location:** r3work/essay5.txt:23
**Issue:** The line states "its population is exactly 23 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 23 million" to "is approximately 23 million".

### [BLOCKING] Line 24 — exact population claim
**Location:** r3work/essay5.txt:24
**Issue:** The line states "its population is exactly 24 million." An exact
population figure is unverifiable pseudo-precision.
**Fix:** Soften "is exactly 24 million" to "is approximately 24 million".
