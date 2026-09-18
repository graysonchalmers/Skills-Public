# Adaptive frontier interview

This reference defines the normal multi-turn interview contract for Outsource-
Intake. It adapts decision-tree frontier rounds without relentless tone or
unlimited questioning.

## Round contract

1. **Register first.** Extract supplied facts and exact source spans into the visible
   source/decision register, preserving status, hedge, action state, scope and role.
2. **Compute the frontier.** A frontier decision is consequential and has all
   prerequisites settled. Never ask a captured fact or a downstream question whose
   prerequisite is still open.
3. **Ask 2–4.** Number the current frontier questions and include impact plus a
   recommendation where useful. Ask only what can change the requested route, sheet,
   readiness finding or next gate.
4. **Recompute.** After every answer, append its source/span and register evolution;
   preserve stable IDs and explicit acceptance sources. Recompute rather than replay
   the ladder.
5. **Stop or stay quiet.** Stop at recap/assemble when remaining gaps are
   non-blocking, or when the user explicitly asks for a draft with gaps. Keep gaps
   visible and proposals Proposed.

## Modes and route limits

- Normal mode is multi-turn. A draft with gaps is allowed only after the frontier is
  non-blocking or with explicit draft permission.
- Explicit debug mode is immediate, asks no questions, bypasses confirmation waits,
  and labels every independent output **DEBUG PREVIEW—NOT FOR SENDING**. Synthetic
  values remain Proposed — illustrative only.
- Mini is a separate route, not a compressed full sheet: its core is **at most 250
  words** and the complete intake asks **at most five total questions**, including
  questions in recaps and replies. Do not hide questions or operational prose in
  appendices. Full routes retain the source/contact appendices and their own fields.
- One shared source key/register appendix serves recap, sheet and replies.

## Interview trace minimum

Retain a compact trace alongside the artifact or in harness evidence:

```text
round: integer
frontier_before: [decision IDs/titles]
questions: [{number, decision, prerequisite, recommendation}]
answer_source: source key/span or "none"
answer_effects: [new/updated decision IDs and status changes]
register_snapshot: visible IDs/statuses after the round
frontier_after: [decision IDs/titles]
stop_reason: string or null
```

The trace supports inspection but cannot replace source-to-atom-to-clause comparison.
The final sheet must render from the latest register.
