# EDGE v2 — Workflow

This file defines what the agent should do when working with the EDGE v2 Lab experiment.

## Before any analysis

Always read:

1. `README.md`
2. `RULES.md`
3. `TRACKER.md`
4. `RESEARCH.md`
5. all existing files in `/bets`
6. recent relevant files in `/cases`

The repository is the source of truth for the experiment.

`RESEARCH.md` contains external models, research ideas, and possible future improvements. Treat it as additional context and independent evidence only. It does **not** modify the current experiment rules or create new selection criteria during the initial 10-bet sample.

`/cases` contains detailed histories of meaningful candidates, including PASS decisions and near-miss spots. Case files are observational records and do not count toward the 10-bet experiment.

Do not change the methodology because of a single result.

---

## Morning workflow

Scan today's CS2 schedule.

Priority:

- Tier 1
- strong Tier 2

Avoid low-information / low-tier matches unless there is an exceptional reason to investigate them.

Do not start by asking the user for all STS odds.

The morning scan should be broad enough to show that the relevant market was reviewed, not only the single match eventually selected.

When practical, divide the day into time blocks and analyze the nearest block first, while identifying later windows that require re-checks.

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

If a match looks interesting, identify the specific market thesis before evaluating price.

The agent may independently surface a market not yet mentioned by the user and ask whether that market is available at STS.

Only request markets relevant to the thesis.

---

## Candidate status discipline

Use only the following pre-decision states:

### `SCREEN`

The match is being investigated.

No probability estimate is required.

### `WATCH`

There is a plausible matchup angle, but important evidence is incomplete, weak, contradictory, or not yet verified.

A WATCH must not be described as close to a bet.

### `CANDIDATE`

The independent thesis has passed the evidence verification gate and adversarial check.

The specific market being evaluated is known.

Only at this stage should the relevant STS price be evaluated for the final decision.

### `BET`

The verified thesis plus the STS price produces sufficient estimated edge relative to uncertainty.

### `PASS`

The matchup, evidence, price, or uncertainty does not justify a bet.

Do not use intermediate labels such as:

- near-BET
- almost BET
- likely BET

These labels create commitment before the process is complete.

---

## Required candidate worksheet

Before requesting or evaluating STS odds, record internally:

1. Event and format
2. Roster status
3. Specific market thesis
4. Evidence supporting the thesis
5. Evidence quality: LOW / MEDIUM / HIGH
6. Key statistics with sample sizes
7. Opponent-quality caveat
8. Likely veto implications
9. What would invalidate the thesis
10. Adversarial case

For map totals additionally record:

11. Which map(s) the underdog can realistically win
12. Which map(s) the favorite is expected to win
13. Whether the likely veto can plausibly create both outcomes

If points 11–13 cannot be answered with reasonable confidence, an Over 2.5 maps thesis should normally remain `WATCH` or become `PASS`.

Before labeling a market `CANDIDATE`, the agent should be able to explain the concrete edge mechanism in 2–3 sentences **without referring to the STS price**.

If it cannot do that, the market is not yet a candidate.

---

## Evidence verification gate

Before a `CANDIDATE` status is allowed, verify the critical inputs supporting the thesis.

For map-based reasoning, verify where possible:

- current/relevant roster or core
- source time window
- sample size
- opponent quality
- current map pool
- whether another reliable source materially disagrees

Do not convert unverified map statistics into a numerical probability estimate.

If the key evidence cannot be verified, keep the match at `WATCH` or move it to `PASS`.

---

## Probability sanity check

Before publishing an estimated probability:

- calculate the bookmaker break-even probability
- compare the estimate with the independent matchup evidence
- ask whether the difference is larger than the uncertainty in the estimate

Example:

If STS requires `51.8%` and our reasonable probability range is `49–53%`, this is not a reliable edge.

Do not choose the top of a probability range simply because it creates value.

The relevant question is not:

> Can we construct a number above break-even?

The relevant question is:

> Is our probability estimate sufficiently reliable that the difference from break-even survives reasonable uncertainty?

Avoid narrow ranges such as `53–55%` unless the data quality genuinely supports that degree of precision.

