---
layout: default
title: Test Objective
parent: Best Practices
nav_order: 1
---

# Objective of Tests

Your tests should have only one objective. This means that if a test fails, its name should clearly state the aim and intention of the test scenario.

It can be tempting to add assertions to each and every step when creating automated test cases. However, it is advisable to focus on a single objective instead. For instance, if you are testing a file upload scenario, let the test fail only if the upload itself fails. Avoid adding additional assertions to check, for example, the correctness of the page title or if the user is on the correct page, within your pre-condition or test action steps.

The reason behind this approach is to prevent false negatives in your tests. If a test fails prematurely due to an added assertion in a pre-condition step, it can create unnecessary workload to analyze multiple test cases that failed solely because of a page title assertion in a "Given" step. You cannot assume that all these test failures were caused by an incorrect page title, as they may involve failures due to other conditions as well.

By having a single test objective, you can ensure that the test is concise, targeted, and easier to understand and maintain.

Having a single test objective helps in several ways:

1. Clarity: It provides clarity on what is being tested and what the expected outcome should be. <br>
2. Isolation: It isolates the functionality being tested from other unrelated components, making it easier to identify the cause of failures or issues. <br>
3. Maintainability: With a single objective, tests are more modular and can be updated or modified without affecting other test cases. <br>
4. Reusability: Tests with clear objectives can be reused in different scenarios or integrated into larger test suites, enhancing test coverage and efficiency.


#### Examples:

```text
Test Objective: Verify Successful User Registration
Description: The objective of this test is to ensure that the user registration process 
functions correctly and that users can successfully register on the system.

Test Objective: Validate Login Functionality
Description: The objective of this test is to verify that users can log in to the system using 
valid credentials and gain access to the appropriate user interface.

Test Objective: Test Add to Cart Functionality
Description: The objective of this test is to validate that the "Add to Cart" functionality 
of an e-commerce website works as expected, allowing users to add items to their shopping cart.

Test Objective: Check Email Notification Delivery
Description: The objective of this test is to confirm that email notifications are being 
successfully delivered to the intended recipients within a reasonable time frame.

Test Objective: Validate Search Functionality
Description: The objective of this test is to ensure that the search feature of a 
web application retrieves accurate and relevant results based on user input.

Test Objective: Verify Payment Processing
Description: The objective of this test is to validate that the payment processing 
system accurately processes payment transactions and updates the necessary records.
```

#### Gherkin Examples For the above scenarios:

```gherkin
Feature: User Registration
  Scenario: Successful user registration
    Given I am on the registration page
    When I fill in the registration form with valid details
    And I click the "Register" button
    Then I should be registered successfully
    And I should be redirected to the home page


Feature: User Login
  Scenario: Successful user login
    Given I am on the login page
    When I enter valid login credentials
    And I click the "Login" button
    Then I should be logged in successfully
    And I should see the dashboard page


Feature: Add to Cart
  Scenario: Add item to cart
    Given I am on the product page
    When I click the "Add to Cart" button for a specific item
    Then the item should be added to my cart
    And the cart should display the correct item count


Feature: Email Notification
  Scenario: Email notification delivery
    Given I am a registered user
    And I have an unread email notification
    When I check my email inbox
    Then I should see the email notification
    And the notification should have been delivered within 24 hours


Feature: Search
  Scenario: Perform a search
    Given I am on the search page
    When I enter a search query
    And I click the "Search" button
    Then I should see search results
    And the results should be relevant to my search query


Feature: Payment Processing
  Scenario: Process payment successfully
    Given I am on the payment page
    When I enter valid payment details
    And I click the "Submit Payment" button
    Then the payment should be processed successfully
    And I should receive a payment confirmation
```