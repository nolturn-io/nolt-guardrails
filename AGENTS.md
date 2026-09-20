# Agent Instructions

Read this before making any change in this repository — you are an AI coding agent, and this file is how the project talks to you.

## Read first, in order

| File | What it tells you |
|---|---|
| `docs/PROJECT_CONTEXT.md` | What this project is, for whom, and what it deliberately does not do |
| `docs/ARCHITECTURE.md` | How it is actually built, right now |
| `docs/adr/DECISIONS.md` | What has already been decided, so you don't re-litigate it |
| `docs/RULES.md` | The guardrails below, in full, with the reasoning behind them |

If any of these is still full of bracketed placeholders, say so before proceeding — don't invent a plausible-sounding project context to fill the gap.

## Before you change anything

- **Inspect before you propose.** Read the relevant part of `docs/ARCHITECTURE.md` and recent `docs/adr/DECISIONS.md` entries before suggesting a structural change. If the codebase and the docs disagree, the codebase is real and the docs are stale — say so, don't silently pick one.
- **Separate what was asked for from what would be nice to add.** If a request implies something durable — a new file, a new dependency, a new abstraction, a new workflow, a new table — run it through the Additive Change Gate in `docs/RULES.md` before building it.
- **Stay in the requested scope.** Finish what was asked. Note anything else you noticed along the way; don't act on it unasked.
- **Plan before anything substantial.** For a non-trivial change, state the plan, the files it touches, and any real tradeoff — then wait, unless told to proceed autonomously.

## Recording what happens

- **A decision that matters gets written down.** Use the two-tier test at the top of `docs/adr/DECISIONS.md` to decide whether it needs a one-line log entry or a full ADR.
- **Living docs stay honest.** If a change makes something in `docs/PROJECT_CONTEXT.md` or `docs/ARCHITECTURE.md` untrue, update it in the same change — not as a follow-up someone forgets.
- **Don't claim done before it's checked.** State what you actually verified — ran it, tested it, read the output — versus what you're assuming will work.

## Ready-made prompts

`PROMPTS.md` has copy-pasteable prompts for the recurring moments: starting a session, proposing a change, recording a decision, opening a PR, ending a long session. Use them — they exist so this file doesn't have to be re-read and re-interpreted from scratch every time.
