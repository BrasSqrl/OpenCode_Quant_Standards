# Data Pipelines And Feature Engineering Playbook

Use this playbook when the task involves ingestion, cleaning, joins, feature creation, dataset assembly, or feature-store style logic.

## Data Pipeline Expectations

- Make source tables, keys, filters, and timestamp semantics explicit.
- Prefer idempotent, composable transforms over monolithic scripts with hidden state.
- Validate schema, duplicates, null behavior, and row-count expectations at important boundaries.
- Keep raw inputs, intermediate transforms, and final modeling tables distinguishable.

## Time And Availability Controls

- Align every feature with the time it would have been known in production.
- Be careful with forward fills, rolling windows, and lag features that can leak future information.
- Use explicit timezone handling and document conversions.
- Distinguish observation time from publication time when external data releases are involved.

## Feature Engineering

- Favor interpretable, auditable features over opaque transformations unless the use case requires otherwise.
- Document feature intent, units, and expected ranges for features that materially drive the model.
- Handle outliers and missingness deliberately rather than relying on accidental library defaults.
- Avoid joining auxiliary data that changes the investable universe without calling it out.

## Verification

- Add contract-style tests for required columns, dtypes, uniqueness assumptions, and timestamp ordering where they matter.
- Use small controlled fixtures to verify joins and rolling logic.
- When a pipeline change affects downstream models, say so explicitly and recommend the minimum reruns needed.
