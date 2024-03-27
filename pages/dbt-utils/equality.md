# Equality Test

This page outlines the `equality` test provided by the dbt-utils package. This test is designed to ensure the equality of two datasets, often used to validate that transformations or data migrations have not altered the underlying data unexpectedly.

## How it Works

The `equality` test compares two tables or models to verify that they are identical. It can be applied to the entire dataset or a specified subset of columns. The test performs a row-by-row and column-by-column comparison between the base model (the one on which the test is defined) and a comparison model. The test passes if every corresponding value in the base model matches exactly with the values in the comparison model, indicating that the two relations are equal. If any discrepancy is found, the test fails.

### Steps and Conditions:

1. **Identify Models**: Determine the base model (where the test is applied) and the comparison model (specified in the test parameters).
2. **Subset Columns (Optional)**: If `compare_columns` is specified, limit the comparison to these columns. Otherwise, compare all columns.
3. **Compare Data**: Perform a detailed comparison of the specified columns (or all columns if none are specified) between the two models. This includes checking that:
   - Every row in the base model has a matching row in the comparison model.
   - Every row in the comparison model has a matching row in the base model.
   - The values in each compared column are identical for matching rows.
4. **Pass/Fail**: The test passes only if the two models (or the specified columns within those models) are exactly the same. It fails if any differences are found.

## Example Usage: Fintech

In a Fintech company, ensuring the accuracy of financial data after a migration from one database to another is critical. The `equality` test can be used to validate that transaction data remains consistent before and after the migration.

Consider a scenario where you've migrated transaction data from an old system (`old_transactions`) to a new system (`new_transactions`). You want to ensure that key financial information, such as transaction amounts and account IDs, has been migrated accurately.

```yaml
models:
  - name: new_transactions
    tests:
      - dbt_utils.equality:
          compare_model: ref('old_transactions')
          compare_columns:
            - transaction_amount
            - account_id
```

In this example, the test is applied to the `new_transactions` model, comparing it to the `old_transactions` model. By specifying `transaction_amount` and `account_id` in `compare_columns`, the test focuses on these critical fields, ensuring their values are identical in both the old and new datasets.