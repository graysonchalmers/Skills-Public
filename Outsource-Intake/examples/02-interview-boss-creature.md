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

**Q:** Criticality — hero/critical-path, standard, or background?
**A:** Hero — a boss on the critical path for the swamp biome milestone.
This calibrates how much rigor the rest of the intake and vendor vetting
gets: full weight, not the light-touch version.

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

**Q7 — Cost/timeline reality check:** Is there a process for sanity-checking
whatever estimate comes back — a defined "day," a stated revision
allowance, a named change cost?
**A:** No — first boss for the project, no existing rate arrangement or
process to check against yet. Flagging as a gap. This is independent of
the vendor being unassigned — it would still be a gap even with a vendor
picked.

**Q8 — Commercial readiness:** Payment trigger, change-order rule, IP/credit
terms — agreed anywhere, even a standard studio SOW?
**A:** Unknown — likely covered by a standard studio SOW but not confirmed
for this specific engagement. Flagging lightly, not blocking on it.

**Q9 — Style authority and approval owner:** Who's the final word on the
look, and who can procedurally say yes — same person or different?
**A:** Style authority is the Art Director throughout. Approval owner is
the Art Director alone for concept and blockout, and the Art Director
*plus* Lead Designer jointly for final and the animation test — design
needs to confirm readability there, not just visual quality. Naming both
roles even though they overlap for most of the timeline, so it's on record
if a review ever splits.

**Q10 — File paths:** Where should this land?
**A:** Not settled yet — leaving a placeholder.

---

## 📋 QUICK RECAP — confirm before finalizing

```
Asset: 1 creature (boss, corrupted temple guardian)
Criticality: hero/critical-path
Vendor: needs recommendation — no database connected, route to outsource
  manager or art director; hero criticality means the full new-partner
  vetting bar applies once one's identified (named lead + availability,
  in-engine proof, a paid test asset before full commitment)
Starting material: one-line design pitch only, no sketch/concept
Phases: Concept -> Blockout -> Final texture -> Animation test (added by
  requester)
Due: 6 weeks overall, per-phase dates TBD by vendor
Style authority / Approval owner: AD (style, throughout) | AD alone
  (concept, blockout) -> AD + Lead Designer (final, anim test)
Cost/timeline process: not established
Commercial terms: unknown — likely standard SOW, not confirmed

🔶 Flags: no final-quality reference exists yet (first boss/first creature
  for this project — real rework risk); no per-phase references either;
  vendor unassigned and, once picked, unvetted for hero criticality; no
  cost/timeline process established; commercial terms unconfirmed; file
  destination unsettled.
```

---

## OUTPUT — 📋 Asset Request Sheet

# 📋 Asset Request — Corrupted Temple Guardian (Boss Creature)

**Requested by:** AI Team  |  **Date:** [demo date]  |  **Status:** Draft

## Scope
- Asset type(s): Creature (boss enemy)
- Quantity, and what counts as one: 1 — a fully textured, rigged,
  animation-tested boss creature
- Batch (shared style) or distinct assets: n/a — single asset
- Criticality: hero/critical-path

## Vendor
- 🔶 Needs assignment — route to outsource manager or art director. No
  vendor database configured in this environment to search automatically.
- New partner? Yes, by default (unassigned) — hero criticality means the
  full vetting bar applies once a candidate exists: named lead + confirmed
  availability, in-engine/in-motion proof (not just beauty renders), and a
  paid test asset before committing to full scope.

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

## Roles
- Style authority (final word on the look): Art Director
- Approval owner (can say yes procedurally): Art Director (concept,
  blockout); Art Director + Lead Designer jointly (final, animation test)

## Cost & Timeline Process
- Estimate exists: not yet established
- "A day/week" defined: n/a — no estimate yet
- Revision allowance stated with the price: n/a
- Cost of a change named before there is one: n/a
- Flag: "no process established yet" — first engagement of this kind for
  the project, independent of the vendor gap above

## Commercial Terms (lightweight check, not a contract)
- Payment trigger agreed: unknown — likely standard SOW, not confirmed
- Change-order rule agreed: unknown
- IP / credit / portfolio rights understood: unknown

## File Delivery
- Destination: 📎 placeholder — not yet settled

## Open Risks / Flags
- 🔶 No final-quality reference exists — first boss creature for the
  project. High rework risk; strongly recommend a quick internal
  mood-board or 2-3 reference IPs before this goes to a vendor.
- 🔶 No per-phase references either, for the same reason.
- 🔶 Vendor unassigned — needs outsource manager or art director input.
  Once assigned, this is hero criticality: apply the full new-partner
  vetting bar, including a paid test asset, before committing to full scope.
- 🔶 No cost/timeline process established yet — flagged as a process gap,
  not tied to whether a vendor is picked.
- 🔶 Commercial terms (payment trigger, change-order rule, IP/portfolio
  rights) unconfirmed for this specific engagement — likely covered by a
  standard SOW, worth a quick check before kickoff.
- 🔶 File delivery destination not yet settled — placeholder left in place
  rather than blocking the intake.
