### expect_column_values_to_not_match_regex ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_not_match_regex))

Expect column entries to be strings that do NOT match a given regular expression. The regex must not match any portion of the provided string. For example, "[at]+" would identify the following strings as expected: "fish”, "dog”, and the following as unexpected: "cat”, "hat”.

Optional (keyword) arguments:

- `is_raw` indicates the `regex` pattern is a "raw" string and should be escaped. The default is `False`.
- `flags` is a string of one or more characters that are passed to the regex engine as flags (or parameters). Allowed flags are adapter-specific. A common flag is `i`, for case-insensitive matching. The default is no flags.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_not_match_regex:
      regex: "[at]+"
      row_condition: "id is not null" # (Optional)
      is_raw: True # (Optional)
      flags: i # (Optional)
```