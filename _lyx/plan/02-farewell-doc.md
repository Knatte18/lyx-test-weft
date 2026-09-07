# Card 2 — farewell-doc

**Edit:**
- `services/api#ComposeFarewell`

**Uses:**
- `services/api#orDefault`

**Intent:** `ComposeFarewell`'s godoc line states what it returns but not that its empty-name
default is shared with `ComposeGreeting`. Extend the existing godoc comment with one further
sentence naming the shared unexported helper it delegates that default to.

Comment text only — the function body, signature and behaviour stay byte-identical, and no
other file is touched.

**ImpactSummary:** Adds one godoc sentence to one exported function; no code and no behaviour changes.

**Commit:** `2: farewell-doc`
