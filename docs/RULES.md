# Project Rules — Guardrails for AI-Assisted Development

This is the standing set of guardrails for how an AI agent — and you — should reason about adding anything to this project. `AGENTS.md`, `CLAUDE.md`, and `.cursor/rules/project.mdc` all point here rather than restating it: one definition, read from one place, applied every time instead of remembered inconsistently.

## Core principle and Reductive Change

Software should absorb complexity so people do not have to. Development tooling should absorb governance complexity so developers do not have to.

**Cheap implementation is not evidence of worthwhile complexity.** AI-assisted development makes software inexpensive to create, not inexpensive to own. Do not confuse easy to build with worth having. Before accepting meaningful complexity, consider its maintenance, conceptual overhead, data ownership, user and security impact, integrations, testing, migrations, future coupling, and operational burden.

Keep solutions boring, readable, and as small as the outcome safely permits. Prefer removing, consolidating, automating, deriving, reusing, simplifying, and retiring before adding. Before adding anything, ask: **What can disappear because of this enhancement?**

## Additive Change Gate

**This is a pre-implementation execution gate.** Before deep research, planning, or implementation, apply it to any meaningful request that introduces durable architecture: persistent fields or configuration, tables, statuses or state machines, approvals, workflows, scheduled jobs, notification systems, dashboards, API routes, sources of truth, permission families, agents, integrations, duplicated business logic, or permanent abstractions for temporary behavior.

First separate the **DESIRED OUTCOME** from the **REQUESTED IMPLEMENTATION**. Implementation details in a request are proposals unless the requester clearly identifies them as non-negotiable constraints. Determine whether the additions are necessary to achieve the outcome and whether existing rules, records, state, alerts, workflows, ownership, or sources of truth already provide or can derive the needed behavior.

**Decision before implementation.** The first objective is to decide whether anything is worth implementing; do not assume implementation will follow. Until the gate resolves, do not announce or promise implementation, select technical mechanisms, design schema, migrations, permissions/access control, APIs, dashboards, or other implementation patterns, edit files, or perform implementation-scale research. "As requested" is not architectural justification.

Do not load implementation-specific guidance, deployment steps, infrastructure patterns, or framework references merely to prepare for building. During premise validation, use one only when it is necessary to determine whether an existing capability already satisfies the outcome.

Use **Minimum Necessary Discovery**: inspect only enough of the project to determine whether the addition is necessary. Check whether state already exists or is derivable, another part of the system owns the behavior, an authoritative mechanism already exists, or the proposal duplicates state, automates unnecessary manual work, or makes a temporary need permanent. If the premise may fail, stop discovery and surface the alternative; do not continue into implementation pattern-matching. Research and reasoning cost time and attention, so depth scales only after the premise survives.

If the change is unjustified, **stop and wait for a decision** rather than proceeding. Concisely state the outcome, evidence, concern, and reductive alternative, then return control to whoever asked. Until they explicitly choose an option, do not edit or create files, run implementation commands, generate migrations, or otherwise implement either design. The original request, an existing plan, autonomous mode, or the ability to continue is not authorization to cross this boundary. After a decision is made, proceed with that choice unless a hard constraint prevents it. Challenge once; do not re-argue without materially new evidence.

## Process first, tools second

Do not automate waste simply because automation is cheap.

Before agentifying or automating a task, determine whether the task should exist, whether the process is sound, and whether automation eliminates a gap or merely hides it. Look for unnecessary manual work standing in for a missing system: copying or reconciling data between places, manually moving statuses, remembering future actions, translating between incompatible workflows, and other human effort that compensates for missing integration or bad process design. Eliminate the underlying need where practical; do not merely hide the work inside an agent.

Avoid unnecessary abstractions and dependencies. Prefer server-side (or otherwise trusted-side) handling for anything sensitive, and never expose a privileged credential or admin-level key to a client. Use environment variables for secrets. Explain material data-model changes, enforce access control at a layer the client cannot bypass, and handle the relevant loading, empty, and error states. Make the primary real-world use case usable by default, not an afterthought.

## AI-first application

