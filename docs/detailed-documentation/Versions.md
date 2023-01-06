---
layout: default
title: Versions
parent: Detailed Docs
nav_order: 1
---

# Version 1.1.0

Added custom expectation failure message

Example:
```java
find("#invisibleElement").expecting(toBePresent).orElseFail("The element expected to be present, but failed to fulfill the condition");
```

This would cause an assertion failure with the custom message given.

## Version 1.0.1

```Upgrade to native Selenium Manager from WebDriver Manager.```

Selenium has integrated Boni García's WebDriver manager to the core Selenium library.

## Version 1.0.0

```Initial version release.```




