### expect_table_row_count_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_row_count_to_be_between))

Expect the number of rows in a model to be between two values.
*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_row_count_to_be_between:
          min_value: 1 # (Optional)
          max_value: 4 # (Optional)
          group_by: [group_id, other_group_id, ...] # (Optional)
          row_condition: "id is not null" # (Optional)
          strictly: false # (Optional. Adds an 'or equal to' to the comparison operator for min/max)
```