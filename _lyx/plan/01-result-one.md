# 01 — result-one: create result1.md

## Intent

Create `result1.md` at the repo root containing exactly the single line `OK`.
Stand-alone: after this batch the file exists and is committed.

## Scope

- result1.md

## Cards

### Card 01.1 — create result1.md

**What:** Create `result1.md` at the repo root containing exactly the single
line `OK` (three bytes: O, K, newline). Commit it.
**Context:** none
**Edits:** none
**Creates:**
- `result1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content result1.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'result1.md content mismatch'; exit 1 }"
