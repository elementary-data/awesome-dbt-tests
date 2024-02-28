### expect_table_row_count_to_equal ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_row_count_to_equal))

Expect the number of rows in a model to be equal to `expected_number_of_rows`.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name: my_model
    tests:
      - dbt_expectations.expect_table_row_count_to_equal:
          value: 4
          group_by: [group_id, other_group_id, ...] # (Optional)
          row_condition: "id is not null" # (Optional)
```