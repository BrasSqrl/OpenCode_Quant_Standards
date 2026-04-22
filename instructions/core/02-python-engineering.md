# Python Engineering Standards

Use this guidance unless the repository already defines a different standard.

## Design

- Prefer small, typed functions with explicit inputs and outputs.
- Isolate side effects such as file I/O, network access, database calls, and plotting from core model logic.
- Keep notebooks for exploration. Move reusable production logic into importable modules.
- Favor clear data flow over deep inheritance or hidden state.
- Make configuration explicit and versionable. Avoid magic constants embedded across the codebase.

## Interfaces And Data Structures

- Add type hints to public functions and important internal boundaries.
- Use structured objects for configuration and domain concepts when that improves clarity.
- Validate assumptions at boundaries, especially for shapes, nullability, timestamp fields, units, and entity keys.
- Avoid mutating shared state across training, scoring, and evaluation paths.

## Testing And Verification

- Add unit tests for transforms, metrics, and edge cases that can silently corrupt results.
- Add a smoke test for fit and predict paths when models or pipelines change materially.
- Prefer regression tests for bugs involving numerics, schema drift, or time alignment.
- If the repo has no test harness, provide the smallest credible verification path instead of skipping validation silently.

## Numerical And Operational Discipline

- Set and document random seeds when stochastic behavior matters.
- Separate training artifacts, evaluation outputs, and temporary scratch files.
- Profile before optimizing. Do not trade clarity for speed without evidence.
- Raise specific errors when inputs violate required contracts.
- Follow repo tooling for linting, formatting, and type checks. If the repo is silent and the user asks for a recommendation, prefer lightweight, common tools rather than a heavy stack.
