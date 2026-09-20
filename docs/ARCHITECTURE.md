# Architecture

**Status:** initial — update this whenever the real structure changes, before considering that work done.
**Last reviewed:** [date]

This describes the system **as it actually exists** — current state, not target state. If you're planning a change that isn't built yet, that belongs in an issue or an ADR, not here. An agent that trusts this file should never be surprised by what it finds in the code; if it would be, this file is stale, and that's worth fixing on its own before anything else.

---

## Overview

One paragraph: what kind of system this is, the primary language/stack, and how it runs (locally, deployed, a script, a library — whatever applies). [Replace this line.]

## Structure

The major directories or modules and what each one owns. Describe the structure that exists, not an ideal one. If two things do similar jobs for unclear reasons, say so here rather than pretending it's tidy — an agent that reads a lie will confidently repeat it.

[Replace this list:]
- `[path]` — [what it owns]
- `[path]` — [what it owns]

## Key decisions that shape this structure

Point to the relevant entries in `docs/adr/DECISIONS.md` rather than re-explaining the reasoning here — one definition of "why," not two that can drift apart.

## External dependencies

What this talks to outside itself — other services, APIs, data stores — and why. An agent proposing a new integration should check this list first, both to avoid duplicating one and to know what's already a dependency. [Replace this line.]

## Testing approach

What's actually tested, and where. Doesn't need to be exhaustive — needs to be true. [Replace this line.]

## To be written

As the project grows, this file should grow with it: the data model, a route/API map, or anything a new agent would otherwise have to reconstruct by reading the whole codebase.
