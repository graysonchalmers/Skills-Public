# Deciding what needs enforcement, not just description

A custom-instructions doc is text the model reads and (usually) follows.
That's enough for most preferences. It is not enough for a rule that gets
violated exactly when it matters — a long session where earlier context
falls out of the window, a model that's "forgotten" a standing instruction
by the fortieth turn, or a rule that was never going to hold through
willpower alone because it needs a mechanical trigger (a specific word
banned outright, a response required to start with a specific marker, a
step that must run before another one).

That second category needs a **hook** — a deterministic script the harness
runs on an event (a new turn starting, a response finishing) rather than a
request the model might or might not honor. This skill does not wire hooks
itself. If the current harness has its own config/hooks skill available
(Claude Code's `update-config` is one example), hand the wiring off there.
Otherwise, describe the hook as a trigger/condition/action triple (see
"Handing off" below) and let the interviewee wire it into whatever their
harness actually uses. This file is just the litmus test for *which* rules
are worth wiring at all.

## The test

Ask, for each candidate rule: **if the model silently ignored this on turn
200 of a long session, would anyone notice before real damage was done?**

- If yes (the mistake is visible and correctable in the next message) —
  plain instruction is fine.
- If no (the mistake compounds, or the whole point was that it's supposed
  to be invisible/automatic) — it's a hook candidate.

A second, faster test: **has the interviewee corrected this more than
twice?** A rule stated once and never violated again was probably just
under-specified the first time — a plain instruction fixed it. A rule
that keeps recurring despite being stated is exactly the failure mode
hooks exist for.

The two tests usually agree. When they don't — a rule with real,
high-severity damage but no repetition history yet, because it's only been
stated once — severity wins: a single bad silent failure (a silent edit to
shared state, a compliance boundary crossed once) can qualify a rule for
enforcement without waiting for it to recur. Low-severity rules still need
the repetition evidence; don't promote a stylistic nit to a hook just
because it happened once.

## What tends to be hook-worthy

- A hard format requirement on every response (a required prefix, a
  banned character, a required closing structure) — checkable mechanically
  against the literal output text.
- A rule about *when* something happens ("always do X before Y," "never
  skip the confirmation step") where skipping it is easy to miss in the
  moment and expensive to catch after.
- Anything that's really a compliance/safety boundary rather than a style
  preference — those shouldn't depend on the model remembering to care.

## What tends to stay soft

- Anything that requires judgment to apply correctly (tone calibration,
  how much detail is "too much" for this specific question) — a hook can't
  make that call, only a model reading the actual content can.
- Preferences that are fine to get wrong occasionally and self-correct
  (format nits, phrasing choices) — the cost of an occasional miss is low
  enough that a hook is more engineering than the rule is worth.
- Anything still being calibrated. Don't hard-enforce a rule that hasn't
  been lived with yet — get a few sessions of plain-text use first, then
  promote it once it's proven durable and precisely stated. A hook that
  encodes the wrong version of a rule is harder to notice and fix than a
  soft instruction that's slightly off.

## Handing off

Once the enforcement candidates are identified, describe each one
concretely: the trigger event (new turn / response finishing / specific
command), the exact condition to check, and what should happen when it
fires (block, rewrite, inject a reminder, log). If a config/hooks skill is
available in this harness, hand that triple to it. If not, hand the triple
to the interviewee — it's enough for them or a developer to implement in
whatever hook/plugin/middleware system their tool supports. Keep this
skill's job at identifying *which* rules qualify — the mechanics of any one
platform's hook system belong elsewhere.
