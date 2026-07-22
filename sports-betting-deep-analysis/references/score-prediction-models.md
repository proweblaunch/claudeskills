# Score Prediction Models

This is the engine that everything in `market-frameworks.md` reads from. The goal is a full probability matrix (home goals × away goals), not a single predicted score — a single score is almost always the wrong answer even when the model is good, because even the single most likely scoreline in a normal match is usually only 10-15% likely on its own.

## 1. Estimate expected goals (λ) for each team

Build a per-team, per-fixture expected-goals number for both sides, using the context gathered in Phase 2:

- **Baseline attack/defense strength**: each team's goals-for and goals-against rate over a recent window (last 6-10 matches, home/away split), ideally using underlying xG rather than actual goals if available — actual goals over a short window are noisy (a few deflections or a hot goalkeeper skew raw goals data more than they skew shot-quality data).
- **Opponent adjustment**: scale by the opponent's defensive/attacking strength relative to league average — a strong attack facing a strong defense should have its raw scoring average pulled down, and vice versa. This is the core of the classic Poisson approach (team attack strength × opponent defense weakness × home/away adjustment × league average goals).
- **Home/away adjustment**: apply each team's specific home or away scoring/conceding split rather than a flat league-average home advantage.
- **Context adjustments from Phase 2**: injuries to key attackers/defenders, motivation, fatigue, weather, and tactical matchup all nudge λ up or down from the baseline — these are judgment adjustments layered on top of the statistical baseline, not a replacement for it. Be explicit about which adjustments were applied and roughly how large (e.g. "missing starting striker, λ reduced ~15%").

## 2. Build the fulltime score matrix

With λ_home and λ_away estimated, compute a Poisson (or Dixon-Coles adjusted) probability for every realistic scoreline combination (0-0 through roughly 5-5, covers the vast majority of probability mass):

P(home = i, away = j) = Poisson(i; λ_home) × Poisson(j; λ_away)

**Dixon-Coles adjustment**: plain independent Poisson slightly misprices low-scoring draws (0-0, 1-1) and narrow results (1-0, 0-1) — real football has a small negative correlation between the two teams' low scores (both teams being cautious in a 0-0 tends to happen slightly more than pure independence predicts). Apply a small correction that boosts 0-0, 1-1, 1-0, and 0-1 slightly and shrinks the mass elsewhere very slightly, if precision on those specific low scorelines matters for the request (it usually does for correct-score and Both-Halves-Under-1.5-style markets). If doing this by hand/reasoning rather than with a fitted parameter, treat it as a qualitative nudge: acknowledge these cells are somewhat underweighted by plain independent Poisson, rather than needing an exact coefficient.

Normalize the matrix so all cells sum to 1, then read off:
- **1X2**: sum cells where i>j, i=j, i<j
- **Total goals markets**: sum cells by i+j value
- **BTTS**: sum cells where i≥1 and j≥1
- **Correct score**: read individual cells directly, ranked by probability

## 3. Splitting into halftime and second-half distributions

Full-match λ isn't split 50/50 between halves in most leagues/competitions — second halves tend to see more goals (fatigue, tactical adjustments, subs, chasing/protecting a scoreline). Before assuming a split, search for the league or competition's actual first-half/second-half goal-share split if precision matters (it varies by league and season) — a commonly-seen pattern across many leagues is a modest tilt toward the second half (something in the ballpark of 45% first half / 55% second half of total goals), but treat this as a starting assumption to verify per-league rather than a hard constant, and note explicitly in the answer that this is what was assumed.

**Two ways to get a half-specific matrix:**

**A. Independent half model** (use when the request is about a standalone half market, e.g. "2nd Half Multigoals" or a half-specific Over/Under, with no fixed halftime state given):
- Split λ_home and λ_away by the first/second-half share above to get half-specific λ's.
- Build a Poisson matrix the same way as the fulltime one, using the half-specific λ's.
- This gives a standalone "goals scored in this half" distribution, independent of what happens in the other half.

**B. Residual/conditional model** (use when the user gives or the analysis assumes a specific halftime scoreline and wants "given HT is X-Y, what's the 2nd-half/FT score"):
- Take the halftime score as fixed.
- Model the second half using second-half-share λ's (from method A) to get the distribution of *additional* goals each team scores in the second half.
- Convolve: fulltime score = halftime score + second-half-additional-goals distribution. This gives both a second-half-only correct score answer and an implied fulltime correct score conditional on that specific halftime state.

## 4. Presenting correct-score predictions

Never present a single scoreline as "the prediction." Present the top 4-6 scorelines by probability for whichever timeframe was asked (fulltime / halftime / second-half), with their percentage probability, and briefly name the 1-2 factors most responsible for shaping the distribution (e.g. "home side's strong home xG and the away side's injury-depleted defense push the distribution toward home wins by 1-2 goals; low first-half goal-share in this fixture historically keeps 0-0 and 1-0 as the leading halftime states").

If asked for halftime AND fulltime AND second-half together, present all three as their own small ranked lists — don't try to force one artificially "consistent" combined score across all three; it's completely normal and expected for the most likely HT score, most likely 2H score, and most likely FT score to not literally sum together, because each is the single highest-probability outcome from a wide distribution, not a locked-in scoreline.

## 5. Calibration check

Before finalizing, sanity-check the model's implied Over/Under and BTTS numbers against what was gathered in the context phase (does a "mostly Under 2.5" implied output match teams that were flagged as low-scoring/cautious? does the model's home-win-heavy tilt match a team flagged with weak away form?). If the model output contradicts the qualitative picture from Phase 2, that's a signal to revisit the λ estimates rather than to override the model output with a gut call — usually it means an input (an opponent-strength adjustment, a home/away split) was miscalibrated.
