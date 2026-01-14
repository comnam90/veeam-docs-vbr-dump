---
title: "replicasessions_id_replicatasksessions"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicasessions_id_replicatasksessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---


In this article

Represents a collection of replication task sessions of the replication session that has the specified ID. Within the replication session, each task processes one object (VM or VM container).

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaSessions/{ID}/replicaTaskSessions |

Related Resources

* [/replicaSessions/{ID}](replicasessions_id.md)
* [/replicaTaskSessions](replicatasksessions.md)

Methods

The following methods are supported for the /replicaSessions/{ID}/replicaTaskSessions resource:

[GET /replicaSessions/{ID}/replicaTaskSessions](get_replicasessions_id_replicatasksessions.md)

Resource Representation

The /replicaSessions/{ID}/replicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <?xml version="1.0" encoding="utf-8"?> |

Page updated 5/22/2025

Page content applies to build 13.0.1.1071
