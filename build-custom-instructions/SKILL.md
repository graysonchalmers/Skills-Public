---
name: build-custom-instructions
visibility: public
description: >
  Interviews a person about how they want an AI assistant to communicate with
  them — tone and directness, technical/jargon level, output format, learning
  style, collaboration rules — and drafts a personal custom-instructions
  document (CLAUDE.md / AGENTS.md / system-prompt style) from their answers,
  plus an optional layer of hard-enforced rules via hooks for anything that
  needs to be guaranteed rather than just requested.

  Use this whenever someone wants to write, improve, or start from scratch on
  their custom instructions, system prompt, CLAUDE.md, AGENTS.md, or "how
  should the AI talk to me" preferences — even if they don't know the term
  for it and just say things like "I want Claude to stop explaining stuff I
  already know," "can I make it match how I actually talk," or "I want a doc
  like the pros have for tuning their assistant." Also trigger when someone
  wants to onboard a new teammate, client, or themselves onto a fresh Claude
  Code / agent setup and needs a communication-preferences doc to start from.
---

# Build Custom Instructions

## Why this exists

Most friction with an AI assistant traces back to a handful of dials that
were never set explicitly — tone, technical level, format, how the person
learns, when to act versus ask. Left unset, the assistant guesses at a
generic user. A short, explicit doc removes the guessing. A few of those
dials matter enough that "described" isn't reliable under pressure — those
need to be *enforced*, not just requested (Step 3).

## Ground rule: opinionated about structure, neutral about content

Two different things are being offered here, and they get different
treatment. The **shape** of a good custom-instructions doc — six axes,
second-person imperative, attach the why to each rule, keep it short enough
to actually get read — is not up for debate per-interviewee. Recommend it
freely, lead with it, use the template and its example lines as real
starting drafts the interviewee edits rather than blank-page scaffolding.

The **content** — what this specific person's tone, jargon level, and
non-negotiables actually are — belongs entirely to them, and that's where
leading does damage: an example offered to unstick someone can quietly
become the answer just because agreeing was easier than generating
something new. If someone's response is just an example phrasing echoed
back verbatim, don't take the echo as their answer — follow up with a
contrast ("more like X, or more like Y?") that forces them to react instead
of confirm.

## Step 0 — Orient: Bootstrap or Refine

Ask whether a custom-instructions doc already exists for this person. The
two answers lead to genuinely different procedures — this isn't a one-time
interview that either happens or doesn't, it's a bootstrap-then-refine loop:

- **No doc yet → Bootstrap mode.** Run Step 1 for a good-enough baseline,
  not an exhaustive one. Don't chase precision on every axis in the first
  pass — a rough-but-real answer on all six beats a perfect answer on two.
  End with an explicit checkpoint (Step 4½): "this is a baseline, go use it
  for a while, come back once you notice something it gets right or
  wrong." The doc is deliberately a first draft to be lived with, not a
  finished artifact.
- **Doc already exists → Refine mode.** Read it first and don't re-run the
  full six-axis interview — that re-litigates settled ground and wastes
  the person's patience. Ask what they've noticed since they started using
  it: what's worked, what's been wrong, what they've caught themselves
  correcting. Translate specific, lived feedback into targeted edits to
  the specific rules it concerns, going back to Step 1's relevant axis
  only for the parts that are actually in question. See Step 4½.

The conversation itself is also signal in either mode: how the person is
already writing to you (terse vs elaborate, formal vs casual, jargon-heavy
vs plain) is real evidence, not something to ask about from scratch.

If this doc is for someone other than the interviewee (a teammate, a
client, a template for a team), ask who the subject is first — the
questions below assume the interviewee is describing themselves.

## Step 1 — The interview

Run this as an actual back-and-forth, not a form dump. Batch it — a few
questions at a time (the `AskUserQuestion`-style tool if the platform has
one, otherwise 2–3 questions per conversational turn) — so it doesn't read
like a twenty-item survey. Six axes, one real question each:

