### fewer_rows_than ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#fewer_rows_than-source))

Asserts that the respective model has fewer rows than the model being compared.

Usage:

```yaml
 models:
  - name: model_name
    tests:
      - dbt_utils.fewer_rows_than:
          compare_model: ref('other_table_name')
```

This test supports the `group_by_columns` parameter; see [Grouping in tests](grouping_in_tests.md) for details.