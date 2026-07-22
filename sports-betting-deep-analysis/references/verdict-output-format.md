# Verdict & Output Format

How to present the analysis once Phases 1-4 are done. The right format depends on what was asked for.

## Slip review (multi-leg accumulator/booking-code analysis)

Use a per-leg verdict of **Keep / Moderate Risk / Remove**, each backed by the model probability vs. market-implied probability gap and the one or two deciding context factors. If the user is working in a chat surface that supports interactive widgets (the Visualizer / HTML artifact), a color-coded card layout per leg (green/amber/red) with the match, market, model probability, and a one-line reason reads faster than a long prose table for a 20-50 leg slip — build it that way when the surface supports it; otherwise a structured markdown table (Match | Market | Model % | Market % | Verdict | Reason) works as plain text.

Close a slip review with a portfolio-level summary: combined probability of the full slip (or of a sub-set if some legs are flagged Remove), and a callout of the weakest-link legs per the portfolio-risk notes in `market-frameworks.md`.

## Correct-score requests (fulltime / halftime / second-half)

Present as a ranked list or small table per timeframe requested:

| Scoreline | Probability |
|---|---|
| 1-0 | 14% |
| 1-1 | 12% |
| 2-0 | 11% |
| ... | ... |

Follow each table with 1-2 sentences on what's driving that distribution (see Phase 4/5 of the main SKILL.md and section 4 of `score-prediction-models.md`). If halftime, second-half, and fulltime are all requested, give three such tables, clearly labeled, and don't force them to look "consistent" with each other beyond what the model actually implies.

## General factor/analysis questions (not tied to a specific slip)

When the user is asking conceptually "what factors should I check" rather than requesting a specific match analysis, walk through the relevant sections of `match-context-factors.md` and `market-frameworks.md` directly in prose/checklist form — no need to force a verdict-card format onto a conceptual answer.

## Always disclose assumptions

Whatever the output format, state plainly: the data window used for form, whether injury/team-news was confirmed close to kickoff or estimated, which first-half/second-half goal split assumption was used, and the overall confidence level of the fixture (some matches — dead rubbers, heavily rotated sides, teams with very little recent data — deserve an explicit "lower confidence than usual" flag rather than being presented with the same certainty as a well-supported analysis).
