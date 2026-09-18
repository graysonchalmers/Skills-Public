---
name: outsource-intake
version: 1.6
visibility: public
description: >
  Runs a structured intake when someone requests an art/production asset
  (or batch) from outsourcing or an internal team — scope, starting
  materials, delivery phases, what "good" looks like per phase, reviewers,
  deadlines, and file paths. Produces an Asset Request Sheet ready to hand
  to a vendor, preventing rework from vague scope or an undefined quality
  bar. This is the delivery-authority record; it consumes an art-brief
  document by reference (`brief_ref`) rather than re-deriving art decisions.

  Use whenever someone brings the user an asset ask that needs to become a
  trackable request. Triggers on: "someone just asked me for an asset,"
  "help me scope this ask," "walk me through this asset request," or a
  pasted Slack/email message asking for art, 3D, animation, VFX, UI, or
  fabrication work.

  Not for pure visual/style direction alone — use art-brief for that. This
  covers scope, phases, sign-off, timeline, and files, with lightweight
  style capture built in and an optional handoff to art-brief for full
  visual direction.
---

# Outsource / Asset Request Intake v1.6

![Example output: a vague "12 props" ask turned into a vendor-ready Asset Request Sheet with phased delivery gates, per-phase acceptance, and flagged risks](references/example-output.webp)

## Why this exists

Most asset asks arrive underspecified: "hey can you get me a chair for the
tavern scene." Nobody's being lazy — the requester usually doesn't know what
information a production request actually needs. The gap gets discovered
three weeks later when the vendor delivers something technically correct but
wrong, because "good" was never defined, or nobody agreed on when to review
the blockout before high poly work started.

This skill runs the intake conversation an experienced outsource manager
would run instinctively, so the gaps get caught before work starts instead
of after money and time are spent.

## Request-scoped debug preview

Only an explicit request for debug mode / a headless debug preview enables this
exception. Read `references/debug-and-contacts.md` before using it. Produce the
requested artifact immediately with unobtrusive placeholders; do not ask for real
information or wait at STOP/confirmation gates. Label every preview, output block,
and excerpt **DEBUG PREVIEW—NOT FOR SENDING**. Placeholders/examples are never
Confirmed or evidence for Ready, even when quoted from a supplied synthetic
fixture. Keep fixture values Proposed — illustrative only; keep missing values
Unresolved. Genuine non-synthetic inputs retain their source/status. No lookup,
outreach, or tracker writes in debug.
The override ends with this request; normal mode and its gates are unchanged.

## Source-linked rendering — load before any recap

Read `references/source-linked-output.md` **before the first extraction summary,
quick read or Step 5 recap**, and read it again **before Step 6 assembly or a
recipient reply**. Build a visible compact source/decision register first. Render
condensed claims from those atoms with IDs, labels and a source key; one shared
appendix serves recap, sheet and replies in a package. No runtime dependency.

## Adaptive frontier interview contract

Read `references/frontier-interview.md` before a normal-mode intake; it defines the round trace and frontier fields used below.

Normal mode is an adaptive, multi-turn interview. Register supplied facts and exact
source spans first; compute the current decision frontier, meaning only decisions
whose prerequisites are settled. Ask **2–4 consequential questions** from that
frontier, with recommendations where useful. Never re-ask captured facts or ask a
downstream question before its prerequisite is settled. After every answer, update
the visible source-linked register without silently recycling IDs, append the answer
and atom change to the interview trace, and recompute the frontier. Be quiet when
remaining gaps are non-blocking; stop at the recap/assemble step when the remaining
gaps do not change the requested sheet, or when the user explicitly requests a
draft with gaps. Gaps remain visible and proposals remain Proposed.

This is request-scoped. Explicit debug mode is immediate and asks no questions,
does not wait at confirmation gates, and uses **DEBUG PREVIEW—NOT FOR SENDING**
per `references/debug-and-contacts.md`. Normal multi-turn runs retain the frontier,
question, answer-source, and register-evolution trace — **and include the trace
block itself (rounds with `frontier_before` / `frontier_after`, per
`references/frontier-interview.md`) in the assembled sheet**, not only in harness
evidence; the final sheet renders
from the latest register plus one shared source key/register appendix. The mini
route remains a separate route: its core is **at most 250 words** and the entire
intake asks **at most five total questions**, including recap/reply questions; do
not hide operational prose or extra questions in appendices.

## Role boundary — the two records (v1.6)

This skill produces the **delivery-authority record**: scope/change policy,
contact directory, review process, commercial terms, phases, and milestones.
**Art-brief** produces the **style-authority record** (the art bible): visual
language, references, priority-weighted requirements, explicit avoids. The
only coupling point is `brief_ref`.

### Consuming an art brief (`brief_ref`)

When an art-brief document exists for the ask (supplied directly, or named by
the requester), register it as the **brief of record** and cite it in the
sheet's `brief_ref` field:

