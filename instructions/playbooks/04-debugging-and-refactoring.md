# Debugging And Refactoring Playbook

Use this playbook when the task is to diagnose a failure, investigate incorrect outputs, improve performance, or clean up code without changing intended behavior.

## Debugging Method

- Reproduce the issue before changing code.
- Narrow the problem to the smallest failing component or dataset slice.
- Distinguish numerical bugs, data bugs, infrastructure bugs, and expectation mismatches.
- Prefer direct evidence such as failing tests, minimal scripts, stack traces, and metric diffs over intuition.

## Refactoring Rules

- Preserve observable behavior unless the task explicitly includes a behavioral change.
- Keep public interfaces stable unless there is a clear reason and the impact is documented.
- Break large refactors into smaller, reviewable steps when possible.
- Do not mix cleanup work with methodological changes without making the distinction explicit.

## Quantitative Safeguards

- Check that refactors do not change timestamp alignment, join behavior, floating-point handling, or default parameter values by accident.
- Compare before and after outputs on a stable fixture or controlled sample when numerics matter.
- Add regression coverage for bugs involving schema drift, edge cases, or time alignment.

## Completion Standard

Report:

- how the issue was reproduced
- the root cause or strongest current hypothesis
- what changed
- what verification shows now
