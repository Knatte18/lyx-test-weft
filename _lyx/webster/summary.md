# fable-r3 integration bisect probe

All three cards in this plan were implemented and committed successfully:

- **01-good-one**: created `r3g1.md` (content `G1`). Done in a prior session.
- **02-bad-plant**: created `r3bad.md` (content `BAD`), committed as `15504a9baeed21ca1184c79966f270a9afc01c11`. No deviations reported.
- **03-good-two**: created `r3g3.md` (content `G3`), committed as `412df107995c595fafd26be09ab36abc79ae56cf`. No deviations reported.

With all batches done, the plan-level integration verify was run once at HEAD
`412df10`:

```
echo run >> /home/knatte/Code/lyx-test-HUB/bisect-count.log; test ! -f r3bad.md
```

It **FAILED**: `r3bad.md` exists (planted by card 02-bad-plant), which the
verify command explicitly forbids. No commits were made by the integration
check itself.

This is the expected outcome for this probe plan — card 02 deliberately plants
a file the plan-level verify rejects, so the integration suite fails and the
offending card should localize to 02-bad-plant via SHA-bisect once this
session ends.


## Integration suite failed

The plan-level `## verify:` suite failed. SHA-bisect localized the failure to card `02-bad-plant` (commit `15504a9baeed21ca1184c79966f270a9afc01c11`).
