### expect_column_values_to_not_match_regex_list ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_not_match_regex_list))

Expect the column entries to be strings that do not match any of a list of regular expressions. Matches can be anywhere in the string.

Optional (keyword) arguments:

- `is_raw` indicates the `regex` pattern is a "raw" string and should be escaped. The default is `False`.
- `flags` is a string of one or more characters that are passed to the regex engine as flags (or parameters). Allowed flags are adapter-specific. A common flag is `i`, for case-insensitive matching. The default is no flags.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_not_match_regex_list:
      regex_list: ["@[^.]*", "&[^.]*"]
      match_on: any # (Optional. Default is 'any', which applies an 'OR' for each regex. If 'all', it applies an 'AND' for each regex.)
      row_condition: "id is not null" # (Optional)
      is_raw: True # (Optional)
      flags: i # (Optional)
```