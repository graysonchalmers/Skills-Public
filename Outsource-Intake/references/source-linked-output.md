# Source-linked output contract

Load before the first checkpoint/recap/quick read, and again before assembly or
any recipient reply. Applies to headings, tables, prompts and change logs too.
Use ordinary Markdown; no Python, validator, or workflow engine is required.

## 1. Capture once, then render

Build a small **visible source/decision register**, not an invisible reasoning
step. Give sources S1, S2… and decision atoms D1, D2…; IDs identify records, not
approval levels. Keep stable IDs within the package and across an iteration;
record changed values/acceptance sources rather than silently recycling an ID.

A source key identifies speaker/document and location (message, section, line
range, file/version or link as available). Preserve the **exact relevant source
span**, including qualifiers and context that limits it. Quote only text actually
supplied/inspected; never invent a quotation to justify an inference. Several
atoms may use different exact spans from the same source. A secondhand report
remains a report by that source, not direct evidence from the reported speaker.
For inspected images, use reference ID + file/region and an Observed description;
there is no textual quote to fabricate. Uninspected images cannot be Observed.

| ID | Value / decision status | Source span | Hedge / action state | Scope / role limit |
|---|---|---|---|---|
| Dn | [value; Confirmed / Observed / Proposed / Unresolved] | [Sn + exact quote, or located image observation] | [literal hedge; needed / planned / underway / done / not stated / N/A] | [dimension, phase, role, agreement or evidence limit] |

For **Unresolved**, use `not supplied in S1–S3` (the inputs actually reviewed),
or quote the explicit undecided/conflicting statement. That marker proves only
an information gap; it does not prove absence. For assistant-authored **Proposed**
choices, say `assistant proposal; based on Dn` (or `no source; creative option`)
instead of fabricating a source span. Record proposal acceptance with its exact
acceptance span and applicable scope. General permission to draft is not acceptance.

Split atoms whenever status, hedge, scope or role differs: a confirmed visual
goal versus a proposed method; a number versus its unstated reason; an option
request versus approval of that option; reviewer versus sign-off authority;
file drop versus notes channel. Group genuinely shared unknowns, not unlike facts.
Capture only substantive decisions used in the output and consequential gaps;
no row per filler word, contact token or repeated occurrence.

## 2. Preserve what the source actually establishes

- **Hedges:** retain probably, maybe, roughly, optional, target and conditional
  clauses in the value and every rendering. Confirmed means the statement was
  supplied, not that its tentative value became settled.
- **Action:** needed is a gap; planned requires a stated intention; underway
  requires evidence of starting; done requires evidence of completion. “I'd
  have to check” is needed, not “checking” or “we'll confirm.” Availability is
  not assignment. A drafted pricing question is neither sent nor quoted.
- **Roles:** name only the evidenced role. Reviewer does not imply approver,
  requester does not imply producer, and approval owner does not imply art lead.
  Authority over proportions does not ban rendering styles or require a new
  sign-off. One reviewer does not prove that escalation is unnecessary.
- **Scope:** missing references/estimate/process evidence is not nonexistence;
  omitted work is not excluded work. Unknown commercial treatment stays unknown,
  even if a scope item appears in a draft. Requested dates are not agreed dates.
- **Priority/gates:** a requirement's acceptance does not accept its priority.
  Record useful weights and review suggestions as separate Proposed atoms;
  a template is not a production instruction. No mandatory filling of blanks.

## 3. Compact rendering and creative support

Render condensed clauses **from atoms**, not from a fresh freehand summary of
another output block. Use `value [D1 Confirmed]`, `Proposed: value [D2]`, or
`Unresolved: value [D3]`; the source key/register supplies the source once.
A shared label may cover adjacent clauses only with truly identical status and
limits. Split mixed claims. Keep hedges and scope in the clause itself, not
only in a footnote. Unknowns render as open items/questions, never commitments.

Keep creativity useful: register Proposed palette roles, materials, lighting,
composition, references or process options with a concrete reason. Render them
in an explicitly Proposed options section; do not launder them through priority
bullets, prompt negatives or a “current bar” heading. A requested/delegated
exploration may have a Proposed prompt alongside the production direction.
Annotated prompt clauses retain IDs/status; do not offer an untraced clean copy
that drops those distinctions. A fully Proposed prompt may use one Proposed
header with its clause IDs; mixed-status prompts keep inline labels.

Attach **one compact register + source key appendix per package**, shared by
all blocks. A standalone excerpt carries only the referenced rows/source key,
plus required contacts for a standalone recipient brief/sheet. Reuse the complete
six-role contact appendix; generic role purposes describe roles, not assignments.
Unknown contact fields can share a row-level Unresolved/source marker. The
mini-sheet's 250-word core excludes only these source/contact appendices; no
full Stage ceremony or operational prose hidden outside that core.

## 4. Compare before returning — IDs are not proof

