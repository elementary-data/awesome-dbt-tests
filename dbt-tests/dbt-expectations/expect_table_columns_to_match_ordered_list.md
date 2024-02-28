### expect_table_columns_to_match_ordered_list ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_columns_to_match_ordered_list))

Expect the columns to exactly match a specified list.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_columns_to_match_ordered_list:
          column_list: ["col_a", "col_b"]
          transform: upper # (Optional)
```