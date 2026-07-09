# Round 1 fixer report

All 4 findings from `round-1-review.md` were fixed, each as its own commit on the host working
tree.

## Fixes applied

- **F1** (BLOCKING, perchwork/essay.txt:3) — Capitalized "earth" to "Earth" as the proper noun.
  Commit `c5a0ad4`: `essay: fix F1 — capitalize earth as the proper noun Earth`.
- **F2** (BLOCKING, perchwork/essay.txt:3-4) — Capitalized "moon" to "Moon" in both body
  sentences to match the capitalized "Moon" in the title.
  Commit `61e4c1d`: `essay: fix F2 — capitalize moon consistently to match title's Moon`.
- **F3** (BLOCKING, perchwork/essay.txt:3-4) — Rewrote the opening of the second paragraph to
  add a transitional clause ("Long after these basic facts were understood, the Moon still
  captured human imagination — and...") linking the composition/orbit facts to the 1969 landing,
  instead of dropping the Armstrong fact in with no connective tissue.
  Commit `c037af8`: `essay: fix F3 — add transitional phrasing linking orbit facts to the 1969 landing`.
- **F4** (BLOCKING, perchwork/essay.txt:1) — Added an introductory sentence ("Humanity has gazed
  up at the Moon since long before recorded history, wondering what secrets it might hold.") and
  a closing sentence ("Today, this once-mysterious rock remains the only other world humans have
  ever set foot on.") so the piece has a beginning and an end befitting its "Essay" title, rather
  than reading as three isolated facts.
  Commit `0386b6e`: `essay: fix F4 — add intro and closing sentences so the piece reads as a developed essay`.

Final text of `perchwork/essay.txt`:

```
The Moon Essay

Humanity has gazed up at the Moon since long before recorded history, wondering what secrets it might hold. The Moon is made of rock and dust. It orbits the Earth once every 27.3 days.
Long after these basic facts were understood, the Moon still captured human imagination — and in 1969, Neil Armstrong became the first person to walk on its surface. Today, this once-mysterious rock remains the only other world humans have ever set foot on.
```

## Deferred

None. All findings were fixable within this round and were fixed.
