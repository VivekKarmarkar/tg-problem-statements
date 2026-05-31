# Problem Statement — acad-paper-api

## Context

Getting a research paper is notoriously tricky: many journal websites have paywalls. Workarounds that already work for a human-in-the-loop:

- arXiv (if the paper is there, easy)
- Sci-Hub (the de facto fallback — works, has been working reliably for years)

The current AI-agent solution is the `paper-download-hack` skill, which mirrors the human workflow: tries arXiv, falls back to Sci-Hub, uses Playwright MCP and browser automation. It works but is **not clean and not programmatic** — it's a hack.

What's wanted instead: a programmatic, reliable, agent-native way for Claude Code to fetch any paper by name/DOI, without browser automation.

**"Reliable" is load-bearing** here. It means:
- A solution validated by the community (not just by me — I haven't used it).
- Signals of community trust: GitHub stars, reviews, repeated use by other projects, etc.
- Functionally at least as good as Sci-Hub (which has been working for 4–5 years as a manual + scripted fallback).
- An **API definitely exists** at the database / service layer. An MCP may or may not exist.
- One-shot fetch: make the request, get the paper, no polling, no waiting loops. Backgroundable.

## 1. Does the solution exist?

This is the **gating question** for this problem statement.

- If **NO** (no community-vouched, reliable, API-exposing paper service exists) → `/goal` quits with that finding. Don't build anything.
- If **YES** → proceed to phases below.

## 2. Sub-problem decomposition (phases)

### Phase A — Discovery
Identify the candidate service(s). For each, gather: API documentation, auth requirements, rate limits, coverage (does it actually have the paper of interest?), community signals (stars, reviews, real-world usage).

### Phase B — Access
Connect to the chosen service via its API.
- If credentials are required, **stop and ask Vivek** — they need to be supplied manually, not assumed.
- Verify with a small probe request before any larger work.

### Phase C — MCP layer
- If an MCP server for this service **already exists**: install/configure it, validate it works in Claude Code.
- If **no MCP exists**: build one wrapping the API so an AI agent can call it cleanly. (The whole point is that future agent calls are one-shot tool calls, not browser dances.)

### Phase D — End-to-end test
Use the new pipeline to actually download the target paper:
> **Target paper:** *Tactile Elastography* (2025)

Confirm the PDF lands on disk and is readable.

## 3. Clear deliverables

- A YES/NO answer to "does the solution exist?" — with the reasoning and the community signals that support it.
- If YES:
  - Identified service + API documentation pointer.
  - Working MCP (existing or newly built) registered with Claude Code.
  - The *Tactile Elastography* (2025) PDF, fetched programmatically (no Playwright, no Sci-Hub fallback for this run).
  - A short note on how this compares to `paper-download-hack` — what it replaces, what it complements, whether the hack can be retired.

