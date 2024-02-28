### expect_column_values_to_be_within_n_moving_stdevs ([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_column_values_to_be_within_n_moving_stdevs))

A simple anomaly test based on the assumption that differences between periods in a given time series follow a log-normal distribution.
Thus, we would expect the logged differences (vs N periods ago) in metric values to be within Z sigma away from a moving average.
By applying a list of columns in the `group_by` parameter, you can also test for deviations within a group.

*Applies to:* Column

```yaml
tests:
  - dbt_expectations.expect_column_values_to_be_within_n_moving_stdevs:
      date_column_name: date
      period: day # (Optional. Default is 'day')
      lookback_periods: 1 # (Optional. Default is 1)
      trend_periods: 7 # (Optional. Default is 7)
      test_periods: 14 # (Optional. Default is 14)
      sigma_threshold: 3 # (Optional. Default is 3)
      take_logs: true # (Optional. Default is 'true')
      sigma_threshold_upper: x # (Optional. Replace 'x' with a value. Default is 'None')
      sigma_threshold_lower: y # (Optional. Replace 'y' with a value. Default is 'None')
      take_diffs: true # (Optional. Default is 'true')
      group_by: [group_id] # (Optional. Default is 'None')
```