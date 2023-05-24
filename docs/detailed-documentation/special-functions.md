---
layout: default
title: Functions and Features
parent: Detailed Docs
nav_order: 15
---

# Special Functions

These functions are quite unique to the Tidal Wave framework. 

## Retry If

Tidal can retry a set of actions perfomed before if a certain condition is not met. Those conditions are called retry conditions.

### Not Present

Let's imagine you click a button and a popup is supposed to open. Some times, the click may not be effective or the click may have
happened before the component was ready to interact with. The only logical solution to this problem is to try to click on the element again
so that the popup will appear as a result. The condition here is the presence of the pop up. You can write this as below 

```java
find("element").click().retryIf(notPresent("new element"));
```

The click() action will try again if the 'new element' is not present as a result. It will try exacly once. If you need to try a few times, just 
give the number of tries as the second parameter of 'retry'

```java
find("element").click().retryIf(notPresent("new element"), 3);
```

This will attempt the click() action three times or until the 'new element' is PRESENT. To get the meaning of the function, you have to read it with
the name of the method `retry if not present`.

### Not Visible

This can be used if the new element is not visible and you want to attempt a few retries

```java
    find("element").click().clear().sendKeys("some value").retryIf(notVisible("new element"));

    //To attempt the retry a number of times.
    find("element").click().clear().sendKeys("some value").retryIf(notVisible("new element"), 4);
```
<br>
#### Opposites of the above

The below to conditions are the opposites of the above two. 

### Still Present
If an element is supposed to disappear from the DOM (hidden or not hidden), you can use the stillPresent() condition as below:

```java
    find("element").click().sendKeys("some value").retryIf(stillPresent);

    //To attempt the retry a number of times.
    find("element").click().sendKeys("some value").retryIf(stillPresent, 4);
```

Here, a second locator is not needed as we are checking the condition on the same element.

### Still Visible
If an element is supposed not to be visible any more from the DOM, you can use the stillPresent() condition as below:

```java
    find("element").click().sendKeys("some value").retryIf(stillVisible);

    //To attempt the retry a number of times.
    find("element").click().sendKeys("some value").retryIf(stillVisible, 4);
```

Here, a second locator is not needed as we are checking the condition on the same element.


## Do Page Refresh
New (v - 1.3.0)
{: .label .label-green }

Certain elements may not appear until you do a page refresh. But a single page refresh may not 
guarantee the element would appear and we may have to try it again a few times. 
Normally, we can use a loop to check the presence of the element, but the code would be quite complex
and if you forget to add a timecounter or another condition to exit the loop in time, it would result in an infinite loop. 

The solution can be easily achieved by using the `doPageRefresh()` method.
The parameters of the method are the maximum time and the refresh interval time.

Example:

```java
find("element").doPageRefresh(MaxTime maxTime, IntervalTime intervalTime).click();
```

The refresh function will try for a 'maxTime' with interval 'intervalTime' until the 'element' is found. 


## Slow Run

New (v - 1.3.0)
{: .label .label-green }

You can make Tidal run a bit slower using the property `slow.run = true`
The value can be passed as an environment variable or can be put in the `configuration.properties` file.
This will result in a slower execution. 

NOTE: Do not use this option in your daily test automation runs. This should be used only for debugging purpose or demo purpose 
when you present your test automation to the stake holders.

## Debug Mode
New (v - 1.3.0)
{: .label .label-green }

Debug mode will generate more logs than the normal run. It will enable you to identify the exact point of failure. 
You can enable the debug mode passing the the property `debug = true` 








