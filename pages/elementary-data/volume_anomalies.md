# Volume Anomalies Test

This page introduces the `volume_anomalies` test in dbt (data build tool), which is a part of the anomaly detection tests provided by Elementary. This test is designed to monitor the volume of data in a table, specifically by tracking the row count over time. It compares the row count of each time bucket within a specified detection period against the row count of previous time buckets. This comparison helps in identifying any significant changes or anomalies in data volume that could indicate issues with data collection, processing, or deletion practices.

## How it Works

The `volume_anomalies` test operates by first determining the appropriate time buckets based on a specified timestamp column. It then counts the rows within each time bucket and compares these counts over the detection period to identify any significant deviations from expected volume patterns.

### Steps and Conditions:

1. **Time Bucket Creation**: The test divides the data into time buckets based on a specified timestamp column. If no timestamp column is configured, the test monitors the overall row count without time filtering.
2. **Row Count Comparison**: For each time bucket, the test calculates the row count and compares it with the row counts of previous time buckets.
3. **Anomaly Detection**: The test analyzes these comparisons to identify significant volume anomalies, such as unexpected spikes or drops in the number of rows.
4. **Outcome**:
   - **Pass**: If the row counts remain within expected ranges or follow expected patterns, indicating no significant anomalies, the test passes.
   - **Fail**: If significant deviations in row counts are detected, the test fails. This suggests potential issues in data collection, processing, or deletion that may need investigation.

## Example Usage: Marketplace Company

For a Marketplace company, maintaining accurate and consistent data on user activities, such as login events, is crucial for analyzing user behavior, system performance, and security. The `volume_anomalies` test can be applied to the `login_events` table to monitor the volume of login events recorded over time.

Consider a scenario where the `login_events` table captures details of user login attempts, including the time each event was loaded into the database (`loaded_at`), the type of event, and the country of origin. Monitoring the volume of these events helps in identifying any unusual patterns, such as a sudden increase in login attempts that could indicate a security issue or a drop in events that could suggest a problem with data collection processes.

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
          tags: ["elementary"]
          config:
            severity: warn
```

In this example, the `volume_anomalies` test is configured to monitor the daily volume of specific types of login events, excluding those from an unwanted country. By setting the severity to warn, the Marketplace company can proactively identify and address any significant changes in the volume of login events, ensuring the integrity and reliability of their user activity data.