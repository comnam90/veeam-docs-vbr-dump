---
title: "/cdpReplicaSessions/{ID}/cdpReplicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/cdpreplicasessions_id_cdpreplicatasksessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions


Represents a collection of CDP replication task sessions of the CDP replication session that has the specified ID. Within the CDP replication session, each task processes one object (VM or VM container) until a new long-term restore point is created. After a long-term restore point is created, Veeam Backup & Replication starts new CDP replication task sessions.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/cdpReplicaSessions/{ID}/cdpReplicaTaskSessions |

Related Resources

[/cdpReplicaTaskSessions/{ID}](cdpreplicatasksessions_id.md)

Methods

The following methods are supported for the /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions resource:

[GET /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions](get_cdpreplicasessions_id_cdpreplicatasksessions.md)

Resource Representation

The /cdpReplicaSessions/{ID}/cdpReplicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


