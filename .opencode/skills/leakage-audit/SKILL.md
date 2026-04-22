---
name: leakage-audit
description: Audit a quantitative pipeline for target leakage, point-in-time violations, timestamp misuse, and survivorship bias
license: MIT
compatibility: opencode
metadata:
  audience: quant-teams
  workflow: controls
---

## What I Do

- Inspect how targets, features, joins, and timestamps interact
- Look for future information entering training, scoring, or evaluation paths
- Challenge assumptions around as-of joins, revisions, forward fills, rolling windows, and universe filters
- Summarize leakage risk with concrete evidence and required remediation

## When To Use Me

Use this skill when the task involves target construction, point-in-time data access, feature generation, dataset assembly, backtesting, or unexplained performance that may be caused by leakage.

## Audit Checklist

- What is the true decision timestamp?
- When was each feature known in practice?
- Are joins based on event time, publish time, effective time, or an ambiguous surrogate?
- Do rolling features or forward fills accidentally access future rows?
- Are restatements, revisions, or delayed vendor fields treated as if they were immediate?
- Does universe construction depend on future membership information?
- Does evaluation use labels or filters that would not exist at scoring time?

## Working Rules

- Be skeptical of unexplained performance improvements
- Prefer explicit timestamp diagrams or table-level explanations when needed
- Report uncertainty directly when the code or docs do not prove point-in-time integrity
- Recommend the minimum reproducible test or fixture that would confirm the issue

## Output Shape

- Leakage risk summary
- Suspected leakage vectors
- Evidence inspected
- Confidence level and unknowns
- Required fixes or validation checks
