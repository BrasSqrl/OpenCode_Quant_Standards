# Model Methodology Documentation Playbook

Use this playbook when the task is to draft, revise, assemble, or assess a model methodology document aligned to SR 11-7-style model risk management expectations or successor internal policy.

## Regulatory Currency Check

- SR 11-7 was issued by the Federal Reserve and OCC on April 4, 2011.
- As of April 17, 2026, Federal Reserve SR 26-2 states that revised interagency guidance supersedes and replaces SR 11-7 and SR 21-8.
- If the user asks specifically for SR 11-7, follow the requested SR 11-7 table of contents, but flag that the governing standard should be confirmed against current agency guidance and internal MRM policy.
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

## LLM Drafting Rules

- Treat this as evidence synthesis, not creative writing.
- Every material claim should be traceable to a source artifact or explicitly marked as missing evidence.
- Do not invent approvals, validation results, monitoring thresholds, business sign-offs, data lineage, model history, or regulatory applicability.
- Preserve section numbering from the approved template unless the user instructs otherwise.
- Mark optional sections as `Not applicable` only when the evidence supports that conclusion.
- Use placeholders such as `[EVIDENCE NEEDED: ...]` when source material is missing.
- Maintain a separate evidence index while drafting so reviewers can trace claims back to source files.

## Source Material To Gather First

Before drafting, inspect or request the available artifacts:

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

## Drafting Sequence

1. Confirm the governing documentation standard, template version, and intended audience.
2. Build an evidence inventory from the repo and supplied artifacts.
3. Create a document skeleton using `instructions/templates/04-sr11-7-model-methodology-template.md`.
4. Fill sections only from available evidence.
5. Add `[EVIDENCE NEEDED]` markers for missing support.
6. Add `[NOT APPLICABLE - BASIS: ...]` only when there is evidence supporting non-applicability.
7. Review for consistency across target, horizon, population, data windows, model version, and approval state.
8. Produce an open-items list for unresolved evidence gaps, approvals, or MRM policy questions.

## Quality Bar

A good draft is:

- structured exactly to the approved table of contents
- technically precise enough for effective challenge
- traceable to source artifacts
- explicit about assumptions, limitations, weaknesses, and usage constraints
- clear about what is final, draft, missing, or pending approval

## Common Failure Modes

- polishing unsupported claims into authoritative prose
- mixing validation conclusions with developer assertions
- omitting limitations because they are inconvenient
- presenting optional sections as not applicable without evidence
- losing consistency across model name, version, target, horizon, population, or effective date
- treating AI/ML explainability, fair lending, vendor, or consumer compliance sections as boilerplate

## Final Response Expectations

When helping draft or revise the methodology document, report:

- sections drafted or changed
- source artifacts used
- material assumptions made
- evidence gaps that remain
- sections requiring MRM, compliance, vendor, legal, or business-owner review
