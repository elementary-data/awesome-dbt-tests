# Accepted Values Test

This page details the `accepted_values` test in dbt (data build tool), designed to ensure data integrity by verifying that the values in a specific column match a predefined set of acceptable values. This test is crucial for maintaining consistency in categorical data, such as status codes, types, or any other field where only certain values are valid.

## How it Works

The `accepted_values` test checks a specified column within a model (such as a table or view) to ensure that every entry in that column is within a set of predefined acceptable values. This test helps enforce data validation rules by identifying records that contain unexpected or invalid values, which could indicate data entry errors, processing issues, or other data quality problems.

### Steps and Conditions:

1. **Column and Values Selection**: The test targets a specific column and compares each of its values against a predefined list of acceptable values.
2. **Value Validation**: It scans through each row in the targeted column, checking if the value is part of the acceptable values list.
3. **Outcome**:
   - **Pass**: If all values in the column are found within the acceptable values list, the test passes, confirming that the column's data adheres to the expected constraints.
   - **Fail**: If any value in the column is not in the list of acceptable values, the test fails. This result highlights the presence of unexpected or invalid data that needs to be investigated and corrected.

## Example Usage: Marketplace

In a Marketplace platform, managing the status of transactions accurately is essential for operational efficiency and customer satisfaction. The `accepted_values` test can be applied to the `status` column in the `transactions` table to ensure that each transaction's status is correctly recorded and falls within the expected range of values.

Consider a scenario where the `transactions` table tracks the lifecycle of customer transactions, and the `status` column indicates the current state of each transaction. It's crucial that the status of each transaction is accurately captured using a consistent set of predefined statuses.

```yaml
models:
  - name: transactions
    columns:
        - name: status
          tests:
            - accepted_values:
                values: ['placed', 'shipped', 'completed', 'returned']
```

In this example, the `accepted_values` test is applied to the `status` column of the `transactions` model. By specifying the acceptable values as `['placed', 'shipped', 'completed', 'returned']`, this setup ensures that every transaction in the Marketplace platform is categorized correctly. This validation is critical for processes such as transaction fulfillment, customer notifications, and returns management, as it prevents issues arising from incorrect transaction statuses.