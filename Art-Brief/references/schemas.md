# Asset-Type Reactive Schemas

Use the classification from Step 1A to select the relevant schema below.
Only include fields that are genuinely applicable. Omit rather than pad with
"N/A" or "TBD."

---

## Schema A — CHARACTER

```
CHARACTER SPEC
──────────────
Role: [hero / NPC / enemy / boss / companion / figurine]
Gender presentation & age range:
Body type & proportions: [stylized / realistic / exaggerated — specifics]
Silhouette priority: [describe the key readable shape]
Facial design language: [expressive / stoic / alien / etc.]

Costume / Armor:
- Primary material(s):
- Secondary material(s):
- Color blocking (which parts carry which palette colors):
- Wear & damage level: [pristine / worn / battle-damaged]
- Cultural / historical inspiration:

Hair / Head:
- Style:
- Key color(s):

Accessories & Props:
- [list any carried items, weapons, talismans, etc.]

Animation considerations (if rigged):
- Rig complexity: [hero / NPC / background]
- Key poses to design toward: [idle, action, hero moment]
- Pose directive if animations already exist: [exact A-pose or T-pose joint
  angles — "A-pose" alone is not a spec if the mesh has to match an
  existing animation set]
- Topology / deformation-zone rules: [eyes, mouth, shoulders, elbows,
  knees — name which zones need dedicated edge flow, don't leave it implied]

Technical budget:
- Material count / draw-call allocation: [e.g., max 2 materials — this is a
  budget decision, not a style preference, and should be stated as one]
- Hair, cloth and skin systems: [which shader; cards, cards-plus-strands,
  or geometry]

Silhouette read distance: [does this need to read at a specific distance or
  screen size — icon, inventory, gameplay-distance — state it, it changes
  every decision downstream]

Expression sheet needed: [yes / no]
Turnaround needed: [yes / no / front+back only]
```

---

## Schema B — ENVIRONMENT / SCENE

```
ENVIRONMENT SPEC
────────────────
Scene type: [interior / exterior / mixed]
Biome / setting:
Time of day:
Weather / atmosphere:

Scale reference: [what is the viewer's scale in this space]
Traversal type: [explorable / background / cutscene only / static set]

Architecture style:
- Primary material(s):
- Secondary material(s):
- Architectural era / cultural influence:
- Decay / age level:

Lighting:
- Key light source (sun, torch, magic, practical, etc.):
- Light color temperature:
- Shadow depth and softness:
- Any emissive or magical light sources:

Focal point: [what should the eye go to first]
Depth layers: [FG / MG / BG treatment]
Hero props (key set dressing items):

Modular kit needed: [yes / no]
- If yes — grid alignment: [does this snap to unit metrics, and to which
  grid — an unstated grid is how modular pieces stop lining up]
- If yes — pivot points and intersection tolerances for walls, floors, trim:
Tileable textures needed: [yes / no]
Skybox / skydome needed: [yes / no]

Technical budget:
- Texel density target: [e.g., 512 px/metre — without a number, adjacent
  props at different resolutions will visibly disagree]
- Tangent space for baking: [name it — MikkTSpace is the Unreal default; a
  custom space left unstated is how seam artifacts arrive]
- Reuse: [is this a hero piece seen once, or set dressing seen fifty times —
  it changes the cost model, not just the polish level]
```

---

## Schema C — PROP / ITEM

```
PROP SPEC
─────────
Item type: [weapon / armor / furniture / vehicle / collectible / tool / other]
Function in world: [what does this thing DO or mean]
Who owns/uses it: [faction, character, era, culture]

Form language: [organic / geometric / mechanical / hybrid]
Scale: [dimensions or scale reference — e.g., "one-handed sword, ~90cm"]

Primary material(s):
Secondary material(s):
Surface treatment: [polished / aged / rusted / enchanted / hand-finished / etc.]
Color: [primary, secondary, accent]
Wear level: [mint / used / ancient / destroyed]

Iconographic clarity: [does it need to read at small sizes — icon/inventory]
Iconic silhouette notes: [any shape that MUST be clear]

If grid/pixel-constrained (icon, sprite): canvas grid size and render size
are one decision, not two — changing either without the other silently
breaks the silhouette read. State both together, and flag as 🔴 Critical.

If a functional item (weapon, vehicle, interactable):
- Attachment points: [name them, and the socket naming convention]
- Functional readability: [which parts must read as usable at gameplay
  distance — a grip, a trigger, a hinge]
- Animation dependencies: [must this mesh support an existing rig or
  animation set — treat as a hard constraint, not a note]

Texel density target: [e.g., 512 px/metre, if this sits next to other props
  that already have one]

In-world lore hook (optional): [one sentence — what makes this object special]
```

---

## Schema D — CREATURE / MONSTER

```
CREATURE SPEC
─────────────
Role: [boss / standard enemy / passive / familiar / mount]
Threat level impression: [what emotion should it trigger on sight]

Biological classification (loose): [mammal / reptile / insect / eldritch / hybrid]
Size reference: [relative to human — e.g., "twice human height, quadruped"]
Locomotion: [bipedal / quadruped / flying / swimming / burrowing / etc.]

Body surface: [scales / fur / chitin / skin / hide / bark / etc.]
Primary color range:
Secondary / accent colors:
Any bioluminescence or emissive elements:

Silhouette priority: [describe the most readable shape feature]
Key anatomical details: [horns, tail, claws, wings — what defines this creature]
Attack tells / visual design hooks: [visual cues that communicate its danger]

Topology / deformation-zone rules (if rigged): [same discipline as
  Character — name the zones needing dedicated edge flow]

Cultural / mythological inspiration (if any):
IP reference closest in spirit:
```

---

## Schema E — KEY_ART / MARKETING

```
KEY ART SPEC
────────────
Use case: [box art / store banner / splash screen / poster / social media]
Platform(s): [Steam, App Store, console, print, web — affects safe zones]

Composition type: [hero-centric / ensemble / environmental / abstract]
Focal hierarchy: [what reads first, second, third]

Logo-safe zone: [where does the title/logo sit — top, center, etc.]
Text-safe areas: [regions that must remain uncluttered for copy]
Crop guide: [which edges can be cropped for different aspect ratios]

Hero character(s) or subject:
Background treatment:
Key action or narrative moment:

Aspect ratios needed:
- Primary: [e.g., 16:9 for Steam capsule]
- Secondary: [e.g., 1:1 for social, 9:16 for mobile store]

Brand elements required: [logo, tagline, rating badge, platform logos]
```

---

## Schema F — PHYSICAL / FABRICATION

```
PHYSICAL SPEC
─────────────
Object type: [furniture / prop / sculpture / costume piece / set element]
Fabrication method: [woodworking / 3D print / CNC / casting / sewing / mixed]

Dimensions (L × W × H):
Weight target or constraint:
Material(s): [species of wood, type of resin, fabric, metal, etc.]
Finish: [stain, paint, lacquer, raw, weathered, etc.]

Structural requirements: [load-bearing, wall-mounted, freestanding, wearable]
Joinery / assembly method (if applicable):
Tolerance: [precision level — e.g., ±1mm, ±1/16"]

Reference scale: [1:1, miniature, oversized]
Texture / surface treatment:
Color: [paint spec, stain color, natural grain]

Safety / compliance: [if applicable — fire rating, child safety, etc.]
Environment: [indoor / outdoor / both — affects material choice]
```
