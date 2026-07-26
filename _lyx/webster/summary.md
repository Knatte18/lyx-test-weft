# opus-r4 post-fix integration probe

Both cards in this plan were implemented and committed:

- **Batch 1 — pgood**: created `pg-a.md` containing `PG-A`, committed as `fd8e878` (`1: pgood`). No deviations reported.
- **Batch 2 — pbad**: created `pg-bad.md` containing `PG-BAD`, committed as `ce2367f` (`2: pbad`). No deviations reported. This card was designed to break the plan-level verify.

After both batches reached `done`, the plan-level `## verify:` step (`test ! -f pg-bad.md`) was run once by an integration fork at HEAD `ce2367f`. It failed, as intended: `pg-bad.md` exists on disk, so `test ! -f pg-bad.md` exits non-zero. No commits were made by the integration fork.

This is the expected outcome for this probe plan — it confirms the normal stuck-flow (Master reports stuck, webster's own SHA-bisect runs afterward to localize the offending card) still works correctly. The run ends with `outcome: stuck`, naming the integration verify failure.


## Integration suite failed

The plan-level `## verify:` suite failed. SHA-bisect localized the failure to card `02-pbad` (commit `ce2367f8fb531118a95851abb0915d66dfff67cc`).
