### equality ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#equality-source))

Asserts the equality of two relations. Optionally specify a subset of columns to compare.

**Usage:**

```yaml
 models:
  - name: model_name
    tests:
      - dbt_utils.equality:
          compare_model: ref('other_table_name')
          compare_columns:
            - first_column
            - second_column
```