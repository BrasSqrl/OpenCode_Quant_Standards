# Repository Context Template

This file is meant to be edited after this standards pack is copied into a real repository.

Important:

- Replace bracketed prompts with short factual entries.
- Keep entries terse. Prefer noun phrases, exact commands, and concrete paths over prose.
- If a field is unknown, write `UNKNOWN` rather than guessing.
- For a worked example, see `instructions/project/02-repository-context-example.md`.
- If this file has not been customized yet, rely on actual repository files and the user request instead.

## Working Assumption

- Primary user profile: experienced quantitative modeler
- Typical task stage: [research | feature engineering | model training | scoring | validation | review | monitoring]
- Expected response style: concise, technical, no introductory teaching unless asked

## Repository Snapshot

- Business purpose: [one line]
- Primary model domain: [alpha | forecasting | classification | regression | risk | pricing | surveillance | other]
- Asset class or business domain: [one line]
- Unit of prediction: [security | issuer | account | trade | loan | portfolio | other]
- Target variable: [one line]
- Prediction horizon: [one line]
- Primary success metrics: [top 2 to 4 metrics]
- Production status: [research only | pre-production | production]
- Main decision supported: [one line]

## Canonical Commands

- Environment bootstrap: [exact command]
- Lint: [exact command]
- Format: [exact command]
- Type check: [exact command]
- Unit tests: [exact command]
- Targeted model test: [exact command]
- Smoke run or local workflow: [exact command]
- Backtest or evaluation entry point: [exact command or script path]

## Codebase Map

- Main Python package: [path]
- Model implementations: [path]
- Feature pipelines: [path]
- Evaluation or backtesting code: [path]
- Shared utilities: [path]
- Tests: [path]
- Config files: [path]
- Data contracts or schemas: [path]
- Notebooks or research artifacts: [path]
- Output or artifact directories: [path]

## Quantitative Conventions

- Label construction rule: [one line]
- Decision timestamp convention: [one line]
- Timezone and calendar rule: [one line]
- Point-in-time or as-of data rule: [one line]
- Train, validation, and test split rule: [one line]
- Required baseline models: [list]
- Required cost, slippage, or operational assumptions: [one line]
- Minimum validation evidence before merge: [one line]
- Required robustness or slice checks: [one line]

## Data And Security Constraints

- Sensitive datasets or identifiers: [one line]
- Never expose in logs, tests, or examples: [one line]
- Approved synthetic or masked test-data rule: [one line]
- External network or tool restrictions: [one line]
- Restricted storage locations or artifact types: [one line]

## Review And Release Requirements

- Required reviewers or sign-off path: [one line]
- Required artifacts for methodology changes: [diff note | experiment note | validation memo | benchmark table | other]
- Required artifacts for implementation-only changes: [tests | smoke output | profiling note | other]
- Release gate for production-impacting changes: [one line]

## Model Methodology Documentation

- Governing documentation standard: [SR 11-7 | SR 26-2 | internal MRM policy | other]
- Methodology document owner: [role or team]
- Required output format: [docx | docx plus sidecar markdown/csv | other]
- Approved methodology DOCX output path: [path/model_methodology.docx]
- Approved sidecar output location: [path for evidence index, image inventory, open items]
- Source documents folder: [source_documents | other path]
- Source documents contents: [exported Quant run bundle at source_documents/run_* or source_documents/quant_runs/run_*]
- Supplemental methodology evidence: [source_documents/supplemental paths for approvals, monitoring, inventory, policy, vendor materials | none]
- Quant run selection rule: [explicit run folder | latest successful run_* | user supplied each time]
- Quant run folder: [path to selected run folder | leave blank until selected]
- Quant image source rule: [artifact_manifest figures/png | figures/png | interactive_report.html screenshots with approval | none]
- Image inclusion rule: [embed relevant PNG/JPEG figures with captions and source paths | reference only | other]
- Required evidence index format: [section-level citations | appendix evidence table | other]
- Required image inventory format: [appendix table | sidecar markdown/csv | other]
- Required reviewer sign-off before distribution: [role or committee]
- Sections that may be omitted only if not applicable: [list]
