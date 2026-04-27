# Enterprise Quantitative OpenCode Standards Pack

This repository is a portable control pack for `opencode`-based development workflows. Its purpose is to make large-language-model behavior more consistent, more auditable, and less repo-specific by default when teams are building, reviewing, validating, or maintaining Python-based quantitative models.

The pack is designed to be copied into the root of another repository and then lightly customized. It combines:

- always-on repository rules
- structured quantitative engineering guidance
- on-demand skills for repeated workflows
- custom agents and subagents for role-shaped work
- permission patterns for safer automatic delegation

The result is not a model itself. It is a control layer for how OpenCode should behave inside a destination repository.

## Who This Is For

This README is written for both:

- end users who want to use the pack inside a target repository
- maintainers who want to extend, harden, or standardize the pack across teams

The pack assumes the primary operator is an experienced quantitative modeler, model reviewer, or quantitative engineer. The default writing style is concise and technical. It avoids beginner-level explanations unless explicitly requested.

## What This Project Is Trying To Accomplish

The pack is trying to solve a practical problem: most repositories do not contain enough structured guidance for a coding agent to behave consistently across teams. In quantitative work, that inconsistency creates real risk because subtle mistakes in targets, timestamps, joins, validation design, or release evidence can lead to invalid conclusions or unsafe deployment decisions.

This pack provides a reusable baseline so that when it is copied into another repository:

- OpenCode has a clear root rule file
- the agent starts from a small, stable instruction set
- deeper guidance is loaded only when needed
- repeatable workflows are available through skills
- specialized review and implementation roles are available through custom agents and subagents
- permission patterns reduce uncontrolled automatic delegation

## Design Philosophy

The pack is built around a few deliberate choices:

- Keep the always-on context small.
- Put durable standards in Markdown, not only in human memory.
- Separate always-on rules from on-demand workflows.
- Separate role-specific review work from implementation work.
- Bias toward explicit evidence, reproducibility, and point-in-time discipline.
- Make it easy to transplant the pack into another repo with minimal editing.

## How OpenCode Uses The Pack

There are several different OpenCode control surfaces in this project. They do different jobs.

### `AGENTS.md`

[AGENTS.md](AGENTS.md) is the root rule file. OpenCode loads it automatically when you start from this repository root or from a subdirectory under it.

What it does:

- defines the overall behavioral contract
- sets precedence rules
- defines the default user assumption
- tells the agent how to inspect a new repository
- routes the agent to deeper files only when needed

What it should contain:

- short, stable, high-value rules
- task-routing instructions
- repo-independent guardrails

What it should not contain:

- long duplicated playbooks
- detailed repository facts
- large amounts of operational prose that belong in supporting docs

### `opencode.json`

[opencode.json](opencode.json) is the structured OpenCode configuration file.

What it does in this pack:

- loads the small always-on instruction set
- defines skill permission behavior
- defines task permission patterns for automatic subagent delegation
- customizes built-in and custom agent delegation behavior

What it does not do:

- replace `AGENTS.md`
- hold the full qualitative guidance corpus
- substitute for real repository facts

### `instructions/`

The [instructions](instructions) directory holds the Markdown corpus that `AGENTS.md` and `opencode.json` rely on.

It is split intentionally:

- `instructions/core/`: stable cross-repository principles
- `instructions/project/`: repo-transfer guidance, repo context, operator docs, and supporting project-specific controls
- `instructions/playbooks/`: deeper task-specific workflows
- `instructions/templates/`: output structures and memo templates

### `.opencode/skills/`

The [`.opencode/skills`](.opencode/skills) directory contains project-local OpenCode skills.

Skills are:

- on-demand
- reusable
- workflow-shaped
- not always in context

They are the right tool when you want a repeatable procedure or checklist without creating a whole new agent role.

### `.opencode/agents/`

The [`.opencode/agents`](.opencode/agents) directory contains custom agents and subagents.

Agents are the right tool when you want:

- a distinct role
- a distinct prompt
- different tool access
- a different delegation pattern
- a separate primary agent mode

This pack includes both custom primary agents and custom subagents.

## What Is Already Premade

The following components are already built and can usually be copied unchanged into another repo.

### Root Control Files

- [AGENTS.md](AGENTS.md): root router and core behavioral contract
- [opencode.json](opencode.json): OpenCode configuration, instruction loading, and permission patterns

### Core Instruction Files

