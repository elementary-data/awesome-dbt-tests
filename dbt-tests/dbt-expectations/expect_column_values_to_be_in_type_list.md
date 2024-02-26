### expect_column_values_to_be_in_type_list ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_in_type_list))

Expect a column to be one of a specified type list.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_in_type_list:
      column_type_list: [date, datetime]
```