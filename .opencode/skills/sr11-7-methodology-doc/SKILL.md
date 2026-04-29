---
name: sr11-7-methodology-doc
description: Draft or revise an SR 11-7-style model methodology document using supplied evidence, repository artifacts, and an explicit table of contents
license: MIT
compatibility: opencode
metadata:
  audience: quant-teams
  workflow: documentation
---

## What I Do

- Assemble model methodology documentation from available evidence
- Follow the consolidated SR 11-7-style methodology structure in `instructions/templates/04-sr11-7-model-methodology-template.md`
- Optimize drafting from Quant sister project run artifacts when available
- Produce a `.docx` methodology document as the default deliverable
- Include relevant image files and report figures with captions, interpretation, and source paths
- Use the appendix crosswalk when a reviewer needs traceability back to a longer institution-provided table of contents
- Track evidence used for material claims
- Mark missing evidence, unresolved approvals, optional sections, and non-applicable sections clearly

## Regulatory Currency Rule

- SR 11-7 was issued on April 4, 2011.
- Federal Reserve SR 26-2, dated April 17, 2026, says revised interagency guidance supersedes and replaces SR 11-7 and SR 21-8.
- If the user specifically requests SR 11-7, follow the consolidated SR 11-7-style documentation structure unless the institution provides a required long-form template, and flag that the governing policy should be confirmed against current agency guidance and internal MRM requirements.

## When To Use Me

Use this skill when the user asks for:

- a model methodology document
- SR 11-7 documentation
- model technical documentation
- model governance documentation
- a monitoring plan section
- a documentation gap assessment against the supplied table of contents

## Working Rules

- Do not invent evidence, approvals, validation conclusions, controls, monitoring thresholds, or model history.
- Look for a `source_documents/` folder first and treat it as the default source corpus unless repository context says otherwise.
- If the task references Quant output, a Quant run folder, or `source_documents/` as the methodology evidence corpus, read `instructions/project/08-quant-output-integration.md`.
- Treat `source_documents/` as input evidence. Do not write generated documents, converted images, screenshots, or intermediate files there.
- Use the selected Quant run under `source_documents/` for empirical model evidence, metrics, diagnostics, warnings, feature-selection evidence, and generated reports.
- Use optional `source_documents/supplemental/` for business purpose, approvals, governance procedures, monitoring thresholds, inventory facts, and institution-specific policy when those items are not in the run bundle.
- Use `[EVIDENCE NEEDED: ...]` for unsupported sections.
- Use `[NOT APPLICABLE - BASIS: ...]` only when non-applicability is supported.
- Maintain section numbering and headings unless the user provides a controlling template.
- Prefer cohesive sections over duplicative checklist-style drafting.
- Keep an evidence index linking material claims to source artifacts.
- Keep an image inventory for included, excluded, converted, or referenced figures.
- Separate developer assertions from independent validation findings.
- Treat fair lending, consumer compliance, AI/ML, vendor, and regulatory approval sections as substantive, not boilerplate.
- Do not hide or soften run warnings, blocking decision issues, failed checks, or challenger-model findings.

## Source Artifacts To Seek

Start with `source_documents/` when present. For the intended Quant workflow, locate the selected `run_*` folder directly under `source_documents/` or under `source_documents/quant_runs/`. Then inspect repo-local artifacts or user-supplied materials as needed.

- model inventory entry
- model development scripts, notebooks, and configs
- data lineage and data quality artifacts
- feature definitions and variable selection evidence
- performance, backtesting, sensitivity, and explainability reports
- implementation, UAT, and production-control artifacts
- monitoring plans and threshold definitions
- approval, effective challenge, and validation records
- vendor and third-party risk materials where applicable

For Quant sister project output, inspect the selected run's:

- `START_HERE.md`
- `artifact_manifest.json`
- `reports/decision_summary.md`
- `reports/model_documentation_pack.md`
- `reports/validation_pack.md`
- `reports/run_report.md`
- `config/run_config.json`
- `metadata/metrics.json`
- `metadata/statistical_tests.json`
- `metadata/reproducibility_manifest.json`
- high-value `tables/` groups for diagnostics, performance, calibration, backtesting, explainability, scorecard, stability, and governance
- optional `figures/png`, `figures/html`, or `reports/interactive_report.html` visual assets

## DOCX And Image Rules

- Write the final methodology as `.docx` unless the user explicitly asks for Markdown only.
- Write the DOCX to the approved output location, not inside `source_documents/`.
- Embed only relevant PNG or JPEG visuals that support methodology claims.
- If only HTML figures or `interactive_report.html` exist, ask whether to create screenshots or request PNG figure exports.
- Caption every embedded image with figure number, title, concise interpretation, and source path.
- Include an evidence index and image inventory as DOCX appendices when feasible and sidecar files when useful.

## Output Shape

- `.docx` methodology document path
- evidence index path or appendix location
- image inventory path or appendix location
- drafted sections or revised sections
- selected Quant run ID when applicable
- open items and missing evidence
- optional sections proposed for deletion and the basis
- review gates requiring MRM, compliance, legal, business-owner, vendor, or technology review
