# Current Project Analysis

**Project:** Risk-Adjusted Stock Performance Analysis and Optimal Portfolio Construction Using CAPM and MPT  
**Status:** Research design / pre-implementation  
**Version:** 0.1

## 1. Executive summary

The project aims to evaluate the historical risk-return characteristics of selected stocks across multiple sectors and construct portfolios using CAPM and Modern Portfolio Theory. The core research work is quantitative: data engineering, return calculation, regression, covariance estimation, optimization and out-of-sample evaluation.

The repository should follow the documentation discipline of the team's Formula 1 Operations Research project: distinguish the research specification, mathematical models, architecture, implementation plan and validation evidence.

## 2. Decisions currently proposed

| Item | Proposed state | Status |
|---|---|---|
| Market | NASDAQ-listed US equities | Confirmed |
| Sectors | 5 | Initial recommendation |
| Companies per sector | 2 | Initial recommendation |
| Universe size | 10 stocks | Derived from proposed design |
| Historical window | Approximately 5 years | Provisional; must be based on overlapping reliable data |
| Main frequency | Daily | Proposed |
| Benchmark | NASDAQ Composite total-return series, if consistently available; otherwise a documented Nasdaq-market proxy | Exact series to verify |
| Risk-free rate | US Treasury yield series converted to a compatible return horizon | Exact maturity/source/conversion to document |
| CAPM | Excess-return regression | Core |
| MPT | Mean-variance framework | Core |
| Portfolio objectives | Minimum variance and maximum Sharpe | Core |
| Simulation | Monte Carlo portfolio-weight sampling | Visualization/diagnostic, not the optimizer itself |
| Solver | Numerical constrained optimization | Core |
| Benchmark portfolio | Equal-weighted portfolio | Core |
| Validation | Chronological holdout | Minimum requirement |
| Advanced extension | One focused extension after baseline | Open |

## 3. What is already established

- The project title and conceptual foundation are CAPM and MPT.
- The project will broaden beyond the original automobile-only stock universe.
- The team wants explicit choices for sector count, companies per sector, exchange, historical duration, portfolio simulation, risk-return analysis and the efficient frontier.
- The project should have a clean README, a structured repository and detailed implementation instructions.

## 4. Confirmed decisions

- Market: NASDAQ-listed US equities.
- Five sectors, two companies per sector, ten stocks in total.
- Approximately five years of daily data, with monthly robustness checks if feasible.
- CAPM, mean-variance optimization, minimum-variance and maximum-Sharpe portfolios, Monte Carlo weight sampling, numerical constrained optimization, equal-weight benchmark, and chronological holdout validation.

The NASDAQ listing venue and the benchmark index are different concepts: listing eligibility defines the stock universe; the benchmark is a separate return series used to estimate market exposure and compare performance.

## 5. What remains unresolved

### Market and data
- Exact NASDAQ-listed company universe and sector classification.
- Exact companies and sector taxonomy.
- Data vendor/provider and licensing/access constraints.
- Exact beginning/end dates and overlap across all assets.
- Total-return availability or a documented adjusted-price proxy.
- Benchmark index and risk-free-rate series.
- Handling of dividends, splits, delistings, ticker changes and missing observations.

### Modelling
- Whether the main optimizer uses historical mean returns, CAPM-implied expected returns, or compares both.
- Long-only constraints and any per-stock/sector allocation caps.
- Whether covariance shrinkage is included.
- Rebalancing frequency and transaction-cost assumptions for any backtest.
- Holdout dates and whether rolling walk-forward validation is feasible.

## 6. Recommended feasibility audit

Before committing to an exchange, create a candidate list and verify for each market:

1. Ten companies across five clearly defined sectors can be selected without excessive overlap in business exposure.
2. Each stock has a consistent historical price/total-return series for the intended period.
3. A compatible broad-market benchmark series is available.
4. A documented risk-free-rate series is available in the same currency.
5. The data can be retrieved legally and reproducibly using the team's available access.
6. The dates can be aligned without silently filling missing prices or mixing non-trading-day observations.

Keep NASDAQ-listed US equities as the project universe. Select the specific companies, benchmark series and risk-free-rate convention that meet these requirements with the least avoidable data friction.

## 7. Risks and mitigations

| Risk | Why it matters | Mitigation |
|---|---|---|
| Inconsistent price adjustment | Dividends/splits can distort measured returns | Document provider conventions; prefer consistent total-return data |
| Look-ahead leakage | Makes backtest performance unrealistically optimistic | Chronological splits; estimate weights only from past data |
| Estimation error | Mean-variance optimization can amplify noisy estimates | Equal-weight baseline; sensitivity checks; optional shrinkage |
| Concentration | Optimizer may place excessive weight in a few stocks/sectors | Report concentration; test explicit caps as a separate experiment |
| Survivorship/selection bias | Current winners may not represent the historical opportunity set | Predefine selection rules; disclose fixed-universe limitation |
| Unit mismatch | Daily, monthly and annualized values can be combined incorrectly | Centralize frequency and annualization conventions |
| False precision | Historical optimum may not generalize | Out-of-sample testing and parameter sensitivity |
| Scope creep | Too many models delay validation | Complete baseline before adding one advanced extension |

## 8. Preservation and reproducibility rules

- Preserve raw downloads unchanged.
- Store cleaned/merged data separately.
- Record source, download date, fields, adjustment convention and transformations.
- Do not claim the dataset is complete until a data audit demonstrates it.
- Do not commit credentials, API keys or licensed data unless permitted.
- Save model configuration and random seed for Monte Carlo experiments.
- Every reported result should be reproducible from a documented command or notebook.

## 9. Readiness gate

Do not begin full portfolio optimization until the team has:
- finalized the market and candidate universe;
- documented the return and risk-free-rate conventions;
- produced a date-aligned return matrix;
- passed data-quality tests;
- agreed on the chronological evaluation design.
