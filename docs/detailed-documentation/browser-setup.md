---
layout: default
title: Browser Setup
parent: Detailed Docs
nav_order: 1
---

# Browser Setup

The framework will run in Chrome by default, but if you want to run in any other browser, you can specify its name as a string value.

Options are [chrome, firefox, opera, edge, safari]
 
Opera and Safari will not support headless execution

## Browser Specific Set up
The below given is an example for Chrome Browser Setup.  
 
For local execution: 
```java
ChromeOptions options = new ChromeOptions();
options.addArguments("window-size=1920,1080"); 
Browser.withOptions(options)
       .withWaitTime(Duration.ofSeconds(15)) //Your custom wait time, else the default wait time of 5 seconds applies
       .open(PropertiesFinder.getProperty("base.url"));
```


For remote execution if the browser is Chrome; add the following options:
```java
ChromeOptions options = new ChromeOptions();
options.addArguments("window-size=1920,1080");
options.setHeadless(true);
options.addArguments("--no-sandbox");
options.addArguments("--disable-dev-shm-usage");
```
