🧹 Voltmart Orders Data Cleaning with PySpark

This project prepares Voltmart’s online orders dataset for downstream demand forecasting by the Machine Learning team.
The raw dataset (orders_data.parquet) contains last year's order activity across multiple U.S. states, and the cleaned output (orders_data_clean.parquet) is structured, standardized, and ready for modeling.

The project applies data engineering best practices using PySpark to ensure quality, consistency, and modeling-readiness.

Voltmart, an electronics e-commerce retailer, requested a cleaned version of its orders dataset to support future demand forecasting models. This project focuses on:

- Filtering invalid or unwanted records

- Standardizing product and category fields

- Extracting new useful features

- Cleaning timestamps and removing nighttime orders

- Parsing U.S. state information from full purchase addresses

- Writing a new modeling-ready parquet dataset

The final output is a clean and structured orders dataset that matches all requirements from the ML team.

**Cleaning Requirements Implemented**

- Remove unwanted datetime ranges

Orders placed between 00:00 and 05:00 (inclusive) are removed.

- Convert timestamp → date

order_date is cast from timestamp to a pure date field.

- Add time_of_day feature

Based on the order’s hour:

morning → 5:00–12:00

afternoon → 12:00–18:00

evening → 18:00–24:00

- Standardize product/category

All product values → lowercase

All category values → lowercase

Remove rows containing "tv" (Voltmart no longer sells TVs)

- Extract purchase state

purchase_state is derived from purchase_address, where the state abbreviation is the second-to-last token.

**PySpark Workflow Summary**

- Load orders dataset from parquet

- Remove nighttime orders

- Construct time_of_day field

- Convert timestamp to date

- Standardize text fields

- Remove discontinued products

- Parse state from address

- Save results to a new parquet directory

The code is fully rewritten, professional, and engineering-oriented.

## Files Included

| File Name | Description |
|----------|-------------|
| `Retail_Orders_Cleaning_PySpark.ipynb` | Main PySpark notebook performing all cleaning operations. |
| `orders_data.parquet` | Raw input dataset containing last year's orders. |
| `orders_data_clean.parquet` | Final cleaned output dataset generated using PySpark. |
| `part-00000-93df7b0d-...snappy.parquet` | Parquet part file inside the cleaned output dataset folder. |
| `.crc file` | Automatic Spark integrity checksum file for the parquet output. |
| `README.md` | Project documentation and explanation. |

**Practical Application**

The cleaned dataset enables:

- Reliable demand forecasting

- Accurate inventory planning

- Enhanced promotional strategy modeling

- Better insights on state-level purchase behavior

