### expect_column_pair_values_to_be_in_set ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_pair_values_to_be_in_set))

Expect paired values from columns A and B to belong to a set of valid pairs.

Note: value pairs are expressed as lists within lists

*Applies to:* Model, Seed, Source

```yaml
tests:
  - dbt_expectations.expect_column_pair_values_to_be_in_set:
      column_A: col_numeric_a
      column_B: col_numeric_b
      value_pairs_set: [[0, 1], [1, 0], [0.5, 0.5], [0.5, 0.5]]
      row_condition: "id is not null" # (Optional)
```