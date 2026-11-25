# Brent's Odds 2.0 — exhaustive candidate-filter audit

**Snapshot:** 2026-11-24 (Powerball through 2026-11-23; Mega Millions through 2026-11-20).

## Purpose
Enumerate every possible five-white-ball combination for the current games, calculate the exact size of structural exclusion categories, and compare historical drawing frequencies with the probability expected from a fair draw. These filters are **not proven predictive**.

- **Powerball:** C(69,5) = **11,238,513** white combinations; × 26 bonus balls = **292,201,338** full outcomes.
- **Mega Millions:** C(70,5) = **12,103,014** white combinations; × 24 bonus balls = **290,472,336** full outcomes.
- **Total white combinations enumerated:** **23,341,527**.

## Files

- [brents_odds_v2.json](brents_odds_v2.json): exact **2,048-bucket structural mask distribution** for each game, plus separate 75% chronological training and 25% holdout histograms.
- [brents_odds_v2_summary.csv](brents_odds_v2_summary.csv): candidate rule definitions, theoretical exclusion shares and historical expected-versus-actual counts.
- [Live Lottery Draw Lab](https://brent-ux.github.io/lottery-draw-lab/): interactive exact-union calculator and optional Ticket Lab screening.

## Eleven candidate rules
1. At least one adjacent pair.
2. Run of three consecutive numbers.
3. Run of four consecutive numbers.
4. All five consecutive.
5. Entire five-ball span ≤9.
6. Entire five-ball span ≤14.
7. Five white balls all odd or all even.
8. All five in the same numerical half of the current ball range.
9. At least four white balls within one ten-number band (1–10, 11–20, ...).
10. At least three white balls with the same final digit.
11. Sum of the five white balls ≤95 or ≥260.

**Overlaps:** Rules are not independent. The app applies a bitmask to each of the 23.34 million enumerated white sets, then sums the masked buckets; it never naively adds rule percentages.

## Historical method
Historical data originates from the [New York State Powerball dataset](https://data.ny.gov/d/d6yy-54nr) and [New York State Mega Millions dataset](https://data.ny.gov/d/5xaw-6ayf), as normalized in the [lottery-master-archive](https://github.com/cruiseliner/lottery-master-archive) snapshots:
- Powerball: 2,029 observed drawings 2010–2026, but current-matrix comparison uses **1,437** drawings in the `pb-2015` era (1,077 training / 360 holdout).
- Mega Millions: 2,559 observed drawings 2002–2026, but current-matrix comparison uses **170** drawings in `mm-2025` era (127 training / 43 holdout).

**We do not pool eras with different ball ranges to calculate an observed-vs-expected probability under the current rules.** Historical drawing archives are derivative snapshots; for official payout verification, the certified lottery records take precedence. Actual data snapshots end on the above dates.

## Findings
- Any adjacent pair is expected in **26.5037%** of current Powerball outcomes and **26.1595%** of current Mega Millions outcomes.
- The current-format Powerball sample has **377 / 1,437** adjacent-pair drawings, versus approximately **381** expected.
- The current-format Mega Millions sample has **41 / 170**, versus approximately **44.5** expected.
- No five-consecutive white draw appears in these archives. Such draws are extraordinarily rare **even if the machines are perfectly fair**, so absence is not evidence of suppression.
- A conservative **example** filter combining *four or more consecutive numbers* OR *span ≤9* excludes exactly **11,226** white combinations (0.09989%) for PB and **11,472** (0.09479%) for MM.
- The Powerball same-half filter illustrates why held-out checking matters: **77** training hits vs **57.8** expected, but only **9** held-out hits vs **19.3** expected—an apparent reversal.
- No candidate is established as a reproducible bias that improves jackpot odds. Small or post-hoc differences can result from chance and multiple testing.

## Interpretation and constraints
**Brent's Odds** is the size of the _retained playing pool conditional on excluding certain structures_. It is **not** the actual chance that a single retained ticket wins. In an unbiased lottery each five-white-ball plus bonus combination is still equally likely, and excluding a category removes that category's share of future winners. The simulator uses approximate 2D mechanics and does not reproduce certified physical draws; never train filters against its output as though that proves real-world physical suppression.

### Next research step
Pre-register a small set of falsifiable bias hypotheses, gather much more current-equipment outcome history, and report the same one-sided significance test on later drawings with corrections for the 11 simultaneous comparisons. Treat the training portion as exploration, not confirmation.
