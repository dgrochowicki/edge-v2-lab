# EDGE v2 — Experiment Rules

## 1. Market scan

Each morning, scan the available CS2 market.

Priority:
- Tier 1
- strong Tier 2

Avoid low-information matches unless there is an exceptional reason to investigate them.

No bet is required on any given day.

PASS is a successful outcome when no reliable edge exists.

## 2. Analysis before STS odds

First identify potentially interesting matches without using STS odds as the reason for selection.

Check:
- event and match format
- confirmed rosters
- stand-ins / substitutions
- recent form
- quality of recent opponents
- map pool
- matchup characteristics
- veto, when available
- sample size and reliability of map statistics
- relevant recent H2H, without overweighting it

Never invent missing information.

If important information cannot be verified, uncertainty must be reflected in the decision.

## 2A. Evidence verification gate

A match must not become a `CANDIDATE` until the key evidence supporting the thesis has been verified.

For map-based reasoning verify, where possible:

- that statistics belong to the current or relevant roster/core
- the time window used by the source
- number of maps in the sample
- quality of opponents in that sample
- whether the statistic refers to the current map pool
- whether multiple reliable sources materially disagree

Do not convert an unverified statistic into a probability estimate.

If a key statistic is uncertain, contradictory, based on a weak sample, or tied to an outdated roster, downgrade evidence quality before evaluating price.

## 2B. Market-specific thesis

The thesis must explain why the **specific market** may be mispriced, not merely why the match is interesting.

For Match ML:
- explain why one team's series win probability may differ from the market

For Over 2.5 maps:
- identify credible paths for both teams to win at least one map
- identify which likely maps create those paths
- assess whether those paths survive a plausible veto
- do not use a history of recent 2:1 scores as sufficient evidence by itself

For team over 0.5 maps:
- identify at least one credible map-winning path for that team

A general statement such as "the underdog can make this competitive" is not sufficient.

## 2C. Probability discipline

Do not assign a narrow probability range such as `53–55%` unless the evidence supports that degree of precision.

When evidence is limited, use:

- a wider probability range
- lower confidence
- or no numerical estimate until sufficient verification is complete

Every probability estimate should be explainable from the underlying matchup evidence.

Do not create false precision from small samples, qualitative impressions, or isolated recent results.

## 2D. Price must not strengthen a weak thesis

Public odds and STS odds may be used only after an independent thesis exists.

A better-than-market STS price does not make a weak matchup thesis stronger.

If independent analysis does not establish a plausible mispricing:

`PASS`

even when STS offers a better price than other bookmakers.

## 2E. Mandatory adversarial gate before CANDIDATE

Before labeling a match `CANDIDATE`, answer both:

### Why might the market be wrong?

State the concrete mechanism that could cause the market to misprice the match.

### Why might we be wrong?

Actively search for evidence that invalidates the thesis, including:

- stronger opponent quality on the other side
- misleading map win rates
- small samples
- roster changes
- unfavorable likely veto
- strength-of-schedule differences
- evidence already incorporated into the market

If the counter-case is as strong as the original thesis, the match remains `WATCH` or becomes `PASS`.

## 2F. User challenge is not new evidence

A user question or disagreement must not by itself cause the probability or decision to move.

When a challenge reveals:

- overlooked data
- incorrect statistics
- faulty interpretation
- missing market logic

explicitly classify the change as an **analysis correction**, not as new information.

Record what was wrong and recompute the thesis from the evidence.

The objective is not to agree with the user. The objective is to produce the same conclusion from the same verified data regardless of who points out a potential problem.

## 3. Request STS prices

Only after a potentially interesting spot has been identified, request the relevant STS markets.

Usually:
- Match ML
- Over 2.5 maps
- individual map ML when relevant
- team total maps when relevant to the thesis

Do not request every available market just to search for something to bet.

When scanning the market, the agent should also independently identify potentially relevant markets and ask the user whether they are available at STS rather than relying only on markets already supplied by the user.

## 4. Price evaluation

For a candidate estimate:
- win probability (p)
- fair odds = 1 / p
- STS odds
- break-even probability
- estimated edge
- confidence in the estimate

The purpose is not to predict the winner.

The question is:

> Is the offered price better than our estimate of the true probability by enough to justify the uncertainty?

A small theoretical edge is not enough when the uncertainty around the estimate is of similar or greater size.

## 5. Decision

Every analyzed candidate ends with BET or PASS.

BET requires:
- meaningful price advantage
- sufficiently reliable information
- understood downside/risk
- acceptable uncertainty

PASS when:
- edge is too small
- price is too short
- data quality is weak
- roster uncertainty is significant
- map samples are misleading or too small
- the thesis depends on one fragile assumption
- there is no reliable advantage over the market

## 6. Experiment sample

Only actual BET decisions enter the 10-bet experiment.

PASS does not count.

Number bets #1/10 through #10/10.

Do not change the methodology because of one win or loss.

Observations can be recorded during the experiment, but rule changes are considered only during the final review.

## 7. No chasing

A losing bet does not create another betting opportunity.

Do not:
- increase exposure to recover a loss
- add live bets because the original position looks bad
- manufacture a second bet from frustration

A live market may only be considered if it independently qualifies under the same value logic.

## 8. Evaluation

After bet #10, freeze the experiment and review the complete sample.

Evaluate:
- W/L
- units / ROI
- average odds
- closing-line value
- probability calibration
- performance by market type
- quality of reasoning
- quality of data
- repeated analytical mistakes
- cases where the result was good but reasoning was bad
- cases where the result was bad but reasoning was good

Results alone do not determine whether a decision was correct.

The final question is whether EDGE v2 showed evidence of identifying mispriced probabilities consistently enough to justify further testing.