- [instructions/core/01-operating-principles.md](instructions/core/01-operating-principles.md): global operating expectations and audience assumptions
- [instructions/core/02-python-engineering.md](instructions/core/02-python-engineering.md): Python engineering defaults
- [instructions/core/03-quantitative-model-controls.md](instructions/core/03-quantitative-model-controls.md): quantitative modeling control expectations

### Playbooks

- [instructions/playbooks/01-model-development.md](instructions/playbooks/01-model-development.md): model implementation workflow
- [instructions/playbooks/02-model-assessment.md](instructions/playbooks/02-model-assessment.md): review and validation workflow
- [instructions/playbooks/03-experimentation-and-backtesting.md](instructions/playbooks/03-experimentation-and-backtesting.md): experiment and backtest discipline
- [instructions/playbooks/04-debugging-and-refactoring.md](instructions/playbooks/04-debugging-and-refactoring.md): debugging and refactor workflow
- [instructions/playbooks/05-data-pipelines-and-feature-engineering.md](instructions/playbooks/05-data-pipelines-and-feature-engineering.md): data and feature pipeline workflow
- [instructions/playbooks/06-model-methodology-documentation.md](instructions/playbooks/06-model-methodology-documentation.md): SR 11-7-style methodology-document drafting workflow

### Templates

- [instructions/templates/01-standard-response-format.md](instructions/templates/01-standard-response-format.md): consistent response shape
- [instructions/templates/02-model-review-template.md](instructions/templates/02-model-review-template.md): formal review memo structure
- [instructions/templates/03-experiment-note-template.md](instructions/templates/03-experiment-note-template.md): experiment note structure
- [instructions/templates/04-sr11-7-model-methodology-template.md](instructions/templates/04-sr11-7-model-methodology-template.md): model methodology document table of contents and evidence-index scaffold

### Project Guidance And Operator Files

- [instructions/project/01-repository-context.md](instructions/project/01-repository-context.md): the repo-context intake form you must customize after copying the pack
- [instructions/project/02-repository-context-example.md](instructions/project/02-repository-context-example.md): a worked example showing the expected level of specificity
- [instructions/project/03-opencode-skills-and-subagents.md](instructions/project/03-opencode-skills-and-subagents.md): operator guide for local skills and agents
- [instructions/project/04-transfer-and-customization-checklist.md](instructions/project/04-transfer-and-customization-checklist.md): checklist for moving the pack into a real repo
- [instructions/project/05-failure-modes-and-red-flags.md](instructions/project/05-failure-modes-and-red-flags.md): common quantitative red flags
- [instructions/project/06-deliverables-matrix.md](instructions/project/06-deliverables-matrix.md): required artifacts by task type

### Included Skills

These are project-local skills and are intended to be available on demand.

- [model-review](.opencode/skills/model-review/SKILL.md): structured quantitative model review workflow
- [leakage-audit](.opencode/skills/leakage-audit/SKILL.md): point-in-time and leakage audit workflow
- [experiment-note](.opencode/skills/experiment-note/SKILL.md): experiment planning and result writeup workflow
- [promotion-readiness](.opencode/skills/promotion-readiness/SKILL.md): merge, release, and promotion readiness workflow
- [feature-contract](.opencode/skills/feature-contract/SKILL.md): feature and dataset contract workflow
- [deliverables-check](.opencode/skills/deliverables-check/SKILL.md): required-artifact classification workflow
- [sr11-7-methodology-doc](.opencode/skills/sr11-7-methodology-doc/SKILL.md): SR 11-7-style methodology-document drafting workflow

### Included Custom Agents And Subagents

These are project-local agents defined in Markdown.

Primary agents:

- [quant-build](.opencode/agents/quant-build.md): quantitative implementation primary agent
- [quant-plan](.opencode/agents/quant-plan.md): read-oriented quantitative planning primary agent

Subagents:

- [quant-reviewer](.opencode/agents/quant-reviewer.md): methodology and controls reviewer
- [quant-data-auditor](.opencode/agents/quant-data-auditor.md): data and point-in-time auditor
- [quant-implementer](.opencode/agents/quant-implementer.md): bounded implementation worker
- [model-methodology-writer](.opencode/agents/model-methodology-writer.md): documentation writer for model methodology documents

## What Must Be Updated In A New Repository

The single most important file to update after copying this pack is:

- [instructions/project/01-repository-context.md](instructions/project/01-repository-context.md)

