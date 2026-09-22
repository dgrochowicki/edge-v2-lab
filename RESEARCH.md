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

Instead of assuming a single likely veto before it is available, estimate `P(map played)` for each map and use it as supplementary context for map-level and series-level analysis.

Once the actual veto is known, replace predictions with the confirmed maps and reassess the match.

Important limitation:

External veto models are supplementary evidence only. Confirmed veto and independent matchup analysis always take priority.

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

Prediction accuracy alone is insufficient. For betting, probability calibration matters more than simply predicting the winner.

EDGE should therefore continue recording:

- estimated probability
- fair odds
- bookmaker odds
- CLV
- eventual result

rather than measuring only W/L.

---

## 2. Potential improvements for EDGE v2.1

### Opponent-adjusted recent form

Current form should not be treated as simple W/L.

Possible future metric:

`opponent-adjusted form`

---

### Time decay

Recent matches should carry more weight than older matches.

Possible approach:

30-day half-life.

The exact decay parameter should be tested rather than assumed.

---

### Small-sample correction

Raw map win rate can be misleading.

Possible approaches:

- Beta smoothing
- Bayesian shrinkage
- minimum sample thresholds
- explicit uncertainty ranges

---

### Probabilistic veto

Before official veto, estimate map-play probabilities.

After official veto, replace predicted veto with confirmed maps and update the match probability.

Important review question:

Do not over-adjust probabilities merely because a map is one team's pick. Pick ownership should only move the estimate materially when supported by underlying map-level evidence.

---

## 3. Possible future probability pipeline

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

### CS2 Win Prediction

https://github.com/TaiZo1/cs2-win-prediction

### CS2 Evalbar

https://github.com/eigenpaul/cs2-evalbar

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

The key question is:

> Does the model estimate probabilities better than the market often enough to produce persistent value?

---

## 6. Status during initial EDGE v2 experiment

Current experiment:

`0 / 10`

No methodology changes should be made based on this research during the initial sample.

External models may be consulted as additional evidence, but they should not override the existing EDGE process or become a new selection rule mid-experiment.

Detailed candidate histories and PASS cases belong in `/cases`, not in this file.

After bet #10, review:

- `README.md`
- `RULES.md`
- `TRACKER.md`
- `RESEARCH.md`
- all `/bets`
- relevant `/cases`

Then decide which ideas are worth testing in EDGE v2.1.
