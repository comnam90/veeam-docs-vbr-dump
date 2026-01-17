---
title: "/cdpReplicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicatasksessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of CDP replication task sessions that run on backup servers connected to Veeam Backup Enterprise Manager.

The /cdpReplicaTaskSessions resource differs from the /cdpReplicaSessions resource. The /cdpReplicaSessions resource represents a 24-hour session of CDP replication. The /cdpReplicaTaskSessions resource provides information about a specific task within a CDP replication session. Each task processes one object (VM or VM container) until a new long-term restore point is created. After a long-term restore point is created, Veeam Backup & Replication starts new CDP replication task sessions.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaTaskSessions |

Related Resources

[/cdpReplicaTaskSessions/{ID}](cdpreplicatasksessions_id.md)

Methods

The following methods are supported for the /replicaTaskSessions resource:

[GET /cdpReplicaTaskSessions](get_cdpreplicatasksessions.md)

Resource Representation

The /cdpReplicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
