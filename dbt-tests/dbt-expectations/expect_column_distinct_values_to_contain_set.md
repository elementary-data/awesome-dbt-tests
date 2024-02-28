### expect_column_distinct_values_to_contain_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_distinct_values_to_contain_set))

Expect the set of distinct column values to contain a given set.

In contrast to `expect_column_values_to_be_in_set` this ensures not that all column values are members of the given set but that values from the set must be present in the column.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_distinct_values_to_contain_set:
      value_set: ['a','b']
      quote_values: true # (Optional. Default is 'true'.)
      row_condition: "id is not null" # (Optional)
```