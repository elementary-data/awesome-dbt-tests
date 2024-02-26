### expect_column_median_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_median_to_be_between))

Expect the column median to be between a min_value value and a max_value value (inclusive).

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_median_to_be_between:
      min_value: 0
      max_value: 2
      group_by: [group_id, other_group_id, ...] # (Optional)
      row_condition: "id is not null" # (Optional)
      strictly: false # (Optional. Default is 'false'. Adds an 'or equal to' to the comparison operator for min/max)
```