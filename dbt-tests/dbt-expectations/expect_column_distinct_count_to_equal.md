### expect_column_distinct_count_to_equal ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_distinct_count_to_equal))

Expect the number of distinct column values to be equal to a given value.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_distinct_count_to_equal:
      value: 10
      quote_values: true # (Optional. Default is 'true'.)
      group_by: [group_id, other_group_id, ...] # (Optional)
      row_condition: "id is not null" # (Optional)
```