- **Reuse, don't re-derive.** The brief's priority-weighted requirements,
  borrow/avoid decisions, style authority, interpretation class, and
  reference IDs are captured decisions with provenance — copy them into the
  sheet by reference (cite the brief's version/date and register appendix),
  never re-interview or re-interpret them here. This skill's lightweight
  Style Capture covers only asks with *no* brief of record.
- **The brief's open decisions stay the brief's.** A Proposed palette or an
  Unresolved visual decision in the brief does not become Confirmed by
  appearing in the sheet; cite it with its label and route resolutions back
  through the brief (or the handoff below), not through intake questions.
- **No brief on file is a visible gap, not a blocker.** When the ask needs
  full visual direction and none exists, record `brief_ref: Unresolved — no
  brief on file`, keep the quality bar flagged, and offer the handoff to
  art-brief (Step 3) rather than improvising art decisions here.
- **Conflicts route, never resolve here.** If a supplied intake fact
  contradicts the brief (e.g. a milestone the brief's avoids conflict with,
  or a spec the brief leaves Unresolved), flag the conflict against the
  brief's register IDs and mark it Unresolved with next action + owner.
  Do not silently override the style record from the delivery record.

This skill never composes the brief's blocks (visual language, avoids,
generation prompts), and art-brief never composes this sheet's blocks
(scope/change policy, contacts, process, commercial terms, milestones).

## Input Modes — detect automatically, don't ask which mode to use

**Extraction mode**: the user pastes a forwarded message, email, or a request
that already contains real details (asset type, rough scope, maybe a
deadline). Parse everything you can out of it first. Then ask only for what's
genuinely missing — don't re-ask anything already answered.

**Interview mode**: the user gives a bare trigger with little detail ("someone
just asked me for a character asset, help me intake it"). Select the mini/full
route in Step 1, then ask only the consequential gaps within that route.

Most requests are a blend. Extract supplied facts into register atoms before
paraphrasing them. Render a short ID-linked summary; mark interpretations
Proposed and requested dates as requested. Then ask only consequential gaps.

## Provenance — preserve through recap, output, and handoff

Use these labels for captured facts and decisions, not confidence scores:
- **Confirmed** — explicit input; cite the message, document/section, or
  named person/date. This records what was stated, not proof of that person's
  authority or of partner agreement. Record those separately when needed.
- **Observed** — something actually seen in a reference, with a reference ID
  (e.g. R1). An observation is not a requirement.
- **Proposed** — an agent suggestion, inference, or interpretation, including
  inferred engagement class and suggested phases. Ask for confirmation.
- **Unresolved** — a missing decision; record next action and owner/date if
  known, otherwise leave those explicitly unknown.

Group fields sharing a source/status for brevity, but never hide differences
inside a group. A general "go ahead" permits the draft, not promotion of every
assumption. Only explicit acceptance of identified proposals promotes them
to Confirmed; keep the acceptance source. Do not re-ask captured information.

Use the source-linked register for value, hedge, action state, and scope/role
limits. Unknown means **not supplied or not established by these sources**, not
nonexistent, excluded, unassigned, or not yet done. Keep numeric values separate
from their reasons, requested dates from agreed dates, review from approval,
availability from assignment, and scope inclusion from commercial treatment.

## Step 1 — Classify the Ask

Determine:
- **Asset type(s)**: character, prop, environment, creature, VFX, UI, key
  art/marketing, scene comp, physical/fabrication, or something else. If
  ambiguous, make your best call and confirm it rather than guessing
  silently.
- **What counts as one.** Before counting, confirm the unit. "A character"
  can mean a bust, or a full body with four outfits, three LODs, a rig and a
  cosmetic set. An undefined unit doesn't stay undefined — it resolves
  silently in whoever prices it next, then resolves again, differently, at
  review. Confirming this costs one sentence and prevents the most common
  scope argument in outsourcing.
- **Single asset or batch**: how many, and are they variants of one thing
  (12 icons in one style) or distinct assets (3 different creatures)? This
  changes how phases and reviews get structured — a batch usually wants a
  style-lock on one exemplar before scaling to the rest. If the requester
  plans to compress a batch's timeline by adding artists, note (don't
  block on) that this has diminishing returns, not a linear speedup.
- **Criticality.** Record supplied stakes; a classification inferred from
  context is Proposed, not a settled priority. Use it to right-size questions
  and optional review suggestions, not to invent mandatory gates.

### Choose mini or full before asking questions

Use the **mini-sheet** for an internal, single-asset, low-stakes ask with a short
(sub-week) turnaround. If that route is inferred, label the routing choice
Proposed; it does not settle project requirements. External vendors, batches
and hero-critical work use the full sheet.

