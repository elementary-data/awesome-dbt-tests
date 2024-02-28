### not_constant ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#not_constant-source))

Asserts that a column does not have the same value in all rows.

**Usage:**

```yaml
 models:
  - name: model_name
    columns:
      - name: column_name
        tests:
          - dbt_utils.not_constant
```

This test supports the `group_by_columns` parameter; see [Grouping in tests](grouping_in_tests.md) for details.