# Repository Context Example

This is a worked example for a typical enterprise quantitative research repository.

Important:

- These values are illustrative, not authoritative for any real repository.
- Copy the patterns, field granularity, and level of specificity.
- Do not use these example facts as if they describe your actual repo.

## Working Assumption

- Primary user profile: experienced quantitative modeler
- Typical task stage: model training
- Expected response style: concise, technical, no introductory teaching unless asked

## Repository Snapshot

- Business purpose: develop, validate, and operationalize cross-sectional equity signals for US large- and mid-cap stocks, with reproducible research, controlled backtesting, and batch production scoring
- Primary model domain: alpha
- Asset class or business domain: US cash equities
- Unit of prediction: security
- Target variable: 5-trading-day forward sector-neutral residual return from next-day close to day-plus-5 close
- Prediction horizon: 5 trading days
- Primary success metrics: out-of-sample Spearman IC, top-minus-bottom decile spread net of costs, turnover-adjusted information ratio, stability of factor exposures
- Production status: pre-production
- Main decision supported: weekly model promotion and daily signal publication for downstream portfolio construction

## Canonical Commands

- Environment bootstrap: `python -m pip install -e .[dev]`
- Lint: `ruff check src tests`
- Format: `ruff format src tests`
- Type check: `pyright src`
- Unit tests: `pytest tests/unit -q`
- Targeted model test: `pytest tests/models/test_training_pipeline.py -q`
- Smoke run or local workflow: `python -m src.cli.train --config configs/equity_xs_baseline.yaml --as-of 2025-12-31`
- Backtest or evaluation entry point: `python -m src.research.backtest --config configs/equity_xs_baseline.yaml --start 2022-01-03 --end 2025-12-31`

## Codebase Map

- Main Python package: `src/quant_platform`
- Model implementations: `src/quant_platform/models`
- Feature pipelines: `src/quant_platform/features`
- Evaluation or backtesting code: `src/quant_platform/evaluation`
- Shared utilities: `src/quant_platform/common`
- Tests: `tests`
- Config files: `configs`
- Data contracts or schemas: `schemas`
- Notebooks or research artifacts: `notebooks`
- Output or artifact directories: `artifacts`

## Quantitative Conventions

- Label construction rule: labels are built from split-adjusted closes, winsorized cross-sectionally, then residualized by sector and beta bucket before training
- Decision timestamp convention: features must be available by 16:15 America/New_York on trade date T for positions entered at next regular-session open on T+1
- Timezone and calendar rule: all trading timestamps use `America/New_York` and the NYSE business calendar; non-trading dates must never be forward-filled into the investable universe
- Point-in-time or as-of data rule: joins must use point-in-time snapshots keyed by effective timestamp; revised fundamentals and restatements cannot appear before publication timestamp plus vendor lag
- Train, validation, and test split rule: use expanding-window training, rolling validation, and fixed final holdout by date; never random-shuffle rows across time
- Required baseline models: sector-neutral linear rank model, ridge regression baseline, lasso baseline
- Required cost, slippage, or operational assumptions: report results with 5 bps per side, one-day execution lag, ADV participation cap, and turnover penalty
- Minimum validation evidence before merge: passing unit tests, successful end-to-end train-and-score smoke run, walk-forward out-of-sample benchmark comparison, and no unresolved leakage findings
- Required robustness or slice checks: monthly IC stability, market-cap bucket performance, sector neutrality drift, high-volatility regime behavior, and top-feature stability over time

## Data And Security Constraints

- Sensitive datasets or identifiers: vendor market data, issuer identifiers, proprietary feature values, portfolio holdings, and any client or account mappings
- Never expose in logs, tests, or examples: raw vendor extracts, real account IDs, production signal files, credentials, and uncensored holdings snapshots
- Approved synthetic or masked test-data rule: tests must use synthetic fixtures or masked extracts that preserve schema and key edge cases without exposing real securities or client records
- External network or tool restrictions: no outbound calls to vendor APIs or cloud storage from routine local tests; production credentials may not be used in ad hoc notebooks
- Restricted storage locations or artifact types: model artifacts and backtest outputs must remain under approved encrypted workspace paths; no export to personal drives or public buckets

## Review And Release Requirements

- Required reviewers or sign-off path: one quantitative research reviewer plus one model-risk or platform reviewer for methodology changes; code-owner approval for production-path changes
- Required artifacts for methodology changes: diff note, experiment note, validation memo, benchmark table
- Required artifacts for implementation-only changes: tests, smoke output, profiling note when performance is affected
- Release gate for production-impacting changes: no production promotion without approved validation artifacts, green CI, reproducible config, and explicit sign-off from the strategy owner

## Model Methodology Documentation

- Governing documentation standard: SR 11-7 format retained by internal MRM policy; verify whether SR 26-2 updates are required before final approval
- Methodology document owner: Quantitative Research Lead
- Required output format: DOCX plus sidecar Markdown evidence index, image inventory, and open-items log
- Approved methodology DOCX output path: `docs/model_methodology/equity_signal_methodology.docx`
- Approved sidecar output location: `docs/model_methodology/supporting_artifacts`
- Source documents folder: `source_documents`
- Source documents contents: exported Quant run bundle at `source_documents/run_*` or `source_documents/quant_runs/run_*`
- Supplemental methodology evidence: `source_documents/supplemental/model_inventory`, `source_documents/supplemental/monitoring`, `source_documents/supplemental/approvals`, `source_documents/supplemental/policy`, and `source_documents/supplemental/vendor` when needed
- Quant run selection rule: use the explicit run folder supplied by the model owner; if absent, use the latest successful `run_*` folder under `source_documents`
- Quant run folder: leave blank until a run is selected
- Quant image source rule: prefer `artifact_manifest.json` figure entries and `figures/png`; if unavailable, use `reports/interactive_report.html` as reference and request screenshot approval or a new run with PNG figure exports enabled
- Image inclusion rule: embed only relevant PNG/JPEG figures with figure number, caption, interpretation, and source path
- Required evidence index format: appendix evidence table with section, claim, source artifact, owner, and status
- Required image inventory format: sidecar Markdown table plus Appendix D when figures are embedded
- Required reviewer sign-off before distribution: Model Risk Management reviewer and strategy owner
- Sections that may be omitted only if not applicable: predecessor model, related MRA, vendor model, external data, regulatory approval, overlays
