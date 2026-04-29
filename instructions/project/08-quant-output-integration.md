# Quant Sister Project Output Integration

Use this guide when drafting an SR 11-7-style model methodology document from Quant sister project output placed under `source_documents/`.

No absolute local path is assumed. The intended portable workflow is to copy, export, or mount the Quant run bundle into `source_documents/` under the OpenCode workspace. Treat `source_documents/` as input evidence, not as the output folder for generated documents.

## Purpose

The Quant sister project produces model-development evidence. This standards pack turns that evidence into controlled methodology documentation after the evidence has been placed in `source_documents/`.

The target deliverable is a `.docx` model methodology document, supported by an evidence index, an image inventory, and an open-items list.

## Default Paths

- Standards pack or destination workspace: start OpenCode from the folder containing `AGENTS.md` and `opencode.json`.
- Default source-document folder: `source_documents/` under the OpenCode workspace root.
- Default Quant run location: a selected `run_*` folder directly under `source_documents/` or under `source_documents/quant_runs/`.
- Optional supplemental evidence location: `source_documents/supplemental/`.
- Default methodology output folder: the approved output location in `instructions/project/01-repository-context.md`, or `output/` when no repo-specific path is set.

If these paths differ, use the values in `instructions/project/01-repository-context.md` or the user's prompt.

## Expected `source_documents/` Layout

Preferred single-run layout:

```text
source_documents/
  run_YYYY-MM-DD_HH-MM-SS_UTC/
    START_HERE.md
    artifact_manifest.json
    config/
    metadata/
    reports/
    tables/
    figures/
  supplemental/
    approvals/
    monitoring/
    model_inventory/
    policy/
```

Preferred multi-run layout:

```text
source_documents/
  quant_runs/
    run_YYYY-MM-DD_HH-MM-SS_UTC/
    run_YYYY-MM-DD_HH-MM-SS_UTC/
  supplemental/
    approvals/
    monitoring/
    model_inventory/
    policy/
```

The `supplemental/` folder is optional. Use it only for evidence that is not included in the Quant run bundle, such as model inventory records, committee approvals, internal policy decisions, monitoring thresholds, vendor materials, or effective-challenge notes.

## Evidence Input Rule

- Do not write generated `.docx`, evidence indexes, image inventories, screenshots, converted images, or intermediate extracts into `source_documents/`.
- Write generated outputs only to `output/`, `docs/model_methodology/`, or another approved output path.
- If image conversion is needed, convert into the methodology output workspace, not into the Quant run folder.

## Run Selection

Use this selection order:

1. Explicit run folder named by the user.
2. Explicit run folder named in `instructions/project/01-repository-context.md`.
3. Latest suitable `source_documents/run_*` folder.
4. Latest suitable `source_documents/quant_runs/run_*` folder.
5. If no suitable run is found, stop drafting and report the missing run-bundle issue.

When selecting a run automatically, state the selected run ID and basis, such as latest `LastWriteTime`.

## Required Discovery Sequence

For a selected Quant run, inspect these artifacts first:

1. `START_HERE.md` for run identity, model family, execution mode, and folder map.
2. `artifact_manifest.json` for the machine-readable artifact index.
3. `reports/decision_summary.md` for the model decision, blocking issues, and review posture.
4. `reports/model_documentation_pack.md` for development-facing narrative evidence.
5. `reports/validation_pack.md` for validator-facing evidence.
6. `reports/run_report.md` for warnings, diagnostics, and run summary details.
7. `config/run_config.json` for final configuration, model setup, target setup, and artifact settings.
8. `metadata/metrics.json`, `metadata/statistical_tests.json`, `metadata/reproducibility_manifest.json`, `metadata/step_manifest.json`, and `metadata/run_debug_trace.json` when present.

Do not bulk-read large prediction or input-snapshot files unless the task requires row-level evidence. Prefer summaries, headers, row counts, schema, and already exported diagnostic tables.

## High-Value Quant Tables

Use the artifact manifest and table names to map evidence to methodology sections.

Data and preparation:

- `tables/diagnostics/data_quality_summary.csv`
- `tables/diagnostics/descriptive_statistics.csv`
- `tables/diagnostics/feature_dictionary.csv`
- `tables/diagnostics/missingness.csv`
- `tables/diagnostics/missingness_by_split.csv`
- `tables/diagnostics/imputation_rules.csv`
- `tables/diagnostics/working_data_snapshot.csv`
- `data/input/input_snapshot.csv` or `.parquet` only when needed for schema or row-level verification

Development and selection:

- `tables/diagnostics/variable_selection.csv`
- `model/feature_importance.csv`
- `model/model_summary.txt`
- `tables/model_performance/model_comparison.csv`
- `tables/scorecard/*` when the model is a scorecard
- `tables/explainability/*` when explainability evidence exists

Validation and performance:

- `metadata/metrics.json`
- `tables/model_performance/split_metrics.csv`
- `tables/model_performance/roc_curve.csv`
- `tables/model_performance/precision_recall_curve.csv`
- `tables/calibration/calibration.csv`
- `tables/calibration/calibration_summary.csv`
- `tables/calibration/threshold_analysis.csv`
- `tables/backtesting/backtest_summary.csv`
- `tables/backtesting/quantile_summary.csv`
- `tables/segmentation/segment_performance.csv`
- `tables/stability/psi.csv`
- `tables/statistical_tests/*`

Governance, controls, and reproducibility:

- `tables/governance/evidence_traceability_map.csv`
- `tables/governance/validation_checklist.csv`
- `tables/governance/workflow_guardrails.csv`
- `tables/governance/feature_policy_checks.csv`
- `tables/governance/model_numerical_diagnostics.csv`
- `tables/governance/report_payload_audit.csv`
- `metadata/reproducibility_manifest.json`
- `metadata/step_manifest.json`
- `code/HOW_TO_RERUN.md`
- `model_bundle_for_monitoring/monitoring_metadata.json`

