---
name: art-brief
version: 2.7
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

# Art Brief Composition Skill v2.7

![Example output: a real environment brief — palette, priority-weighted requirements, and borrow/avoid references, compressed into a vendor-ready spec](references/example-output.webp)

## Philosophy

Creative vision lives in latent space — a rich, multidimensional mental model
that resists compression into words. This skill is a **lossy codec for creative
intent**. The goal is maximum fidelity: capture enough signal that another
human (or AI) can reconstruct the vision with minimal drift.

Every field in this brief exists to reduce ambiguity. Omit inapplicable fields;
keep relevant missing decisions visible as Unresolved. Completeness is not
permission to invent a requirement.

**The single idea the whole skill rests on:** an external artist cannot walk
over and ask. Every ambiguity in a brief resolves one of two ways — a
question that costs a round-trip, or a guess that costs a rework cycle. A
brief is not a description of the asset; it is a pre-payment of every
question the artist would otherwise have to ask. Judge one by how many
questions it makes unnecessary, not by how complete it looks. Ambiguity is
priced as risk by whoever receives the brief — it never comes back cheaper
for being vague.

---

## Request-scoped debug preview

Only an explicit request for debug mode / a headless debug preview enables this
exception. Read `references/debug-and-contacts.md` before using it. Produce the
requested artifact immediately with unobtrusive placeholders; do not ask for real
information or wait at STOP/confirmation gates. Label every preview, output block,
and excerpt **DEBUG PREVIEW—NOT FOR SENDING**. Placeholders/examples are never
Confirmed or evidence for Ready, even when quoted from a supplied synthetic
fixture. Keep fixture values Proposed — illustrative only; keep missing values
Unresolved. Genuine non-synthetic inputs retain their source/status. No lookup,
outreach, or tracker writes in debug.
The override ends with this request; normal mode and its gates are unchanged.

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

## Source-linked rendering — load before any checkpoint

Read `references/source-linked-output.md` **before the first intake summary or
Step 2 checkpoint**, and read it again **before Step 5 assembly or any Mode B
reply/change log**. Build the visible compact source/decision register first;
render every condensed claim from its atoms with IDs, labels and a source key.
Reuse one register appendix across the three blocks, not three repeated ledgers.
This is a writing contract, not a software/runtime dependency.

## Adaptive frontier interview contract

Read `references/frontier-interview.md` before a normal-mode intake or iteration; it defines the round trace and frontier fields used below.

Normal mode is an adaptive, multi-turn interview rather than a fixed questionnaire.
Register supplied facts and their exact source spans first; then compute the current
decision frontier: only decisions whose prerequisites are settled. Ask **2–4
consequential questions** from that frontier, with a recommendation where useful,
and never ask a captured fact or a downstream question whose prerequisite is still
open. After each answer, update the visible register (preserving IDs, status,
hedges, scope and source), record the answer-to-atom change in the interview trace,
and recompute the frontier. Stay quiet when the remaining gaps are non-blocking;
stop at the checkpoint/assemble step once remaining gaps do not change the requested
artifact, or when the user explicitly asks for a draft with gaps. Normal mode may
produce a draft with visible Unresolved items; it must not promote proposals.

This contract is request-scoped. Explicit debug mode remains immediate: ask no
questions, do not wait for confirmation, and label the result **DEBUG
PREVIEW—NOT FOR SENDING** as required by `references/debug-and-contacts.md`.
For normal multi-turn work, retain a source-linked interview trace with each round's
frontier, numbered questions, answer source, and register evolution; the final
artifact must be renderable from the latest register and cite the shared appendix.
Keep the complete three output blocks in every assembled Art-Brief (Art Direction,
Vendor Brief, and Generation Prompts/Materials & Process Note), even when gaps remain.

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

If the asset type is ambiguous, suggest a classification as Proposed in the
Assumption Block.

### 1B — Establish the Interpretation Class

