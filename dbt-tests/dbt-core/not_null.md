### not_null ([source](https://docs.getdbt.com/docs/build/data-tests))

Ensures that the specified column does not contain any null values.

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