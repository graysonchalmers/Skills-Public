# Release notes — Outsource-Intake v1.5

## What changed

**Source-linked rendering contract.** The intake now loads a compact source/decision register before the first extraction summary, recap, or sheet assembly. Every condensed claim renders from a register atom with an inline ID and source key. This prevents the provenance drift, reviewer-to-approver inference, and missing-to-nonexistent upgrades that the v1.4 run4 sweep found.

**Separate reviewer and approver.** A named reviewer does not establish procedural approval authority. Style authority is recorded separately from the approval owner, even when the same person holds both. File drop destination is not a feedback channel.

**Missing ≠ nonexistent.** "Not supplied" stays "not supplied" — it never becomes "none exist" or "out of scope" without an explicit source. A prior call establishes contact, not prior engagement or vetting. An existing partner claim from the user is attributed input; an assistant inference of a relationship is Proposed.

**Optional, not mandatory.** Phase templates are offered as Proposed when useful, not silently applied. An empty process is Unresolved, not a requirement to invent gates. Criticality inferred from context is Proposed, not a settled priority.

**Mini-sheet is a separate route.** Internal, single-asset, low-stakes asks get a compact ≤250-word core with at most five questions total and one readiness line — no Stage A/B/C ceremony, no phase template. The full six-role contact appendix and compact source register sit outside the cap.

**Adaptive frontier interview.** Normal mode now registers supplied facts first, asks only 2–4 consequential questions from the current decision frontier, recomputes after each answer, and records a source-linked interview trace. Sparse requests get deeper questioning; dense requests stay quiet. Debug remains immediate and question-free. The mini route remains capped at five total questions.

**Semantic example chips.** Public cards keep dark-neutral surfaces while using restrained muted accents for Borrow/Avoid/Target and Critical/Important/Nice-to-have. Color communicates role or priority, not approval status.

**Debug is request-scoped.** Debug previews use placeholder tokens or clearly synthetic Example values. The override ends with the request; the next request returns to normal gates. Synthetic fixture values stay Proposed, never Confirmed or Ready.

## Behavioral evidence

11/11 synthetic cases passed independent review against the specific failures from the prior run. See `scratch/art-intake-release/run5-REVIEW.md` for the per-case evidence table. This is one synthetic run per case, not a measured reliability rate.
