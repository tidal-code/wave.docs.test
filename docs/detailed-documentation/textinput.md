---
layout: default
title: Text Input
parent: Detailed Docs
nav_order: 5
---

# Text Input Methods

The available text input methods in the framework are:

```java
sendKeys(String text);
setText(String text);
setInnerHtml(String text);
clearAndType(String text);
```

**sendKeys(text):**
Normal text input method to send text data to a UI text input field. 

**setText(text):**
This method would revisit the value input and if it is not correct, it will clear and 
try again until it succeeds or a timeout is reached. This method is quite useful to fill
difficult text input fields. This method is slower than the sendKeys() method. So use it only
when it is necessary. 

**<span class='text-red-000'>Caution:</span>**
<br>Do not try to input passwords or send keyboard key inputs using this method. The setText method will fail to read the
value and evaluate it. This will eventually cause an exception when the timeout reaches.



**setInnerHtml(text):**
This method would set the text value as an inner HTML value. This is not a proper text input method as it relies on modifying the
HTML directly. So it may have unforeseen consequences. Use this method only if you need it absolutely necessary.

**clearAndType(text):**
This method will try to clear the input field and send the text to the input field. 

## Javscript Text Input Method

This is a method using JavaScript to send a text value to an element. This may not be reliable always as it 
will not throw an exception also the UI application may not recognise the value. So please use this method when it is 
absolutely necessary only.

```java
setValue(String text);
```




