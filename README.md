# tg-problem-statements

A staging ground for problem statements captured via Telegram voice notes and dispatched to autonomous AI agents via the `/goal` slash command.

## Overview

This repo is the *capture-and-stage* layer of a personal voice-driven agent workflow. Multiple problem statements — one per target repo — are dictated in a single Telegram voice session, transcribed, decomposed into agent-actionable phases, and stored here as markdown. From there each statement is copied into its respective project repo in remote-control mode and fired off with `/goal`.

It is not a library, not a tool, not code. It's a structured notebook for autonomous-agent task specifications.

## Workflow

1. **Capture** — dictate multiple problem statements in one Telegram voice session.
2. **Decompose** — write each statement using the anatomy in `problem_statement_general_anatomy.md` so phases (one or more sub-problems each) can be autonomously executed.
3. **Distribute** — copy each problem statement to its target repo in remote-control mode.
4. **Execute** — fire `/goal` in the target repo to launch the autonomous agent.

See `workflow.md` for the source description.

## Files

- **`list_of_problem_statements.md`** — registry of problem-statement slugs (one per target repo / skill).
- **`problem_statement_general_anatomy.md`** — the schema every problem statement should follow:
  1. Does the solution exist?
  2. Sub-problem decomposition
  3. Clear deliverables
  4. Email final result if possible
- **`workflow.md`** — one-paragraph description of the capture → distribute → `/goal` pipeline.

## Adding a Problem Statement

1. Add the slug to `list_of_problem_statements.md`.
2. Create `<slug>.md` in the repo root (e.g. via `/new-md`).
3. Populate it against the four anatomy items, ensuring sub-problem decomposition is phase-friendly for `/goal`.

## License

No license declared.
