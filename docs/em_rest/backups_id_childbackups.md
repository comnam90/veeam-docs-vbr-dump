---
title: "/backups/{ID}/childbackups"
product: "vbr"
doc_type: "em_rest"
source_url: "https://helpcenter.veeam.com/docs/vbr/em_rest/backups_id_childbackups.html"
last_updated: "5/22/2025"
product_version: "13.0.1.1071"
---

# /backups/{ID}/childbackups


Represents a collection of all [ChildBackup](get_backups_id.md#BackupType) resources of a [ParentBackup](get_backups_id.md#BackupType) backup type having the specified ID.

Resource URL

|  |
| --- |
| https://<Enterprise-Manager>:9398/api/backups/{ID}/childbackups |

Related Resources

[/backups/{ID}](backups_id.md)

Methods

The following methods are supported for the /backups/{ID}/childbackups resource:

[GET /backups/{ID}/childbackups](get_backups_id_childbackups.md)

Resource Representation

The /backups/{ID}/childbackups resource has a resource representation of the following type:

|  |
| --- |
| <EntityReferences xmlns="http://www.veeam.com/ent/v1.0" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"> |


