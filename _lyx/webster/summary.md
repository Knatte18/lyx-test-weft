# Add a shout helper and wire it into main

This run implemented both cards of the plan to add an unexported `shout` helper to
`services/api/main.go` and route the greeting through it.

Batch `01-shout-helper` added the `shout` helper function, committed as `1: shout-helper`
(`15c8eed440fdaca4421dab4d3ef7d7b097eb336a`). No deviations were reported.

Batch `02-shout-wiring` changed `main` to print its greeting through the new `shout` helper,
committed as `2: shout-wiring` (`431c5e427ce3f91d8b04449bc88d8739c8461c8c`). No deviations
were reported.

The plan's integration verify stage ran and reported `status: OK` against head
`431c5e427ce3f91d8b04449bc88d8739c8461c8c`, with no deviations.

All batches completed successfully; the plan is fully done.
