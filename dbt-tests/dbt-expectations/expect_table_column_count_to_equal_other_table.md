### expect_table_column_count_to_equal_other_table ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_column_count_to_equal_other_table))

Expect the number of columns in a model to match another model.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_column_count_to_equal_other_table:
          compare_model: ref("other_model")
```