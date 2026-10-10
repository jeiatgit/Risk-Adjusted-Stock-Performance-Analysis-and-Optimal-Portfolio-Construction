# Scripts

Command-line entry points for reproducible batch execution:
- `audit_data.py`: Audit raw market data for duplicates, missingness, and invalid prices.
- `build_dataset.py`: Execute data ingestion, alignment, and return transformation.
- `run_validation.py`: Execute out-of-sample backtest and generate validation reports.

Scripts call core library services in `src/portfolio_optimizer` and avoid embedding duplicated business formulas.
