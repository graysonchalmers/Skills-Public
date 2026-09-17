# Example 2 — Interview mode (bare trigger, full Q&A)

**Synthetic user input:**

> Someone on the AI team just asked me for a boss creature. Help me intake it.

No details given — running the full question flow from scratch.

---

## Step 1 — Classify the Ask

**Q:** What's the asset — character, prop, environment, creature, VFX, UI,
key art, scene comp, or physical?
**A (synthetic):** Creature — a boss enemy.

**Q:** Single asset, or part of a batch?
**A:** Single asset.

## Step 2 — Core Intake Questions

**Q1 — Vendor:** Named vendor, or need a recommendation?
**A:** No vendor picked yet, need a recommendation.

*(No vendor database connected in this environment — flagging per Step 4's
degrade-gracefully rule rather than guessing.)*

**Q2 — Starting material:** What exists today — nothing, napkin sketch,
rough concept, polished concept, or fully approved concept?
**A:** Nothing yet — just a one-line pitch from design: "a corrupted temple
guardian, stone-and-vine boss, mid-game difficulty spike."

**Q3 — Reference for "good" (final):** Any example images, files, or style
guide showing the target quality for the finished asset?
**A:** No — this is the first boss in the game, no existing style guide for
creatures yet.

*(Flagging this directly: an undefined final target is the single biggest
cause of rework — worth being explicit about with the requester before this
goes anywhere.)*

**Q4 — Delivery phases:** What stages do you want to review before final?

Pulling the closest template — this is a creature, so offering the
standard concept → blockout → final pass structure rather than applying it
silently:

> Suggested phases: (1) Concept sketches, (2) Sculpt/blockout, (3) Final
> textured asset. Want to keep this, cut a stage, or add one (e.g. a
> separate rigging/animation-ready pass)?

**A:** Keep it, but add a 4th phase for a basic idle/attack animation test
before calling it done — this is a boss, animation readability matters.

**Q5 — Reference for "good" (per phase):** For each phase, is there an
example of what good looks like at that stage specifically?
**A:** No per-phase references either — first creature for this project.

**Q6 — Timeline:** Overall due date, and per-phase if phased?
**A:** Overall due in 6 weeks. No fixed per-phase dates yet — asking the
vendor to propose a schedule once assigned.

**Q7 — Reviewers:** Who signs off, and does it change by phase?
**A:** Art director reviews concept and blockout; art director + lead
designer both review final and the animation test (design needs to confirm
readability, not just visual quality).

**Q8 — File paths:** Where should this land?
**A:** Not settled yet — leaving a placeholder.

---

## 📋 QUICK RECAP — confirm before finalizing

```
Asset: 1 creature (boss, corrupted temple guardian)
Vendor: needs recommendation — no database connected, route to outsource
  manager or art director
Starting material: one-line design pitch only, no sketch/concept
Phases: Concept -> Blockout -> Final texture -> Animation test (added by
  requester)
Due: 6 weeks overall, per-phase dates TBD by vendor
Reviewers: AD (concept, blockout) | AD + Lead Designer (final, anim test)

🔶 Flags: no final-quality reference exists yet (first boss/first creature
  for this project — real rework risk); no per-phase references either;
  vendor unassigned; file destination unsettled.
```

---

## OUTPUT — 📋 Asset Request Sheet

# 📋 Asset Request — Corrupted Temple Guardian (Boss Creature)

**Requested by:** AI Team  |  **Date:** [demo date]  |  **Status:** Draft

## Scope
- Asset type(s): Creature (boss enemy)
- Quantity: 1
- Batch (shared style) or distinct assets: n/a — single asset

## Vendor
- 🔶 Needs assignment — route to outsource manager or art director. No
  vendor database configured in this environment to search automatically.

## Starting Material
- What exists: one-line design pitch — "a corrupted temple guardian,
  stone-and-vine boss, mid-game difficulty spike"
- Approval status: n/a — pitch only, not yet a concept
- Files: none yet 📎

## Target Quality — Final
- Quick read: 🔶 **Undefined** — this is the first boss creature for the
  project, no existing style guide or reference to anchor "good." Flagging
  directly: this is the single biggest rework risk on this request.
- Reference images: none 📎

## Delivery Phases
| Phase | What "good" looks like here | Reference | Due | Reviewer |
|---|---|---|---|---|
| 1 — Concept sketches | 🔶 undefined — first creature, no reference | 📎 placeholder | TBD by vendor | Art Director |
| 2 — Sculpt / blockout | 🔶 undefined | 📎 placeholder | TBD by vendor | Art Director |
| 3 — Final textured asset | 🔶 undefined | 📎 placeholder | TBD by vendor | AD + Lead Designer |
| 4 — Idle/attack animation test | Readability of boss "tells" at gameplay speed | 📎 placeholder | TBD by vendor | AD + Lead Designer |

## File Delivery
- Destination: 📎 placeholder — not yet settled

## Open Risks / Flags
- 🔶 No final-quality reference exists — first boss creature for the
  project. High rework risk; strongly recommend a quick internal
  mood-board or 2-3 reference IPs before this goes to a vendor.
- 🔶 No per-phase references either, for the same reason.
- 🔶 Vendor unassigned — needs outsource manager or art director input.
- 🔶 File delivery destination not yet settled — placeholder left in place
  rather than blocking the intake.
