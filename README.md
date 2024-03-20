# dbt Tests index

This repo is dedicated to gathering, documenting, and sharing a comprehensive collection of dbt (data build tool) tests from various packages.
Our goal is to provide a resource for data professionals looking to ensure data quality, integrity, and reliability within their dbt projects through effective testing.

## 🎯 Repository Objective

This repository aims to create a community-driven collection of dbt tests, covering a wide range of use cases and data scenarios. By compiling tests from various dbt packages and encouraging the addition of real-world examples, we strive to foster a rich resource that enhances data testing practices within the dbt ecosystem.

## 📦 Included tests sources

- **dbt-core** native tests.

dbt packages:
- **[dbt-data-reliability](https://github.com/elementary-data/dbt-data-reliability):** Package by [Elementary](https://www.elementary-data.com/), the dbt native data observability platform.
- **[dbt-expectations](https://github.com/calogica/dbt-expectations):** Inspired by the Great Expectations python library, providing a set of tests for data validation.
- **[dbt-utils](https://github.com/dbt-labs/dbt-utils)**

We welcome contributions covering tests from any dbt package not listed above.


## 🔎 dbt Tests Index

### Data completeness

Tests to validate a dataset has all the expected records and data isn't missing. 

<details>
<summary>
    <b>expect_row_values_to_have_data_for_every_n_datepart</b>
</summary>

The test ensures data completeness by verifying the presence of data for every specified interval unit in your date or timestamp column.
Essentially, it ensures that your dataset has data for every specified interval, such as every month, day, hour, etc., depending on your configuration.

Example use cases:

- **Financial reporting**: You're generating financial reports based on transaction data. By using this test with an interval of 1 for the month, you can ensure that your dataset has entries for every month, ensuring completeness in your financial reporting.
- **Web traffic analysis**: You need to analyze website traffic on an hourly basis. Using this test with an interval of 1 for the hour, you can ensure that your dataset has entries for every hour, allowing you to accurately analyze traffic patterns throughout the day.

**Test configuration**

Expects model to have values for every grouped `date_part`.
For example, this tests whether a model has data for every `day` (grouped on `date_col`) between either:

- The `min`/`max` value of the specified `date_col` (default).
- A specified `test_start_date` and/or `test_end_date`.

*Applies to:* Model, Seed, Source

```yaml
tests:
    - dbt_expectations.expect_row_values_to_have_data_for_every_n_datepart:
        date_col: date_day
        date_part: day # (Optional. Default is 'day')
        row_condition: "id is not null" # (Optional)
        test_start_date: 'yyyy-mm-dd' # (Optional. Replace 'yyyy-mm-dd' with a date. Default is 'None')
        test_end_date: 'yyyy-mm-dd' # (Optional. Replace 'yyyy-mm-dd' with a date. Default is 'None')
        exclusion_condition: statement # (Optional. See details below. Default is 'None')
```

([source](https://github.com/calogica/dbt-expectations/blob/main/README.md#expect_row_values_to_have_data_for_every_n_datepart))

</details>

<details>
<summary>
    <b>at_least_one</b>
</summary>

Asserts that the tested column has at least one value.
The test will probably be useful with grouping by another column. 

Example use cases:
- **Product events** - Some product events include the user email address, others don't. However, there must be an email for at least one event per user. 
The test `at_least_one` can be configured on `user_email` column with `group_by_columns: user_name` configuration. 

**Test configuration**

This test supports the `group_by_columns` parameter.

*Applies to:* Column

```yaml
 models:
  - name: model_name
    columns:
      - name: col_name
        tests:
          - dbt_utils.at_least_one:
              group_by_columns: ['customer_segment']
```

([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#at_least_one))

</details>