### cardinality_equality ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#cardinality_equality-source))

Asserts that values in a given column have exactly the same cardinality as values from a different column in a different model.

**Usage:**

```yaml
 models:
  - name: model_name
    columns:
      - name: from_column
        tests:
          - dbt_utils.cardinality_equality:
              field: other_column_name
              to: ref('other_model_name')
```