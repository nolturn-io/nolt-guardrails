# Agent Guardrails

Lightweight project governance for Claude Code, Cursor, and other AI coding agents.

This isn't a code template. It's a lightweight set of guardrails for building software with an AI coding agent so the agent has context to work from, checks before changing something, preserves why decisions were made, and doesn't quietly expand what you asked for.

Drop it into a new or existing project. No application code, framework, or dependencies.

## Why this exists

AI coding agents are fast and capable, but left to guess, they forget why the project exists between sessions, propose changes nobody asked for, lose the reasoning behind decisions that were already made, and let the architecture drift in directions no one actually decided on.

This kit is the minimum structure I've found useful for preventing that. Nothing more.

## What's in here

| File | Job |
| --- | --- |
| `AGENTS.md` | The shared operating rules for AI agents working in the repo |
| `CLAUDE.md` | Points Claude Code at `AGENTS.md` |
| `.cursor/rules/project.mdc` | Points Cursor at `AGENTS.md` |
| `docs/PROJECT_CONTEXT.md` | What you're building, for whom, and what it deliberately won't do |
| `docs/ARCHITECTURE.md` | How it's actually built today: current state, not the plan |
| `docs/RULES.md` | The guardrails: how to tell a needed change from scope creep before building it |
| `docs/adr/DECISIONS.md` | The running log of what was decided and why |
| `docs/adr/0000-template.md` | Template for a decision big enough to need more than one line |
| `.github/PULL_REQUEST_TEMPLATE.md` | Checklist that fires every time a PR opens |
| `.github/ISSUE_TEMPLATE/change_request.md` | Form for proposing a change that forces the "is this actually needed?" question up front |
| `PROMPTS.md` | Ready-to-paste prompts that make the agent actually use everything above |

Each type of project knowledge has one source of truth. Where files need the same information, they point to that source rather than maintaining separate copies.

## Quick start

About 10 minutes.

1. Copy everything in this kit into your project's root. It can be a brand-new repo or an existing one. It doesn't touch, require, or conflict with your application code.

2. Fill in the bracketed placeholders in `docs/PROJECT_CONTEXT.md` and `docs/ARCHITECTURE.md`. A few honest sentences per section is enough to start. You can add detail later as the project develops.

3. Open the project in Claude Code, Cursor, or a similar agent. `CLAUDE.md` and `.cursor/rules/project.mdc` point Claude Code and Cursor to the shared instructions in `AGENTS.md`, so the operating rules stay in one place.

4. Give the agent the **"Starting a session"** prompt from `PROMPTS.md` as your first message.

From there, the agent has project context, knows the guardrails, and knows where decisions and changes should be recorded.

## What you're actually getting

The files are Markdown. The value is the structure connecting them:

- what context an AI agent gets before it starts instead of guessing
- what it checks before changing anything instead of proposing blind
- how a decision gets preserved once instead of re-litigated every session
- how a requested change gets separated from an unrequested one before either gets built
- how "what's actually built" stays distinguishable from "what's planned," so the agent stops confusing the two
- how a human stays in the loop on anything that matters without creating a process for everything

Any of these files individually could be drafted by asking an AI assistant for one.

What that doesn't give you is the connective tissue: each file knowing what the others are for, one place for each kind of project truth, and prompts that actually get the guardrails applied instead of read once and forgotten.

## What this is not

This doesn't generate an application, choose your stack, or replace engineering judgment. It doesn't try to make an AI agent autonomous.

It gives the agent better context and boundaries, keeps important decisions from disappearing between sessions, and makes changes easier for a human to review.

## Works everywhere

No framework. No dependencies. No account. No service to configure.

The project-specific details live in `PROJECT_CONTEXT.md` and `ARCHITECTURE.md`, which you fill in. Nothing here assumes a particular language, framework, database, hosting provider, or application architecture.

Use it with a new project or drop it into something that already exists.
