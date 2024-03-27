# Sequential Values Test

This page describes the `sequential_values` test from the dbt-utils package. This test is designed to verify that a column contains values in a sequential order, without any gaps. It is versatile and can be applied to both numeric sequences (e.g., IDs, version numbers) and datetime sequences (e.g., log timestamps, scheduled events). Ensuring sequences are uninterrupted can be crucial for data integrity, especially in systems where continuity and order are essential.

## How it Works

The `sequential_values` test checks for the presence of a continuous sequence in a specified column, based on either numeric intervals or datetime intervals. It identifies any gaps in the sequence that do not match the specified interval, indicating missing or out-of-order records.

### Steps and Conditions:

1. **Column Selection**: Identify the column you wish to test for sequential values.
2. **Define Interval**: Specify the `interval` argument to set the expected gap between sequential values. The default is `1`, indicating a continuous sequence with no gaps.
3. **Specify Datepart (if applicable)**: If the sequence is based on datetime values, use the `datepart` argument to define the unit of time for the interval (e.g., hour, day).
4. **Optional Grouping**: If the `group_by_columns` parameter is used, the test evaluates the sequence within each group defined by the specified columns, rather than across the entire dataset.
5. **Execution**: The test calculates the gaps between consecutive values in the selected column (or within each group, if grouping is used) and compares these gaps to the specified interval.
6. **Outcome**:
   - **Pass**: If all gaps between consecutive values match the specified interval, the test passes, indicating that the column contains a perfect sequence.
   - **Fail**: If any gap between consecutive values does not match the specified interval, the test fails. This failure suggests the presence of missing or out-of-order records in the sequence.

## Example Usage: E-commerce Company

For an E-commerce company, ensuring that order IDs are issued in a sequential manner without any gaps is important for tracking orders accurately and maintaining data integrity.

Consider a scenario where the `orders` table stores records of customer orders, including an `order_id` column that is expected to contain sequential numeric values.

```yml
models:
  - name: orders
    columns:
      - name: order_id
        tests:
          - dbt_utils.sequential_values:
              interval: 1
```

In this example, the `sequential_values` test ensures that:
- The `order_id` column in the `orders` table contains values that are sequential with no gaps, indicating that all orders are accounted for and there are no missing records.