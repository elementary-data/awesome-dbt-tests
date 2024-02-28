### freshness_anomalies ([source](https://docs.elementary-data.com/data-tests/anomaly-detection-tests/freshness-anomalies))

Monitors the freshness of your table over time, comparing the freshness of each bucket within the detection period to the freshness of previous time buckets.

**Usage:**

```yml
models:
  - name: login_events
    tests:
      - elementary.freshness_anomalies:
          timestamp_column: "updated_at"
          # optional - use tags to run elementary tests on a dedicated run
          tags: ["elementary"]
          config:
            # optional - change severity
            severity: warn
```