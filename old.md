
| Package | Test Name | Test Description | Applies To |
| --- | ---| --- | --- |
| dbt-core | [unique](/dbt-tests/dbt-core/unique.md) | Checks if the values in a specific column or a combination of columns are unique. | Column |
|  dbt-core | [not_null](/dbt-tests/dbt-core/not_null.md) | Ensures that the specified column does not contain any null values. | Column |
|  dbt-core | [relationships](/dbt-tests/dbt-core/relationships.md) | Verifies the referential integrity between a child and a parent table, typically ensuring foreign key constraints. | Column |
|  dbt-core | [accepted_values](/dbt-tests/dbt-core/accepted_values.md) | Ensures that a column's values are within a predefined set of acceptable values. | Column |
|  dbt-utils | [equal_rowcount](/dbt-tests/dbt-utils/equal_rowcount.md) | Asserts that two relations have the same number of rows. | Model |
|  dbt-utils | [fewer_rows_than](/dbt-tests/dbt-utils/fewer_rows_than.md) | Asserts that the respective model has fewer rows than the model being compared. | Model |
|  dbt-utils | [equality](/dbt-tests/dbt-utils/equality.md) | Asserts the equality of two relations. Optionally specify a subset of columns to compare. | Model |
|  dbt-utils | [expression_is_true](/dbt-tests/dbt-utils/expression_is_true.md) | Asserts that a valid SQL expression is true for all records. Useful for checking integrity across columns, verifying outcomes based on algebraic operations, verifying column length, or the truth value of a column. | Model, Column |
|  dbt-utils | [recency](/dbt-tests/dbt-utils/recency.md) | Asserts that a timestamp column in the reference model contains data that is at least as recent as the defined date interval. | Model |
|  dbt-utils | [at_least_one](/dbt-tests/dbt-utils/at_least_one.md) | Asserts that a column has at least one value. | Model, Column |
|  dbt-utils | [not_constant](/dbt-tests/dbt-utils/not_constant.md) | Asserts that a column does not have the same value in all rows. | Model, Column |
|  dbt-utils | [not_empty_string](/dbt-tests/dbt-utils/not_empty_string.md) | Asserts that a column does not have any values equal to ''. An optional argument trim_whitespace controls whether whitespace should be trimmed from the column when evaluating. | Model, Column |
|  dbt-utils | [cardinality_equality](/dbt-tests/dbt-utils/cardinality_equality.md) | Asserts that values in a given column have exactly the same cardinality as values from a different column in a different model. | Model, Column |
|  dbt-utils | [not_null_proportion](/dbt-tests/dbt-utils/not_null_proportion.md) | Asserts that the proportion of non-null values present in a column is between a specified range [at_least, at_most] where at_most is an optional argument (default: 1.0). | Model, Column |
|  dbt-utils | [not_accepted_values](/dbt-tests/dbt-utils/not_accepted_values.md) | Asserts that there are no rows that match the given values. | Model, Column |
|  dbt-utils | [relationships_where](/dbt-tests/dbt-utils/relationships_where.md) | Asserts the referential integrity between two relations with an added predicate to filter out some rows from the test. Useful to exclude records such as test entities or rows created in the last X minutes/hours. | Model, Column |
|  dbt-utils | [mutually_exclusive_ranges](/dbt-tests/dbt-utils/mutually_exclusive_ranges.md) | Asserts that for a given lower_bound_column and upper_bound_column, the ranges between the lower and upper bounds do not overlap with the ranges of another row. | Model |
|  dbt-utils | [sequential_values](/dbt-tests/dbt-utils/sequential_values.md) | Confirms that a column contains sequential values. It can be used for both numeric values, and datetime values. | Model, Column |
|  dbt-utils | [unique_combination_of_columns](/dbt-tests/dbt-utils/unique_combination_of_columns.md) | Asserts that the combination of columns is unique. For example, the combination of month and product is unique, however neither column is unique in isolation. | Model |
|  dbt-utils | [accepted_range](/dbt-tests/dbt-utils/accepted_range.md) | Asserts that a column's values fall inside an expected range. Any combination of min_value and max_value is allowed, and the range can be inclusive or exclusive. | Model, Column |
|  elementary-data | [volume_anomalies](/dbt-tests/elementary-data/volume_anomalies.md) | Monitors the row count of your table over time per time bucket, comparing the row count of each bucket within the detection period to the row count of previous time buckets. | Model |
|  elementary-data | [freshness_anomalies](/dbt-tests/elementary-data/freshness_anomalies.md) | Monitors the freshness of your table over time, comparing the freshness of each bucket within the detection period to the freshness of previous time buckets. | Model |
|  elementary-data | [event_freshness_anomalies](/dbt-tests/elementary-data/event_freshness_anomalies.md) | Monitors the freshness of event data over time, focusing on the expected time it takes each event to load by measuring the difference between the event timestamp and when it is loaded to the database. | Model |
|  elementary-data | [dimension_anomalies](/dbt-tests/elementary-data/dimension_anomalies.md) | Monitors the frequency of values in configured dimensions over time, alerting on unexpected changes in distribution. Best configured on low-cardinality fields. | Model |
|  elementary-data | [all_columns_anomalies](/dbt-tests/elementary-data/all_columns_anomalies.md) | Executes column-level monitors and anomaly detection on all columns of the table, checking data type of each column and executing relevant monitors. Excludes columns based on exclude_prefix/exclude_regexp. | Model |
|  elementary-data | [column_anomalies](/dbt-tests/elementary-data/column_anomalies.md) | Executes column-level monitors and anomaly detection on a specific column, checking the data type of the column and executing relevant monitors. | Column |
|  dbt-expectations | [expect_column_to_exist](/dbt-tests/dbt-expectations/expect_column_to_exist.md) | Expect the specified column to exist. | Column |
|  dbt-expectations | [expect_row_values_to_have_recent_data](/dbt-tests/dbt-expectations/expect_row_values_to_have_recent_data.md) | Expect the model to have rows that are at least as recent as the defined interval prior to the current timestamp. Optionally gives the possibility to apply filters on the results. | Column |
|  dbt-expectations | [expect_grouped_row_values_to_have_recent_data](/dbt-tests/dbt-expectations/expect_grouped_row_values_to_have_recent_data.md) | Expect the model to have grouped rows that are at least as recent as the defined interval prior to the current timestamp. Use this to test whether there is recent data for each grouped row defined by group_by and a timestamp_column. | Model, Seed, Source |
|  dbt-expectations | [expect_table_aggregation_to_equal_other_table](/dbt-tests/dbt-expectations/expect_table_aggregation_to_equal_other_table.md) | Except an (optionally grouped) expression to match the same (or optionally other) expression in a different table. | Model, Seed, Source |
|  dbt-expectations | [expect_table_column_count_to_be_between](/dbt-tests/dbt-expectations/expect_table_column_count_to_be_between.md) | Expect the number of columns in a model to be between two values. | Model, Seed, Source |
|  dbt-expectations | [expect_table_column_count_to_equal_other_table](/dbt-tests/dbt-expectations/expect_table_column_count_to_equal_other_table.md) | Expect the number of columns in a model to match another model. | Model, Seed, Source |
|  dbt-expectations | [expect_table_columns_to_not_contain_set](/dbt-tests/dbt-expectations/expect_table_columns_to_not_contain_set.md) | Expect the columns in a model not to contain a given list. | Model, Seed, Source |
|  dbt-expectations | [expect_table_columns_to_contain_set](/dbt-tests/dbt-expectations/expect_table_columns_to_contain_set.md) | Expect the columns in a model to contain a given list. | Model, Seed, Source |
|  dbt-expectations | [expect_table_column_count_to_equal](/dbt-tests/dbt-expectations/expect_table_column_count_to_equal.md) | Expect the number of columns in a model to be equal to expected_number_of_columns. | Model, Seed, Source |
|  dbt-expectations | [expect_table_columns_to_match_ordered_list](/dbt-tests/dbt-expectations/expect_table_columns_to_match_ordered_list.md) | Expect the columns to exactly match a specified list. | Model, Seed, Source |
|  dbt-expectations | [expect_table_columns_to_match_set](/dbt-tests/dbt-expectations/expect_table_columns_to_match_set.md) | Expect the columns in a model to match a given list. | Model, Seed, Source |
|  dbt-expectations | [expect_table_row_count_to_be_between](/dbt-tests/dbt-expectations/expect_table_row_count_to_be_between.md) | Expect the number of rows in a model to be between two values. | Model, Seed, Source |
|  dbt-expectations | [expect_table_row_count_to_equal_other_table](/dbt-tests/dbt-expectations/expect_table_row_count_to_equal_other_table.md) | Expect the number of rows in a model match another model. | Model, Seed, Source |
|  dbt-expectations | [expect_table_row_count_to_equal_other_table_times_factor](/dbt-tests/dbt-expectations/expect_table_row_count_to_equal_other_table_times_factor.md) | Expect the number of rows in a model to match another model times a preconfigured factor. | Model, Seed, Source |
|  dbt-expectations | [expect_table_row_count_to_equal](/dbt-tests/dbt-expectations/expect_table_row_count_to_equal.md) | Expect the number of rows in a model to be equal to expected_number_of_rows. | Model, Seed, Source |
|  dbt-expectations | [expect_column_values_to_be_unique](/dbt-tests/dbt-expectations/expect_column_values_to_be_unique.md) | Expect each column value to be unique. | Column |
|  dbt-expectations | [expect_column_values_to_not_be_null](/dbt-tests/dbt-expectations/expect_column_values_to_not_be_null.md) | Expect column values to not be null. | Column |
|  dbt-expectations | [expect_column_values_to_be_null](/dbt-tests/dbt-expectations/expect_column_values_to_be_null.md) | Expect column values to be null. | Column |
|  dbt-expectations | [expect_column_values_to_be_of_type](/dbt-tests/dbt-expectations/expect_column_values_to_be_of_type.md) | Expect a column to be of a specified data type. | Column |
|  dbt-expectations | [expect_column_values_to_be_in_type_list](/dbt-tests/dbt-expectations/expect_column_values_to_be_in_type_list.md) | Expect a column to be one of a specified type list. | Column |
|  dbt-expectations | [expect_column_values_to_have_consistent_casing](/dbt-tests/dbt-expectations/expect_column_values_to_have_consistent_casing.md) | Expect a column to have consistent casing. By setting display_inconsistent_columns to true, the number of inconsistent values in the column will be displayed in the terminal. | Column |
|  dbt-expectations | [expect_column_values_to_be_in_set](/dbt-tests/dbt-expectations/expect_column_values_to_be_in_set.md) | Expect each column value to be in a given set. | Column |
|  dbt-expectations | [expect_column_values_to_be_between](/dbt-tests/dbt-expectations/expect_column_values_to_be_between.md) | Expect each column value to be between two values. | Column |
|  dbt-expectations | [expect_column_values_to_not_be_in_set](/dbt-tests/dbt-expectations/expect_column_values_to_not_be_in_set.md) | Expect each column value not to be in a given set. | Column |
|  dbt-expectations | [expect_column_values_to_be_increasing](/dbt-tests/dbt-expectations/expect_column_values_to_be_increasing.md) | Expect column values to be increasing. If strictly: True, then this expectation is only satisfied if each consecutive value is strictly increasing. | Column |
|  dbt-expectations | [expect_column_values_to_be_decreasing](/dbt-tests/dbt-expectations/expect_column_values_to_be_decreasing.md) | Expect column values to be decreasing. If strictly=True, then this expectation is only satisfied if each consecutive value is strictly decreasing. | Column |
|  dbt-expectations | [expect_column_value_lengths_to_be_between](/dbt-tests/dbt-expectations/expect_column_value_lengths_to_be_between.md) | Expect column entries to be strings with length between a min_value value and a max_value value (inclusive). | Column |
|  dbt-expectations | [expect_column_value_lengths_to_equal](/dbt-tests/dbt-expectations/expect_column_value_lengths_to_equal.md) | Expect column entries to be strings with length equal to the provided value. | Column |
|  dbt-expectations | [expect_column_values_to_match_regex](/dbt-tests/dbt-expectations/expect_column_values_to_match_regex.md) | Expect column entries to be strings that match a given regular expression. | Column |
|  dbt-expectations | [expect_column_values_to_not_match_regex](/dbt-tests/dbt-expectations/expect_column_values_to_not_match_regex.md) | Expect column entries to be strings that do NOT match a given regular expression. | Column |
|  dbt-expectations | [expect_column_values_to_match_regex_list](/dbt-tests/dbt-expectations/expect_column_values_to_match_regex_list.md) | Expect the column entries to be strings that can be matched to either any of or all of a list of regular expressions. | Column |
|  dbt-expectations | [expect_column_values_to_not_match_regex_list](/dbt-tests/dbt-expectations/expect_column_values_to_not_match_regex_list.md) | Expect the column entries to be strings that do not match any of a list of regular expressions. | Column |
|  dbt-expectations | [expect_column_values_to_match_like_pattern](/dbt-tests/dbt-expectations/expect_column_values_to_match_like_pattern.md) | Expect column entries to be strings that match a given SQL like pattern. | Column |
|  dbt-expectations | [expect_column_values_to_not_match_like_pattern](/dbt-tests/dbt-expectations/expect_column_values_to_not_match_like_pattern.md) | Expect column entries to be strings that do not match a given SQL like pattern. | Column |
|  dbt-expectations | [expect_column_values_to_match_like_pattern_list](/dbt-tests/dbt-expectations/expect_column_values_to_match_like_pattern_list.md) | Expect the column entries to be strings that match any of a list of SQL like patterns. | Column |
|  dbt-expectations | [expect_column_values_to_not_match_like_pattern_list](/dbt-tests/dbt-expectations/expect_column_values_to_not_match_like_pattern_list.md) | Expect the column entries to be strings that do not match any of a list of SQL like patterns. | Column |
|  dbt-expectations | [expect_column_distinct_count_to_equal](/dbt-tests/dbt-expectations/expect_column_distinct_count_to_equal.md) | Expect the number of distinct column values to be equal to a given value. | Column |
|  dbt-expectations | [expect_column_distinct_count_to_be_greater_than](/dbt-tests/dbt-expectations/expect_column_distinct_count_to_be_greater_than.md) | Expect the number of distinct column values to be greater than a given value. | Column |
|  dbt-expectations | [expect_column_distinct_count_to_be_less_than](/dbt-tests/dbt-expectations/expect_column_distinct_count_to_be_less_than.md) | Expect the number of distinct column values to be less than a given value. | Column |
|  dbt-expectations | [expect_column_distinct_values_to_be_in_set](/dbt-tests/dbt-expectations/expect_column_distinct_values_to_be_in_set.md) | Expect the set of distinct column values to be contained by a given set. | Column |
|  dbt-expectations | [expect_column_distinct_values_to_contain_set](/dbt-tests/dbt-expectations/expect_column_distinct_values_to_contain_set.md) | Expect the set of distinct column values to contain a given set. | Column |
|  dbt-expectations | [expect_column_distinct_values_to_equal_set](/dbt-tests/dbt-expectations/expect_column_distinct_values_to_equal_set.md) | Expect the set of distinct column values to equal a given set. | Column |
|  dbt-expectations | [expect_column_distinct_count_to_equal_other_table](/dbt-tests/dbt-expectations/expect_column_distinct_count_to_equal_other_table.md) | Expect the number of distinct column values to be equal to number of distinct values in another model. | Model, Column, Seed, Source |
|  dbt-expectations | [expect_column_mean_to_be_between](/dbt-tests/dbt-expectations/expect_column_mean_to_be_between.md) | Expect the column mean to be between a min_value value and a max_value value (inclusive). | Column |
|  dbt-expectations | [expect_column_median_to_be_between](/dbt-tests/dbt-expectations/expect_column_median_to_be_between.md) | Expect the column median to be between a min_value value and a max_value value (inclusive). | Column |
|  dbt-expectations | [expect_column_quantile_values_to_be_between](/dbt-tests/dbt-expectations/expect_column_quantile_values_to_be_between.md) | Expect specific provided column quantiles to be between provided min_value and max_value values. | Column |
|  dbt-expectations | [expect_column_stdev_to_be_between](/dbt-tests/dbt-expectations/expect_column_stdev_to_be_between.md) | Expect the column standard deviation to be between a min_value value and a max_value value. Uses sample standard deviation (normalized by N-1). | Column |
|  dbt-expectations | [expect_column_unique_value_count_to_be_between](/dbt-tests/dbt-expectations/expect_column_unique_value_count_to_be_between.md) | Expect the number of unique values to be between a min_value value and a max_value value. | Column |
|  dbt-expectations | [expect_column_proportion_of_unique_values_to_be_between](/dbt-tests/dbt-expectations/expect_column_proportion_of_unique_values_to_be_between.md) | Expect the proportion of unique values to be between a min_value value and a max_value value. | Column |
|  dbt-expectations | [expect_column_most_common_value_to_be_in_set](/dbt-tests/dbt-expectations/expect_column_most_common_value_to_be_in_set.md) | Expect the most common value to be within the designated value set | Column |
|  dbt-expectations | [expect_column_max_to_be_between](/dbt-tests/dbt-expectations/expect_column_max_to_be_between.md) | Expect the column max to be between a min and max value | Column |
|  dbt-expectations | [expect_column_min_to_be_between](/dbt-tests/dbt-expectations/expect_column_min_to_be_between.md) | Expect the column min to be between a min and max value | Column |
|  dbt-expectations | [expect_column_sum_to_be_between](/dbt-tests/dbt-expectations/expect_column_sum_to_be_between.md) | Expect the column to sum to be between a min and max value | Column |
|  dbt-expectations | [expect_column_pair_values_A_to_be_greater_than_B](/dbt-tests/dbt-expectations/expect_column_pair_values_A_to_be_greater_than_B.md) | Expect values in column A to be greater than column B. | Model, Seed, Source |
|  dbt-expectations | [expect_column_pair_values_to_be_equal](/dbt-tests/dbt-expectations/expect_column_pair_values_to_be_equal.md) | Expect the values in column A to be the same as column B. | Model, Seed, Source |
|  dbt-expectations | [expect_column_pair_values_to_be_in_set](/dbt-tests/dbt-expectations/expect_column_pair_values_to_be_in_set.md) | Expect paired values from columns A and B to belong to a set of valid pairs. | Model, Seed, Source |
|  dbt-expectations | [expect_select_column_values_to_be_unique_within_record](/dbt-tests/dbt-expectations/expect_select_column_values_to_be_unique_within_record.md) | Expect the values for each record to be unique across the columns listed. Note that records can be duplicated. | Model, Seed, Source |
|  dbt-expectations | [expect_multicolumn_sum_to_equal](/dbt-tests/dbt-expectations/expect_multicolumn_sum_to_equal.md) | Expects that sum of all rows for a set of columns is equal to a specific value | Model, Seed, Source |
|  dbt-expectations | [expect_compound_columns_to_be_unique](/dbt-tests/dbt-expectations/expect_compound_columns_to_be_unique.md) | Expect that the columns are unique together, e.g. a multi-column primary key. | Model, Seed, Source |
|  dbt-expectations | [expect_column_values_to_be_within_n_moving_stdevs](/dbt-tests/dbt-expectations/expect_column_values_to_be_within_n_moving_stdevs.md) | A simple anomaly test based on the assumption that differences between periods in a given time series follow a log-normal distribution. | Column |
|  dbt-expectations | [expect_column_values_to_be_within_n_stdevs](/dbt-tests/dbt-expectations/expect_column_values_to_be_within_n_stdevs.md) | Expects (optionally grouped & summed) metric values to be within Z sigma away from the column average | Column |
|  dbt-expectations | [expect_row_values_to_have_data_for_every_n_datepart](/dbt-tests/dbt-expectations/expect_row_values_to_have_data_for_every_n_datepart.md) | Expects model to have values for every grouped date_part. | Model, Seed, Source |


## 📝 How to Contribute

Contributions are what make the "Awesome dbt Tests" repository thrive. Whether you're contributing a new test, a real-world example, or simply fixing a typo, your input is highly valued.

To contribute:

1. **Fork the Repository:** Start by forking the repository to your GitHub account.
2. **Clone the Repository:** Clone the forked repository to your local machine.
3. **Create a Branch:** Create a new branch for your contribution.
4. **Add Your Contribution:** Whether it's a new test definition, a real-world example, or any other valuable content, add it to the relevant section.
5. **Submit a Pull Request:** Once you're satisfied with your contribution, submit a pull request for review.

Please refer to the [CONTRIBUTING.md](contributing.md) file for detailed contribution guidelines.

## 📄 License

This repository is licensed under the [MIT License](/license.md). By contributing to the "Awesome dbt Tests" repository, you agree to abide by its terms.

## 🙏 Acknowledgments

- [dbt Labs](https://www.getdbt.com/) for creating and maintaining dbt, a transformational tool in the data world.
- The creators and maintainers of the dbt packages featured in this repository.
- The data community for continuously contributing to and advancing the dbt ecosystem.

Join us in building the most comprehensive resource for dbt testing. Let's work together to enhance data reliability and quality across the board!