---

## Pre-match re-check

For relevant matches, perform a final re-check approximately **20–30 minutes before scheduled start** when practical.

Do not assume confirmed veto will be available at that time.

Re-check where possible:

- roster / stand-in changes
- confirmed or newly available veto information
- map-related information
- significant public market movement
- other material information affecting the original thesis

If confirmed veto becomes available, reassess the original matchup thesis and probability estimate before making or confirming a decision.

If veto is still unavailable, make the decision using the verified pre-veto evidence and uncertainty already documented.

Do not wait so long for veto that the match goes live before a pre-match decision can be made.

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

A better STS price than the public market does not strengthen a weak thesis.

Then make one decision:

`BET`

or

`PASS`

A correct prediction is not automatically a good bet.

A PASS does not count toward the 10-bet experiment.

---

## Correction protocol

If an error is discovered before the match:

1. identify exactly which input or assumption was wrong
2. withdraw the previous estimate
3. rebuild the relevant part of the analysis
4. state whether the status changed because of:
   - new external information, or
   - correction of our previous analysis

Do not silently move probabilities or change a decision.

A user question or disagreement is not new evidence by itself.

If the user's challenge exposes an overlooked fact, incorrect statistic, or faulty interpretation, classify the change as an **analysis correction** and explain the concrete reason for the change.

The objective is not to agree with the user. The objective is to reach the same conclusion from the same verified evidence regardless of who identifies the issue.

---

## Case logging

Create a file in `/cases` when a candidate receives substantial analysis and is useful for later review, especially when:

- STS odds were requested and evaluated
- the candidate reached `WATCH` / `CANDIDATE` status
- veto materially changed the estimate
- an external model or predictor was used
- a meaningful market move occurred
- the final decision was PASS but the reasoning may teach us something
- an analysis correction materially changed the assessment

Naming convention:

`cases/YYYY-MM-DD_TEAM-A_vs_TEAM-B.md`

A case file should contain, where available:

- date
- event / format
- matchup
- initial edge hypothesis
- evidence quality
- relevant STS prices
- public market context
- pre-veto probability / fair odds
- veto predictor output, if used
- confirmed veto
- post-veto probability / fair odds
- adversarial check
- final decision
- result
- post-match observation
- analysis corrections, if any

Case files are historical records.

Never rewrite the original pre-match estimates after the result is known. Add post-match notes separately.

A PASS case does **not** enter `TRACKER.md` and does **not** count toward #1/10–#10/10.

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

A confirmed BET may also have a corresponding `/cases` file if the pre-decision history is useful, but `/bets` remains the authoritative record for the experiment sample.

### Freeze the pre-match snapshot

Once the bet is confirmed, the original pre-match analysis is frozen.

Never rewrite the original:

- probability
- fair odds
- confidence
- thesis
- risks

after seeing the match result or live action.

---

## Live matches

Do not chase losses.

Do not add exposure merely because the original bet is losing.

A live market can only become a new candidate if it independently satisfies the same value process.

Live score or momentum alone is not sufficient evidence of value.

Research into dedicated live models belongs in `RESEARCH.md` and does not change the current live-betting rules during the initial experiment.

---

## After the match

### Confirmed BET

For a confirmed BET:

- add result
- add closing odds, if available
- add CLV, if available
- add P/L
- add a short post-match evaluation
- update `TRACKER.md`

### Logged PASS case

For a logged PASS case:

- keep the original pre-match analysis frozen
- append the actual result
- add a short post-match observation
- assess reasoning independently of whether the PASS would have won or lost
- do not add it to `TRACKER.md`

A winning bet can be a bad decision.

A losing bet can be a good decision.

A PASS that would have won is not automatically a mistake.

Do not create a new methodology rule from one match.

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
- relevant near-miss PASS cases from `/cases`
- research ideas collected in `RESEARCH.md`

Only after the complete review should changes to the methodology be proposed.

The purpose of the first 10 bets is not to prove profitability.

The purpose is to determine whether EDGE v2 shows enough evidence of identifying mispriced probabilities to justify further testing.
