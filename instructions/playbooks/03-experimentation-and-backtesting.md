# Experimentation And Backtesting Playbook

Use this playbook when the task involves experimental design, benchmark comparison, backtesting, walk-forward validation, or result interpretation.

## Experimental Setup

- Write down the hypothesis before tuning.
- Record the dataset window, universe, feature set, target definition, and random seed.
- Keep a clear distinction between training, validation, test, and any final holdout periods.
- Use time-aware splits for time-dependent problems unless there is a documented reason not to.

## Backtesting Discipline

- Make signal generation time, order time, and assumed execution time explicit.
- Include realistic constraints such as slippage, fees, turnover, borrow, liquidity, or latency when they are relevant to the strategy.
- Avoid parameter searches that reuse the same evaluation slice without acknowledging selection bias.
- Report benchmark results alongside the candidate model, not after the fact.

## Result Interpretation

- Do not elevate a single best run over the broader distribution of outcomes.
- Look for stability across periods, sectors, entities, or regimes that matter to the use case.
- Treat negative or inconclusive results as useful evidence rather than something to hide.
- Separate exploratory evidence from evidence that is strong enough to support deployment or policy changes.

## What To Preserve

Capture enough detail for another engineer or reviewer to rerun the work:

- code version
- config
- dataset snapshot or extraction definition
- seed
- evaluation protocol
- reported metrics and plots
