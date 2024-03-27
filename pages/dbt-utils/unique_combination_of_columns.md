# Unique Combination of Columns Test

This page details the `unique_combination_of_columns` test from the dbt-utils package. This test verifies that a specific combination of columns within a table or model is unique. It's particularly useful when individual columns are not unique on their own but their combination should be, such as a composite key in a database table.

## How it Works

The `unique_combination_of_columns` test checks that every row in a dataset has a unique combination of values across specified columns. This ensures that, while individual columns might contain duplicate values, the specified group of columns together forms a unique identifier for each row.

### Steps and Conditions:

1. **Column Selection**: Identify the columns whose combined values should be unique within the dataset.
2. **Define Combination**: Specify the columns in the `combination_of_columns` argument to indicate which columns, when combined, should be checked for uniqueness.
3. **Optional Quote Columns**: Use the `quote_columns` argument if any column names need to be quoted (e.g., if they are reserved keywords or include special characters). The default is `false`.
4. **Execution**: The test constructs a virtual column by combining the specified columns and then checks this virtual column for duplicate entries across the dataset.
5. **Outcome**:
   - **Pass**: If no duplicate combinations are found, the test passes, indicating that the dataset adheres to the expected uniqueness constraint for the specified combination of columns.
   - **Fail**: If any duplicate combinations are detected, the test fails. This failure indicates that the dataset violates the expected uniqueness constraint, suggesting issues with data integrity or processing logic that need to be addressed.

## Example Usage: E-commerce Company

A common scenario involves tracking revenue by product for each month, where neither the month nor the product column is unique individually, but their combination should be.

Consider a scenario where the `revenue_by_product_by_month` table stores monthly revenue figures for different products. The table includes `month` and `product` columns, among others.

```yaml
- name: revenue_by_product_by_month
  tests:
    - dbt_utils.unique_combination_of_columns:
        combination_of_columns:
          - month
          - product
```

In this example, the `unique_combination_of_columns` test ensures that:
- Each `month` and `product` combination in the `revenue_by_product_by_month` table is unique. This validation helps guarantee that the table accurately represents revenue figures without duplication, supporting reliable financial analysis and reporting.