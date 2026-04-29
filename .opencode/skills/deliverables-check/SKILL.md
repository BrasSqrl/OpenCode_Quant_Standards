---
name: deliverables-check
description: Determine the minimum review and validation artifacts required for a given quantitative engineering or model change
license: MIT
compatibility: opencode
metadata:
  audience: quant-teams
  workflow: governance
---

## What I Do

- Map a task to the minimum required artifacts and checks
- Identify whether the change is implementation-only, methodological, data-related, evaluation-related, or production-impacting
- Identify when a model methodology task requires DOCX output, evidence index, image inventory, and Quant run traceability
- Highlight what evidence is present and what is still missing
- Keep the artifact list practical and decision-oriented

## When To Use Me

Use this skill when deciding what documentation, tests, validation notes, or sign-off evidence a change must include.

## Working Rules

- Start by classifying the change type
- If multiple change types apply, combine their requirements
- For methodology documentation, require the approved DOCX deliverable unless the user or repo context explicitly allows another format.
- For methodology documentation using Quant sister project outputs, require the selected run ID, source artifact paths, and image-handling evidence.
- Separate required artifacts from nice-to-have artifacts
- Escalate missing artifacts that block merge, promotion, or approval decisions

## Output Shape

- Change classification
- Required artifacts
- Present artifacts
- Missing artifacts
- Release or review impact
