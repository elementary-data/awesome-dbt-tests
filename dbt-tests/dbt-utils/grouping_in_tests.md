### Grouping in tests

Certain tests support the optional `group_by_columns` argument to provide more granularity in performing tests. This can be useful when:

- Some data checks can only be expressed within a group (e.g. ID values should be unique within a group but can be repeated between groups)
- Some data checks are more precise when done by group (e.g. not only should table rowcounts be equal but the counts within each group should be equal)

This feature is currently available for the following tests:

- equal_rowcount()
- fewer_rows_than()
- recency()
- at_least_one()
- not_constant()
- sequential_values()
- non_null_proportion()

To use this feature, the names of grouping variables can be passed as a list. For example, to test for at least one valid value by group, the `group_by_columns` argument could be used as follows:

```
  - name: data_test_at_least_one
    columns:
      - name: field
        tests:
          - dbt_utils.at_least_one:
              group_by_columns: ['customer_segment']
```