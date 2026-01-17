---
title: "/logonSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/loginsessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of currently existing logon sessions for Veeam Backup Enterprise Manager REST API.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/logonSessions |

Related Resources

[/logonSessions/{ID}](loginsessions_id.md)

Methods

The following methods are supported for the /logonSessions resource:

* [GET /logonSessions](get_loginsessions.md)
* [POST /sessionMngr/](post_sessionmngr.md)

Resource Representation

The /logonSessions resource has a resource representation of the following type:

|  |
| --- |
| <LogonSession xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://www.veeam.com/ent/v1.0" Href="https://enterprise04.tech.local:9398/api/logonSessions/7686d89e-26fd-48e6-963c-c9dbce802981" Type="LogonSession"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
