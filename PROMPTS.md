# Prompts

Copy-paste these at the moments they're named for. They exist so `AGENTS.md` and `docs/RULES.md` get applied in practice, not just read once and forgotten.

---

## Before you build anything

> Before implementing this, apply the Additive Change Gate in `docs/RULES.md`. Separate the desired outcome from the specific implementation I described. Check `docs/PROJECT_CONTEXT.md` and `docs/ARCHITECTURE.md` for whether something already covers this. Tell me the smallest version that would work before writing code.

## Starting a session

> Read `AGENTS.md`, `docs/PROJECT_CONTEXT.md`, `docs/ARCHITECTURE.md`, and the most recent entries in `docs/adr/DECISIONS.md` before proposing anything. Tell me if any of them look stale compared to the actual code.

## Recording a decision

> We just decided [X]. Apply the two-tier test at the top of `docs/adr/DECISIONS.md` — were there real alternatives someone will ask about later? If yes, write a full ADR using `docs/adr/0000-template.md`. If not, add a one-line entry to `DECISIONS.md`.

## Before opening a PR

> Review this diff against `.github/PULL_REQUEST_TEMPLATE.md`. Flag anything in the diff that wasn't part of the original request — a new dependency, a new abstraction, an unrequested refactor — even if it looks like an improvement.

## Ending a long session

> Before we stop: does anything in `docs/PROJECT_CONTEXT.md` or `docs/ARCHITECTURE.md` need updating based on what changed today? Add anything decision-worthy to `docs/adr/DECISIONS.md`. Do this before compacting or handing off, not after.
