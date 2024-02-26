### expect_column_values_to_not_match_like_pattern_list ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_not_match_like_pattern_list))

Expect the column entries to be strings that do not match any of a list of SQL `like` patterns.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_not_match_like_pattern_list:
      like_pattern_list: ["%@%", "%&%"]
      match_on: any # (Optional. Default is 'any', which applies an 'OR' for each pattern. If 'all', it applies an 'AND' for each regex.)
      row_condition: "id is not null" # (Optional)
```