## Source Precedence For Methodology Drafting

Use different sources for different claim types:

- Direct user instructions and repository context control the requested output, audience, and applicable internal policy.
- The selected Quant run under `source_documents/` controls empirical model evidence, metrics, diagnostics, feature selection, reproducibility, generated reports, and run-specific warnings.
- `source_documents/supplemental/` controls business purpose, approvals, governance procedures, monitoring thresholds, model inventory, committee decisions, and institution-specific language when those items are not already in the selected run.
- Repository code, notebooks, configs, and docs can supplement missing context, but they should not override the selected run's exported evidence unless the user explains why.

If sources conflict, do not reconcile silently. State the conflict and cite both artifacts.

## Figure And Image Handling

Quant run folders may include optional individual chart exports under `figures/html` and `figures/png`. Recent standard runs may have no standalone image files because individual figure exports can be disabled while `reports/interactive_report.html` still contains visual diagnostics.

Discovery order for visual assets:

1. Read `artifact_manifest.json` and inspect `figure_file_exports`, `figures`, `directories.figures`, `directories.figures_html`, and `directories.figures_png`.
2. Search the selected run for `.png`, `.jpg`, `.jpeg`, and `.svg` files.
3. Inspect `figures/html` for individual chart HTML files when PNGs are unavailable.
4. Use `reports/interactive_report.html` as the visual diagnostic source of record when individual figure files are not exported.

DOCX image rules:

- Prefer `.png` or `.jpg` for embedding in DOCX.
- Convert `.svg` or individual chart `.html` to `.png` only in the methodology output workspace.
- If only `interactive_report.html` exists and the final DOCX requires visuals, ask whether to create screenshots or request a new Quant run with individual PNG exports enabled.
- Do not embed decorative images.
- Include only figures that support a methodology claim, key diagnostic result, material limitation, model-selection decision, or monitoring requirement.
- Place each figure near the first section that discusses it.
- Add a figure number, title, concise interpretation, and source path for every embedded image.
- Preserve an image inventory with figure file path, source run, candidate methodology section, caption, and inclusion decision.

Preferred figure categories:

- model performance: ROC, precision-recall, lift/gain, confusion matrix, split metrics
- calibration: calibration curve, threshold analysis, score distribution
- explainability: feature importance, coefficient breakdown, PDP, ICE, ALE, marginal effects
- data quality: missingness, distribution shifts, feature diagnostics
- stability and monitoring: PSI, drift, backtesting, segment performance
- scorecard: points distribution, WOE/binning, reason-code frequency

## DOCX Assembly Requirements

The final methodology deliverable should be a `.docx` file unless the user explicitly asks for a different format.

Required outputs:

- `model_methodology.docx` or the repo-approved filename
- evidence index, preferably as an appendix inside the DOCX and as a sidecar Markdown or CSV file
- image inventory, preferably as a sidecar Markdown or CSV file
- open-items list for missing evidence, unsupported claims, pending approvals, and required reviewer decisions

DOCX structure rules:

- Use the consolidated SR 11-7-style template unless an institution-specific template is provided.
- Use Word heading styles or equivalent so the document can generate a table of contents.
- Include a placeholder table of contents if the DOCX generator cannot update Word fields directly.
- Keep section numbering stable.
- Use real tables for compact metrics and evidence indexes.
- Embed selected images with captions and source references.
- Mark unsupported material with `[EVIDENCE NEEDED: ...]`.
- Mark non-applicable content with `[NOT APPLICABLE - BASIS: ...]` only when evidence supports the conclusion.
- Include a regulatory-currency note when SR 11-7 is requested without confirming current internal MRM policy and successor guidance treatment.

## Section Mapping From Quant Artifacts

- Executive Summary and Model Identification: `START_HERE.md`, `decision_summary.md`, `model_documentation_pack.md`, `artifact_manifest.json`
- Business Context, Scope, and Interconnectedness: `source_documents/supplemental/`, `run_config.json`, `model_documentation_pack.md`
- Data, Population, and Preparation: diagnostics tables, feature dictionary, missingness tables, input snapshot metadata, data-quality summary
- Methodology and Model Development: run config, model summary, variable selection, feature importance, scorecard tables, explainability tables
- Validation, Performance, and Outcomes Analysis: metrics, split metrics, calibration, backtesting, model comparison, statistical tests, validation pack
- Assumptions, Limitations, Weaknesses, and Use Constraints: validation pack, decision summary warnings, workflow guardrails, source documents
- Implementation, Systems Integration, and Production Controls: rerun bundle, step manifest, reproducibility manifest, monitoring bundle, source documents
- User Procedures, Reporting, and Management Use: source documents, committee report, validation report, decision summary
- Ongoing Monitoring and Model Lifecycle Management: monitoring bundle metadata, PSI/stability tables, monitoring plans in `source_documents/supplemental/`
- Governance, Approvals, and Open Items: validation checklist, evidence traceability map, approvals in `source_documents/supplemental/`, decision summary

## Final Quality Checks

Before considering the methodology package complete:

- Confirm the selected Quant run ID is recorded in the document.
- Confirm each material metric or diagnostic claim cites a source artifact.
- Confirm every embedded figure has a caption and source.
- Confirm the evidence index includes source paths and status.
- Confirm warnings and blocking decision issues from the Quant run are not buried or softened.
- Confirm missing business, approval, monitoring, vendor, or policy evidence is explicitly listed as open.
- Confirm generated files are outside `source_documents/`.
