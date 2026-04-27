# SR 11-7-Style Model Methodology Document Template

Use this template when drafting a model methodology document aligned to SR 11-7-style model risk management expectations or successor internal policy. This is a consolidated structure: it preserves the substance of the longer table of contents while reducing duplicate headings and improving document flow.

Important:

- Follow the institution's approved template if one is provided.
- Treat this file as a drafting scaffold, not a regulatory safe harbor.
- If evidence is missing, keep the relevant section and mark it with `[EVIDENCE NEEDED: ...]`.
- If a topic is not applicable, write `[NOT APPLICABLE - BASIS: ...]`.
- Maintain an evidence index linking material claims to source artifacts.
- Do not invent approvals, validation findings, monitoring thresholds, model history, or regulatory applicability.

## 1 Executive Summary and Model Identification

Purpose: give approvers, validators, auditors, and senior management a concise view of what the model is, how it is used, whether it is ready for use, and what material risks remain.

Include:

- model name, inventory ID, version, owner, developer, user group, and effective date
- model purpose, intended use, approved use restrictions, and prohibited uses
- model risk tier, materiality, and business criticality
- AI/ML classification and explainability posture, if applicable
- final model summary and primary methodology
- key performance results and benchmark comparison
- key assumptions, limitations, weaknesses, and compensating controls
- model history, change log, predecessor model comparison, and related MRAs
- approval status, effective challenge summary, and open approval conditions
- vendor or third-party dependency summary, if applicable

## 2 Business Context, Scope, and Interconnectedness

Purpose: explain the business problem, model hypothesis, population, boundaries, and connected model ecosystem.

Include:

- portfolio, product, business process, or decision context
- population, segmentation, inclusion and exclusion boundaries
- model hypothesis and expected relationship between inputs and outputs
- model users and decisions supported
- frequency of use and reporting requirements
- upstream data sources, feeder models, related models, downstream models, and overlays
- consumer compliance, fair and responsible banking, or regulatory approval considerations, if applicable

## 3 Data, Population, and Preparation

Purpose: document data suitability, lineage, quality, transformations, and any differences between the original population and final modeling population.

Include:

- data sources, ownership, lineage, and data flow diagram or narrative
- observation window, outcome window, population definition, and sampling approach
- external data, vendor data, or third-party data applicability
- data quality assessment, known issues, and remediation
- missing-value handling, imputation, cleaning, exclusions, adjustments, aggregation, and transformations
- key statistics for original data, final modeling data, and important segments
- comparison of original population, development sample, validation sample, and final production population
- data controls, input controls, reconciliation checks, and production data dependencies

## 4 Methodology and Model Development

Purpose: make the model design, theoretical basis, development choices, and final selection understandable and challengeable.

Include:

- conceptual theory, model logic, and design rationale
- materiality thresholds and business rules
- variables considered, transformations considered, and variable selection process
- statistical analysis used for selection
- alternate approaches and rejected models
- business input or expert judgment used in development
- final model selected and rationale for selection
- principal formulas, algorithms, objective functions, or decision rules
- hyperparameter tuning, training procedure, and reproducibility controls, if applicable
- explainability method and feature-importance evidence, if applicable
- model update, recalibration, redevelopment, or benchmarking approach, if applicable

## 5 Validation, Performance, and Outcomes Analysis

Purpose: consolidate evidence that the model is conceptually sound, empirically supported, independently challenged, and performing within acceptable thresholds.

Include:

- validation scope, independence, date, reviewer, and validation status
- conceptual soundness assessment
- standard evaluation statistics, diagnostics, and testing results
- out-of-sample, out-of-time, cross-validation, or backtesting evidence
- outcomes analysis comparing model output to realized outcomes
- benchmark, challenger, predecessor, or industry-data comparison
- sensitivity analysis, stability analysis, stress or scenario testing, and segment performance
- threshold breaches, exceptions, overrides, and unresolved validation findings
- limitations of validation evidence and compensating controls

## 6 Assumptions, Limitations, Weaknesses, and Use Constraints

Purpose: make model risk visible and connect limitations to allowed use, controls, monitoring, and management reporting.

Include:

- key assumptions and their rationale
- known limitations, weaknesses, data constraints, and methodology constraints
- conditions under which model use is unreliable or prohibited
- compensating controls, overlays, adjustments, or management judgment
- residual risks requiring management awareness
- required remediation, redevelopment triggers, or restrictions on use

