# Portfolio Optimization, Monte Carlo Sampling and the Efficient Frontier

## 1. Purpose

Construct portfolios from a selected stock universe and compare risk-return trade-offs under explicit assumptions. The baseline uses mean-variance optimization.

## 2. Inputs

- \(\boldsymbol{\mu}\): expected-return vector for the \(n\) stocks;
- \(\Sigma\): covariance matrix of their returns;
- \(\mathbf{w}\): portfolio weights;
- \(R_f\): risk-free rate matched to the return horizon.

The expected-return vector may be estimated from historical averages. A later controlled experiment may replace it with CAPM-implied estimates. Do not silently switch methods between portfolios.

## 3. Portfolio return and variance

\[
E(R_p)=\mathbf{w}^{T}\boldsymbol{\mu}
\]

\[
\sigma_p^2=\mathbf{w}^{T}\Sigma\mathbf{w}
\]

\[
S_p=\frac{E(R_p)-R_f}{\sigma_p}
\]

All quantities must use compatible return horizons and units.

## 4. Baseline constraints

Use a long-only, fully invested portfolio initially:

\[
\sum_{i=1}^{n}w_i=1,\qquad 0\leq w_i\leq1
\]

Optional experiments may add maximum stock-weight or sector-allocation limits. Report the reason for each constraint and compare constrained results with the baseline. Short selling and leverage are excluded from the initial scope.

## 5. Minimum-variance portfolio

\[
\min_{\mathbf{w}}\quad \mathbf{w}^{T}\Sigma\mathbf{w}
\]

subject to the fully invested and long-only constraints.

Output: weights, estimated expected return, volatility, Sharpe ratio and concentration metrics.

## 6. Maximum-Sharpe portfolio

\[
\max_{\mathbf{w}}\quad
\frac{\mathbf{w}^{T}\boldsymbol{\mu}-R_f}
{\sqrt{\mathbf{w}^{T}\Sigma\mathbf{w}}}
\]

subject to the same baseline constraints. The implementation must handle solver failures, invalid inputs and edge cases explicitly.

## 7. Efficient frontier

For a sequence of feasible target returns \(r^*\), solve:

\[
\min_{\mathbf{w}}\quad \mathbf{w}^{T}\Sigma\mathbf{w}
\]

subject to:

\[
\mathbf{w}^{T}\boldsymbol{\mu}=r^*,\quad
\sum_i w_i=1,\quad w_i\geq0
\]

The efficient frontier is the upper/efficient part of the minimum-variance frontier. Plot annualized volatility on the horizontal axis and annualized expected return on the vertical axis. Mark the minimum-variance and maximum-Sharpe portfolios.

## 8. Monte Carlo portfolio-weight sampling

Monte Carlo weight sampling generates many feasible candidate vectors \(\mathbf{w}\), calculates each candidate's return, volatility and Sharpe ratio, and plots the feasible region.

It is useful for visualization and diagnostics. It does **not** guarantee that the mathematical optimum has been found. Use a numerical optimizer for the reported optimum and frontier; use Monte Carlo to illustrate the distribution of candidate portfolios.

Record:
- number of samples;
- random seed;
- weight constraints and sampling procedure;
- estimation period;
- input return and covariance method.

Do not confuse weight sampling with Monte Carlo simulation of future return paths. Future-path simulation is a separate optional extension requiring explicit assumptions about return distributions or resampling.

## 9. Benchmark portfolios

At minimum compare:
1. Equal-weighted portfolio.
2. Minimum-variance portfolio.
3. Maximum-Sharpe portfolio.
4. Selected broad-market benchmark.

All portfolio comparisons must use the same evaluation dates and compatible total-return conventions. If rebalancing is simulated, state its frequency and transaction-cost treatment.

## 10. Estimation error and optional enhancements

Historical means and covariance estimates are noisy. Optimizers can amplify this noise and create extreme allocations. After the baseline is tested, consider one extension:
- Ledoit-Wolf covariance shrinkage;
- CAPM-implied versus historical expected-return inputs;
- maximum stock/sector weight constraints;
- CVaR-based downside-risk optimization.

Keep the baseline results and compare the extension using the same out-of-sample design.

## 11. Required output

- Weight table;
- estimated return, volatility and Sharpe ratio;
- minimum-variance and maximum-Sharpe allocations;
- efficient-frontier plot;
- Monte Carlo candidate cloud;
- benchmark comparison;
- out-of-sample evaluation;
- sensitivity and limitations report.