That file is intentionally an intake form. It should be filled with real facts about the destination repository.

At minimum, you should update:

- business purpose
- model domain and unit of prediction
- target variable and prediction horizon
- canonical environment, lint, test, and run commands
- source, test, config, data, and artifact paths
- target construction and timestamp rules
- baseline-model expectations
- validation evidence required before merge
- data sensitivity and storage constraints
- review, sign-off, and release requirements
- methodology documentation standard, owner, source artifacts, output location, evidence-index format, and approval path

If you fail to update that file, the pack still works as a generic control layer, but it loses most of the repo-specific value.

## What Usually Does Not Need To Be Updated

These components are intended to be reused largely unchanged across repos:

- the core instruction files
- the playbooks
- the templates
- the generic quant failure modes
- the transfer checklist
- the deliverables matrix
- the skills, unless your organization uses different approval language or artifact requirements
- the custom agent prompts, unless your team needs materially different role boundaries

## How To Copy This Pack Into Another Repository

1. Copy the entire contents of this project into the root of the destination repository.
2. Confirm that `AGENTS.md` and `opencode.json` sit at that repo root.
3. Edit [instructions/project/01-repository-context.md](instructions/project/01-repository-context.md) and replace the bracketed prompts with real repo facts.
4. Validate the exact commands you entered in that file.
5. Confirm the listed paths actually exist in the destination repo.
6. Start OpenCode from the destination repo root.
7. Check that the root rules load, the local skills appear, and the custom agents appear in `@` autocomplete.
8. Commit the pack and the repo-context customizations so every user gets the same baseline.

Use [instructions/project/04-transfer-and-customization-checklist.md](instructions/project/04-transfer-and-customization-checklist.md) as the operational transfer checklist.

## How The Premade Pieces Work Together

The normal flow is:

1. OpenCode starts and loads [AGENTS.md](AGENTS.md).
2. [opencode.json](opencode.json) loads the always-on instruction set.
3. The agent reads the repo-context intake form and then inspects local repository truth.
4. The agent loads deeper playbooks only if the task requires them.
5. Skills are loaded only when needed for workflow-specific structure.
6. Subagents are invoked manually by `@mention` or automatically through OpenCode's task system when permissions allow.

This separation is intentional:

- root rules stay short
- always-on context stays controlled
- specialized guidance stays available without bloating every session

## How To Use The Included Skills

Skills are best when you want a reusable workflow inside the current session without changing to a different primary agent.

Use cases:

- load `model-review` when you need a formal model review structure
- load `leakage-audit` when you suspect timing or availability issues
- load `experiment-note` when you need a disciplined experiment plan or result summary
- load `promotion-readiness` when a change may affect merge, release, or production readiness
- load `feature-contract` when you need explicit schema or feature semantics
- load `deliverables-check` when you need to know what artifacts should exist
- load `sr11-7-methodology-doc` when drafting or gap-checking a model methodology document

Use skills for:

- repeated workflow structure
- checklists
- memo formats
- task framing

Do not use skills for:

- root behavioral rules
- permanent repo facts
- cases where you need different tool permissions or a different role

## How To Use The Included Agents And Subagents

### Built-In OpenCode Agents

OpenCode already provides built-in primary agents and subagents such as:

- `build`
- `plan`
- `@general`
- `@explore`

These remain useful and this pack does not replace them.

### Custom Primary Agents In This Pack

Use `quant-build` when you want a primary agent that is already framed around quantitative implementation, validation, and controlled delegation.

Use `quant-plan` when you want a primary agent that remains read-only and is optimized for:

- planning
- methodology review preparation
- validation-gap analysis
- decomposition before implementation

### Custom Subagents In This Pack

Use `@quant-reviewer` for:

- model methodology review
- validation design critique
- production-readiness challenge
- evidence-oriented approval decisions

Use `@quant-data-auditor` for:

- training-table reviews
- feature-join audits
- schema and key assumptions
- point-in-time and data-contract issues

Use `@quant-implementer` for:

- narrow code changes
- targeted tests
- focused regression fixes
- bounded secondary implementation work

Use `@model-methodology-writer` for:

- drafting SR 11-7-style methodology documents
- stitching together evidence from repository artifacts and supplied documents
- maintaining section-level evidence gaps and open items
- separating developer assertions from validation findings and approvals

## Model Methodology Documentation

