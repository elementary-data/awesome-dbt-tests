### all_columns_anomalies ([source](https://docs.elementary-data.com/data-tests/anomaly-detection-tests/all-columns-anomalies))

Executes column-level monitors and anomaly detection on all columns of the table, checking data type of each column and executing relevant monitors. Excludes columns based on exclude_prefix/exclude_regexp.

**Usage:**

```yml
models:
  - name: login_events
    config:
      elementary:
        timestamp_column: "loaded_at"
    tests:
      - elementary.all_columns_anomalies:
          where_expression: "event_type in ('event_1', 'event_2') and country_name != 'unwanted country'"
          time_bucket:
            period: day
            count: 1
          tags: ["elementary"]
          # optional - change global sensitivity
          anomaly_sensitivity: 3.5
```