**Mini is a separate route, not a compressed Stage A/B/C form.** Capture scope,
quality/style-match, supplied technical constraints, requested deadline,
reviewer and separately evidenced acceptance owner, and load-bearing gaps.
Do not load phase templates or add quote/payment/vetting ceremony by default.
Record a supplied review point or a useful Proposed check, not a new stage plan.
At most **five questions total** for a mini-sheet, counting questions in recaps
and replies; no extra questions hidden in appendix rows. Unknowns remain gaps.
Go to Step 3 only for supplied references, then use the mini recap/output in
Steps 5–6; skip the full ladder, vendor checks and full-sheet template.

The complete mini core, including header, readiness line and questions, is
**at most 250 words**, excluding only the compact source register/key and full
six-role contact appendix. Do not move operational prose into an appendix to
hide it from the cap. A separately requested short DM uses the same atoms,
not a second intake or a way to add questions.

### Engagement class — the interpretation dial

Ask lightly: *"How much interpretation should the partner carry?"* Infer a
class as **Proposed** when context supports it, then confirm. Use these exact
names, including in an art-brief handoff:

| Class | Intake emphasis |
|---|---|
| **Self-governing** | Supply vision, boundaries, a decision-maker, and timely answers. Invite creative proposals and technical judgement; never invent approved technical or business facts. Keep proposed solutions distinct from settled constraints. |
| **Brief-driven** | Capture the stated quality bar, explicit requirements and exceptions, and a named reviewer. Do not expect unspoken gaps to be filled. |
| **Volume with QA overhead** | Capture approved exemplars, repeatable specs, intake ownership, and actual QA/review capacity before scaling. Record the sampling/review plan as Proposed until accepted. |

These describe the engagement, not vendor quality or a permanent studio tier.
Split by workstream when useful (e.g. self-governing concept work, brief-driven
production). Never infer class from asset count alone. Class calibrates how
much interpretation to invite, not risk or review gates by itself; criticality,
novelty, dependencies, and actual review capacity still govern process.

## Step 2 — Core Intake Questions

For full sheets, ask only unanswered consequential questions; mini-sheets use
the Step 1 route instead of the ladder below. If an elicitation/tappable-question
tool is available, use it and batch 2-3 questions per round — that's easier
to answer than a wall of text, especially mid-conversation. If that tool is
unavailable or fails, fall back immediately to a clean numbered list in plain
text. Don't stall on the tool not working — the questions matter, not the
delivery mechanism.

Cap the first full-sheet question round at five questions, ordered by what unblocks
the next decision; park the remainder behind the recap instead of front-
loading them. A bare trigger ("someone asked for X, that's all I know")
still yields a usable artifact: captured facts, one capped question round,
and a draft skeleton — not a fifteen-question interrogation. Later rounds
follow once the first answers land.

Capture any supplied partner/context without making vendor selection an intake
question or prerequisite. Lookup/recommendation is opt-in via Step 4. Read
`references/debug-and-contacts.md` for the six-role client/internal + partner
directory (producer, outsource manager, art lead per side; name, email,
Slack/Teams, phone, timezone, purpose, status/source). Fill unknowns with tokens;
internal-only partner rows are N/A. Keep sign-off authority separate. Missing
contacts do not block a draft or trigger procurement questions.

Organize the remaining gaps around the GRIP Buyer Readiness ladder. Capture
answers once, then reuse them in the process check and readiness rows.

### Stage A — Can we quote?

1. **Scope / unit** — count, type(s), inclusions and exclusions from Step 1.
2. **Quality bar and starting material** — name an existing quality artifact
   (file, shipped asset, or reference ID), not just adjectives. Capture what
   exists today and its approval status, by whom and for what use. A polished
   concept is not necessarily approved. Run Step 3 for visual references;
   flag missing or unapproved targets rather than inventing an approved bar.
3. **Technical specification** — engine and version; formats; polygon,
   texture, and other applicable budgets; naming convention; source-file
   expectations; delivery destination. Cite the spec/version when available.
   Mark genuinely inapplicable fields with a rationale; unknown paths get
   placeholders and remain gaps, not guessed defaults.
4. **Style authority** — one named final voice on the look. Capture separately
   from Stage B's procedural approval owner, even if the person is the same.

### Stage B — Can we run?

5. **Review gates and deliverables** — reuse the stated process. If a plan
   would help, offer a relevant portion of `references/phase-templates.md` as
   **Proposed**, not a required full sequence. Ask for acceptance or changes
   within the question budget. Record only sourced or clearly Proposed gates;
   absent process evidence is a gap, not a mandate for extra sign-offs.
6. **Approval owner and reviewers** — record commenting reviewers separately
   from evidenced procedural approvers, scoped to each phase. Reviewer-only
   input cannot populate approval ownership or any exact contact-directory
   role. Preserve committees/joint approvers as supplied; ask who releases
   the gate if unclear, without inventing a sole owner or escalation waiver.
