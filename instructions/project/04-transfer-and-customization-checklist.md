# Transfer And Customization Checklist

Use this checklist when copying this standards pack into a new repository.

## Required Before Team Use

- Copy the full pack to the repository root.
- Confirm `AGENTS.md` is at the root that `opencode` will start from.
- Confirm `opencode.json` is at the same root as `AGENTS.md`.
- Fill in `instructions/project/01-repository-context.md` with real repo facts.
- Remove or replace any placeholder bracketed entries.
- Verify the listed commands actually work in the target repo.
- Verify the listed paths match the target repo layout.
- Commit the pack so the whole team shares the same defaults.

## Recommended Validation After Transfer

- Start `opencode` from the target repo root and confirm `AGENTS.md` is loaded.
- Confirm the local skills appear in the skill tool.
- Confirm the custom agents appear in `@` autocomplete.
- Run one read-only task with `quant-plan` or `@quant-reviewer`.
- Run one implementation task with `quant-build` or the default `build` agent.
- Check whether the permission prompts match your intended risk tolerance.

## Customize First If These Change By Repo

- target construction and horizon conventions
- timezones and market calendars
- package manager and environment commands
- required baselines and validation evidence
- data sensitivity rules
- release and sign-off requirements
- allowed or restricted external tools

## Do Not Customize Unless You Have A Clear Reason

- the core operating principles
- the default distinction between always-on rules and on-demand skills
- the separation of review roles from implementation roles
- the conservative stance on leakage, validation, and evidence claims
