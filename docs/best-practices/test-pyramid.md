---
layout: default
title: Test Pyramid
parent: Best Practices
nav_order: 1
---

# Number of UI Tests

Out of the three major test automation types (Unit Tests, API Tests and UI Tests), the UI tests are the slowest and you should be writing more Unit Tests and API (Integration) tests. The UI tests are expensive to create, run and maintain. Imagine a pyramid and the bottom part of the pyramid is the number of unit tests. The middle part is the number is API tests. The upper part would be the number of UI tests. That is what is called a test pyramid and shows the ideal ratio of the types of automated tests you should have. 

Compared to unit test and integration tests, UI tests are slower to run and flaky as well. The results cannot be hundred percent reliable and we should avoid them being a criteria for deployment if possible. 

These reasons make it imperative that you should be choosing your UI tests carefully. The testing via UI has its own advantages though. When you test a UI, you might be testing hundreds of APIs. These APIs utilise hundreds or thousands of functions in the core application to run. So in effect you are indirectly testing APIs and core function methods. This should be taken with a grain of salt because, eventhough you are testing all these, you may not exactly know the failure points. 



