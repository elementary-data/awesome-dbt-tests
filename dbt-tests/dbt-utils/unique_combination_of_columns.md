### unique_combination_of_columns ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#unique_combination_of_columns-source))

Asserts that the combination of columns is unique. For example, the
combination of month and product is unique, however neither column is unique
in isolation.

We generally recommend testing this uniqueness condition by either:

- generating a [surrogate_key](#generate_surrogate_key-source) for your model and testing
the uniqueness of said key, OR
- passing the `unique` test a concatenation of the columns (as discussed [here](https://docs.getdbt.com/docs/building-a-dbt-project/testing-and-documentation/testing/#testing-expressions)).

However, these approaches can become non-perfomant on large data sets, in which
case we recommend using this test instead.

**Usage:**

```yaml
- name: revenue_by_product_by_month
  tests:
    - dbt_utils.unique_combination_of_columns:
        combination_of_columns:
          - month
          - product
```

An optional `quote_columns` argument (`default=false`) can also be used if a column name needs to be quoted.

```yaml
- name: revenue_by_product_by_month
  tests:
    - dbt_utils.unique_combination_of_columns:
        combination_of_columns:
          - month
          - group
        quote_columns: true

```