Before filling gaps, establish how much interpretation the receiving partner
is expected to carry. Extract an explicit answer from existing inputs; otherwise
ask: **"How much interpretation should the partner carry on this work?"**
Offer the classes below in plain language. A suggested class is Proposed until
confirmed. Do not infer it from asset count, partner reputation, or familiarity.

| Class | Partner carries | Brief behavior |
|---|---|---|
| **Self-governing** | Interpretation, creative and technical judgment within agreed boundaries | Capture intent, fixed constraints, and delegated decisions; offer creative options and any exploration/selection gate as Proposed |
| **Brief-driven** | Execution to a stated bar, raising questions before starting | Capture approved targets and exceptions; ask about consequential gaps rather than inventing direction |
| **Volume with QA overhead** | Throughput and consistency against agreed exemplars | Preserve approved style; establish exemplar access, style-lock and buyer QA capacity before scaling; no unsolicited redesign |

These are engagement classes, not quality grades. Different workstreams may
have different classes. Class adjusts questions and proposed review structure;
criticality, dependencies, and the actual agreement still determine the gates.
Offer gates for confirmation, never silently impose them. For internal or AI
work, apply the same distinction to how much exploration the receiver may do.
An unknown class does not prevent a draft; keep it Unresolved.

No class authorizes this assistant to invent approved budgets, technical limits,
dates, commercial terms, or decision-makers. Delegating a decision confirms
who may make it, not the value they will choose. Ask for existing project specs
or flag the missing constraint; do not derive a budget from an engine name.

### 1B continued — Assess Input Sufficiency

Before asking questions, evaluate what you already have:

**If inputs are rich** (image-decomp output, detailed description, multiple
references, clear context): extract what is stated, preserve its source and
status, then ask only about consequential gaps before the Assumption Block.

**If inputs are sparse** (one sentence, vague idea, no references): Ask the
**minimum critical questions** needed in rounds of 2–4. This is a per-round
limit, not permission to invent everything after the fourth question. Offer
a draft with visible gaps if the user does not have the answers.

**Critical questions (ask only if truly missing):**
1. **What is the asset?** — 1-sentence description of the subject
2. **What project/world is this for?** — genre, tone, setting, medium
3. **Who receives this brief?** — internal team, outsource studio, fabricator, AI gen
4. **Any reference images, IPs, or real-world objects in mind?**

Use the four decision labels in Step 2. Self-governing work invites proposed
creative options; brief-driven and volume work prioritize missing requirements
and exceptions. Ask for asset intent and any delegated decisions, not just its
appearance. Reuse answers supplied by outsource-intake without re-interviewing.

### 1C — IP & Inspirational Reference Extraction

Read `references/curated-comparisons.md` for supplied IP extraction and curated
comparisons. Where evidence supports useful enrichment, offer 3–5 artist/studio/IP
comparisons with exact borrow/avoid/why and Proposed labels; fewer or none is valid.
Keep suggested comparisons separate from inspected references and approved targets.
Optionally add 1–2 dimension-specific X-meets-Y pitches with support for both halves.
Never imply influence, invent an approved negative, or force a quota. Preserve the
user's stated reference roles; proposed extensions remain proposals everywhere.

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

- **Style authority** — whose taste is the final word, for which dimensions
  and scope. Record separately from the procedural approval owner; neither
  role implies the other. Preserve explicitly joint authority rather than
  inventing a single decision-maker.
- **Process** — who reviews, how fast, through what channel, and what
  happens if a review stalls. This becomes the Process block in Step 3; ask
  for it here if it isn't already known.

If either is genuinely undecided, say so in the Assumption Block rather than
inventing a name — an undefined style authority is a real risk, not a gap to
paper over. One person may legitimately hold both roles; record this without
flagging a risk merely because the names match. A conflict exists only when
authority or the decision itself is unclear, not because roles are combined.

An authority ruling resolves the contested dimension only — the decision
actually in dispute (proportion language, a palette, an avoid). Extending it
into new requirements the authority never stated (rendering finishes, new
bans, new musts) is authorship, not resolution: label the extension
Proposed or leave it out. "The AD ruled chunky-stylized proportions" never
becomes "realistic rendering is banned."

