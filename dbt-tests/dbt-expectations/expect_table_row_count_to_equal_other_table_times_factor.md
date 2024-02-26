### expect_table_row_count_to_equal_other_table_times_factor ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_row_count_to_equal_other_table_times_factor))

Expect the number of rows in a model to match another model times a preconfigured factor.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_row_count_to_equal_other_table_times_factor:
          compare_model: ref("other_model")
          factor: 13
          group_by: [col1, col2] # (Optional)
          compare_group_by: [col1, col2] # (Optional)
          row_condition: "id is not null" # (Optional)
          compare_row_condition: "id is not null" # (Optional)
```