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
- Follow the SR 11-7-style table of contents in `instructions/templates/04-sr11-7-model-methodology-template.md`
- Track evidence used for material claims
- Mark missing evidence, unresolved approvals, optional sections, and non-applicable sections clearly

## Regulatory Currency Rule

- SR 11-7 was issued on April 4, 2011.
- Federal Reserve SR 26-2, dated April 17, 2026, says revised interagency guidance supersedes and replaces SR 11-7 and SR 21-8.
- If the user specifically requests SR 11-7, follow the SR 11-7-style documentation structure, but flag that the governing policy should be confirmed against current agency guidance and internal MRM requirements.

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
- Use `[EVIDENCE NEEDED: ...]` for unsupported sections.
- Use `[NOT APPLICABLE - BASIS: ...]` only when non-applicability is supported.
- Maintain section numbering and headings unless the user provides a controlling template.
- Keep an evidence index linking material claims to source artifacts.
- Separate developer assertions from independent validation findings.
- Treat fair lending, consumer compliance, AI/ML, vendor, and regulatory approval sections as substantive, not boilerplate.

## Source Artifacts To Seek

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
