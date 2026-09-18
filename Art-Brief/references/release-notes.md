# Release notes — Art-Brief v2.8 / Outsource-Intake v1.6

## What changed

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
