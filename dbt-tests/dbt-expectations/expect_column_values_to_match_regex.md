### expect_column_values_to_match_regex ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_match_regex))

Expect column entries to be strings that match a given regular expression. Valid matches can be found anywhere in the string, for example "[at]+" will identify the following strings as expected: "cat", "hat", "aa", "a", and "t", and the following strings as unexpected: "fish", "dog".

Optional (keyword) arguments:

- `is_raw` indicates the `regex` pattern is a "raw" string and should be escaped. The default is `False`.
- `flags` is a string of one or more characters that are passed to the regex engine as flags (or parameters). Allowed flags are adapter-specific. A common flag is `i`, for case-insensitive matching. The default is no flags.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_match_regex:
      regex: "[at]+"
      row_condition: "id is not null" # (Optional)
      is_raw: True # (Optional)
      flags: i # (Optional)
```