7. **Feedback operation** — channel and form of notes, turnaround, one
   consolidator, buyer-side review/QA capacity, and escalation for conflicts
   or delayed answers. Record capacity for the proposed batch size and cadence,
   not merely that a reviewer exists.
8. **Done per phase** — one sentence of acceptance criteria, a phase-specific
   reference, and review conditions (e.g. engine lighting, camera distance,
   gameplay speed, or agreed viewing/export setup). Also capture overall and
   phase dates, dependencies, and who supplies each dependency by when.

Reuse approved exemplars: mark **reference requirement satisfied** with the
reference ID, approval source, and applicable phase; don't re-ask or create a
redundant exemplar task. **Approved reference availability is not production
phase completion.** Mark a phase complete only with evidence that this scoped
work was delivered and accepted by its approval owner. An approved concept
may settle the look without completing modeling, integration, or the batch.

### Stage C — Can we commit?

Keep this a lightweight check, not a contract audit or drafting service:
9. **Payment terms and trigger** — both the terms (e.g. net period) and event
   (delivery, acceptance, invoice date). "On approval" with no approval owner
   is a gap. Record whose agreement is evidenced, not just whose input arrived.
10. **Change-order rule** — new scope versus fixing a miss, revision allowance,
    and how change cost/approval is handled before it arises.
11. **Pause / cancellation** — applicable notice, payment/work treatment, and
    restart or cancellation terms are settled or explicitly unresolved.
12. **IP / credit / portfolio** — ownership, credit, and what may be shown when
    are separate questions, not one implied permission.

An existing SOW/MSA can answer these: cite its relevant section/version and
applicability to this engagement, and preserve known acceptance status. Don't
re-litigate settled terms; "probably in our standard SOW" is not settled.
For internal work, commercial items may be **Not applicable** only with an
explicit rationale and source; internal does not automatically waive IP,
review, or change-control decisions.

### Cost/timeline process — retained alongside the ladder

Ask lightly whether a process exists to sanity-check whatever estimate comes
back: what a day/week means (hours, overlap, meetings/reviews, one or multiple
artists), revision allowance, and how a change is priced/approved. Reuse
Stage C answers. Missing evidence is a gap even with a confirmed vendor;
write "Unresolved — cost/timeline process not supplied." Say a process does
not exist only when a source explicitly states that, within its stated scope. Use
`references/cost-timeline-reality-check.md` for the framework, never market
rates or dollar recommendations.

### Readiness rules

For full sheets, produce three rows: **Quote / Run / Commit**, each **Ready**, **Gaps**, or
**Not applicable**, with evidence, missing fields, next action, owner, and date
(unknown where unknown). State the exact workstream and phase/scope assessed.
- **Ready** requires all applicable inputs for that row to be explicitly
  settled for the stated scope, with authority/partner agreement recorded
  where required. Confirmed input alone is not proof of those agreements.
  Proposed values, unknown flags, and a document title alone cannot support it.
- **Gaps** identifies unsettled inputs; it never prevents a draft after the
  Step 5 confirmation. Do not label a row Ready merely because gaps are listed.
- **Not applicable** needs an explicit scope-specific rationale and source,
  not a blank field or "no vendor yet." Record item-level exceptions too.

Readiness can be scoped to an agreed exploration phase; do not claim the whole
production batch is ready when its quality bar or specs still depend on that
exploration. Each row assesses its own inputs; show upstream gaps alongside it.
These are readiness findings, **not authorization to hire, start work, or pay**.
Never summarize Run: Ready alone as "ready to start" when Quote or Commit has
gaps. For an internal exploration, explain applicable process/IP controls rather
than manufacturing external commercial requirements. Missing owners stay unknown;
assigning them is a Proposed action, not a fact. One person may legitimately
hold both style authority and approval ownership; matching names alone are not
a risk. Capture authoring canvas and display/export sizes separately for icons;
an export dimension does not establish the source-file canvas.

## Step 3 — Lightweight Style Capture

Don't skip this to art-brief by default. Inspect supplied references with the
lightweight pass below. When comparison would help, read
`references/curated-comparisons.md`: offer only 1–2 useful Proposed comparisons
with exact borrow/avoid/why and source/inspection status, not a quota. Suggested
comps are not inspected refs, claimed influences, or approved negatives. Skip
reference enrichment for a routine internal crate unless requested. With no
provided images, skip the image-analysis steps rather than invent observations.

1. Inspect provided images/files with the available viewing tool and assign
   reference IDs. If a link/file cannot be inspected, say so; a user's
   description is Confirmed input, not an Observed image finding.
2. Capture **Observed** palette, material, silhouette, and mood details with
   reference IDs. Keep **Proposed** interpretations of their intended use
   separate from **Confirmed** requirements and exceptions.
3. Condense into a **quick-read version** — 2-4 sentences preserving those
   labels. Calibrate to the class: invite options for Self-governing, capture
   bar + exceptions for Brief-driven, and emphasize approved exemplars and
   repeatability for Volume with QA overhead. Never turn visual cues into
   approved engine budgets, dimensions, business terms, or requirements.
