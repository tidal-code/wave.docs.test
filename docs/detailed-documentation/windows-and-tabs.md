---
layout: default
title: Windows and Tabs
parent: Detailed Docs
nav_order: 14
---

# Windows and Tabs

Sometimes, you might need to work with multiple windows and tabs in the same test. You may want to approve a
request opening a new window or tab and then come back to the application to continue testing. Tidal supports both
mutli windows and multi tabs testing. 

## Windows

Tidal supports working with multiple windows in the same test. You can open a new window in the middle of the test 
and switch over to the new one and continue testing. Later if you need, you can switch back to the previous window.
There is no limit to the number of windows that can be opened. 


```java
Windows.openNewWindow("url");
Windows.switchToWindow(int);
Windows.switchToWindow(TabOrder); //first, last
Windows.closeWindow(); //closes the active window and would switch back to the last window
Windows.closeWindow(TabOrder); //first, last
Windows.closeWindow(int); //index
```


## Tabs
Same as windows, Tidal supports working with multiple tabs in the same test. You can open a new tab in the middle of the test 
and switch over to the new one and continue testing. Later if you need, you can switch back to the previous tab.
There is no limit to the number of tabs that can be opened. 


```java
Tabs.openNewTab("url");
Tabs.switchToTab(int);
Tabs.switchToTab(TabOrder); //first, last
Tabs.closeTab(); //closes the active tab and would switch back to the last tab
Tabs.closeTab(TabOrder); //first, last
Tabs.closeTab(int); //index
```









