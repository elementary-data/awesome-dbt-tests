### expect_column_unique_value_count_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_unique_value_count_to_be_between))

Expect the number of unique values to be between a min_value value and a max_value value.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_unique_value_count_to_be_between:
      min_value: 3 # (Optional)
      max_value: 3 # (Optional)
      group_by: [group_id, other_group_id, ...] # (Optional)
      row_condition: "id is not null" # (Optional)
      strictly: false # (Optional. Default is 'false'. Adds an 'or equal to' to the comparison operator for min/max)
```