4. Leave an explicit placeholder block for the actual reference images —
   this document ships alongside the real files/images, it doesn't replace
   them. Text interpretation supports the visuals, it isn't a substitute.

If the ask is complex or high-stakes enough to warrant a full art-direction
document (new IP, first brief to a new vendor, major hero asset), say so and
offer to hand off to **art-brief** for the complete treatment — priority-
weighted requirements, IP borrow/avoid extraction, scope boundaries, and
generation prompts. That's an offer, not a default; most day-to-day requests
don't need it. On handoff to art-brief, preserve engagement class per
workstream, its status and source, all captured facts with provenance,
reference IDs/approval scope, and open decisions with owners/dates. Receive
these unchanged on a return handoff; ask only for gaps or conflicts, never
restart intake or silently promote proposals.

## Step 4 — Vendor Lookup (opt-in, never an intake gate)

Run only when the requester explicitly asks for lookup/recommendation, and never
in debug. No vendor name is required to continue intake; leave supplied partner
context or an Unresolved placeholder without asking a procurement question.
If lookup is requested:

1. Check whether a vendor database is available in the current environment
   — an Airtable base, Notion database, spreadsheet, or another connected
   source that indexes vendors by specialty, capacity, or past work.
2. If one is available, search it against the asset type and scope, and
   present 2-3 candidates with a short rationale for each.
3. If no vendor database is configured, or the search doesn't turn up a
   confident match, don't guess — flag the line item clearly:
   **"🔶 Vendor: needs recommendation — route to the outsource manager or
   art director."**

This skill deliberately doesn't hardcode any specific vendor database or
connector, so it works the same way for anyone who installs it. If the
current environment already has a vendor lookup set up (through memory,
another skill, or a connected tool), use it only within that explicit lookup
request — connector availability does not opt the user in. Do not contact
candidates or write a tracker as part of lookup.

### If this is a new or unverified partner

A full vetting process is out of scope for this skill — it belongs earlier,
before an ask ever reaches intake. If a named partner is new/unverified, retain
known evidence and relevant readiness flags at the criticality set in Step 1.
The following are evidence checks, not a mandatory interview or a reason to stop
for vendor names; park gaps unless resolving one matters to the requested decision:

- **Any criticality**: has a named lead and their actual availability been
  confirmed — not just a studio name?
- **Standard or above**: has anything been seen in-engine or in-motion, not
  only beauty renders? A render says nothing about topology, budgets, or
  whether it runs.
- **Hero / critical-path only**: is a paid test asset planned before
  committing to the full scope? Never an unpaid one — an unpaid test
  selects for the studios with the least other work, which is the opposite
  of what a hero asset needs.

When vetting evidence is absent, write "Unresolved — vetting evidence not
supplied for this scope." Only an explicit source can establish that vetting
has not occurred. Let the requester decide what to do; routing needed is not
routing planned or completed.

One call establishes contact only, not prior engagement or vetting. Preserve
an explicit "existing partner" statement as attributed input, with evidence of
engagement/vetting separately Unresolved if absent; an assistant inference of
an existing relationship is Proposed. Neither establishes current capacity.

## Step 5 — Confirm, Then Assemble

Re-read `references/source-linked-output.md` before rendering the recap;
update its atoms from the input, not from an earlier paraphrase. Use IDs and
labels in every substantive recap line and append the compact register/key.

**Mini route:** render the Step 6 mini core itself as the recap/draft with gaps;
ask for corrections within its 250-word/five-question budget. Do not duplicate
it as a full Stage recap or wait solely to issue the same mini-sheet again.

**Full route:** use this recap before assembling the full sheet:

```
📋 QUICK RECAP — confirm before I assemble the full draft:

Scope: [type, count, unit, workstream/current phase]
Art brief of record: [brief_ref + version/date, or Unresolved — no brief on file]
Criticality / Partner context: [level / supplied partner or unknown; relevant flags]
Engagement class: [exact class per workstream — provenance + source]
A — Quote: [quality artifact + starting approval, technical spec, style authority]
B — Run: [confirmed/proposed phases, done criteria + references/conditions,
  approval owner, feedback channel/turnaround/consolidator/capacity/escalation,
  dates + dependencies]
C — Commit: [payment terms + trigger, change rule, pause/cancel, IP/credit/portfolio]
Cost/timeline process: [settled inputs / gaps]
Readiness: [Quote / Run / Commit: Ready / Gaps / Not applicable;
  scope, evidence, missing fields, next action + owner/date for each]
Proposals needing explicit acceptance: [identified P1, P2... + sources]
🔶 Open decisions / flags: [Unresolved + next action/owner/date]
```

