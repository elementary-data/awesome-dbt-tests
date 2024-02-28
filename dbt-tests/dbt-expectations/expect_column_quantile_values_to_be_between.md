### expect_column_quantile_values_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_quantile_values_to_be_between))

Expect specific provided column quantiles to be between provided min_value and max_value values.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_quantile_values_to_be_between:
      quantile: .95
      min_value: 0 # (Optional)
      max_value: 2 # (Optional)
      group_by: [group_id, other_group_id, ...] # (Optional)
      row_condition: "id is not null" # (Optional)
      strictly: false # (Optional. Default is 'false'. Adds an 'or equal to' to the comparison operator for min/max)
```