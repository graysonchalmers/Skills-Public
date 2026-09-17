# Example 3 — PHYSICAL/fabrication brief, internal team tone

**Synthetic user input:**

> I want to build a coffee table that looks like a topographic tide chart —
> walnut, with the "water" areas as a poured blue-green resin inlay showing
> depth contour lines routed into the wood before pouring. About 48"x28"
> tabletop, needs to actually hold weight (it's a real table, not just
> decorative). This is for my own house, not a client. I'll be building it
> myself in my garage shop.

---

## 📋 BRIEF ASSUMPTIONS — confirmed for this demo

⚠️ **Asset Type:** PHYSICAL (furniture / fabrication)
⚠️ **Project Context:** Personal build, functional coffee table
⚠️ **Target Audience:** Internal/self — direct, technical tone, can
reference maker-community shorthand (CNC, epoxy, etc.) without over-explaining
⚠️ **Art Style Direction:** Topographic tide chart aesthetic — routed
contour lines filled with tinted resin to read as depth bands, walnut as
the "land"
⚠️ **Delivery Format:** n/a (this is a personal build spec, not a vendor
deliverable) — brief instead functions as the maker's own build reference
⚠️ **Style Authority:** Grayson (self) — solo personal build, no second
opinion in the loop

🔴 **Priority Flags:** Structural load-bearing integrity is non-negotiable
— this is a real table, not a display piece, so the resin inlay pour depth
and wood removal depth must not compromise structural strength at the
tabletop's thinnest points.

🚩 **Concerns:** Deep contour routing near the tabletop edges risks
thinning the wood below a safe structural minimum — flagged as a
design constraint requiring a routing depth map before cutting, not
freehanded.

---

## OUTPUT BLOCK 1 — 📄 Art Direction Document

### 🎯 Project Context
- **Project:** personal build — topographic "tide chart" coffee table
- **Style:** functional furniture piece styled as a nautical depth chart —
  walnut "land" mass with routed, resin-filled depth contour lines
- **Tone/mood:** quiet, coastal, precise — a chart you'd actually navigate by

### 🎨 Visual Language
- **Palette:** natural walnut grain (warm brown, `#4A3324` base), resin
  bands from `#1B4B4A` (deepest water) lightening to `#7FB3AC` (shallows)
  as depth decreases, following real tide-chart convention (darker = deeper)
- **Surface treatment:** wood sanded/oiled to a satin (not glossy) finish;
  resin poured flush and polished to a higher gloss for contrast
- **Shading model:** n/a (physical object — finish sheen carries this role)

### PHYSICAL SPEC
```
Object type: coffee table (functional, load-bearing)
Fabrication method: CNC or hand-routed wood + poured epoxy resin inlay

Dimensions (L x W x H): 48in x 28in x 16in (standard coffee table height)
Weight target or constraint: table must support 50+ lbs distributed load
  without flex at center span
Material(s): walnut slab or edge-glued walnut panel (tabletop), hardwood
  legs/base (walnut or complementary species), 2-part clear/tinted epoxy
  resin for the water bands
Finish: hard-wax oil or satin polyurethane on wood; resin polished to gloss

Structural requirements: freestanding, load-bearing tabletop — routing
  depth must be mapped BEFORE cutting to guarantee minimum wood thickness
  (recommend no less than 40% of slab thickness remaining at any routed point)
Joinery / assembly method: breadboard ends or a torsion-box substrate
  recommended to counter warping from asymmetric resin pour
Tolerance: ±1/16in on contour routing for clean resin pour lines

Reference scale: 1:1 (functional full-size table)
Texture / surface treatment: satin wood finish, gloss resin finish (deliberate
  contrast between the two surface types)
Color: walnut natural grain; resin bands dark-to-light teal by depth,
  darkest at the deepest/widest contour, following real tide-chart shading

Environment: indoor, living-room use
```

### 🔴🟡🟢 Priority-Weighted Requirements
- 🔴 Structural integrity — no routed area may compromise load-bearing
  capacity; map routing depth before cutting, don't freehand near edges
- 🔴 Resin bands must follow true topographic convention (darker = deeper),
  not just aesthetic color choice — this is what sells the "chart" read
- 🟡 Satin wood / gloss resin finish contrast should be deliberate and
  visible, not accidental from inconsistent sanding
- 🟢 A single reference contour line etched with actual depth numbers
  (like a real chart) would be a nice authenticity detail

### ⛔ Explicit Avoids
- Do not rely on a single thin resin pour for a "river table" look running
  edge-to-edge — this is a full topographic field with multiple contour
  bands, not one channel
- Avoid glossy finish on the wood — the wood/resin finish contrast is part
  of the design language, not an oversight to fix later
- Do not skip the routing depth map — freehanding contour depth risks a
  structural failure that isn't visible until the table is under load

### 🚧 Scope Boundaries & Change Policy
- Out of scope in the vendor sense doesn't apply — no partner, no change
  orders. The real boundary is sequencing: the routing depth map is locked
  before any cut. Redesigning the contour layout after routing starts
  isn't a change, it's a redo — see the structural note above.

### 📋 Process
- n/a — solo build. Self-review at each stage of the sequence below stands
  in for a named reviewer and turnaround.

### 📅 Delivery & Milestones
*(Omitted — personal build, no vendor handoff. Use the Materials & Process
Note below as the working sequence instead.)*

---

## OUTPUT BLOCK 2 — 📬 Vendor Brief

*(Not applicable — this is a personal build. Skipping to the Materials &
Process Note, which replaces both the Vendor Brief and Generation Prompts
blocks for physical/fabrication builds per the skill's own routing rule.)*

---

## OUTPUT BLOCK 3 — 🧰 Materials & Process Note

**Sequence:**
1. Source/mill a walnut slab or edge-glue panel to 48"x28", flatten and
   surface both faces.
2. **Map the routing depth BEFORE cutting** — model the contour bands
   digitally (even a simple layered sketch) and confirm minimum remaining
   wood thickness at every routed point clears 40% of slab thickness.
3. Rout contour bands (CNC preferred for repeatable depth control; hand
   router with a depth-stop jig is workable if you're confident in the
   depth map).
4. Dam the perimeter of each routed band, tint 2-part epoxy in graduated
   teal shades (darkest for the deepest/widest band), pour in stages from
   deepest to shallowest to avoid bleed between colors.
5. Cure fully per resin manufacturer's schedule before sanding.
6. Flatten/sand the whole surface (wood + cured resin together) to bring
   both to one true plane, working up through grits.
7. Finish: hard-wax oil or satin polyurethane on the wood, then polish the
   resin bands separately to a higher gloss for the material contrast.
8. Attach to a torsion-box substrate or breadboard-end base to resist
   warping from the asymmetric resin pour before final assembly with legs.

**Tools/materials to have on hand:** CNC router or plunge router + edge
guide/depth-stop jig, dam material (silicone or tape) for the resin pour,
graduated epoxy tints, random-orbit sander through progressive grits,
digital scale for resin mixing ratios.
