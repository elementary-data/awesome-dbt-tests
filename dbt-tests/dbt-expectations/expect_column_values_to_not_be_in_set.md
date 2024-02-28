### expect_column_values_to_not_be_in_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_not_be_in_set))

Expect each column value not to be in a given set.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_not_be_in_set:
      value_set: ['e','f','g']
      quote_values: true # (Optional. Default is 'true'.)
      row_condition: "id is not null" # (Optional)
```