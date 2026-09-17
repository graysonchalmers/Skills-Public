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

## Step 0 — Orient

Ask whether this is a blank slate or a refinement of an existing file. If
refining, read the existing file first and extract what's already implicit
— don't re-ask what's already answered. The conversation itself is also
signal: how the person is already writing to you (terse vs elaborate,
formal vs casual, jargon-heavy vs plain) is real evidence, not something to
ask about from scratch.

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
   corporate-speak, excessive caveats)?
2. **Technical / jargon calibration** — flat across domains, or does it
   vary ("assume expert in X, explain everything in Y")? Should unfamiliar
   terms get a one-line gloss, get skipped entirely, or wait until the
   person asks?
3. **Format defaults** — headers and bullets, or prose paragraphs? Summary
   up front or at the end? Anything that reads as noise (heavy bolding,
   emoji, tables for facts that don't need one)?
4. **Learning style** — punchline first then reasoning, or reasoning then
   conclusion? Do analogies and examples help or just add length?
   Step-by-step, or big-picture-then-detail?
5. **Collaboration rules** — when should the assistant just act versus
   check first? Best-guess-and-flag or stop-and-ask under uncertainty? Any
   standing always/never rule that came from a specific past frustration —
   name the incident if there is one, it's the strongest evidence available.
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

## Quality standards

- The interviewee's own words show up in the doc more than the skill's
  example phrasings do
- Every axis got a real answer, not a skipped default
- The doc reads as instructions to the assistant, not notes about the user
- Enforcement candidates each have a repeat-correction story, not just a
  feeling of importance
- Nothing in the drafted doc assumes personal facts (name, employer,
  projects, secrets) the interviewee didn't explicitly choose to include

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
- Known gap: no guidance yet for multi-domain technical calibration beyond
  a single free-text answer (e.g. someone expert in three different fields
  at three different levels)
