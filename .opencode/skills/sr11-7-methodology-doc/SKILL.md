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
- Use `[EVIDENCE NEEDED: ...]` for unsupported sections.
- Use `[NOT APPLICABLE - BASIS: ...]` only when non-applicability is supported.
- Maintain section numbering and headings unless the user provides a controlling template.
- Prefer cohesive sections over duplicative checklist-style drafting.
- Keep an evidence index linking material claims to source artifacts.
- Separate developer assertions from independent validation findings.
- Treat fair lending, consumer compliance, AI/ML, vendor, and regulatory approval sections as substantive, not boilerplate.

## Source Artifacts To Seek

Start with `source_documents/` when present. Then inspect repo-local artifacts or user-supplied materials as needed.

- model inventory entry
- model development scripts, notebooks, and configs
- data lineage and data quality artifacts
- feature definitions and variable selection evidence
- performance, backtesting, sensitivity, and explainability reports
- implementation, UAT, and production-control artifacts
- monitoring plans and threshold definitions
- approval, effective challenge, and validation records
- vendor and third-party risk materials where applicable

## Output Shape

- Drafted sections or revised sections
- Evidence index
- Open items and missing evidence
- Optional sections proposed for deletion and the basis
- Review gates requiring MRM, compliance, legal, business-owner, vendor, or technology review
