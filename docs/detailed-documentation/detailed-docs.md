---
layout: default
title: Detailed Docs
nav_order: 3
has_children: true
permalink: /docs/detailed-docs
---

# Detailed Documentation

You can find detailed functional documentation about the project in this section's child pages. 

Most of the functions are designed as static fluent APIs. The `find()` and `findAll()`
methods are the base for most user actions. Most action methods are designed to emulate user interactions with a Web Application.

To begin your understanding about the process to interact with a Web UI, we assume that you
are familiar with how to locate an element. If not; you can find the details [here.](https://www.selenium.dev/documentation/webdriver/elements/locators/){:target='_blank'} Once you identify the 
locator, pass that information to Wave UI Automation library as a string. There is no option to pass ***Selenium
By locator***. Instead you have to prefix the locator type with your locator.

Example:
```java
find("id:some_id").click();
````
<small> More examples can be found in the ***Locators*** page. </small>

There are options to add and retrieve data on the fly. The framework will wait until the 
overlay spinners blocking an operation is disappeared. Iframes will be automatically switched to find the right 
element. 

Examples:

```java
find("class:some_class").click();
find("css:css selector").click();
find("linkText:Selenium").click();
```


For Xpath and Text selectors you do not need to prefix anything. Just add them as is. 

Demo Button Example:

<span class="fs-3">
[Demo Button](){: .btn .btn-purple .xs}
</span>

```java
find("Demo Button").click();
```

For finding Xpaths, use as below

```java
find("//span/a[text()='Demo Button']")
```


{: .fs-6 .fw-300 }
