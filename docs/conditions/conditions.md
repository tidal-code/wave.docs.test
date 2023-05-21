---
layout: default
title: Conditions
nav_order: 4
has_children: true
permalink: docs/conditions
---

# Conditions

Tidal framework has got two types of built in conditonal checks. They are not test assertions. 
Rather, they should be used to check the state of the application. You should use a proper test assertion
library to verify your test results. 

When conditions fail, you get a broken test, not a failed test. 

For example, lets say, you want to update a date and verify that it is reflected in the customer data page.
The objective of our test is to verify the change in the customer data page.

if you are updating a date via the UI, the success message returned could be checked by a conditon.

```java
find("element").shouldHave(matchingText("Date successfully updated"));
```

In the above example, you might need to make sure that the date is successfully updated to the database before
proceeding with the rest of the test steps. If your test fails to satisfy the above condition, we say the test is 
broken. The reason is that, ensuring the database update in that UI is not the objective of our test. 

The actual objective of your test is to verify the updated date in a different page. For that, you should use a proper
test assertion library.

```java
//Using Tidal Flow test assertion library
verify("Updated date should reflect in the new page", actualDate).isEqualTo(expectedDate);
```

