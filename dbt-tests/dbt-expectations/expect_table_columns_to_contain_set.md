### expect_table_columns_to_contain_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_columns_to_contain_set))

Expect the columns in a model to contain a given list.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_columns_to_contain_set:
          column_list: ["col_a", "col_b"]
          transform: upper # (Optional)
```