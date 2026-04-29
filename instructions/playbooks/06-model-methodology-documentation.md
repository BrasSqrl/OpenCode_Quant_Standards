# Model Methodology Documentation Playbook

Use this playbook when the task is to draft, revise, assemble, or assess a model methodology document aligned to SR 11-7-style model risk management expectations or successor internal policy.

## Regulatory Currency Check

- SR 11-7 was issued by the Federal Reserve and OCC on April 4, 2011.
- As of April 17, 2026, Federal Reserve SR 26-2 states that revised interagency guidance supersedes and replaces SR 11-7 and SR 21-8.
- If the user asks specifically for SR 11-7, use the consolidated SR 11-7-style template unless the institution provides a required long-form template.
- Flag that the governing standard should be confirmed against current agency guidance and internal MRM policy.
- Do not present the document as regulator-ready unless the user provides institutional policy, required template version, and reviewer sign-off requirements.

Official references:

- Federal Reserve SR 11-7: https://www.federalreserve.gov/supervisionreg/srletters/sr1107.htm
- Federal Reserve SR 26-2: https://www.federalreserve.gov/supervisionreg/srletters/SR2602.htm

## Purpose

The methodology document should make the model understandable, challengeable, reproducible, and governable. It should give model owners, validators, approvers, auditors, and business users enough evidence to understand:

- what the model is intended to do
- how the model works
- what data and assumptions it depends on
- how performance was evaluated
- what limitations and weaknesses remain
- how the model is implemented, controlled, monitored, and governed

## Primary Deliverable

- Produce a `.docx` methodology document unless the user explicitly requests another format.
- Maintain an evidence index while drafting and include it in the DOCX appendix when feasible.
- Maintain an image inventory when the source corpus includes figures, screenshots, charts, or report images.
- Write generated documents, converted images, evidence indexes, and open-items files only to the current workspace or an approved output path.

## LLM Drafting Rules

- Treat this as evidence synthesis, not creative writing.
- Every material claim should be traceable to a source artifact or explicitly marked as missing evidence.
- Do not invent approvals, validation results, monitoring thresholds, business sign-offs, data lineage, model history, or regulatory applicability.
- Preserve section numbering from the approved template unless the user instructs otherwise.
- Prefer the consolidated template flow over the long-form checklist when both are available.
- Use the long-form crosswalk only to prove coverage or satisfy reviewer mapping requests.
- Mark optional sections as `Not applicable` only when the evidence supports that conclusion.
- Use placeholders such as `[EVIDENCE NEEDED: ...]` when source material is missing.
- Maintain a separate evidence index while drafting so reviewers can trace claims back to source files.
- Do not soften, hide, or omit blocking issues, warnings, failed checks, challenger-model findings, or validation limitations from source artifacts.

## Source Material To Gather First

Before drafting, inspect the `source_documents/` folder when it exists. Treat it as the default evidence corpus for model methodology and technical documentation unless `instructions/project/01-repository-context.md` specifies a different documentation source path.

For the Quant sister project workflow, `source_documents/` is intended to hold the exported Quant run bundle itself. The selected `run_*` folder may be directly under `source_documents/` or under `source_documents/quant_runs/`.

Use this precedence for general source material:

1. `source_documents/`
2. the source-artifact path named in `instructions/project/01-repository-context.md`
3. repository artifacts such as `docs/`, `notebooks/`, `reports/`, `configs/`, and `src/`
4. user-supplied files or pasted evidence

When the methodology document is being drafted from Quant sister project output, also read `instructions/project/08-quant-output-integration.md` and use the selected Quant run inside `source_documents/` as the empirical model evidence source. In that workflow:

- The selected Quant run under `source_documents/` controls model-development outputs, metrics, diagnostics, run warnings, feature-selection evidence, reproducibility evidence, and generated reports.
- Optional `source_documents/supplemental/` controls business purpose, approvals, governance, monitoring thresholds, institution-specific policy, and reviewer sign-off evidence when those items are not already in the run bundle.
- Conflicts between the selected run and supplemental evidence must be reported explicitly.

Within the available source material, inspect or request:

- model inventory entry
- business use case and intended-use statement
- model development notebooks or scripts
- training, validation, and test data descriptions
- data lineage, data quality reports, and feature definitions
- final model configuration and hyperparameters
- variable-selection evidence
- backtesting, out-of-sample, and out-of-time performance results
- sensitivity, stability, and explainability outputs
- implementation design, UAT evidence, and production controls
- monitoring plan and escalation thresholds
- approvals, effective challenge notes, model change log, and prior validation findings
- vendor documentation and third-party risk materials when applicable

## Quant Sister Project Output

If `source_documents/` contains a Quant run bundle, use it as the primary methodology evidence source. If the run bundle is somewhere else, set the source-documents path in repository context rather than treating it as a separate evidence source.

Use this sequence:

1. Select the run folder by user instruction, repo context, latest suitable `source_documents/run_*`, or latest suitable `source_documents/quant_runs/run_*`.
2. Read `START_HERE.md` and `artifact_manifest.json`.
3. Read `reports/decision_summary.md`, `reports/model_documentation_pack.md`, `reports/validation_pack.md`, and `reports/run_report.md` when present.
4. Read configuration, metrics, statistical tests, reproducibility, step manifest, and debug trace metadata when needed.
5. Inspect relevant diagnostic, performance, calibration, backtesting, explainability, scorecard, stability, and governance tables.
6. Discover image files and figure exports before deciding which visuals belong in the DOCX.

Do not edit the Quant run bundle. If images must be converted or screenshots must be created for DOCX insertion, write those derived files only to the methodology output workspace, not to `source_documents/`.

## Visual Evidence And Images

- Prefer existing PNG or JPEG chart exports from the selected run.
- If individual figure exports are unavailable, use `reports/interactive_report.html` as the visual diagnostic reference and ask whether to create screenshots or request a new run with PNG figure exports enabled.
- Embed only figures that support a material methodology claim.
- Caption every embedded image with figure number, title, interpretation, and source artifact path.
- Keep a sidecar image inventory with source path, candidate section, inclusion decision, caption, and any conversion or screenshot notes.
- Do not represent a chart as present in the DOCX unless it is actually embedded or explicitly listed as referenced-only.

## Drafting Sequence

1. Confirm the governing documentation standard, template version, and intended audience.
2. Select and document the evidence corpus, including `source_documents/` and any selected Quant run.
3. Build an evidence inventory and image inventory before prose drafting.
4. Create a consolidated document skeleton using `instructions/templates/04-sr11-7-model-methodology-template.md`.
5. Fill sections only from available evidence.
6. Add `[EVIDENCE NEEDED]` markers for missing support.
7. Add `[NOT APPLICABLE - BASIS: ...]` only when there is evidence supporting non-applicability.
8. Review for consistency across target, horizon, population, data windows, model version, run ID, and approval state.
9. Generate the DOCX in the approved output location.
10. Produce an open-items list for unresolved evidence gaps, approvals, or MRM policy questions.

## Quality Bar

A good draft is:

- structured to the approved template or the consolidated SR 11-7-style flow
- technically precise enough for effective challenge
- traceable to source artifacts
- delivered as a DOCX when requested by default workflow
- supported by a documented evidence index and image inventory
- explicit about assumptions, limitations, weaknesses, and usage constraints
- clear about what is final, draft, missing, or pending approval

## Common Failure Modes

- polishing unsupported claims into authoritative prose
- mixing validation conclusions with developer assertions
- omitting limitations because they are inconvenient
- presenting optional sections as not applicable without evidence
- losing consistency across model name, version, target, horizon, population, or effective date
- treating AI/ML explainability, fair lending, vendor, or consumer compliance sections as boilerplate
- embedding report images without captions, interpretation, or source paths
- writing generated methodology files into a read-only source artifact project

## Final Response Expectations

When helping draft or revise the methodology document, report:

- sections drafted or changed
- source artifacts used
- selected Quant run ID when applicable
- DOCX path and any sidecar evidence or image-inventory paths
- material assumptions made
- evidence gaps that remain
- sections requiring MRM, compliance, vendor, legal, or business-owner review
