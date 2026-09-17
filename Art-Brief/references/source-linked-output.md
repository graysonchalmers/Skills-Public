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

## Compact worked example — teaching excerpts, not a full brief

**DEBUG PREVIEW—NOT FOR SENDING**

Source key: **S1** = Example Requester's synthetic brief message, sentences 1–4:
“Example Hall should read clearly at night. Probably 2K textures. Example Reviewer
will review it. I'd have to check whether wall brackets are included.”
This source text is illustrative, not approval or an inspected image.

### Shared register appendix

| ID | Value / decision status | Source span | Hedge / action state | Scope / role limit |
|---|---|---|---|---|
| D1 | Night readability; Proposed — illustrative only | S1: “Example Hall should read clearly at night.” | should; N/A | readability goal, no lighting method |
| D2 | Probably 2K textures; Proposed — illustrative only | S1: “Probably 2K textures.” | probably; N/A | not a settled budget; reason not supplied |
| D3 | Example Reviewer to review; Proposed — illustrative only | S1: “Example Reviewer will review it.” | will; planned within fixture only | reviewer, not approver/art lead |
| D4 | Wall-bracket inclusion unknown; Unresolved | S1: “I'd have to check whether wall brackets are included.” | conditional; needed | neither inclusion nor exclusion; no promise to check |
| D5 | Warm lantern pools against cool shadow shapes; Proposed | assistant creative option based on D1 | suggestion; N/A | lighting exploration, not a requirement |
| D6 | Approver, scope pricing, numeric reason and gates unknown; Unresolved | not supplied in S1 | not stated | no role assignment, fee rule or milestone implied |

### Block 1 excerpt — art direction

**DEBUG PREVIEW—NOT FOR SENDING** — Debug draft, example scope only.
Proposed readability goal: Example Hall reads clearly at night [D1]. Proposed
creative option: warm lantern pools against cool shadow shapes [D5]. Probably
2K textures, illustrative rather than settled [D2 Proposed].

### Block 2 excerpt — recipient-facing draft

**DEBUG PREVIEW—NOT FOR SENDING**
Proposed night readability [D1]; Proposed lantern/cool-shadow exploration [D5].
Probably 2K textures [D2 Proposed]. Wall-bracket inclusion needs a decision
[D4 Unresolved]; commercial treatment and approval authority are not supplied
[D6 Unresolved]. Example Reviewer is a proposed illustrative reviewer only
[D3], not the approver. Sources: shared S1/register attached.

### Block 3 excerpt — natural-language exploration prompt

**DEBUG PREVIEW—NOT FOR SENDING** — Proposed illustrative exploration, not
production direction: “Example Hall, readable at night [D1], warm lantern pools
against cool shadow shapes [D5].” Texture resolution and wall-bracket exclusion
are not prompt instructions; both remain outside this exploration [D2, D4].

Comparison: D4 cannot render as “brackets excluded” or “we'll confirm”; D3 cannot
populate an art-lead directory row. D1 does not approve D5. Teaching excerpts omit
unrelated full-brief fields; an actual Art-Brief output still supplies all three
complete blocks and its six-role directory. No generation or sending is implied.
