# Expression Is True Test

This page outlines the `expression_is_true` test from the dbt-utils package. This test asserts that a given SQL expression evaluates to true for all records in a dataset. It's a powerful tool for validating data integrity and logical consistency across columns within a table.

## How it Works

The `expression_is_true` test allows you to define a SQL expression that should hold true for every record in the specified model (table or view). This can include checks for basic algebraic relationships between columns, validations of column lengths, or any other condition that can be expressed in SQL and evaluates to a boolean value.

### Steps and Conditions:

1. **Expression Definition**: You specify the SQL expression that needs to be true for all records. This expression can involve one or more columns.
2. **Execution**: The test evaluates the expression for each record in the dataset.
3. **Optional Filtering**: You can optionally define a `where` clause to limit the scope of the test to a subset of records.
4. **Outcome**:
   - **Pass**: If the expression evaluates to true for all records (or all records within the specified subset), the test passes, indicating that the data meets the defined logical criteria.
   - **Fail**: If the expression evaluates to false for any record, the test fails. This indicates a discrepancy in the data that violates the expected logical condition.

## Example Usage: Videogame Company

For a Videogame company, ensuring the integrity of player data, such as scores and achievements, is crucial for maintaining fair play and a competitive environment. The `expression_is_true` test can be applied to the `player_scores` table to validate the consistency of score calculations.

Consider a scenario where the `player_scores` table records each player's scores from different game sessions, including columns for `score_from_kills`, `score_from_objectives`, and a `total_score` that should equal the sum of the other two scores.

```yaml
models:
  - name: player_scores
    tests:
      - dbt_utils.expression_is_true:
          expression: "score_from_kills + score_from_objectives = total_score"
```

In this example, the `expression_is_true` test ensures that the `total_score` for each player accurately reflects the sum of `score_from_kills` and `score_from_objectives`. This validation helps maintain the integrity of the scoring system, ensuring that player rankings and achievements are based on accurate data.

Additionally, suppose there was a recent update to the scoring system on January 1, 2019. In that case, you might want to apply this test only to scores recorded after the update:

```yaml
models:
  - name: player_scores
    tests:
      - dbt_utils.expression_is_true:
          expression: "score_from_kills + score_from_objectives = total_score"
          config:
            where: "created_at > '2019-01-01'"
```

By applying the `expression_is_true` test, the Videogame company can automatically verify the accuracy of score calculations, ensuring that player leaderboards and achievements reflect true player performance.