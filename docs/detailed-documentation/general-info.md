---
layout: default
title: General Info
parent: Detailed Docs
nav_order: 100
---

# Some General Information For Your Reference

These are certain tips you might want to remember for UI automation with Tidal framework. 
The below list is not complete. More will be added later.


## To Check an Element is Present Or Not

The `find("locator")` method cannot be used to check the existence of an element.
It will throw a Timeout error in case the element fails to appear. 

The following code snippet can be used to check for the presence of an element without
causing a test exception.

```java
find("locator").waitFor(5).expecting(toBePresent);  //This will make sure that at least one of the element is present

if(findAll("locator").isPresent()){ 
    //do something
}
```

## How to Freeze Dropdowns

Open developer tools and navigate to 'Console'.
Paste the below code into console and press enter.

```javascript
setTimeout(()=> {debugger;}, 9000)
```

Now click on the dropdown and wait for the screen to freeze. 
You can inspect the element now using the browser inspect element tool.
You can increase or decrease the time '9000' (9 seconds) as per your needs.

## How to open Allure Reports Locally

1. Open Firefox browser.
2. Type <b>about:config</b> into the URL search bar and press 'Enter'.
3. Accept the warning.
4. In the search bar type `security.fileuri.strict_origin_policy`.
5. Double click its value to change it from 'true' to 'false'.
6. Extract the allure report and find the 'index.html' file in it.
7. Open with firefox.


## How to Kill Chrome Sessions

Windows:

```
taskkill /F /IM ChromeDriver.exe
taskkill /F /IM Chrome.exe
```

Mac OS:

```
sudo killall chromedriver
sudo killall Google\ Chrome
```

## Avoid using UIElement and UIElements for too many actions

Since most of the action methods are built as fluent methods which return the instance of UIElement or UIElements,
take caution before your use it for your tests. 

For the example below, the return value of find("element") is UIElement. Using the same element, you can do the following

```java
 UIElement uiElement = find("element");

 uiElement.waitFor(3).expecting(toBePresent);
 uiElement.click();
 ```

 if the 'element' cannot be found, the click action will fail in 3 seconds. You might expect it to fail with the 
 framework default wait of 5 seconds, but it inherited the explicit wait of 3 seconds from its previous statement. 
 
 Instead the code could have been like below:

 ```java
find("element").waitFor(3).expecting(toBePresent);
find("element").click();
```

In the above code, you are not propogating the reduced wait time. So click would fail with 5 seconds if `element` is not found.

***NOTE:*** Every time the find("element") method is invoked, it resets all the previously configured values. 


## Input not set Error

This error would happen if you do not initiate the Browser instance correctly. If you are using Cucumber, make sure that your hooks 
are running. 

## Sample Project to Download

Please find below a sample project to download and practice. It contains all the necessary files and folders. There are some 'to_delete' text files in the  folders which can be deleted once you put some code files in there.

Sample project download link:

```java
git clone git@github.com:tidal-code/example.git
```

Note: This uses and SSH url and you may need to configure SSH authentication with your system and github









