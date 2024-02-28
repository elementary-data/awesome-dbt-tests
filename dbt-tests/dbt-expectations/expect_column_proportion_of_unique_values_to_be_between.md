### expect_column_proportion_of_unique_values_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_proportion_of_unique_values_to_be_between))

Expect the proportion of unique values to be between a min_value value and a max_value value.

For example, in a column containing [1, 2, 2, 3, 3, 3, 4, 4, 4, 4], there are 4 unique values and 10 total values for a proportion of 0.4.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_proportion_of_unique_values_to_be_between:
      min_value: 0  # (Optional)
      max_value: .4 # (Optional)
      group_by: [group_id, other_group_id, ...] # (Optional)
      row_condition: "id is not null" # (Optional)
      strictly: false # (Optional. Default is 'false'. Adds an 'or equal to' to the comparison operator for min/max)
```