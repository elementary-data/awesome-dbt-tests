### unique ([source](https://docs.getdbt.com/docs/build/data-tests))

Checks if the values in a specific column or a combination of columns are unique.

**Usage:**

```yaml
 models:
  - name: orders
    columns:
      - name: order_id
        tests:
          - unique
          - not_null
```