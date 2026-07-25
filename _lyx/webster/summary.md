# fable-r3 crash-window probe

The plan's single card, batch 1 ("phoenix"), had already completed and left a
report behind from a prior session (the crash-window this plan was designed to
probe). On resume, `begin-batch 1` correctly refused since a report already
existed; `record-batch 1` consumed it, reporting `status: done` at head SHA
`5515f0a5be9c7c478d966e64901ea12e24a5acc1` (creating `r3c.md` with the line
`RISEN`). A warning noted the original implementer fork's transcript never
wrote a final in-session report — expected, since the fork was killed mid-run
as part of the crash-window test; the digest report on disk was authoritative.

No plan-level `## verify:` section was present, so no integration stage ran.
The plan is complete: 1/1 batches done.
