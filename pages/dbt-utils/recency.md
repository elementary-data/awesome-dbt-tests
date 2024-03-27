# Recency Test

This page outlines the `recency` test from the dbt-utils package. This test is designed to ensure that a timestamp column in your dataset contains data that is at least as recent as a specified date interval. It's particularly useful for monitoring data freshness and ensuring that datasets are updated within expected timeframes, which is crucial for time-sensitive analyses and operational processes.

## How it Works

The `recency` test evaluates a timestamp column to verify that it includes entries that are no older than a defined interval (e.g., within the last day). This helps ensure that the data remains current and relevant.

### Steps and Conditions:

1. **Column and Model Selection**: Identify the model and the timestamp column you wish to test for recency.
2. **Define Recency Criteria**: Specify the `datepart` (e.g., day, hour) and the `interval` that determines how recent the data should be.
3. **Optional Grouping**: If the `group_by_columns` parameter is used, the test checks for recent data within each group defined by the specified columns, rather than across the entire dataset.
4. **Execution**: The test calculates the maximum timestamp in the selected column (or within each group, if grouping is used) and compares it to the current date and time, adjusted by the specified interval.
5. **Outcome**:
   - **Pass**: If the most recent timestamp is within the defined interval from the current date and time, the test passes, indicating that the dataset contains sufficiently recent data.
   - **Fail**: If the most recent timestamp falls outside the defined interval, the test fails. This failure signals that the dataset may not be updating as expected, potentially impacting analyses and decisions based on this data.

## Example Usage: E-commerce Company

For an E-commerce company, keeping track of recent transactions is essential for real-time monitoring of sales performance and inventory management. The `recency` test can be applied to the `transactions` table to validate the `created_at` timestamp column, ensuring that transactions are being recorded and updated daily.

Consider a scenario where the `transactions` table stores records of customer purchases, including a `created_at` column that tracks when each transaction was made.

```yaml
models:
  - name: transactions
    tests:
      - dbt_utils.recency:
          datepart: day
          field: created_at
          interval: 1
```

In this example, the `recency` test ensures that:
- The `created_at` column in the `transactions` table includes transactions that are at most one day old. This validation helps confirm that transaction data is being captured and updated in near real-time, supporting accurate sales monitoring and inventory management.

By applying the `recency` test to critical timestamp columns like `created_at`, the E-commerce company can automatically monitor the freshness of their transaction data. This validation is crucial for maintaining operational efficiency and ensuring that decision-makers have access to the most current data possible.