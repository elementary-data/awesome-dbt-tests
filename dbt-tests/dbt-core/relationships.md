### relationships ([source](https://docs.getdbt.com/docs/build/data-tests))

Verifies the referential integrity between a child and a parent table, typically ensuring foreign key constraints.

**Usage:**

```yaml
 models:
  - name: orders
    columns:
      - name: customer_id
        tests:
          - relationships:
              to: ref('customers')
              field: id
```