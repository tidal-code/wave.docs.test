---
layout: default
title: Locators
parent: Detailed Docs
nav_order: 2
---

# Locators

Selenium provides us to locate an element by **By** class static methods.
Wave handles the locators slightly differently. The locators are supplied 
as a string prefixed with the locator types as shown in the table below.

| Type | Selenium Function|  Tidal Wave Libary Method
|:-------------|:------------------| :------------------|
| id | By.id(\"some_id\") | find(\"id:some_id\") |
| name | By.name(\"some_name\") | find(\"name:some_name\") |
| class | By.className(\"some_class")| find(\"class:some_class\") |
| tag name | By.tagName(\"some_tag_name\")| find(\"tagName:some_tag_name\")|
| xpath | By.xpath(\"//xpath\")| find(\"//xpath\") |
| css selector | By.cssSelector(\"css selector")| find(\"css: css selector") |
| link text | By.linkText(\"link text")| find(\"linkText:link text") |
| partial link text | By.partilaLinkText(\"partial link text")| find(\"partialLinkText:partial link text") |

To locate an element by its title

| Type | Selenium Function|  Tidal Wave Libary Method
|:-------------|:------------------| :------------------|
| title | By.xpath("//*[title='title value']| find(\"title:title value\") |


To locate an element by its text value

| Type | Selenium Function|  Tidal Wave Library Method
|:-------------|:------------------| :------------------|
| text | By.xpath("//*[text()='text value']| find(\"text value\") |


## Special Xpath functions
<br>
For simple xpath expressions you can just type it in natural English.
For example `//div[name='user_name']` can be passed over to the framework like `find("div with name user_name")`

If it is a partial match you can use `find("div contains name user")`

If the property contains special characters or white spaces, you can enclose them in single quotes
`find("div contains text 'User Login'")`