Agents apply this standard silently while planning and implementing meaningful enhancements. Internally determine:

1. the actual outcome, and whether the requested implementation is necessary
2. whether an existing capability already solves or can derive it
3. what unnecessary manual work should disappear rather than be automated
4. what can be removed, consolidated, reused, simplified, or retired
5. the behavior-change, source-of-truth, maintenance, and mode implications
6. the lowest-complexity safe solution

Use `REDUCES`, `NEUTRAL`, `INCREASES_JUSTIFIED`, or `INCREASES_UNJUSTIFIED` as internal labels when useful. For `REDUCES` and `NEUTRAL`, proceed normally. For `INCREASES_JUSTIFIED`, proceed and briefly surface the tradeoff when useful. For `INCREASES_UNJUSTIFIED`, the Additive Change Gate above is a hard execution boundary: explain once, offer the reductive alternative, stop, and wait for a decision.

## Development modes

Infer the mode from the request. Default to **BUILD** when no mode is specified. Modes change the scrutiny applied to permanence; they do not create a workflow or require anyone to declare a mode out loud.

### EXPLORE

Use for an explicitly identified experiment, prototype, proof of concept, spike, or throwaway exploration. Optimize for learning. Temporary duplication or shortcuts are acceptable when justified, but isolate them, keep them easy to delete, and avoid contaminating core domain models. Keep premise validation brief and don't demand production architecture for disposable learning; the full Additive Change Gate still applies before an experiment turns into permanent production architecture.

**Exploration is allowed to be messy. Permanence is not accidental.** Before experimental work becomes part of BUILD or HARDEN work, reconsider it against the full standards. No formal promotion ceremony is required.

### BUILD

This is the default. Challenge unnecessary additive change, favor reductive solutions, preserve clear sources of truth, apply normal security and testing, and consider ongoing ownership. Cheap implementation is not a reason to retain a new concept. When a request introduces multiple durable concepts at once, assume it requires premise validation before any implementation commitment. The more durable concepts proposed together, the stronger the presumption that the design should be challenged before implementation-scale research or work.

### HARDEN

Use when work is explicitly production hardening, release preparation, customer deployment, security hardening, scaling, or commercialization. Apply the strongest scrutiny to security, tenant isolation, authorization, data integrity, observability, reliability, failure modes, migrations, recovery, testing, operationally necessary documentation, maintenance, and backward compatibility. Deeper investigation is justified when these risks are material. Do not give a low-risk idea the research budget of an authorization, migration, destructive-operation, or customer-production change, and do not turn scrutiny into unnecessary ceremony.

## Relationship to local project instructions

These rules govern how to reason about engineering. `docs/PROJECT_CONTEXT.md` and `docs/ARCHITECTURE.md` govern what is actually true about this project: its architecture, domain, schema, APIs, deployment, and real constraints. Apply this philosophy within those facts, not instead of them. Do not overwrite a legitimate project-specific requirement; surface a genuine conflict when it materially affects the work.

## Governance must not add overhead

Every addition to this file's guardrails must justify its ongoing cost. Before adding a process, document, checklist, required field, approval, CI gate, report, or manual review, prefer automation, existing project metadata, existing review practices, or deterministic tooling over a new human step.

Reserve human attention for exceptions, ambiguity, meaningful tradeoffs, risk, and decisions the system cannot safely make on its own. Do not require a special command, form, checklist, artifact, score, meeting, or manual proof that this standard was applied.

## Planning and completion

Scale planning and review to risk. For a meaningful change, briefly identify the outcome, assumptions, affected areas, data/security impact, and implementation approach. Trivial changes need no ceremonial plan. Ask for a decision only when scope or a consequential tradeoff genuinely requires one.

The Additive Change Gate is the primary safeguard against unnecessary complexity and occurs before implementation. Before completion, inspect the actual diff only for unexpected user actions, fields, approvals, statuses, tables, dependencies, integrations, synchronization, training, permissions, behavior changes, sources of truth, or hidden unnecessary manual work. Fix anything unexpected before declaring completion. Report changed files, verification, and material risks or rollback information — without creating a separate governance artifact to prove it happened.
