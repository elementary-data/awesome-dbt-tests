### expect_grouped_row_values_to_have_recent_data ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_grouped_row_values_to_have_recent_data))

Expect the model to have **grouped** rows that are at least as recent as the defined interval prior to the current timestamp.
Use this to test whether there is recent data for each grouped row defined by `group_by` (which is a list of columns) and a `timestamp_column`. Optionally gives the possibility to apply filters on the results.

*Applies to:* Model, Seed, Source

```yaml
models: # or seeds:
  - name : my_model
    tests :
      - dbt_expectations.expect_grouped_row_values_to_have_recent_data:
          group_by: [group_id]
          timestamp_column: date_day
          datepart: day
          interval: 1
          row_condition: "id is not null" #optional
      # or also:
      - dbt_expectations.expect_grouped_row_values_to_have_recent_data:
          group_by: [group_id, other_group_id]
          timestamp_column: date_day
          datepart: day
          interval: 1
          row_condition: "id is not null" #optional
```