Keep provenance/source labels and IDs visible. For the full route in normal
mode, wait for confirmation or permission to draft **before producing the full sheet**.
Explicit request-scoped debug bypasses this wait.
General permission to draft is sufficient to assemble it with unresolved
items; it does not accept every proposal or authorize execution. Promote only
explicitly accepted, identified proposals, citing that acceptance.

**Sendable-message contract** (any recipient-ready email, DM, or reply —
vendor responses, requester asks, status updates): state settled facts only when
Confirmed with their actual scope and hedges.
Explicitly labeled proposals and questions may be included for review, never as
promises, accepted terms, or instructions to execute. Unresolved items appear
as questions or open items, never as settled answers. Do not commit the user to
dates, prices, scope answers, or process promises (escalation rules,
turnaround offers, "notes always consolidated") they have not stated —
process structure drafted for vendor review stays Proposed and is marked
as such inside the message. A recipient's question plus an undecided user
equals an open item relayed back to the user, not an invented answer. If
the user must decide something before the message is safe to send, say so
plainly at the top.

**Release comparison:** apply `references/source-linked-output.md` to every
condensed clause, including headings, table cells, replies and change logs.
Compare source span → register atom → rendered clause, not just IDs or labels.
Repair unsupported verbs, roles, scope, certainty, or approval before returning
it; a correct appendix cannot excuse a contradictory opener.

## Step 6 — Output: Asset Request Sheet

Re-read `references/source-linked-output.md` before assembly. Render from the
updated atoms, using inline IDs and labels, then compare each rendered clause
against its exact source span. Readiness is separate from provenance/completion.

### Mini-sheet output (Step 1 mini route only)

Use at most 250 words for this entire core, including any questions. Do not
render Stage headings, a phase table, or separate Quote/Run/Commit discussion:

```text
Asset request — [name] | Draft | [document date]
Scope / quality: [ID-linked supplied direction; Proposed style options if useful]
Spec / deadline: [supplied values and hedges; requested vs agreed date]
People / review: [availability vs assignment; reviewer vs acceptance owner]
Open items: [load-bearing Unresolved decisions, owner/date only if supplied]
Readiness: [Gaps/Ready for exact internal task; rationale and evidence IDs;
  external quote/payment N/A only with a scoped reason; internal review/IP retained]
  Readiness is not authorization to start work.
Questions: [only necessary questions, at most five total across this mini intake]
```

Attach the compact source key/register and the **full six-role directory** from
`references/debug-and-contacts.md`: every row retains name, email, chat, phone,
timezone, purpose and status/source; retain three distinct partner N/A rows for
internal-only scope. Do not ask for those contacts to complete the mini-sheet.
Do not declare Ready from a likely budget, available artist or fixture approval.

### Full Asset Request Sheet (not used for mini route)

```markdown
# 📋 Asset Request — [Asset name / batch name]

**Requested by:** [name] | **Date:** [date] | **Status:** Draft
**Assessment scope:** [workstream + current phase/batch boundaries]

## Scope & Engagement
- Art brief of record: [brief_ref: document + version/date, or "Unresolved —
  no brief on file"; conflicts against it flagged, not resolved here]
- Asset type(s), quantity, what counts as one, inclusions/exclusions:
- Shared-style batch or distinct assets:
- Criticality: [hero/critical-path / standard / background]
- Engagement class per workstream: [Self-governing / Brief-driven /
  Volume with QA overhead — Confirmed/Proposed/Unresolved + source]
- Interpretation latitude and fixed boundaries: [provenance + source]

## Partner Context (not a selection gate)
- [Supplied partner / Unresolved — not supplied / internal-only N/A;
  recommended candidates only if explicitly requested]
- New partner? [yes/no/unknown]; lead + availability, applicable
  in-engine/in-motion evidence, paid test plan: [status + evidence/gaps]

## Stage A — Quote Inputs
- Starting material: [what exists, files/reference IDs]
- Approval: [who approved what use, source/date, or Unresolved]
- Quality artifact / approved exemplar: [ID + bar it establishes]
- Quick read: [2-4 sentences with provenance]
- Full interpretation: [Observed details vs Proposed use, if references exist]
- References: [ID -> file/link, or 📎 placeholder]
- Technical spec: [source/version; engine/version; formats; polygon/texture/
  other budgets; naming; source files; destination; explicit N/A rationales]
- Style authority (final word on the look): [name + source]

## Stage B — Run Inputs
- Phase plan acceptance: [source, or identified Proposed plan]
| Phase / deliverable / gate decision | Done criteria | Reference + approval scope | Review conditions | Due / dependencies + owner | Reviewer / approval owner (separate) | Completion evidence or Unresolved — not supplied |
|---|---|---|---|---|---|---|
| ... | ... | [reference satisfied != phase complete] | ... | ... | ... | ... |
- Approval owner (procedural yes): [name per phase, separate from style authority]
- Other reviewers / consultations and disagreement resolution:
- Feedback: [channel + form; turnaround; consolidator]
- Buyer-side review/QA capacity and escalation:
- Overall deadline and external dependencies: [owners + dates]

## Cost & Timeline Process
- Estimate status: [explicitly supplied state + ID, or Unresolved — not supplied; no rate recommendation]
- Unit / day or week: [hours, overlap, meetings/reviews, single/multi-artist]
- Revision allowance and change-cost process: [reuse Stage C evidence]
- Process flag: [specific sourced state or Unresolved — process evidence not supplied]

## Stage C — Commit Inputs (lightweight, not a contract)
- Payment terms AND trigger:
- Change-order rule: [new scope vs fixing a miss, rounds, cost/approval process]
- Pause / cancellation terms:
- IP ownership / credit / portfolio permission and timing:
- Terms sources / applicability / whose acceptance is recorded:
- Internal or other Not applicable items: [explicit rationale + source]

## Readiness — not authorization to hire, start, or pay
| Question | Assessed workstream / phase | Ready / Gaps / Not applicable | Evidence / N/A rationale | Missing fields | Next action | Owner | Date |
|---|---|---|---|---|---|---|---|
| Quote | ... | ... | ... | ... | ... | ... | ... |
| Run | ... | ... | ... | ... | ... | ... | ... |
| Commit | ... | ... | ... | ... | ... | ... | ... |

## Source Register Appendix
[One shared source key and compact decision register; exact spans and IDs per
references/source-linked-output.md. Referenced by recap, sheet and any replies.]

## Contact Directory Appendix
[Full six-role directory from references/debug-and-contacts.md; retain all fields,
status/source, and internal-only partner N/A rows. Not assignment or authority.]

## Open Risks / Flags
- [Unresolved decisions: missing field + next action + owner/date or unknown]
- [Identified Proposed choices awaiting acceptance; source/interpretation basis]
- [Upstream or later-phase gaps outside the current assessment scope]
```

