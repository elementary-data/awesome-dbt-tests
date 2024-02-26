### expect_table_column_count_to_equal ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_column_count_to_equal))

Expect the number of columns in a model to be equal to `expected_number_of_columns`.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_column_count_to_equal:
          value: 7
```