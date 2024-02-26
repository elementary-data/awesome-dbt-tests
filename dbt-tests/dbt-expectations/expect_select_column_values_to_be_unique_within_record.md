### expect_select_column_values_to_be_unique_within_record ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_select_column_values_to_be_unique_within_record))

Expect the values for each record to be unique across the columns listed. Note that records can be duplicated.

*Applies to:* Model, Seed, Source

```yaml
tests:
  - dbt_expectations.expect_select_column_values_to_be_unique_within_record:
      column_list: ["col_string_a", "col_string_b"]
      ignore_row_if: "any_value_is_missing" # (Optional. Default is 'all_values_are_missing')
      quote_columns: false # (Optional)
      row_condition: "id is not null" # (Optional)
```

Note:

- `all_values_are_missing` (default) means that rows are excluded where *all* of the test columns are `null`
- `any_value_is_missing` means that rows are excluded where *either* of the test columns are `null`