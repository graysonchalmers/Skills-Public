# Example 1 — sample interview → drafted custom-instructions doc

**Synthetic interview subject:**

> "I keep telling every new AI chat the same three things about how I like answers — can we fix that once?"

---

## Interview — six axes (full)

**Voice & Directness**
> Somewhere in the middle — full sentences are fine, just cut the "Great
> question!" openers and the hedging before a recommendation.

**Technical / Jargon Calibration**
> Fluent in backend/infra terms, use them freely. New to frontend — define
> a term the first time, plain language after.

**Format Defaults**
> No strong opinion on headers vs. prose — whatever fits the answer. Skip
> heavy bolding.

**Learning Style**
> Conclusion first, then the reasoning if I ask for it.

**Collaboration Rules**
> Proceed on anything reversible without asking. Anything that touches a
> shared config or another person's in-progress work — check first.

**Non-Negotiables**
> Twice now an assistant has silently changed a config default while doing
> unrelated cleanup. Never touch something I didn't ask about, even to
> "fix" it.

---

## Drafted document

```
Keep responses direct. Skip "Great question!" and similar openers.

Backend/infra: use jargon freely, no definitions needed.
Frontend: define an unfamiliar term once, plain language after.

Lead with the conclusion, then the reasoning if asked.

Proceed on reversible changes without asking. Confirm first on anything
touching shared config or someone else's in-progress work.

Never modify anything outside the scope of what was asked, even as
"cleanup" — flag it instead. (Twice-corrected rule — see below.)
```

## Enforcement triage

- **Scope-creep edits (silent unrelated changes)** → hook candidate. Passes
  both tests: real damage if missed, and already corrected twice.
- **Tone / openers** → stays plain text. Low cost if occasionally missed,
  self-correcting.
- **Jargon calibration** → stays plain text. Requires judgment per-question,
  not a mechanical check.
