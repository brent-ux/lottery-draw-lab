# Brent's Odds 4.0 — Deep Five-Year Structural Audit

Research snapshot: **November 24, 2026**. This is a structural **ticket-selection system**, not a demonstrated way to improve the probability of winning a lottery draw. Every complete permitted ticket remains equally likely under a fair draw.

## Scope and coverage

- Period: **November 24, 2021 through November 24, 2026**; last complete Powerball drawing Nov. 23 and last complete Mega Millions drawing Nov. 20.
- **Powerball**: 783 historical draws; 626 earlier / 157 recent-year holdout. White-ball universe 1–69, red ball 1–26.
- **Mega Millions**: 521 draws; 417 earlier / 104 recent-year holdout. White-ball universe 1–70; the bonus range changed in April 2025, so today's jackpot universe uses 24 Mega Balls.
- Independently enumerated **all 11,238,513 Powerball** and **12,103,014 Mega Millions** five-white-ball sets.
- Calculated **31 macro-structural bitmask features**, plus two overlapping end-digit microstructure categories.
- Analyzed the earlier **110 candidate rules** and then **4,960 two- and three-rule intersections** among the 31 new macro features. The 4,960 intersections are investigative comparisons, not individually validated exclusion rules.

The complete audit was computed from independent [New York State Powerball drawing records](https://data.ny.gov/d/d6yy-54nr) and [Mega Millions drawing records](https://data.ny.gov/d/5xaw-6ayf), accessed through [lottery-master-archive snapshots](https://github.com/cruiseliner/lottery-master-archive).

## Four exactly counted filter presets

| Preset | PB pool retained | PB eliminated | PB holdout winners excluded | MM pool retained | MM eliminated | MM holdout winners excluded |
|---|---:|---:|---|---:|---:|---|
| Rare | 259,693,122 | 11.125% | 13/157 (8.3%) | 258,183,696 | 11.116% | 11/104 (10.6%) |
| Broad | 186,092,244 | 36.314% | 44/157 (28.0%) | 186,404,328 | 35.827% | 35/104 (33.7%) |
| **Deep** | **106,476,188** | **63.561%** | **95/157 (60.5%)** | **106,920,624** | **63.191%** | **63/104 (60.6%)** |
| Maximum | 66,757,470 | 77.154% | 119/157 (75.8%) | 67,692,552 | 76.696% | 80/104 (76.9%) |

These are counts of possible **complete combinations still in the playing pool**, not conditional winning probabilities. Observed winner exclusions are close to the theoretical percentage removed from the combination universe. This indicates no demonstrated predictive advantage.

**Deep preset rules:** 4+ of five white balls in the same numeric half; total white-ball span ≤40; white-ball sum ≤120 or ≥245; 3+ share a last digit; 2+ adjacent gaps of exactly 1; 3+ in an aligned ten-number band (1–10, 11–20, etc.); all five are non-prime numbers.

**Maximum** adds 4+ odd or 4+ even, and 3+ white balls from the bottom twenty, further increasing exclusion while removing more genuinely plausible outcomes.

## What the interaction study found

The **4,960** pair and triple intersections were compared against the earlier-four-years data and the newest year:

- Powerball: a combination of 4+ of one parity and 3+ in the lowest 20 appeared **17** times versus **31.0** expected in the training period, but **9** times versus **7.8** expected in the holdout. The apparent shortage reversed.
- Mega Millions: 4+ in one numeric half and zero primes appeared **17** times versus **28.6** expected in training, but **6** versus **7.1** in the holdout.
- In these 4,960 exploratory comparisons, no striking discrepancy survives a correction for searching thousands of categories and then independent confirmation in later drawings. We should not infer a controlled machine suppression mechanism from the training anomalies.

The original 110 single-rule analysis also did **not** establish statistically validated mechanical bias.

## The crucial distinction

Restricting a hypothetical ticket pool from 292.2 million to 106.5 million (Powerball) does **not** improve an individual ticket's jackpot chance. With a random draw, each exact five-number + bonus-ball ticket is still 1 in 292,201,338 for Powerball and 1 in 290,472,336 for today's Mega Millions.

A filter can remove *millions* of number structures, but it does not remove those outcomes from the machines. If the drawing falls in the excluded share, none of the tickets generated from the filtered pool can win the jackpot.

A statistically credible advantage would require **underrepresentation of excluded structures in genuinely new results**, compared with exact theoretical combinatorial frequency, accounting for thousands of tests, and a plausible physical mechanism. Current results do not provide that.

## Reproducible sources and browser tools

- [Exact 31-feature full-population histograms](brents_odds_deep_v4.json) — exhaustive counts for every distinct combined structural pattern, plus 5-year training and holdout histograms.
- [Four selected preset definitions, overlaps, and winner dropout](brents_odds_v4_presets.json).
- [4,960 pair-and-triple interactions](brents_odds_2way_3way_v4.json).
- [Original 110 individual candidate tests](brents_odds_5yr_v3_summary.csv).
- [Open Lottery Draw Lab / Brent's Odds 4.0](https://brent-ux.github.io/lottery-draw-lab/): choose four presets, adjust 33 exact filter toggles, and optionally apply rules to ticket generation. The option to screen tickets is **off** unless checked explicitly.

**Preregistered next step:** Freeze a small set of machine-related bias hypotheses and evaluate them only on future completed drawings, without modifying thresholds after observing the outcomes.
