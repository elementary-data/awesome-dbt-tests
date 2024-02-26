### event_freshness_anomalies ([source](https://docs.elementary-data.com/data-tests/anomaly-detection-tests/event-freshness-anomalies))

Monitors the freshness of event data over time, focusing on the expected time it takes each event to load by measuring the difference between the event timestamp and when it is loaded to the database.

**Usage:**

```yml
models:
  - name: login_events
    tests:
      - elementary.event_freshness_anomalies:
          event_timestamp_column: "occurred_at"
          update_timestamp_column: "updated_at"
          # optional - use tags to run elementary tests on a dedicated run
          tags: ["elementary"]
          config:
            # optional - change severity
            severity: warn
```