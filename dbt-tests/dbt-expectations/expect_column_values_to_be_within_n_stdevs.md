### expect_column_values_to_be_within_n_stdevs ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_within_n_stdevs))

Expects (optionally grouped & summed) metric values to be within Z sigma away from the column average

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_within_n_stdevs:
      group_by: group_id # (Optional. Default is 'None')
      sigma_threshold: 3 # (Optional. Default is 3)
```