This pack includes a dedicated workflow for model methodology documents because that work usually requires substantial synthesis across code, notebooks, data lineage, validation evidence, approvals, monitoring plans, and governance materials.

The workflow is centered on:

- [instructions/playbooks/06-model-methodology-documentation.md](instructions/playbooks/06-model-methodology-documentation.md)
- [instructions/templates/04-sr11-7-model-methodology-template.md](instructions/templates/04-sr11-7-model-methodology-template.md)
- [sr11-7-methodology-doc](.opencode/skills/sr11-7-methodology-doc/SKILL.md)
- [model-methodology-writer](.opencode/agents/model-methodology-writer.md)

The template preserves the user-provided table of contents across:

- Part One: Technical Documentation
- Part Two: Model Governance and Procedures
- Part Three: Ongoing Performance Monitoring Plan
- Appendix 1: Template Version Change History

The LLM should treat this as evidence synthesis, not freeform writing. Material claims should be traceable to source artifacts, missing support should be marked with `[EVIDENCE NEEDED: ...]`, and optional sections should be removed or marked not applicable only when the basis is documented.

Regulatory currency matters. SR 11-7 was issued on April 4, 2011. Federal Reserve SR 26-2, dated April 17, 2026, states that revised interagency guidance supersedes and replaces SR 11-7 and SR 21-8. If an institution still requires an SR 11-7-style table of contents, use the included workflow, but confirm the governing internal MRM policy and whether successor guidance must also be reflected.

## How To Spawn Subagents And Split Work

In OpenCode, subagents can be used in two ways:

- manually, by `@` mentioning a subagent
- automatically, when a primary agent invokes a subagent through the task system and permissions allow it

Examples of manual use:

- `@explore map where the target is constructed`
- `@quant-reviewer review the validation split logic`
- `@quant-data-auditor inspect the point-in-time join assumptions`
- `@quant-implementer add a regression test for duplicate entity-timestamp rows`
- `@model-methodology-writer draft the model context and data analysis sections from the supplied artifacts`

Recommended delegation patterns in this pack:

- main implementation agent writes code while `@quant-reviewer` checks methodology and controls
- main implementation agent writes code while `@quant-data-auditor` audits feature joins and timestamps
- `quant-plan` develops a plan while `@explore` maps code paths and `@quant-reviewer` identifies methodological risk
- `quant-build` executes a change while `@quant-implementer` handles one bounded secondary task
- `@model-methodology-writer` drafts documentation while `@quant-reviewer` challenges methodology claims and `@quant-data-auditor` checks data-lineage claims

When to use a subagent:

- when the task can be cleanly separated
- when parallel work helps
- when a specialized role should assess the work independently
- when you want a different prompt or tool access than the primary agent has

When not to use a subagent:

- when the task is tiny and local
- when the split would create more coordination cost than value
- when a skill would solve the problem more simply

## Included Permission Patterns

This pack includes explicit permission behavior in [opencode.json](opencode.json).

### Skill Permissions

Unknown skills are set to `ask`.

The included local skills are set to `allow`:

- `model-review`
- `leakage-audit`
- `experiment-note`
- `promotion-readiness`
- `feature-contract`
- `deliverables-check`
- `sr11-7-methodology-doc`

This means the pack is permissive for known local workflows but cautious about unfamiliar skills.

### Task Permissions For Delegation

The pack configures automatic task delegation so that:

- built-in `build` can auto-delegate to `general`, `explore`, `quant-reviewer`, `quant-data-auditor`, `quant-implementer`, and `model-methodology-writer`
- built-in `plan` can auto-delegate to `explore`, `quant-reviewer`, and `quant-data-auditor`
- custom `quant-build` can auto-delegate to `general`, `explore`, `quant-reviewer`, `quant-data-auditor`, `quant-implementer`, and `model-methodology-writer`
- custom `quant-plan` can auto-delegate to `explore`, `quant-reviewer`, and `quant-data-auditor`

Unknown automatic task delegation targets are set to `ask`.

Users can still manually invoke subagents directly with `@mention` even when a task permission would otherwise block automatic invocation.

## Included Supporting Project Files

The files below are not the root control plane, but they materially improve operational clarity.

Use [instructions/project/05-failure-modes-and-red-flags.md](instructions/project/05-failure-modes-and-red-flags.md) when:

- suspicious performance appears too good to trust
- a reviewer needs common quantitative failure patterns in one place
- a debugging task may involve leakage, survivorship bias, or weak baselines

