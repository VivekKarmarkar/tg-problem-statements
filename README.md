# tg-problem-statements

A staging ground for problems captured via Telegram voice notes — sorted into ones that can be dispatched autonomously via `/goal` and ones that are better worked through conversationally.

## Overview

This repo is the *capture-and-stage* layer of a personal voice-driven agent workflow. Multiple problems — one per target repo — are dictated in a single Telegram voice session, transcribed, and sorted by *mode*: either packaged as a clean problem statement that can be fired autonomously with `/goal`, or treated as an exploratory discussion better resolved by talking it through.

It is not a library, not a tool, not code. It's a structured notebook for organizing problems before agentic work begins.

## Workflow

1. **Capture** — dictate one or more problems in a Telegram voice session connected to a Claude Code session.
2. **Sort** — classify each problem by execution mode: `statement` (autonomous) or `discussion` (conversational).
3. **Statements**: decompose using the schema in `problem_statement_general_anatomy.md`, then later copy to the target repo and fire `/goal`.
4. **Discussions**: talk it through here in real time; write the final conclusion into `problem_discussion_subfolder/` once it settles.

See `workflow.md` for the original capture-pipeline description.

## Why this architecture (the Amdahl story)

The single-Telegram-session, batch-then-distribute design is intentional, not a workaround. It's the architecture that minimizes the *human-serial bottleneck* in solo-operator + AI workflows. The full reasoning lives in `problem_discussion_subfolder/multiple-tg-channels-at-once_story.pdf` (story version) and `problem_discussion_subfolder/problem_discussion_multiple-tg-channels-at-once.md` (technical version). Short form: parallel-execution doesn't need voice; voice-dictation is serial through one brain anyway; multi-channel Telegram solves nothing and adds session-switching overhead. The only structural gap vs. an idealized future is one file copy per problem.

## Files

### At the root

- **`list_of_problems.md`** — registry of all problems being tracked. One slug per line. The corresponding file in either subfolder is what determines its execution mode.
- **`problem_statement_general_anatomy.md`** — the schema every statement-mode problem should follow:
  1. Does the solution exist?
  2. Sub-problem decomposition
  3. Clear deliverables
  4. Email final result if possible
- **`workflow.md`** — one-paragraph capture-pipeline description.
- **`next_steps.md`** — externalized memory of what to do after this session is wrapped (so it doesn't have to live in your head between sessions).

### Subfolders

- **`problem_statements_subfolder/`** — `problem_statement_<slug>.md` files for problems amenable to clean autonomous packaging. These are agent-actionable specs.
- **`problem_discussion_subfolder/`** — `problem_discussion_<slug>.md` files for exploratory/conversational problems. May include accompanying artifacts (story PDFs, audio narrations) summarizing the discussion outcome.

## Adding a problem

1. Add the slug to `list_of_problems.md`.
2. Decide its mode. Create either `problem_statements_subfolder/problem_statement_<slug>.md` or `problem_discussion_subfolder/problem_discussion_<slug>.md`.
3. For statements: populate against the four anatomy items. Sub-problems should be phase-decomposed so `/goal` can execute them.
4. For discussions: leave the file empty until the conversation settles, then write the final conclusion in.

## Conventions

- Slug naming is kebab-case (`acad-paper-api`, not `acad_paper_api`).
- The numbered position in the registry is *display only*; the slug is the canonical identity. External references should cite slugs, not numbers.
- The registry shrinks as problems are resolved — captured statements stay, finished discussions stay as historical record, dropped problems leave entirely.

## Stay-in-domain discipline

The hardest cognitive bottleneck in this workflow is domain-switching during dictation. Same-domain problems flow well in one session; cross-domain hops stall hard. Batch problems by domain, run one session per cluster.

## .gitignore

Generated audio artifacts (`*.mp3`, `*.wav`, `*.ogg`) are ignored — they're large and easily regenerated from their narrative source files.

## License

No license declared.