Label integrity is per-decision, not per-section: an inference labeled
Proposed in one section stays Proposed everywhere it reappears — priority
lists, vendor-facing text, prompts, change logs. Condensing, reordering, or
moving a decision across sections never upgrades its label; restating a
Proposed inference without its label is how invented facts acquire authority.

---

## Step 2 — Decision Labels & Assumption Block

Every substantive decision has a register ID, one of these labels, and its
source span or explicit missing-source marker. Condensed clauses cite those IDs;
shared labels are valid only where source, status, hedge and scope truly match.
Use the compact format in `references/source-linked-output.md`.

| Label | Meaning | Example |
|---|---|---|
| **Confirmed** | Explicitly supplied or accepted by the user or identified source; state who/source and what was actually confirmed | `Confirmed — requester: 12 icons` |
| **Observed** | Visible in an inspected reference, not automatically a requirement | `Observed — ref R2: broad, rounded forms` |
| **Proposed** | Assistant suggestion or interpretation not yet accepted | `Proposed — borrow R2's rounded forms, not its palette` |
| **Unresolved** | Missing or conflicting decision; identify impact, owner and decision date if known | `Unresolved — texture budget; technical owner/date not supplied` |

Confirmed records provenance, not independent verification, partner agreement,
or authority to approve work. Distinguish requested deadlines from partner-
agreed dates, and a supplied concept from an approved concept. Do not invent
source names, approval dates, or access to a referenced file. An inaccessible
image is not Observed; record the user's description as such and flag access.
Image-analysis output remains attributed analysis, not approved direction.

Promote a proposal only when the user explicitly accepts the identified value
or a clearly bounded list of proposals. A general "go ahead" authorizes drafting,
not blanket promotion of every assumption. Approval of one proposal does not
resolve other gaps. Proposed priorities remain proposals, even when marked
Critical. Group labels to keep the document readable, never to hide uncertainty.
Never call a Proposed item the current bar, approved requirement, or instruction
to execute. Requests to draft/explore named options do not accept their values.
Do not assign an open decision to the requester by default; unknown owners stay
unknown, or an assignment is Proposed. Scope exclusions, review gates, reasons
for numbers, and priority weights need the same provenance as visual choices.

Use the source-linked register for value, hedge, action state, and scope/role
limits. Unknown means **not supplied or not established by these sources**, not
nonexistent, excluded, unassigned, or not yet done. Keep numeric values separate
from their reasons, requested dates from agreed dates, review from approval,
availability from assignment, and scope inclusion from commercial treatment.

Before building the full brief, render this compact Assumption Block from the
register. Attach its source key/register once; cite IDs in each populated line:

```
BRIEF CHECKPOINT — confirm/correct decisions, or authorize a draft with gaps:
Asset / intent / project: [value + label/source]
Interpretation class: [class + label/source, split by workstream if needed]
Delegated decisions / fixed constraints: [value + label/source]
Audience / style authority / approval owner: [value + label/source]
Visual direction / reference roles: [value + label/source]
Technical requirements / delivery / process: [value + label/source]
Proposals to accept: [named items, or none]
Open decisions: [impact, owner, date; unknown where not supplied]
Priorities: [sourced or Proposed weight + separate decision ID; otherwise Unresolved]
```

Reference differences are conflicts only when incompatible requirements apply
to the same dimension in the same context. A silhouette-only reference may
legitimately disagree with a palette reference. Ask what each is intended to
supply before declaring a conflict; never average contradictory targets away.
Self-governing exploration may present alternatives as Proposed. Unresolved
production-critical conflicts prevent calling the brief approved or ready for
production, not creation of an explicitly labeled draft.

**STOP HERE in normal mode.** Explicit request-scoped debug bypasses this wait.
Otherwise wait for confirmation/corrections or explicit permission to
produce a draft with gaps before Step 3. Carry remaining labels and open decisions
into the output. Confirming this checkpoint is not commercial authorization.

