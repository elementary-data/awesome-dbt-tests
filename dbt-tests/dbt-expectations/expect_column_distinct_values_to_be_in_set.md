### expect_column_distinct_values_to_be_in_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_distinct_values_to_be_in_set))

Expect the set of distinct column values to be contained by a given set.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_distinct_values_to_be_in_set:
      value_set: ['a','b','c','d']
      quote_values: true # (Optional. Default is 'true'.)
      row_condition: "id is not null" # (Optional)
```