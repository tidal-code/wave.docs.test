---
layout: default
title: Click Methods
parent: Detailed Docs
nav_order: 3
---

# Click Methods

The available click methods in the framework are:

```java
click();
doubleClick();
contextClick();
actionClick();
forceClick();
```

**click()**:
Involves a normal selenium click. It handles stale element exception and element intercepted
exceptions.

**doubleClick()**:
Would send a double click to the element.

**contextClick()**:
Would send a right click (or left depending on mouse configuration), or a context click.

**actionClick()**:
This is a Selenium action click. This  may not throw an error if a click did not work properly.

**forceClick()**:
This click type will simulate a force click by clicking and holding on to an element for a short time.

## Javscript Click Method

This is a method using JavaScript to send a click action to an element. This may not be reliable always as it 
will not throw an exception like the other click methods when it fails. So please use this method when it is 
absolutely necessary only.

```java
clickByJS();
```




