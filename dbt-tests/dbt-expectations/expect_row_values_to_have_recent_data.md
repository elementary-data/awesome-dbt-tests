### expect_row_values_to_have_recent_data ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_row_values_to_have_recent_data))

Expect the model to have rows that are at least as recent as the defined interval prior to the current timestamp. Optionally gives the possibility to apply filters on the results.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_row_values_to_have_recent_data:
      datepart: day
      interval: 1
      row_condition: 'id is not null' #optional
```