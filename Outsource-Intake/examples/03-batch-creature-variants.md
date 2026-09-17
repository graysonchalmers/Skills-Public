# Example 3 — Batch ask, distinct variants (style-lock before scaling)

**Synthetic user input:**

> Need 3 enemy creature variants for the new swamp biome — same base
> creature (a bog-lurker), but a basic version, an elite version with bone
> armor plating, and a rare "alpha" version that's bigger with a
> bioluminescent underbelly. We have concept art for the basic version
> already, approved. No vendor picked yet. Need the elite and alpha
> within 3 weeks of the basic being locked. Sam reviews everything.

---

## Step 1 — Classify the Ask

- **Asset type:** Creature
- **Batch or distinct:** Batch, but **distinct variants of one base
  creature** rather than unrelated assets — this changes the phase
  structure: the basic version needs to lock the style FIRST, and the
  elite/alpha variants scale from that locked style rather than each
  going through their own full concept phase.

## Step 2 — Core Intake Questions

1. **Vendor** — none picked yet, needs recommendation. No vendor database
   connected in this environment — flagging per the standard degrade path.
2. **Scope** — confirmed: 3 variants of one base creature (bog-lurker).
3. **Starting material** — approved concept art exists **for the basic
   variant only**. Elite and alpha have no concept yet.
4. **Reference for "good" (final)** — the approved basic concept satisfies
   the final-quality bar for that one variant. Elite and alpha still need
   their own reference once the basic's sculpt/texture treatment is locked,
   since they scale off it rather than starting fresh.
5. **Delivery phases** — proposing a style-lock structure since this is a
   variant batch:
   > Phase 1: Basic variant — blockout → final (style-lock for the whole
   > set). Phase 2: Elite variant — scales from locked basic + adds bone
   > armor. Phase 3: Alpha variant — scales from locked basic + size
   > increase + bioluminescent underbelly.
   Confirmed as-is by requester.
6. **Reference for "good" (per phase)** — basic variant's approved concept
   satisfies Phase 1. Elite and alpha phases will use the *locked Phase 1
   final asset* as their reference once it exists — marking that
   dependency explicitly rather than leaving it as a generic "no
   reference" flag.
7. **Timeline** — elite + alpha both due 3 weeks after basic locks; basic's
   own due date not yet set (assumed ASAP since it gates the other two).
8. **Reviewers** — Sam, all phases.
9. **File paths** — not settled yet, placeholder.

---

## 📋 QUICK RECAP — confirm before finalizing

```
Asset: 3 creature variants (bog-lurker: basic, elite, alpha), batch —
  shared base creature, not distinct designs
Vendor: needs recommendation — no database connected
Starting material: approved concept for basic variant only
Phases: Basic (style-lock) -> Elite (scales from locked basic) ->
  Alpha (scales from locked basic)
Due: Elite + Alpha - 3 weeks after basic locks | Basic - date TBD
Reviewers: Sam (all phases)

🔶 Flags: basic variant's own due date isn't set yet, and it gates the
  other two — worth pinning down before vendor kickoff so "3 weeks after
  lock" has a real anchor date. Vendor unassigned.
```

---

## OUTPUT — 📋 Asset Request Sheet

# 📋 Asset Request — Bog-Lurker Variant Batch (3 creatures)

**Requested by:** [demo requester]  |  **Date:** [demo date]  |  **Status:** Draft

## Scope
- Asset type(s): Creature
- Quantity: 3 (Basic, Elite, Alpha)
- Batch (shared style) or distinct assets: Batch — shared base creature,
  variants scale from a locked style rather than each starting fresh

## Vendor
- 🔶 Needs assignment — no vendor database configured in this environment.

## Starting Material
- What exists: approved concept art for the Basic variant only
- Approval status: Basic — approved. Elite/Alpha — not started, scale
  from Basic once it's locked in production
- Files: Basic concept art 📎

## Target Quality — Final
- Quick read: Basic variant's approved concept sets the final-quality bar
  for the whole set; Elite and Alpha inherit its sculpt/texture treatment
  and add their own defining features on top (bone armor / size +
  bioluminescence).
- Reference images: Basic concept art 📎ᐧ Elite/Alpha references pending
  Basic lock

## Delivery Phases
| Phase | What "good" looks like here | Reference | Due | Reviewer |
|---|---|---|---|---|
| 1 — Basic (style-lock) | Matches approved concept exactly — this locks the shared base for the other two | Approved Basic concept | 🔶 not yet set — gates Phases 2-3 | Sam |
| 2 — Elite | Locked Basic sculpt/texture + bone armor plating | Locked Phase 1 final asset | 3 weeks after Phase 1 locks | Sam |
| 3 — Alpha | Locked Basic sculpt/texture + size increase + bioluminescent underbelly | Locked Phase 1 final asset | 3 weeks after Phase 1 locks | Sam |

## File Delivery
- Destination: 📎 placeholder — not yet settled

## Open Risks / Flags
- 🔶 Basic variant's own due date isn't pinned down yet, and it gates
  Phases 2-3's "3 weeks after lock" timeline — recommend setting a firm
  Basic due date before vendor kickoff so downstream dates have a real
  anchor.
- 🔶 Vendor unassigned — needs outsource manager or art director input.
