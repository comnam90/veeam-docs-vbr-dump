---
title: "/systemSessions/{ID}/events"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/systemsessions_id_events.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a list of all log events of a system session having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/systemSessions/{ID}/events |

Related Resources

[/systemSessions/{ID}](systemsessions_id.md)

Methods

The following methods are supported for the /systemSessions/{ID}/events resource:

[GET /systemSessions/{ID}/events](get_systemsessions_id_events.md)

Resource Representation

The /systemSessions/{ID}/events resource has a resource representation of the following type:

|  |
| --- |
| <SystemSessionEvents xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/systemSessions/00057ade-8f1a-4b54-a265-391441981e25/events" Type="SystemSessionEvents"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
