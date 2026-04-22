# Model Development Playbook

Use this playbook when the task is to build, extend, or modify a quantitative model or its supporting Python code.

## Before Coding

- Confirm the business objective, prediction target, horizon, and primary success metric.
- Identify the interfaces that matter: training input, scoring input, output schema, config, and artifact storage.
- Find the simplest credible baseline already in the repo or define one that can be implemented quickly.
- Check whether the change is methodological, implementation-only, or both.

## Implementation Approach

- Keep feature generation, model fitting, scoring, and evaluation as separable steps.
- Make timestamp handling and train versus validation boundaries explicit in code.
- Put important assumptions in config or clearly named constants, not scattered literals.
- Preserve the ability to reproduce a run from code version, config, seed, and dataset snapshot.
- Avoid notebook-only logic for anything the team will need to maintain or test.

## Coding Expectations

- Prefer modules that are easy to inspect over abstraction-heavy frameworks unless the repo already standardizes them.
- Validate shapes, columns, entity keys, and timestamp fields near the boundary where they enter the pipeline.
- Use deterministic behavior when feasible or explain why randomness is required.
- Keep model code separate from report generation, plotting, and ad hoc analysis.

## Verification

- Test transforms and target construction where silent errors are plausible.
- Run at least one focused smoke test through the updated training or scoring path.
- Compare against an existing baseline or prior behavior when the task changes model logic.
- State clearly whether validation is unit-level, integration-level, or methodological.

## Final Deliverable

Make it easy to see:

- what changed
- whether methodology changed or only implementation changed
- what validation was completed
- what risks or follow-up work remain
