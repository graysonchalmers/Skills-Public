---
name: art-brief
version: 2.3
visibility: public
description: >
  Composes vendor-ready art briefs from any inputs: text descriptions, reference
  images, project context, IP references, asset lists, or rough sketches. Use
  whenever a user wants to create, write, or generate an art brief, style guide,
  asset spec, outsource brief, or art direction document for any creative asset
  — game art, film, industrial design, illustration, concept art, props,
  characters, environments, creatures, marketing assets, or physical fabrication.

  Triggers on: "write me a brief for...", "I need to brief a vendor on...",
  "help me spec out this asset", "how do I describe this art style to an
  artist", "I have this idea and need to get it on paper", or "turn this
  concept into something I can send to a studio."

  Core purpose: compress a creator's mental vision into the highest-fidelity
  written specification possible, minimizing lossy transfer between minds. Also
  handles brief iteration — updating an existing brief based on vendor questions,
  stakeholder feedback, or evolved creative direction.
---

# Art Brief Composition Skill v2.3

![Example output: a real environment brief — palette, priority-weighted requirements, and borrow/avoid references, compressed into a vendor-ready spec](references/example-output.webp)

## Philosophy

Creative vision lives in latent space — a rich, multidimensional mental model
that resists compression into words. This skill is a **lossy codec for creative
intent**. The goal is maximum fidelity: capture enough signal that another
human (or AI) can reconstruct the vision with minimal drift.

Every field in this brief exists to reduce ambiguity. If a field doesn't reduce
ambiguity for THIS specific brief, omit it.

**The single idea the whole skill rests on:** an external artist cannot walk
over and ask. Every ambiguity in a brief resolves one of two ways — a
question that costs a round-trip, or a guess that costs a rework cycle. A
brief is not a description of the asset; it is a pre-payment of every
question the artist would otherwise have to ask. Judge one by how many
questions it makes unnecessary, not by how complete it looks. Ambiguity is
priced as risk by whoever receives the brief — it never comes back cheaper
for being vague.

---

## Modes of Operation

This skill operates in two modes:

### Mode A — New Brief
Transform loose inputs into a structured brief from scratch.
Flow: Intake → Assumptions → Build → Output

### Mode B — Brief Iteration
Update an existing brief based on new information.
Triggers: "here's my old brief," "the vendor asked...", "stakeholder wants...",
"we changed direction on..."

Flow: Ingest existing brief → Identify deltas → Update → Output revised brief
with a **Change Log** section appended showing what changed and why.

---

## Step 1 — Intake & Classification

### 1A — Classify the Asset Type

Determine what is being briefed. This drives the reactive schema in Step 4.

| Asset Type | Key signals |
|---|---|
| `CHARACTER` | Hero, NPC, enemy, villain, companion, player avatar, figurine |
| `ENVIRONMENT` | Level, scene, biome, interior, exterior, skybox, background, set |
| `PROP` | Item, weapon, armor, furniture, vehicle, collectible, tool |
| `CREATURE` | Monster, beast, familiar, enemy creature, boss, animal |
| `VFX` | Effect, particle, spell, ability, impact, simulation |
| `UI` | Interface element, icon, HUD, menu screen, signage |
| `KEY_ART` | Splash art, box art, poster, marketing image, store asset, hero banner |
| `SCENE_COMP` | Keyframe, cutscene frame, storyboard, establishing shot |
| `PHYSICAL` | Woodworking, fabrication, set build, practical prop, sculpture |

If the asset type is ambiguous, make your best call and flag it in the
Assumption Block.

### 1B — Assess Input Sufficiency

Before asking questions, evaluate what you already have:

**If inputs are rich** (image-decomp output, detailed description, multiple
references, clear context): Skip directly to the Assumption Block. Do not
interrogate — infer and confirm.

**If inputs are sparse** (one sentence, vague idea, no references): Ask the
**minimum critical questions** needed — 2 to 4 max. Never more.

**Critical questions (ask only if truly missing):**
1. **What is the asset?** — 1-sentence description of the subject
2. **What project/world is this for?** — genre, tone, setting, medium
3. **Who receives this brief?** — internal team, outsource studio, fabricator, AI gen
4. **Any reference images, IPs, or real-world objects in mind?**

Infer everything else. Flag inferred values with `⚠️ Assumed:` so the user
can correct.

### 1C — IP & Inspirational Reference Extraction

