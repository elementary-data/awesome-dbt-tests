# Unique Test

This page explains the `unique` test in dbt (data build tool), which is designed to ensure that each value in a specified column or a set of columns within a table is unique. This test is crucial for maintaining data integrity, especially for primary keys or other fields where values must be distinct to correctly identify records.

## How it Works

The `unique` test operates by examining each value in the targeted column(s) of a model (such as a table or view) to verify that no two rows have the same value in that column(s). This is essential for fields that are expected to uniquely identify each record, such as order IDs, customer IDs, or any composite keys.

### Steps and Conditions:

1. **Column Selection**: The test targets a specific column or a combination of columns within a model that you define in your dbt project.
2. **Uniqueness Check**: It scans through the values in the targeted column(s), checking for any duplicates.
3. **Outcome**:
   - **Pass**: If no duplicate values are found, the test passes, confirming that all values in the column(s) are unique.
   - **Fail**: If any duplicate values are detected, the test fails. This result indicates a potential issue with data entry, processing, or integrity that needs to be addressed to ensure each record is uniquely identifiable.

## Example Usage: E-commerce

In an E-commerce platform, ensuring that each order has a unique `order_id` is critical for order tracking, processing, and reporting. The `unique` test can be applied to the `order_id` column in the `orders` table to verify that every order is uniquely identified.

Consider a scenario where the `orders` table stores comprehensive details about customer purchases. It's vital for the operational integrity of the E-commerce platform that each order can be uniquely identified through its `order_id`.

```yaml
models:
  - name: orders
    columns:
      - name: order_id
        tests:
          - unique
```

In this example, the `unique` test is applied to the `order_id` column of the `orders` model. This setup ensures that each `order_id` is distinct, preventing issues such as order duplication, incorrect order processing, or challenges in order tracking and analysis.