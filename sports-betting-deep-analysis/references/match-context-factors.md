# Match Context Factors

Everything downstream (the score model, the market verdicts) is only as good as this layer. Work through these for every fixture before touching a model. Use web_search per fixture — don't rely on training-data memory of team strength, since squads, form, and injuries change constantly.

## 1. Form — but the right kind of form
- Last 5-6 matches result *and* underlying performance (xG for/against, shots, big chances) — a team can be "in form" on results while getting outplayed, which reverses soon. Prioritize xG-based form over results-based form when available.
- Split home form and away form separately — a team's overall form table position hides large home/away splits that matter more for 1X2, Handicap, and Asian Handicap markets.
- Form *in the specific market context*: e.g. for Over/Under research, look at the team's actual goals-for/against trend and BTTS rate over the last 6-8 games, not just win/loss.
- Recency-weight: a heavy loss 6 games ago matters less than a heavy loss last week — but check *why* a result happened (see "context of results" below) before weighting it.

## 2. Head-to-head (H2H)
- Last 5-6 meetings, but discount H2H heavily if the squads/managers have changed significantly since — stale H2H is a common analysis trap.
- Look for structural patterns that recur regardless of squad changes: does this fixture tend to be cagey/low-scoring (derbies, relegation six-pointers) or open (contrasting playing styles)? That structural pattern is more durable than "team A beat team B last time."

## 3. Injuries, suspensions, and squad news
- Confirm via official team news / press conference reports as close to kickoff as available — not stale reports from days earlier.
- Weight by positional importance: a missing first-choice striker or starting goalkeeper matters far more to a score model than a squad rotation player.
- Check for suspensions from accumulated cards, not just injuries — easy to miss.
- International duty / long-haul travel returns: players just back from international travel carry fatigue risk, especially for the following weekend's fixture.

## 4. Motivation and context of the match
- League position and what's at stake: title race, European qualification push, relegation battle, mid-table "nothing to play for" dead rubber. Motivation mismatches (one team fighting for survival, the other with nothing to play for) are one of the strongest predictors of surprising results.
- Cup competition context: is this a replay, a two-legged tie where a team is already through/out, or a game before/after a bigger fixture (managers sometimes rotate heavily before/after a Champions League leg)?
- Rivalry/derby intensity: tends to suppress expected goals and inflate card counts versus a "normal" fixture between the same quality of teams.
- End-of-season dead rubbers: sharply reduce reliability of all models — flag these explicitly as low-confidence.

## 5. Schedule congestion and fixture fatigue
- Days of rest since last match for both sides — 3 days between matches is materially different from 6-7.
- Number of matches played in the last 2-3 weeks (congested fixture list from cup runs, continental competition, rescheduled games).
- Upcoming fixture list: a team may field a weakened side knowing a bigger match is 3-4 days later.

## 6. Tactical matchup
- Playing styles: high press vs. possession-based, direct/counter vs. build-from-the-back — certain style matchups produce more chaos (and goals) than others regardless of raw team quality.
- Set-piece dependency: a team that scores heavily from set pieces changes the calculus for BTTS/Over-Under against a weak set-piece defense.
- Expected approach given the scoreline stakes (a team needing a win by 2+ goals plays differently than one happy with a draw) — relevant for 2nd-half and late-goal markets specifically.

## 7. Referee tendencies
- Average cards per game and penalty award rate for the assigned referee — relevant for card/corner-adjacent markets and can indirectly affect goal expectancy (more stoppages, more set pieces).
- Consistency of officiating style with the two teams' playing styles (a strict referee against a team that relies on physical pressing can suppress their effectiveness).

## 8. Weather and pitch conditions
- Heavy rain, wind, extreme heat, or a poor pitch surface generally suppress total goals and technical/possession-based play — check forecast for the kickoff window, not just the day.
- Altitude for away teams unaccustomed to it (South America especially) is a real, measurable fatigue factor.

## 9. Home/away and travel-specific splits
- True home advantage varies hugely by league/team — some teams have a much stronger home xG differential than their away form suggests, and vice versa.
- Travel distance/time zones for the away side, especially for continental fixtures.
- Neutral-venue matches remove home advantage entirely — don't apply a home-team model boost.

## 10. Market signal — odds movement and liquidity
- Compare the current odds to the opening line. Significant steam toward one outcome (beyond what public-money bias would explain) is a real signal that professional money has moved — search for line-movement commentary or compare odds across a couple of books if possible.
- Be skeptical of odds on obscure lower-league/lower-liquidity fixtures — wider margins and less efficient pricing means the "market signal" is weaker and your own model should be weighted more heavily relative to the odds.
- Note: line movement is a supporting signal, not a replacement for the fundamental analysis above — public betting can move lines on popular teams without any real informational edge behind it.

## Assembling the picture
For each fixture, this phase should leave you able to state, in a sentence or two per team: current attacking output, current defensive output, who's missing and how much it matters, what's at stake, and whether conditions/schedule cut against normal form. That's the input to the score model in `references/score-prediction-models.md`.
