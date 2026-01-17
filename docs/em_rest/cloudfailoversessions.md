---
title: "/cloud/failoverSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cloudfailoversessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of cloud failover sessions performed on all backup servers connected to Veeam Backup Enterprise Manager.

A new cloud failover session is started every time you start a cloud failover plan. When the start a cloud failover plan operation completes, a cloud failover session ends.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cloud/failoverSessions |

Related Resources

[/cloud/failoverSessions/{ID}](cloudfailoversessions_id.md)

Methods

The following methods are supported for the /cloud/failoverSessions resource:

[GET /cloud/failoverSessions](get_cloudfailoversessions.md)

Resource Representation

The /cloud/failoverSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
