### expect_table_column_count_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_column_count_to_be_between))

Expect the number of columns in a model to be between two values.

*Applies to:* Model, Seed, Source

```yaml
tests:
  - dbt_expectations.expect_table_column_count_to_be_between:
      min_value: 1 # (Optional)
      max_value: 4 # (Optional)
```