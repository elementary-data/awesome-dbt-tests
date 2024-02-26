### expect_table_aggregation_to_equal_other_table ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_table_aggregation_to_equal_other_table))

Except an (optionally grouped) expression to match the same (or optionally other) expression in a different table.

*Applies to:* Model, Seed, Source

Simple:

```yaml
tests:
  - dbt_expectations.expect_table_aggregation_to_equal_other_table:
      expression: sum(col_numeric_a)
      compare_model: ref("other_model")
      group_by: [idx]
```

More complex:

```yaml
tests:
  - dbt_expectations.expect_table_aggregation_to_equal_other_table:
      expression: count(*)
      compare_model: ref("other_model")
      compare_expression: count(distinct id)
      group_by: [date_column]
      compare_group_by: [some_other_date_column]
```

or:

```yaml
tests:
  - dbt_expectations.expect_table_aggregation_to_equal_other_table:
      expression: max(column_a)
      compare_model: ref("other_model")
      compare_expression: max(column_b)
      group_by: [date_column]
      compare_group_by: [some_other_date_column]
      row_condition: some_flag=true
      compare_row_condition: some_flag=false
```

**Note**: You can also express a **tolerance** factor, either as an absolute tolerable difference, `tolerance`, or as a tolerable % difference `tolerance_percent` expressed as a decimal (i.e 0.05 for 5%).