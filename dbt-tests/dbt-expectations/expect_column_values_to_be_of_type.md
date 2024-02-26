### expect_column_values_to_be_of_type ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_of_type))

Expect a column to be of a specified data type.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_of_type:
      column_type: date
```