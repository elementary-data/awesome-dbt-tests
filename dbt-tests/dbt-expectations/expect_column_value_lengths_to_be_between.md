### expect_column_value_lengths_to_be_between ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_value_lengths_to_be_between))

Expect column entries to be strings with length between a min_value value and a max_value value (inclusive).

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_value_lengths_to_be_between:
      min_value: 1 # (Optional)
      max_value: 4 # (Optional)
      row_condition: "id is not null" # (Optional)
      strictly: false # (Optional. Default is 'false'. Adds an 'or equal to' to the comparison operator for min/max)
```