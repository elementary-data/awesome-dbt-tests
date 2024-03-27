# Accepted Range Test

This page describes the `accepted_range` test from the dbt-utils package, a versatile tool for ensuring that the values of a specific column in your database fall within an expected range. This test can be applied to any data type that supports comparison operations, making it a fundamental check for data quality and integrity across various scenarios.

## How it Works

The `accepted_range` test asserts that the values of a column are within a specified minimum and maximum value. This range can be defined to be either inclusive or exclusive of the boundary values. The test allows for flexibility in defining the range, as you can specify either or both `min_value` and `max_value`, and even compare a column's values against another column or a scalar value like the current date. This makes it suitable for a wide array of data validation needs, from ensuring IDs are positive to verifying dates are in the past.

### Steps and Conditions:

1. **Range Specification**: Define the acceptable range for the column values with `min_value` and/or `max_value`. The range can be made inclusive or exclusive.
2. **Comparison Execution**: The test compares each value in the specified column against the defined range.
3. **Filtering (Optional)**: A `where` argument can be provided to apply the test to a subset of records, allowing for more targeted validation.
4. **Outcome**:
   - **Pass**: If all column values fall within the specified range, the test passes, indicating the data meets the defined criteria.
   - **Fail**: If any column value falls outside the specified range, the test fails, signaling a potential issue with the data that may require correction.

## Example Usage: E-commerce Company

For an E-commerce company, maintaining accurate and consistent data on user activities and transactions is crucial. The `accepted_range` test can be applied to various columns in the `users` and `orders` tables to ensure data integrity.

Consider a scenario where the `users` table tracks user IDs, account creation dates, and the number of returned orders, while the `orders` table records the number of web sessions and orders per user.

```yaml
models:
  - name: users
    columns:
      - name: user_id
        tests:
          - dbt_utils.accepted_range:
              min_value: 1
              inclusive: true

      - name: account_created_at
        tests:
          - dbt_utils.accepted_range:
              max_value: "getdate()"

      - name: num_returned_orders
        tests:
          - dbt_utils.accepted_range:
              min_value: 0
              max_value: "num_orders"

  - name: orders
    columns:
      - name: num_web_sessions
        tests:
          - dbt_utils.accepted_range:
              min_value: 0
              inclusive: false
              config:
                where: "num_orders > 0"
```

In this example, the `accepted_range` test is used to ensure that:
- User IDs are positive integers.
- Account creation dates are not in the future.
- The number of returned orders does not exceed the total number of orders.
- The number of web sessions is positive for users with at least one order.