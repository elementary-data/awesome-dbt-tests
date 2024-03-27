# All Columns Anomalies Test

This page describes the `all_columns_anomalies` test in dbt (data build tool), which is part of the suite of anomaly detection tests provided by Elementary. This test is designed to automatically monitor and detect anomalies at the column level across all columns of a table. It takes into account the data type of each column and executes relevant monitors, ensuring comprehensive data quality and integrity checks.

## How it Works

The `all_columns_anomalies` test performs column-level anomaly detection by analyzing each column's data distribution, trends, and patterns over time. It adjusts its monitoring based on the data type of each column (e.g., numeric, categorical) and applies anomaly detection algorithms to identify unexpected changes or outliers. The test can be configured to exclude specific columns based on prefixes or regular expressions and allows for customization of the anomaly detection sensitivity.

### Steps and Conditions:

1. **Column Analysis**: The test analyzes each column in the specified table, considering its data type and applying appropriate monitoring techniques.
2. **Anomaly Detection**: It employs statistical and machine learning algorithms to detect anomalies in each column's data, based on historical trends and patterns.
3. **Customization**: Users can specify conditions (e.g., `where_expression`), time buckets for analysis, and anomaly sensitivity levels to tailor the test to their specific needs.
4. **Outcome**:
   - **Pass**: If no anomalies are detected according to the specified sensitivity and conditions, the test passes, indicating that the data behaves as expected.
   - **Fail**: If anomalies are detected in any of the columns, the test fails. This result highlights potential issues with data quality, integrity, or unexpected changes in data patterns that require further investigation.

## Example Usage: Fintech

In a Fintech company, monitoring login events is crucial for security and operational analytics. The `all_columns_anomalies` test can be applied to the `login_events` table to ensure that all aspects of login data (e.g., timestamps, event types, country names) maintain expected patterns and do not exhibit anomalies that could indicate security issues or data integrity problems.

Consider a scenario where the `login_events` table tracks user login attempts, including timestamps, event types, and geographical information. It's essential to monitor this data for anomalies to quickly identify and respond to potential security threats or operational issues.

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
          anomaly_sensitivity: 3.5
```

In this example, the `all_columns_anomalies` test is configured to monitor the `login_events` table, focusing on specific event types and excluding logins from an unwanted country. By setting a daily time bucket and adjusting the anomaly sensitivity, the Fintech company can effectively monitor login data for any unusual patterns or outliers, enhancing their security posture and operational efficiency.