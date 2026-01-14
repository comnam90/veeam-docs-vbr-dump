---
title: "format"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/format.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

The format query parameter allows you to define the representation type that you want to retrieve using the query. Veeam Backup Enterprise Manager REST API lets you retrieve representations of two types:

* References (retrieved by default)
* Entities

For details, see [Resource Representations](resource_representations.md).

For example, using the query below, you can get a list of VM restore point entities:

|  |
| --- |
| Request:  GET https://localhost:9398/api/query?type=VmRestorePoint&format=entities    Response:  200 OK    Response Body:  <QueryResult xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
