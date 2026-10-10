# Data Directory

- `raw/`: immutable copies of downloaded source files.
- `interim/`: temporary or partially transformed data, if needed.
- `processed/`: validated, aligned data products consumed by the analytical pipeline.

Do not commit secrets or data that the provider's terms do not permit redistribution. Record data source, retrieval date, adjustment convention, currency and transformations in the audit report. Never silently overwrite raw files.

The repository blueprint does not include a market dataset yet. Do not create fake sample market data and label it real.
