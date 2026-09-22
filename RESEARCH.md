# EDGE v2 — Research Notes

This file stores research ideas, external models, and potential improvements discovered during the initial 10-bet experiment.

These notes **do not modify the current EDGE v2 methodology**.

The rules defined in `RULES.md` remain frozen for the initial #1/10–#10/10 sample.

Ideas collected here should be evaluated only after the first experiment is completed, unless they are used purely as additional independent evidence without changing the decision process.

---

## 1. External CS2 prediction models

Several public projects were identified that may contain useful ideas for future versions of EDGE.

### CS2 Major ML Pick'Em Predictor

Repository:

https://github.com/holygodly/CS2-Major-ML-PickEm-Predictor

Interesting concepts:

- map-level prediction rather than only match-level prediction
- XGBoost model
- ~40 engineered features
- recent team/map form
- player strength
- roster stability
- H2H information
- time decay
- approximately 30-day half-life for historical data
- Beta smoothing for small map samples
- probability calibration
- veto simulation

Potential EDGE application:

Use some of these concepts to improve estimation of map and series probabilities rather than relying mainly on raw recent win rates.

---

### CS2 Veto Predictor

Repository:

https://github.com/hyprcs/cs2-veto

Interesting concepts:

- probabilistic veto prediction
- historical veto tendencies
- recency weighting
- map form
- opponent-aware veto behaviour
- profiles for hundreds of teams

Reported held-out results include strong performance in predicting bans and the eventual map set.

Potential EDGE application:

Instead of assuming a single likely veto before it is available, estimate:

`P(map played)`

for each map.

This could then feed into map-level and series-level probability estimates.

Once the actual veto is known, probabilities could be recalculated.

This may be particularly useful for:

- ML
- Over 2.5 maps
- individual map ML

---

### CS2 Match Prediction — lc-leonardo

Repository:

https://github.com/lc-leonardo/cs2-match-prediction

Interesting concepts:

- 2400+ maps
- 1000+ matches
- 20+ engineered features
- comparison of LightGBM, Random Forest, XGBoost and MLP
- probability-oriented evaluation
- Brier score
- ROC-AUC
- calibration considerations

Reported best model performance is approximately:

- accuracy: 67%
- ROC-AUC: 0.72
- Brier score: 0.231

Potential EDGE application:

The important lesson is that prediction accuracy alone is insufficient.

For betting, probability calibration matters more than simply predicting the winner.

EDGE should therefore continue recording:

- estimated probability
- fair odds
- bookmaker odds
- CLV
- eventual result

rather than measuring only W/L.

---

## 2. Potential improvements for EDGE v2.1

The following ideas should be investigated after the initial 10-bet experiment.

### Opponent-adjusted recent form

Current form should not be treated as simple W/L.

Example:

7 wins from 10 matches against weak opposition should not necessarily be considered stronger evidence than 5 wins from 10 against Tier 1 opposition.

Possible future metric:

`opponent-adjusted form`

---

### Time decay

Recent matches should carry more weight than older matches.

Possible approach:

30-day half-life.

Example:

A map played 10 days ago contributes substantially more information than a map played 80 days ago.

The exact decay parameter should be tested rather than assumed.

---

### Small-sample correction

Raw map win rate can be misleading.

Example:

80% win rate over 5 maps should not carry the same confidence as 80% over 25 maps.

Possible approaches:

- Beta smoothing
- Bayesian shrinkage
- minimum sample thresholds
- explicit uncertainty ranges

---

### Probabilistic veto

Before official veto:

Estimate probability that each map will be played.

Example:

Mirage: 72%  
Ancient: 64%  
Inferno: 41%  
Nuke: 28%

Then combine map probabilities with estimated team strength on each map.

After official veto:

Replace predicted veto with confirmed maps and update the match probability.

This creates two useful snapshots:

`pre-veto probability`

and

`post-veto probability`

The difference itself may reveal information relevant to market pricing.

---

## 3. Possible future probability pipeline

A future EDGE model could roughly follow:

Team strength

→ opponent-adjusted recent form

→ roster stability

→ player strength / availability

→ map-level strength

→ sample-size correction

→ time decay

→ probabilistic veto

→ probability of winning each likely map

→ BO3/BO5 series simulation

→ estimated match probability

