# Dimension Anomalies Test

This page provides an overview of the `dimension_anomalies` test from the Elementary package. This test is designed to monitor the distribution of values within specified dimensions over time, alerting users to any unexpected changes. It is particularly useful for fields with low cardinality, where sudden shifts in data distribution could indicate data quality issues or significant changes in user behavior.

## How it Works

The `dimension_anomalies` test tracks the frequency of values in one or more dimensions (fields) within a dataset. By analyzing these frequencies over specified time intervals, the test can identify anomalies in the distribution of these values. Anomalies might include a sudden increase or decrease in the occurrence of a particular value, indicating potential issues or changes that warrant further investigation.

### Steps and Conditions:

1. **Select Dimensions**: Identify the dimensions (fields) to monitor. These should be low-cardinality fields where changes in value distribution are meaningful.
2. **Apply Filters**: Use the `where_expression` to include only certain rows in the analysis, based on specific conditions.
3. **Define Time Buckets**: Configure the `time_bucket` to specify the period and count for analyzing data distribution over time. For example, analyzing hourly data over the past 4 hours.
4. **Monitor Changes**: The test analyzes the frequency of each value within the specified dimensions across the defined time buckets, looking for significant deviations from expected patterns.
5. **Alert on Anomalies**: If an unexpected change in distribution is detected, the test triggers an alert. The severity of this alert can be configured.

## Example Usage: Videogame Company

In a Videogame company, monitoring player engagement and behavior is crucial. The `dimension_anomalies` test can be applied to `login_events` to track changes in player activity types and their geographical distribution.

Consider a scenario where you want to monitor the types of events players engage in (`event_type`) and the countries they are playing from (`country_name`), excluding events from an unwanted country and focusing on specific event types.

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
          where_expression: "event_type in ('login', 'logout') and country_name != 'unwanted country'"
          time_bucket:
            period: hour
            count: 4
          tags: ["elementary"]
          config:
            severity: warn
```

In this example, the test is configured to monitor `event_type` and `country_name` dimensions within the `login_events` model. It focuses on `login` and `logout` events, excluding any events from 'unwanted country'. The analysis is performed in 4-hour intervals, looking for any significant changes in the distribution of these events or the countries of origin. A warning is issued if anomalies are detected, allowing the company to quickly respond to potential issues such as a drop in player activity or unexpected shifts in geographical distribution.