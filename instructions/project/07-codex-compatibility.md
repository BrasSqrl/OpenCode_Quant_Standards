# Codex Compatibility

Use this file when the repository is being used by Codex rather than OpenCode.

## Primary Rule

OpenCode remains the primary target for this standards pack. Codex support should preserve the same instructions while treating OpenCode-specific files as prompt modules instead of runtime configuration.

## Codex Loading Model

- `AGENTS.md` is the main project instruction file for Codex.
- `CODEX.md` is a human-readable compatibility guide and should be read when Codex usage is relevant.
- `opencode.json` is OpenCode configuration and should not be interpreted as Codex configuration.
- `.opencode/skills/*/SKILL.md` files are reusable workflow prompts for Codex.
- `.opencode/agents/*.md` files are reusable role prompts for Codex.

## Codex Task Routing

For normal quantitative coding work:

- read `instructions/core/01-operating-principles.md`
- read `instructions/core/02-python-engineering.md`
- read `instructions/core/03-quantitative-model-controls.md`
- read the relevant playbook under `instructions/playbooks/`

For SR 11-7-style methodology documentation:

- read `instructions/playbooks/06-model-methodology-documentation.md`
- read `instructions/templates/04-sr11-7-model-methodology-template.md`
- inspect `source_documents/` first
- use `.opencode/skills/sr11-7-methodology-doc/SKILL.md` as additional drafting rules
- use `.opencode/agents/model-methodology-writer.md` as role guidance

## Codex Limitations Relative To OpenCode

When using Codex outside OpenCode:

- OpenCode skill permissions do not apply.
- OpenCode subagent delegation rules do not apply.
- `@agent` invocation examples are conceptual unless the Codex environment supports comparable agent spawning.
- Any `.opencode` frontmatter should be treated as descriptive metadata unless the runtime explicitly supports it.

## Required Behavior

- Follow repository facts over generic pack guidance.
- Do not fabricate evidence, metrics, approvals, or validation findings.
- Report when an OpenCode-only feature is being approximated manually.
- Keep OpenCode files intact unless the user explicitly asks to remove OpenCode support.
