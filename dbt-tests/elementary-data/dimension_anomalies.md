### dimension_anomalies ([source](https://docs.elementary-data.com/data-tests/anomaly-detection-tests/dimension-anomalies))

Monitors the frequency of values in configured dimensions over time, alerting on unexpected changes in distribution. Best configured on low-cardinality fields.

**Usage:**

```yml
models:
  - name: login_events
    config:
      elementary:
        timestamp_column: "loaded_at"
    tests:
      - elementary.dimension_anomalies:
          dimensions:
            - event_type
            - country_name
          where_expression: "event_type in ('event_1', 'event_2') and country_name != 'unwanted country'"
          time_bucket:
            period: hour
            count: 4
          # optional - use tags to run elementary tests on a dedicated run
          tags: ["elementary"]
          config:
            # optional - change severity
            severity: warn

  - name: users
    # if no timestamp is configured, elementary will monitor without time filtering
    tests:
      - elementary.dimension_anomalies:
          dimensions:
            - event_type
          tags: ["elementary"]
```