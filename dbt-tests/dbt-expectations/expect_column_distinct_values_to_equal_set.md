### expect_column_distinct_values_to_equal_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_distinct_values_to_equal_set))

Expect the set of distinct column values to equal a given set.

In contrast to `expect_column_distinct_values_to_contain_set` this ensures not only that a certain set of values are present in the column but that these and only these values are present.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_distinct_values_to_equal_set:
      value_set: ['a','b','c']
      quote_values: true # (Optional. Default is 'true'.)
      row_condition: "id is not null" # (Optional)
```