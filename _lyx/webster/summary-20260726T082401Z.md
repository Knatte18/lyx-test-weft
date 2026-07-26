# opus-r4 integration-bisect probe

All three cards in the plan were implemented and committed in order:

- **01-igood**: created `ig-a.md` containing `IG-A`, committed as `fb674d8` ("1: igood").
- **02-ibad**: created `ig-bad.md` containing `IG-BAD`, committed as `7de31e1` ("2: ibad").
- **03-itail**: created `ig-c.md` containing `IG-C`, committed as `6cb3af4` ("3: itail").

None of the three implementer forks reported any deviations from their cards' declared file-ops.

After all batches reached `done`, the plan-level `## verify:` command was run once by
the integration fork at HEAD `6cb3af4`:

```
echo candidate >> /tmp/opusr4-bisect-count.log; test ! -f ig-bad.md
```

This failed (non-zero exit) because `ig-bad.md` exists, exactly as the plan intended —
card 02-ibad was designed to break this verify so that webster's in-process SHA-bisect
could localize it as the offending card. The integration fork made no commit and wrote
`status: FAILED` to `_lyx/webster/reports/integration.yaml`.

The run stops here as `stuck`, handing off to webster's automatic SHA-bisect to
localize card 02-ibad as the offender.


## Integration suite failed

The plan-level `## verify:` suite failed. SHA-bisect localized the failure to card `02-ibad` (commit `7de31e18b486be3ec611b66134702c3872284c85`).
