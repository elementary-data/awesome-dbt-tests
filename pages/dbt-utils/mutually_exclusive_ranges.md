# Mutually Exclusive Ranges Test

This page details the `mutually_exclusive_ranges` test from the dbt-utils package. This test ensures that for any two rows in a dataset, the ranges defined by a lower and an upper bound do not overlap. It's essential for validating scenarios where records should not intersect in time or any other continuous scale, such as ensuring non-overlapping booking periods or validating age brackets.

## How it Works

The `mutually_exclusive_ranges` test checks that the ranges between a specified lower and upper bound column in a dataset do not overlap for any two rows. This is crucial for maintaining data integrity in scenarios where records represent periods or ranges that should be distinct and non-intersecting.

### Steps and Conditions:

1. **Bound Columns Specification**: Identify the columns that represent the lower and upper bounds of the range. These columns must not contain null values.
2. **Partitioning (Optional)**: If the test should apply within subsets of the data (e.g., per customer or per item), specify a column to partition by.
3. **Gap Handling**: Specify how gaps between ranges should be handled (`not_allowed`, `allowed`, `required`), depending on the data integrity requirements.
4. **Zero-Length Ranges**: Determine whether ranges that start and end on the same value are permissible.
5. **Outcome**:
   - **Pass**: If all ranges are mutually exclusive according to the specified conditions, the test passes, indicating that the dataset adheres to the expected constraints.
   - **Fail**: If any ranges overlap (contrary to the specified conditions), the test fails, highlighting a potential issue with the data that may require correction.

## Example Usage: Marketplace Company

For a Marketplace company, ensuring that product listings do not have overlapping availability periods is critical for avoiding double bookings or conflicts in reservation schedules.

Consider a scenario where the `listings_availability` table tracks the start and end dates (`available_from`, `available_to`) for each product listing (`listing_id`), partitioned by `product_id`.

```yaml
models:
  - name: listings_availability
    tests:
      - dbt_utils.mutually_exclusive_ranges:
          lower_bound_column: available_from
          upper_bound_column: available_to
          partition_by: product_id
          gaps: required
```

In this example, the `mutually_exclusive_ranges` test verifies that:
- For each product, the availability periods of its listings do not overlap.
- There must be a gap between the availability periods of consecutive listings for the same product, ensuring clear demarcation of availability.