### not_accepted_values ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#not_accepted_values-source))

Asserts that there are no rows that match the given values.

Usage:

```yaml
 models:
  - name: my_model
    columns:
      - name: city
        tests:
          - dbt_utils.not_accepted_values:
              values: ['Barcelona', 'New York']
```