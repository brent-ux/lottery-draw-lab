# Brent's Odds — Five-Year Deep Research (v3.0)

**Research snapshot:** November 24, 2026. This is an experimental *ticket-filtering research system*, not a validated method for improving lottery jackpot odds.

## Scope
- Powerball: 783 completed drawings, November 24, 2021–November 23, 2026. White balls 1–69; current-format full jackpot outcome count 292,201,338.
- Mega Millions: 521 completed drawings, November 26, 2021–November 20, 2026. White balls 1–70; jackpot bonus-ball range changed from 25 to 24 in April 2025. Today's full jackpot outcome count 290,472,336.
- Sources: [New York State Powerball draw records](https://data.ny.gov/d/d6yy-54nr) and [New York State Mega Millions draw records](https://data.ny.gov/d/5xaw-6ayf), accessed via date-stamped [lottery-master-archive](https://github.com/cruiseliner/lottery-master-archive) CSV snapshots.
- Audited **11,238,513 Powerball** and **12,103,014 Mega Millions** unique white-ball combinations: **23,341,527 total**.
- Studied **110 candidate structural exclusion rules** across gaps, consecutive runs, span, ranges, position, digit endings, modular arithmetic, primes, multiples, parity, and sum. **29** of these have exact combined-union selection in the live dashboard.
- Held out the most recent year from the first four years for preliminary validation (Powerball 626/157 draws; Mega Millions 417/104). The entire search was exploratory; the holdout is not an independent preregistered future study.

## Specific hypothesis: all five white balls end with the same digit
- Examples: 1, 11, 21, 31, 41; 11, 21, 31, 41, 51; or *non*-ten-step variants such as 1, 11, 21, 41, 61.
- In the five-year window, **zero** 5-same-ending outcomes in either game.
- Exactly 195 / 11,238,513 Powerball white combinations and 210 / 12,103,014 Mega Millions white combinations share one final digit. Both shares equal 0.00173510499%, or approximately **1 chance in 57,633.4 per draw**.
- Expected counts if fair: 0.0136 for 783 PB drawings, 0.0090 for 521 MM drawings; chances of zero under fair randomness ~98.65% PB, ~99.10% MM. So an absence is overwhelmingly expected, **not evidence of prevention by hardware**.
- The narrower **five whites exactly 10 apart** family has 29 PB combinations and 30 MM combinations. It is a strict subset of five-same-ending and is not double counted.
- Four-same-ending near misses: PB 2024-05-27 [9, 30, 39, 49, 59]; MM 2024-10-29 [16, 22, 26, 36, 56] and 2025-05-16 [2, 22, 42, 62, 66].
- Across broader checked archives: 0 five-same-ending in 3,885 PB draws from 1992–2026, and 0 in 2,559 MM draws from 2002–2026; old Powerball data is from a separate GitHub historical CSV and has earlier game matrices.

## Five-year scan findings
No one of the 110 structural rules was statistically supported as suppressed after accounting for searching 110 hypotheses and testing the most recent year. For example:

| Game | Candidate most depleted during first four years | Earlier observed | Earlier expected | Unadjusted one-sided p | Newer observed | Newer expected |
|---|---|---:|---:|---:|---:|---:|
| PB | At least three numbers in 1–20 | 68 | 88.76 | 0.00844 | 19 | 22.26 |
| MM | At least three numbers in highest 20 | 44 | 57.00 | 0.03408 | 12 | 14.21 |

Both preliminary signals fail 110-test correction (Bonferroni threshold 0.0004545), and neither is strongly replicated in the later sample. These do not establish machine bias.

## Exact interactive filters and overlaps
The site uses a **sparse count-of-bitmasks** for all Powerball and Mega Millions white combinations, derived from exhaustive enumeration. The core 27 overlapping structural rules are represented by 2,899 nonempty pattern buckets per game. The two nested special cases (all five same final digit and exactly ten apart) are separately cross-tabulated with those 27 buckets. The union calculation avoids counting the same excluded five-white combination twice. For all games, excluded white sets are then multiplied by the current bonus-ball count.

Initial exploratory preset: exclude 4+ consecutive white balls, five-white span ≤9, and 5 same-ending white balls (the ten-step subcase adds no additional exclusions).
- Powerball: **11,421 distinct white sets removed**, ×26 = **296,946 complete full-ticket combinations** excluded; **291,904,392** retained.
- Mega Millions: **11,682 distinct white sets removed**, ×24 = **280,368 complete full-ticket combinations** excluded; **290,191,968** retained.

These retained counts are **not improved per-ticket winning odds**. If every complete ticket remains equally likely, selecting a non-excluded ticket still wins with the original odds of 1/292,201,338 for PB and 1/290,472,336 for MM.

## Files and usage
- [Raw research and exact mask counts](brents_odds_5yr_v3.json)
- [110 candidate tests for both games (CSV)](brents_odds_5yr_v3_summary.csv)
- [Interactive website](https://brent-ux.github.io/lottery-draw-lab/)

Avoid treating **historical zero** or **visually unusual combinations** as mechanically impossible. A physical-machine hypothesis needs equipment evidence, reproducible directional bias, enough data, multiple-testing control and preferably prospective out-of-sample confirmation. The simulator's own 2D mixing model is not a real-draw ground truth.
