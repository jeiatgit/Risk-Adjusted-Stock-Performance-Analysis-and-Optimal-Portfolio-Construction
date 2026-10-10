# Data Methodology and Market Selection

## 1. Purpose

The data design must support comparable return, CAPM and portfolio calculations. The chosen universe is US equities listed on NASDAQ. The specific stock universe, benchmark series and risk-free-rate convention must pass the feasibility checks below.

## 2. Confirmed market: NASDAQ-listed US equities

The stock universe will consist of companies listed on NASDAQ. The exchange is not itself the benchmark index: select a separate market-return series for CAPM and performance comparison. Do not mix market conventions casually; the US market choice determines currency, benchmark, risk-free-rate source, trading calendar and data-access constraints.

### Market feasibility checklist

Test a small sample of candidate NASDAQ-listed stocks before freezing the final universe:
- Can daily history be obtained for all proposed companies over an overlapping period?
- Is dividend/total-return treatment documented?
- Is a matching broad-market benchmark available?
- Is a historical government yield series available?
- Are historical symbols, splits, mergers and delistings handled?
- Is access permitted and reproducible within the project?
- Can all series be aligned without fabricated observations?

Keep NASDAQ-listed US equities as the market. Choose the exact stocks and source series based on consistent data, manageable access and a clear research rationale.

## 3. Initial universe design

Proposed starting scope: five sectors × two companies per sector = ten stocks.

Use five clearly defined US-market sectors and select two NASDAQ-listed companies per sector. Possible categories include information technology, healthcare, consumer discretionary, consumer staples and industrials; these are suggestions for the universe design, not a finalized company list. Verify each company's listing, sector classification, historical availability and corporate actions before freezing the list.

Selection rules should be written before looking at optimization results. A fixed list of current survivors can create survivorship/selection bias; disclose this limitation if a point-in-time historical universe is not feasible.

## 4. Historical duration

Initial proposal: approximately five years of daily data, subject to availability.

Longer history can capture more market conditions but may include structural changes. Shorter history is more recent but provides fewer observations and can produce unstable estimates. Do not select the period because it produces a favourable portfolio.

Record:
- exact first and last date;
- raw trading observations per series;
- common aligned observation count;
- excluded dates and reasons;
- any ticker or corporate-action changes.

## 5. Price and return convention

Prefer consistent total-return series when reliably available. If using adjusted prices as a proxy, document exactly what the provider adjusts for and do not claim dividend completeness unless confirmed.

Simple return:

\[
R_{i,t} = \frac{P_{i,t}}{P_{i,t-1}} - 1
\]

Use one documented convention across assets. Do not calculate returns across a missing observation as if it were a normal one-day return without explicitly handling the gap.

For daily data, 252 trading days is a common annualization convention, but it is an assumption. Use it consistently and document it. Annualized volatility is commonly calculated as daily standard deviation multiplied by \(\sqrt{252}\). Annualized mean return conventions must also be stated clearly.

## 6. Benchmark

Evaluate a NASDAQ Composite total-return series as the primary benchmark if a consistent, accessible series is available. If not, document the precise Nasdaq-market proxy selected and explain its coverage and return convention. A price-only index omits dividends and can make comparisons inconsistent with total-return stock data. A Nasdaq-100 series is narrower and should not be described as a broad-market benchmark without qualification. Choose and justify the primary CAPM market proxy before inspecting results.

## 7. Risk-free rate

Use a documented US Treasury yield series in USD, consistent with the stock and benchmark return currency. Record maturity, quotation convention, source, frequency and conversion method.

A quoted annualized yield is not automatically a daily investment return. Convert it to the analysis frequency according to its quote convention. Align observations by date using a documented rule. Avoid applying one current rate to all historical periods without labelling that simplification.

## 8. Data quality checks

The audit should test:
- unique, ordered dates;
- duplicate observations;
- missing values and missing date coverage;
- nonpositive or implausible prices;
- corporate-action discontinuities;
- currency consistency;
- benchmark/risk-free alignment;
- common observation window;
- sufficient observations for each CAPM regression;
- no silent leakage from future dates.

Keep `data/raw/` immutable. Store audit reports and cleaned outputs in separate folders.
