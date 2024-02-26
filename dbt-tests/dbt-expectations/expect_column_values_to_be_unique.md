### expect_column_values_to_be_unique ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_unique))

Expect each column value to be unique.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_unique:
      row_condition: "id is not null" # (Optional)
```