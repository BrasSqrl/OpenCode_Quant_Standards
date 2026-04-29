# Codex Compatibility Guide

This repository is primarily an OpenCode standards pack. Codex can still use it effectively because the core guidance is plain Markdown and the root `AGENTS.md` file is the primary project instruction entry point.

## Codex Startup

When using Codex in this repository or in a repo that has copied this pack:

1. Start with `AGENTS.md`.
2. Read `instructions/project/01-repository-context.md`.
3. Inspect local repo facts before drafting or changing files.
4. Load task-specific playbooks only when needed.
5. Treat `.opencode/skills/` and `.opencode/agents/` as prompt libraries, not runtime features.

## What Codex Should Ignore As Configuration

Codex should not treat these files as Codex-native configuration:

- `opencode.json`
- `.opencode/skills/*/SKILL.md` frontmatter
- `.opencode/agents/*.md` frontmatter

The text inside those files can still be useful. Use it as task guidance when it matches the user request.

## Common Codex Workflows

For implementation or model changes, read:

- `instructions/playbooks/01-model-development.md`
- `instructions/core/02-python-engineering.md`
- `instructions/core/03-quantitative-model-controls.md`

For model review or validation, read:

- `instructions/playbooks/02-model-assessment.md`
- `instructions/project/05-failure-modes-and-red-flags.md`
- `.opencode/skills/model-review/SKILL.md`

For SR 11-7-style methodology documentation, read:

- `instructions/playbooks/06-model-methodology-documentation.md`
- `instructions/templates/04-sr11-7-model-methodology-template.md`
- `instructions/project/08-quant-output-integration.md` when using Quant sister project output, run folders, figures, or DOCX generation rules
- `.opencode/skills/sr11-7-methodology-doc/SKILL.md`

For methodology documents, inspect `source_documents/` first. In the intended Quant workflow, `source_documents/` contains the exported Quant run bundle, usually as `source_documents/run_*` or `source_documents/quant_runs/run_*`.
Treat `source_documents/` as input evidence and write generated `.docx` files, sidecar evidence indexes, and derived images only to `output/`, `docs/model_methodology/`, or another approved output path.

## Codex Output Expectations

- State what files or evidence were used.
- State the selected Quant run ID when Quant artifacts are used.
- State the generated DOCX path and any evidence-index or image-inventory paths.
- Distinguish facts, assumptions, missing evidence, and recommendations.
- Do not invent metrics, approvals, validation findings, monitoring thresholds, model history, or data availability.
- When OpenCode guidance mentions skills or subagents, apply the corresponding Markdown guidance directly.
- Keep final responses concise and include validation performed or gaps left unresolved.
