---
layout: default
title: Versions
parent: Detailed Docs
nav_order: 1
---

## Future Releases

Under Test Snapshot Version
{: .label .label-orange }

This snapshot version may get updates and the new experimental functions under test could change without notice.
No backward compatibility would be provided for these new functions. 
```xml
        <dependency>
            <groupId>io.github.tidal-code</groupId>
            <artifactId>wave</artifactId>
            <version>1.3.2-SNAPSHOT</version>
        </dependency>
```

1. Table data scraping function (Under development. No API provided).

2. Advanced debug mode.

3. waitFor for findAll has been limited to expected conditions.



# Current - Version 1.3.1

New release
{: .label .label-purple }

Maven:

```xml
        <dependency>
            <groupId>io.github.tidal-code</groupId>
            <artifactId>wave</artifactId>
            <version>1.3.1</version>
        </dependency>
```

Gradle:

```yml
implementation group: 'io.github.tidal-code', name: 'wave', version: '1.3.0'
```

Added keyboard multi interaction function.

New `FluentRquest` class for API requests.



### Version 1.3.0

Added slow run mode and debug mode. 

New upload file by drag and drop function has been added.
`find("element").uploadFileByDragAndDrop("file name");`

New page refresh function has been added.              
`find("element").doPageRefresh(MaxTime, IntervalTime);`

BugFixes:
Fixed nullpointer exception for certain user interaction scenarios.


### Version 1.2.9

Added functions to find first(), last() and skipFirst() from a collection


Bug Fixes:
Element finder scripts iframe iterator had an issue which would cause it not to find the right iframe, the element contains.
The issue has been identified and fixed.


### Version 1.2.8
Changed assertion type for test failures to reflect correct failure types in Allure reporting.

### Version 1.2.7
Internal changes only. <br>
Change in Element finder class to use CommandContext class to pass more information about element to be found.


### Version 1.2.4 to 1.2.6
Minor bug fixes and enhancements

### Version 1.2.3
Part 2 of core scripts refactoring to increase execution speed.

### Version 1.2.2
Part 1 of core scripts refactoring to increase execution speed.

### Version 1.2.1

Fixed a bug with getText, that may cause a nullpointer exception. 

### Version 1.2.0

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




