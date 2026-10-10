# Research Design Decisions

## Confirmed

- Market/universe venue: NASDAQ-listed US equities.
- Research scope: multi-sector equity portfolio optimization.
- Sector count: five.
- Companies per sector: two.
- Universe size: ten companies.
- Historical period: five years, subject to consistent data coverage.
- Return frequency: daily; monthly robustness checks if feasible.
- Individual-stock analysis: descriptive statistics and CAPM.
- Portfolio framework: mean-variance optimization.
- Portfolio objectives: minimum variance and maximum Sharpe.
- Portfolio simulation: Monte Carlo weight sampling.
- Solver: numerical constrained optimization.
- Portfolio baseline: equal weighting.
- Market comparison: a justified Nasdaq-market benchmark series with a consistent return convention.
- Validation: chronological holdout, with walk-forward validation if feasible.
- Advanced extension: covariance shrinkage or CAPM-informed optimization; select one after the baseline is validated.

## Still requires evidence-based specification

- Exact ten companies and sector assignments.
- Exact historical start/end dates after checking overlapping data.
- Price/total-return source and corporate-action conventions.
- Exact benchmark series and availability of a total-return version.
- US Treasury maturity, data source and conversion from quoted yield to the analysis frequency.
- Whether the advanced extension will be covariance shrinkage or CAPM-informed expected returns.

## Important distinction

NASDAQ is the listing venue for the selected stocks. It is not, by itself, a unique benchmark return series. The project must name the exact benchmark index/data series used in CAPM and portfolio comparisons. The NASDAQ Composite and NASDAQ-100 have different coverage and must not be treated as interchangeable.
