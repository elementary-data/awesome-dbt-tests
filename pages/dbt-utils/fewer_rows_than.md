# Fewer Rows Than Test

This page describes the `fewer_rows_than` test from the dbt-utils package. This test is designed to ensure that one dataset (model) contains fewer rows than another, specified dataset. It's particularly useful for validating data processing logic that is expected to filter or reduce the number of records, such as when ensuring a summary table has fewer rows than its detailed source table.

## How it Works

The `fewer_rows_than` test compares the row count of the model on which it is applied (the "subject model") against the row count of another specified model (the "compare model"). This test helps in maintaining data integrity by ensuring that data transformations that are supposed to reduce dataset size are working as expected.

### Steps and Conditions:

1. **Model Selection**: Identify the subject model to test and the compare model to which its row count will be compared.
2. **Row Count Comparison**: The test calculates the row count of both the subject model and the compare model.
3. **Optional Grouping**: If the `group_by_columns` parameter is used, the test performs the row count comparison for each group defined by the specified columns, rather than for the entire models.
4. **Outcome**:
   - **Pass**: If the subject model has fewer rows than the compare model (for each group, if grouping is used), the test passes. This indicates that the data transformation logic is correctly reducing the dataset size as expected.
   - **Fail**: If the subject model has the same number of rows as or more rows than the compare model, the test fails. This suggests an issue with the data processing logic that needs to be investigated.

## Example Usage: E-commerce Company

For an E-commerce company, ensuring that the daily summary table of transactions contains fewer rows than the detailed transactions table is crucial for accurate reporting and analysis.

Consider a scenario where the `daily_transactions_summary` table aggregates transaction data from the `transactions` table, summarizing total sales and number of transactions per day.

```yaml
models:
  - name: daily_transactions_summary
    tests:
      - dbt_utils.fewer_rows_than:
          compare_model: ref('transactions')
```

In this example, the `fewer_rows_than` test verifies that the `daily_transactions_summary` table, which aggregates data on a daily basis, indeed has fewer rows than the detailed `transactions` table. This validation is essential to ensure that the summary table accurately reflects aggregated data without inadvertently duplicating or omitting records.

By applying the `fewer_rows_than` test, the E-commerce company can automatically ensure the integrity of their data aggregation processes, supporting reliable business intelligence and decision-making.