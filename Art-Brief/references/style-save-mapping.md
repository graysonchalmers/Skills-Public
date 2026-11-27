# Style save ↔ brief mapping (Art-Brief v2.9)

How Art-Brief reads and writes a style save (`<subject>.style.json`). The
contract itself is `style-save.md` + `style-save.schema.json` in this folder
(vendored, frozen; do not edit them here). This file only says which part of
the brief each save section mirrors. Ordinary Markdown/JSON; no runtime needed.

## 1. One register, rendered twice

The visible source/decision register (`source-linked-output.md`) is the single
record. The brief renders it for people; the save renders it for tools.

| Brief (visible) | Save section | ID rule |
|---|---|---|
| Source key S1, S2… | `sources[]` (`kind`: conversation, image, brief, decomp, text, other) | same S-ids |
| Register D-atoms | `decisions[]` (`value`, `status`, `sourceSpan`, `hedge`, `scope`) | same D-ids, one-to-one both ways |
| 📖 Terms we use | `lexicon[]` (`term`, `kind`, `means`, `notThis`, `gloss`, `status`, `sourceSpan`) | same L-ids |
| Terms we use: parts nomenclature; schema fields for named components | `parts[]` (`name`, `parent`, `lexiconId`, `anchor`) | same P-ids |
| Visual Language: color palette (hex values only) | `palette[]` (`hex`, `role`, `status`) | no ID; cite roles as written |
| Artistic References (supplied/inspected, with borrow/avoid/target) | `refs[]` (`source` = an S-id, `use`, `dimension`, `why`) | R-ids |
| Technical Spec numbers; brand/fidelity/engine constraints | `constraints[]` (`kind`, `value`, `impact`) | C-ids |
| Direction statements that move along a named axis | `axes[]` (`low`, `high`, `current`, `target`) | A-ids |
| Interview-trace vocabulary questions (did-you-mean) | `forks[]` (`ask`, `options`, `picked`, `pickSpan`) | F-ids |
| Block 3 prompt blocks | `prompts[]` (`target`, `text`, `negative`, `derivedFrom`) | G-ids |
| Header version/date | `meta.briefRef`; `meta.humanDoc` = brief filename | — |

Rules:

- **Decisions mirror exactly.** Every D-atom in the register appears in
  `decisions[]` with the same ID, value, status, hedge and scope; the save holds
  no D-id the register lacks. Map the register columns: Value → `value`,
  status → `status`, Source span → `sourceSpan`, Hedge/action state → `hedge`,
  Scope/role limit → `scope`.
- **Typed sections are views, not new facts.** When a palette entry, ref,
  constraint, axis target or prompt restates a D-atom, it carries that atom's
  status and cites it as `[Dn]` in a free-text field (`value`, `why`, `impact`,
  `evidence`, `note`) or in `derivedFrom` for prompts. Split an atom rather than
  give one typed entry two statuses.
- **Only what the save can hold honestly.** Palette needs a hex; a color named
  only in words stays in the brief. `refs[]` needs an S-id source, so assistant-
  proposed comparisons without a supplied/inspected source stay as Proposed
  D-atoms (mirrored in `decisions[]`), not refs. Logistics facts the user
  volunteered stay D-atoms scoped `pass-through to outsource-intake`; they are
  not written as `timeline` constraints.
- Include only sections you filled. Empty arrays are noise.

## 2. Glossary atoms (L-ids)

Glossary rows are register atoms with L-ids in the same table as D-atoms, so
the Terms glossary renders from them like any other block. Reuse a supplied
save's L-ids; new terms take the next free number. Kinds follow the schema:
`part`, `style`, `quality`, `motif`, `technique`. `style`/`quality` terms need
at least one `notThis`; if the user gave none, the term stays Proposed or
Unresolved, never Confirmed with an invented exclusion. A term becomes
Confirmed only when the user adopts or states it (quote the span).

Did-you-mean flow inside the frontier interview (`frontier-interview.md`):
the vague word's ask → an F-id with 2–3 named options (each `reading` +
visible `change`) → the user's reply sets `picked` and `pickSpan` verbatim →
the resulting meaning is written to an L-atom listed in `lexiconAdded`. No
reply, or a general "sounds good", leaves `picked: null`.

## 3. Ingesting a supplied save

Do this before the first checkpoint (Mode A) or before 6A's diff (Mode B):

1. Validate against `style-save.schema.json` when a validator is available;
   otherwise check required fields by eye. Report failures; don't silently fix.
2. Seed the register from it: S-ids, D-ids, L-ids and P-ids keep their numbers.
   New atoms take the next free number per prefix; IDs are never recycled.
3. Treat statuses as-is. Observed/Proposed from image-decomp, vector-translator
   or any other writer stay Observed/Proposed; a recorded source you cannot
   re-inspect keeps its attribution ("Observed per image-decomp on S1, not
   re-inspected here").
4. Remove what it answers from the frontier. An open fork (`picked: null`) is
   still a candidate frontier question: ask for the pick, don't re-derive the
   readings. A recorded Confirmed term is not re-asked.
5. On write: bump `meta.revision`, set `meta.updated`, append `art-brief@2.9`
   to `meta.producedBy` (unless already last) (never reorder or drop earlier entries), set
   `meta.briefRef` to the brief's version/date and `meta.humanDoc` to its
   filename when it is on disk. Leave other writers' sections intact unless the
   brief changed the underlying atom.

## 4. Emitting a new save

When the brief is written to disk, the user asks, or a save was supplied:
write `<subject-slug>.style.json` next to the brief. Minimum: `schema`, `meta`
(`subject`, `revision`, `updated`, `producedBy`, `briefRef`), `sources`, and
`decisions`; add `lexicon`/`parts` whenever the glossary has rows. Mode B
re-issues bump both the brief version and `meta.revision` together.

## 5. Companions (optional)

Art-Brief is complete without any companion. If installed:
image-decomp (v3.2) supplies `parts`, `lexicon`, `palette`, `refs`, `prompts`;
Vector-Translator supplies `axes`/`forks`; ref-validator / ref-synthesizer
supply `refs`; constraint-shaper supplies `constraints`. Their entries keep
their statuses; the brief's register adopts their IDs instead of renumbering.

## 6. Pre-delivery check

- `decisions[]` IDs = register D-ids; `lexicon[]` IDs = glossary L-ids.
- No status in the save is higher than in the register (Observed/Proposed never
  become Confirmed through condensation, handoff or copying).
- Every `picked` has a `pickSpan` that is the user's own quoted reply.
- `meta.producedBy` ends with `art-brief@2.9`; `revision` bumped; `briefRef` set.
