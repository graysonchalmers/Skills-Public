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

*(For this demo, assuming: Sarah reviews both phases; no separate rough-pass
reference needed — icons are simple enough that final-quality review on the
4-icon batch is sufficient.)*

---

## 📋 QUICK RECAP — confirm before finalizing

```
Asset: 12 UI icons (crafting update), batch — shared style
Vendor: IconForge (assigned, prior relationship)
Starting material: existing 40-icon set + Figma style guide (approved,
  satisfies final-quality reference — no need to re-request)
Phases: Phase 1 (4 icons, review) -> Phase 2 (remaining 8, final)
Due: Phase 1 - next Friday | Full set - end of month
Reviewers: Sarah (both phases)

🔶 Flags: none — style reference already exists and is approved, vendor
  is known, timeline and destination are both clear.
```

---

## OUTPUT — 📋 Asset Request Sheet

# 📋 Asset Request — Crafting Update Icon Batch (12 icons)

**Requested by:** Sarah  |  **Date:** [demo date]  |  **Status:** Draft

## Scope
- Asset type(s): UI / Icon
- Quantity: 12
- Batch (shared style) or distinct assets: Batch — shared style with
  existing 40-icon set

## Vendor
- IconForge — assigned, prior relationship (2nd/3rd engagement)

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

## File Delivery
- Destination: `/assets/ui/icons/crafting/`
- Naming convention: [not specified — 📎 confirm with vendor before delivery,
  likely matches existing icon naming pattern]

## Open Risks / Flags
- None significant — known vendor, approved style reference already exists,
  clear phased timeline and destination. Low-risk request.
