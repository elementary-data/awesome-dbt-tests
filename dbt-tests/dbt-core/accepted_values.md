### accepted_values ([source](https://docs.getdbt.com/docs/build/data-tests))

Ensures that a column's values are within a predefined set of acceptable values.

**Usage:**

```yaml
 models:
  - name: orders
    columns:
        - name: status
          tests:
            - accepted_values:
                values: ['placed', 'shipped', 'completed', 'returned']

```