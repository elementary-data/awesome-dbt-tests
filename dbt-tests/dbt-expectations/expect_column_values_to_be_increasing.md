### expect_column_values_to_be_increasing ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_increasing))

Expect column values to be increasing.

If `strictly: True`, then this expectation is only satisfied if each consecutive value is strictly increasing – equal values are treated as failures.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_increasing:
      sort_column: date_day
      row_condition: "id is not null" # (Optional)
      strictly: true # (Optional for comparison operator. Default is 'true', and it uses '>'. If set to 'false' it uses '>='.)
      group_by: [group_id, other_group_id, ...] # (Optional)
```