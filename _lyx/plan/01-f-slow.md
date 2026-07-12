# 01 — f-slow: migration wait, then create f1.md

## Intent

Simulate a long-running data migration: run the mandatory 150-second wait
command FIRST, then create `f1.md` containing the single line `OK`.

## Cards

### Card 01.1 — migration wait, then create f1.md

**What:** FIRST run exactly this command and wait for it to finish (it
simulates the data migration this batch depends on; do not skip or shorten
it): `pwsh -NoProfile -Command "Start-Sleep -Seconds 150"`. Only AFTER that
command has completed, create `f1.md` at the repo root containing exactly the
single line `OK`, and commit it.
**Context:** none
**Edits:** none
**Creates:**
- `f1.md`
**Deletes:** none
**Moves:** none

## Scope

- f1.md

## verify:

pwsh -NoProfile -Command "if ((Get-Content f1.md -Raw).Trim() -eq 'OK') { exit 0 } else { exit 1 }"
