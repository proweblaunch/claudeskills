# Market Frameworks

Each section below is a checklist for translating the Phase 1-3 context and score matrix (see `score-prediction-models.md`) into a verdict for that specific market. Run the relevant section(s) for whatever markets appear on the slip.

## 1X2 (Home / Draw / Away)
- Read the three probabilities straight off the score matrix (sum the cells where home-goals > away-goals, =, <).
- Compare to bookmaker implied probability (1/odds, then normalize the three implied probabilities to remove the overround/margin) — the gap is the edge.
- Sense-check against motivation/context: a mathematically "correct" favorite can still be a trap in a dead-rubber or rotation scenario.

## Double Chance (1X, X2, 12) and "Home or Away" (12)
- Sum the relevant pair of 1X2 probabilities.
- This market is a volatility-reduction play — it's most useful specifically when the draw probability is meaningfully high (cagey matchup, evenly matched sides) or when hedging against a single specific outcome. If the model gives one side a dominant single-outcome probability already >75-80%, Double Chance adds little extra safety over a straight 1X2/Handicap bet, so flag that as a "low value-add" note even if it will likely win.

## BTTS / GG-NG (Both Teams to Score)
- Sum score-matrix cells where both home-goals ≥1 and away-goals ≥1 for GG; the complement for NG.
- Key drivers: both teams' scoring rate AND both teams' clean-sheet rate — a team can have a high scoring rate but the BTTS answer depends equally on the opponent's defense.
- Watch for one very weak attack (low goals-for average) even against a leaky defense — that alone can flip BTTS from "likely" to "coinflip."

## Over/Under Goals (full match and half-specific)
- Sum score-matrix cells where total goals > or < the line.
- For half-specific Over/Under (e.g. "Nottingham Over/Under" style 2nd-half-only lines), use the half-specific matrix from `score-prediction-models.md`, not the full-match matrix scaled by a flat ratio — first and second halves have systematically different scoring rates (most leagues score more in the 2nd half; fatigue, tactical adjustments, and desperation goals late).
- Check pace-of-game context (tactical matchup, weather, stakes) as a sanity check against the raw average.

## Both Halves Under 1.5 (goals in each half separately under 1.5)
- Requires BOTH the 1st-half matrix and 2nd-half matrix to each independently show <1.5 goals — this is a compound condition, not a single-matrix read. Compute each half's Under 1.5 probability separately, and note this is NOT the same as full-match Under 3.5 (a 2-2 first half / 0-0 second half fails Both Halves Under 1.5 despite being a low-scoring-looking overall pattern... actually a 3-goal full match could easily fail this market if the goals cluster in one half).
- This market is essentially a "low chaos in both periods" bet — teams with genuinely low pace throughout (not just a low full-match average driven by one dominant half) are the safest picks.

## Multigoals (goal range brackets, e.g. "1-3" markets, including 2nd Half Multigoals)
- Sum score-matrix cells (or half-specific matrix cells) falling inside the stated range.
- These are naturally wide brackets (e.g. 1-3 goals covers a lot of realistic outcomes) so they often carry short odds — the checklist question is whether the *tails* are being underpriced: a genuinely high-pace or genuinely dead-rubber/defensive fixture can push real probability toward the excluded 0 or 4+ ends more than the short odds imply.
- For 2nd-half-specific multigoals, tactical-context factors matter more than in a full-match view: substitutions, chasing/protecting a scoreline, and fatigue all disproportionately affect the second 45 minutes — factor in what the likely halftime state will be and how each side tends to play from a leading/trailing/level position.

## Asian Handicap (AH)
- Adjust the score matrix by the handicap line, then sum probabilities for the adjusted-win / push / adjusted-loss outcomes (quarter lines split the stake across two half-lines — calculate each half separately).
- AH is a refined 1X2 — the checklist is the same fundamentals as 1X2 but the question shifts from "who wins" to "by how much," which makes squad depth, game-state tactics (does the favorite keep attacking once ahead, or sit back?), and motivation to run up the score (relevant in must-score-differential scenarios, e.g. group-stage qualification) much more decisive than in a simple win/draw/lose read.

## Asian Total / Asian Over-Under
- Same mechanic as AH but applied to the total-goals line instead of the result line — use the full-match (or half-specific, if it's a half AH total) goal matrix.
- Quarter-lines again split into two calculations — don't skip this, quarter Asian lines are common and a single-line calculation will misprice them.

## European (fixed) Handicap
- Apply the handicap to each scoreline in the matrix before re-deriving 1X2 (unlike Asian Handicap, this keeps the draw as a live, separate outcome after adjustment) — sum accordingly for the three adjusted outcomes.

## Goal Bounds (over X / under Y bracketed total-goals markets)
- Same sum-the-matrix-cells method as Multigoals; treat any exotic "X or more goals" wording carefully — confirm inclusive/exclusive boundaries before computing (is exactly the boundary number included in "over" or not).

## Corners and cards markets
- These aren't derivable from the goal-based score matrix — they need their own inputs: each team's average corners/cards for and against, referee card average (see context file), tactical style (wide-attacking teams generate more corners; low-block defensive teams concede more), and game-state effects (a team chasing a goal late tends to generate a flurry of corners).
- Build a simple expected-count model (team A's for-average blended with team B's against-average, adjusted for referee/context) the same way as goals, rather than reading off the score matrix.

## Combo / same-game and cross-game accumulator legs
- **Same-game combos**: check correlation before treating combined odds as independent. A same-game "Home Win + Over 2.5 + BTTS" combo is more correlated than the raw multiplied odds imply if the home team's most likely winning scorelines already involve high goals — the true combined probability can be meaningfully higher (or lower, for negatively correlated legs like "Under 1.5 + BTTS") than naive multiplication suggests. Where possible, read the exact combined probability directly off the joint score matrix rather than multiplying individual market probabilities.
- **Cross-game accumulators** (the large 20-50+ leg slips): legs across different matches are independent of each other, so combined probability is the product of each leg's model probability — but the *practical* risk isn't just that product. Two things matter beyond raw math:
  1. **Weakest-link sensitivity**: one leg at 60% confidence inside a slip of otherwise-90%+ legs disproportionately drives the whole slip's failure risk — flag and consider removing/hedging outlier-low-confidence legs before staking, since a 50-leg accumulator's win probability is brutally sensitive to its worst legs, not its average leg.
  2. **Model-uncertainty correlation**: if the *same kind* of context risk appears across multiple legs (e.g. several legs rely on weather forecasts, or several rely on unconfirmed team news for the same league on the same weekend), those legs aren't statistically correlated in outcome but are correlated in *analysis risk* — a bad information source infecting several legs at once. Note this as a portfolio-level flag, distinct from in-game correlation.
- For staking/coverage math across multiple slip variants (wheels/system bets), treat it as a combinatorics problem: check whether the exclusion/rotation pattern used to build multiple slip variants actually gives even coverage across outcome combinations, or whether it structurally favors/ignores certain combinations (as identified in prior wheel analysis) — a lopsided rotation pattern quietly changes the effective odds of the whole system versus its advertised coverage.

## Turning market probability into a verdict
For every leg: state the model probability, the bookmaker implied probability (margin-adjusted), and the gap. A leg where the model agrees closely with the market is "priced correctly" — not necessarily bad, just not where the edge is. Flag as high-risk any leg where market and model *disagree in a way that favors the bookmaker* (i.e. the market thinks it's less likely than your model does — that's a signal your inputs may be missing something the market knows, not necessarily an edge in your favor). Flag as a genuine value candidate only when the disagreement is well-explained by a specific factor from the context phase, not just "the model says so."