Keep **Open Risks / Flags** on full sheets (Open items on mini-sheets). If no
issues were identified, bound that finding to the supplied material and assessed
scope; an empty source package is not evidence that no risks exist.

In normal mode only, if a Notion, Airtable, or similar destination is connected and the requester
wants this tracked there rather than (or in addition to) a standalone
document, offer to push it — but confirm before writing anything to an
external system. Default to producing the document itself; pushing it
somewhere is a follow-up action, not an assumption.

## Quality Standards

- **No automatic phase templates** — reuse sourced process; useful additions
  are Proposed. Mini-sheets skip the full ladder and template loading.
- **Reuse approved exemplars without claiming completion** — record the
  reference requirement as satisfied; phase completion requires evidence of
  delivery and acceptance of the scoped work. Don't re-ask for captured refs.
- **Undefined "good" gets flagged, not invented as approved** — offer a
  clearly Proposed bar or exploration phase where useful. Observed references
  and creative interpretations do not become requirements without acceptance.
- **Class and provenance survive handoff** — use the shared exact class names
  and Confirmed / Observed / Proposed / Unresolved labels. Class is engagement
  context, never a vendor ranking or a substitute for risk/review decisions.
- **Gaps don't block drafting; they do prevent unsupported Ready** — unknown
  technical, operational, cost/timeline, or commercial inputs stay visible,
  regardless of vendor assignment. Apply the scoped readiness rules in Step 2
  and the confirm-before-full-sheet rule in Step 5 together.
- **No dollar figures, ever.** This skill checks whether a cost/timeline
  process exists, never what the number should be. Publishing or inventing
  a rate is a market intervention this skill has no business making — see
  `references/cost-timeline-reality-check.md`.
- **Style authority and approval owner are named separately**, even when
  they're the same person — collapsing them is a common, avoidable source
  of rework.
- **Vetting rigor scales with criticality**, not a uniform checklist for
  every ask — a background prop and a hero asset on the critical path earn
  different amounts of process.
- **Mini means a separate route** — select it in Step 1; at most 250 words of
  core and five questions total, one scoped readiness line, no Stage ceremony.
  Only the compact source register/key and complete six-role contact appendix
  sit outside that cap. Full sheets serve external, batch or hero-critical asks.
- **Placeholders over blocking** — missing file paths or images shouldn't
  stall the intake; leave a clear 📎 placeholder and move on.
- **Style capture is lightweight by design** — this isn't art-brief. Offer
  the handoff for anything that needs full art-direction treatment rather
  than trying to replicate it inline.
- **Vendor lookup degrades gracefully** — no configured database is a normal
  case, not an error. Flag and move on.

## Version Notes & Verification

**v1.6** — role-boundary split: this skill is the delivery-authority record;
art-brief is the style-authority record. New `brief_ref` consumption: an
existing art brief is cited and reused by reference (never re-derived,
re-interviewed, or silently overridden); "no brief on file" is a visible gap
with a handoff offer, and conflicts against the brief route to its register
instead of resolving here. Recap and full sheet gain an "Art brief of record"
line.

