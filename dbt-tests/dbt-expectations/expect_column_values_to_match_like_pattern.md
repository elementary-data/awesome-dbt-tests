### expect_column_values_to_match_like_pattern ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_match_like_pattern))

Expect column entries to be strings that match a given SQL `like` pattern.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_match_like_pattern:
      like_pattern: "%@%"
      row_condition: "id is not null" # (Optional)
```