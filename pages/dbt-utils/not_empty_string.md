# Not Empty String Test

This page introduces the `not_empty_string` test from the dbt-utils package. This test ensures that a specified column within your dataset does not contain any empty string values (`''`). It's crucial for validating that fields expected to hold data are not left blank, which can be particularly important for columns that are critical to business logic or data integrity.

## How it Works

The `not_empty_string` test scans a specified column to verify that none of its values are empty strings. Optionally, it can also trim whitespace from the values before checking, to ensure that fields filled with only whitespace are also flagged as empty. This helps maintain the quality and completeness of the data.

### Steps and Conditions:

1. **Column Selection**: Identify the column you wish to test for empty string values.
2. **Whitespace Trimming (Optional)**: Decide whether to trim whitespace from the column values before evaluating them. By default, whitespace is trimmed.
3. **Execution**: The test examines each value in the selected column.
4. **Outcome**:
   - **Pass**: If no empty string values are found (considering the whitespace trimming setting), the test passes, indicating that the column contains no blank entries.
   - **Fail**: If any empty string values are present (after optionally trimming whitespace), the test fails. This failure indicates that the column contains blank entries, which may need to be addressed.

## Example Usage: B2B SaaS Company

For a B2B SaaS company, ensuring that customer records are complete and accurate is essential for customer relationship management, billing, and support. The `not_empty_string` test can be applied to the `customers` table to validate the `email_address` column, ensuring it does not contain any blank entries.

Consider a scenario where the `customers` table stores information about each customer, including their `email_address`, which is critical for communication and should not be left blank.

```yaml
models:
  - name: customers
    columns:
      - name: email_address
        tests:
          - dbt_utils.not_empty_string
```

In this example, the `not_empty_string` test ensures that:
- The `email_address` column in the `customers` table contains no empty string values. This validation helps ensure that all customer records have an email address provided, supporting effective communication and service delivery.

Optionally, if the company decides not to trim whitespace (perhaps to catch and address entries that consist solely of whitespace), the test configuration can be adjusted as follows:

```yaml
models:
  - name: customers
    columns:
      - name: email_address
        tests:
          - dbt_utils.not_empty_string:
              trim_whitespace: false
```