# Phase Templates by Asset Type

These are **suggestions to offer during intake**, not assumptions to apply
silently. Always show the relevant template to the requester and ask them to
confirm, cut, add, or reorder phases — different studios, vendors, and
projects split work differently. The value of these templates is speeding up
the question, not skipping it.

Format per phase: **Phase name** — what "good" typically means at that stage
(the thing a reviewer should actually be checking for, not surface polish
that belongs to a later phase).

---

## CHARACTER / CREATURE (3D)

1. **Blockout** — proportions, silhouette, scale relative to reference (e.g.
   a doorway, a held weapon). No detail. Good = "if I squint, I know what
   this is and it's the right size."
2. **High Poly / Sculpt** — form, volume, major surface detail, silhouette
   read from all key angles. Good = holds up as a render, not just a shape.
3. **Low Poly / Retopo** — clean topology, correct poly budget, deforms well
   if it will be rigged. Good = no visible faceting on silhouette, edge flow
   supports animation.
4. **UVs** — no stretching, sensible texel density, seams hidden in natural
   breaks. Good = a texture painted on this won't visibly distort.
5. **Texture / Materials** — palette match, material read (metal reads as
   metal), matches the approved style reference. Good = matches "final"
   reference at a glance.
6. **Rig / Animation** (if applicable) — deformation quality at range of
   motion, no pinching or volume loss.
7. **Final In-Engine Tweak** — reads correctly under actual game lighting,
   LOD pop-in behavior, material setup finalized. Good = looks like the
   reference *in the game*, not just in a turntable render.

## PROP (3D)

Same as Character/Creature minus rigging, often collapsed to fewer review
gates for simple props:
1. **Blockout** — scale and silhouette
2. **High Poly** (skip for simple hard-surface props if not needed)
3. **Low Poly / UVs / Texture** — often reviewed as one combined pass for
   small props
4. **Final In-Engine Tweak** — placement, scale, and material read in context

## ENVIRONMENT / SCENE

1. **Greybox / Blockout** — spatial layout, scale, sightlines, gameplay
   flow if applicable. Good = navigable and readable, zero detail.
2. **Lighting Pass (rough)** — mood and readability established early;
   lighting drives a huge amount of perceived quality and is cheap to
   iterate on before detail work.
3. **Asset Population (rough)** — placeholder or early-pass props/set
   dressing in place to judge density and composition.
4. **Detail / Hero Asset Pass** — key set pieces brought to final quality.
5. **Final Lighting + Polish** — lighting finalized, atmosphere/fx layered
   in, performance pass if needed.

## VFX

1. **Reference / Concept** — timing and look defined via reference or
   storyboard, not yet built.
2. **Prototype** — rough simulation/timing in engine, silhouette and
   readability at a glance, no final art.
3. **First Pass** — final art direction applied, timing still rough.
4. **Polish** — timing, layering, and secondary motion refined.
5. **In-Engine Integration** — reads correctly against actual backgrounds,
   camera distances, and frame rate.

## UI

1. **Wireframe / Concept** — layout and information hierarchy, no visual
   style.
2. **Style Pass (1-2 exemplar screens)** — visual language established on a
   small sample before scaling to the full set. This is the highest-leverage
   review gate — catching a style problem here saves redoing dozens of
   assets later.
3. **Full Set Draft** — style applied across all screens/icons at once.
4. **Consistency / Polish Pass** — spacing, alignment, and state variants
   (hover, disabled, selected) checked across the whole set.
5. **Export / Spec Sheet** — assets sliced and delivered per platform spec.

## KEY ART / MARKETING

1. **Thumbnail / Comp Sketches** (usually 2-3 options) — composition and
   focal point only, no color or detail.
2. **Rough Color Comp** — value structure and color direction on the chosen
   thumbnail.
3. **Refined Comp** — near-final rendering, all major elements resolved.
4. **Final Polish / Retouch** — color correction, text/logo integration if
   applicable, output-format-specific adjustments.

## SCENE COMP / CUTSCENE FRAME

1. **Thumbnail** — composition and staging
2. **Rough Comp** — value structure, camera framing locked
3. **Value / Color Pass** — mood and lighting resolved
4. **Final Render / Comp** — full detail and post-processing

## PHYSICAL / FABRICATION

1. **Concept / Design** — form and dimensions on paper/CAD, materials
   specified.
2. **Maquette / Prototype** — small-scale or rough build to validate form
   and proportion before committing to final materials.
3. **Material Test** — sample of the actual finish/material on a test piece,
   especially important for paint, stain, or texture treatments.
4. **Build** — full-scale construction.
5. **Finish / Paint** — final surface treatment applied.

---

## Using these templates during intake

1. Identify asset type (Step 1 of the main skill).
2. Pull the matching template above.
3. Present it back to the requester as a starting point: *"For a
   [asset type], a typical phase breakdown looks like [list]. Does that
   match what you want reviewed, or do you want to add/cut/merge stages?"*
4. Record their actual answer — not the template — in the output. The
   template is scaffolding for the conversation, never a substitute for it.
5. If the asset type doesn't match any template above, skip straight to
   asking the requester to define their own phases from scratch.
