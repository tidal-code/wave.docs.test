---
layout: default
title: Expected Conditions
parent: Conditions
---

# Expected Conditions

Expected Conditions are soft conditional checks that can be forced to fail, if the failure should stop the test execution. 
They are not assertions. If the expected condition fails, it means that your test is broken at some point.

Expected Conditions can be specifically instructed to fail
by calling a follow up function called ***orElseFail()***


Examples:

```java
find("element").expecting(toBePresent);
find("element").expecting(toBeVisible);
find("element").expecting(toBeInvisible);
find("element").expecting(toBeStale);
find("element").expecting(toBeInteractable);
find("element").expecting(toBeClickable);
find("element").expecting(toBePresent);
find("element").expecting(toBeNotPresent);
find("element").expecting(textNotEmpty);
find("element").expecting(newTextValue);
find("element").expecting(aChangeOfState);
```