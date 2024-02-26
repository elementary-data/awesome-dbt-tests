### expect_column_values_to_be_decreasing ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_decreasing))

Expect column values to be decreasing.

If `strictly=True`, then this expectation is only satisfied if each consecutive value is strictly decreasing – equal values are treated as failures.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_decreasing:
      sort_column: col_numeric_a
      row_condition: "id is not null" # (Optional)
      strictly: true # (Optional for comparison operator. Default is 'true' and it uses '<'. If set to 'false', it uses '<='.)
      group_by: [group_id, other_group_id, ...] # (Optional)
```