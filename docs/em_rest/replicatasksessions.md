---
title: "/replicaTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/replicatasksessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /replicaTaskSessions


Represents a collection of replication tasks run on backup servers connected to Veeam Backup Enterprise Manager.

You should distinguish the /replicaTaskSessions resource from the /replicaSessions resource. The /replicaSessions resource provides information about a specific cycle of a replication job. The /replicaTaskSessions resource provides information about a specific task within a replication job session. Typically, one task processes one object in the replication job: VM or VM container.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/replicaTaskSessions |

Related Resources

[/replicaTaskSessions/{ID}](replicatasksessions_id.md)

Methods

The following methods are supported for the /replicaTaskSessions resource:

[GET /replicaTaskSessions](get_replicatasksessions.md)

Resource Representation

The /replicaTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


