# Release notes — Art-Brief v2.9

## v2.9 — style save sidecar and Terms glossary

**Style save sidecar.** Art-Brief can now emit `<subject>.style.json` next to its three output blocks: when the brief is written to disk, when asked, or when a save was supplied (then it updates it). One register, rendered twice: `decisions[]` mirror the visible D-atoms with the same IDs, `sources[]` the S-key, `lexicon[]` the glossary's L-ids. Contract: vendored `style-save.md` + `style-save.schema.json`; mapping: new `style-save-mapping.md`.

**Terms we use.** The Art Direction Document carries a glossary of the project's vocabulary (term — what it means here — not this — status), rendered from L-id atoms, plus parts nomenclature when the asset has named parts.

**Vocabulary forks in the frontier.** A loaded style word ("premium", "gritty") is a candidate consequential question when its readings change the output: asked as a did-you-mean fork with 2–3 named readings, inside the existing 2–4-per-round limit. The pick comes only from the user's quoted reply and is recorded as a lexicon atom.

**Mode B ingests a save first.** Keeps its IDs and statuses, doesn't re-ask what it records, bumps `meta.revision`, appends `art-brief@2.9` to `producedBy`, sets `briefRef`.

**image-decomp v3.2 mapping.** Companion table adds `pitchLines` (thesis/pitch), `parts` + `lexicon` (glossary, Observed/Proposed until confirmed), `elementUtility` + `compositionGeometry` (composition/focal), `intent` (descriptive viewer effect, not a requirement unless confirmed).

**Verification covers the sidecar.** No Observed/Proposed value becomes Confirmed in the save through condensation, handoff, or copying; fork picks quote the user's own reply. Companions (Vector-Translator, ref-validator/ref-synthesizer, constraint-shaper) may fill save sections if installed; none is required. Example renders are unchanged from v2.8.

## v2.8 (with Outsource-Intake v1.6) — what changed

**Role-boundary split: art bible vs. production.** Art-Brief is now the style-authority record — the art bible. Outsource-Intake is the delivery-authority record — scope/change policy, contacts, review process, commercial terms, milestones. The only coupling point is `brief_ref`: an intake packet consumes a brief by reference and never re-derives its art decisions; a brief that will drive a vendor engagement carries an open pointer (`brief_ref [ID] / Unresolved — no intake on file`) instead of logistics blocks.

**Logistics blocks left the brief.** Scope Boundaries & Change Policy, Contact Directory, Process, and Delivery & Milestones are no longer composed in an Art-Brief output. The Vendor Brief now carries a one-line logistics pointer; style avoids stay strictly stylistic, with work-scope rulings routed to intake.

**Creative-only interview.** Art-Brief's adaptive frontier questions resolve creative ambiguity only — reference conflicts, stylization floors, mood, interpretation latitude. It never interviews for reviewer names, channels, dates, payment, or change-order terms; volunteered facts are registered and passed through to intake.

**Change-order disposition deferred.** Art-Brief Mode B still classifies an edit (clarification / correction / included revision / new scope) but routes the commercial disposition to the intake packet's change-order rule instead of deciding it.

**Consuming a brief by reference (Outsource-Intake v1.6).** When an art-brief document exists, intake cites it as `brief_ref`, copies its decisions with provenance, never re-interviews them, flags "no brief on file" as a visible gap with a handoff offer, and routes conflicts against the brief back to its register instead of resolving them in the sheet.

**Source-linked rendering contract.** Both skills load a compact source/decision register before any checkpoint, recap, or assembly. Every condensed claim renders from a register atom with an inline ID and source key — not from a freehand summary of another output block.

**Separate reviewer and approver roles.** A named reviewer no longer populates procedural approval ownership. Style authority is scoped to the dimensions it actually rules; a proportions ruling does not ban rendering styles or require new sign-off gates.

**Missing ≠ nonexistent.** "Not supplied" stays "not supplied" — it never becomes "none exist" or "out of scope" without an explicit source. Requested dates stay requested, not agreed. A file drop is not a feedback channel.

**Optional, not mandatory.** Priority weights, milestone structures, and phase templates are offered as Proposed when useful, not forced into every output. An empty plan is Unresolved, not a requirement to invent M1–M4.

**Mini-sheet is a separate route.** Internal, single-asset, low-stakes asks get a compact ≤250-word core with at most five questions and one readiness line — no Stage ceremony, no phase template. The full six-role contact appendix sits outside the cap.

**Adaptive frontier interview.** Normal mode now registers supplied facts first, asks only 2–4 consequential questions from the current decision frontier, recomputes after each answer, and records a source-linked interview trace. Sparse requests get deeper questioning; dense requests stay quiet. Debug remains immediate and question-free.

**Semantic example chips.** Public cards keep dark-neutral surfaces while using restrained muted accents for Borrow/Avoid/Target and Critical/Important/Nice-to-have. Color communicates role or priority, not approval status.

**Debug is request-scoped.** Debug previews use placeholder tokens or clearly synthetic Example values. The override ends with the request; the next request returns to normal gates. Synthetic fixture values stay Proposed, never Confirmed or Ready.

## Behavioral evidence

11/11 synthetic cases passed independent review against the specific failures from the prior run. See `scratch/art-intake-release/run5-REVIEW.md` for the per-case evidence table. This is one synthetic run per case, not a measured reliability rate.

## Earlier versions

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
procedural adaptations, not rate guidance or automatic approval. Example cards were regenerated against the v2.8 role-boundary layout
(logistics pointer, no scope/process blocks); they illustrate layout and
honest labels, not the full v2.7 source-register contract. Living-brief/rejection tracing is deferred.

## Maintainer regression checks

Exercise the debug/action cases in `references/debug-and-contacts.md` (the
contact-directory cases are outsource-intake's; the brief carries only the
logistics pointer), plus comp-versus-inspected-reference labels from
`references/curated-comparisons.md`; retain outputs for independent review.

For regression testing, run sparse, exploratory, and production-batch requests
through both skills; retain actual outputs and check labels at the checkpoint
and final output. Also test partial confirmation, inaccessible references,
and mixed-class handoffs. Structural checks alone do not prove model behavior.
Condensation-specific regressions to check: Proposed requirements appearing
unlabeled in Output Block 2; any Scope Boundaries / Contact Directory /
Process / Milestones content composed into a brief (these belong to intake —
only the logistics pointer may appear); vendor replies answering undecided
scope questions; authority rulings expanded into new bans. Found via headless
multi-case runs (scratch/headless-rig/ in the skills repo).
