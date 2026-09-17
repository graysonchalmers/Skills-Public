# Example 1 — PROP brief, new vendor, IP borrow/avoid

**Synthetic user input:**

> Need an art brief for a legendary greatsword called "Duskfall" for our
> souls-like action RPG. Think Bloodborne's Saw Cleaver for the transforming
> mechanic, and Elden Ring's Golden Order weapons for the ornate gold
> filigree — but our world isn't gothic horror or high fantasy, it's a
> sun-scorched dying empire, more desert-baroque. Going to a vendor we
> haven't worked with before. Need it delivered as FBX + 4K Substance
> textures for Unreal 5.

---

## 📋 BRIEF ASSUMPTIONS — confirmed for this demo

⚠️ **Asset Type:** PROP (weapon)
⚠️ **Project Context:** Souls-like action RPG, "sun-scorched dying empire" —
desert-baroque aesthetic, not the more common gothic-horror or high-fantasy
default for this genre
⚠️ **Target Audience:** New vendor, first brief — precise, no assumptions,
full style bible references included
⚠️ **Art Style Direction:** Ornate, sun-bleached ceremonial weaponry that
still reads as lethal — baroque gold filigree over sand-worn steel, not
polished/pristine
⚠️ **Delivery Format:** FBX + 4K Substance Painter textures, Unreal 5 PBR
pipeline

🔴 **Priority Flags:** The transforming silhouette (sealed vs. unsealed
state) must read as two distinct, equally strong shapes — this is the
weapon's core gameplay hook, not just a visual flourish.

🚩 **Concerns:** None — references don't conflict; both borrowed qualities
target mechanism and ornamentation, not palette, so the desert-baroque
palette direction sits cleanly on top of both.

---

## OUTPUT BLOCK 1 — 📄 Art Direction Document

### 🎯 Project Context
- **Project:** *Duskfall* (working title) — souls-like action RPG, PC/console
- **Art style:** Desert-baroque — ceremonial imperial weaponry left to bake
  in the sun for a thousand years; ornamentation intact, function still lethal
- **Tone/mood:** Faded grandeur, sun-scorched, ceremonial-turned-feral,
  imperial decay

### 🎨 Visual Language
- **Palette:** `#C9A15C` (aged gold primary), `#8B4A2B` (oxidized bronze
  shadow), `#E8D9B5` (bone-sand accent), `#2B1F14` (deep shadow crevice),
  `#D64545` (blood-rust highlight, unsealed state only)
- **Lighting:** Hard overhead desert sun, high-contrast rim light on gold
  edges
- **Edge style:** Ornate filigree edges sharp and clean where gold survives;
  base steel edges pitted and irregular
- **Texture density:** High — this is a hero prop, hold up in close-up
  inventory/inspection views
- **Shading model:** PBR, metal/rough workflow

### 📐 Technical Spec
- **Deliverable:** FBX (game-ready + high-poly bake source), 4K Substance
  Painter texture set (Base Color, Normal, ORM)
- **Polycount target:** ≤18K tris game-res; unlimited high-poly for baking
- **LOD:** LOD0 (hero) + LOD1 (mid-range) required; LOD2 optional

### 🧭 Artistic References

```
IP: Bloodborne — Saw Cleaver
✅ Borrow: the two-state transforming mechanic — a compact "sealed" form
   that unfolds into a longer, more aggressive silhouette
❌ Avoid: the gothic-horror material language (blackened iron, cloth wrap,
   blood grime) — this is not our world's palette or material story
🎯 Target: proves the transform reads instantly in gameplay, at speed,
   from a third-person camera

IP: Elden Ring — Golden Order weapons (e.g. Marika's / Radagon's weapons)
✅ Borrow: ornate gold filigree engraving over the blade and guard,
   ceremonial-religious iconography worked into functional geometry
❌ Avoid: the pristine, unweathered "divine" finish — ours has centuries of
   sun and sand damage, not immaculate holy shine
🎯 Target: establishes the ornamentation language and how gold sits against
   base metal
```

### 🔴🟡🟢 Priority-Weighted Requirements
- 🔴 Sealed and unsealed silhouettes must both read clearly and distinctly
  at gameplay camera distance
- 🔴 Gold filigree must look inlaid/engraved into the steel, not applied as
  a decal or flat texture overlay
