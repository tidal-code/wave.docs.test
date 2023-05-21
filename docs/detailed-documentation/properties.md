---
layout: default
title: Data and Properties
parent: Detailed Docs
nav_order: 9
---


---

# Supplying Property Variables for Testing

Testing in different environments requires different variable values. When we try to hard code the value, our tests will become inflexible and will not be able to switch between different test environments.
 For this purpose we need to externalise the data. One way of doing this would be storing data in property files. The framework has built in support for reading from property files.

```java
 controller.properties //decides test enviroment
 application-{test environment}.properties //environment specific data file
```

The controller properties files should contain the value `environment = {test environment}` for example if your test environment name is 'TRAINING' the the value should be `environment = TRAINING`.
This is an easy set up for your local runs. You can override this value in your CICD pipelines by setting pipeline environment variables. 
The corresponding properties file would be in the format `application-training.properties`.

## How To Read Data

If you need to read data using the built in framework method, you need to have three essential files as below

```
controller.properties //decides test enviroment
application-{test environment}.properties //environment specific data file
configuration.properties
```

The first two files - controller.properties and application-{test environment}.properties should be put inside the folder ```test/resources/properties```

The property value can be read as a string using the method ```PropertiesFinder.getProperty("key")```


## Data Read Order

The order of data reading would be

```Environment Variables > Configuration.Properties > application-{environment}.properties```

This is given as such because, we might need to override the static values in our properties files using the system environment variables. For example, regardless of what 'environment' you have put
in the controller.properties file, if you want to pass a different environment variable, that value will gain the precedence. 



