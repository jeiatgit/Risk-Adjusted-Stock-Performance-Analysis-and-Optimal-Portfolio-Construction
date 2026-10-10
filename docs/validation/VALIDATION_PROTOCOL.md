# Validation Protocol

## 1. Purpose

Validation determines whether data processing and mathematical implementation are correct and whether portfolio conclusions survive evaluation on observations not used to estimate the model.

## 2. Data validation

Required checks:
- dates are unique and sorted;
- price and return values are finite and plausible;
- missing observations and exclusions are recorded;
- benchmark and risk-free data are aligned;
- corporate-action and dividend treatment is documented;
- processed outputs can be recreated from preserved raw inputs.

## 3. Unit tests

Test at minimum:
- simple-return calculation on hand-computed examples;
- annualization functions;
- covariance/correlation calculations;
- CAPM regression on synthetic data with known beta and alpha;
- weights sum to one within tolerance;
- long-only constraints hold;
- portfolio variance is nonnegative within numerical tolerance;
- portfolio metrics match independent calculations;
- infeasible optimization inputs and solver failures return explicit errors;
- Monte Carlo samples obey constraints and are reproducible with a fixed seed.

## 4. Chronological evaluation

At minimum, divide observations chronologically:
- training/estimation period: earlier dates;
- test/evaluation period: later dates.

Estimate expected returns, covariance and weights using training data only. Evaluate those weights on the later period. Never shuffle time-series rows into a random train/test split for the primary portfolio backtest.

If rolling or walk-forward validation is implemented, specify the estimation-window length, re-estimation schedule and rebalancing frequency before inspecting the results.

## 5. Benchmark comparison

Compare on the same test dates:
- equal-weighted portfolio;
- minimum-variance portfolio;
- maximum-Sharpe portfolio;
- broad-market benchmark.

Report at minimum:
- cumulative or annualized return with convention stated;
- annualized volatility;
- Sharpe ratio;
- maximum drawdown;
- turnover and transaction costs if periodic rebalancing is modelled;
- portfolio concentration and sector exposures.

Do not compare one portfolio's in-sample metrics with another portfolio's out-of-sample metrics.

## 6. Sensitivity analysis

Where feasible, test one or more:
- shorter versus longer estimation windows;
- daily versus monthly return frequency;
- sample covariance versus shrinkage covariance;
- historical versus CAPM-implied expected returns;
- unconstrained long-only versus stock/sector caps.

Record all configurations. Do not select and report only the best-looking run.

## 7. Reporting rules

- Label results as in-sample or out-of-sample.
- Separate observed results from model assumptions.
- State the sample, period, currency and data convention.
- Report failures and limitations.
- Never claim that an optimizer guarantees future returns or that historical alpha proves mispricing.
- Save tables, plots and configuration so another team member can reproduce them.