For each substantive rendered clause, open its source span and compare
**source → atom → clause**. Check subject, role, value/unit, negation, tense,
hedge, action state, dimension/scope and approval/commercial meaning. A copied
ID with an invented claim fails this comparison. Inspect headings, summaries,
prompt negatives and table cells, not just paragraphs; check repeated atoms for
contradictions. If a claim exceeds its source, repair the atom and all repeats,
or split off a Proposed choice. If the source cannot be inspected, retain the
access limitation and do not claim verification. Checks of IDs, links or document
shape alone cannot establish semantic fidelity or behavioral acceptance.

## 5. Debug and synthetic fixtures

Debug status is request-scoped per `debug-and-contacts.md`. A source key pointing
to a synthetic fixture does not make it real input: its filled illustrative
values remain **Proposed — illustrative only**, even when a fixture says
“approved.” Unknown fields remain Unresolved. Synthetic approval, agreement or
completion cannot support Confirmed, Approved, Ready, or authorization. Keep
**DEBUG PREVIEW—NOT FOR SENDING** on independently copyable blocks/excerpts.
Use Example-prefixed names and only `example.invalid` for illustrative addresses.
Actual non-synthetic inputs retain their true status; do not turn a normal request
into debug merely because information is sparse or execution is headless.

## Compact worked example — mini-sheet

**DEBUG PREVIEW—NOT FOR SENDING**

Source key: **S1** = Example Requester's synthetic internal message, sentences
1–4: “Please model one simple crate for our internal team by Friday. Example
Artist can do it. Probably 500-ish triangles; I'd have to check. Example
Reviewer will review it.” No calendar date is inferred from “Friday.”

### Shared register appendix

| ID | Value / decision status | Source span | Hedge / action state | Scope / role limit |
|---|---|---|---|---|
| D1 | One simple crate, internal team, Friday requested; Proposed — illustrative only | S1: “Please model one simple crate for our internal team by Friday.” | requested; N/A | not an agreed delivery date |
| D2 | Example Artist can do it; Proposed — illustrative only | S1: “Example Artist can do it.” | can; assignment not stated | ability/availability, not a booked task |
| D3 | Probably 500-ish triangles; Proposed — illustrative only | S1: “Probably 500-ish triangles; I'd have to check.” | probably, -ish; check needed | not a confirmed limit or check underway |
| D4 | Example Reviewer to review; Proposed — illustrative only | S1: “Example Reviewer will review it.” | will; planned within fixture only | review, not acceptance authority |
| D5 | Match neighboring props; Proposed | assistant creative option; based on D1 | suggestion; N/A | candidate quality bar, not approved reference |
| D6 | Acceptance owner, reference, file spec and destination unknown; Unresolved | not supplied in S1 | not stated | no assigned next action or deadline |

### Mini core (under 250 words)

**DEBUG PREVIEW—NOT FOR SENDING** — Example Crate | Debug draft

- Proposed illustrative scope: one simple internal crate, requested by Friday
  [D1]. Proposed quality bar: match neighboring props [D5].
- Proposed illustrative budget: probably 500-ish triangles; check needed, not
  underway [D3].
- Example Artist can do it; assignment not established [D2 Proposed]. Example
  Reviewer would review, not necessarily approve [D4 Proposed].
- Open: acceptance owner, reference, file spec and destination [D6 Unresolved].
- Readiness: Gaps for this illustrative internal task [D3, D6]; fixture values
  cannot establish Ready. External quote/payment omitted from this internal
  example's core [D1]; internal acceptance and rights are not waived.

### Six-role contact appendix

All tokens below: **Unresolved — not supplied in S1**. Purposes describe generic
roles only. Partner fields remain placeholders here: synthetic internal scope
[D1 Proposed] is not real evidence for Not applicable.

| Role | Name | Email | Chat | Phone | Timezone | Purpose | Status / source |
|---|---|---|---|---|---|---|---|
| Client producer | [NAME] | [EMAIL] | [CHAT] | [PHONE] | [TZ] | Production coordination | Unresolved / S1 not supplied |
| Client outsource manager | [NAME] | [EMAIL] | [CHAT] | [PHONE] | [TZ] | Scope/delivery coordination | Unresolved / S1 not supplied |
| Client art lead | [NAME] | [EMAIL] | [CHAT] | [PHONE] | [TZ] | Art feedback | Unresolved / S1 not supplied |
| Partner producer | [NAME] | [EMAIL] | [CHAT] | [PHONE] | [TZ] | Partner production | Unresolved / S1 not supplied |
| Partner outsource manager | [NAME] | [EMAIL] | [CHAT] | [PHONE] | [TZ] | Partner intake | Unresolved / S1 not supplied |
| Partner art lead | [NAME] | [EMAIL] | [CHAT] | [PHONE] | [TZ] | Partner art feedback | Unresolved / S1 not supplied |

An explicit debug-examples request could fill a contact as `Example Client
Producer`, `client-producer@example.invalid`, labeled Proposed — illustrative
only. This example leaves tokens to avoid inventing any role assignment.

Comparison: D2 must not render as “assigned”; D3 must not become “budget being
finalized”; D4 does not populate the client art-lead row. With actual sourced
internal-only scope, retain three separate partner N/A rows, all contact fields
N/A and the source/rationale visible. Debug does not ask the example's missing
questions; normal mini intake may ask at most five, within the 250-word core.
