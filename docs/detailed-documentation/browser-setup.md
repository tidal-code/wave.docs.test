---
layout: default
title: Browser Setup
parent: Detailed Docs
nav_order: 1
---

# Browser Setup

The framework will run in Chrome by default, but if you want to run in any other browser, you can specify its name as a string value.

Options are [chrome, firefox, edge, safari]
 
**<span class='text-red-000'>Caution:</span>** 
Safari will not support headless execution

## Browser Specific Set up
The below given is an example for Chrome Browser Setup. The browser options need to be set up by yourself as each browser vendor will have different implementations and it is hard to standardise the options with the framework. 
 
For local execution: 
```java
ChromeOptions options = new ChromeOptions();
options.addArguments("window-size=1920,1080"); 
Browser.withOptions(options)
       .withWaitTime(Duration.ofSeconds(15)) //Your custom wait time, else the default wait time of 5 seconds applies
       .open("url"); //'url' is any web url that you can use. 
```


For remote execution if the browser is Chrome; add the following options:
```java
ChromeOptions options = new ChromeOptions();
options.addArguments("window-size=1920,1080");
options.setHeadless(true);
options.addArguments("--no-sandbox");
options.addArguments("--disable-dev-shm-usage");
```

***Note:*** You should use a standardised screen size across your automation projects. Here the window-size option is given as 1920*1080. You can choose any size as per your requirement. Bear in mind that most modern websites are responsive, and they change their layout with screen size. Once you set the test browser screen size, do not attempt to maximise or resize the browser yourself. If your team uses different monitors with different resolutions, your test automation script would fail when another team member with a smaller screen size try to run them on their local machine.
