# Freshness Anomalies Test

This page details the `freshness_anomalies` test in dbt (data build tool), which is part of the anomaly detection suite provided by Elementary. This test is aimed at monitoring the overall freshness of a table's data over time. It does this by comparing the freshness (i.e., how recently data has been updated) of each time bucket within a specified detection period against the freshness of previous time buckets. This helps in identifying any significant deviations or anomalies that could indicate issues with data ingestion or updating processes.

## How it Works

The `freshness_anomalies` test operates by first identifying the timestamp column that indicates when each record was last updated. It then divides the data into time buckets based on this timestamp and compares the freshness of these buckets over the detection period. By analyzing these comparisons, the test can detect anomalies in data freshness, such as unexpected delays in data updates or ingestion.

### Steps and Conditions:

1. **Timestamp Column Identification**: The test requires you to specify the column that records when each data record was last updated.
2. **Time Bucket Comparison**: Data is divided into time buckets based on the specified timestamp column. The test then compares the freshness of current time buckets against previous ones.
3. **Anomaly Detection**: By examining these comparisons, the test identifies any significant deviations from expected freshness patterns.
4. **Outcome**:
   - **Pass**: If the freshness of data remains consistent with historical patterns, the test passes, indicating no detected anomalies in data freshness.
   - **Fail**: If significant deviations in data freshness are detected, the test fails. This outcome suggests potential issues in the data updating or ingestion processes that need to be addressed.

## Example Usage: E-commerce Company

For an E-commerce company, keeping product, customer, and transaction data up-to-date is crucial for accurate reporting, inventory management, and customer service. The `freshness_anomalies` test can be applied to the `login_events` table to ensure that login event data, which is critical for analyzing user engagement and system performance, remains fresh.

Consider a scenario where the `login_events` table tracks user login activities, including when each login event was last updated (`updated_at`). Monitoring the freshness of this data helps in ensuring that the system accurately reflects the most recent user activities.

```yml
models:
  - name: login_events
    tests:
      - elementary.freshness_anomalies:
          timestamp_column: "updated_at"
          tags: ["elementary"]
          config:
            severity: warn
```

In this example, the `freshness_anomalies` test is configured to monitor the `updated_at` timestamp column of the `login_events` table. By setting the severity to warn, the E-commerce company can proactively identify and investigate any significant delays or anomalies in the updating of login event data. This ensures that the data used for user engagement analysis and system performance monitoring remains accurate and up-to-date.