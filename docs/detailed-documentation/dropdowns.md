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
select(String selectText); //Visible text in the dropdown
select(String value); //value of select elements
select(int index); //index value of elements
```

Many web applications may not have dropdown types as \'select\'. You might need to add extra
user interactions to select an element from those types of dropdowns. For example you might need to click on a drop down arrow and then click on one of the values shown.
