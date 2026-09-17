# Debug previews and contact directory

## Explicit debug only

Enable only for the current explicitly requested debug/headless-preview artifact,
not because information is missing or a runner is headless. A normal "draft with
gaps" is not debug. Debug overrides the skill's question, STOP, recap-confirmation,
and template-confirmation waits solely to produce a non-sendable artifact. It
never simulates user approval. Show a non-interactive checkpoint if useful, then
continue to the full requested output without requesting real details.

Default to quiet tokens such as `[CLIENT_PRODUCER_NAME]`,
`[CLIENT_PRODUCER_EMAIL]`, `[DELIVERY_PATH]`, `[TECHNICAL_BUDGET]`, or `[DECISION_DATE]`.
Use **Unresolved — placeholder; source: debug scaffolding, not supplied**. Keep
actual supplied facts and their hedges/source intact; do not replace them with
fabricated facts. Proposed creative ideas can remain Proposed, not Confirmed.

Only an explicit **debug examples** request permits filled illustrative values.
Use obvious examples, never plausible invented people or organizations:
- Name: `Example Client Producer` (analogous names for the other roles).
- Email: `client-producer@example.invalid` (only the `example.invalid` domain).
- Slack/Teams: `@example-client-producer`, plain text; no real workspace, profile,
  invite, channel URL, or platform mention markup that could notify someone.
- Phone: `+1 202-555-0101`; any other examples must remain in the reserved
  `+1 202-555-0100` through `+1 202-555-0199` range.
- Timezone: `Example timezone: UTC`; never imply real overlap or availability.
Label filled examples **Proposed — illustrative example only; source: debug
scaffolding**, never Confirmed. Examples of approval, delivery, or agreements
cannot become evidence. Prefer placeholders even in examples mode unless filling
that field helps the requested test.

Prefix every preview, independently copyable output block, and excerpt (including
recipient messages, tables shown alone, prompts, and change-log excerpts) with
**DEBUG PREVIEW—NOT FOR SENDING**. Keep document status **Debug draft**, not
Approved or sendable. Do not label any readiness row Ready on placeholder/example
evidence; show Gaps, or Not applicable with an actual scope-specific rationale.
Never imply that generating a debug artifact completed production work.

No contact/vendor/reference lookup, outreach, message sending, or external tracker
writes in debug, even if a connector is available. Supplied accessible local files
may be inspected and attributed honestly; do not fetch missing remote material.
Return the artifact in chat or an explicitly requested local file only. Requests
to send/track it need a separate normal-mode request and normal approval checks,
replacement of synthetic fields, and fresh readiness assessment. Debug is not
sticky: do not carry its gate override or synthetic values into the next request.

## Contact directory — normal and debug outputs

Read this section when building any brief/request sheet. Capture both sides:
**client/internal** and **partner**, with three roles on each side: **producer**,
**outsource manager**, and **art lead**. Reuse provided data; do not stop intake for
vendor names or missing contacts. Unknowns get tokens with Unresolved status and
source "not supplied." Role purpose below is a description, not an assigned task.
Capture the project's stated purpose if different, with its source.

Use this schema (one row per role; split field status inline if it differs):

