### not_empty_string ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#not_empty_string-source))
Asserts that a column does not have any values equal to `''`. 

**Usage:**
```yaml
 models:
  - name: model_name
    columns:
      - name: column_name
        tests:
          - dbt_utils.not_empty_string
```

The macro accepts an optional argument `trim_whitespace` that controls whether whitespace should be trimmed from the column when evaluating. The default is `true`. 

**Usage:**
```yaml
 models:
  - name: model_name
    columns:
      - name: column_name
        tests:
          - dbt_utils.not_empty_string:
              trim_whitespace: false
              
```