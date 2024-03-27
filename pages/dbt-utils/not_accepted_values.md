# Not Accepted Values Test

This page outlines the `not_accepted_values` test from the dbt-utils package. This test is designed to ensure that specific, defined values do not appear in a column within your dataset. It's particularly useful for maintaining data integrity by preventing the inclusion of known incorrect, irrelevant, or otherwise unacceptable values.

## How it Works

The `not_accepted_values` test checks a specified column for the presence of any values from a defined list of unacceptable values. If any of these values are found, the test fails, indicating that the dataset contains data that violates the predefined constraints.

### Steps and Conditions:

1. **Column Selection**: Identify the column you wish to test for unacceptable values.
2. **Define Unacceptable Values**: Specify a list of values that should not appear in the selected column.
3. **Execution**: The test scans the column for any occurrences of the defined unacceptable values.
4. **Outcome**:
   - **Pass**: If none of the unacceptable values are found in the column, the test passes, indicating that the column complies with the defined data quality standards.
   - **Fail**: If any of the unacceptable values are present in the column, the test fails. This failure signals a need to investigate and rectify the source of these values.

## Example Usage: E-commerce Company

For an E-commerce company, ensuring accurate and consistent geographical data is crucial for logistics, shipping calculations, and regional compliance. The `not_accepted_values` test can be applied to the `addresses` table to validate the `city` column, ensuring it does not contain known incorrect city names that could disrupt shipping processes.

Consider a scenario where the `addresses` table stores user shipping information, including a `city` column that should not include fictional or deprecated city names.

```yaml
models:
  - name: addresses
    columns:
      - name: city
        tests:
          - dbt_utils.not_accepted_values:
              values: ['Gotham', 'Metropolis']
```

In this example, the `not_accepted_values` test ensures that:
- The `city` column in the `addresses` table does not contain the values 'Gotham' or 'Metropolis', which are known to be fictional and therefore unacceptable for real shipping addresses.