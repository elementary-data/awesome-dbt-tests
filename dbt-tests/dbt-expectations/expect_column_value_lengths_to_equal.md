### expect_column_value_lengths_to_equal ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_value_lengths_to_equal))

Expect column entries to be strings with length equal to the provided value.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_value_lengths_to_equal:
      value: 10
      row_condition: "id is not null" # (Optional)
```