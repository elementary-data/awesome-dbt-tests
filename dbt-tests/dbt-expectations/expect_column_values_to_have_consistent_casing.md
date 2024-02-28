### expect_column_values_to_have_consistent_casing ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_have_consistent_casing))

Expect a column to have consistent casing. By setting `display_inconsistent_columns` to true, the number of inconsistent values in the column will be displayed in the terminal whereas the inconsistent values themselves will be returned if the SQL compiled test is run.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_have_consistent_casing:
      display_inconsistent_columns: false # (Optional)
```