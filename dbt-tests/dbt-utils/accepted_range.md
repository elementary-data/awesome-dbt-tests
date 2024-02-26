### accepted_range ([source](https://github.com/dbt-labs/dbt-utils/blob/main/README.md#accepted_range-source))

Asserts that a column's values fall inside an expected range. Any combination of `min_value` and `max_value` is allowed, and the range can be inclusive or exclusive. Provide [a `where` argument](https://docs.getdbt.com/reference/resource-configs/where) to filter to specific records only.

In addition to comparisons to a scalar value, you can also compare to another column's values. Any data type that supports the `>` or `<` operators can be compared, so you could also run tests like checking that all order dates are in the past.

**Usage:**

```yaml
 models:
  - name: model_name
    columns:
      - name: user_id
        tests:
          - dbt_utils.accepted_range:
              min_value: 0
              inclusive: false

      - name: account_created_at
        tests:
          - dbt_utils.accepted_range:
              max_value: "getdate()"
              #inclusive is true by default

      - name: num_returned_orders
        tests:
          - dbt_utils.accepted_range:
              min_value: 0
              max_value: "num_orders"

      - name: num_web_sessions
        tests:
          - dbt_utils.accepted_range:
              min_value: 0
              inclusive: false
              config:
                where: "num_orders > 0"
```

#### Examples

##### Monitoring Subscription Durations in a SaaS Company

**Scenario:** 

A B2B SaaS company offers subscription-based services with various tiers, including monthly and annual plans. To ensure billing accuracy and service consistency, it's vital that the subscription durations recorded in the database match the expected ranges for each plan type.

**Problem:**

Inaccurate subscription durations can lead to billing errors, affecting revenue recognition and customer satisfaction. For instance, a monthly subscription incorrectly recorded with a duration of more than 31 days or an annual subscription exceeding 366 days (considering leap years) can cause overcharging or undercharging issues.

**Solution:**

The company can use the `accepted_range` test to assert that the `duration_days` column in the `subscriptions` table falls within an expected range for each subscription plan.

**Implementation:**

   For monthly subscriptions, the expected range of duration might be 28 to 31 days, depending on the month. The test can be applied to ensure no monthly subscription exceeds this range.
   For annual subscriptions, considering leap years, the acceptable range could be set from 365 to 366 days. This ensures all annual plans are correctly recorded.

   ```yaml
       models:
     - name: subscriptions
       columns:
         - name: duration_days
           tests:
             - dbt_utils.accepted_range:
                 min_value: 28
                 max_value: 31
                 where: "subscription_type = 'monthly'"
             - dbt_utils.accepted_range:
                 min_value: 365
                 max_value: 366
                 where: "subscription_type = 'annual'"
   ```