---
name: outsource-intake
version: 1.1
visibility: public
description: >
  Runs a structured intake when someone requests an art/production asset
  (or batch) from outsourcing or an internal team — vendor, scope, starting
  materials, delivery phases, what "good" looks like per phase, reviewers,
  deadlines, and file paths. Produces an Asset Request Sheet ready to hand
  to a vendor, preventing rework from vague scope or an undefined quality
  bar.

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

# Outsource / Asset Request Intake

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

## Input Modes — detect automatically, don't ask which mode to use

**Extraction mode**: the user pastes a forwarded message, email, or a request
that already contains real details (asset type, rough scope, maybe a
deadline). Parse everything you can out of it first. Then ask only for what's
genuinely missing — don't re-ask anything already answered.

**Interview mode**: the user gives a bare trigger with little detail ("someone
just asked me for a character asset, help me intake it"). Run the full
question flow from scratch.

Most real requests are a blend — start by parsing whatever's given, then drop
into interview mode for the gaps. Say what you inferred before asking the
rest, so the requester can correct you cheaply: *"Got it — sounds like this
is 1 environment prop, deadline end of July. A few more things I need:"*

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
- **Criticality.** Is this a hero asset on the critical path, a standard
  production asset, or a background/low-stakes piece? This isn't a fourth
  scope question to ask the requester in isolation — it's usually obvious
  from context, and it calibrates everything downstream: how much vendor
  vetting is warranted (Step 4), how many review gates are worth the time
  (Step 2), and how much this intake itself should slow down to get right.
  A batch of background props and a hero character on the box art deserve
  different amounts of process — running the full checklist uniformly on
  both is its own kind of waste.

## Step 2 — Core Intake Questions

Ask whatever wasn't already answered. If an elicitation/tappable-question
tool is available, use it and batch 2-3 questions per round — that's easier
to answer than a wall of text, especially mid-conversation. If that tool is
unavailable or fails, fall back immediately to a clean numbered list in plain
text. Don't stall on the tool not working — the questions matter, not the
delivery mechanism.

1. **Vendor** — Named vendor in mind, or need a recommendation? See
   *Vendor Lookup* below either way — including what to check if this is a
   new or unverified partner.
2. **Scope** — confirmed from Step 1: count + type(s) + the unit definition.
3. **Starting material** — what exists today: nothing / napkin sketch / rough
   concept / polished concept / fully approved concept. Ask explicitly
   whether it's been **approved**, and by whom — an unapproved concept is a
   real risk to flag, since the vendor may build against something that
   still changes.
4. **Reference for "good" — final** — does the requester have example
   images, files, or an existing style guide showing the target quality for
   the *finished* asset? If yes, run Step 3 (Style Capture). If no, flag it —
   an undefined final target is the single biggest cause of rework, and it's
   worth being direct about that with the requester.
5. **Delivery phases** — what stages does the requester want to review before
   final? Pull the matching template from `references/phase-templates.md`
   and offer it as a starting point — never apply it silently. Always ask
   the requester to confirm, cut, add, or reorder. If the asset type doesn't
   match a template, ask them to define phases from scratch.
6. **Reference for "good" — per phase** — for each phase they've confirmed,
   is there an example of what good looks like at *that* stage specifically?
   A blockout reviewer checking for final texture quality is a common and
   entirely avoidable failure mode — this question exists to prevent it.
   If the starting material already includes an *approved* example that
   satisfies a given phase (e.g. approved exemplar icons before a UI batch,
   an approved concept that already covers the "final" bar for a simple
   prop), mark that phase as satisfied in the output instead of re-asking
   for a reference that already exists. Don't manufacture a review gate
   where the work is already done.
7. **Style authority and approval owner** — these are two different roles,
   and treating them as one is a common cause of rework. **Style authority**
   is whose taste is the final word on whether it looks right. **Approval
   owner** is who can procedurally say yes and move the milestone forward.
   They're often the same person on a small team and often not on a larger
   one — ask both, even if the answer is identical, so it's on record which
   one it is if a review ever splits.
8. **Timeline** — overall due date, and a due date per phase if the ask is
   phased.
9. **Cost/timeline reality check** — is there an actual process for
   sanity-checking the estimate, whatever the estimate turns out to be? Ask
   three things, lightly: what "a day" or "a week" means here (does it
   include review time, does it assume one artist or several), whether a
   revision allowance is already understood alongside the price, and
   whether the cost of a change has been named before there is one. If none
   of this exists yet, that's a normal state, not a failure — flag it as
   "no cost/timeline process established yet." This is about whether the
   requester has a process nailed down, independent of whether a vendor has
   been picked — a confirmed vendor with no such process is just as much a
   gap as an unassigned one. See `references/cost-timeline-reality-check.md`
   for the full framework and why it deliberately contains no dollar
   figures.
10. **Commercial readiness (lightweight)** — three yes/no/unknown checks,
    not a contract audit: is there an agreed **payment trigger** (delivery,
    acceptance, or invoice date — "on approval" with no named approval
    owner is a real gap, see item 7); is there an agreed **change-order
    rule** (what counts as new scope vs. fixing a miss); and is there a
    shared understanding of **IP, credit, and portfolio rights**. If any of
    these live in a standard SOW/MSA the requester already has, that's a
    satisfied answer — don't re-litigate a solved problem. If they're
    genuinely undefined, flag once and move on; this skill doesn't draft
    commercial terms.
11. **Reviewers / approvers** — beyond style authority and approval owner
    (item 7), is there anyone else in the loop, and does that change by
    phase (e.g., a lead reviews blockout, a producer reviews final)?
12. **File paths / delivery destination** — ask for the path. If it's not
    settled yet, leave a placeholder block in the output rather than
    blocking the intake on it — this gets filled in later.

## Step 3 — Style Capture (only if references or images were provided)

Don't skip this to art-brief by default — do a lightweight pass inline:

1. Look at whatever reference material was provided (images, style guide
   links, described concept art).
2. Write a **deep interpretation**: palette, materials/surface treatment,
   silhouette language, mood, and anything about the reference that a vendor
   could misread if left unstated.
3. Condense that into a **quick-read version** — 2-4 sentences a vendor could
   absorb in ten seconds, for the top of the request sheet.
4. Leave an explicit placeholder block for the actual reference images —
   this document ships alongside the real files/images, it doesn't replace
   them. Text interpretation supports the visuals, it isn't a substitute.

If the ask is complex or high-stakes enough to warrant a full art-direction
document (new IP, first brief to a new vendor, major hero asset), say so and
offer to hand off to **art-brief** for the complete treatment — priority-
weighted requirements, IP borrow/avoid extraction, scope boundaries, and
generation prompts. That's an offer, not a default; most day-to-day requests
don't need it.

## Step 4 — Vendor Lookup

If the requester wants a recommendation rather than naming a vendor:

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
another skill, or a connected tool), this step uses it automatically — there's
nothing to configure inside this skill itself.

