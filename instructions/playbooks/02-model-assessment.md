# Model Assessment Playbook

Use this playbook when the task is to review, validate, challenge, or approve a quantitative model, experiment, or implementation.

## Assessment Scope

- Identify whether the review is focused on methodology, code quality, controls, production readiness, or all of them.
- State what artifacts were actually reviewed: code, config, notebook, report, backtest output, or documentation.
- Mark missing evidence explicitly instead of assuming a positive or negative conclusion.

## Methodology Review

- Check that the target, horizon, universe, and decision timestamp are well defined.
- Look for leakage, peeking, survivorship bias, or unavailable-at-decision-time features.
- Check whether baselines are credible and whether the claimed improvement is meaningful.
- Review evaluation splits, regime coverage, segment stability, and realistic cost or execution assumptions when relevant.

## Implementation Review

- Confirm that the code path used for evidence can be reproduced from repository state and configuration.
- Check that key transformations, metrics, and edge cases are testable and not hidden in notebooks or one-off scripts.
- Look for fragile joins, silent coercions, ambiguous timezone handling, and mutable shared state.
- Verify that artifacts, seeds, and important parameters are captured well enough to rerun the analysis.

## Control Decision

Default to one of these outcomes:

- Approve
- Approve with conditions
- Hold pending evidence
- Reject

Tie the outcome to evidence, not confidence alone.

## Assessment Output

Prioritize:

- material findings first
- the evidence behind each finding
- the operational impact if unresolved
- the minimum actions required to clear the issue