| Side / role | Name | Email | Slack or Teams | Phone | Timezone | Role purpose | Status / source |
|---|---|---|---|---|---|---|---|
| Client/internal producer | [CLIENT_PRODUCER_NAME] | [CLIENT_PRODUCER_EMAIL] | [CLIENT_PRODUCER_CHAT] | [CLIENT_PRODUCER_PHONE] | [CLIENT_PRODUCER_TIMEZONE] | Production coordination | Unresolved — not supplied |
| Client/internal outsource manager | [CLIENT_OUTSOURCE_MANAGER_NAME] | [CLIENT_OUTSOURCE_MANAGER_EMAIL] | [CLIENT_OUTSOURCE_MANAGER_CHAT] | [CLIENT_OUTSOURCE_MANAGER_PHONE] | [CLIENT_OUTSOURCE_MANAGER_TIMEZONE] | Outsource scope and delivery coordination | Unresolved — not supplied |
| Client/internal art lead | [CLIENT_ART_LEAD_NAME] | [CLIENT_ART_LEAD_EMAIL] | [CLIENT_ART_LEAD_CHAT] | [CLIENT_ART_LEAD_PHONE] | [CLIENT_ART_LEAD_TIMEZONE] | Art-direction questions and feedback | Unresolved — not supplied |
| Partner producer | [PARTNER_PRODUCER_NAME] | [PARTNER_PRODUCER_EMAIL] | [PARTNER_PRODUCER_CHAT] | [PARTNER_PRODUCER_PHONE] | [PARTNER_PRODUCER_TIMEZONE] | Partner production coordination | Unresolved — not supplied |
| Partner outsource manager | [PARTNER_OUTSOURCE_MANAGER_NAME] | [PARTNER_OUTSOURCE_MANAGER_EMAIL] | [PARTNER_OUTSOURCE_MANAGER_CHAT] | [PARTNER_OUTSOURCE_MANAGER_PHONE] | [PARTNER_OUTSOURCE_MANAGER_TIMEZONE] | Partner intake and delivery coordination | Unresolved — not supplied |
| Partner art lead | [PARTNER_ART_LEAD_NAME] | [PARTNER_ART_LEAD_EMAIL] | [PARTNER_ART_LEAD_CHAT] | [PARTNER_ART_LEAD_PHONE] | [PARTNER_ART_LEAD_TIMEZONE] | Partner art-direction questions and feedback | Unresolved — not supplied |

In debug, replace "not supplied" with the explicit debug-scaffolding source above.
For **internal-only work**, retain all three partner rows as **Not applicable —
internal-only; source: [request]** and use N/A for their contact fields. This does
not waive internal review or rights decisions. Unknown recipient scope is not N/A.
One person may occupy multiple roles if evidenced; do not invent extra people.

A directory is **not assignment, availability, escalation policy, or sign-off
authority**. Keep style authority, approval owner, actual task ownership, and any
accepted process separately evidenced. An art lead listed here is not automatically
the final approver. A listed available lead is not automatically assigned.

For a mini-sheet, keep the operational core roughly one screen and append the
**full six-role directory as a compact appendix**, not six new intake questions.
Combine contact methods within a cell or use short multiline rows if needed, but
retain all five contact fields, purpose, and status/source. The same appendix can
serve condensed/full blocks in a single package; any standalone recipient brief
must include or attach it, not silently drop it. Generation prompts need no contacts.

## Verification cases (retain actual outputs, not self-grades)

- Explicit sparse headless debug: full requested artifact, no requests for real
  info or pause at a confirmation gate; labels on every independently shown block.
- Debug examples versus default: default uses tokens; explicit examples use only
  obvious example names, example.invalid, plain chat handles, and reserved phones.
  Neither can establish Confirmed facts, approval, completion, or Ready.
- Next normal request after debug: normal gate returns, no synthetic data leaks.
  No lookup, outreach, or tracker writes occurred during the debug request.
- Unknown contacts: six rows with five contact fields, purpose, status/source;
  internal-only mini-sheet keeps the full directory outside the short core with
  partner N/A rows. No vendor-name interrogation, invented approver, or assignment.
- A supplied budget without reason, "I'd have to check", and "probably available":
  rationale stays Unresolved, checking is needed rather than underway, and probably
  survives every repeat. Availability alone does not assign a person to the work.
- Scope addition: document inclusion plus an unknown agreement yields Unresolved
  commercial treatment, including change-log and recipient-reply wording. A reply
  can ask a question or make a labeled proposal without promising action.

These are behavioral scenarios to exercise separately. Structural validators
check document shape and instruction presence only; they cannot prove execution.

