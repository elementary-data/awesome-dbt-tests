# Cardinality Equality Test

This page details the `cardinality_equality` test from the dbt-utils package. This test is designed to ensure that two columns, potentially from different models (tables or views), have the same cardinality. Cardinality, in this context, refers to the number of unique values in a column. Ensuring equal cardinality between columns is crucial in scenarios where relationships between datasets rely on matching unique identifiers or attributes.

## How it Works

The `cardinality_equality` test compares the number of unique values in a specified column of one model to the number of unique values in a column of another model. This test is particularly useful for validating data integrity across related datasets, such as ensuring foreign key relationships are correctly maintained.

### Steps and Conditions:

1. **Column and Model Selection**: Identify the column and model you want to test (`from_column` and `model_name`). Also, specify the column and model you want to compare against (`other_column_name` and `other_model_name`).
2. **Cardinality Calculation**: The test calculates the cardinality (number of unique values) for both specified columns.
3. **Comparison**: The cardinalities of the two columns are compared.
4. **Outcome**:
   - **Pass**: If the cardinalities are equal, the test passes, indicating that the columns have the same number of unique values, which is expected in many data integrity scenarios.
   - **Fail**: If the cardinalities are not equal, the test fails. This result suggests a discrepancy in the data that may indicate issues such as missing records, duplication, or improper data linkage.

## Example Usage: B2B SaaS Company

For a B2B SaaS company, maintaining consistent data across user and subscription models is essential for accurate reporting and billing. The `cardinality_equality` test can be applied to ensure that each unique user has a corresponding subscription record and vice versa.

Consider a scenario where the `users` table contains a list of users identified by `user_id`, and the `subscriptions` table tracks subscription details, including a `user_id` to link subscriptions to users.

```yaml
models:
  - name: users
    columns:
      - name: user_id
        tests:
          - dbt_utils.cardinality_equality:
              field: user_id
              to: ref('subscriptions')

  - name: subscriptions
    columns:
      - name: user_id
        tests:
          - dbt_utils.cardinality_equality:
              field: user_id
              to: ref('users')
```

In this example, the `cardinality_equality` test is used to ensure that:
- The `user_id` column in the `users` table has the same cardinality as the `user_id` column in the `subscriptions` table.
- This setup helps verify that each user has a corresponding subscription record, and there are no orphan records in either table.