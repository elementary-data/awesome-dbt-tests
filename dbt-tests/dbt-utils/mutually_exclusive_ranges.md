### mutually_exclusive_ranges ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#mutually_exclusive_ranges-source))

Asserts that for a given lower_bound_column and upper_bound_column,
the ranges between the lower and upper bounds do not overlap with the ranges
of another row.

**Usage:**

```yaml
 models:
  # test that age ranges do not overlap
  - name: age_brackets
    tests:
      - dbt_utils.mutually_exclusive_ranges:
          lower_bound_column: min_age
          upper_bound_column: max_age
          gaps: not_allowed

  # test that each customer can only have one subscription at a time
  - name: subscriptions
    tests:
      - dbt_utils.mutually_exclusive_ranges:
          lower_bound_column: started_at
          upper_bound_column: ended_at
          partition_by: customer_id
          gaps: required

  # test that each customer can have subscriptions that start and end on the same date
  - name: subscriptions
    tests:
      - dbt_utils.mutually_exclusive_ranges:
          lower_bound_column: started_at
          upper_bound_column: ended_at
          partition_by: customer_id
          zero_length_range_allowed: true
```

**Args:**

- `lower_bound_column` (required): The name of the column that represents the
lower value of the range. Must be not null.
- `upper_bound_column` (required): The name of the column that represents the
upper value of the range. Must be not null.
- `partition_by` (optional): If a subset of records should be mutually exclusive
(e.g. all periods for a single subscription_id are mutually exclusive), use this
argument to indicate which column to partition by. `default=none`
- `gaps` (optional): Whether there can be gaps are allowed between ranges.
`default='allowed', one_of=['not_allowed', 'allowed', 'required']`
- `zero_length_range_allowed` (optional): Whether ranges can start and end on the same date.
`default=False`

**Note:** Both `lower_bound_column` and `upper_bound_column` should be not null.
If this is not the case in your data source, consider passing a coalesce function
to the `lower_` and `upper_bound_column` arguments, like so:

```yaml
 models:
  - name: subscriptions
    tests:
      - dbt_utils.mutually_exclusive_ranges:
          lower_bound_column: coalesce(started_at, '1900-01-01')
          upper_bound_column: coalesce(ended_at, '2099-12-31')
          partition_by: customer_id
          gaps: allowed
```

<details>
<summary>Additional `gaps` and `zero_length_range_allowed` examples</summary>
  **Understanding the `gaps` argument:**

  Here are a number of examples for each allowed `gaps` argument.

- `gaps: not_allowed`: The upper bound of one record must be the lower bound of
  the next record.

  | lower_bound | upper_bound |
  |-------------|-------------|
  | 0           | 1           |
  | 1           | 2           |
  | 2           | 3           |

- `gaps: allowed` (default): There may be a gap between the upper bound of one
  record and the lower bound of the next record.

  | lower_bound | upper_bound |
  |-------------|-------------|
  | 0           | 1           |
  | 2           | 3           |
  | 3           | 4           |

- `gaps: required`: There must be a gap between the upper bound of one record and
  the lower bound of the next record (common for date ranges).

  | lower_bound | upper_bound |
  |-------------|-------------|
  | 0           | 1           |
  | 2           | 3           |
  | 4           | 5           |

  **Understanding the `zero_length_range_allowed` argument:**
  Here are a number of examples for each allowed `zero_length_range_allowed` argument.

- `zero_length_range_allowed: false`: (default) The upper bound of each record must be greater than its lower bound.

  | lower_bound | upper_bound |
  |-------------|-------------|
  | 0           | 1           |
  | 1           | 2           |
  | 2           | 3           |

- `zero_length_range_allowed: true`: The upper bound of each record can be greater than or equal to its lower bound.

  | lower_bound | upper_bound |
  |-------------|-------------|
  | 0           | 1           |
  | 2           | 2           |
  | 3           | 4           |

</details>