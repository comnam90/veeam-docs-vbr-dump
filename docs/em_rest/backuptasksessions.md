---
title: "/backupTaskSessions"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backuptasksessions.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backupTaskSessions


Represents a collection of backup tasks run on backup servers connected to Veeam Backup Enterprise Manager.

You should distinguish the /backupTaskSessions resource from the /backupSessions resource. The /backupSessions resource provides information about a specific cycle of a backup job. The /backupTaskSessions resource provides information about a specific task within a backup job session. Typically, one task processes one object in the backup job: VM or VM container.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backupTaskSessions |

Related Resources

[/backupTaskSessions/{ID}](backuptasksessions_id.md)

Methods

The following methods are supported for the /backupTaskSessions resource:

[GET /backupTaskSessions](get_backuptasksessions.md)

Resource Representation

The /backupTaskSessions resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0"> |


