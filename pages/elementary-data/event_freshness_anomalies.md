# Event Freshness Anomalies Test

This page outlines the `event_freshness_anomalies` test in dbt (data build tool), provided by Elementary. This test is specifically designed to monitor the freshness of event data, ensuring that events are loaded into the database within an expected timeframe. It measures the difference between the event's occurrence time and its load time into the database, helping to identify delays or anomalies in data processing and ingestion.

## How it Works

The `event_freshness_anomalies` test calculates the time difference between when an event occurred (`event_timestamp_column`) and when it was updated or loaded into the database (`update_timestamp_column`). By monitoring this time difference, the test can detect significant deviations from normal processing times, indicating potential issues with data ingestion pipelines or systems capturing the events.

### Steps and Conditions:

1. **Timestamp Columns Identification**: The test requires specification of the columns that record the event's occurrence time and the time it was loaded into the database.
2. **Time Difference Calculation**: For each event, it calculates the time difference between the occurrence and load times.
3. **Anomaly Detection**: The test analyzes these time differences over a period to identify any significant anomalies or deviations from expected patterns.
4. **Outcome**:
   - **Pass**: If the time differences remain within expected ranges or patterns, the test passes, indicating that event data is being loaded with expected freshness.
   - **Fail**: If significant anomalies or deviations in the time differences are detected, the test fails, signaling potential issues in the data processing or ingestion pipeline that may affect data freshness.

## Example Usage: B2B SaaS Company

For a B2B SaaS company, ensuring that usage data is timely processed and available is crucial for operational monitoring, billing, and customer support. The `event_freshness_anomalies` test can be applied to the `login_events` table to monitor the freshness of login event data, crucial for understanding customer engagement and system performance.

Consider a scenario where the `login_events` table records each user's login attempts, including the time the login occurred (`occurred_at`) and when the event was loaded into the database (`updated_at`). Monitoring the freshness of these login events helps ensure that the data reflects recent user activities accurately.

```yml
models:
  - name: login_events
    tests:
      - elementary.event_freshness_anomalies:
          event_timestamp_column: "occurred_at"
          update_timestamp_column: "updated_at"
          tags: ["elementary"]
          config:
            severity: warn
```

In this example, the `event_freshness_anomalies` test is configured to monitor the time difference between `occurred_at` and `updated_at` for each login event. By setting the severity to warn, the B2B SaaS company can identify and address delays in data processing or ingestion, ensuring that the login event data remains fresh and reflective of current user activities. This is essential for maintaining accurate operational monitoring and customer engagement metrics.