# Card 2 — shout-wiring

**Edit:**
- `services/api#main`

**Uses:**
- `plan:services/api#shout`

**Intent:** Route `main`'s greeting line through the helper card 1 added: print
`shout(ComposeGreeting("lyx"))` where it currently prints `ComposeGreeting("lyx")`.

The farewell line is left exactly as it is, no import is added, and no other file is touched.

**ImpactSummary:** Changes one line of main's own output; no exported surface and no other caller is affected.

**Commit:** `2: shout-wiring`
