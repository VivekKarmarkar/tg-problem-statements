# Hallucination Audit — multiple-tg-channels-at-once podcast narrative

## Sources audited
- `multiple-tg-channels-at-once_story.pdf` (story register, plain narrative)
- `problem_discussion_multiple-tg-channels-at-once.md` (engineering record)

## Journal
- 15 journal entries written to `reconstruction/multi-tg-discussion/find-evidence-in-discussion.md`
- All 15 substantive claims **supported** by verbatim source text in PDF and/or MD.
- 0 contradicted, 0 silent.
- 0 corrections applied between `narrative_refined.md` and `narrative_final.md`.

## Load-bearing claims verified
1. Project purpose (Telegram voice → structured doc)
2. Self-destructing entry framing
3. Three-agent swarm dispatch
4. Silent-listener bug + known bug report
5. shaike1/relay tmux-keys mechanism
6. Custom-rule breakage list (voice, food-photo, WhatsApp)
7. Ongoing vs one-time tax tradeoff
8. Amdahl 1967 attribution
9. Vivek-as-serial-bottleneck reframing
10. Two-phase split (setup serial / execution parallel)
11. "Category error" phrase
12. Ideal-vs-current step-by-step parity
13. **One file copy per problem** = entire structural gap (load-bearing)
14. Architecture is Amdahl-optimal under solo-human constraint
15. Closing operational lesson (one domain per session)

## Judgment calls
- Treated story PDF as primary for tonal register; MD as fact-checker for technical precision (e.g. tmux-send-keys detail behind "pretend to be a human typing").
- Did NOT name shaike1/relay verbatim in the narrative — softened to "a popular community relay project" lineage with "shaike1/relay is the popular one" mentioned once, consistent with both sources.
- Replaced jargon per the Delight Brief: "/goal" rendered as "the command that fires it off to work on its own"; "MCP" not used; "Amdahl's Law" introduced with plain-language gloss before naming.
- Kept "Amdahl's Law" by name because the narrative arc IS the Amdahl reframing — naming it gives the reader a hook, and the gloss makes it accessible.

## Verdict
Narrative is faithful to both source artifacts. No fabricated quotes, no invented details. Safe to ship.
