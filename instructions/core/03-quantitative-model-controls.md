# Quantitative Model Controls

All quantitative work should be explicit about the decision being supported, the data available at decision time, and the evidence behind the claimed behavior.

## Problem Definition

- Define the target, prediction horizon, unit of analysis, and decision timestamp.
- Distinguish event time, data availability time, and execution time.
- State the intended use of the model: research aid, production signal, risk control, or operational forecast.

## Data Controls

- Check for label leakage, look-ahead bias, survivorship bias, and post-event feature contamination.
- Make joins, filters, and universe definitions auditable.
- Be explicit about missing data handling, outlier treatment, and corporate action or price adjustment rules where relevant.
- Record dataset versions, extraction windows, and feature-generation assumptions when they affect reproducibility.

## Evaluation Controls

- Use time-aware validation for time-dependent problems.
- Compare against simple, defensible baselines before claiming improvement.
- Reflect realistic constraints such as latency, turnover, transaction costs, capacity, and execution assumptions when they matter.
- Inspect stability across time periods, segments, and stress conditions instead of relying on a single headline metric.
- Separate in-sample tuning evidence from out-of-sample validation evidence.

## Governance

- Separate methodological soundness from implementation quality and operational readiness.
- Document key assumptions, known failure modes, and monitoring requirements.
- Treat missing evidence as a gap to report, not a detail to gloss over.
- Do not present a model as production-ready based solely on exploratory notebook results.
