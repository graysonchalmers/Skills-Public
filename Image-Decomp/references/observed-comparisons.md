# Observation-first art direction

Shared standard for visual work across projects. Use it with the relevant authoring workflow; it does not replace that workflow or authorize extra edits. Review actual output for new visuals. When a real baseline exists, compare it. Do not invent a Before for new work or turn a small visual task into an exhaustive report.

## Evidence before explanation

- Open the actual images/renders before drafting visible-change claims. Inspect scene/normal viewing scale and useful native detail. Read implementation notes afterward to investigate causes; intention, settings and passing tests do not prove a visible improvement.
- Verify which outputs are being compared. Match camera, viewport/state, seed, lighting and relevant settings when possible. Disclose intentional differences; confounded captures cannot isolate a cause.
- Select 1–3 consequential differences supported by the images. For each give: **location → visible Before → visible After → artistic effect → verdict**. Verdicts: improved, mixed, regressed, inconclusive. Separate observation from interpretation and causal hypotheses.
- A change can be visible yet worse. A visible difference is not automatically an improvement. Distinguish user acceptance from the reviewer's provisional judgment.
- If something is only visible under magnification, say small/local. If imperceptible or not demonstrated, omit its visual highlight and state that limitation. Unchanged regions may orient the reader, but must not be presented as changed.

## Let the reader see the evidence

- Default to numbered boxes/circles on **Before**, a clean **After**, a context pair and identical enlarged crops of the marked locations. Prefer one clear example over a wall of weak comparisons. For a single image, mark observed issues on a separate review copy; retain its clean original.
- Captions say exactly where to look and what is visible in each view. Use concrete terms such as silhouette, value contrast, spacing, edge density, material response or gaze hierarchy only when they help describe the actual artifact.
- Match crop coordinates and magnification. Keep marks off the evidence they explain. Use neutral location markers for areas where new content appears; do not label empty Before space a defect merely because After adds something.
- Preserve original screenshot pixels and provenance. Use HTML/SVG overlays or the project's existing review renderer; do not generatively redraw the source to annotate it. No independent auto-crops, exposure/color changes or beauty lighting to make a result appear stronger. Disclose any requested presentation treatment.
- Say when image evidence cannot establish collision, reliable grounding, animation, accessibility, responsive behavior or performance. Report measured behavior separately and only when actually checked.

## Useful compact output

For a comparison: one sentence on overall impact, 1–3 numbered observations with verdicts, matched annotated/clean evidence, and the most consequential remaining issue. Scale detail to the task. Keep code changes, tested behavior and visible art judgment distinct.

For new output without a baseline: inspect the actual final artifact against the brief, identify the strongest visible quality and the leading issue, and state what remains unverified. Do not fabricate a comparison or demand a before/after package.

Example: “Below the flat stone, grass reaches the edge in Before; After exposes a green strip. The stone separates more clearly, but the strip reads as a cleared moat: mixed.” A few new tan leaves may be a small/local change, not proof of better overall scatter or correct grounding.
