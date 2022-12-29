---
layout: default
title: Expected Conditions
parent: Verifications
---

# Expected Conditions

Expected conditions are kind of soft verifications. But not exactly similar to the soft verification concept as well. They are expectations that may or may not get realised. They do not cause a failure by themselves unless specifically instructed to do so by calling a follow up function called ***orEleseFail()***

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