### If this is a new or unverified partner

A full vetting process is out of scope for this skill — it belongs earlier,
before an ask ever reaches intake. But if the requester mentions this is a
first engagement with this vendor, scale a light check to the criticality
set in Step 1 rather than skipping it or over-building it:

- **Any criticality**: has a named lead and their actual availability been
  confirmed — not just a studio name?
- **Standard or above**: has anything been seen in-engine or in-motion, not
  only beauty renders? A render says nothing about topology, budgets, or
  whether it runs.
- **Hero / critical-path only**: is a paid test asset planned before
  committing to the full scope? Never an unpaid one — an unpaid test
  selects for the studios with the least other work, which is the opposite
  of what a hero asset needs.

If none of this has happened yet, flag it — "new partner, not yet vetted for
this criticality level" — and let the requester decide whether to proceed,
slow down, or route it to whoever owns vendor vetting.

## Step 5 — Confirm, Then Assemble

Before producing the final sheet, show a short recap so the requester can
correct anything cheaply:

```
📋 QUICK RECAP — confirm before I finalize:

Asset: [type, count, unit definition]
Criticality: [hero/critical-path / standard / background]
Vendor: [assigned / recommended / needs assignment — new partner? vetted?]
Starting material: [status + approval]
Phases: [list, confirmed by requester]
Due: [date(s)]
Style authority / Approval owner: [name / name, or "same person"]
Cost/timeline process: [in place / not yet established]
Commercial terms: [covered by existing SOW / gaps flagged]

🔶 Flags: [anything underspecified — no "good" reference, unapproved concept,
   unassigned or unvetted vendor, no cost/timeline process, commercial gaps,
   etc.]
```

