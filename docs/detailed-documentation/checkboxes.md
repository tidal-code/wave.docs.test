---
layout: default
title: Checkboxes
parent: Detailed Docs
nav_order: 8
---

# Check Methods

The available check methods in the framework are:

```java
find("locator").check();
find("locator").unCheck();
```

You will be able to clik on a checkbox using the `click()` method as well. But it will have a side effect
as you may not be sure if the checkbox is already checked or not. The built-in check and uncheck methods will do
it the right way. 

**check()**:
This will check the checkbox only if it is not already checked. 

**unCheck()**:
This will uncheck the checkbox only if it is already checked.


## Invisible Checkboxes

Some times the actual checkboxes will be hidden to make it uniform across different browsers. 
All the browsers have their own default style of implementing web components. So the developers
mask it using CCS. In the case of checkboxes, the original one will be hidden to apply a CSS layer.
If this is the case the framework will fail to find the element. 

To overcome this, we have to use a function to inform the framework that the element is invisible.

Code as below:

```java
find("checkbox").invisibleElement().click();
```