## 7 Implementation, Systems Integration, and Production Controls

Purpose: document how the model is implemented, controlled, tested, and operated in production.

Include:

- implementation plan and deployment architecture
- configuration management database or inventory references
- production system integration, batch or real-time workflow, and dependency map
- user acceptance testing results and implementation defects
- open implementation issues and remediation owners
- model access controls and segregation of duties
- input controls, processing controls, output controls, and reconciliation controls
- change management, release management, rollback, and incident procedures
- vendor documentation, third-party contingency plans, and Coupa or third-party risk information, if applicable

## 8 User Procedures, Reporting, and Management Use

Purpose: show how model outputs are consumed, reported, interpreted, and controlled by business users.

Include:

- user guidelines, operating procedures, and interpretation guidance
- management reports, report recipients, and reporting frequency
- output definitions, thresholds, alerts, and escalation points
- override procedures, overlay governance, and manual adjustment controls
- end user committee name, references, and decision rights
- training, communication, and handoff requirements for model users

## 9 Ongoing Monitoring and Model Lifecycle Management

Purpose: define how the organization will detect performance degradation, data drift, invalid assumptions, operational issues, and needed model changes.

Include:

- models addressed in the monitoring plan
- risk factor monitoring and metric monitoring
- monitoring frequency, ownership, and submission requirements to MRM
- thresholds, tolerances, traffic-light rules, and breach escalation
- population stability, data quality, performance, calibration, bias/fairness, explainability, and usage monitoring as applicable
- overlays, temporary adjustments, and management action triggers
- periodic review, annual review, recalibration, redevelopment, retirement, and change-log requirements

## 10 Governance, Approvals, and Open Items

Purpose: make ownership, accountability, approval status, and unresolved work explicit.

Include:

- model owner, developer, validator, user, technology owner, and control owner roles
- approval bodies, approval dates, conditions, and expiration or review cycle
- effective challenge summary and outstanding challenge items
- related MRAs, audit findings, regulatory commitments, or policy exceptions
- open issues, remediation owners, due dates, and blocking status
- final readiness decision or distribution restrictions

## Appendix A Evidence Index

| Section | Claim or Content Area | Source Artifact | Owner | Status |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | Needed |

## Appendix B Template Version Change History

| Version | Date | Author | Summary of Changes | Approval |
| --- | --- | --- | --- | --- |
| TBD | TBD | TBD | TBD | TBD |

## Appendix C Optional Long-Form Crosswalk

Use this crosswalk only when a reviewer needs to map the consolidated structure back to the longer institution-provided table of contents.

| Consolidated Section | Long-Form Topics Covered |
| --- | --- |
| 1 Executive Summary and Model Identification | executive summary, intended use, AI/ML, final model summary, results, assumptions, reporting, history, change log, approvals, predecessor model, MRA, vendor summary |
| 2 Business Context, Scope, and Interconnectedness | portfolio context, segmentation, hypothesis, feeder and downstream models, compliance and regulatory applicability |
| 3 Data, Population, and Preparation | data sources, data flow, quality, external data, statistics, cleaning, exclusions, aggregation, sampling, original versus final data |
| 4 Methodology and Model Development | theory, logic, thresholds, variables, transformations, selection, rejected models, business input, final model, formulas, tuning, explainability, updates, benchmarks |
| 5 Validation, Performance, and Outcomes Analysis | diagnostics, backtesting, out-of-time testing, K-fold testing, sensitivity, outcomes analysis, independent validation, unresolved findings |
| 6 Assumptions, Limitations, Weaknesses, and Use Constraints | final assumptions, limitations, weaknesses, restrictions, compensating controls |
| 7 Implementation, Systems Integration, and Production Controls | implementation plan, CMDB, system implementation, UAT, open implementation issues, input controls, production controls, access controls, vendor controls |
| 8 User Procedures, Reporting, and Management Use | user guidelines, management reporting, output controls, overlays, EUC references |
| 9 Ongoing Monitoring and Model Lifecycle Management | monitoring plan, risk factors, metrics, frequency, escalation, overlays, model update lifecycle |
| 10 Governance, Approvals, and Open Items | approvals, effective challenge, MRAs, open items, ownership, readiness decision |
