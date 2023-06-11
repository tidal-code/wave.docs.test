---
layout: default
title: Hidden Elements
parent: Detailed Docs
nav_order: 7
---

# When Elements are Not Visible

## ScrollToView

If the target element is not in the view port, you might need to scroll up or down to bring it to view. 
Most of the times, Selenium will automatically do that. If it fails to do so and the user interaction 
fails with messages such as element not interactable or element hidden behind another element etc, we might
need to bring it to view. For that use

```java
find("locator").scrollToView();
```    

## MoveToElement

Another option is to use the `moveToElement` method. It will bring the element into view and will place the cursor on top of it.
This function is quite useful when you have internal scrollable panes in the application. ScrollToView may not work with such elements. 

Tip: Using moveToElement() to between the elements on a scrollable pane can simulate a mouse scroll action. 

```java
find("locator").moveToElement();
```  

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


