### expect_compound_columns_to_be_unique ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_compound_columns_to_be_unique))

Expect that the columns are unique together, e.g. a multi-column primary key.

*Applies to:* Model, Seed, Source

```yaml
tests:
  - dbt_expectations.expect_compound_columns_to_be_unique:
      column_list: ["date_col", "col_string_b"]
      ignore_row_if: "any_value_is_missing" # (Optional. Default is 'all_values_are_missing')
      quote_columns: false # (Optional)
      row_condition: "id is not null" # (Optional)
```

Note:

- `all_values_are_missing` (default) means that rows are excluded where *all* of the test columns are `null`
- `any_value_is_missing` means that rows are excluded where *either* of the test columns are `null`