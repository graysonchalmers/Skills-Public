# Example 1 — Extraction mode (dense forwarded request)

**Synthetic user input:**

> hey can you help me intake this — Sarah just sent me this in Slack:
> "need 12 inventory icons for the crafting update, same style as our
> existing 40 icons (style guide is in Figma, link below), vendor is
> IconForge (we've used them twice before), first batch of 4 needed by
> next Friday for review, I'll sign off on those before the rest,
> full set due end of month, delivery to /assets/ui/icons/crafting/"

---

## 🔍 Parsed automatically from the message

- **Asset type:** UI (icon batch)
- **Criticality:** background/low-stakes — extending an already-shipped
  icon set, not a hero asset
- **Quantity:** 12, batch (shared style, not distinct assets)
- **Vendor:** IconForge — named, trusted (used twice before)
- **Starting material:** existing 40-icon set + Figma style guide — this
  **satisfies** the "final quality reference" requirement already
- **Delivery phases (implied):** first-4 review batch → remaining 8
- **Timeline:** first 4 by next Friday, full set end of month
- **File path:** `/assets/ui/icons/crafting/`

Got it — sounds like this is a 12-icon batch matching your existing style
guide, IconForge again, phased 4-then-8. A couple more things I need before
I can finalize the sheet:

## 📋 Gaps — only what's missing

1. **Reviewer** — who signs off on the first-4 batch, Sarah or someone else?
2. **Per-phase reference** — the Figma style guide covers final quality; is
   there also a reference for what "good" looks like at a rougher pass
   (e.g. line-art only), or should the first-4 batch just be judged against
   final quality directly since these are simple icons?
3. **Cost/timeline process** — with IconForge on their third engagement, is
   there already a standing rate/turnaround understanding, or does this
   need a fresh check?

*(For this demo, assuming: Sarah reviews both phases as both style
authority and approval owner — same person, low-stakes batch; no separate
rough-pass reference needed; and yes, a standing arrangement from the prior
two engagements already covers day definition and revision allowance, so
no new cost/timeline process needed here.)*

---

## 📋 QUICK RECAP — confirm before finalizing

```
Asset: 12 UI icons (crafting update), batch — shared style
Criticality: background/low-stakes
Vendor: IconForge (assigned, prior relationship)
Starting material: existing 40-icon set + Figma style guide (approved,
  satisfies final-quality reference — no need to re-request)
Phases: Phase 1 (4 icons, review) -> Phase 2 (remaining 8, final)
Due: Phase 1 - next Friday | Full set - end of month
Style authority / Approval owner: Sarah (both roles, same person)
Cost/timeline process: in place — standing arrangement from prior engagements
Commercial terms: covered by existing vendor relationship, not re-litigated

🔶 Flags: none — style reference already exists and is approved, vendor
  is known and vetted from two prior engagements, timeline and destination
  are both clear.
```

---

## OUTPUT — 📋 Asset Request Sheet

# 📋 Asset Request — Crafting Update Icon Batch (12 icons)

**Requested by:** Sarah  |  **Date:** [demo date]  |  **Status:** Draft

## Scope
- Art brief of record: **Unresolved — no brief on file** [not supplied]; full art-direction treatment available via the art-brief handoff, offered not invoked.
- Asset type(s): UI / Icon
- Quantity, and what counts as one: 12 individual icons
- Batch (shared style) or distinct assets: Batch — shared style with
  existing 40-icon set
- Criticality: background/low-stakes

## Vendor
- IconForge — assigned, prior relationship (2nd/3rd engagement)
- New partner? No — third engagement, no vetting bar to apply

## Starting Material
- What exists: existing 40-icon set + Figma style guide
- Approval status: approved (existing production style guide)
- Files: Figma style guide — [link placeholder 📎]

## Target Quality — Final
- Quick read: Match the existing 40-icon set's line weight, palette, and
  grid exactly — these 12 are an extension of an already-shipped set, not
  a new style.
- Full interpretation: n/a — style guide + existing shipped icons already
  fully define the target; no additional interpretation needed
- Reference images: existing 40-icon set + Figma style guide 📎

## Delivery Phases
| Phase | What "good" looks like here | Reference | Due | Reviewer |
|---|---|---|---|---|
| Phase 1 — First 4 icons | Final quality, matching existing set | Figma style guide + existing 40 icons | Next Friday | Sarah |
| Phase 2 — Remaining 8 icons | Final quality, matching approved Phase 1 icons | Approved Phase 1 icons + style guide | End of month | Sarah |

## Roles
- Style authority (final word on the look): Sarah
- Approval owner (can say yes procedurally): Sarah — same as above

## Cost & Timeline Process
- Estimate exists: yes — standing arrangement from prior engagements
- "A day/week" defined: yes (established in prior engagements)
- Revision allowance stated with the price: yes
- Cost of a change named before there is one: yes
- Flag: none

## Commercial Terms (lightweight check, not a contract)
- Payment trigger agreed: yes — covered by existing vendor relationship
- Change-order rule agreed: yes
- IP / credit / portfolio rights understood: yes

## File Delivery
- Destination: `/assets/ui/icons/crafting/`
- Naming convention: [not specified — 📎 confirm with vendor before delivery,
  likely matches existing icon naming pattern]

## Open Risks / Flags
- None significant — known vendor, approved style reference already exists,
  clear phased timeline and destination. Low-risk request.
