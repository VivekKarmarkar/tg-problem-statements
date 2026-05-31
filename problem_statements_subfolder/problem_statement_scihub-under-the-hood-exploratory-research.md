# Problem Statement — scihub-under-the-hood-exploratory-research

## Context

Getting academic research papers is notoriously difficult. Sci-Hub is the go-to for me as a human — I've been using it for 4–5 years: go to it, put my paper in, download it, mostly I get it.

For an AI agent, we currently have the `paper-download-hack` skill, which reflects what I do manually — arXiv + Sci-Hub (via browser automation).

The question this problem statement explores: **is there a way to get at Sci-Hub programmatically?** Hypothesis: maybe Sci-Hub has a database, and the Sci-Hub website is just a thin wrapper that connects to that database, runs a query, and lets you download. If so, that database might be reachable directly.

## 1. Does the solution exist?

Three sequential gates. If any gate fails, `/goal` quits.

### Gate 1 — Internals exposed?
Use the **swarm** skill to go and figure out if there is any official Sci-Hub documentation or reference that tells you how to connect to Sci-Hub's database, or if there's any window into what Sci-Hub does under the hood — a GitHub repository, a website about this, anything.

- If **nothing found** → `/goal` quits: "no internal data exposed."
- If **something found** (frameworks officially affiliated with Sci-Hub that tell you how to connect to the database, or otherwise give a window in) → proceed to Gate 2.

### Gate 2 — Clear connection method?
For each critical framework found, use the **niche-library-research** skill to figure out how to connect.

- If **no clear method to connect** → `/goal` quits: no solution.
- If a clear connection method exists → proceed to Gate 3.

### Gate 3 — Reliable?
"Reliable" is **load-bearing**. It means:
- I haven't tried it.
- The community has vouched for it: reviews, clear signal of community use.

- If **nothing reliable** → `/goal` quits.
- If there is a reliable solution → proceed.

## 2. Sub-problem decomposition (phases)

### Phase A — Establish connection
Figure out what they expose and how to establish a connection to the database.

### Phase B — MCP connector
Get some kind of MCP connector for this.
- Figure out if one already exists.
- If it exists, check if it is reliable.
- If it doesn't exist (or isn't reliable), build it.

### Phase C — End-to-end test
Extract the *Tactile Elastography* (2025) paper using this method.

## 3. Clear deliverables

- Outcome from each of the three gates (with reasoning + evidence at the gate that fired).
- If all gates pass:
  - Identification of what Sci-Hub exposes and how to connect.
  - An MCP connector (existing or newly built) registered with Claude Code.
  - The *Tactile Elastography* (2025) paper extracted via this method.