---

## Step 3 — Core Brief Elements (All Asset Types)

Use these sections where applicable, with Step 2 labels intact. Relevant
unknowns stay Unresolved; never fill required sections with invented decisions.

### 🎯 Project Context
- Project name, genre, and medium (game / film / product / etc.)
- Asset intent: where it is encountered and what it should communicate
- Target platform or use context (if applicable)
- Overall art style in 1–2 sentences
- Tone and mood keywords (3–5)

### 🎨 Visual Language
- Color palette: supplied values, or Proposed colors with roles. Only call hex
  values measured when actually sampled; lighting in a reference is not a
  material color specification. Do not invent colors to meet a quota.
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
- Target engine/version, naming, source-file expectations and integration
  requirements for production assets, sourced from the project spec

Missing values or reasons remain Unresolved; examples here and in schemas are
not defaults. Numeric precision is not evidence of an agreed requirement.

**Capture each numeric constraint's sourced reason when available.** If only
"max 15k triangles" was supplied, retain that limit with its source and mark the
reason Unresolved. Do not invent a viewing distance, performance rationale, or
tradeoff to make the number sound justified. A proposed rationale is a question
for confirmation, never the explanation of the existing limit.

**If the asset ships across more than one hardware tier**, the scalability
rules belong in the brief, not discovered at integration: the LOD chain,
target counts per tier, texture budgets, and shader complexity ceiling.
Discovering these at integration means the vendor built the wrong thing
correctly — and that cost lands on whoever wrote the brief, not the vendor.

### 🧭 Artistic References
Use Step 1C's borrow/avoid/why format and keep inspected reference IDs separate
from Proposed comparisons. For a new production direction, assess coverage of the
needed dimensions, not a numeric image quota. Missing consequential coverage is
a visible gap, not permission to fabricate sources. Reuse an existing approved
package when its scope covers the request; don't add images just for completeness.

For Self-governing exploration, distinguish inspirations from acceptance
targets; record an agreed style-selection gate or offer one as Proposed when
useful. For Brief-driven work,
identify the approved target and allowed exceptions. For Volume with QA
overhead, confirm access to approved exemplars before declaring style-lock;
an existing exemplar does not mean the new batch has passed its review.
Caption each reference with the dimension it supplies and its decision label.

**Negative references — a separate sub-block when applicable.**
For inspected negative images, caption the exact unwanted dimension with its
status/source; rejection in one dimension does not reject the entire style.
If a negative target is needed but unavailable, retain an Unresolved slot.
Proposed avoids are suggestions, never approved negatives. Do not invent bans or
source unnecessary images to fill this section.

### 🔴🟡🟢 Priority-Weighted Requirements

Record a weight only when sourced or useful as an explicitly Proposed choice.
An accepted requirement does not imply an accepted priority. Keep them separate
in the register; leave an unstated weight Unresolved (one shared note is enough).
Do not force a classification on every requirement. Available weights:

- 🔴 **Critical** — Brief fails without this. Non-negotiable. (e.g., "Must
  read as a silhouette at icon size," "Color must match brand hex exactly")
- 🟡 **Important** — Strong preference, but some flexibility. (e.g., "Prefer
  warm lighting, but cool is acceptable if it serves the mood")
- 🟢 **Nice-to-have** — Enhances quality but won't block approval. (e.g.,
  "Subtle fabric texture on the cloak would be a plus")

This system helps vendors triage effort and prevents everything from feeling
equally urgent.

### ⛔ Explicit Avoids
A short list of sourced stylistic avoids, with decision labels. Keep the section,
but if no avoids are supplied, say Unresolved or offer explicitly Proposed avoids;
mandatory structure is not permission to invent restrictions.

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

- **What is explicitly out of scope.** Named, not implied — but named by a
  source: the requester, the prior brief, or an accepted proposal. Every
  exclusion carries its provenance. Boundaries you draft to make the brief
  look complete are invented scope — label them `Proposed — confirm` or cut
  them. "Characters/NPCs out of scope" written as agreed fact is a made-up
  agreement; the same line labeled Proposed is honest.
- **What a change costs, in principle, before there is one.** This brief
  doesn't need to name a dollar figure — that's a rate conversation, not a
  brief one — but it should say whether a scope change after kickoff is
  handled under an existing allowance, quoted as a change order, or explicitly
  accepted by the partner as a favor. Never invent that agreement. Leaving this ambiguous means it resolves in favor
  of whoever is more comfortable with conflict, which is a bad way to
  decide anything.

Writing this down is not adversarial — it's what lets both sides say yes to
a change quickly, because they already agree on what a change is.

### 📇 Contact Directory
Read `references/debug-and-contacts.md` and include its six-role directory for
client/internal and partner contacts: producer, outsource manager, art lead on
each side; name, email, Slack/Teams, phone, timezone, purpose, and status/source.
Use placeholders without blocking the draft; internal-only partner rows are N/A.
Keep the directory separate from task assignment and sign-off authority. Vendor
lookup/recommendation is opt-in only; do not interrupt briefing to procure a vendor.

### 📋 Process
- **Reviewer(s)** — who comments, with the scope actually supplied.
- **Approval owner(s)** — separately evidenced procedural sign-off authority;
  a named reviewer is not enough. Unknown authority stays Unresolved.
- **Review turnaround** — retain stated commitments, targets or tentative
  availability with their original status/hedge; do not upgrade an aspiration.
- **Feedback channel / notes format** — sourced values, not inferred from a
  file-delivery destination.
- **Escalation path** — the agreed path if supplied; otherwise Unresolved,
  or a Proposed option when useful. Neither conflict nor a single reviewer
  establishes a policy, new gate, or requirement for a fresh authority ruling.

Late direction can create new scope. Classify it against the agreed boundary
between a clarification, fixing a miss, an included revision, and a scope
change; do not invent billing consequences from its arrival time alone.

### 📅 Delivery & Milestones (if applicable)

Include when the brief is going to an external vendor or fabricator.
Omit for internal brainstorming or AI generation.

Record the supplied milestones and dates. If planning would help, offer a
small Proposed sequence adapted to the medium; there is no default number of
stages, options, revision rounds, or review gates.

| Milestone / deliverable | Date or timeframe + state | Revision allowance | Decision IDs |
|---|---|---|---|
| [sourced value or Proposed option] | [requested / agreed / tentative / Unresolved] | [sourced / Proposed / Unresolved] | [IDs] |

An empty plan is Unresolved, not a requirement to invent M1–M4. A Proposed gate
remains Proposed in the vendor brief, prompt notes and production preconditions.

---

## Step 4 — Asset-Type Reactive Schema

Use the classification from Step 1A to select the matching schema.
**Read the relevant schema from `references/schemas.md`** and populate only
the fields that genuinely apply. Omit inapplicable fields; keep relevant
missing decisions as Unresolved with impact, owner/date if known.

| Asset Type | Schema to Load |
|---|---|
| `CHARACTER` | Schema A — CHARACTER |
| `ENVIRONMENT` | Schema B — ENVIRONMENT / SCENE |
| `PROP` | Schema C — PROP / ITEM |
| `CREATURE` | Schema D — CREATURE / MONSTER |
| `KEY_ART` | Schema E — KEY_ART / MARKETING |
| `PHYSICAL` | Schema F — PHYSICAL / FABRICATION |
| `VFX`, `UI`, `SCENE_COMP` | No dedicated schema — use Core Brief Elements (Step 3) with extra detail in relevant sections |

For UI icons and sprites, also load Schema C's grid/pixel paragraph. Source
canvas and display/export size are separate constraints, never inferred equal.

---

## Step 5 — Assemble the Full Brief

Re-read `references/source-linked-output.md`, update the register with any
explicit acceptances, then assemble **all three output blocks**. Preserve all
load-bearing decisions and creative detail; omit repetitive explanations, not
scope or uncertainty. Condensed blocks render from the atoms, never from a
freehand summary of Block 1. Attach one shared source key/register appendix;
a standalone excerpt carries its referenced rows and source key with it.

Every brief header carries a **version number and date**, from v1 — not
only once it's been iterated on. It's the cheapest line in the document and
it ends an entire category of "which copy is current" argument later.

---

### OUTPUT BLOCK 1 — 📄 Art Direction Document

Full structured document using all populated sections from Steps 3 and 4.
Write clear, active art direction without changing tense, hedges or authority.
Separate supplied direction from useful Proposed creative options: materials,
palette roles, lighting methods, composition and dimension-specific references.
Register each option before rendering it; creative support need not wait for
all technical or business decisions to be settled.

Header always includes: **Version: v[X] — [date]**, interpretation class,
workstream/phase scope, and document status (Draft / For review / Approved).
Use Approved only with explicit approval of this version and scope by the
named authority; unknown authority remains Unresolved. Include a short open-
decisions block. A finished document is not authorization to start production.

Include sourced or Proposed priority weights inline; unknown weights stay unknown.

---

### OUTPUT BLOCK 2 — 📬 Vendor Brief

A condensed, semi-formal version of the Art Direction Document. It is a
recipient-facing draft, not a sent message; do not invent a recipient or claim
it has been delivered. Proposed values and unknowns remain visibly provisional.
Tone: calibrated per Step 1D (default: professional, precise, no assumptions).

Structure:
- Version, date, class, scope, status, and remaining open decisions, matching
  the full document; keep decision labels/source notes when condensing
- 2–3 sentence project context opener
- Key visual requirements with inline decision IDs and labels; include
  sourced/Proposed priority weights only. Split a sourced goal from a Proposed
  method (e.g. night readability versus a lantern-light solution).
- IP references with extracted borrow/avoid
- Explicit avoids (style) and Scope Boundaries & Change Policy (scope) —
  kept as two distinct sections, not merged
- Process: reviewer and separately evidenced approver, turnaround, feedback channel
- Contact Directory appendix (six roles; attach the shared directory for this package)
- Deliverable spec (format, resolution, dimensions)
- Milestone structure (if applicable)
- "Please reach out if you have questions or need clarification on any point."

Keep it tight — one page if possible. Cut anything that's nice-to-know vs.
need-to-know. But never cut a 🔴 Critical requirement, and never cut Scope
Boundaries — it's short by nature and it's the section most worth keeping
even under space pressure.

**Sendable-message contract** (any recipient-ready email, DM, or reply —
vendor answers, Mode B responses, status updates): state settled facts only when
Confirmed with their actual scope and hedges.
Explicitly labeled proposals and questions may be included for review, never as
promises, accepted terms, or instructions to execute. Unresolved items appear
as questions or open items, never as settled answers. Do not commit the user to
dates, prices, scope inclusions/exclusions, or process promises (escalation
rules, turnaround offers, note formats) they have not stated. A recipient's
question plus an undecided user equals an open item relayed back to the
user — not an invented answer. If the user must decide something before
the message is safe to send, say so plainly at the top.

**Release comparison:** apply `references/source-linked-output.md` to every
condensed clause, including headings, table cells, replies and change logs.
Compare source span → register atom → rendered clause, not just IDs or labels.
Repair unsupported verbs, roles, scope, certainty, or approval before returning
it; a correct appendix cannot excuse a contradictory opener.


---

### OUTPUT BLOCK 3 — 🤖 Generation Prompts

Provide **model-specific** prompt blocks. Each block must state whether it
is a concept exploration using named Proposed choices or a translation of
Confirmed direction. Never silently turn Observed/Proposed content into
approved requirements, or fill Unresolved specs in a prompt. Label suggested
model parameters as Proposed; if syntax/version is unverified, say so.
Apply the same rule to a Materials & Process Note for physical work.
Translate the registered direction, retaining clause IDs and status in the
annotated prompt. If exploration is requested or interpretation is delegated,
include useful creative support as named Proposed rows, then render a separately
labeled Proposed exploration prompt from them. This never replaces an approved
production target. For Brief-driven or Volume work, do not invent stand-in
styles, subjects, avoids or composition; identify pending inputs rather than
supply an unauthorized substitute. Unknown class is not permission to redesign.
No prompt fills unknown technical/business constraints or turns missing scope
into negative-prompt exclusions.

**Midjourney format:**
- Subject + descriptors, style references, lighting, composition
- Use verified applicable MJ parameters where known; otherwise omit them
  with a short unverified-syntax note, rather than inventing a version.
- Reference-image controls depend on model/version; verify before specifying.

**DALL-E / GPT-Image format:**
- Natural language paragraph, more descriptive
- Include registered medium, references, mood and descriptors where applicable
- Include only sourced negatives or explicitly Proposed exploration negatives

**Stable Diffusion format:**
- Comma-separated tag style
- Include positive and negative prompt blocks separately
- Label a suggested model/checkpoint Proposed, with its basis and syntax limits

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
Update affected atoms and their rendered occurrences; preserve unaffected
substance. For a legacy brief without IDs, add the compact register once and
retain its exact source spans. Do not preserve unsupported legacy certainty as
newly verified fact: attribute the prior claim and keep its authority gap visible.
Bump the
version number on every re-issue, even a small one — a silent update is
worse than no update, because it destroys trust in the document itself.

Absent from the prior brief is Unresolved, never out of scope: when a vendor
asks about something v1 never mentioned, the answer is "not covered by the
current brief — decision needed." List the appropriate owner if known; routing
needed is not routing done. Do not claim "checking" or "will confirm" without an
evidenced action or stated commitment. Do not convert absence into "not included
in the fee"; commercial disposition needs the relevant parties' actual agreement
and otherwise stays Unresolved.

### 6C — Is This a Change Order?

Classify the edit against the actual agreement: clarification, correction
of a miss, included revision, or new scope. Inclusion in the revised document
is not itself an agreed change order. New scope may use an existing allowance,
an agreed change order, or an explicitly accepted favor; record only evidenced
terms, not an automatic billable classification. If terms or consent are unknown,
mark the commercial disposition Unresolved with routing needed to the relevant
approval owner (unknown if not supplied);
do not choose on behalf of either party. Preserve decision labels and sources
on changed fields. This is the same boundary used by outsource-intake.

### 6D — Change Log
Append a Change Log to the updated brief:

```
📝 CHANGE LOG — [Date or Version]
──────────────────────────────────
Section: [which section changed]
Change: [what changed]
Reason: [why — vendor question, stakeholder feedback, creative pivot]
Status: [clarification / correction / included revision / agreed allowance / agreed change order /
  agreed favor / Unresolved — label and source of the disposition]
Impact: [does this change cascade to other sections? If so, flag them]
Action state: [needed / planned / underway / done + source; preserve hedges]
Commercial treatment: [evidence or Unresolved; inclusion != change order]
```

### 6E — Re-output
Produce the updated full brief (all three output blocks) with changes
integrated. The Change Log is appended at the end, not inline.

**Output Block 3 (Generation Prompts) must be fully regenerated — do not
summarize or reference the previous version. Every prompt block must reflect
the updated brief at full fidelity.**

---

## Quality Standards

- **Decision provenance**: Confirmed / Observed / Proposed / Unresolved, with
  sources, survive every output and handoff. A class never grants approval.
- **Risk-scaled questions**: ask 2–4 at a time; no total cap that forces guessing.
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
- **Priorities are decisions too**: use sourced or Proposed weights; no forced
  🔴🟡🟢 assignment. Gate suggestions likewise never become mandatory by repetition.
- **Numeric reasons require sources**; unstated rationales stay Unresolved.
- **Every brief is versioned and dated, from v1** — not only once it's iterated.
- **Output all 3 blocks**: Art Direction Doc + Vendor Brief + Generation Prompts always
  (or Materials & Process Note for physical assets)
- **Reactive schema**: Use the correct asset-type schema — don't default to generic
- **Full fidelity, compact provenance**: preserve decisions, creative specificity
  and uncertainty in all three blocks; reuse one source register instead of
  repeating caveats or a ledger in every section.
- **Iteration-ready**: The brief structure must support versioning and change tracking.
  A post-kickoff edit carries an evidenced disposition, or stays Unresolved;
  new scope is never silently treated as included.

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

When image-decomp output is provided, map relevant analysis with its source
and uncertainty intact. It is not approved direction or proof of technical
budgets. Resolve consequential gaps before the Step 2 checkpoint without
re-asking for facts already captured.

## Companion Skill: outsource-intake

For scope, phases, sign-off, timeline, and files without full visual
direction, use **outsource-intake** instead — it's the lighter-weight
sibling to this skill and the two share vocabulary on purpose (Style
Authority vs. Approval Owner, Scope Boundaries, cost/timeline process
checks). outsource-intake can hand off to this skill for complex or
high-stakes asks; this skill's output can seed an outsource-intake request
when a full brief already exists and just needs to become a trackable ask.
Pass interpretation class, phase scope, decision labels/sources, approved
reference identifiers, roles, and open decisions with it. Reuse those fields
on return; do not promote a proposal or copy a stale readiness judgment after
the scope changes. Each skill remains usable without the other installed.

---

## Verification & Version Notes

Before delivery, check every technical number, date, role, reference, and
commercial disposition against its source. Confirm no Observed or Proposed
value became Confirmed through condensation, prompt generation, or handoff.
Check the class is evidenced, open decisions survive, and an exemplar has not
been mistaken for completion of new work. Exercise the debug/contact/action cases
in `references/debug-and-contacts.md`, plus comp-versus-inspected-reference labels
from `references/curated-comparisons.md`; retain outputs for independent review.

For regression testing, run sparse, exploratory, and production-batch requests
through both skills; retain actual outputs and check labels at the checkpoint
and final output. Also test partial confirmation, inaccessible references,
and mixed-class handoffs. Structural checks alone do not prove model behavior.
Condensation-specific regressions to check: Proposed requirements appearing
unlabeled in Output Block 2; assistant-authored exclusions stated as agreed
in Scope Boundaries; vendor replies answering undecided scope questions;
authority rulings expanded into new bans. Found via headless multi-case runs
(scratch/headless-rig/ in the skills repo).

**v2.7** — source-linked atoms before checkpoint and assembly; shared compact
source register; semantic source-to-clause comparison; reviewer/approver split;
optional evidenced priorities/gates; missing evidence distinguished from absence;
creative proposals and annotated prompts retained without approval promotion.

**v2.6** — explicit request-scoped debug artifacts with placeholders; six-role
contact appendix; evidence-backed curated comparisons and optional pitches;
action-state/hedge preservation; sourced numeric reasons; recipient proposals
without promises; inclusion and commercial disposition kept separate.

**v2.5** — condensation-layer fixes from headless-rig findings: per-bullet
provenance in Output Block 2; scope exclusions require a source (no invented
boundaries); authority rulings bounded to the contested dimension; labels
survive section moves (no laundering); sendable-message contract for
recipient-ready replies; Mode B: absent from the prior brief is Unresolved,
never out of scope.

**v2.4** — adds interpretation classes, four decision labels, class-aware
questioning/reference coverage, and provenance-preserving outputs/handoffs.
Relevant missing schema values remain visible. Commercial disposition follows
the agreed change boundary rather than being invented by the assistant.
Grounding: GRIP Field Journal, Rates & Tiers (engagement classes), Buyer
Readiness (explicit decisions), and The Brief (annotated targets). These are
procedural adaptations, not rate guidance or automatic approval. Existing
example images predate v2.4; they illustrate layout, not the decision-label
contract. Living-brief/rejection tracing is deferred.

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