**v1.5** — source-linked register before recap and assembly; semantic clause
comparison; missing evidence no longer rendered as nonexistence; distinct
reviewer/approver roles; optional evidenced gates; separate 250-word mini route
with five-question total cap and complete source/contact appendices.

**v1.4** — explicit request-scoped debug artifacts with placeholders; six-role
contact appendix; opt-in lookup without procurement interrogation; lightweight
curated comparisons; action-state/hedge preservation; sourced numeric reasons;
proposals allowed in replies without promises; inclusion is not a change order.

**v1.3** — condensation-layer fixes from headless-rig findings:
sendable-message contract for recipient-ready replies (no invented dates,
scope answers, or process promises); proportional mini-sheet for trivial
internal asks; first-round question cap; relationship claims (existing
partner) require documented prior engagement, not a single call.

**v1.2:** adds the shared engagement-class/provenance contract and GRIP
Quote / Run / Commit ladder; expands technical, feedback, and commercial
capture; distinguishes approved references from completed production phases.
Vendor lookup, criticality-scaled vetting, template confirmation, and explicit
confirmation before the full sheet remain. Existing examples are historical
illustrations, not authority to skip v1.2 fields or promote assumptions.

Verify with scenarios, checking recap and full-sheet behavior separately. Also
exercise `references/debug-and-contacts.md`'s debug/contact/action cases and
`references/curated-comparisons.md`'s comp-versus-inspected-reference boundaries;
retain actual outputs for independent review, not the generator's self-grade.
Structural checks alone do not prove behavior.

Additional cases:
- Dense 12-icon ask with approved exemplars: reuse IDs and approval scope;
  do not infer Volume with QA overhead from count or mark the batch complete.
- Bare hero creature ask: propose class/phases; flag missing bar/spec/process;
  preserve paid-test/light-vetting behavior, then wait for recap confirmation.
- Self-governing exploration: creative options remain Proposed, unknown
  engine budgets remain Unresolved, readiness is only for the settled phase.
- Brief-driven work with exceptions: preserve the confirmed bar and exceptions;
  do not silently substitute observed reference details as requirements.
- Volume with QA overhead but no review capacity: flag Run gaps despite
  approved exemplars. Class alone must not select gates or lower risk.
- "Go ahead" after P1/P2: assemble a draft but keep both Proposed. "Accept P1"
  promotes only P1 with that source; a forwarded statement proves neither
  approval authority nor partner agreement by itself.
- Existing SOW or internal work: reuse applicable evidenced terms, require
  N/A rationale, and retain unknown pause/payment/rights decisions as gaps.
- art-brief round trip: class/status/source, reference IDs, and open decisions
  survive; no re-interview of captured answers. Missing paths remain placeholders
  and gaps, not a reason to refuse the draft or claim Ready.
- Trivial internal ask ("model a crate by Friday"): mini-sheet, ≤5 questions,
  collapsed readiness, and a reply that invents no schedule or capacity
  commitments on the user's behalf.

Sources: GRIP Field Journal, *The Buyer Readiness Checklist*
(`KIT-01-Buyer-Readiness-Checklist.md`, Stages A–C) and *Rates, Tiers & Fair
Engagement* (`SOP-03-Rates-And-Tiers.md`, engagement classes and rate structure).
The local companion `references/cost-timeline-reality-check.md` applies those
principles without publishing rates; `references/phase-templates.md` remains
suggestion-only.

## Companion Skills

- **art-brief** — the style-authority record (the art bible: visual language,
  IP extraction, priority-weighted requirements, explicit avoids, generation
  prompts). This skill is the delivery-authority record; when an art-brief
  document exists for the ask, cite it as `brief_ref` and reuse its decisions
  by reference (see "Role boundary" above) — never re-derive or re-interview
  them. Offer the handoff for complex or high-stakes asks with no brief on
  file; don't invoke by default.
- **image-decomp** — if reference images need deeper structured analysis
  than the lightweight Style Capture in Step 3 provides, this can feed richer
  input into that step.
- Any configured vendor-database skill may support an explicitly requested
  Step 4 lookup. Tracking is a separate opt-in, confirmed before writing;
  neither connector availability nor debug permits automatic use.

## Example Triggers

- "Someone on the AI team just asked me for 3 enemy creature variants for
  the new biome — help me intake this."
- "hey grayson can u get me a treasure chest prop for the dungeon area? need
  it by end of july, sarah's gonna review. nothing existing yet, no concept
  art" (forwarded message — extraction mode)
- "I need 12 inventory icons, we already have a style guide page and 3
  approved example icons, vendor is StudioXYZ, need first 4 by next Friday
  for review." (dense forwarded request — mostly extraction, few gaps)
- "Help me scope this ask before I send it to outsourcing."
- "Walk me through intaking this request — no vendor picked yet."
