# Relationships Test

This page introduces the `relationships` test in dbt (data build tool), which is designed to ensure the referential integrity between two tables in your database. Specifically, this test verifies that foreign key relationships are correctly maintained, meaning that every foreign key in a child table corresponds to a primary key in a parent table. This is crucial for maintaining the consistency and reliability of relational data.

## How it Works

The `relationships` test checks that for every record in a child table (where the test is applied), the value in the specified foreign key column matches a value in the specified primary key column of the parent table. This test helps identify orphaned records in the child table, which are records that reference non-existent values in the parent table, indicating a breach in referential integrity.

### Steps and Conditions:

1. **Identify Foreign Key and Parent Table**: The test targets a specific foreign key column in the child table and identifies the corresponding primary key column in the parent table.
2. **Check for Matching Records**: It scans through each row in the child table, verifying that the foreign key value for each record exists as a primary key value in the parent table.
3. **Outcome**:
   - **Pass**: If every foreign key value in the child table has a corresponding primary key value in the parent table, the test passes, confirming referential integrity.
   - **Fail**: If any foreign key value in the child table does not have a matching primary key value in the parent table, the test fails. This failure indicates the presence of orphaned records, which could lead to data inconsistencies and errors in data processing or analysis.

## Example Usage: Fintech

In a Fintech company, managing the relationship between `transactions` and `customers` is essential for accurate financial reporting and customer management. The `relationships` test can be applied to the `customer_id` column in the `transactions` table to ensure that every transaction is linked to an existing customer in the `customers` table.

Consider a scenario where the `transactions` table records financial transactions made by customers, and each transaction has a `customer_id` that should correspond to an `id` in the `customers` table.

```yaml
models:
  - name: transactions
    columns:
      - name: customer_id
        tests:
          - relationships:
              to: ref('customers')
              field: id
```

In this example, the `relationships` test is applied to the `customer_id` column of the `transactions` model, verifying that each `customer_id` matches an `id` in the `customers` table. This setup ensures that every financial transaction recorded in the `transactions` table is associated with a valid customer, preventing issues such as unattributed transactions or errors in customer-related reporting and analysis.