### at_least_one ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#at_least_one-source))

Asserts that a column has at least one value.

**Usage:**

```yaml
 models:
  - name: model_name
    columns:
      - name: col_name
        tests:
          - dbt_utils.at_least_one
```

This test supports the `group_by_columns` parameter; see [Grouping in tests](grouping_in_tests.md) for details.