### expect_column_pair_values_A_to_be_greater_than_B ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_pair_values_A_to_be_greater_than_B))

Expect values in column A to be greater than column B.

*Applies to:* Model, Seed, Source

```yaml
tests:
  - dbt_expectations.expect_column_pair_values_A_to_be_greater_than_B:
      column_A: col_numeric_a
      column_B: col_numeric_a
      or_equal: True
      row_condition: "id is not null" # (Optional)
```