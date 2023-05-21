---
layout: default
title: API Requests
nav_order: 5
has_children: false
permalink: docs/api-requests
---

# API Request Capabilities

Tidal has got API request capabilities under the hood. Though it doesn't offer you a full fledged API testing capabilities,
it will give you enough to extend its capabilities using other libraries. 

A few examples are given below:

```java
    Request.set("url");
    Request.setMediaType("Media Type"); // json, xml etc
    Request.setHeader("key", "value");
    Request.setQueryParams("key", "value");
    Request.setPayload("payload");
    Request.send(ReqType) //
    Request.response() //to retrieve response object
    Request.getResponseString() //retrieve response as string
    Request.reset() // to close and reset all connections
```




