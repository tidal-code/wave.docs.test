---
layout: default
title: Multiple Elements
parent: Detailed Docs
nav_order: 12
---

# Finding Multiple Elements

You can use `findAll("element")` to identity a list of elements from the UI.
By default it will not have any wait associated with it because it is supposed to return zero or more elements.
But you can still use `waitFor(seconds)` to add a wait property to its associated expected conditions.

From findAll method you will get an iterable class of UIElements. You can iterate through the elements to extract
the properties or do actions on the UI.


```java
findAll("element").expecting(sizeGreaterThan(0));
findAll("element").first();
findAll("element").last();
findAll("element").skipFirst(); //to skip the first element - useful to skip table headers
findAll("element").get(index); //to retrieve a UI element with nth index
findAll("element").size();
findAll("element").isPresent();
findAll("element").pause(int); //static wait
findAll("element").shouldHave(CollectionsCondition);
findAll("element").expecting(Expectation);
findAll("element").getAllText(); //list
```









