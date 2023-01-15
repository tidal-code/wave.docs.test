---
layout: default
title: Versions
parent: Detailed Docs
nav_order: 1
---

## Future Releases

<br>
Planned Features:

1. In built shadow DOM support. <br>
2. Able to fetch first(), last() and nth() element from a collection without using get(n);

<br>

# Current - Version 1.2.0 

New release
{: .label .label-purple }

Maven:

```xml
        <dependency>
            <groupId>io.github.tidal-code</groupId>
            <artifactId>wave</artifactId>
            <version>1.2.0</version>
        </dependency>
```

Gradle:

```yml
implementation group: 'io.github.tidal-code', name: 'wave', version: '1.2.0'
```

Changes:

1. Reverted from Selenium Manager to WedDriver Manager due to preformance issues. 
2. Iframe iteration is optimised to increase test execution speed. Old IframeHandler is now deprecated.

<br>

### Version 1.1.0

Added custom expectation failure message.

Example:
```java
find("#invisibleElement").expecting(toBePresent).orElseFail("The element expected to be present, but failed to fulfill the condition");
```

This would cause an assertion failure with the custom message given.


### Version 1.0.1

```Upgrade to native Selenium Manager from WebDriver Manager.```

Selenium has integrated Boni García's WebDriver manager to the core Selenium library.

### Version 1.0.0

```Initial version release.```




