---
name: feature-contract
description: Review or draft feature and dataset contracts covering schemas, keys, units, null behavior, timestamps, and point-in-time assumptions
license: MIT
compatibility: opencode
metadata:
  audience: quant-teams
  workflow: data
---

## What I Do

- Turn implicit feature assumptions into explicit contracts
- Check keys, uniqueness rules, dtypes, units, allowed nulls, timestamp semantics, and publication timing
- Make downstream model dependencies and failure modes visible
- Recommend tests and validation checks that enforce the contract

## When To Use Me

Use this skill when creating or changing training tables, feature pipelines, dataset schemas, or feature definitions that multiple teams will rely on.

## Working Rules

- Prefer exact field-level statements over vague descriptions
- Distinguish observation time, effective time, and publish time
- State uniqueness expectations for entity and timestamp keys
- Call out contract changes that require downstream reruns or backfills

## Output Shape

- Contract summary
- Required columns and semantics
- Key and uniqueness rules
- Timestamp and point-in-time rules
- Null, range, and dtype expectations
- Required tests and downstream implications