When the user provides IP references (games, films, art styles, real-world
objects, architectural movements), do not just name-drop them. Extract and filter:

**For each IP reference, identify:**
- ✅ **Borrow** — the specific quality to reference (e.g., "Arcane: painterly
  texture on skin, NOT the neon color palette")
- ❌ **Avoid** — what to explicitly NOT take from that IP (prevents derivative work)
- 🎯 **Target quality** — the single most useful thing this IP contributes to
  this brief

**Format:**
```
IP: [Title]
✅ Borrow: [specific visual quality — lighting, silhouette, texture, palette, form, etc.]
❌ Avoid: [what NOT to copy — be specific]
🎯 Target: [one sentence on why this IP is in the brief]
```

### 1D — Audience & Tone Calibration

The brief's tone adapts to who receives it:

| Audience | Tone | What changes |
|---|---|---|
| **Trusted long-term vendor** | Collaborative, shorthand OK | Can reference shared history, lighter on basics |
| **New vendor / first brief** | Precise, no assumptions | Spell out everything, include style bible refs |
| **Internal team** | Direct, technical | Can use internal jargon, reference existing assets |
| **AI generation** | Prompt-optimized | Condense to generation-ready language |
| **Fabricator / physical** | Dimensional, material-specific | Include tolerances, material specs, scale refs |

Default to **"New vendor"** tone if unspecified.

### 1E — Style Authority & Process

Two things a brief needs that are easy to leave implicit and expensive to
leave undefined:

- **Style authority** — one name: whose taste is the final word on whether
  this reads as correct. Not the same person as the approval owner in Step 3
  (Process) by default — a brief that quietly conflates "whose taste wins"
  with "who can say yes" causes more rework than almost anything else on
  this list, because a technically-approved asset can still be wrong by the
  one standard that actually mattered.
- **Process** — who reviews, how fast, through what channel, and what
  happens if a review stalls. This becomes the Process block in Step 3; ask
  for it here if it isn't already known.

If either is genuinely undecided, say so in the Assumption Block rather than
inventing a name — an undefined style authority is a real risk, not a gap to
paper over.

---

## Step 2 — Assumption Block

Before building the brief, output a short Assumption Block for user review.

```
📋 BRIEF ASSUMPTIONS — please confirm or correct before I finalize:

⚠️ Asset Type: [your classification]
⚠️ Project Context: [what you inferred about the project/world]
⚠️ Target Audience: [who receives this brief + tone calibration]
⚠️ Style Authority: [one name — whose taste is the final word]
⚠️ Art Style Direction: [your inferred style in 1–2 sentences]
⚠️ Delivery Format: [file types, resolution, platform constraints]
⚠️ [Any other significant inference]

🔴 Priority Flags: [anything that MUST be right or the brief fails —
   e.g., "The silhouette must read at 64px for inventory icons"]

🚩 Concerns: [flag anything underspecified, contradictory, or risky —
   e.g., "The IP references conflict in color temperature — Arcane is warm,
   Dark Souls is desaturated. Which takes priority?"]

⛔ IP Conflicts: If IP references create a direct visual contradiction
   (conflicting color temperatures, incompatible stylization levels, etc.),
   flag this as a BLOCKER. State clearly: "This conflict must be resolved
   before the brief can be finalized." Do not proceed to Step 3 with
   unresolved contradictions — they will produce an incoherent brief.
```

**STOP HERE.** Output the Assumption Block and wait for user confirmation before proceeding.
Do not generate the full brief until the user explicitly confirms or corrects these assumptions.
If the user confirms, proceed to Step 3.

---

## Step 3 — Core Brief Elements (All Asset Types)

Populate these sections for every brief, regardless of asset type.

### 🎯 Project Context
- Project name, genre, and medium (game / film / product / etc.)
- Target platform or use context (if applicable)
- Overall art style in 1–2 sentences
- Tone and mood keywords (3–5)

### 🎨 Visual Language
- Color palette: 4–8 hex values with roles (primary, shadow, accent, highlight)
- Lighting style and key light direction
- Line work / edge style (if applicable)
- Texture density and surface treatment
- Shading model (flat, cel, painterly, PBR, hand-finished, etc.)

### 📐 Technical Spec
- Deliverable format (PSD, PNG, FBX, OBJ, physical dimensions, etc.)
- Resolution / texture size / DPI
- Polycount target (if 3D) or dimensional tolerances (if physical)
- Style guide or bible reference (if exists)
- LOD requirements (if applicable)

**Every numeric constraint carries its reason.** "Max 15k triangles" gets a
vendor 15k triangles distributed badly. "Max 15k, because this reads at 8
metres in motion and the silhouette is the whole read" gets a vendor making
the same tradeoff the brief-writer would have made, without a round trip.
This is the single cheapest addition to a technical spec and the one most
often skipped because the number alone feels sufficient.

**If the asset ships across more than one hardware tier**, the scalability
rules belong in the brief, not discovered at integration: the LOD chain,
target counts per tier, texture budgets, and shader complexity ceiling.
Discovering these at integration means the vendor built the wrong thing
correctly — and that cost lands on whoever wrote the brief, not the vendor.

### 🧭 Artistic References
For each reference, use the extracted IP format from Step 1C.
Include 3–6 references total — mix of IP, artists, movements, and/or
real-world objects.

**Negative references — a separate, mandatory sub-block, not just prose.**
At least 2 actual images (not just described avoids), each captioned with
the one specific reason it's wrong. "What good is not" is exactly as
informative as "what good is," and it's the block most likely to be skipped
because it feels like it should be obvious. It usually isn't — the one
interpretation that seems too obvious to state out loud is precisely the
one an outside artist lands on.

### 🔴🟡🟢 Priority-Weighted Requirements

Every visual requirement gets a priority weight:

- 🔴 **Critical** — Brief fails without this. Non-negotiable. (e.g., "Must
  read as a silhouette at icon size," "Color must match brand hex exactly")
- 🟡 **Important** — Strong preference, but some flexibility. (e.g., "Prefer
  warm lighting, but cool is acceptable if it serves the mood")
- 🟢 **Nice-to-have** — Enhances quality but won't block approval. (e.g.,
  "Subtle fabric texture on the cloak would be a plus")

This system helps vendors triage effort and prevents everything from feeling
equally urgent.

### ⛔ Explicit Avoids
A short list of what NOT to do, stylistically. This section is mandatory —
it is as important as what to include.

Examples: "Do not use photorealistic rendering," "Avoid oversaturated neon
colors," "No generic fantasy tropes — this world has a specific visual
identity," "Do not reference [specific IP] — too close to their trademark."

This is a **style** list — what the asset should not look like. It is a
different thing from Scope Boundaries below, which is about what work is
and isn't included. Conflating the two is common and leaves scope
disagreements with no document to resolve them.

### 🚧 Scope Boundaries & Change Policy

The most-skipped block in any brief, and the one that most often decides
whether a disagreement gets resolved calmly or turns into whoever's more
willing to damage the relationship. Two things, stated plainly:

- **What is explicitly out of scope.** Named, not implied — "concept
  exploration ends at the selected direction; further exploration is a
  change," "texture variants beyond the two specified are a change,"
  whatever applies to this asset.
- **What a change costs, in principle, before there is one.** This brief
  doesn't need to name a dollar figure — that's a rate conversation, not a
  brief one — but it should say whether a scope change after kickoff is
  handled as a change order, or is the kind of small thing a good partner
  is expected to absorb. Leaving this ambiguous means it resolves in favor
  of whoever is more comfortable with conflict, which is a bad way to
  decide anything.

Writing this down is not adversarial — it's what lets both sides say yes to
a change quickly, because they already agree on what a change is.

### 📋 Process
- **Named reviewer** with actual authority to approve, not just to comment
  — distinct from the Style Authority named in Step 1E if that's a
  different person, and noted as such if so.
- **Stated review turnaround** — a real commitment, not an aspiration.
- **Feedback channel** — where notes arrive and in what form.
- **Escalation path** — what happens if a review stalls or two reviewers
  disagree.

Feedback that arrives after final isn't feedback — it's a change order, and
this block exists so that never happens by accident.

### 📅 Delivery & Milestones (if applicable)

Include when the brief is going to an external vendor or fabricator.
Omit for internal brainstorming or AI generation.

```
MILESTONE STRUCTURE
───────────────────
M1 — Sketch / Concept (2–3 options): [date or timeframe]
M2 — Refined Concept (1 selected direction): [date or timeframe]
M3 — [Medium-specific stage — e.g., Lineart / Blockout / Maquette]: [date or timeframe]
M4 — Final Asset: [date or timeframe]

Revision rounds per milestone: [number — typically 1–2]
Feedback turnaround: [expected response time from your side]
```

Adapt milestone names to the medium — a 3D character has different stages
than a matte painting or a woodworked prop.

---

## Step 4 — Asset-Type Reactive Schema

Use the classification from Step 1A to select the matching schema.
**Read the relevant schema from `references/schemas.md`** and populate only
the fields that genuinely apply. Omit rather than pad with "N/A" or "TBD."

| Asset Type | Schema to Load |
|---|---|
| `CHARACTER` | Schema A — CHARACTER |
| `ENVIRONMENT` | Schema B — ENVIRONMENT / SCENE |
| `PROP` | Schema C — PROP / ITEM |
| `CREATURE` | Schema D — CREATURE / MONSTER |
| `KEY_ART` | Schema E — KEY_ART / MARKETING |
| `PHYSICAL` | Schema F — PHYSICAL / FABRICATION |
| `VFX`, `UI`, `SCENE_COMP` | No dedicated schema — use Core Brief Elements (Step 3) with extra detail in relevant sections |

---

## Step 5 — Assemble the Full Brief

Once all sections are populated, assemble the three output blocks.
**All three blocks are always produced at full fidelity regardless of any
user verbosity or formatting preferences.** The resolution of this output IS
the value — never truncate for brevity.

Every brief header carries a **version number and date**, from v1 — not
only once it's been iterated on. It's the cheapest line in the document and
it ends an entire category of "which copy is current" argument later.

---

### OUTPUT BLOCK 1 — 📄 Art Direction Document

Full structured document using all populated sections from Steps 3 and 4.
Write in clear, confident art direction voice — present tense, active voice.
This is the document an art director, creative director, or project lead
would sign off on.

Header always includes: **Version: v[X] — [date]**.

Include the priority weights (🔴🟡🟢) inline with requirements.

---

### OUTPUT BLOCK 2 — 📬 Vendor Brief

A condensed, semi-formal version of the Art Direction Document.
Tone: calibrated per Step 1D (default: professional, precise, no assumptions).

Structure:
- Version and date, same as the full document
- 2–3 sentence project context opener
- Priority-weighted bullet list of key visual requirements (🔴🟡🟢)
- IP references with extracted borrow/avoid
- Explicit avoids (style) and Scope Boundaries & Change Policy (scope) —
  kept as two distinct sections, not merged
- Process: named reviewer, turnaround, feedback channel
- Deliverable spec (format, resolution, dimensions)
- Milestone structure (if applicable)
- "Please reach out if you have questions or need clarification on any point."

Keep it tight — one page if possible. Cut anything that's nice-to-know vs.
need-to-know. But never cut a 🔴 Critical requirement, and never cut Scope
Boundaries — it's short by nature and it's the section most worth keeping
even under space pressure.

---

### OUTPUT BLOCK 3 — 🤖 Generation Prompts

Provide **model-specific** prompt blocks:

**Midjourney format:**
- Subject + descriptors, style references, lighting, composition
- End with MJ parameters: `--ar [ratio] --s [stylize] --v [version]`
- Use `--sref` or `--cref` notes if the user has reference images

**DALL-E / GPT-Image format:**
- Natural language paragraph, more descriptive
- Include medium, artist references, mood, and quality descriptors
- Note any negative prompt requirements

**Stable Diffusion format:**
- Comma-separated tag style
- Include positive and negative prompt blocks separately
- Note recommended model/checkpoint if inferable from the style

If the target medium is physical (woodworking, fabrication), replace this
block with a **Materials & Process Note** instead — a short paragraph on
recommended approach, tools, and sequencing.

Keep this block general-purpose. The brief itself — the document a human
artist reads — is the higher-leverage output; this block is a convenience,
not the point of the skill.

---

## Step 6 — Brief Iteration (Mode B)

When updating an existing brief, follow this flow:

### 6A — Ingest & Diff
Parse the existing brief. Identify which sections are affected by the new
information (vendor questions, feedback, direction change).

### 6B — Targeted Update
Only modify affected sections. Preserve everything else verbatim. Bump the
version number on every re-issue, even a small one — a silent update is
worse than no update, because it destroys trust in the document itself.

### 6C — Is This a Change Order?

A brief edit after kickoff is either a **change order** or an explicitly
named gift the vendor is choosing to absorb — never silent, and never
ambiguous by default. Before writing the Change Log, decide which this is
and say so in it. Both are legitimate; leaving it unstated is not, because
ambiguity resolves in favor of whoever is more comfortable with conflict.

### 6D — Change Log
Append a Change Log to the updated brief:

```
📝 CHANGE LOG — [Date or Version]
──────────────────────────────────
Section: [which section changed]
Change: [what changed]
Reason: [why — vendor question, stakeholder feedback, creative pivot]
Status: [change order — quoted separately / absorbed as a favor, named as such]
Impact: [does this change cascade to other sections? If so, flag them]
```

### 6E — Re-output
Produce the updated full brief (all three output blocks) with changes
integrated. The Change Log is appended at the end, not inline.

**Output Block 3 (Generation Prompts) must be fully regenerated — do not
summarize or reference the previous version. Every prompt block must reflect
the updated brief at full fidelity.**

---

## Quality Standards

- **Assumption transparency**: Every inferred value is flagged `⚠️ Assumed:`
- **Concern flagging**: If inputs conflict or are underspecified, say so explicitly
- **IP extraction depth**: Never just name-drop — always extract borrow/avoid/target
- **No generic filler**: "Epic fantasy style" is not useful. Be specific about WHAT
  makes it epic and WHICH flavor of fantasy.
- **Ambiguity is priced as risk, not discounted** — a brief this skill produces
  should remove questions, not just describe the asset. That's the standard
  to write against, not "does this look complete."
- **Avoid list is mandatory, and Scope Boundaries is a separate mandatory
  block** — style avoids and scope boundaries answer different questions and
  must not be merged into one list.
- **Priority weights are mandatory**: Every requirement gets 🔴🟡🟢 classification
- **Every numeric technical constraint carries its reason**, not just the number.
- **Every brief is versioned and dated, from v1** — not only once it's iterated.
- **Output all 3 blocks**: Art Direction Doc + Vendor Brief + Generation Prompts always
  (or Materials & Process Note for physical assets)
- **Reactive schema**: Use the correct asset-type schema — don't default to generic
- **Full fidelity always**: Never truncate output for brevity preferences. The
  resolution of the brief is the product.
- **Iteration-ready**: The brief structure must support versioning and change tracking.
  A post-kickoff edit is a change order or a named absorbed favor — never silent.

---

## Companion Skill: image-decomp

The image-decomp skill (v2) analyzes existing images into structured reports.
Its output maps naturally into this skill as structured input:

| image-decomp output | art-brief input |
|---|---|
| `artisticReferences` | Step 1C IP references |
| `colors` | Visual Language — color palette |
| `customFields` | Asset-type schema fields |
| `technicalSummary` | Art Direction Doc opener |
| `generatedPrompt` | Seed for Generation Prompt block |
| `tags` | Tone/mood keywords |
| `metadata` | Context-reactive fields for matching schemas |

When image-decomp output is provided as input, auto-populate matching fields
and skip directly to the Assumption Block (Step 2). Do not re-ask for
information already captured in the decomp.

## Companion Skill: outsource-intake

For scope, phases, sign-off, timeline, and files without full visual
direction, use **outsource-intake** instead — it's the lighter-weight
sibling to this skill and the two share vocabulary on purpose (Style
Authority vs. Approval Owner, Scope Boundaries, cost/timeline process
checks). outsource-intake can hand off to this skill for complex or
high-stakes asks; this skill's output can seed an outsource-intake request
when a full brief already exists and just needs to become a trackable ask.

---

## Example Triggers

**New brief:**
- "Write me an art brief for a dark elf assassin character"
- "I need to brief a vendor on an abandoned cathedral environment"
- "Help me spec out this weapon — it's like Bloodborne meets Breath of the Wild"
- "Turn this concept into something I can send to an outsource studio"
- "Create an art direction doc for our protagonist"
- "I have a rough idea for a boss creature, help me flesh it out into a brief"
- "I need to build a walnut credenza — help me spec it out"
- "We need box art for our Steam page — can you write the brief?"

**Brief iteration:**
- "Here's the brief we sent — the vendor asked these questions, help me update it"
- "Our AD wants to push the palette warmer — update the brief"
- "We changed the character's weapon from a staff to a scythe — revise everything affected"
- "The client wants the poster to also work as a social media banner — what needs to change?"
