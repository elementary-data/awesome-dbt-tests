### expect_row_values_to_have_data_for_every_n_datepart ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_row_values_to_have_data_for_every_n_datepart))

Expects model to have values for every grouped `date_part`.

For example, this tests whether a model has data for every `day` (grouped on `date_col`) between either:

- The `min`/`max` value of the specified `date_col` (default).
- A specified `test_start_date` and/or `test_end_date`.

*Applies to:* Model, Seed, Source

```yaml
tests:
    - dbt_expectations.expect_row_values_to_have_data_for_every_n_datepart:
        date_col: date_day
        date_part: day # (Optional. Default is 'day')
        row_condition: "id is not null" # (Optional)
        test_start_date: 'yyyy-mm-dd' # (Optional. Replace 'yyyy-mm-dd' with a date. Default is 'None')
        test_end_date: 'yyyy-mm-dd' # (Optional. Replace 'yyyy-mm-dd' with a date. Default is 'None')
        exclusion_condition: statement # (Optional. See details below. Default is 'None')
```