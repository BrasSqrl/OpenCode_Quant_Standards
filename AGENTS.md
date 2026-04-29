# Enterprise Quantitative Python Guidance

This repository contains shared instructions for `opencode` sessions that support enterprise Python work for quantitative model development, validation, and review. It also includes compatibility guidance for Codex agents.

## External File Loading

CRITICAL: When this file references another Markdown file using `@...`, load it on a need-to-know basis. Do not load the entire corpus by default.

Rules for referenced files:

- Treat loaded guidance as mandatory for the current task unless it conflicts with direct user instructions or repository-specific facts.
- Do not assume a referenced file was loaded unless you actually read it.
- Follow references recursively only when the current task requires that extra detail.

## Precedence

Use this order when instructions conflict:

1. Direct user instructions
2. Repository truth from code, configs, tests, and docs
3. `instructions/project/01-repository-context.md`
4. This shared standards pack

Flag important conflicts instead of silently blending them together.

## Always-On Expectations

- Work in a way that is reproducible, testable, and explicit about uncertainty.
- Distinguish facts, assumptions, risks, and recommendations.
- Do not invent data availability, metrics, backtest outcomes, or validation evidence.
- Prefer simple, inspectable Python over clever abstractions that hide methodology.
- Keep changes scoped and avoid modifying unrelated files.

## Default User Assumption

- Assume the user is an experienced quantitative modeler working on a concrete step in the model development lifecycle.
- Skip basic explanations unless the user asks for them.
- Use precise language about targets, horizons, baselines, leakage, validation design, and operational constraints.
- Focus on what changes methodology, evidence, controls, or production behavior.

## Startup Sequence In A New Repository

1. Read `instructions/project/01-repository-context.md`.
2. Inspect local sources of truth such as `README*`, `pyproject.toml`, `requirements*.txt`, `Makefile`, `src/`, `tests/`, `docs/`, and `notebooks/` when they exist.
3. Use explicit repo commands and conventions when they are available.
4. If essential repo facts are missing, state the gap and proceed with the least risky assumption.

## Codex Compatibility

- Codex should treat this `AGENTS.md` file as the primary project instruction file.
- Codex should read `CODEX.md` when available for runtime-specific usage guidance.
- Codex should treat `.opencode/skills/*/SKILL.md` and `.opencode/agents/*.md` as reusable prompt modules, not as OpenCode runtime features.
- OpenCode remains the primary target; do not remove or weaken OpenCode-specific files for Codex compatibility.

## Task Routing

Read these files only when the task requires them:

- For implementing or changing a model: `@instructions/playbooks/01-model-development.md`
- For reviewing, validating, or challenging a model: `@instructions/playbooks/02-model-assessment.md`
- For experiment design, benchmarking, or backtesting: `@instructions/playbooks/03-experimentation-and-backtesting.md`
- For debugging, optimization, or refactoring: `@instructions/playbooks/04-debugging-and-refactoring.md`
- For data pipelines, joins, or feature engineering: `@instructions/playbooks/05-data-pipelines-and-feature-engineering.md`
- For drafting a model methodology document aligned to SR 11-7 or successor guidance: `@instructions/playbooks/06-model-methodology-documentation.md`
- For methodology drafting from the Quant sister project output, DOCX generation, or image use from exported runs: `@instructions/project/08-quant-output-integration.md`
- For common failure modes and quantitative red flags: `@instructions/project/05-failure-modes-and-red-flags.md`
- For required review artifacts and release evidence: `@instructions/project/06-deliverables-matrix.md`
- For Codex-specific usage guidance: `@instructions/project/07-codex-compatibility.md`
- For a consistent final structure: `@instructions/templates/01-standard-response-format.md`
- For a formal model review memo: `@instructions/templates/02-model-review-template.md`
- For an experiment plan or result summary: `@instructions/templates/03-experiment-note-template.md`
- For a model methodology document table of contents: `@instructions/templates/04-sr11-7-model-methodology-template.md`

## Repository Context To Maintain

After copying this pack into a real repo, update `instructions/project/01-repository-context.md` so the agent has:

- package manager and environment workflow
- lint, test, type-check, and run commands
- expected project layout
- data sensitivity and access constraints
- repo-specific modeling conventions
- approval or review requirements
- methodology documentation source paths, Quant run paths, DOCX output location, and image-handling rules when applicable
