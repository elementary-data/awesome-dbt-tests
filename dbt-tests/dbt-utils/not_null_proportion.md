### not_null_proportion ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#not_null_proportion-source))

Asserts that the proportion of non-null values present in a column is between a specified range [`at_least`, `at_most`] where `at_most` is an optional argument (default: `1.0`).

**Usage:**

```yaml
 models:
  - name: my_model
    columns:
      - name: id
        tests:
          - dbt_utils.not_null_proportion:
              at_least: 0.95
```

This test supports the `group_by_columns` parameter; see [Grouping in tests](grouping_in_tests.md) for details.