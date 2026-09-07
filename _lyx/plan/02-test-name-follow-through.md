# Card 2 — Rename the test function to TestComposeGreeting

**Rename:**
- `services/api#TestFormatGreeting` -> `plan:services/api#TestComposeGreeting`

**Intent:** Retire the last occurrence of the old name. Go's convention pairs
`TestXxx` with the `Xxx` under test, and after card 1 the test function still
points at a symbol that no longer exists.

This is the function name on its own declaration line and nothing else. Card 1
already retargeted the call under test and the failure-message format string
inside the body, so the table of three cases — a named greeting, the empty-name
default to `"world"`, and a multi-word name — stays untouched: no new cases, no
altered expectations. Rename it in place with the editing tools; the body is not
rewritten.

After this card `grep -rn FormatGreeting services/api` returns nothing, in code,
comments, test names, and string literals alike.

**Commit:** 2: rename TestFormatGreeting to TestComposeGreeting
