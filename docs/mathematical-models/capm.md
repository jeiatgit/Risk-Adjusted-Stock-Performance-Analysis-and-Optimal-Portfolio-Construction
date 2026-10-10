# CAPM: Individual-Stock Risk and Return Analysis

## 1. Purpose

CAPM estimates a stock's expected return based on its exposure to market risk. In this project it provides an interpretable baseline for systematic risk and a framework for evaluating realized performance relative to a single-factor model.

## 2. Excess-return regression

For stock \(i\) at time \(t\):

\[
R_{i,t}-R_{f,t} = \alpha_i + \beta_i(R_{m,t}-R_{f,t})+\epsilon_{i,t}
\]

where:
- \(R_{i,t}\): stock return for period \(t\);
- \(R_{f,t}\): risk-free return matched to period \(t\);
- \(R_{m,t}\): market benchmark return for period \(t\);
- \(\alpha_i\): regression intercept, commonly interpreted as Jensen's alpha in this setup;
- \(\beta_i\): sensitivity to market excess returns;
- \(\epsilon_{i,t}\): residual.

## 3. Beta

\[
\beta_i =
\frac{\operatorname{Cov}(R_i-R_f,\ R_m-R_f)}
{\operatorname{Var}(R_m-R_f)}
\]

Beta above one indicates higher estimated market sensitivity than the benchmark; beta below one indicates lower estimated sensitivity. Beta is historical and can change over time.

## 4. CAPM-implied expected return

\[
E(R_i)=R_f+\beta_i\left(E(R_m)-R_f\right)
\]

Use annualized inputs with an annual risk-free rate, or daily inputs with a daily risk-free rate. Do not mix horizons. Document how expected market return is estimated.

## 5. Outputs

For each stock, report:
- beta;
- alpha estimate;
- R-squared;
- coefficient uncertainty (e.g. standard error and/or confidence interval);
- sample period and observation count;
- CAPM-implied expected return under the stated convention;
- realized return over the corresponding evaluation period;
- volatility and risk-adjusted metrics from the common analytics module.

## 6. Interpretation safeguards

- A positive alpha estimate is not automatically statistically distinguishable from zero.
- A positive historical alpha does not guarantee future outperformance.
- R-squared describes fit to the selected market factor; it is not a measure of investment quality.
- CAPM is a model, not proof that a stock is under- or overvalued.
- Report uncertainty and model limitations, particularly when the sample is short or the regression assumptions are questionable.

## 7. Validation

Test the regression implementation on synthetic data with known beta and intercept. Verify that stock, benchmark and risk-free returns have matching dates and compatible units. Independently recalculate reported metrics from the regression outputs.
