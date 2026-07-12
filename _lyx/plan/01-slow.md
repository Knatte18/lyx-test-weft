# 01 — slow: run the migration wait, then create w1.md

## Intent

Simulate a long-running data migration: run the mandatory 150-second wait
command FIRST (it stands in for the migration and MUST complete before any
file is written), then create `w1.md` containing the single line `OK`.

## Scope

- w1.md

## Cards

### Card 01.1 — migration wait, then create w1.md

**What:** FIRST run exactly this command and wait for it to finish (it
simulates the data migration this batch depends on; do not skip or shorten
it): `pwsh -NoProfile -Command "Start-Sleep -Seconds 150"`. Only AFTER that
command has completed, create `w1.md` at the repo root containing exactly the
single line `OK`, and commit it.
**Context:** none
**Edits:** none
**Creates:**
- `w1.md`
**Deletes:** none
**Moves:** none

## verify:

pwsh -NoProfile -Command "if ((Get-Content w1.md -Raw).Trim() -eq 'OK') { exit 0 } else { Write-Output 'w1.md content mismatch'; exit 1 }"
