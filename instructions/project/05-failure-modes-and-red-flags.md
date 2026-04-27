# Failure Modes And Red Flags

Use this file when the task involves model review, debugging suspicious performance, data pipeline changes, or production-readiness assessment.

## Data And Timing Red Flags

- features use timestamps that do not reflect real-world data availability
- joins rely on current snapshots instead of point-in-time snapshots
- revisions or restatements appear before publication lag would allow
- forward fills cross boundaries where the value would not have been known
- random train-test splitting is used on time-dependent data
- investable universe membership is constructed with future information

## Methodology Red Flags

- target definition is vague or undocumented
- baseline models are missing or intentionally weak
- metric gains are reported without stability analysis
- cost, slippage, latency, or turnover assumptions are absent where they matter
- evaluation and tuning are done repeatedly on the same holdout slice
- model complexity increased without evidence that the simpler baseline was exhausted

## Implementation Red Flags

- core logic lives only in notebooks
- feature engineering, model fitting, and evaluation are tightly entangled
- timestamp handling is implicit or scattered across the codebase
- important configuration is hidden in constants or ad hoc scripts
- tests cover only happy paths and not edge cases that affect numerics or alignment
- artifacts cannot be traced to code version, config, seed, and dataset definition

## Governance Red Flags

- production-readiness is claimed from exploratory notebook output alone
- missing validation artifacts are treated as a documentation issue rather than a control failure
- methodology changes are mixed with refactors in ways that obscure review
- no explicit owner exists for promotion or rollback decisions
- sensitive data appears in test fixtures, examples, or debug logs

## Methodology Documentation Red Flags

- the document contains unsupported claims without an evidence index
- approvals, effective challenge, model history, or validation results are described without source artifacts
- optional sections are deleted without a documented non-applicability basis
- AI/ML, explainability, fair lending, vendor, or regulatory approval sections are treated as boilerplate
- model purpose, target, horizon, population, model version, or effective date differ across sections
- SR 11-7 is named as the governing standard without confirming current agency guidance or internal MRM policy

## Response Pattern

When using this file:

- name the red flag directly
- tie it to code, config, outputs, or missing evidence
- explain the operational or methodological consequence
- recommend the smallest action that would resolve or clarify the issue
