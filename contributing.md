# Contributing to Awesome dbt Tests

First off, thank you for considering contributing to Awesome dbt Tests! It's people like you that make this project such a great resource for the dbt community. We welcome contributions of all kinds from anyone.

This document outlines how to propose a change to Awesome dbt Tests and the process we follow to evaluate it. Reading and following these guidelines will help us make the contribution process easy and effective for everyone involved.

## What we are looking for

We are looking for contributions that:

- Add new dbt tests from various packages like dbt-utils, dbt-expectations, or elementary-data.
- Provide real-world examples of how specific dbt tests can be applied.
- Enhance the documentation with best practices, tips, or tutorials related to dbt tests.
- Fix errors or inconsistencies in the existing content.

## How to contribute

If you'd like to contribute with a real-world example, please do the following:

1. **Fork the repository**: Click on the 'Fork' button at the top right corner of the page. This will create a copy of the repository in your GitHub account.
2. **Clone your fork**: Navigate to your GitHub profile, find the forked repository, and clone it to your local machine.
3. **Create a branch**: Once you have cloned the repository, navigate to it from your terminal and create a branch where you'll work on your contribution. Use a name that describes your contribution, for example, `add-new-test-example`.
4. **Make your changes**: Add or modify the content as needed. Make sure to follow the style and structure of the existing content.

Go to the md file of the test you want to add an example, like `accepted_range.md` and submit an example like the one below:

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


5. **Commit your changes**: Once you're happy with your contribution, commit it with a clear and concise commit message.
6. **Push to your fork**: Push your changes to your forked repository on GitHub.
7. **Submit a pull request**: Navigate to the original "Awesome dbt Tests" repository you forked and press the "New pull request" button. Select your branch and submit the pull request with a clear description of your changes.

## Review process

Once you submit a pull request, the maintainers will review your proposed changes. They might request further details or suggest modifications before merging your contribution. This review process helps ensure that the repository maintains high-quality and relevant content.

## Conduct

We have committed to fostering an open and welcoming environment. By participating, you are expected to uphold this code. Please report unacceptable behavior to the repository maintainers.

## Questions?

If you have any questions or need further clarification about contributing, please feel free to open an issue or contact the maintainers directly. We're here to help!

Thank you for contributing to Awesome dbt Tests, and we look forward to your contribution!