---
layout: default
title: Data Storage
parent: Detailed Docs
nav_order: 10
---

# Built In Dynamic Data Storage

A dynamic data storage mechanism stores data only for the life time of a test. It is not permanent. There are no files to read or write data. Instead the data will be kept in the memory and used during the active test run time. Once the test is finished the data will be cleared.

The framework by itself do not provide any method to write data to any file types. For that you can use your own utility functions. A good starting point is the Apache Commons FileUtils library. 

Inorder to use the built in dynamic data storage in the framework, you can use the addData(KEY, value) method. It stores the value againts the 'KEY'. The key can be either a string value or an extended enum value of the **DataEnum** class.

The 'KEY' can be later used to retrieve data using the method getData(KEY).  

Example:

```java
//Adding data to be stored
addData("THE_KEY", "some data string");

//Retrieving stored data
getData("THE_KEY");
```

The DataEnum class is a special interface that can be extended to use as the 'KEY'. The drawback with string keys is that, you need to be careful while retrieving the data. A wrong key would give you a null return value. The DataEnum class is safer for that reason as it will be using the enum constant value.

How to set up a data enum class example:

```java
//Set up Data Enum class
public enum CustomerData implements DataEnum{
    CUSTOMER_A("John"),
    CUSTOMER_B("Doe");

    final String key;

    CustomerData(String key) {
        this.key = key;
    }

    @Override
    public String getKey() {
        return key;
    }
}

//Using the data Enum Class
addData(CustomerData.CUSTOMER_A, "This is some informatin about customer A");

//Retrieving the data
getData(CustomerData.CUSTOMER_A);
```



