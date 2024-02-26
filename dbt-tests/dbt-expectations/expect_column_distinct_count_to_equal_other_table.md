### expect_column_distinct_count_to_equal_other_table ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_distinct_count_to_equal_other_table))

Expect the number of distinct column values to be equal to number of distinct values in another model.

*Applies to:* Model, Column, Seed, Source

This can be applied to a model:

```yaml
models: # or seeds:
  - name: my_model_1
    tests:
      - dbt_expectations.expect_column_distinct_count_to_equal_other_table:
          column_name: col_1
          compare_model: ref("my_model_2")
          compare_column_name: col_2
          row_condition: "id is not null" # (Optional)
          compare_row_condition: "id is not null" # (Optional)
```

or at the column level:

```yaml
models: # or seeds:
  - name: my_model_1
    columns:
      - name: col_1
        tests:
          - dbt_expectations.expect_column_distinct_count_to_equal_other_table:
              compare_model: ref("my_model_2")
              compare_column_name: col_2
              row_condition: "id is not null" # (Optional)
              compare_row_condition: "id is not null" # (Optional)
```

If `compare_model` or `compare_column_name` are no specified, `model` and `column_name` are substituted. So, one could compare distinct counts of two different columns in the same model, or identically named columns in separate models etc.