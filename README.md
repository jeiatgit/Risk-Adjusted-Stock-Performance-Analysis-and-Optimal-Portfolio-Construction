# Risk-Adjusted Stock Performance Analysis and Optimal Portfolio Construction Using CAPM and Modern Portfolio Theory (MPT)

**Course:** Financial Engineering  
**Project status:** Research design and architecture blueprint  
**Research framework:** CAPM + Modern Portfolio Theory (MPT) + portfolio optimization

## 1. Project overview

This project studies the risk-adjusted performance of selected publicly listed companies across multiple sectors and constructs portfolios using financial estimates derived from historical market data.

The project has two connected analytical responsibilities:

1. **Individual-stock analysis:** estimate returns, volatility, beta, CAPM-implied return, Jensen's alpha and risk-adjusted performance.
2. **Portfolio analysis:** estimate the covariance structure of selected stocks, construct feasible portfolios, identify the minimum-variance and maximum-Sharpe portfolios, visualize the efficient frontier, and evaluate the portfolios against simple benchmarks.

The project is not primarily a stock-price prediction system. Its core task is to analyze risk and return and evaluate portfolio allocations under explicit assumptions.

## 2. Research question

> How can CAPM and Modern Portfolio Theory be used to evaluate risk-adjusted stock performance and construct diversified portfolios across selected market sectors, and how do optimized portfolios compare with benchmark portfolios on out-of-sample data?

The market choice is now NASDAQ-listed US equities. The exact stock universe, benchmark series and risk-free-rate convention must be finalized during the data-feasibility audit.

## 3. Provisional research design

The market and high-level design choices below are confirmed. The exact company list, benchmark series and risk-free-rate conversion still require a documented data-feasibility audit.

| Design decision | Initial proposal |
|---|---|
| Market/exchange | NASDAQ-listed US equities |
| Sector universe | Start with 5 sectors |
| Companies per sector | Start with 2 |
| Total stocks | 10 |
| Historical period | Approximately 5 years, subject to comparable data availability |
| Frequency | Daily returns for the primary analysis; monthly returns as an optional robustness check |
| Individual-stock model | Standard CAPM regression |
| Portfolio model | Mean-variance optimization |
| Primary portfolios | Minimum variance and maximum Sharpe |
| Reference portfolio | Equal-weighted portfolio |
| Visualization | Risk-return scatter and optimized efficient frontier |
| Validation | Chronological holdout at minimum; walk-forward validation if feasible |
| Advanced extension | Select one: covariance shrinkage, CAPM-informed expected returns, sector caps, or CVaR |

## 4. Core methodology

1. Define the market, sectors, company-selection rules and date range.
2. Audit data availability for every selected NASDAQ-listed stock, the selected Nasdaq-market benchmark series and US Treasury risk-free-rate series.
3. Collect and preserve raw source data.
4. Clean, align and validate observations; document corporate-action and dividend treatment.
5. Calculate simple returns and descriptive risk/return statistics.
6. Estimate CAPM beta, alpha, expected return and regression diagnostics.
7. Estimate the expected-return vector and covariance matrix for portfolio analysis.
8. Construct equal-weight, minimum-variance and maximum-Sharpe portfolios.
9. Use Monte Carlo weight sampling to visualize the feasible portfolio region; use a numerical optimizer for the actual constrained optima.
10. Construct the efficient frontier using optimization across target-return levels.
11. Compare portfolios using consistent metrics and identical evaluation dates.
12. Perform out-of-sample validation and document limitations.

## 5. Repository architecture

```text
financial-engineering-portfolio/
├── README.md
├── pyproject.toml
├── .python-version
├── .gitignore
├── data/
│   ├── README.md
│   ├── raw/
│   ├── interim/
│   └── processed/
├── docs/
│   ├── CURRENT_PROJECT_ANALYSIS.md
│   ├── PROJECT_PLAN.md
│   ├── ARCHITECTURE.md
│   ├── DATA_METHODOLOGY.md
│   ├── IMPLEMENTATION_PROMPT.md
│   ├── mathematical-models/
│   │   ├── README.md
│   │   ├── capm.md
│   │   └── portfolio_optimization.md
│   └── validation/
│       └── VALIDATION_PROTOCOL.md
├── notebooks/
│   ├── exploration/
│   ├── experiments/
│   └── validation/
├── scripts/
│   ├── audit_data.py
│   ├── build_dataset.py
│   └── run_validation.py
├── src/
│   └── portfolio_optimizer/
│       ├── common/
│       ├── data/
│       ├── analytics/
│       ├── capm/
│       ├── portfolio/
│       ├── simulation/
│       ├── validation/
│       └── integration/
├── backend/
│   └── app/
│       ├── api/
│       ├── schemas/
│       ├── services/
│       └── main.py
├── frontend/
│   └── src/
│       ├── components/
│       ├── pages/
│       ├── services/
│       ├── types/
│       └── utils/
└── tests/
    ├── data/
    ├── analytics/
    ├── capm/
    ├── portfolio/
    ├── simulation/
    └── integration/
```

The frontend and backend are planned delivery layers, not prerequisites for validating the financial models. Implement and test the Python core first.

## 6. What each documentation file is for

- `CURRENT_PROJECT_ANALYSIS.md`: current state, decisions, unknowns, risks and preservation rules.
- `PROJECT_PLAN.md`: research objectives, work phases, milestones and acceptance criteria.
- `ARCHITECTURE.md`: module boundaries, data flow, contracts and repository tree.
- `DATA_METHODOLOGY.md`: market selection, data sources, date range, returns, benchmark and risk-free-rate conventions.
- `mathematical-models/capm.md`: regression model, definitions, estimation and interpretation.
- `mathematical-models/portfolio_optimization.md`: mean-variance model, constraints, efficient frontier and simulation.
- `validation/VALIDATION_PROTOCOL.md`: unit tests, in-sample/out-of-sample separation, benchmarks and performance metrics.
- `IMPLEMENTATION_PROMPT.md`: a detailed instruction for an AI coding agent to build the repository from the agreed specifications.

## 7. Important methodological rules

- Do not use future observations to estimate weights for an earlier test period.
- Do not call in-sample performance evidence of future performance.
- Do not treat CAPM alpha as proof of mispricing or guaranteed future outperformance.
- Do not treat Monte Carlo sampling as a guarantee of finding the mathematical optimum.
- Use compatible return horizons for expected return, volatility and risk-free rate.
- Clearly label assumptions, proxies, unavailable data and limitations.
- Keep raw data separate from processed data; never silently overwrite source files.
- Keep optimization logic out of API routes and frontend components.
- Do not fabricate results, metrics, source coverage or validation claims.

## 8. Scope control

The first milestone is a reproducible analytical pipeline that runs locally and produces validated tables and figures. Add the API and dashboard only after the core calculations and validation tests pass.

This repository is a documentation/architecture starter pack. It does not claim that market data have been downloaded, models have been implemented, or empirical results have been obtained.
