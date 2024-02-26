### sequential_values ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#sequential_values-source))

This test confirms that a column contains sequential values. It can be used
for both numeric values, and datetime values, as follows:

```yml
 seeds:
  - name: util_even_numbers
    columns:
      - name: i
        tests:
          - dbt_utils.sequential_values:
              interval: 2


  - name: util_hours
    columns:
      - name: date_hour
        tests:
          - dbt_utils.sequential_values:
              interval: 1
              datepart: 'hour'
```

**Args:**

- `interval` (default=1): The gap between two sequential values
- `datepart` (default=None): Used when the gaps are a unit of time. If omitted, the test will check for a numeric gap.

This test supports the `group_by_columns` parameter; see [Grouping in tests](grouping_in_tests.md) for details.