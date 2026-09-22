# EDGE v2 Case — UPGRADE vs Just Players

Date: 2026-09-22  
Decision: `PASS`  
Experiment status after decision: `0 / 10`

This case does **not** count toward the 10-bet sample.

---

## Match context

Match: UPGRADE vs Just Players  
Format: BO3  
Market investigated: UPGRADE ML  
Secondary market checked: Over 2.5 maps

UPGRADE was identified independently as a plausible candidate before the final STS price move.

---

## Initial thesis

The initial thesis was that UPGRADE could be undervalued because of:

- higher team ranking / baseline strength
- more stable roster
- Just Players playing with substitutes
- a potentially favorable map path
- public market pricing UPGRADE shorter than STS

Evidence quality:

`MEDIUM`

Main uncertainty:

- UPGRADE's recent form was not strong
- exact veto was not yet known
- Just Players had credible map-level paths despite roster instability

---

## STS price history

Observed STS UPGRADE ML:

- 1.65
- 1.72
- 1.70 before veto

At 1.70:

Break-even probability:

`58.8%`

Working pre-veto UPGRADE probability:

`~61–62%`

Indicative pre-veto fair odds:

`~1.61–1.64`

This made UPGRADE a credible WATCH / near-BET candidate, but not yet a confirmed BET.

---

## Veto predictor check

Supplementary model:

`hyprcs/cs2-veto`

The model was used as additional evidence only.

Its strongest expectations included:

- Just Players first ban: Inferno
- UPGRADE likely pick: Anubis
- Just Players likely pick: Mirage or Ancient
- Anubis had a high probability of being played

The predictor supported the general idea that UPGRADE could reach a favorable map structure, but it was not treated as decision authority.

---

## Confirmed veto

Actual maps:

- M1 Ancient — Just Players pick
- M2 Nuke — UPGRADE pick
- M3 Anubis — decider

The actual veto only partially matched the predictor.

---

## Post-veto reassessment

The confirmed veto reduced confidence in the original UPGRADE ML thesis.

Reasoning at the time:

- Ancient was treated as a credible Just Players map
- Nuke was considered reasonable for UPGRADE
- Anubis as decider was acceptable for UPGRADE, but not enough to create a large margin

Post-veto estimated UPGRADE series probability:

`~59–61%`

STS odds:

`1.70`

Break-even probability:

`58.8%`

Estimated edge after veto:

`~0–2 percentage points`

Evidence quality:

`MEDIUM`

---

## Adversarial check

### Why the market could be wrong

- UPGRADE had the stronger baseline profile
- roster stability favored UPGRADE
- Just Players had substitutes
- STS 1.70 was better than the earlier public-market range
- Anubis as a possible decider was not unfavorable for UPGRADE

### Why we could be wrong

- recent UPGRADE form was weak
- Just Players had a credible Ancient path
- veto uncertainty was still meaningful at decision time
- the estimated edge was small relative to model uncertainty
- the external veto predictor was not proven enough to justify increasing confidence

---

## Final decision

`PASS`

Reason:

The estimated post-veto edge was too small relative to uncertainty.

The match was not added to `TRACKER.md` and did not become #1/10.

---

## Result

UPGRADE won 2:1.

Map scores:

- Ancient: UPGRADE 13:5 Just Players
- Nuke: UPGRADE 13:16 Just Players
- Anubis: UPGRADE 13:4 Just Players

The PASS would have won at 1.70.

---

## Post-match observation

The result does not make the PASS incorrect by itself.

However, this case suggests that the post-veto reassessment may have:

- overweighted map ownership / pick order
- underweighted UPGRADE's underlying strength on Ancient and Anubis
- reduced the series probability too aggressively after seeing the veto

Notably:

- UPGRADE dominated Ancient despite it being the Just Players pick
- UPGRADE lost Nuke despite it being the UPGRADE pick
- UPGRADE dominated the Anubis decider

This is a useful reminder that:

> A team's pick is not automatically a strong probability advantage.

For future review, compare actual map strength and matchup evidence against simple pick ownership before making large probability adjustments.

No methodology rule is changed from this single case.
