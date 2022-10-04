---
layout: default
title: Configuration Properties
parent: Detailed Docs
nav_order: 7
---


---

# Supplying Property Variables for Testing

Testing in different environments require different variable values. When we try to hard code the value, our tests would become inflexible and will not be able to switch to different test environments. 

For this purpose we need to externalise the data. One way of doing this would be storing data in property files. The framework has built in support for reading from property files. 

```java
 controller.properties //decides test enviroment
 application-{test environment}.properties
```

The controller properties files should contain the value `environment = {test environment}` for example if your test environment name is 'TRAINING' the the value should be `environment = TRAINING`. The corresponding properties file would be in the format `application-training.properties`.





