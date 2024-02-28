### volume_anomalies ([source](https://docs.elementary-data.com/data-tests/anomaly-detection-tests/volume-anomalies))

Monitors the row count of your table over time per time bucket, comparing the row count of each bucket within the detection period to the row count of previous time buckets.

**Usage:**

```yml
models:
  - name: login_events
    config:
      elementary:
        timestamp_column: "loaded_at"
    tests:
      - elementary.volume_anomalies:
          where_expression: "event_type in ('event_1', 'event_2') and country_name != 'unwanted country'"
          time_bucket:
            period: day
            count: 1
          # optional - use tags to run elementary tests on a dedicated run
          tags: ["elementary"]
          config:
            # optional - change severity
            severity: warn

  - name: users
    # if no timestamp is configured, elementary will monitor without time filtering
    tests:
      - elementary.volume_anomalies:
          tags: ["elementary"]
```