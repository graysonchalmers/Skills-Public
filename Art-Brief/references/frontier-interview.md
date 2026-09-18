# Adaptive frontier interview

This reference defines the normal multi-turn interview contract for Art-Brief.
It adapts the decision-tree frontier pattern without importing relentless tone or
unlimited questioning.

## Frontier domain — creative decisions only (v2.8)

Art-Brief's frontier contains **creative decisions**: interpretation class,
asset intent, visual language, reference roles and conflicts, stylization
floors, mood, technical-art spec, and creative priority weights. It never
contains delivery-authority decisions — reviewer/approver names, review
channels or turnaround, contacts, milestones, payment, scope/change policy.
Those belong to outsource-intake (`brief_ref` contract in SKILL.md). If the
user volunteers such facts, register them with provenance and pass them
through; do not spend frontier questions on them.

## Round contract

1. **Register first.** Extract every supplied fact, exact qualifier, source span,
   status (`Confirmed`, `Observed`, `Proposed`, `Unresolved`), action state, hedge,
   scope and role limit into the visible source/decision register before asking.
2. **Compute the frontier.** A frontier item is a consequential decision whose
   prerequisites are settled. Do not ask for facts already captured, and do not ask
   downstream questions while their prerequisites are open.
3. **Ask 2–4.** Number only the current frontier questions. Explain the decision
   impact and give a recommendation where useful. Questions are not permission to
   invent a value or promote a proposal.
4. **Recompute.** After each answer, append the answer source and register evolution,
   preserving stable IDs and recording changed values/acceptance spans. Recompute the
   next frontier; do not blindly repeat a questionnaire.
5. **Stop or stay quiet.** Stop at the checkpoint/assemble step when remaining gaps
   are non-blocking for the requested artifact, or when the user explicitly asks for
   a draft with gaps. If no consequential question remains, be quiet and assemble
   when the route permits. Keep all remaining gaps visible.

## Modes and output

- Normal mode is multi-turn and may pause at the checkpoint. A draft with gaps is
  allowed only with explicit draft permission or after the frontier is non-blocking.
- Explicit debug mode is immediate, asks no questions, bypasses confirmation waits,
  and labels every independent output **DEBUG PREVIEW—NOT FOR SENDING**. Synthetic
  values remain Proposed — illustrative only.
- Art-Brief always preserves all three blocks: Art Direction Document, Vendor Brief,
  and Generation Prompts (or Materials & Process Note for physical work). One shared
  source key/register appendix serves all blocks.

## Interview trace minimum

Retain a compact trace alongside the artifact or in the harness evidence:

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

The trace is evidence of behavior, not a substitute for source-to-atom-to-clause
comparison. The final blocks must render from the latest register.