Wait for confirmation or corrections before producing the full sheet below.

## Step 6 — Output: Asset Request Sheet

```markdown
# 📋 Asset Request — [Asset name / batch name]

**Requested by:** [name]  |  **Date:** [date]  |  **Status:** Draft

## Scope
- Asset type(s):
- Quantity, and what counts as one:
- Batch (shared style) or distinct assets:
- Criticality: [hero/critical-path / standard / background]

## Vendor
- [Assigned name] / [Recommended candidates + rationale] /
  🔶 Needs assignment — route to [outsource manager / art director]
- New partner? [yes/no] — if yes: lead + availability confirmed [y/n],
  in-engine proof seen [y/n], paid test planned [y/n/not applicable]

## Starting Material
- What exists: [nothing / napkin sketch / rough concept / approved concept]
- Approval status: [approved by X on Y / not yet approved / n/a]
- Files: [path, or 📎 placeholder — paste in when ready]

## Target Quality — Final
- Quick read: [2-4 sentence condensed style capture]
- Full interpretation: [deep style capture, if references were provided]
- Reference images: [📎 placeholder]

## Delivery Phases
| Phase | What "good" looks like here | Reference | Due | Reviewer |
|---|---|---|---|---|
| ... | ... | 📎 placeholder | ... | ... |

## Roles
- Style authority (final word on the look): [name]
- Approval owner (can say yes procedurally): [name — same as above, or different]
- Other reviewers, by phase (if applicable): [names]

## Cost & Timeline Process
- Estimate exists: [yes — from vendor/budget/gut sense / not yet established]
- "A day/week" defined (hours, review time included, single or multi-artist): [y/n]
- Revision allowance stated with the price: [y/n]
- Cost of a change named before there is one: [y/n]
- Flag: [none / "no process established yet"]

## Commercial Terms (lightweight check, not a contract)
- Payment trigger agreed: [y/n/n-a — covered by existing SOW]
- Change-order rule agreed: [y/n/n-a]
- IP / credit / portfolio rights understood: [y/n/n-a]

## File Delivery
- Destination: [path, or 📎 placeholder]
- Naming convention: [if specified]

## Open Risks / Flags
- [e.g. "No final reference provided — high rework risk," "Vendor unassigned,"
  "Concept not yet approved by X," "No cost/timeline process established,"
  "New partner not yet vetted for this criticality level"]
```

Always keep the **Open Risks / Flags** section even if it's short — a clean
"no flags" is useful signal too, not just a place to note problems.

If a Notion, Airtable, or similar destination is connected and the requester
wants this tracked there rather than (or in addition to) a standalone
document, offer to push it — but confirm before writing anything to an
external system. Default to producing the document itself; pushing it
somewhere is a follow-up action, not an assumption.

## Quality Standards

- **Never silently apply a phase template** — always surface it as a
  question, not a default.
- **Recognize already-satisfied phases** — if the starting material already
  includes an approved example for a phase, mark it satisfied rather than
  re-asking for a reference that already exists.
- **Undefined "good" gets flagged, not filled in** — don't invent a quality
  bar the requester didn't give you.
- **Undefined cost/timeline process or commercial terms get flagged, not
  gated** — a missing process is a line in Open Risks, exactly like an
  undefined quality bar. It never blocks the intake, and it's never
  contingent on whether a vendor has been assigned — a confirmed vendor
  with no process is just as much a gap as an unassigned one.
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
- **Placeholders over blocking** — missing file paths or images shouldn't
  stall the intake; leave a clear 📎 placeholder and move on.
- **Style capture is lightweight by design** — this isn't art-brief. Offer
  the handoff for anything that needs full art-direction treatment rather
  than trying to replicate it inline.
- **Vendor lookup degrades gracefully** — no configured database is a normal
  case, not an error. Flag and move on.

## Companion Skills

- **art-brief** — full vendor-brief-grade visual direction document (IP
  extraction, priority-weighted requirements, scope boundaries, generation
  prompts). Offer as a handoff for complex or high-stakes asks; don't
  invoke by default.
- **image-decomp** — if reference images need deeper structured analysis
  than the lightweight Style Capture in Step 3 provides, this can feed richer
  input into that step.
- Any Notion/Airtable/vendor-database routing skill already configured in
  the environment — this skill uses it automatically via Step 4, no direct
  integration needed.

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