Use [instructions/project/06-deliverables-matrix.md](instructions/project/06-deliverables-matrix.md) when:

- a task affects methodology
- a change touches production
- a reviewer wants to know what artifacts should exist before approval

Use [instructions/project/03-opencode-skills-and-subagents.md](instructions/project/03-opencode-skills-and-subagents.md) when:

- a human operator is unsure whether to use a skill, a subagent, or a built-in agent
- a maintainer wants the local delegation model explained in one place

## Model-Agnostic By Design

This pack is written to stay generic across OpenCode-compatible models. It does not hardcode a specific provider or a specific model family into the agent files or `opencode.json`.

That said, model differences still matter.

If you use a model that is weaker at long-context reasoning, instruction following, or tool discipline, you may need to:

- keep `AGENTS.md` even shorter
- make `instructions/project/01-repository-context.md` more explicit
- rely more heavily on skills for structured workflows
- prefer `quant-plan` before implementation
- keep subagent tasks smaller and more concrete
- tighten permission patterns further

If you use a model that is strong but more agentic or more aggressive with tools, you may need to:

- keep the explicit permission patterns
- retain read-only reviewer and auditor roles
- require clearer promotion artifacts before trusting conclusions
- avoid broad automatic delegation to new agents without review

If you want model-specific tuning later, the usual places are:

- agent `model` overrides
- agent `temperature`
- agent `steps`
- default-agent selection
- permission tightening or loosening

This pack intentionally leaves those mostly generic so it can be transplanted without assuming a provider.

## What Maintainers Should Extend Carefully

Extend this pack carefully in these areas:

- `instructions/core/`: only add stable cross-team guidance
- `.opencode/skills/`: add a skill only when the workflow repeats across repos or teams
- `.opencode/agents/`: add an agent only when you need a true role distinction
- `opencode.json`: change permission patterns deliberately because they affect automatic behavior

Avoid:

- stuffing too much text into `AGENTS.md`
- moving repo facts into generic files
- creating many overlapping skills
- creating many near-duplicate subagents
- allowing unrestricted automatic delegation without a reason

## Minimal Setup For A New Repo

If you want the minimum viable transfer:

1. Copy the whole pack.
2. Fill in [instructions/project/01-repository-context.md](instructions/project/01-repository-context.md).
3. Keep the rest unchanged.
4. Validate one planning task and one implementation task.

That is enough for a strong starting point.

## Full File Inventory

```text
AGENTS.md
opencode.json
README.md
.opencode/
  agents/
    model-methodology-writer.md
    quant-build.md
    quant-data-auditor.md
    quant-implementer.md
    quant-plan.md
    quant-reviewer.md
  skills/
    deliverables-check/SKILL.md
    experiment-note/SKILL.md
    feature-contract/SKILL.md
    leakage-audit/SKILL.md
    model-review/SKILL.md
    promotion-readiness/SKILL.md
    sr11-7-methodology-doc/SKILL.md
instructions/
  core/
    01-operating-principles.md
    02-python-engineering.md
    03-quantitative-model-controls.md
  playbooks/
    01-model-development.md
    02-model-assessment.md
    03-experimentation-and-backtesting.md
    04-debugging-and-refactoring.md
    05-data-pipelines-and-feature-engineering.md
    06-model-methodology-documentation.md
  project/
    01-repository-context.md
    02-repository-context-example.md
    03-opencode-skills-and-subagents.md
    04-transfer-and-customization-checklist.md
    05-failure-modes-and-red-flags.md
    06-deliverables-matrix.md
  templates/
    01-standard-response-format.md
    02-model-review-template.md
    03-experiment-note-template.md
    04-sr11-7-model-methodology-template.md
```

## External OpenCode Concepts This README Depends On

This pack relies on current OpenCode behavior for:

- `AGENTS.md` rule loading
- `opencode.json` instruction loading
- project-local skill discovery from `.opencode/skills/<name>/SKILL.md`
- project-local agent discovery from `.opencode/agents/*.md`
- subagent invocation by `@mention`
- task permission patterns for automatic subagent invocation

Official references:

- [OpenCode Rules](https://opencode.ai/docs/rules)
- [OpenCode Skills](https://opencode.ai/docs/skills)
- [OpenCode Agents](https://opencode.ai/docs/agents)
- [Federal Reserve SR 11-7](https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm)
- [Federal Reserve SR 26-2](https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm)

