# Style Save (`*.style.json`) — spec v1.0

A **style save** is the machine-readable twin of a human art-direction doc
(an Art-Brief, an Image-Decomp report, a Vector-Translator exploration). The
human doc is for reading; the save is for resuming, diffing, and handing to the
next skill or tool without re-deriving anything. Schema: `style-save.schema.json`
(same folder). Source of truth lives in Skills-Private `shared/style-save/`;
every member skill carries a vendored copy in its own `references/`, so each
still works alone.

## Why it exists

Design talk fails on vocabulary before it fails on taste. "Make it more premium"
means five different things until both sides agree what "premium" points at,
and "the little leafy bits" stays vague until someone says *laurels*. The save
file records that alignment so it survives the conversation:

1. **Lexicon** — the shared vocabulary (a *ubiquitous language* for this
   project). Each term: what it means *here*, a plain gloss, image anchors, and
   `notThis` (the nearby readings it excludes).
2. **Parts** — the nomenclature map: the subject's named components as a tree.
3. **Axes** — named directions with a current and target position (0..1).
   **Palette** — key colors and their roles.
4. **Forks** — "did you mean A or B?" history: a vague ask split into named
   readings, each with its visible change and prompt, plus the user's pick.
5. **Refs, constraints, decisions, prompts** — what the brief already tracks,
   in structured form.

## File conventions

- Name: `<subject-slug>.style.json`, saved next to its human doc.
- One file per subject; skills **update** an existing save instead of starting
  a new one. Bump `meta.revision` on every write; append `skill@version` to
  `meta.producedBy` unless it is already the last entry. A brief's own version
  goes in `meta.briefRef`, not `revision`.
- IDs are stable and never recycled: `S` sources, `L` lexicon, `P` parts,
  `A` axes, `R` refs, `C` constraints, `D` decisions, `F` forks, `G` prompts.
  A new ID is the next unused number **in the save**; a human doc that has a
  save ingests the save's IDs before minting its own, so skills never collide.
- **One register, rendered twice.** When a human doc has a visible register
  (Art-Brief S/D atoms), the save uses the same IDs. Never renumber in one
  place and not the other.
- Only include sections you actually filled. Empty arrays are noise.

## Status rules (same labels as Art-Brief)

`Confirmed` (the user said it, or a document the user authored records it, quoted
with file:line) · `Observed` (seen in an inspected image or render, or read from a
file or code) · `Proposed` (assistant option) · `Unresolved` (open).

- **Nothing is promoted by copying.** A status carried from one skill to
  another, or from the human doc to the save, keeps its label.
- Image analysis yields `Observed` (what's visible) or `Proposed` (a term or
  reading the assistant offers). Never `Confirmed`.
- A lexicon term becomes `Confirmed` only when the user adopts or states it.
- A fork's `picked` is set **only** from the user's own reply, with that reply
  quoted in `pickSpan`. Until then `picked` is `null`.
- Every lexicon term except `kind: part` requires at least one `notThis`.
- A fork raised by a review finding (not a user ask) sets `originDecision` to the
  finding's D-id; its `ask` is the finding's one-line problem. The pick still comes
  only from the user's reply.
- Review findings are `Unresolved` decisions with `scope: "review finding"`,
  a `severity`, and the finding type in `scope` ("review finding · inconsistency").
- Evidence read from code or config uses a `code` source (`ref` = path:line); a
  captured render uses a `render` source. Palette entries cite their `source`.
- `hedge` holds only qualifiers the source itself stated. The assistant's
  interpretation of a Confirmed statement is a separate `Proposed` atom that
  cites it, never folded into the Confirmed one.
- A value the user typed (their budget, their deadline) is `Confirmed`;
  anything derived from it is `Proposed`.

## Interactive edits (paste-back from an interactive view)

An interactive view (see `shared/interactive/SPEC.md`) lets the user tweak the save and
copy it back. The pasted block is the **full save**, `meta.revision` bumped by the view.

- A field the user touched in the view (slider moved, term renamed or adopted, fork
  picked) is `Confirmed`, with `sourceSpan: "interactive edit <YYYY-MM-DD>"`. For a
  fork, `pickSpan` is the same string.
- Every field they did not touch keeps its prior status. Never promote by copying.
- On paste-back, diff against the last save you hold. A change with no matching
  edit mark, or a status that rose without one, is reported to the user, not accepted.
- Run the validator when available, otherwise check required fields by eye, then
  continue the loop from the pasted save.

## Who writes what

| Section | Primary writer | Readers |
|---|---|---|
| `lexicon`, `parts` | image-decomp (Observed/Proposed); art-brief interview (Confirmed) | everyone |
| `palette` | image-decomp, art-brief | everyone |
| `axes`, `forks` | vector-translator | art-brief, image-decomp regen prompts |
| `refs` | ref-synthesizer, ref-validator, image-decomp | art-brief |
| `constraints` | constraint-shaper, art-brief | art-brief |
| `decisions` | art-brief (mirror of its register) | outsource-intake via `briefRef` |
| `prompts` | image-decomp, vector-translator, art-brief | generation tools |

Any skill may write any section it has evidence for; the table is who usually does.

## Reading a save

When a user supplies a `*.style.json` (or one sits next to the doc being worked
on), load it first: reuse its terms in your wording, don't re-ask what it
already records, and treat its statuses as-is. Validate against the schema when
a validator is available; otherwise check required fields by eye.

## Minimal example

```json
{
  "schema": "style-save/1.0",
  "meta": { "subject": "clan crest", "revision": 2, "updated": "2026-09-28",
            "producedBy": ["image-decomp@3.2", "vector-translator@1.1"] },
  "sources": [ { "id": "S1", "kind": "image", "ref": "crest_v3.png" },
               { "id": "S2", "kind": "conversation", "ref": "msg 4" } ],
  "lexicon": [
    { "id": "L1", "term": "laurels", "kind": "part",
      "means": "the pair of leafy branches curving up either side of the shield",
      "gloss": "victory-wreath branches, like on a medal", "status": "Confirmed",
      "sourceSpan": "S2: \"yes, the laurels\"" },
    { "id": "L2", "term": "premium", "kind": "quality",
      "means": "fewer, finer strokes; restrained metallic accent",
      "notThis": ["more gold everywhere", "more ornament"], "status": "Proposed",
      "sourceSpan": "assistant proposal; based on F1" }
  ],
  "parts": [ { "id": "P1", "name": "shield", "status": "Observed",
               "anchor": { "source": "S1", "xy": [0.5, 0.5] } },
             { "id": "P2", "name": "laurels", "lexiconId": "L1", "parent": "P1",
               "status": "Observed", "anchor": { "source": "S1", "region": "left and right of shield" } } ],
  "axes": [ { "id": "A1", "name": "ornament density", "low": "bare shapes",
              "high": "every surface engraved", "current": 0.7, "target": 0.4,
              "status": "Proposed" } ],
  "forks": [ { "id": "F1", "ask": "make it feel more premium", "askSource": "S2",
               "options": [
                 { "key": "a", "reading": "restraint", "change": "thin the laurels to 5 leaves a side, single gold accent",
                   "axisDeltas": [ { "axis": "A1", "delta": -0.3 } ] },
                 { "key": "b", "reading": "richness", "change": "add engraved bevel and gradient gold",
                   "axisDeltas": [ { "axis": "A1", "delta": 0.2 } ] } ],
               "picked": null } ]
}
```
