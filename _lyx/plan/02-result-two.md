# 02 — result-two: create result2.md

## Intent

Create `result2.md` at the repo root containing exactly the single line `OK`.
Stand-alone: assumes batch 01 is committed.

## Scope

- result2.md

## Cards

### Card 02.1 — create result2.md

**What:** Create `result2.md` at the repo root containing exactly the single
line `OK` (three bytes: O, K, newline). Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `result2.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content result2.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'result2.md content mismatch'; exit 1 }"