1. **Voice & directness** — how much fluff, hedging, and pleasantries
   should get stripped versus kept? Full sentences or terse fragments
   welcome? Any tone that actively grates (cheerleading, apologizing,
   corporate-speak, excessive caveats)? Offer a quick numeric dial as a
   shortcut ("fluff stripped, on a scale of 1–10?") alongside the open
   question — some people can point at a number faster than they can
   describe a tone, and a dial is also something a future session can
   re-tune in one line without re-running the whole interview. The number
   is a shortcut into the same answer, not a replacement for it — still
   capture what the number means in their words (see Step 2's drafting
   rule on this).
2. **Technical / jargon calibration** — flat across domains, or does it
   vary ("assume expert in X, explain everything in Y")? Ask directly
   whether it varies by domain — don't let this collapse to one flat
   answer by default. If they name more than one domain, capture each
   one's calibration separately in the final doc rather than averaging
   them into a single vague middle ground. Should unfamiliar terms get a
   one-line gloss, get skipped entirely, or wait until the person asks?
3. **Format defaults** — headers and bullets, or prose paragraphs? Summary
   up front or at the end? Anything that reads as noise (heavy bolding,
   emoji, tables for facts that don't need one)?
4. **Learning style** — try to pick this up from *how* they've already
   answered the other five rather than asking it head-on: did they reach
   for an analogy unprompted, organize an answer step-by-step, or give the
   conclusion before the reasoning when explaining something? That's
   usually enough signal. Ask directly only when it's genuinely unclear —
   punchline first then reasoning, or reasoning then conclusion? Do
   analogies help or just add length? Step-by-step or big-picture-first?
5. **Collaboration rules** — when should the assistant just act versus
   check first? Best-guess-and-flag or stop-and-ask under uncertainty? If
   someone doesn't have a strong opinion here, a solid default to offer:
   act autonomously on anything reversible/low-stakes; for anything that's
   a real decision, generate 3–5 concrete options with a recommendation
   picked from among them, then confirm direction before proceeding rather
   than freezing until asked or barreling ahead alone. Offer it as a
   starting point to react to, not the only shape — see the ground rule
   above. Any standing always/never rule that came from a specific past
   frustration — name the incident if there is one, it's the strongest
   evidence available.
6. **Non-negotiables** — anything they've corrected more than once, with
   any assistant, human or AI. Usually the single highest-signal answer of
   the six, because it's not hypothetical.

`references/template.md` has the fill-in-the-blank shape each answer maps
to, plus starting-draft example lines for each section — offer these
freely as a first pass to react to and edit, not just when someone's stuck.
They're generic on purpose so the interviewee's real answer visibly
replaces them rather than blends into them.

## Step 2 — Draft the document

Draft a `CLAUDE.md`-style file using the structure in
`references/template.md`. Drafting rules worth holding to:

- **Second person, imperative.** "Keep responses terse," not "The user
  likes terse responses." It's an instruction to the assistant, not a bio.
- **Attach the why where one exists.** A rule with a remembered reason
  survives edge cases a bare directive doesn't — if the interviewee gave a
  reason, keep it attached to the rule, not dropped for brevity.
- **Pair a numeric dial with prose, never alone.** If axis 1 produced a
  number, put it up top as a quick-reference line ("Directness: 8/10") but
  keep the prose rule right under it. The number is fast to re-tune later;
  the prose is what actually tells a future session what the number means.
- **Length that gets read.** A 30-line doc that's actually followed beats a
  300-line doc that gets skimmed once and ignored thereafter.
- **Show the draft, don't just hand it over.** Ask what's wrong before
  calling it done — first drafts of self-description are almost always
  slightly off, and the correction is where the real signal shows up.

## Step 3 — Decide what needs enforcement, not just description

Plain text the model reads holds up fine for most rules. A few get broken
exactly when they matter most — long session, model "forgets," the rule
never had a mechanical trigger to begin with. Those need a deterministic
check, not a request. Read `references/hook-enforcement.md` for how to tell
which is which. For the actual wiring: if the current harness has its own
config/hooks skill available (e.g. Claude Code's `update-config`), hand it
off there rather than reimplementing hook mechanics here. Otherwise, state
the hook as a trigger/condition/action triple and let the interviewee wire
it into whatever their harness uses — the mechanics are platform-specific,
the triple isn't.

Don't ask this as a fresh question — it's a re-examination of what already
came out of axes 5 and 6 (collaboration rules and non-negotiables usually
surface the repeat-correction stories), scored against the two tests in
`references/hook-enforcement.md`. Only go back to the interviewee if
severity or repetition is genuinely unclear from what they already said.
Those that qualify are the hook candidates; everything else stays as plain
instructions.

## Step 4 — Place it

Ask where it lives before finishing — global (a user-level `CLAUDE.md` or
equivalent), project-level (`CLAUDE.md` / `AGENTS.md` in a repo, checked in
or not), or a portable block to paste into whatever tool comes next. Scope
changes content: a project-level file shouldn't carry personal
communication preferences that belong globally, and a global file shouldn't
carry one project's local conventions.

## Step 4½ — Set the checkpoint (Bootstrap) or close the loop (Refine)

**Bootstrap mode ends here, not at "done."** Say plainly that this is a
baseline, not a finished product: they should go use it for a while and
come back once they've noticed something specific — a rule that's wrong,
a rule that's missing, a rule that turned out to not matter. A vague "let
me know if you want changes" doesn't produce a return visit; a concrete
"come back once you've noticed something" does, because it gives them a
trigger condition instead of an open-ended invitation.

**Refine mode closes by confirming the specific edits landed**, not by
re-validating the whole doc. If their feedback only touched two rules,
show them those two rules changed — don't re-walk all six axes just
because you're already in the file. Re-run Step 3's enforcement check only
on what changed; a rule that already passed or failed that test doesn't
need re-litigating because an unrelated rule got edited.

## Quality standards

- The interviewee's own words show up in the doc more than the skill's
  example phrasings do
- Every axis got a real answer, not a skipped default
- The doc reads as instructions to the assistant, not notes about the user
- Enforcement candidates each have a repeat-correction story, not just a
  feeling of importance
- Nothing in the drafted doc assumes personal facts (name, employer,
  projects, secrets) the interviewee didn't explicitly choose to include
- Bootstrap runs end with a concrete return trigger, not an open-ended
  "let me know"; Refine runs touch only what the feedback actually named

## Example triggers

- "Can you help me write a CLAUDE.md that actually captures how I like to work?"
- "I keep telling every new AI chat the same three things about how I like answers — can we fix that once?"
- "Set up custom instructions for my team's new Claude Code rollout"
- "I want something like a system prompt but for my own communication style"

## Companion skills

| Skill | Relationship |
|---|---|
| `update-config` | Downstream — wires any rule that needs hard enforcement into an actual hook |
| `pickup` / `wrap-up` | Unrelated lifecycle skills that may reference the resulting doc once it exists |

## Version notes

**v1.0 baseline**
- Interview-first, template-assisted; no automated hook generation of its
  own — identifies enforcement candidates and hands wiring to whatever
  config/hooks skill the current harness provides, if any
- Not yet run against a real second party
- Bootstrap/Refine is a human-in-the-loop cycle (Step 0, Step 4½), not a
  standing background system — nothing updates the doc automatically or
  between sessions on its own. The person has to come back and say what
  they noticed; the skill doesn't watch, poll, or remember on its behalf.
  A true continuously-self-updating mode (something tracking real usage
  and proposing edits without being asked) is a bigger, still-deferred
  idea — this only covers the "they return with real feedback" half.
