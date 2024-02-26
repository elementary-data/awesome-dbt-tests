### recency ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#recency-source))

Asserts that a timestamp column in the reference model contains data that is at least as recent as the defined date interval.

**Usage:**

```yaml
 models:
  - name: model_name
    tests:
      - dbt_utils.recency:
          datepart: day
          field: created_at
          interval: 1
```
This test supports the `group_by_columns` parameter; see [Grouping in tests](grouping_in_tests.md) for details.