- 🟡 Prefer visible sand/wear accumulation in recessed filigree grooves
- 🟡 Unsealed state should introduce the blood-rust accent color as the
  weapon "activates"
- 🟢 A worn engraving fragment hinting at imperial iconography would be a
  nice easter-egg detail, not required for approval

### ⛔ Explicit Avoids
- Do not use gothic-horror material language (blackened iron, cloth
  wrapping, grime/blood-soaked cloth)
- Avoid pristine/unweathered "holy" gold — this is a decayed empire, not an
  active religious order
- No glowing rune lines — the unsealed state uses color/form change, not
  emissive VFX (VFX team owns any particle/glow pass separately)
- Do not reference Bloodborne's transform *mechanism aesthetic* (the visible
  gear/mechanism at the fold point) — ours should look more like a ceremonial
  unfolding, not industrial machinery

### 📅 Delivery & Milestones
```
MILESTONE STRUCTURE
───────────────────
M1 — Concept sketches (2-3 silhouette options, both states): 1 week
M2 — Refined concept (1 selected direction, both states, colored): 1 week
M3 — Blockout (game-res mesh, both states, no textures): 1 week
M4 — Final Asset (textured, both states, LOD0+LOD1): 2 weeks

Revision rounds per milestone: 2
Feedback turnaround: 2 business days
```

---

## OUTPUT BLOCK 2 — 📬 Vendor Brief

*Duskfall* is a souls-like action RPG set in a sun-scorched dying empire —
desert-baroque, not gothic-horror or high-fantasy. This brief covers
"Duskfall," a legendary transforming greatsword and one of our hero props.

**Key requirements:**
- 🔴 Two-state transforming weapon — sealed and unsealed forms must each
  read as a strong, distinct silhouette at gameplay camera distance
- 🔴 Gold filigree engraved/inlaid into base steel, not decaled on top
- 🟡 Sand/wear buildup in recessed engraving grooves
- 🟡 Blood-rust accent color (`#D64545`) introduced only in the unsealed state

**References:**
```
IP: Bloodborne — Saw Cleaver
✅ Borrow: two-state transforming mechanic, compact → aggressive silhouette
❌ Avoid: gothic-horror material language (blackened iron, cloth, grime)

IP: Elden Ring — Golden Order weapons
✅ Borrow: ornate gold filigree over functional geometry
❌ Avoid: pristine/unweathered "divine" finish
```

**Explicit avoids:** gothic-horror materials, pristine holy gold, glowing
rune VFX, visible mechanical transform hardware.

**Deliverables:** FBX (game-res ≤18K tris + high-poly bake source), 4K
Substance Painter texture set (Base Color/Normal/ORM), LOD0 + LOD1.

**Milestones:** Concept (1wk) → Refined concept (1wk) → Blockout (1wk) →
Final (2wk). 2 revision rounds/milestone, 2-day feedback turnaround.

Please reach out if you have questions or need clarification on any point.

---

## OUTPUT BLOCK 3 — 🤖 Generation Prompts

**Midjourney:**
> ornate ceremonial greatsword, desert-baroque design, engraved gold
> filigree inlaid into sun-bleached pitted steel, imperial iconography
> worn by centuries of sand, hard overhead desert sunlight, high contrast
> rim light on gold edges, weapon concept art, game asset render
> --ar 2:3 --s 250 --v 6

**DALL-E / GPT-Image:**
> A weapon concept art render of an ornate, sun-scorched ceremonial
> greatsword called "Duskfall," blending the ornate gold filigree
> engraving of Elden Ring's Golden Order weapons with the compact,
> two-state transforming silhouette of Bloodborne's Saw Cleaver — but
> reimagined for a desert-baroque dying empire rather than gothic horror
> or high fantasy. Sun-bleached pitted steel base, gold inlay worn by sand
> and time, hard directional desert light, PBR game-asset quality render
> on a neutral studio background.

**Stable Diffusion:**
> ornate greatsword, desert-baroque, gold filigree inlay, sun-bleached
> steel, sand-worn engraving, imperial iconography, transforming weapon,
> pitted metal texture, hard rim lighting, PBR render, weapon concept art,
> game asset
> Negative: gothic, blackened iron, cloth wrap, blood grime, glowing runes,
> pristine polish, fantasy generic
