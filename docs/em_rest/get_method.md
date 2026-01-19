---
title: "GET Method"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/get_method.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# GET Method


The GET HTTP method is used to read data or retrieve information about a resource.

In case of success, the GET HTTP method returns the HTTP response code 200 OK. In the response body, the method returns a representation of the resource.

In the example below, the GET HTTP method is used to retrieve a resource representation of the default backup repository entity:

|  |
| --- |
| Request:  GET https://localhost:9398/api/repositories/3efc471c-04be-4dd1-9ed2-54e7fddc5ecf?format=Entity    Response:  200 OK    Response Body:  <Repository xmlns="http://www.veeam.com/ent/v1.0" Type="Repository" Href="https://localhost:9398/api/repositories/3efc471c-04be-4dd1-9ed2-54e7fddc5ecf?format=Entity" Name="Default Backup Repository" UID="urn:veeam:Repository:3efc471c-04be-4dd1-9ed2-54e7fddc5ecf"> |


