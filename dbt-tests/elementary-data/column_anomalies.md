### column_anomalies ([source](https://docs.elementary-data.com/data-tests/anomaly-detection-tests/column-anomalies))

Executes column-level monitors and anomaly detection on all columns of the table, checking data type of each column and executing relevant monitors. Excludes columns based on exclude_prefix/exclude_regexp.

**Usage:**

```yml

models:
  - name: login_events
    config:
      elementary:
        timestamp_column: 'loaded_at'
    columns:
      - name: user_name
        tests:
          - elementary.column_anomalies:
              column_anomalies:
                - missing_count
                - min_length
              where_expression: "event_type in ('event_1', 'event_2') and country_name != 'unwanted country'"
              time_bucket:
                period: day
                count: 1
              tags: ['elementary']

  - name: users
    ## if no timestamp is configured, elementary will monitor without time filtering
    tests:
        elementary.volume_anomalies
          tags: ['elementary']
    columns:
      - name: user_id
        tests:
          - elementary.column_anomalies:
              tags: ['elementary']
              timestamp_column: 'updated_at'
              where_expression: "event_type in ('event_1', 'event_2') and country_name != 'unwanted country'"
              time_bucket:
                period: < time period >
                count: < number of periods >
      - name: user_name
        tests:
          - elementary.column_anomalies:
              column_anomalies:
                - missing_count
                - min_length
              tags: ['elementary']
```