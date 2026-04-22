---
name: model-review
description: Perform a structured quantitative model review covering methodology, implementation, controls, and production readiness
license: MIT
compatibility: opencode
metadata:
  audience: quant-teams
  workflow: review
---

## What I Do

- Structure a model review around material findings rather than narrative summary
- Separate methodology issues from implementation issues and operational risks
- Focus on target definition, horizon, point-in-time integrity, baselines, validation design, reproducibility, and release readiness
- Call out missing evidence explicitly instead of inferring a positive conclusion

## When To Use Me

Use this skill when the user wants a model review, validation memo, approval recommendation, challenge process, or control-focused assessment.

Do not use this skill for routine coding tasks or for broad repository exploration.

## Working Rules

- Findings first, ordered by severity or impact
- Tie every finding to evidence from code, config, tests, outputs, or missing artifacts
- Distinguish observed facts from assumptions
- Default to one of: approve, approve with conditions, hold pending evidence, reject
- Do not claim a model is production-ready without explicit validation evidence

## Review Checklist

- Is the target and horizon defined clearly enough to reproduce?
- Are decision time and data-availability time separated correctly?
- Is there visible risk of leakage, survivorship bias, or post-event contamination?
- Are baselines credible and comparisons fair?
- Is validation time-aware and operationally realistic?
- Are artifacts, configs, seeds, and code paths reproducible?
- Are the main failure modes and release gates visible?

## Output Shape

- Decision summary
- Material findings
- Evidence and impact
- Gaps in evidence
- Minimum actions required to clear the review
