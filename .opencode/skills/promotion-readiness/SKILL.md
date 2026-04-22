---
name: promotion-readiness
description: Evaluate whether a quantitative model or pipeline change is ready for merge, release, or production promotion based on evidence and controls
license: MIT
compatibility: opencode
metadata:
  audience: quant-teams
  workflow: release
---

## What I Do

- Assess whether the available evidence is sufficient for the claimed promotion state
- Separate implementation readiness from methodological readiness
- Check that validation artifacts, sign-offs, and operational safeguards are visible
- Produce a clear go, conditional go, or hold recommendation

## When To Use Me

Use this skill when a task affects production scoring, model promotion, release gating, operational rollout, or approval readiness.

## Working Rules

- Do not treat missing evidence as implicitly acceptable
- Tie every readiness judgment to concrete artifacts or gaps
- Distinguish merge readiness from production readiness
- Highlight unresolved leakage, reproducibility, or monitoring gaps as blockers

## Output Shape

- Readiness decision
- Evidence reviewed
- Blocking gaps
- Non-blocking conditions
- Required next actions
