---
layout: default
title: Hidden Elements
parent: Detailed Docs
nav_order: 6
---

# When Elements are Not Visible

## ScrollToView

If the target element is not in the view port, you might need to scroll up or down to bring it to view. 
Most of the times, Selenium will automatically do that. If it fails to do so and the user interaction 
fails with messages such as element not interactable or element hidden behind another element etc, we might
need to bring it to view. For that use

```find("locator").scrollToView()```    



## Invisible Elements

Some times the actual checkboxes will be hidden to make it uniform across different browsers. 
All the browsers have their own default style of implementing web components. So the developers
mask it using CCS. In the case of checkboxes, the original one will be hidden to apply a CSS layer.
If this is the case the framework will fail to find the element. 

To overcome this, we have to use a function to inform the framework that the element is invisible.

Code as below:

```java
find("checkbox").invisibleElement().click();
```


