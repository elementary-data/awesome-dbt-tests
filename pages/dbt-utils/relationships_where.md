# Relationships Where Test

This page details the `relationships_where` test from the dbt-utils package. This test extends the functionality of the standard referential integrity test by allowing for additional conditions (predicates) to be specified. These conditions can exclude certain rows from the test, making it highly useful for handling special cases like test entities, or accounting for delays in data processing pipelines that might temporarily break referential integrity.

## How it Works

The `relationships_where` test checks that a foreign key in one table (the "from" table) correctly references a primary key in another table (the "to" table), similar to the core `relationships` test. However, it adds the ability to include `from_condition` and `to_condition` arguments, which apply filters to the rows considered in both the "from" and "to" tables, respectively.

### Steps and Conditions:

1. **Model and Column Selection**: Identify the model and the foreign key column you wish to test.
2. **Define Referential Target**: Specify the target model and the corresponding primary key column that the foreign key should reference.
3. **Specify Conditions**: Define any conditions to filter rows in both the source and target models. These conditions are applied before checking referential integrity.
4. **Execution**: The test first applies the specified conditions to filter rows in both the source and target models. It then checks that all remaining foreign key values in the source model have corresponding primary key values in the target model.
5. **Outcome**:
   - **Pass**: If all filtered foreign key values in the source model correctly reference primary key values in the target model, the test passes, indicating referential integrity is maintained under the specified conditions.
   - **Fail**: If any filtered foreign key value in the source model does not have a corresponding primary key value in the target model, the test fails. This failure suggests a referential integrity issue within the filtered dataset.

## Example Usage: Marketplace Company

For a Marketplace company, ensuring the integrity of transaction records is crucial. However, there might be a need to exclude transactions created by test accounts or transactions that are very recent and might not yet be fully processed due to ETL delays.

Consider a scenario where the `transactions` table stores transaction records, including a `client_id` foreign key column that references the `id` column in the `clients` table. The company wants to ensure referential integrity but needs to exclude transactions made by a specific test account and only consider client records created after a certain date.

```yaml
models:
  - name: transactions
    columns:
      - name: client_id
        tests:
          - dbt_utils.relationships_where:
              to: ref('clients')
              field: client_id
              from_condition: client_id <> 'test-account-id'
              to_condition: created_date >= '2020-01-01'
```

In this example, the `relationships_where` test ensures that:
- All `client_id` values in the `transactions` table (excluding those belonging to the test account) correctly reference `id` values in the `clients` table.
- Only `clients` records created on or after January 1, 2020, are considered in the test.