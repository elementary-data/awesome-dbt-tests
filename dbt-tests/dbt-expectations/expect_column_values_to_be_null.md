### expect_column_values_to_be_null ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_null))

Expect column values to be null.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_null:
      row_condition: "id is not null" # (Optional)
```