# OpenCode Skills And Subagents Guide

This file is for human operators and maintainers. It explains how to use the local `.opencode/skills/` and `.opencode/agents/` folders included with this standards pack.

## What Belongs Where

- Put always-on behavioral rules in `AGENTS.md` and the files loaded by `opencode.json`.
- Put reusable, on-demand workflows in `.opencode/skills/`.
- Put role-shaped assistants with distinct prompts or tool access in `.opencode/agents/`.

## Use The Included Skills

The local skills are:

- `model-review`
- `leakage-audit`
- `experiment-note`
- `promotion-readiness`
- `feature-contract`
- `deliverables-check`
- `sr11-7-methodology-doc`

Use skills when you want the same session or agent to load a focused workflow without switching to another agent.

Good fit:

- formal model review structure
- leakage checks
- experiment planning and result writeups
- model methodology documentation aligned to SR 11-7-style or successor internal MRM templates

Bad fit:

- repo facts that should always be in context
- broad project rules
- tasks that need different tool permissions rather than different instructions

## Use Built-In Subagents First

OpenCode already includes these useful built-ins:

- `@explore`: fast, read-only codebase exploration
- `@general`: broader multi-step work with full tool access

Typical patterns:

- `@explore map the training pipeline and identify where labels are built`
- `@general add a regression test for this leakage bug while I review the current pipeline`

## Use The Included Custom Subagent

This pack adds:

- `@quant-reviewer`
- `@quant-data-auditor`
- `@quant-implementer`
- `@model-methodology-writer`

It also adds two custom primary agents:

- `quant-plan`
- `quant-build`

Use it when you want a read-only, control-focused assessment of methodology, implementation quality, leakage risk, validation design, or production readiness.

Example prompts:

- `@quant-reviewer review the walk-forward validation design and call out material weaknesses`
- `@quant-reviewer assess this training pipeline for point-in-time violations and missing controls`

Use `@quant-data-auditor` when the task is centered on data joins, schema assumptions, point-in-time logic, feature availability, and dataset assembly risk.

Example prompts:

- `@quant-data-auditor map the feature join logic and identify point-in-time risks`
- `@quant-data-auditor review this training table build for duplicate keys, null handling, and schema drift`

Use `@quant-implementer` for bounded implementation work that should stay narrowly scoped to one quantitative engineering task.

Example prompts:

- `@quant-implementer add a focused regression test for this label leakage bug`
- `@quant-implementer update the feature pipeline to validate duplicate entity-timestamp rows`

Use `@model-methodology-writer` when the task is to draft or revise a model methodology document from repo artifacts, supplied evidence, and the approved table of contents.

Example prompts:

- `@model-methodology-writer draft sections 1 through 3 of the model methodology document from these artifacts`
- `@model-methodology-writer build an evidence-gap table against the SR 11-7-style template`

## How Subagent Spawning Works

- You can manually invoke a subagent by `@` mentioning it in your prompt.
- Primary agents can also invoke subagents automatically through OpenCode's task system when permissions allow.
- Built-in primary agents are `build` and `plan`.
- Built-in subagents are `general` and `explore`.
- Custom primary agents in this pack are `quant-build` and `quant-plan`.
- Custom subagents in this pack are `quant-reviewer`, `quant-data-auditor`, `quant-implementer`, and `model-methodology-writer`.

## Recommended Multi-Agent Patterns

- Main agent implements while `@quant-reviewer` reviews methodology and `@explore` maps impacted code paths.
- Main agent investigates a bug while `@general` prepares a focused test or isolated fix.
- Main agent writes code while `@quant-reviewer` checks whether the change alters model controls, evidence, or production behavior.
- `quant-build` drives execution while `@quant-reviewer` and `@quant-data-auditor` review methodology and data controls in parallel.
- `quant-plan` develops a read-only implementation plan while `@explore` maps code structure and `@quant-reviewer` identifies validation risks.
- `@model-methodology-writer` drafts documentation while `@quant-reviewer` reviews methodology claims and `@quant-data-auditor` checks data-lineage claims.

## When To Add More Custom Subagents

Add a new subagent only when all of these are true:

- the workflow repeats across teams
- the role has a stable prompt shape
- the role benefits from distinct tool permissions or a different model
- the role is not already covered by `@general`, `@explore`, or a skill

If the difference is only a checklist or workflow, prefer a skill. If the difference is a distinct role with different permissions, prefer a subagent.

## Included Permission Patterns

This pack configures:

- global skill permissions that allow the included local skills and set unknown skills to `ask`
- built-in `build` task permissions that allow the common custom and built-in subagents
- built-in `plan` task permissions that allow read-oriented subagents
- custom `quant-build` and `quant-plan` task permissions aligned to their intended roles

This gives you a controlled default for automatic delegation without blocking direct manual `@agent` usage.
