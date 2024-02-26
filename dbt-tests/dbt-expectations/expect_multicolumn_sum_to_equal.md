### expect_multicolumn_sum_to_equal ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_multicolumn_sum_to_equal))

Expects that sum of all rows for a set of columns is equal to a specific value

*Applies to:* Model, Seed, Source

```yaml
tests:
  - dbt_expectations.expect_multicolumn_sum_to_equal:
      column_list: ["col_numeric_a", "col_numeric_b"]
      sum_total: 4
      group_by: [group_id, other_group_id, ...] # (Optional)
      row_condition: "id is not null" # (Optional)
```