# Not Null Proportion Test

This page describes the `not_null_proportion` test from the dbt-utils package. This test is designed to ensure that the proportion of non-null values in a specified column falls within a defined acceptable range. It's particularly useful for maintaining data quality by ensuring that critical columns contain a minimal number of null values, which can be essential for analytics, reporting, and operational processes.

## How it Works

The `not_null_proportion` test calculates the proportion of non-null values in a specified column and checks that this proportion is at least a certain threshold (`at_least`) and optionally at most another threshold (`at_most`, defaulting to `1.0` or 100% non-null). This helps ensure that the data meets quality standards regarding completeness.

### Steps and Conditions:

1. **Column Selection**: Identify the column you wish to test for non-null value proportion.
2. **Define Acceptable Range**: Specify the minimum acceptable proportion of non-null values (`at_least`) and optionally the maximum (`at_most`).
3. **Optional Grouping**: If the `group_by_columns` parameter is used, the test evaluates the non-null proportion within each group defined by the specified columns, rather than across the entire dataset.
4. **Execution**: The test calculates the proportion of non-null values in the selected column (or within each group, if grouping is used).
5. **Outcome**:
   - **Pass**: If the proportion of non-null values is within the specified range (at least `at_least` and at most `at_most`), the test passes, indicating that the column meets the defined criteria for data completeness.
   - **Fail**: If the proportion of non-null values falls outside the specified range, the test fails. This failure signals that the column does not meet the required standards for non-null value proportion, indicating potential issues with data collection, processing, or integrity that may need to be addressed.

## Example Usage: Fintech Company

For a Fintech company, ensuring that transaction records are complete is crucial for accurate financial reporting and analysis. The `not_null_proportion` test can be applied to the `transactions` table to validate the `amount` column, ensuring it has a high proportion of non-null values.

Consider a scenario where the `transactions` table stores records of financial transactions, including an `amount` column that is critical for financial calculations and should rarely, if ever, be null.

```yaml
models:
  - name: transactions
    columns:
      - name: amount
        tests:
          - dbt_utils.not_null_proportion:
              at_least: 0.99
```

In this example, the `not_null_proportion` test ensures that:
- The `amount` column in the `transactions` table has at least 99% non-null values. This high threshold for non-null values helps ensure that the financial data is as complete as possible, supporting accurate financial reporting and analysis.