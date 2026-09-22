# EDGE v2 — Workflow

This file defines what the agent should do when working with the EDGE v2 Lab experiment.

## Before any analysis

Always read:

1. `README.md`
2. `RULES.md`
3. `TRACKER.md`
4. `RESEARCH.md`
5. all existing files in `/bets`

The repository is the source of truth for the experiment.

`RESEARCH.md` contains external models, research ideas, and possible future improvements. Treat it as additional context and independent evidence only. It does **not** modify the current experiment rules or create new selection criteria during the initial 10-bet sample.

Do not change the methodology because of a single result.

---

## Morning workflow

Scan today's CS2 schedule.

Priority:

- Tier 1
- strong Tier 2

Avoid low-information / low-tier matches unless there is an exceptional reason to investigate them.

Do not start by asking the user for all STS odds.

### Step 1 — Independent market scan

First analyze potentially relevant matches independently of STS prices.

Verify where possible:

- event and match format
- confirmed rosters
- stand-ins / substitutions
- recent form
- quality of recent opponents
- map pool
- matchup characteristics
- likely or confirmed veto
- sample size and reliability of map statistics
- relevant recent H2H without overweighting it

Never invent missing data.

If important information cannot be verified, explicitly treat it as uncertainty.

Public models or tools documented in `RESEARCH.md` may be consulted as supplementary evidence when relevant. Their output must not be treated as ground truth and must not replace independent matchup analysis.

### Step 2 — Candidate selection

Select only matches where there is a plausible reason the market could be mispriced.

If nothing looks sufficiently interesting:

`NO CANDIDATE`

Do not manufacture a bet.

If a match looks interesting, tell the user exactly which STS prices are needed.

Example:

> Potential spot: MOUZ–NAVI.
> Please provide STS:
> - ML
> - Over 2.5 maps
> - M2 ML

Only request markets relevant to the thesis.

---

## Pre-match re-check

For relevant matches, perform a final re-check approximately **20–30 minutes before scheduled start** when practical.

The purpose is to catch information that may not have been available during the morning scan.

Re-check where possible:

- roster / stand-in changes
- confirmed or newly available veto information
- map-related information
- significant public market movement
- other material information affecting the original thesis

If confirmed veto becomes available, reassess the original matchup thesis and probability estimate before making or confirming a decision.

Do not create a candidate merely because odds moved.

---

## After receiving STS odds

For each candidate calculate or estimate:

- win probability (`p`)
- fair odds (`1 / p`)
- STS break-even probability
- estimated edge
- confidence in the estimate
- main risks / uncertainty

Compare the independent analysis with the actual STS price.

Use public bookmaker prices, when reliably available, as market context. They are not a substitute for the actual STS price used for the decision.

Then make one decision:

`BET`

or

`PASS`

A correct prediction is not automatically a good bet.

A PASS does not count toward the 10-bet experiment.

---

## When a BET is confirmed

Assign the next experiment number:

`#1/10` through `#10/10`

Create:

`bets/XX_TEAM-A_vs_TEAM-B.md`

The pre-match record must contain:

- experiment number
- date
- event
- format
- matchup
- market
- STS entry odds
- estimated probability
- fair odds
- break-even probability
- estimated edge
- confidence
- thesis
- main risks

### Freeze the pre-match snapshot

Once the bet is confirmed, the original pre-match analysis is frozen.

Never rewrite the original:

- probability
- fair odds
- confidence
- thesis
- risks

after seeing the match result or live action.

Provide the completed `.md` file to the user so it can be added to the repository.

---

## Live matches

Do not chase losses.

Do not add exposure merely because the original bet is losing.

A live market can only become a new candidate if it independently satisfies the same value process.

Live score or momentum alone is not sufficient evidence of value.

Research into dedicated live models belongs in `RESEARCH.md` and does not change the current live-betting rules during the initial experiment.

---

## After the match

Add a separate post-match section containing:

- result
- closing odds, if available
- CLV, if available
- P/L
- short post-match evaluation

Evaluate the quality of the original decision independently from whether the bet won or lost.

A winning bet can be a bad decision.

A losing bet can be a good decision.

Do not create a new methodology rule from one match.

Update `TRACKER.md`.

Provide the updated bet file and tracker to the user so they can be added to the repository.

---

## Experiment state

Only confirmed BET decisions count toward the sample.

PASS decisions do not count.

The experiment starts at:

`0/10`

and ends after:

`10/10`

---

## After bet #10

Stop the initial experiment.

Do not add bet #11 before reviewing the first batch.

Review:

- W/L
- P/L and ROI
- average entry odds
- CLV
- probability calibration
- estimated edge vs actual outcomes
- performance by market type
- quality of data
- quality of reasoning
- repeated analytical errors
- good results produced by weak reasoning
- bad results produced by sound reasoning
- research ideas collected in `RESEARCH.md`

Only after the complete review should changes to the methodology be proposed.

The purpose of the first 10 bets is not to prove profitability.

The purpose is to determine whether EDGE v2 shows enough evidence of identifying mispriced probabilities to justify further testing.
