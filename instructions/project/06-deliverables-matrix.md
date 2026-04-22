# Deliverables Matrix

Use this matrix to determine the minimum artifacts that should accompany different task types.

## Implementation-Only Change

Minimum expected artifacts:

- code diff
- targeted tests
- smoke verification summary
- note confirming no methodology change

## Methodology Change

Minimum expected artifacts:

- code diff
- experiment note
- benchmark comparison against required baselines
- validation memo or review summary
- note describing what changed in methodology

## Data Pipeline Or Feature Logic Change

Minimum expected artifacts:

- code diff
- schema or contract validation evidence
- focused regression test for joins, timestamps, or null behavior
- note describing downstream model impact

## Backtest Or Evaluation Change

Minimum expected artifacts:

- explicit evaluation protocol
- benchmark comparison
- cost or execution assumptions
- result summary with stability notes

## Production-Impacting Change

Minimum expected artifacts:

- all artifacts from the relevant categories above
- release or promotion readiness summary
- required reviewer sign-off
- rollback or mitigation note when appropriate

## Operator Rule

If a task touches more than one category, combine the artifact requirements rather than selecting only one line from the matrix.
