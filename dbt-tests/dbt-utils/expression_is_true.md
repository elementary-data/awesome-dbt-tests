### expression_is_true ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#expression_is_true-source))

Asserts that a valid SQL expression is true for all records. This is useful when checking integrity across columns.
Examples:

- Verify an outcome based on the application of basic algebraic operations between columns.
- Verify the length of a column.
- Verify the truth value of a column.

**Usage:**

```yaml
 models:
  - name: model_name
    tests:
      - dbt_utils.expression_is_true:
          expression: "col_a + col_b = total"
```

The macro accepts an optional argument `where` that allows for asserting
the `expression` on a subset of all records.

**Usage:**

```yaml
 models:
  - name: model_name
    tests:
      - dbt_utils.expression_is_true:
          expression: "col_a + col_b = total"
          config:
            where: "created_at > '2018-12-31'"
```

```yaml
version: 2
models:
  - name: model_name
    columns:
      - name: col_a
        tests:
          - dbt_utils.expression_is_true:
              expression: '>= 1'
      - name: col_b
        tests:
          - dbt_utils.expression_is_true:
              expression: '= 1'
              config:
                where: col_a = 1
```