→ fair odds

→ bookmaker odds

→ estimated edge

→ adversarial check

→ BET / PASS

The model should output probabilities rather than only predicted winners.

---

## 4. Live betting research

Live betting should remain separate from the current pre-match experiment.

Potential future research:

### CS2 Win Prediction

https://github.com/TaiZo1/cs2-win-prediction

Interesting concepts include round-level modelling using:

- economy
- map
- CT/T side
- opponent strength
- pistol rounds
- post-pistol rounds
- normal rounds

### CS2 Evalbar

https://github.com/eigenpaul/cs2-evalbar

Explores estimating win probability from game state using historical demo data and machine-learning models.

Potential future project:

`EDGE Live`

Possible inputs:

- pre-match probability
- confirmed veto
- current map
- current score
- CT/T side
- economy
- round state
- live bookmaker odds

The goal would again be price evaluation rather than predicting who eventually wins.

Live betting must never become a mechanism for chasing a losing pre-match position.

---

## 5. Important research question

A future research task should search for public models that provide:

- timestamped pre-match predictions
- explicit probabilities
- historical predictions that cannot be retroactively changed
- bookmaker odds at prediction time
- ideally closing odds

This would allow EDGE to evaluate whether a model actually beats the market.

Useful metrics:

- Brier score
- calibration
- log loss
- ROI
- CLV
- performance by odds range
- performance by confidence level
- performance by tournament tier
- performance by market type

A model claiming high prediction accuracy is not sufficient evidence of betting value.

The key question is:

> Does the model estimate probabilities better than the market often enough to produce persistent value?

---

## 6. Status during initial EDGE v2 experiment

Current experiment:

`0 / 10`

No methodology changes should be made based on this research during the initial sample.

External models may be consulted as additional evidence, but they should not override the existing EDGE process or become a new selection rule mid-experiment.

After bet #10, review this file together with:

- `README.md`
- `RULES.md`
- `TRACKER.md`
- all `/bets`

Then decide which ideas are worth testing in EDGE v2.1.

---

## 7. Experiment observation — UPGRADE vs Just Players (2026-09-22)

This was a useful PASS case and should be reviewed after the initial 10-bet sample.

### Pre-veto state

- UPGRADE was identified independently as a plausible candidate before the final STS price move.
- STS moved from approximately 1.65 to 1.72 and then 1.70 on UPGRADE ML.
- At 1.70, break-even probability was 58.8%.
- The working pre-veto estimate for UPGRADE was around 61–62%, so the price initially looked potentially playable.
- Evidence quality remained only MEDIUM because of recent form uncertainty and the importance of the map veto.

### Veto predictor check

The `hyprcs/cs2-veto` model was used only as supplementary evidence.

Its strongest expectations included:

- Just Players first ban: Inferno
- UPGRADE likely pick: Anubis
- Just Players likely pick: Mirage or Ancient

The actual veto was:

- M1 Ancient — Just Players pick
- M2 Nuke — UPGRADE pick
- M3 Anubis — decider

The model captured part of the map structure but did not predict the exact pick sequence.

This supports the current rule that external veto models should remain supplementary evidence rather than decision authority.

### Post-veto reassessment

The confirmed veto reduced confidence in the original UPGRADE ML thesis.

- Ancient gave Just Players a credible path to take map 1.
- Nuke was a reasonable UPGRADE map.
- Anubis as the decider was acceptable for UPGRADE, but not strong enough to create a large margin.

Post-veto estimated UPGRADE series probability was reduced to approximately 59–61%.

At STS 1.70:

- break-even: 58.8%
- estimated edge: approximately 0–2 percentage points
- evidence quality: MEDIUM

### Decision

`PASS`

The candidate was not added to the 10-bet sample.

### Why this case matters

This case demonstrates several useful process behaviours:

1. A candidate can exist before a favorable odds move; the price move should improve an existing thesis rather than create one.
2. Waiting for confirmed veto can materially change the estimated edge.
3. A seemingly attractive price is not sufficient when the remaining edge is smaller than the uncertainty in the estimate.
4. External veto models can be informative but should not override confirmed veto or independent matchup analysis.
5. A late PASS after a strong WATCH phase is a successful process outcome, not a missed bet.

No methodology rule is changed by this observation.
