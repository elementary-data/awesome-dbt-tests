### expect_column_most_common_value_to_be_in_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_most_common_value_to_be_in_set))

Expect the most common value to be within the designated value set

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_most_common_value_to_be_in_set:
      value_set: [0.5]
      top_n: 1
      quote_values: true # (Optional. Default is 'true'.)
      data_type: "decimal" # (Optional. Default is 'decimal')
      strictly: false # (Optional. Default is 'false'. Adds an 'or equal to' to the comparison operator for min/max)
```