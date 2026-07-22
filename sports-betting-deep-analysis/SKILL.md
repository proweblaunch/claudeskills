---
name: sports-betting-deep-analysis
description: Deep research and analysis framework for predicting football (soccer) betting outcomes across every major market — 1X2, Double Chance, BTTS/GG-NG, Over/Under (full match, half-specific, Both Halves Under 1.5), Asian Handicap, Asian Total, European Handicap, Multigoals, Goal Bounds, Corners, and combo/accumulator slips — plus correct-score prediction for fulltime, halftime, and second-half-only outcomes. Use this skill whenever the user pastes or describes a betting slip/booking code, asks "what are the chances", "predict the score", "is this selection safe", "analyze this accumulator", wants a per-match verdict (keep/remove/risk), or asks about factors that affect a football match outcome — even if they don't say the word "skill" or "betting" explicitly. Always trigger for multi-selection slips (SportyBet, Bet9ja, 1xBet, Betway or similar booking codes/screenshots) and for any request involving correct score, halftime score, or second-half score prediction.
---

# Sports Betting Deep Analysis

## Mission

Go past "check the form table and pick a favorite." This skill exists to replicate what a professional trading/analyst desk does before pricing a match: pull every available signal, run it through a proper scoring model, and only then translate probabilities into a betting verdict. The output should be defensible with numbers, not vibes — every "Keep" or "Remove" call should trace back to a specific factor or a specific probability gap between the model and the bookmaker's price.

This skill is built for exactly the kind of work the user does: large multi-selection accumulators (often 20-50+ legs) mixing markets like 2nd Half Multigoals, Both Halves Under 1.5, Double Chance, Over/Under, and 1X2, submitted for per-leg research before staking.

## Core workflow

Work through these phases in order. Don't skip to scoring/verdicts without doing the data-gathering phase — a model built on stale or assumed inputs produces a confident-looking wrong answer, which is worse than no model.

### Phase 1 — Parse the slip
If the user pastes a screenshot or booking code, extract every leg: teams, market, selection, odds, and kickoff date/time. Group legs by market type so the same analytical lens gets applied consistently (all Over/Under legs together, all Double Chance legs together, etc.) — see `references/market-frameworks.md` for the per-market checklist to run on each group.

### Phase 2 — Gather match context
For each fixture, work through `references/match-context-factors.md`. This is the fact-finding layer: form, injuries, motivation, schedule congestion, tactical matchup, referee, and odds movement. Use web_search for anything not already known — team news changes daily and this skill is worthless if it runs on stale priors. Search each fixture individually rather than batching; a combined query returns shallow results for all of them.

### Phase 3 — Build the score model
Once context is gathered, convert it into expected goals (xG-based or Poisson) for both teams and build a fulltime score probability matrix. `references/score-prediction-models.md` has the full method, including how to derive halftime-only and second-half-only score distributions from the same model — this is what most casual analysis skips, and it's exactly what's needed for markets like "2nd Half Multigoals" or "Nottingham Over/Under" (half-specific goal markets).

### Phase 4 — Score every market against the model
Run the matrix through each market the user is asking about (BTTS, AH, O/U, Multigoals, Handicap, Goal Bounds, Corners, combos). `references/market-frameworks.md` has the checklist and the math for translating a score matrix into a market probability for each of these. Compare the model probability to the implied probability of the bookmaker's odds (1/odds, adjusted for margin) — that gap is where the edge or the danger lives.

### Phase 5 — Verdict and output
Turn the analysis into a decision per leg (and, if it's an accumulator, a decision on the slip as a whole — see the portfolio-risk section of `references/market-frameworks.md` for how correlated legs multiply risk beyond the sum of their odds). Use `references/verdict-output-format.md` for how to present this: color-coded verdict cards for a slip review, and structured score-probability tables for a correct-score prediction request.

## When the ask is specifically "predict the correct score"

Don't return a single score. Return the top 4-6 most probable scorelines with their model probability, split by whichever timeframe was asked for:
- **Fulltime correct score** — full match Poisson/Dixon-Coles matrix
- **Halftime correct score** — same matrix scaled to first-half-only expected goals (first-half goal share is lower than 50% in most leagues — use league-specific first/second half goal splits, don't assume an even 45/55 default without checking)
- **Second-half correct score** — either modeled independently with second-half xG, or derived as the residual distribution once a halftime scoreline is fixed (both methods are in `references/score-prediction-models.md`; use the residual method when the user gives/assumes a specific HT score, the independent method when they want a standalone 2nd-half market like "2nd Half Multigoals")

Always state the assumptions the model rests on (which xG/form window, whether injuries were confirmed or reported, referee card average used) — a score prediction without visible assumptions is not analysis, it's a guess with a probability attached.

## A note on rigor vs. false precision

Football is high-variance; a well-built model still gets the scoreline wrong most of the time — that's expected, not a model failure. The value of this process is in identifying where the model and the market disagree, and being honest about confidence (wide vs. narrow probability spread across scorelines, strength of the underlying data). Flag low-confidence legs as low-confidence rather than smoothing them into a false "safe" verdict — that's the difference between analysis and marketing copy for a bet.
