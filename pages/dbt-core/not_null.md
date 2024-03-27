# Not Null Test

This page provides an overview of the `not_null` test in dbt (data build tool), a fundamental data quality check aimed at ensuring the completeness of your dataset. This test verifies that a specified column within your data model does not contain any null (missing or undefined) values.

## How it Works

The `not_null` test operates by scanning each row in the specified column of a model (such as a table or view) to check for the presence of null values. The primary goal is to ensure that every record in the column has a defined value, which is crucial for maintaining the integrity and reliability of your data, especially for key fields that are critical to your business logic and analyses.

### Steps and Conditions:

1. **Column Selection**: The test targets a specific column within a model that you define in your dbt project.
2. **Null Value Check**: It systematically examines each row in the targeted column to identify any null values.
3. **Outcome**:
   - **Pass**: If no null values are found, the test passes, indicating that the column is fully populated with valid data.
   - **Fail**: If any null values are detected, the test fails. This outcome signals a potential issue with data collection, entry, or processing that needs to be addressed to ensure data quality.

## Example Usage: E-commerce

In an E-commerce platform, maintaining accurate and complete order information is essential for order processing, inventory management, and customer service. Using the `not_null` test to validate the `order_id` column in the `orders` table ensures that every order recorded in the system has a unique identifier, which is crucial for tracking and managing orders efficiently.

Consider a scenario where the `orders` table stores detailed information about customer purchases. It's vital that each entry in this table has a non-null `order_id` to uniquely identify the order.

```yaml
models:
  - name: orders
    columns:
      - name: order_id
        tests:
          - not_null
```

In this example, the `not_null` test is applied to the `order_id` column of the `orders` model. This setup ensures that the E-commerce platform's database does not contain any orders missing an `order_id`. This validation step is critical for preventing issues such as order duplication, misprocessing, or difficulties in linking orders to customers and inventory items.