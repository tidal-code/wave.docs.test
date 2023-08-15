---
layout: default
title: Dropdowns
parent: Detailed Docs
nav_order: 6
---

# Dropdowns

Typical dropdown with input type as \'select\' can be interacted with using three
methods 

```java
find("locator").select(String selectText); //Visible text in the dropdown
find("locator").select(String value); //value of select elements
find("locator").select(int index); //index value of elements
```

Many web applications may not have dropdown types as \'select\'. You might need to add extra
user interactions to select an element from those types of dropdowns. For example you might need to click on a drop down arrow and then click on one of the values shown.
